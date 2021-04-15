---
layout: post
title:      "Art n Joliette"
date:       2021-04-15 18:41:28 -0400
permalink:  art_n_joliette
---

TL;DR heres a link to the project: [click me!](https://art-n-joliette.herokuapp.com/)

I did it, I finally did it ! I graduated ! It feels good to say. 

Unfortunalty the fun part is over, now it's job search time. Last time I job hunted I made the mistake of stopping to code every day, this time I want to find a project that I want to see done so I can make the time to complete it all the while sharpening my newly learnt knowledge.

Good timing, my best friend just texted me and she wants to know if I can make her an app. (I'm sure you've all had this conversation)
She is majoring in "Art" and making her capstone project.
Ok I'll be honest, I don't know how to translate what she's majoring in, but it has to do with culture more than it has to do with art.
Her capstone project is to bring a class of highschoolers around a neighboorhood that has a lot of street art and get them to appreciate it. Theres much more to it but for my purposes that's all I need to know. To get them excited about it, she wants to create a game app where you need to complete a puzzle to access the art piece information (such as gps coordinates, description, pictures...) She also wants to describe the artists and have a place to talk about the history of the neighboorhood.
After hearing all that she wanted in the short amount of time that she wanted it, I suggested instead of a phone App, using a website which will work accross diffent OS's without having to create two apps (Android and iOS).

We talked for many hours about the details and what could be done and what made sense to do. She only had a quick idea and had barely put any thought into it (as expected from anyone coming to a software developper with an idea )
This is a perfect probono project for me to:
* keep coding and learn new things
* learn how to work for a client 
* learn how to work from home (some say it's an important skill to master during Covid19)
* learn how to comunicate software to a non software knowlegeble team
* work on different schedules (Time zones in particular)
* populate my Github
* coding for an evolving product as client ideas kept coming as I was completing the website and giving them inspiration

So I accepted to make it.
She also left me with the idea and I could do mostly what I wanted as for designs so I got to unleash my creative side which was nice.
She and her team still got the final say and made me chage a few things here and there but as for the choice of language, frameworks, packages, hosting website... it was all up to my little self.

#### Choice of tools

I believe **React** was the perfect framework for the job, I could see repitions of objects that React Components would work beautifly. I was also planning on making my own API with Ruby on Rails mostly because I was excited to use multiple languages on a single project but I quickly realized it was overkill since they changed their mind and instead of having an unlimited amount of art/enigmas that admins would be able to create they will only have 4, so I wouldn't even need a CRUD architcture since I only need to *Read* so I decided a json file in my project with all the data will do. 

I was kinda sad not to be able to have a CRUD website nor a RESTfull API but I need to create something that makes sense instead of something that I think is more fun. This would not be as difficult as I intended it to be but that's ok they still managed to take me out of my comfort zone.

#### Agile and deployment mistakes

As soon as the project was good enough to do the basic functions I wanted to deploy it to make it accessible, yes to show it off, but also to create a link that they could use in real time so they could give me feedback faster thant me sending screenshots of my work of the day since they seemed genuinely annoyed by my constant messages. I have to admit, I did not forsee their lack of intrest in the project. As soon as I stopped sending them almost daily updates (Agile style) they stopped giving me feedback. It did have the benifit to reinforce why **Agile** method is effective. I had to keep sending messages of what I accomplished but I started sending them weekly instead of daily. It did the trick, I guess all teams have different interest levels? It was educational trying to tailor a communication pattern with them so that they don't lose intrest and I don't waste my time.  

Anyway I chose **Heroku** to deploy the website mostly because they made it easy to deploy automatically through **Git** so I didn't need to take an extra step everytime I update the website. I'm sure there are many other free hosting websites that are just as easy but I had to make a decision! Setup did take me almost a week but that's because I could not find the proper documentation, not that they don't have it, I was just reading the wrong one.... Their error messages were very unhelpfull as well but I wouldn't have gotten any error if I had just read the proper documentation. Lesson learnt!

#### Why React?


The point of React and not just Javascript was because Objects. Javascript is not quite a OOP and since I will have 4 different Art pieces with 4 different artists, I just thought I'd make it easier for myself and make objects that I could just pass down properties. Reduce, Reuse, Recycle right?
Not that it would've been impossible to do in Javascript, but I do like Reacts simplicity.
I also could've used Ruby on Rails but since I was planning on making a Ruby on Rails API I thought it would be better excersise to code in both languages instead of an all Ruby website. With that in mind, React was a better choice in my opinion.

#### Biggest challenge

Other than communication issues since my French is deteriorating fast from lack of use, the hardest part was probably including somone elses code AKA packages.

The team wanted puzzles and I'd rather not spend a whole week creating a puzzle when there are plenty of **Node** Packages out there that does exactly what they ask for. The two that I am currently using are giving me grief. 

*The jigsaw puzzle* works great!... on a computer. Touch sceen is not enabled with it which means phones cannot solve it, (it's not a bug it's a feature) I might have to find a different package for it but in the meantime I have left the urls "unsafe" as I call it, to easily change the url to acces the art without having to solve the puzzle. As soon as I fix this issue I plan on putting the solved art in a cookie session so they won't have to keep solving the puzzled once it has been done. And obviously making the urls "safe".

*The Labyrinth* was a tougher one. She wanted to free draw a pattern that would need to be close enough to her drawing to solve it, it took me a while to figure out I could instead use a phone unlocking principle to draw the maze. But the package I'm using is giving bugs that are out of my control. It is intended to be a 3x3 even though it lets you make as many points as you'd like, unfortunatly it can give the wrong output if you're drawing right to left.

<div>Example:
</br>
 1     2     3     4</br>
 5     6     7     8</br>
 9    10  11  12</br>
13  14  15  16</div>

If you're solution path is 4 3 2 1 and try to go from 4 to 1, skiping the 2 and 3, it should output 4321 instead it outputs 4231 which is less than ideal but not a deal breaker, I can work around this issue.

The biggest problem is that it makes the app crash but only if you're using a phone and only sometimes. I have no idea what triggers the crash nor do I know how to fix it but it's clear that it comes from this package. 

Of course the issues are only showing for a phone seeing as the whole purpose of this webiste is to use on phones

#### To Summerize

I've learnt a lot about working for a Client throughout this process. How to communicate and how to apply my skills.
Tommorow is their presentation day and I will not be coding for them anymore. I will however stubbornly finish this website and make sure to keep upgrading it
