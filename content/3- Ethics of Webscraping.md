---
title: Ethics of Webscraping
nav: Content
topics: ethical considerations, permissions, scraping potentially sensitive data
description: >
    This section covers the ethical and regulatory guidelins for webscraping for research.   
---

## Getting started  

Webscraping is using code, an API or web based add on to scrape individual pages for data. This is different from web crawling where you are scraping the whole web for similar papges.

As web pages have different levels of access and different tupes of information you do need to think about ethical concerns before you scrape for data.   the pages you wish to use should have their condiditions for scraping available for you to access. prior to scraping you need to think about the following aspects


## Ethical consderations

Before scraping-
find out if the data is freely publically available
are wanting to scrape social media pages or a forum? 

find the permissions as set by the page owners, you can find this using the /robots.txt add on. 

for the data you wish to find; are there people, living or dead, involved?  could their identity or privacy be compromised? is the page you wish to scrape paywalled?  is the group private or public? 


API?
written permissions

Web Scraping for data is  
- excellent for publically available content - 
- probelmatic where there are people involved - as there are both privacy issues and ethical concerns with this. 
- not so cool to try and scrape data from behind a paywall and so on

examples of webscraping gone bad - 







--------

## good practice/bad practice

THE API WAY IS OFTEN THE BEST WAY
Some websites have their own APIs built specifically for you to gather data without having to scrape it. This means that you’d be doing it according to their rules; you have been authorized to get the information. So, if there’s an API, use it instead of scraping.

RESPECT THE ROBOTS.TXT
Also known as Robots Exclusion Standard, the robots.txt file is what indicates the web-crawling software where it is allowed (or not allowed) within the website. This is part of the Robots Exclusion Protocol (REP) which are a group of web standards created as a way to regulate how robots crawl the web.

READ THE TERMS AND CONDITIONS
This is the main way the website owner tells you the rules. Yes, it’s easier to just click “I agree” or “I accept” and hope for the best. Remember they wrote those for a reason. They are talking to you, listen to what they have to say.

BE GENTLE
The process of scraping can be pretty harsh on the server, and aggressive scraping can sometimes lead to functionality issues, generating a bad user experience for human users. So, make a habit to do the scraping off-peak hours. And don’t forget to space out the requests so the website’s owner won’t confuse your scraping for a DDoS attack.

IDENTIFY YOURSELF
The website’s administrator may notice some unusual traffic happening. Manners come first, so let them know who you are, your intentions, and how to contact you for more questions. You can do this by simply adding a User-Agent string with your information, so they will be able to see it. Is that simple.

ASK FOR PERMISSION
Some basic human courtesy is always appreciated. They have something that you want, be courteous and ask before assuming the information is free for you to take. Remember: the data doesn’t belong to you.


### references
https://www.empiricaldata.org/dataladyblog/a-guide-to-ethical-web-scraping
https://monashdatafluency.github.io/python-web-scraping/section-5-legal-and-ethical-considerations/
https://towardsdatascience.com/ethics-in-web-scraping-b96b18136f01
https://robertorocha.info/on-the-ethics-of-web-scraping/
