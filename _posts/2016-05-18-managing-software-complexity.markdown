---
layout: post
title: "Managing Software Complexity"
date: 2016-05-18 12:42:00
categories: complexity
author: Alexander Heimonen
comments: true
---
When I went to university and started learning to program I spent a lot of my free time making games from scratch, I wanted to apply some of my physics knowledge in making game engines. I started off with making a space simulation game and implemented movement based on *Newton's law of motion,* gravity was affecting the ships and I made them able to shoot bullets. However, the engine proved to become more difficult to program the more features I added, I wanted collision detection, support for multiple players etc. and finally ended up in scrapping it all together due to design flaws and the engine being way too complex to keep together without introducing bugs all across the board. I did not give up, though, and ended up restarting from scratch multiple times bringing knowledge of my mistakes to the next try. My point being that reducing complexity in software design is not something only the most senior software architects need to address, it is among the first problems a junior programmer has to learn ways to tackle as well. 

I have seen a lot of projects where simple fixes introduce multiple bugs, where programmers do not understand how the system works and are afraid to make changes, the systems end up succumbing in their own complexity. 

In this article, even though I am providing some pointers, the reader should keep in mind that complexity in one end could be simplicity in another end. There is no rule of thumb or a pragmatic way to always achieve simplicity and many times complexity is warranted. There are two terms to keep in mind here, *essential complexity* and *accidental complexity*, programming is not simple and the tasks our systems need to address are not inherently simple either, so a complex design would be warranted in order to minimize the growth of *accidental complexity*. 

# Software Complexity

When we design software, what we essentially do is abstract real world problems into code, we need to create an exact model of reality since we need to determine precisely how the domain works. It is difficult to interface accurately with the complex real world, that is not only approximately correct but exactly correct. This increases the *essential complexity* of the code, which needs to be designed in such a way that as the software grows, the *accidental complexity* does not get out of hand and the project remains maintainable and sufficiently easy to understand.[^1]

The most important technique to reduce complexity is to design programs in such a way that we can focus on one part at a time, as Dijkstra pointed out that no one's skull is really big enough to contain a modern computer program (Dijkstra 1972). The system needs to be split up in several well-defined components, the most important being:

1. **Software System**
At this level, it is important to think about what the purpose of the system is, what requirements it is supposed to address and generally which technology stack is going to be used.
2. **Subsystems or packages**
It is important to identify all subsystems and their purpose at this level, how they are allowed to use each other. The latter being the most important part, if all subsystems can communicate with each other, then there is little purpose in partitioning them. The fewer dependencies a subsystem has, the easier it is to reuse elsewhere since there are fewer hoses to reconnect.	
3. **Classes within packages**
At this level, the subsystem is divided into the most important classes or interfaces. The level of effort at this level is dependent on how big the system is and how much responsibility the developers can handle. It is generally a good idea to have a rough idea of the general class design before development begins.

Now if the system is huge, a developer can focus on building one class at a time, or if the system is smaller the developer can focus on building a subsystem at a time. 

# Keeping it Clean

Today's applications grow larger and larger and a fundamental shift has started to happen years ago, the biggest complexity in software is in the application design as a whole and not in the smaller parts. This makes it top priority for a programmer to write clean and well-designed code that is easy to read. Software architecture is out of scope for this article, so I chose to focus on some guidelines to improve design, quality, readability and reduce complexity of code when designing and programming software:

- **Design for the maintenance programmer.** 
Make your code and design self-explanatory, try to imagine what questions a maintenance programmer would ask you about your code. 

- **Avoid clever code.**
Unless you are writing code for devices with limited resources there is little to no need to do clever bit shifts or algorithms to reduce 5% of CPU load. With that being said, most programmers love to be clever, but when working with professional code we simply have to be able to control our urges. The big downfall in clever code is maintainability, problems can be incredibly hard to fix, or as one of the co-authors of the book *C Programming Language* put it: 

> "Debugging is twice as hard as writing the code in the first place. Therefore, if you write the code as cleverly as possible, you are, by definition, not smart enough to debug it." — Brian Kernighan﻿

- **Avoid assumptions.**
Everyone has done it, more often early in their careers, but these bugs still manage to find their way into the code, bugs caused by the core belief that... *"This can never happen"*. It goes along the lines of "This number can not be negative", "This date can never be null", "Obviously the user is going to input correct data so we don't risk division by zero" etc. These kinds of bugs can sometimes be hard to find, sometimes really easy depending on the assumption and where the exception comes from. However, the problem can be prevented by using assertions or some kind of validation.

- **Be pragmatic when you have to.**
There are pragmatic ideas and rules to guide us in our decision-making, there is no need to reinvent the wheel so standard practices exist to speed up programming. However, sometimes it is worth to give a second thought to some decisions so that they do not lead to more trouble along the way. 

- **Louse coupling**
Minimize the knowledge of connections among different components by e.g. using interfaces and good abstractions.

- **Minimize fan-out**
For any given class, minimize the number of classes it needs to have knowledge of. Research shows that using more than seven classes within a class indicates that it may be overly complex.[^1]

- **Think about your abstractions.**
Well designed abstractions allow the programmer to focus on using an interface without needing knowledge or worrying about how it works internally, meaning that from a complexity point of view you can ignore irrelevant details. Programmers use abstractions at all levels of a system, however, I find it fairly common to see classes with interfaces that define *how they work* instead of *what they do*. Keep implementation details hidden in private routines within the classes.

- **Know your design patterns.**
All programmers are taught early to use design patterns, but surprisingly many developers do not have a clear understanding or even knowledge about the most fundamental ones. Design patterns at their core are ready-made solutions to the most common problems encountered in programming and provide familiar abstractions easily recognized by other programmers. So if you do not have a firm understanding of for instance  Adapter, Bridge, Decorator, Facade, Factory method, Template method, Observer, Singleton and Strategy pattern, I strongly suggest you pick up a pattern book and start reading.

# Final Words

The message I wanted to deliver is to always think about the complexity in your code. It is hard to provide clear rules to follow, but as long as you keep the concept in mind you reflect over the impact on the complexity of your code. 

#### Sources

[^1]:(Steve McConnell. Code Complete: A Practical Handbook of Software Construction, 2nd Edition, Microsoft Press, 2004)
