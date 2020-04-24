---
layout: post
title:      "Sinatra Project"
date:       2020-04-24 19:44:29 +0000
permalink:  sinatra_project
---


### Choosing a topic

Having finished the labs with ease, I wanted to make sure to give myself some kind of difficulty. 
I noted that there's a bonus section with error messages. I hadn't looked too much into it but made a mental note to use it once I was done with the project. It came in handy knowing in advance how I was going to upgrade my website. I was initially going to create a sort of "404 website not found" view and pass an error message to it to display but I kept myself from doing that as I knew I was going to use the Sinatra Flash gem. 

It's hard trying to find a topic and I remembered for the first project I turned to my husband for ideas. So for my CLI Project I had done a Hockey themed gem.
Why not recycle this idea? 
How would the database look like?
A User has many Teams. A Team belongs to a User
A Team has many Players. A Player has many Teams

That's perfect! There's even a "has many <-> has many" connection between the team and the player table.

Well guess I'm going for unoriginallity then and creating a Fantasy Hockey team maker!


### Writters Block

Topic in hand I open visual studio, create a new folder with a pretty name and ... now what?
Where do I even start?
Do I create my controllers first?
Probably my gemfiles right?
What gems do I need?
So much to do!
Well guess who takes all that work away? Corneal!
Corneal is a gem built for this purpose.

gem install corneal 

corneal new Sinatra-Project

DONE

That's it. So simple. So powerful.

Now that all my files and even some code. I am familliar with this pattern of folders that has been generated and I am comftable working with these.


### Sqlite3
I like to create my database first so I can have a better idea of what to expect and fill my pages


I'm old school and need a pen and paper when I start a project from scratch. It helps me visualise what the database is going to look like and which colums to add to the class.
User will have the usual password, username and email. 
Team belongs to user si I need to remember to put a user_id colum in there. Then and obvious name
Player will have a name too, some stats to show, maybe the name of team they play for and a role on the ice,

I almost forgot to create a join table between the Team and the Player! I know, I know... That was the reason I stuck to this project in the first place...

Seeding was not fun doing research on players and copy and paste with no "difficult" coding was boring. 
I do have to admit that it came in very handy. Also being the only way to add players, it's also vital to the work the project.
I've also added a user and made team with a couple of players in it and belongs to that user, just for the sake of it. 


### Views

Doing the first project I remember thinking that I was saddend by the fact that there is nothing much to do for design. Not that I'm very artistic in the first place, but it's always fun to see what people have been making.


So the next 5 pages of my notebook are just doodles of the different views I want to show.
As opposed to most of the labs we've done I decided not to show all the teams ever created. I feel like that wouldn't make any sense in this case. 


To make my views I visited a few website where talented people share their designs. I wanted to keep mine simple and finding some without javascript helped filtered out the search. There was still thousands if not millions of views to pick from. After choosing a few and altering them to fit my needs I finally have a pretty layout for my views. I spent a lot of time making my sinatra project look nice. A little unecessary, but the challenge was new and fun and I've learned a lot about CSS by making this project and that was gratifying.
 
 ### Authentification
 
 After spending a lot of time doing the design I've also done the technical side I swear!
 As for example a User has an email and a username that is unique to them. They can also have only one team with a specific team name but two users can have the same team names.
 Users have their password encypted too.
 
The obvious get post conections to views but also the patch and delete connections too... 
This project was pretty simple but that doesn't mean I don't feel pride in creating a website from scratch.

 ## There's a Gem for that
Using a flash gem was also something new to me. After some online research I noticed the incredible number of gems that create flash messages. 
 It was actually incredibly easy to use but I'm happy I went through the process of learning how to use this gem.
 
