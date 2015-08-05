---
layout: post
title:  "Skipping comments leads to higher quality code"
date:   2015-08-04 17:00:00
categories: Comments
comments: true
draft: true
published: true
---

![Some really bad code]({{ site.url }}/_assets/bad_code.png)

#Intro (sammanfattning)

#Varför jag tycker illa om kommentarer
Every now and then the discussion of wheterter or not we should write comments in our code arises. I am a firm believer of that comments are bad and should be avoided at all cost. Here is why:
- **Commenting code violates the [DRY principle](https://en.wikipedia.org/wiki/Don't_repeat_yourself).** By writing comments you are essentially duplicating what already is written in code. The comments will inevitably become out of date as the code evolves. Either by developers who do not bother to update the comments, or simply do not understand the consequences of a change well enough to update the comments.
- **Comments can be plain wrong!** People use comments to explain what code does on a higher abstraction level, this could be because the code is really complicated (read: bad) so commenting it is justified to make the code more readable. There are however no guarantees that that the comments are correct, *the only 100% correct description of what the code does is the code itself.*

A pretty common counter argument I hear, even written by Jeff Atwood (the author of [Coding horror](http://blog.codinghorror.com/)) itself, is: 
>No matter how simple, concise, and clear your code may end up being, it's impossible for code to be completely self-documenting. Comments can never be replaced by code alone.

Interestingly enough, he uses the following example: 

>What is perfectly, transparently obvious to one developer may be utterly opaque to another developer who has no context. Consider this bit of commenting advice:

>You may very well know that

>`string = join('',reverse(split('',$string)));`

>reverses your string, but how hard is it to insert

>`# Reverse the string`

>into your Perl file?

Yes! How hard can it be? Well, I might as well ask how hard can it be to refactor it as:

    reversedString = ReverseString($string)
    
Not only do we now have a reusable method for reversing strings, there is also no doubt what the code is doing.

#Techniques to replace comments
I digged up some code I myself wrote a few years ago (it was actually written in objective-c for an iPhone application, but I rewrote it as C# now to save horizontal space) which we can analyze for this purpose. 

{% highlight c# %}

    public void didUpdateLocation(Location newLocation, Location oldLocation)
    {
        //Check if the horisontal accuracy indicates an invalid measurement
        if(newLocation.horizontalAccuracy < 0) 
        {
            return;
        }

        //Test the measurement to see if it is more accurate than the previous measurement
        if(BestEffortAtLocation == null || BestEffortAtLocation.horizontalAccuracy > newLocation.horizontalAccuracy) 
        {
            //Store location as best effort
            bestEffortAtLocation = newLocation;
            //Test the measurement to see if it meets the desired accuracy
            if(newLocation.horizontalAccuracy <= LocationManager.desiredAccuracy) 
            {
                //We have a measurement that meets our requirements and can stop updating the location
                LocationManager.StopUpdatingLocation();
                CurrentLocation = newLocation;
                PostNotification(Event.LocationFound)
            }
        }
    }

{% endhighlight %}

- Some comments are plain unecessary and can be removed:

    //Store location as best effort
    bestEffortAtLocation = newLocation;

- But most of all, comments are easily removed by refactoring the code for readability by for instance:

    //Check if the horisontal accuracy indicates an invalid measurement
    if(newLocation.horizontalAccuracy < 0) 
    {
        return;
    }
    
    Becomes
    
    if(IsInvalidMeasurement(newLocation)) 
    {
        return;
    }
 
The previous method could look like the following:
 
{% highlight c# %}

    public void didUpdateLocation(Location newLocation, Location oldLocation)
    {
        if(IsInvalidMeasurement(newLocation)) 
        {
            return;
        }

        if(IsMoreAccurate(newLocation, BestEffortAtLocation)) 
        {
            bestEffortAtLocation = newLocation;
            
            if(newLocation.horizontalAccuracy <= LocationManager.desiredAccuracy) 
            {
                LocationManager.StopUpdatingLocation();
                CurrentLocation = newLocation;
                PostNotification(Event.LocationFound)
            }
        }
    }
    
    {% endhighlight %}
    
I think the code is self-explanatory.

#If comments are so bad, why do people still use them?
In the academia I was taught that code without comments is bad because it is hard to read and understand. I used to  believe in this statement in school because in that environment it was somewhat true. We programmed alot with C and somehow the praxis when teaching C (maybe because of its heritage as an old school language) is to use short and abstract variable names. It seems like the more theoretical a subject is, the worse the code is. For instance, let us take a look at the wikipedia page for [Merge sort](https://en.wikipedia.org/wiki/Merge_sort), it is interestingly common to use bad variable names such as j, B, i1, A and crowd the code with comments.

{% highlight c %}

    // left half is A[iBegin :iMiddle-1]
    // right half is A[iMiddle:iEnd-1   ]
    TopDownMerge(A[], iBegin, iMiddle, iEnd, B[])
    {
        i0 = iBegin, i1 = iMiddle;
    
        // While there are elements in the left or right runs
        for (j = iBegin; j < iEnd; j++) {
            // If left run head exists and is <= existing right run head.
            if (i0 < iMiddle && (i1 >= iEnd || A[i0] <= A[i1]))
                B[j] = A[i0];
                i0 = i0 + 1;
            else
                B[j] = A[i1];
                i1 = i1 + 1;    
        } 
    }
    
{% endhighlight %}

It makes sense to use general variable names in cases like this, because the purpose is to teach an algorithm, not how to write clean code. The problem is, that if this is the only thing students see they start to write similiar code. And when the code is abstract and hard to understand, it also makes sense to write comments that explain what is happening at a higher abstraction level. To make matters worse, we were all taught to write loards of comments in our code, so much that we even failed our assignments if they were not *"properly commented"*.
Dave Thomas also made the same observation in Pragmatic Programmer:

> Programmers are taught to comment their code: good code has lots of comments. Unfortunately, they are never taught *why* code needs comments: bad code requires lots of comments.

*(Andrew Hunt, David Thomas. Pragmatic Programmer: From Journeyman to Master, Adison Wesley Professional, 1999)*

I also did some digging in one of my favourite books, Code Complete to see what Steve McConleys view on commenting code is, and he somewhat agrees:

>*Comments are used to explain difficult code*. Comments have an important role to play, but they should not be used as a crutch to explain bad code. The age-old wisdom is dead-on: "Don't document bad code - rewrite it" (Kernighan and Plauger 1978). (Code Complete)

If you have read anything he has written you know how focused he is on writing good quality code, but obviously we do not live in a world without stress and tight deadlines. So we write bad code because it is faster, but we should at least feel bad when we do it.

So my point is that most programmers are taught from the beginning to become vivid commenters and therefore need to be convinced or taught these ideas.

#But we write comments anyway
Do you agree at this point that comments are indeed bad and a code smell? However, we can have our pragmatic views and principles, but only a fool would skip them alltogether. We live in a world with loads of stress and tight deadlines, the code we write is not always perfect and rightfully so, sometimes it is more important to ship on time. Perhaps my favorite quote about the subject is from Clean Code:

>The proper use of comments is to compensate for our failure to express ourself in code. Note that I used the word *failure*. I meant it. Comments are always failures.

So given the time frame to write the code, if by flipping all the stones you still do not feel confident enough to leave the code without an explanatory comment, you should rightfully feel bad. You failed to express yourself with your craft, but at least you can come back later and refactor it, right?
