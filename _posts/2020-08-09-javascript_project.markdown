---
layout: post
title:      "Javascript Project"
date:       2020-08-09 13:12:00 +0000
permalink:  javascript_project
---



#### OOP
I've said it once, I've said it a million times, I am so much more comfortable with OOP languages. Javasript had me worried because I haven't used a frontend language in a while, thankfully it's (kinda) a OOP language. It was fun finally doing what felt like a real website. Obviously we're not quite there yet as the URL (amongst other things) is not optmal to say the least... but having a "frontend" folder and a "backend" folder made it feel real. 


#### Easiest project so far ?
My husband and I bought a house, Hurrah for us! Obviously we're excited about the news, but Oh the stress that comes with! We're closing right before the deadline of this project?! Oh boy am I in for a treat. I won't be able to walk to work anymore so we need to buy me a car, we're showing the appartement we're leasing so there's no slack when it comes to home chores... With all of that going on, I need to find the time to work on this project. 
I would wake up 1 hour early everyday to make the time. The first day I have off I worked all morning on the project.
And I was done. That's it? That's all it took? I read the requirements 3 times not beleiving it, but yes. I was done. My first thought is that the CLI in Ruby felt the same way. I was done in half a day and was really confused why we had so much time to finish it. Then I remembered I acutally have experience in OOP languages and we're studying part time and it's our first project.
So why was javascript being the second to last project so simple? I'm really worried I butchered this.
So instead of stressing out I decided to give my remaining time to complicate things. I do like myself a challenge!
Instead of doing only 2 of C.R.U.D., I'll do all 4. I don't have much time to spare but if I can do just that, I'll consider this a success. I don't like doing the bare minimum if I can help it.

#### Create
I started with the Read an Delete being the easiest ones. Update was more challenging already as I wanted to show the previous values so the user would have a better idea on what they want to edit.

Create on the other hand was nothing but trouble.
I purposfully didn't add any requirements in my database to create an object. No "Needs X characters or more" for the name of the plant, no default value, no error on anything.
Obviously I did need to add a belongs_to and a has_many. 
I cannot create a plant withou t a user that they belong to. Simple right? Right?!

For some reason I kept getting a "422 Unprocessable Entity" error. It wouldn't say which entity in unprocessable that would be too easy...
user_id  was unrecognized, creating a User object wouldn't work because I'm creating a frontend Javascript object, not a backend Ruby object.
I double and triple checked my database making sure I linked everyting together with belongs_to and has_many, that my migrate file had user_id as an integer... I made sure to play arround with my seed file and made sure with were the minimum data to send to a User object to create one.
I have no idea what's causing the issue and how to fix it. I have to submit the project today but I will keep trying!


