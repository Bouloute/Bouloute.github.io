---
layout: post
title:      "To Prime or not to Prime?"
date:       2020-02-20 23:30:05 +0000
permalink:  to_prime_or_not_to_prime
---


The Prime? Lab is one of my favorites. It's the type of lab that shows us how what coding actually is like. It's a mix of skill and knowledge with a touch of logic. This lab felt like a puzzle to me. A puzzle with multiple ways of solving it.
We all know what a prime number is but how do we make a computer decide if a number is or is not a prime? 

### What exactly is a prime number?

> A prime number (or a prime) is a natural number greater than 1 that cannot be formed by multiplying two smaller natural numbers. -Wikipedia

Simple enough right?

##### So let's start with the first statement.

> A prime number (or a prime) is a natural number greater than 1

All numbers smaller than one **is not** a prime number

```
def prime?(n)
  answer = true
  if (n <=1)
     answer =  false
  end
	
  return answer
end
```

So far so good!

##### Now for the hard part, the second statement.

> A prime number [...] cannot be formed by multiplying two smaller natural numbers.

Let's try and decode what that means:

For a number **x**, **a** and **b** are smaller than **x**. If **a** x **b** = **x** then **x** **is not** a prime  

In pseudo: 

* Multiply **a** by **b**  
* If equals **x**, answer is false
* If not, keep going
* Increment **a**
* Repeat until we've tried every combination

Which will look like this
```
answer = true

a,b = 2,2 
  while (b<n)
    while (a<n)
      if (a*b == n)
        answer =  false
      end
      a += 1
    end
  a = 2
  b += 1
  end
  return answer
```

This will work but there's a few things that bothers me.

##### Let's optimize this
First is my love for returns, and how usefull they are, and how I'm sad that you don't even need to write return in Ruby.

Let's take an example. If we're checking if 20 is a prime, there will be "only" 289 itterations ( 2 to 19 = 17. 17 x 17 = 289)
Sounds excessive right? Especially if 2 x 10 = 20 and that will only require 8 itterations. Which means 281 are uneccesary! What's worse is that 4 x 5 will also change the answer to false when we already had the answer to false. 
So let's make me happy and remove that answer variable and just exit the itteration if/when we have found proof that the number **is not** a prime

```
  if (n <=1)
    return false
  end
	
  a,b = 2,2
  while (b<n)
    while (a<n)
      if (a*b == n)
        return false
      end
      a += 1
    end
  a = 2
  b += 1
  end
  return true
```

Muuuuuch better. Finding a prime will still take more time than a non-prime, but we've made progress!
There's still plenty of ways to optimize this.
For example, if **a**x**b** is greater than **x** then I can stop incrementing **a** because the rest is usless itterations. 


##### Other, maybe better solution?
So that's some solutions. I'd like to finish with the method I've decided to go with.

Let's find wikipedia's definition again

> A prime number [...] cannot be formed by multiplying two smaller natural numbers.

Earlier, this is what we took from it:

For a number **x**, **a** and **b** are smaller than **x**. if **a** x **b** = **x** then **x** **is not** a prime  

But what happens if we reverse this understanding?
Instead of multipling let's divide.
See where I'm going here? 
If the remainder of **x** / **a** is 0 then we've found proof that **x** **is not** a prime number! 

We don't need to increment and itterate over **b**. In fact, we can just forget about ~~**b**~~!  What a time saviour!

In pseudo: 

* Find the remainder of **x** / **a**
* If remainder is 0 -> non prime -> exit with return false
* If remainder is != 0, keep going
* Increment **a**
* Repeat

``` 
  a = 2
  while(a<n)
    if ((n % a) == 0)
      return false
    end
    a += 1
  end
  return true
```

Ahhhhhh. Isn't this much more readable than the first try?

I'm sure there is better, more optimal ways of finding a prime number. But that's enough for today!

If you're doing this lab, I hope you've had as much fun as I did. 
