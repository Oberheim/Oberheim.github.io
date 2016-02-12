---
layout: post
title: "Artificial Intelligence Today"
date: 2016-02-12 12:33:00
categories: Programming
author: Alexander Heimonen
comments: true
---
Artificial Intelligence has been around since beginning of computing and was founded as an academic discipline in 1956, and ever since then, the scientific community have thought that they are close to a real breakthrough every decade or so. Already in the 40's research on neurology found out that the human brain is a network of neurons that fires in all or nothing pulses, and *Alan Turing* suggested that it might be possible to build an electronic brain. In 1951, a 24 years old graduate student, *Marvin Minsky* built the first neural net machine, also known as *SNARC*, which is refered to as the first artificial self-learning machine.

But if they already had the right ideas back then, why don’t we have personal service robots at home already?
It turns out that programs like this require incredible amounts of computing power and early logic relies on traversing trees, where the complexity increases exponentially. In mathematics this is called a combinatorial explosion, which is described as a function that grows very rapidly as a result of combinatorial considerations. Therefore a lot of effort has been put in heuristics, finding techniques for solving problems more quickly by trading completeness, accuracy or precision for speed. Heuristics help to reduce the number of alternatives from an exponential number to a polynomial number. In a general sense, the term heuristic is used for any advice that is often effective, but is not guaranteed to work in every case.

### The Dangers of Artificial Intelligence
There has been quite a lot media attention on the advances of AI in recent years, in particular for unarmed drones and weapons technology. And rightfully so, the US military is funding more research than ever on autonomous and self-aware robots. 
Some of our heavy weight leaders in the scientific community, the physicist *Stephen Hawking*, the entrepreneur *Elon Musk* and the multi billionaire, philanthropist *Bill Gates* in particular, recently issued an open letter about the dangers of AI if we don’t take extreme caution. They agree that Success in creating AI would be the biggest event in human history, but unfortunately possibly the last unless we learn how to avoid the risks.

So how afraid should we be? I think that there is some substance to their concerns, but in reality the wast majority of AI:s you and me will encounter are refered to as weak AI:s. For instance, a real time GPS Map application that routes your pathway across traffic to find the most efficient way from point A to point B. The routing software can get really good at that, thousands of times better and faster than a human actually, but would you say that it was thinking? No, and that’s the rub! 

They warn us about what they call *Strong Artifical Intelligence*. AI that is capable of thinking by itself, perhaps with a conciousness and ability to make decisions. 	
Some scientists think that in 2025 we will have an AI that is equally as intelligent as a human being and by 2040 one single AI instance will be as intelligent as the entire human race collectively. The AI problem can be divided into 2 subproblems, the first one is to figure out how to create intelligence, the second one is how to give the AI safe constraints or the same values as humans. I say that if we figre out problem 2 first, we’re safe.
But what happens is just speculation, but I agree that the unknown can be daunting.

>“Massive transformation is on the horizon. Jobs, companies, and entire industries will be reimagined.”
- Paul Roetzer, CEO @PR 20/20

### Artificial Intelligence Today
The Silicon Valley giants like Google and Facebook are currently riding on top of the AI wave of popularity. Google bought the secretive AI company DeepMind for 400 million dollars and are currently experimenting with the tech. Facebook recently unveiled their photo app called Moments that uses AI to recognize a person in the picture. Then we all know about Google’s fully automated self driving cars capable of driving a million miles without an accident. Your android device knows when you’re on your way to work and informs you if there’s a traffic jam on the way or if your buss is late. If i search the net for a weekend trip to London both Facebook and the rest of the net gets filled with travelling ads. AI technology is literally everywhere and I bet that tomorrows fortune 500 companies follow the formula: 

>Take X, add AI.

But that is only the beginning. All the major cloud companies, plus dozens of startups, are in a mad rush to launch a Watson-like cognitive services, speech recognition software and basically anything AI related. According to quantitative analysis firm Quid, AI has attracted more than $17 billion in investments since 2009. Last year alone more than $2 billion was invested in 322 companies with AI-like technology.[^1]

Facebook and Google have recruited researchers to join their in-house AI research teams. Yahoo, Intel, Dropbox, LinkedIn, Pinterest, and Twitter have all purchased AI companies since last year. Private investment in the AI sector has been expanding 62% a year on average for the past four years, a rate that is expected to continue.

