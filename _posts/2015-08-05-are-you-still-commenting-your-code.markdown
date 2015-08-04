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

#Hur man ersätter kommentarer

#If comments are so bad, why do people still use them?
In the academia I was taught that code without comments is bad because it is hard to read and understand. I used to  believe in this statement in school because in that environment it was somewhat true. We programmed alot with C and somehow the praxis when teaching C (maybe because of its heritage as an old school language) is to use short and abstract variable names. It seems like the more theoretical a subject is, the worse the code is. For instance, let us take a look at the wikipedia page for [Merge sort](https://en.wikipedia.org/wiki/Merge_sort), it is interestingly common to use bad variable names such as j, B, i1, A and crowd the code with comments.

{% highlight c %}

//  left half is A[iBegin :iMiddle-1]
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

´bad code example´ 










Just putting it here so I don't forget.


Arbetstitel: **Why not commenting leads to better source code / Skipping comments leads to source code of higher quality**
- kör på idén att lösa kommentarer med refaktorisering vilket i sin tur tvingar användaren att koda enligt endast-ett-syfte per metod principen (DRY - don't repeat yourself).
- Kommentarer åldras på ett annat sätt än koden
- folk uppdaterar inte kommentarer
- endast okej i externt dokumentationssyfte (javadoc osv)
