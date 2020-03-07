---
layout: post
title:      "My CLI Gem Project"
date:       2020-03-07 03:59:53 +0000
permalink:  my_cli_gem_project
---



### What I chose and Why
<p>My hardest challenge here was to chose what my gem would be able to do. I wanted to do something half usefull and half challenging. I'm really bad at being asked to come up with stuff like this on the spot and couldn't think of anything in particular. Also all my ideas were way too complicated for no reason other that I wanted to make something usefull. So I turned to my muse and asked my husband, Justin, what he thought I should do. His answer was not suprising... It revolved around Hockey. He suggested I should make a gem that collects the stats of players to make a fantisy team and then blabered on for another hour on what I could do (all NHL related). So I decided to look at a few sport websites and started my scraper class and playing around with data until I found a website I was happy with [CBS Sports](http://www.cbssports.com).</p>



#### CLI
<p>First on the list, CLI</p>
<p>This project is quite new and I want to make sure it will behave in a sensible matter so I'll just draw the outlines for now and then add the data.</p>

<p>So on my first (main) screen I want to ask the user what the would want to look into. The Player or the Team stats. Choice "1" or  "2"</p>

```
def call
    puts "Welcome to NHL Stats"
    puts "Here you will be able to see your favorite team or player's statistics from CBS Sports." 
    menu_help  # this will show what commands the user can do

    user_input = nil
    while user_input != "exit"
        user_input = gets.chomp.downcase
        case user_input
        when "1"
            user_input = team_menu 
        when "2"
            user_input = player_menu 
        when "help"
            menu_help
        end
    end
end
```

<p>Now that I have my outline I have a better idea of how to move forward.</p>
<p>My team menu will show the team names then promt the user to get more detail about a team.</p>

<p>So lets get that data!</p>

#### Scraper
My scraper class is actually pretty small as it only contains one method

```
def self.scraper(index_url)
   Nokogiri::HTML(open(index_url))
end 
```

<p>Seems almost unnecessary to create a class this small but it doesnt make sense to put this in anywhere else.
I just added a binding.pry in there to play around with the data untill I could figure out how I was going to collect the data I needed. </p>

#### Teams

<p>I mainly chose CBS Sports because they have all the stats... in a table! How easy! And also I love myself a math problem.</p>
<p>Since all the data is a td, it's a little harder to define what my data is exactly. Thankfully all my data is ordered and every X amout is a new row.</p>

<p>For my team table, every team contains 10 different stats (ergo 11 elements with the team name). So every 11 element is a new Team. Easy to say but how to tell ruby to do that?</p>

<p>I've decided to make two indexs, one for my colum and one for my row. </p>
<p>I start at the first row of data and check if the element I'm on is the first element of the row: (11* row_index) + 1  == element_index</p>
<b>Important: the first element has nothing to do with the team stats, thus I add +1 when I check every 11 elements</b>
<p>The last element also has nothing to do with the team stats. The "Team" name reads "Pages: 1 2 All". To remedy to this I've simply decided to ignore any teams who's first data (aka the name of the team) includes the word "Pages". It's not the best fix as if a team name contains the word "pages" it will likely be ignored. Thankfully I have a NHL connaiseur who told be without hesitation that no NHL teams names contains the word "pages". Lucky me! </p>

```
scraped_data = Scraper.scraper(index_url)

row_index = 0
scraped_data.css("td").each_with_index{|row_info, element_index| 
   # 11 because there is 11 collums of information given one team
   if (11 * row_index + 1) == element_index && !row_info.text.include?("Pages")
      data = {}
      collum_index = 0
      data_index = (11 * (row_index)) + 1
      11.times{
         data[scraped_data.css("th")[collum_index].text] = scraped_data.css("td")[data_index].text
         collum_index += 1
         data_index += 1
      }
      Team.new(data)
      row_index += 1
   end
end
```

#### Players & Refactored Scraper

<p>Now that I've finished my team, I can start doing the same for players. Only difference is that there is 18 different stats (ergo 19 elements) and I'm making a Player object and not a Team object.</p>

<p>I immidiatly think "repitition" and will modify my scraper to be more dynamic. </p>
<p>I'm now passing in a string of the name of the class I'd like to create. And If it's a Team , my row is 11elements, if it's a Player, my row is 19 elements. </p>

```  
    def self.set_from_scraped_data(index_url, class_name)
        scraped_data = Scraper.scraper(index_url)

        row_index = 0
        scraped_data.css("td").each_with_index{|row_info, element_index| 
            # 11 because there is 11 collums of information given one team
            if class_name.downcase == "team"
                if (11 * row_index + 1) == element_index && !row_info.text.include?("Pages")
                    creator_from_data(scraped_data, row_index, 11)
                    row_index += 1
                end
            # 19 because there is 19 collums of information given one player
            elsif class_name.downcase == "player"
                if (19 * row_index + 1) == element_index && !row_info.text.include?("Pages")
                    creator_from_data(scraped_data, row_index, 19)
                    row_index += 1
                end
            end 
        }
    end
		
		
		
		  def self.creator_from_data(scraped_data, row_index, number)
        data = {}
        collum_index = 0
        data_index = (number * (row_index)) + 1
        number.times{
            data[scraped_data.css("th")[collum_index].text] = scraped_data.css("td")[data_index].text
            collum_index += 1
            data_index += 1
        }
        if number == 11 
            Team.new(data)
        else 
            Player.new(data)
        end
    end

```

#### Today's Games & new Scraper method

<p>To be honest I mainly made this feature because there's a requirement to record myself coding for 30 min and I didnt notice until I finished so I added this feature to do exactly that. Then I took it as a challenge to make this feature in 30min. It only took me 55min, so I failed it... Also I managed to fail my recording and the .mp4 showed a black screen for 55min. Not my best. </p>

<p>Thankfullly, I love challenges and I wasn't satisfied with the level of difficulty I imposed myself, a win-win situation if you may. This feature would show today's game, teams, time and location. But the important part is that this time I won't be scraping in the same format as Team and Player.</p>

<p>Unfortunatly for me this new data was also stored in a table but I've decided to use a whole different method to collecting the data I need. This time, I'll devide the index by five and collect the remainder.</p>
<li> If the remainder is 0 it's the first data of the row. AKA a team name</li>
<li> If the remainder is 1 it's the other team name</li>
<li> If the remainder is 2 it's the time of the game</li>
<li> If the remainder is 3 it's the place of the game. I now have all the information I need, I can go ahead and create a Game object.</li>

<p>All the data came with unecessary spaces so I used the gsub to get rid of them</p>

```
        game_data = {}
				
        scraped_games.css("td.TableBase-bodyTd").each_with_index{|game_info, index| 
            
            case index % 5
            
            when 0
                game_data[:team_one] = game_info.text.gsub(/\s+/, '')
            when 1
                game_data[:team_two] = game_info.text.gsub(/\s+/, '')
            when 2
                game_data[:time] = game_info.text.gsub(/\s+/, '')
                if game_data[:time].include?("NBCS")
                    game_data[:time] = game_data[:time].gsub("NBCS", "")
                end
            when 3
                game_data[:place] = game_info.text.gsub(/\s+/, '')
                Game.new(game_data)
                game_data = {}
            end
            
        }
```

#### Refactored CLI

<p>Once I've managed to scrape all my data off, I want the user to be able to access the info whenever they want.</p>
<p>I've also wanted to make sure that the user will be able to exit and return to the main menu any time they'd like. I've managed to obtain this by exiting the team/player/game menu with the user input, the main menu will collect this and behave as if the user imputed this on the menu screen.</p>

<p>Here's the team menu as an example</p>

```
    #menu for the team stats
    #returns nil or "exit" 
    def team_menu
        #displays teams name
        Team.display_all_names_only

        #shows possible commands
        team_help

        #collects command
        while 
        user_input = gets.chomp.downcase
            if user_input.to_i != 0 && user_input.to_i <= Team.all.size
                team_asked = Team.get_from_index(user_input.to_i)
                team_asked.display_all_stats

            elsif user_input == "help"
                team_help
            elsif user_input == "back"
                #returning to the main menu
                menu_help
                return
            elsif user_input == "exit"
                #returns to the main menu to exit
                return user_input
            end
        end
    end
		```


##### Potential Upgrades

* Find a player or a team by entering their name instead of an arbituary number
* Sort players by team or name
* Add some colour to make it more readable
* Create a fantasy team (view team, add and delete players)

