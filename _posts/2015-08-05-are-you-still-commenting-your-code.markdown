---
layout: post
title:  "Skipping comments leads to higher quality code"
date:   2015-08-04 17:00:00
categories: Comments
comments: true
draft: true
published: false
---

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
I digged up some code I myself wrote a few years ago which we can analyze for this purpose. 

{% highlight objective-c %}

    - (void)locationManager:(CLLocationManager *)manager didUpdateToLocation:(CLLocation *)newLocation fromLocation:(CLLocation *)oldLocation {
        
        //Check if the horisontal accuracy indicates an invalid measurement
        if(newLocation.horizontalAccuracy < 0) {
            return;
        }
        //Test the measurement to see if it is more accurate than the previous measurement
        if(self.bestEffortAtLocation == nil || self.bestEffortAtLocation.horizontalAccuracy > newLocation.horizontalAccuracy) {
            //Store location as best effort
            self.bestEffortAtLocation = newLocation;
            //Test the measurement to see if it meets the desired accuracy
            if(newLocation.horizontalAccuracy <= self.locationManager.desiredAccuracy) {
                //We have a measurement that meets our requirements and can stop updating the location (to save battery)
                [self.locationManager stopUpdatingLocation];
                [NSObject cancelPreviousPerformRequestsWithTarget:self selector:@selector(stopUpdatingLocation:) object:nil];
                
                NSDictionary *dict = [NSDictionary dictionaryWithObject:newLocation forKey:@"LOCATION"];
                [[NSNotificationCenter defaultCenter] postNotificationName:@"locationFound" object:self userInfo:dict];
            }
        }
    }

{% endhighlight %}

- Some comments are plain unecessary and can be removed:

    //Store location as best effort
    self.bestEffortAtLocation = newLocation;

- But most of all, comments are easily removed by refactoring the code for readability and separating, the rpecious method could look like the following:
 
{% highlight objective-c %}

    - (void)locationManager:(CLLocationManager *)manager didUpdateToLocation:(CLLocation *)newLocation fromLocation:(CLLocation *)oldLocation {
        NSLog(@"didUpdateToLocaation lat: %.2f long: %.2f", newLocation.coordinate.latitude, newLocation.coordinate.longitude);
        
        if(IsInvalidMeasurement(newLocation)) {
            return;
        }

        if(IsMoreAccurate(newLocation, self.bestEffortAtLocation))
            self.bestEffortAtLocation = newLocation;
            
            if(newLocation.horizontalAccuracy <= self.locationManager.desiredAccuracy) {
                [self.locationManager stopUpdatingLocation];
                [NSObject cancelPreviousPerformRequestsWithTarget:self selector:@selector(stopUpdatingLocation:) object:nil];
                
                NSDictionary *dict = [NSDictionary dictionaryWithObject:newLocation forKey:@"LOCATION"];
                [[NSNotificationCenter defaultCenter] postNotificationName:@"locationFound" object:self userInfo:dict];
            }
        }
    }
    
    {% endhighlight %}
    

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

So my point is that most programmers that come from school are vivid commenters and therefore need to be convinced or taught these ideas. 

#nått skit
The above code snippet is obviously in itself not bad code, what I mean is that with a bit of refactoring the comments could be made obsolete. 



A pretty common discussion I participate in is the existential question about whether we should comment our code or not. I think encouraging comments is a really bad idea and actually leads to various code smells and worse code quality than uncommented code. I'll start of the discussion with a pretty obvious use case of bad comments.

`bad code example`




Arbetstitel: **Why not commenting leads to better source code / Skipping comments leads to source code of higher quality**
- kör på idén att lösa kommentarer med refaktorisering vilket i sin tur tvingar användaren att koda enligt endast-ett-syfte per metod principen (DRY - don't repeat yourself).
- Kommentarer åldras på ett annat sätt än koden
- folk uppdaterar inte kommentarer
- endast okej i externt dokumentationssyfte (javadoc osv)
