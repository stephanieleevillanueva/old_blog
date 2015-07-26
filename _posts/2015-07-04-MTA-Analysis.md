---
layout: post
title: "Week 1: A Simple Study On NYC Subway Data"
published: true
---


Well hello there!

I'll be real honest and say this is my first ever attempt at blogging... so if at any point you start to scratch your head and wonder how reading this will add value to your life (it won't, really haha) or worse, I start to bore you to death, you have my permission to move on to the next funner and more interesting blogger out there. :D

So it's my 1st week out of a gruesome (my personal opinion) and insanely intense 12-week program at Metis Data Science Bootcamp here in New York and I thought of writing about our 1st ever project as well as the challenges that came along with it. I'll make this as short and painless as possible, I promise!

We were asked to come up with a simple analysis on NYC's subway data being that well, this is New York and I'd say about 95% of people here take the subway to wherever and it would be a bit interesting to check out some stats on subway ridership.

Btw, a shout out to my groupmates Nidhin and Julia for making this project a success!

After a good number of brainstorming sessions our group came to an agreement that we will do a study on the busiest MTA stations with also the highest ratio of commuters based on data we gathered from http://web.mta.info/developers/turnstile.html (MTA ridership) and http://web.mta.info/developers/fare.html (MTA fare). Why choose this particular dataset you might ask? The answer is... actually for no particular reason lol. Though knowing where to best reach actual "New Yorkers" vs. tourists may come in handy later.

Now on to the process...

**DATA**
======

Having learned ``Python`` in the past week we put it to good use during this project. First, we needed to import the necessary ``Python`` modules (see below).

![_config.yml](https://raw.githubusercontent.com/stephanieleevillanueva/stephanieleevillanueva.github.io/master/images/Week_1/Imports.png)

Next, we pulled data from NYC's MTA website on entries and exits per subway station and converted it into ``pandas dataframe``. We renamed the columns as well. And yes, I know you might be wondering where the distinction is between commuters and tourists. Hold your excitement (lol) and we'll get to that later.

![_config.yml](https://raw.githubusercontent.com/stephanieleevillanueva/stephanieleevillanueva.github.io/master/images/Week_1/Data.png)

Since the data we pulled was raw, we had to do a few more data clean-up and conversions to get it ready for processing and analysis. I won't go into detail anymore or else my blog would turn into a novel (:p) but basically we did data filters and sorts, date parsing, and data aggregates. This part of the process was truly a challenge for all of us, again it's our first week and we were all still getting our feet wet. I guess the main thing is to just keep grinding and eventually you'll get it done, just as we did. :)

Anyway back to the process...
  
**ANALYSIS**
======

We selected a stacked bar graph to represent our findings (see below).

![_config.yml](https://raw.githubusercontent.com/stephanieleevillanueva/stephanieleevillanueva.github.io/master/images/Week_1/stacked_bar_graph.png)

Whoops! Forgot to mention a very important detail in any type of analysis, the scope of our data. The data we used for this analysis is May 2015. As you can see from the graph, we did separate analysis for weekdays and weekends. What does our data tell us? So far we see a significantly higher volume of traffic on weekdays, which makes sense considering NYC is the main hub for businesses. 

**COMMUTER COMPONENT**
======

While it is interesting to see the stations with highest traffic, it does not really mean much at this point. We learned during this process that sometimes as a data scientist, you have to expand your initial dataset to come up with better and more significant data analysis. For us, it was not enough to analyze high volume stations and as I mentioned earlier, we wanted to take into consideration the ratio of commuters to tourists in the highest volume stations.

We repeated the same process as above for commuter data - data extraction (this time from MTA Fare Usage), data clean up and conversion and commuter analysis. Below is the graph to show stations with the highest commuter to tourist ratio.

![_config.yml](https://raw.githubusercontent.com/stephanieleevillanueva/stephanieleevillanueva.github.io/master/images/Week_1/ratio.png)

If the stations above are cross-checked against our highest volume stations, we have 2 totally different lists. Hmm...

**FINAL ANALYSIS**
======

This brings us to our final graph (see below).

![_config.yml](https://raw.githubusercontent.com/stephanieleevillanueva/stephanieleevillanueva.github.io/master/images/Week_1/high_commuter.png)

As you can see while Penn station has a very high traffic volume, it does not show a good commuter ratio. What does this mean? We probably won't want to include Penn station in our stations of interest. The same goes with the opposite outlier, 22 Bay Pkwy station. While this has a good commuter ratio, it's volume is not high enough to be considered as our ideal station. Obviously, what we want are those stations inside the circle.

With visualizations like these, it is much easier to see what we are looking for and as a data scientist, it is very beneficial to know which graphs to use for which type of analysis. I'm assuming it will also be easier to just show to non-technical users our graphs then explain rather than give tons of crunched numbers which probably they won't have any idea how to interpret anyway. :)
