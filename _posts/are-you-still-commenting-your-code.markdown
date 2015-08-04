---
layout: post
title:  "Skipping comments leads to higher quality code"
date:   2015-08-04 17:00:00
categories: Comments, code
comments: true
published: false
---

In the academia I was taught that code without comments is bad because no one will be able to understand it. I believed in this statement my entire education because it was somewhat true. I have later come to the opposite conclusion, but it was hard to see in school since the more theoretical a subject was, the worse the example code shown was. 
For instance, take a look at the wikipedia page for [Merge sort](https://en.wikipedia.org/wiki/Merge_sort), it is interestingly common to use bad variable names such as j, B, i1, A and crowd the code with comments.

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

Of course it is easy to believe that comments increase readability when the code itself is incredibly diffuse and use bad naming conventions. The code itself is unnecessarily hard to read.
Or as Dave Thomas put it in Pragmatic Programmer:
> Programmers are taught to comment their code: good code has lots of comments. Unfortunately, they are never taught *why* code needs comments: bad code requires lots of comments.

The above code snippet is obviously in itself not bad code, what I mean is that with a bit of refactoring the comments could be made obsolete. 


A pretty common discussion I participate in is the existential question about whether we should comment our code or not. I think encouraging comments is a really bad idea and actually leads to various code smells and worse code quality than uncommented code. I'll start of the discussion with a pretty obvious use case of bad comments.

´bad code example´ 










Just putting it here so I don't forget.


Arbetstitel: **Why not commenting leads to better source code / Skipping comments leads to source code of higher quality**
- kör på idén att lösa kommentarer med refaktorisering vilket i sin tur tvingar användaren att koda enligt endast-ett-syfte per metod principen (DRY - don't repeat yourself).
- Kommentarer åldras på ett annat sätt än koden
- folk uppdaterar inte kommentarer
- endast okej i externt dokumentationssyfte (javadoc osv)
