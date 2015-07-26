---
layout: post
title: "Week 3: Let's Regress In A Good Way"
published: false
---

It has been more than a decade since I last encountered statistical regression so it was not suprising that I had completely 
forgotten about what it is and what it does. For a non-math major like myself, regression would most likely mean to return to 
a former or less developed state. It sort of gives that negative connotation of moving backwards or not progressing. So imagine 
my confusion when I learned that we will be applying regression in statistical modeling. I was like... "wait, what?" 

Anyway, enough about that. I am writing this blog as it is my duty to try to help out ordinary (no offense to math and statistics folks, you are all brilliant!) "regressors" (like me :)) understand this concept in the most basic and non-technical manner.

Is it normal to wonder how "regression" became a very popular term in statistics and the answer to that is Francis Galton. I'm not going to dive deep into his research because that will need an entirely new blog, but the long and short of it, "regression" was derived from Galton's 1886 paper titled "Regression towards mediocrity in hereditary stature". If you are curious to know more about his research, here is a good resource: [Why Is It Called Regression by Ann Lehman and John Sall](http://www.biostat.jhsph.edu/courses/bio653/misc/JMPer%20Cable%20Summer%2098%20Why%20is%20it%20called%20Regression.htm)

Regression in statistical meaning is simply a method of fitting lines or curves through our X and y data points. X variables are also called predictor or independent variables while y are response or dependent variables and also called labels. Basically, regression is trying to find the best line or curve that fits our data so that we can use this line or curve as a model for when we predict the values of y's given a new set of X's in the future. To help understand this definition better, I will be showing the different models I got when I tried plotting the tv dataset I scraped from the web.

**Regressions Demo**
======

####The Data  

Before doing any regression, you must first scrape/build your dataset. For this demo, my dataset is tv shows basic data.

![_config.yml]()

####The Problem

Once you know and see what data you have, you can then choose your problem. Looking at my dataset, I am curious to know if I can accurately predict how many seasons a tv show will run based on given features. Translating it to variables, my y is going to be
the number of seasons and my X can be whichever other feature(s) I choose. For now I will start out with my X being only the user ratings.

####Pre-Modeling

Though this is not a requirement, before doing regression or any type of analysis, it is good practice to try to see first what your data looks like on a plot. The reason is it might already give you a hint as to what model to use that would best fit your data. It saves a good amount of time doing analysis rather than going in blind.

![_config.yml]()

####Linear Regression Model

