---
layout: post
title:      "Understanding React's props and states"
date:       2021-01-13 00:18:10 +0000
permalink:  understanding_reacts_props_and_states
---


I was a little fuzzy about props and states. I've been understanding their differences and how to use them but failed to explain them in further detail. 

# State
A State is similar to props in the sense that it defines a component object but the similarity stops there. A State is private and fully controlled by the component. It is initialized in the constructor and contains data specific to the component and is mutable. 

Make sure NEVER to mutate this state directly otherwise your component lifecycle will not update corretly
# Props
Props is short for properties, they define the object Component.

So how are they different from a state? 
Well first of all, the props are passed from the parent object to the child object, as opposed to created in the constructor. 
Also, Props are immutable, you should consider them as read only.


As an example if we had a<Pet/> component and a <Dog /> component, we could itterate over the list of all the pets, and for every dog, create a <Dog /> component with the ***properties*** of its name, breed, colour..... 
Just like this: 
```
<Dog name={dogName} breed{dogBreed} colour={dogColour} />
```

In the Dog component class, we would create a state that could have for example: his hunger level or his mood.
Just like this:
```
constructor(props){
    super(props)
		this.state = {
		    hunger: 0,
				mood: "playful"
		}
}
```

 If you pet() this dog, his mood would change but nothing would change his name or breed.
```
pet(){
    this.setState({
    		...state,
				mood: "happy"
	  })
}
``` 

It is also important to note that on every state or props change, a few methods are called including, but not limited to, render() and componentDidUpdate() (Yes, in that order!)
