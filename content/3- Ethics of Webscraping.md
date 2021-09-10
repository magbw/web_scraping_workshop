---
title: Ethics of Webscraping
nav: Webscraping ethics
topics: ethical considerations, permissions, scraping potentially sensitive data
description: >
    This section covers the ethical and regulatory guidelins for webscraping for research.   
---

## Getting started  

Webscraping is using code, an API or web based application to scrape individual pages for data. This is different from web crawling where you are scraping the whole web for similar papges.

As web pages have different levels of access and different tupes of information you do need to think about ethical concerns before you scrape for data.   the pages you wish to use should have their condiditions for scraping available for you to access. prior to scraping you need to think about the following aspects


## Ethical consderations

Before scraping-
find out if the data is freely publically available. To find this out check the permissions as set by the page owners, you can find this using the /robots.txt add on.

Be sure to only scrape pages you specified on your ethics application forms.  Ethics forms are <a href='https://www.griffith.edu.au/research/research-services/research-ethics-integrity' target="_blank">found here</a>.

Are you wanting to scrape social media pages or a forum? IS the forum public or private? can you access the materails with outa login? 
For the data you wish to find; are there people, living or dead, involved?  could their identity or privacy be compromised? is the page you wish to scrape paywalled?  is the group private or public? 
If you are wondering if you should really scrape a page for data, the answer is you probably shouldn't. 

Web Scraping for data is  
- excellent for publically available content - 
- probelmatic where there are people involved - as there are both privacy issues and ethical concerns with this. 
- not so cool to try and scrape data from behind a paywall or on private pages or from social media groups or forums

examples of webscraping gone bad - 

example of mothers group scrape






--------

## good practice/bad practice

WHERE YOU CAN, USE THE API
Some websites have their own APIs built specifically for you to gather data without having to scrape it. This means that you’d be doing it according to their rules; you have been authorized to get the information. So, if there’s an API, use it instead of scraping.

ROBOTS.TXT 
before you scrape a page make sure you check what is allowed using /robots.txt. This will tell you what is or is not allowed to be scraped from their pages.  
 This is part of the Robots Exclusion Protocol (REP) which are a group of web standards created as a way to regulate how robots crawl the web.

READ THE TERMS AND CONDITIONS
yes, actually read them.  this will tell you what the page allows and the rules for page use.  The terms and conditions are there for a reason, see what they say and abide. 

CONSIDER THE PAGES OWNERS AND USERS
when you scrape a page you are essentailly attacking the server, this can lead to the page going down, causing poor user experiences and generating bad press for the owners. 
if you scrape, scrape in off peak times, and space out the requests, we go into this aspect of scraping though the tutorial.  you dont want your research to be confused with a DDos attack! 

IDENTIFY YOURSELF AND ASK FOR PERMISSION
if you are going to scrape a page let the page adminstrators know you are going to do it, this does not necessarily mean telling them directly but to add a a User-Agent string with your details to the code. That way the page will know who is accessing the data. Contacting  the page directly to ask would not hurt either. Be courteous, its free. Remember you are scraping for data that does not belong to you, was not colleccted by you and may have taken years to gather. 



### references
- https://www.empiricaldata.org/dataladyblog/a-guide-to-ethical-web-scraping
- https://monashdatafluency.github.io/python-web-scraping/section-5-legal-and-ethical-considerations/
- https://towardsdatascience.com/ethics-in-web-scraping-b96b18136f01
- https://robertorocha.info/on-the-ethics-of-web-scraping/
- https://www.octoparse.com/blog/10-myths-about-web-scraping
