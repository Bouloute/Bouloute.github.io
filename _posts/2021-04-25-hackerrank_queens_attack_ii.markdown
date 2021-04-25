---
layout: post
title:      "HackerRank Queen's Attack II"
date:       2021-04-25 23:36:32 +0000
permalink:  hackerrank_queens_attack_ii
---


I love coding challenges.
I thought I might as well write about one that I'm working on.

[Here's the link so you can follow allong ](https://www.hackerrank.com/challenges/queens-attack-2/problem)

### Intro

Since we've all seen Queen's Gambit, lets talk chess! 
I have never been able to beat my older brother at chess, he can read my every strategy. Maybe it's my fault for only playing the ones he taught me. I remember after a pretty brutal defeat, he told me I'm too logical in my way of thinking which was why he could read me so well.  If Chess is not a logical game I don't know what is... My father backed me up saying that no human could beat a machine on chess since a machine could calculate all options and weigh in the best strategy for a play much faster than a human ever could. (He was right at the time...)

The more I learnt about coding, the more I thought about that statement. Who tells the machine about the strategies and how do you tell it to think?

I have not played a Chess game in over 10years so I'm very rusty but it's ok, for this excercise we don't need to know how to play chess.
Here are the rules to the excercise

### Rules

For a specific size of a board, with a specific number of obstacles placed throughout the board, the queen will be placed on the board and we will need to calculate how many possible moves the queen can make on this board.

The queen can move horizontaly, vertically or diagonally. She cannot go through an obstacle.

### My method

HakerRank gives you 3 tests to try out your code with.
When you submit your solution, they give more tests to make sure your code is successfull.

Call me Spock if you must but their test includes a 1000x1000 board and  up to 10^5 obstacles and well... that's just illogical...
A chess board is 8x8. 
I made my solution to work on any size board BUT it will be very very slow to solve the biggest boards. Which means I cannot submit my solution as passing. This is a choice I made on purpose because I wanted to be able to test out other pieces like the rook (moves horizontally or vertically) or the bishop (diagonally).

So I prioritzed future features over speed since it's absurd to have a 1000x1000 board...




So I created two functions for this excercise. One for counting moves of any pieces that moves in a line (bishop and rook are the only other pieces that can move in a line until the reach an obstacle) and one for counting the Queens possible moves that will utilize the previous method.

If I needed to count all possible moves for the other pieces, then I would just need to substract any obstacle that are in the way of the possible moves.

My Queen piece can move in 8 possible dirrections, it will call my 2nd method 8 times and giving it the direction to look at.

```
def queensAttack(n, k, r_q, c_q, obstacles)
    counter = 0
		
		#Clockwise
		
    counter += checkLineOfAttack(rowQueen, columnQueen, sizeBoard, obstacles, 0, 1)    #North
    counter += checkLineOfAttack(rowQueen, columnQueen, sizeBoard, obstacles, 1, 1)    #North East
    counter += checkLineOfAttack(rowQueen, columnQueen, sizeBoard, obstacles, 1, 0)    #East
    counter += checkLineOfAttack(rowQueen, columnQueen, sizeBoard, obstacles, 1, -1)   #South East
    counter += checkLineOfAttack(rowQueen, columnQueen, sizeBoard, obstacles, 0, -1)   #South
    counter += checkLineOfAttack(rowQueen, columnQueen, sizeBoard, obstacles, -1, -1)  #South West
    counter += checkLineOfAttack(rowQueen, columnQueen, sizeBoard, obstacles, -1, 0)   #West 
    counter += checkLineOfAttack(rowQueen, columnQueen, sizeBoard, obstacles, -1, 1)   #North West
                                           
																					 
    return counter
end

```

As you can see I'm passing the Queens position, the obstacles with their positions, the size of the board but more importantly I'm passing in the direction of the move

If I were to write the rooks method it would look like this:

```
def rooksAttack(n, k, r_q, c_q, obstacles)
    counter = 0
		
		#Clockwise
		
    counter += checkLineOfAttack(rowRook, columnRook, sizeBoard, obstacles, 0, 1)    #North
    counter += checkLineOfAttack(rowRook, columnRook, sizeBoard, obstacles, 1, 0)    #East
    counter += checkLineOfAttack(rowRook, columnRook, sizeBoard, obstacles, 0, -1)   #South
    counter += checkLineOfAttack(rowRook, columnRook, sizeBoard, obstacles, -1, 0)   #West 
                                           
																		
    return counter
end

```

Yes, yes I know I don't need to but I like to think of upgrades when I code.



As for the checkLineOf Attack

```
def checkLineOfAttack(piece_row, piece_column, n, obstacles, r, c)
    #init counter at 0 
    counter = 0
		
    #start at piece position
    myPosition = [piece_row, piece_column]
		
		#go one "direction" away
    myPosition[0] += r
    myPosition[1] += c
    
    #start loop -> while i'm still looking within the board limits
    while myPosition[0] >= 1 && myPosition[0] <= n && myPosition[1] >= 1 && myPosition[1] <= n        
        
        #check if theres an obstacle present
        obstacles.each do |o|
				
            #if present stop and return counter
            if o == myPosition
                return counter
            end
        end
        
        counter += 1        
        myPosition[0] += r
        myPosition[1] += c
        #end loop <-
    end
    
    return counter
end
```

Did you figure out why my code is so slow yet?

Yes! It's the obstacles.
Every time I'm at a position, I check ALL of the obstacles to make sure I'm not on one. 
Not very optimal.
On a 8x8 the time is insignificant, on a 1000 x 1000 it becomes very obvious which is the only reason they make the tests fail if it takes too long. 

I waved this because I was focusing on future upgrades and put a time limit on myself to find a solution in under an hour. I forgot to time myself but I believe I was closer to 30min than 1h. 

I read other peoples solutions and I want to try a few of them out. I do want to be able to pass all tests...


