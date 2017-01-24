---
layout: post
title: The 1,2, and 3 are alive with the sound of Data !
---

Next you can update your site name, avatar and other options using the _config.yml file in the root of your repository (shown below).

![_config.yml]({{ site.baseurl }}/images/config.png)

Imagine you are a talented [Insert instrument here] player and you were just acccepted into the coveted Manhattan School of Music. You are excited about the opportunity to develop as an artist, and the network of other talented artists the program will connect you with, but you are concerned about the cost. Fortunately you have a skill that can make you money while living in one of if not the most expensive cities in the United States. You also will have access to the biggest stage in the world...no, not Carnegie Hall...the NYC Subway system!

The MTA website provides data on the number of Entries and Exits for each turnstile in each station by day. Each file contains data for one week, and data is updated weekly. Since class at the MSM started last week, I looked at the most recent week's data (2017-01-14) to see where are the best stations for a musician to perform to gain themost exposure, and hopefully make the most money!

We start by reading in the data:

[Insert Code Snippet and image of .head()]

We can see the columns and types available with df.info():

[Insert df.info()]

This data is unique at the turnstile level. Each record contains a cumulative count of Entries and Exits for a turnstile at a station on a single day of the week and is updated every 4 hours. There is metadata about each station including how many lines it serves and the line the station originally belonged to when the subway lines were first built. I want to test the the assumption that a station that is serves more lines will have more entries than a station with less. We'll look at entries because we want to know when people will be in the subway station not leaving!

I get the number of entries by using the pandas method diff(), then remove outliers. This data is a bit messy. It ishard to aggregate in a uniform way because different turnstiles are audited at different times, and the counters will randomly reset. In order to resolve this issue, I assume at a station's busiest period 1 person can get through a turnstile a second,and therefore 

Now that the data is clean, let's look at a histogram of the median number of riders per line-number group.

[Insert histogram image]

We can see that our assumption is not necessarily true. There is a peak in the distribution of Entry counts by Number of Lines at a station at 8 Lines per station. But Let's take a look at the distribution of stations with a scatter plot and distinguish between weekend and weekday.

[Insert Scatter Plot]



