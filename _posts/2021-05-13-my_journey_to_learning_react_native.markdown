---
layout: post
title:      "My Journey to learning React Native"
date:       2021-05-14 01:34:02 +0000
permalink:  my_journey_to_learning_react_native
---


Creating my last project with my friend made me realise that I haven't created a phone app in a while. I've learned what React Native is and I've been wanting to try it out.

Join me on my self journey to learn what it is and how amazing it probably is.
I will be following the tutorials of [Programming with Mash](https://youtu.be/LWs6dY92_MU). 
I like audio tutorials because it's a great tool to be able to follow along faster.

## Setup
The untold step is usually the setup. Fortunatly, my tutorial covers that but since the setup is similar to React, I didn't have to add much to my environement.
I did have to download Android Studio which is kind of a heavy software and it makes me wish I had a faster computer...
I'm not looking forward to running both Android Studio and a Phone simulator on my old computer.

I always run into issues when trying to start something new. I apparently did not have enough room on my computer to download Android studio properly. When I was trying to run the phone simulator I ran into an error "ADP not found" I went into my SDK manager and made sure I had downloaded the SDK and the power tools properly which had not been. (Just click on the box with the - through it and it will start downloading again)

The error did persist becaue Android Studio does not set your SDK by default. Go to the file tab, project structure and set up a SDK. 

Easy errors like this are nice. 

Unfortunatly my computer is not powerfull enough to work the phone simulator and VS. I'm lucky enough to have a much more powerful computer that I can borrow but I need to set everything up and it's taking a while.

On his computer I had to change the version in the .flowconfig file to 0.107.0, replace the extention TypeScript Language Basics with Flow Language Support. I also had to accept Android SDK licences with the `%ANDROID_HOME%/tools/bin/sdkmanager --licenses`
 command. I have absolutely no idea why I didn't have to do that with my computer. I had used android studio in another lifetime so maybe thats why?


Anyway, don't forget to set up git on your new computer!
AKA generate a new ssh key and add it to your github settings.


## Step 2: Playing around
Now that we are all set up, let's start coding!

Let's play around with the design a little bit. First let's delete the generated code and design. Blank canvas! Let's keep 4 lines of absolutely nothing.

```
import React from 'react';

const App: () => Node = () => {
  return {
	
  );
};
```

So far it looks exactly like React and I hope it'll keep with the similarities.

Let's add a little bit of text.

If we were coding in React, we would need to add the text into a component, most likely we would be using JSX and adding a < p> inside a < div>. (It wouldn't need to be inside the div if it's the only component but of course we will be adding more that just a meer text).

Instead of a < div> component will be creating a < View> component. < View> doesnt show anything per say, it is just a container for what we will put inside, we can also style it. It basically behaves exactly like a < div>.

Don't forget to import our components as needed! 

```
import {
  View
} from 'react-native';

const App: () => Node = () => {
  return (
    <View>
		
    </View>
  );
};
```

Did it work? I can't tell. At least so far no errors which is nice... Let's add some text shall we?
Again, no < p>, instead we shall use a < Text> 


```
import {
  View,
	Text
} from 'react-native';

const App: () => Node = () => {
  return (
    <View>
      <Text>Hello World</Text>
    </View>
  );
};
```

Well that's one boring app for sure! Lets add a button for fun!

```
const App: () => Node = () => {
  return (
    <View>
      <Text>Hello World</Text>
      <Button title='Click me!' }></Button>
    </View>
  );
};
```

You might've noticed that you get an error if you don't give a title to your button. The title is simply the text that will be shown on it so no need to over think it.

But wait a second. Nothing happens when we click on it!

Easy peasy lemon squeezy!
Just pass the Button component a function for the onPress parameter.
I will be opening a link but you can do whatever you please
```
      <Button title='Youtube' onPress={()=>{Linking.openURL('https://youtube.com')}}></Button>

```

And now we have a useless app that opens youtube. NICE!


## See you soon!
So far so good! I'm loving the feel of this and I'm hoping it won't be that much different to code as I get to create ;ore intrecate features.
That's all the time I have for this week. My computer issues gave me a hard time but I'm looking forward to doing a part 2. I have a few ideas of what I want to create and I'm excited to go deeper into React Native and see what I can create!


