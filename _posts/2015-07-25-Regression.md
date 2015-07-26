---
layout: post
title: "Week 3: Let's Regress In A Good Way"
published: true
---

It has been more than a decade since I last encountered statistical regression so it was not suprising that I had completely 
forgotten about what it is and what it does. For a non-math major like myself, regression would most likely mean to return to 
a former or less developed state. It sort of gives that negative connotation of moving backwards or not progressing. So imagine 
my confusion when I learned that we will be applying regression in statistical modeling. I was like... "wait, what?" 

Anyway, enough about that. I am writing this blog as it is my duty to try to help out ordinary (no offense to math and statistics folks, you are all brilliant!) "regressors" (like me :)) understand this concept in the most basic and non-technical manner.

Is it normal to wonder how "regression" became a very popular term in statistics and the answer to that is Francis Galton. I'm not going to dive deep into his research because that will need an entirely new blog, but the long and short of it, "regression" was derived from Galton's 1886 paper titled "Regression towards mediocrity in hereditary stature". If you are curious to know more about his research, here is a good resource: [Why Is It Called Regression by Ann Lehman and John Sall](http://www.biostat.jhsph.edu/courses/bio653/misc/JMPer%20Cable%20Summer%2098%20Why%20is%20it%20called%20Regression.htm)

Regression in statistical meaning is simply a method of fitting lines or curves through our X and y data points. X variables are also called predictor or independent variables while y are response or dependent variables and also called labels. Basically, regression is trying to find the best line or curve that fits our data so that we can use this line or curve as a model for when we predict the values of y's given a new set of X's in the future. To help understand this definition better, I will be showing the different models I got when I tried plotting the tv dataset I scraped from the web.

I will be using the following Python library for my demo:
* `statsmodels` (for creation of regressions/models)
* `patsy` (for generating my X and y sets to be used as input to statsmodels)
* `matplotlib` (for plotting)

**Regressions Demo**
======

####The Data  

Before doing any regression, you must first scrape/build your dataset. For this demo, my dataset is tv shows basic data.

![_config.yml](https://raw.githubusercontent.com/stephanieleevillanueva/stephanieleevillanueva.github.io/master/images/Week_3/tv_df.png)

####The Problem

Once you know and see what data you have, you can then choose your problem. Looking at my dataset, I am curious to know if I can accurately predict how many seasons a tv show will run based on given features. Translating it to variables, my y is going to be
the number of seasons and my X can be whichever other feature(s) I choose. For now I will start out with my X being only the user ratings.

####Pre-Modeling

Though this is not a requirement, before doing regression or any type of analysis, it is good practice to try to see first what your data looks like on a plot. The reason is it might already give you a hint as to what model to use that would best fit your data. It saves a good amount of time doing analysis rather than going in blind.

![_config.yml](https://raw.githubusercontent.com/stephanieleevillanueva/stephanieleevillanueva.github.io/master/images/Week_3/dataset_plot.png)

####Model 1: Simple Linear Regression Model

Let's get to the modeling part. As I've mentioned earlier, our initial model will only have 1 X feature and we will use Linear Regression for that. Python has at least a couple of modeling libraries that are very intuitive and user-friendly and for this demo we will be using `statsmodels`. We will also want to import `patsy` and `matplotlib.pyplot`.

![_config.yml](https://raw.githubusercontent.com/stephanieleevillanueva/stephanieleevillanueva.github.io/master/images/Week_3/imports.png)

Next, we build our model.

![_config.yml](https://raw.githubusercontent.com/stephanieleevillanueva/stephanieleevillanueva.github.io/master/images/Week_3/ols1.png)

We'll break this down line by line. The first line with `dmatrices` is creating 2 arrays, 1 for my X variables and 1 for my y variables. It takes the values from my `tv_df` dataset and assigns `Seasons` (value before the ~) to my y array `ols_train1_y` and assigns `UserRating` (value after the ~) to my X array `ols_train1_X`. The next line basically creates my model. I know what you're thinking... yes, it is that simple! I use OLS (Ordinary Least Squares from Linear Regression module) model of statsmodels to create the line that fits my X and y data points. The last line is a bit more tricky. When you run the `summary()` function of a model, it will display a comprehensive statistics table, as shown below.

![_config.yml](https://raw.githubusercontent.com/stephanieleevillanueva/stephanieleevillanueva.github.io/master/images/Week_3/summary1.png)

The summary table can be a bit overwhelming. Or at least that's how I felt upon seeing this pop-up for the first time. Not to worry, in determining how well your model fits the data, you really only need to look at a couple of things: R-squared and adjusted R-squared. R-squared is the variance that can be explained by the model which means we want a high R-squared, as close to 1 as possible. Adjusted R-squared provides an adjustment to R-squared such that an independent variable (any X) that has a correlation to Y increases adjusted R-squared. Conversely, any independent variable without a strong correlation will make adjusted R-squared decrease. Adjusted R-squared matters if you have more than 1 independent variable, otherwise both R-squared and adjusted R-squared will be more or less the same (e.g. this model). 

Looking at the statistic P>|t| in the second table will also give you insight as to which independent variable or X impacts the Y the most. A feature with a very small P>|t| value has a strong correlation with the Y.

Now that we know how to interpret the goodness of fit of a model (using R-squared), we can say that this first model did not turn out to be a good fit and we can improve it much more.

Before moving on to a new model that hopefully would be a better fit to the data points, I'm going to show you the plot of the first model.

![_config.yml](https://raw.githubusercontent.com/stephanieleevillanueva/stephanieleevillanueva.github.io/master/images/Week_3/plot1.png)

As you can see, a good ratio of the blue dots (actual values) are far off from the red line (model predicted values) which means the sum of errors for each point is very high.

####Model 2: Multiple Linear Regression Model

Now for the second model I will be using multiple linear regression, or in simple terms a model with more than one X. I choose `UserRating` and `Genre` as my predictors as shown in the code below.

![_config.yml](https://raw.githubusercontent.com/stephanieleevillanueva/stephanieleevillanueva.github.io/master/images/Week_3/ols2.png)

One cool feature of `dmatrices` is its ability to recognize categorical (non-numeric) features and convert them into what are called dummy variables. Basically, a dummy variable is an artificial variable created to represent an attribute with two or more distinct categories/levels. Regression needs numerical features and dummy variables are the answer to that. For more on dummy variables, you can read [The Use of Dummy Variables in Regression Analysis by By Smita Skrivanek](https://www.moresteam.com/whitepapers/download/dummy-variables.pdf)

Apart from dummy variables, the process of building a model is generally the same. We will check the `summary()` to see whether adding `Genre` created a better fit model.

![_config.yml](https://raw.githubusercontent.com/stephanieleevillanueva/stephanieleevillanueva.github.io/master/images/Week_3/summary2.png)

Looks like the R-squared statistic improved, but not by much. Also, the adjusted R-squared is showing a lower value than the R-squared which means that although adding genre as predictor increased the variance that can be explained by this model, genre does not have a very strong correlation with Y. Interestingly, there is one genre that shows strong correlation with Y and that is the reality genre. This means that reality TV shows generally run for more seasons, about 1.5 more, when compared to other shows.

Here is the plot of this model.

![_config.yml](https://raw.githubusercontent.com/stephanieleevillanueva/stephanieleevillanueva.github.io/master/images/Week_3/plot2.png)

What I've shown above are only 2 of the very many ways of building a model. There is enough flexibility in these models. You can do quadratic models where you add another feature which is the square of your X, polynomial models to go beyond just squares, log-linear models where you transform your y into log form, etc. I think knowing beforehand which model will probably best fit the data comes with experience and the more you try and do it, the better you'll become at it. Happy modeling! :)
