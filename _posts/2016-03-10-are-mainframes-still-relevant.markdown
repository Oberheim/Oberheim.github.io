---
layout: post
title: "Are Mainframes Still Relevant?"
date: 2016-03-10 09:11:15
categories: mainframe
author: Alexander Heimonen
comments: true
---
I am in an interesting situation at work where I face two realities, on one hand I work with a customer which entire IT infrastructure is based on an old IBM mainframe and on the other hand I am involved in a huge project called [Ciber Momentum](http://momentum.ciber.com/) which purpose is to accelerate application transformation to modern languages. In other words, to help get rid of legacy mainframe applications. Me and my team have discussed several times how important it is for our customer to modernize their codebase, since every day all integrations and development we make increase the technical debt the company accumulates. They are making the migration to a new system harder by the day and the reality is that soon enough they have to make the transition in order to stay relevant. Perhaps this stubbornness is what makes established companies to become surpassed by new startups, with modern codebases and less technical debt enabling them to change more rapidly. Another problem is that traditional modernization projects are unavoidably expensive with no short term return of investment, which by no means helps the management (which necessarily does not understand the technical reasoning) hard to make the decision to launch such a huge project.

### The state of mainframe development
Approximately 150-250 billion lines of COBOL code is running, mostly on mainframes, today and it is believed that more COBOL transactions occur on a day than Google searches.[^1] So one can argue that there is not a deficit of job opportunities, however there is clearly a deficit of mainframe programmers with the required skillset of COBOL, CICS and/or RPG2. One arguably obvious reason for that is simply that the prime time for mainframe development was a few decades ago, but according to my research[^2] there are a few social reasons why new programmers lack interest in becoming mainframe developers:

#### Most of the work is maintenance work
Most of the work on mainframes today is done to keep them alive and functioning in the ever changing software environment, hence condemning the developer to do maintenance work since there is little innovation in the field. Then again, why should companies invest in new development since they know that sooner or later they will have to switch to another platform?

#### Investments in mainframe knowledge are not easily translated to other fields
Developers always fear to become obsolete, it's hard enough to stay relevant as it is today. So investing a full 8 hours a day into programming something that hardly is of use anywhere else puts a lot of stress to work with modern technologies on the free time in order to eventually transition away from mainframe programming. 

#### It is not accessible to the casual learner
Let us say that you are an aspiring young developer really interested in becoming a mainframe programmer, how do you get started? I would guess that the easiest way to learn is on the job, but that would require for you to get hired as a long term investment for the company. A lot of programmers code at home on their PC without access to a mainframe, but it seems like there is a [virtual mainframe](http://www.hercules-390.org/) available, even though it's a daunting task, one could set up.

So the quantity of programmers with the required skillset is declining and hence the cost to keep the mainframes running is increasing. Even though COBOL is dying it is estimated that it its best before date is in the late 2020:s or 2030:s.[^3] How big is the hurry to replace these applications? One reason they are still around is that they simply work and do that well, so should they be modernized just because they are written in COBOL? 

>“For the most part, the COBOL programs that are out there are the kinds that take data from a database somewhere, crunch them and print out reports on a big printer somewhere, or print off cheques, or something like that. It’s the real pretty straightforward applications that don’t have a lot of technical complexity, that haven’t changed. Like, if you have employee records somewhere and you have a payroll run to run, that whole process hasn’t changed that much since the 1950s. That’s why companies haven’t changed the stuff. (Evan Weaver, chair of the School of Information and Communications Technology at Toronto’s Seneca College.)"[^3]

With that said, there are still loads of mainframes that handle a big part of a company's business logic and that is a reason to get worried. It is not hard to argue that it is a lot easier to manage a modern application that is responsive to your business needs and actually helps you innovate, instead of maintaining an old system with legacy code and complicated release routines. The pace of business is constantly accelerating and so is the pace of technology.

### Ciber Momentum
Ciber Momentum is a transformation accelerator that rapidly automates code for legacy modernization. Using Ciber Momentum, up to 85% of the total lines of code for a project can be generated. It does not rely on an army of expensive programmers that can contribute to risk and poor quality, it does not do a like-for-like translation but instead transforms it to a modern software architecture with a modern user experience. Do not let your competition surpass you by sticking to your legacy solution, instead, move at the speed of business at [http://momentum.ciber.com/](http://momentum.ciber.com/).

#### Sources

[^1]:(Brian Bloom, COBOL and the mainframe: big business and big money, 2013, [URL](http://blog.stafflink.ca/recruiting-tips/cobol-and-the-mainframe-big-business-and-big-money), (accessed 02 February 2016))
[^2]:(Stack exchange, Why aren't young programmers interested in mainframes?, 2012-2015, [URL](http://programmers.stackexchange.com/questions/75486/why-arent-young-programmers-interested-in-mainframes), (accessed 02 February 2016))
[^3]:(Brian Bloom, The future of COBOL: Why it won’t go away soon, 2012, [URL](http://www.itworldcanada.com/article/the-future-of-cobol-why-it-wont-go-away-soon/45722), (accessed 02 February 2016))