So what does all this mean for the rest of us? Do we sit here and wait until the Silicon Valley companies develop their technology and get all the market share for themselves? Well, to be honest the ansver is both yes and no and frankly depends on what you want to do. The thing is that creating a truly intelligent AI requires incredible amounts of resources and data, and naturally an AI gets smarter the more data it gets which puts certain companies at a competitive advantage. Literally everyone is using Google’s services so they have argueably the best data source for their research. So in the end I think there will be just 2-3 companies with competing AI’s. 
But in the same way, the internet is a result of the cold war, we get a lot of technology from this research as well. We will be able to use their AI services, and we can implement our own frameworks with components of AI, like Machine Learning or Deep Neural Networks.

### Deep Neural Networks
Neural networks and deep learning currently provide the best solutions to many problems in image recognition, speech recognition, and natural language processing.
We train an artificial neural network by showing it millions of training examples and gradually adjusting the network parameters until it gives the classifications we want. The network typically consists of 10-30 stacked layers of artificial neurons. In the case of Image Recognition, each image is fed into the input layer, which then talks to the next layer, until eventually the “output” layer is reached. The network’s “answer” comes from this final output layer.
One of the challenges of neural networks is understanding what exactly goes on at each layer. We know that after training, each layer progressively extracts higher and higher-level features of the image, until the final layer essentially makes a decision on what the image shows. For example, the first layer maybe looks for edges or corners. Intermediate layers interpret the basic features to look for overall shapes or components, like a door or a leaf. The final few layers assemble those into complete interpretations, these neurons activate in response to very complex things such as entire buildings or trees.[^2]

### Machine Learning
Deep neural networks is a subfield of Deep Learning which in turn is a subfield of Machine Learning. Which is a subfield of Artificial Intelligence. Machine Learning in general is the most utilized and useful aspect of AI at the moment. Machine learning explores the study and construction of algorithms that can learn from and make predictions on data. Such algorithms operate by building a model from example inputs in order to make data-driven predictions or decisions, rather than following strictly static program instructions. These tasks are typically classified into three broad categories, depending on the nature of the learning "signal" or "feedback". These are:

**Supervised Learning**: The computer is presented with example inputs and their desired outputs, given by a "teacher", and the goal is to learn a general rule that maps inputs to outputs. The data is labeled.

**Unsupervised Learning**: No labels are given to the learning algorithm, leaving it on its own to find structure in its input. Unsupervised learning can be a goal in itself for instance for discovering hidden patterns in data.

**Reinforcement Learning**:  A computer program interacts with a dynamic environment in which it must perform a certain goal (such as driving a vehicle), without a teacher explicitly telling it whether it has come close to its goal or not. Another example is learning to play a game by playing against an opponent

The thing is that Machine Learning does not have to be that complicated. A really simple but surprisingly efficient example is by using Linear Regression. The purpose of this article is not to teach specific implementations, but in short you take a bunch of data points and try to find a linear approximation which fits the data best. [You can read more about Linear Regression on Wikipedia](https://en.wikipedia.org/wiki/Linear_regression). My point is that as long as we are creative we can find use cases for AI in basically any sort of application we are developing. For instance when looking for deviant behaviour in fraud detection or credit risks, or dynamic pricing and product recommendations in eCommerce applications, or just take a look at your Spotify account and see how they recommend music based on what you are listening to. They actually analyze the music itself with deep neural networks and are able to recommend music based on how it sounds, so it is based on a lot more than just metadata!

>”It will be more about the sound. You’ll be able to search by the content of the music instead of just text information associated with it.”
– Nicola Montecchio, head of Deep Learning @Spotify

### Developer
Personally I think that alot of these concepts are easy enough to understand and for us to stay relevant as developers we need to start investing in these skill sets. We are moving more and more towards a Big Data world and effective analyzis techniques are essential in order to stay competitive, and imagine what user experiences we can create in our applications using this technology!

I will give a real world example of something I have done. I worked for one of Swedens biggest datacom and telecom companies, their billing and customer data was in an economy system and their associated costs for their broadband network was in another specialized system. However, they had no connection between each customer and the associated cost for the connection and to make matters worse, there were tens of thousands of entities to be matched, so it could not be done manually. No converntional script could do it either because most of the data was written by hand and therefore full of spelling errors and no specific patterns to match since they adjusted the data based on customer billing needs. So me and a former collegue made an AI that made an educated guess for each entity. The program could match about 90% in one go and the remaining 10% was associated with some sort of error, maybe a resource was unmatchable because there was no customer utilizing it!

[^1]:(Kevin Kelly, The Three Breakthroughs That Have Finally Unleashed AI on the World, 2014, [URL](http://www.wired.com/2014/10/future-of-artificial-intelligence/), (accessed 12 February 2016))

[^2]:(Alexander Mordvintsev, Inceptionism: Going Deeper into Neural Networks, 2015, [URL](http://googleresearch.blogspot.se/2015/06/inceptionism-going-deeper-into-neural.html), (accessed 12 February 2016))
