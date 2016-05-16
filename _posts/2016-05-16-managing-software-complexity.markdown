---
layout: post
title: "Managing Software Complexity"
date: 2016-05-16 13:05:00
categories: complexity
author: Alexander Heimonen
comments: true
tags:
  - draft
---
When I went to university and started learning programming I spent a lot of my free time making games from scratch, I wanted to apply some of my physics knowledge in making game engines. I started off with making a space simulation game and implemented movement based on *Newton's law of motion, f = ma*, gravity was affecting the ships and I made them able to shoot bullets. However, the engine proved to become even more difficult to program the more features I added, I wanted collision detection, support for multiple players etc. and finally ended up in giving up due to design flaws and the engine being way too complex to keep together without introducing bugs all across the board. I did not give up though, and ended up restarting from scratch multiple times bringing knowledge of my mistakes to the next try. My point being that reducing complexity in software design is not something only the most senior software architects need to adress, it is among the first problems a junior programmer has to learn ways to tackle as well. 

I have seen a lot of projects where simple fixes introduce multiple bugs, where programmers do not understand how the system works and are afraid to make changes, the systems end up sucumbing in their own complexity. 

However, even though I am providing some pointers, the reader should keep in mind that complexity in one end could be simplicity in another end. There is no rule of thumb or a pragmatic way to always achieve simplicity and many times complexity is warranted. There are two terms to keep in mind here, *essential complexity* and *accidental complexity*, programming is not simple and the tasks our systems need to adress are not inherently simple either, so a complex design would be warranted in order to minimize the growth of *accidental complexity*. 



- Don't always be pragmatic! Sometimes it's better to avoid established principles if your domain requires it. I've done it, you probably have as well.