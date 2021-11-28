---
title: Ethics of Webscraping
nav: Webscraping ethics
topics: ethical considerations, permissions, scraping potentially sensitive data
description: >
    This section covers the ethical and regulatory guidelins for webscraping for research.   
---

## Getting started  

Prior to starting any webscraping project you will need to understand the potential ethical issues and apply for <a href='https://www.griffith.edu.au/research/research-services/research-ethics-integrity' target="_blank">Griffith ethics approval</a>.

As web pages have different levels of access and different tupes of information you do need to think about ethical concerns before you scrape for data.   the pages you wish to use should have their condiditions for scraping available for you to access. prior to scraping you need to think about the following aspects


## Before scraping

Find out if the data is freely publically available. 
To find this out check the permissions as set by the page owners, find and read the terms and conditions, look for an API and use the Robots.

Robots
'A robots.txt file tells search engine crawlers which URLs the crawler can access on your site.' more practically, adding /robots.txt to a web address will tell you the page settings for web scraping. 

eg; to find the permissions for a griffith university at /robots.txt to the address  griffith.edu.au/robots.txt this will tell you what data you can and cannot scrape.

more info on Robots can be<a href='https://developers.google.com/search/docs/advanced/robots/intro' target="_blank"> found here</a>.

<h2>Activity</h2>
<p class="p_border"> In this exercise we would like you to add the /robots.txt suffix to variety of you favourite web pages to see their scraping permissions. <br>

For example, look up gumtree.com.au/robots.txt and we can see that most elements are off limits, however if you search for british motorcycle magazine Visordown, you will find most applications are allowed www.visordown.com/robots. <br>

Over the next few minutes check the permissions of a variety of pages you use and let us know what you find. <br> </p>

## Ethical consderations

Be sure to only scrape pages you specified on your ethics application forms.  Ethics forms are <a href='https://www.griffith.edu.au/research/research-services/research-ethics-integrity' target="_blank">found here</a>.

Are you wanting to scrape social media pages or a forum? IS the forum public or private? can you access the materails with outa login? 
For the data you wish to find; are there people, living or dead, involved?  could their identity or privacy be compromised? is the page you wish to scrape paywalled?  is the group private or public? 
If you are wondering if you should really scrape a page for data, the answer is you probably shouldn't. 

Web Scraping for data is  
- excellent for publically available content 
- probelmatic where there are people involved - as there are both privacy issues and ethical concerns with this. 
- not so cool to try and scrape data from behind a paywall or on private pages or from social media groups or forums


The legality of web scraping is still a grey area. Many webpages forbid scraping in their ToS, but this is not generally enforceable. Issues with data scraping generally occur where the scraped data is used for profit.  Researchers need to remain alert and be aware of restrictions on data scraping and know of the implications of scraping in legal cases.

The following links provide information on cases where companies have sued webscrapers for accessing and using their data. 


<a href='https://techcrunch.com/2020/10/01/facebook-sues-two-companies-engaged-in-data-scraping-operations/' target="_blank"> https://techcrunch.com/2020/10/01/facebook-sues-two-companies-engaged-in-data-scraping-operations/</a>.

<a href='https://jaxenter.com/data-scraping-cases-165385.html' target="_blank"> https://jaxenter.com/data-scraping-cases</a>.

<a href='https://www.informationweek.com/social/linkedin-sues-after-scraping-of-user-data' target="_blank"> https://www.informationweek.com/social/linkedin-sues-after-scraping-of-user-data</a>.



--------
## How to stay out of trouble when scraping

RESEARCH ETHICS
Only scrape pages you have ethics approval for.  You will need ethics approval to publish the materials from the pages scraped. If in doubt contact <a href='https://www.griffith.edu.au/research/research-services/research-ethics-integrity' target="_blank">Griffith Research Ethics</a>, or <a href='https://www.griffith.edu.au/copyright-matters' target="_blank">Griffith Copyright</a>.

WHERE YOU CAN, USE THE API
Some websites have their own APIs built specifically for you to gather data without having to scrape it. This means that you’d be doing it according to their rules; you have been authorized to get the information. So, if there’s an API, use it instead of scraping.

ROBOTS.TXT 
before you scrape a page make sure you check what is allowed using /robots.txt. This will tell you what is or is not allowed to be scraped from their pages.  
 This is part of the Robots Exclusion Protocol (REP) which are a group of web standards created as a way to regulate how robots crawl the web.

READ THE TERMS AND CONDITIONS
yes, actually read them.  this will tell you what the page allows and the rules for page use.  The terms and conditions are there for a reason, see what they say and abide. 

DONT SCRAPE PERSONAL INFO
just dont,. find some other means to get the information. If you are are all unsure check with Ethics before you start, folks dont tend to react well if their personal data and privacy are breached. If you really, really, need to get this data be make sure all the content you use is depersonalised and saved securely. Attend a sensitive data workshop, imagine its your families data, then rethink your choices. 

CONSIDER THE WEBPAGES OWNERS AND USERS
when you scrape a page you are essentailly attacking the server, this can lead to the page going down, causing poor user experiences and generating bad press for the owners. 
if you scrape, scrape in off peak times, and space out the requests, we go into this aspect of scraping though the tutorial.  you dont want your research to be confused with a DDos attack! 

IDENTIFY YOURSELF AND ASK FOR PERMISSION
if you are going to scrape a page let the page adminstrators know you are going to do it, this does not necessarily mean telling them directly but to add a a User-Agent string with your details to the code. That way the page will know who is accessing the data. Contacting  the page directly to ask would not hurt either. Be courteous, its free. Remember you are scraping for data that does not belong to you, was not colleccted by you and may have taken years to gather. 



### references

<a href='https://www.empiricaldata.org/dataladyblog/a-guide-to-ethical-web-scraping' target="_blank"> https://www.empiricaldata.org/dataladyblog/a-guide-to-ethical-web-scraping</a>

<a href='https://monashdatafluency.github.io/python-web-scraping/section-5-legal-and-ethical-considerations/' target="_blank"> https://monashdatafluency.github.io/python-web-scraping/section-5-legal-and-ethical-considerations/</a>

<a href='https://towardsdatascience.com/ethics-in-web-scraping-b96b18136f01' target="_blank"> https://towardsdatascience.com/ethics-in-web-scraping/</a>

<a href='https://robertorocha.info/on-the-ethics-of-web-scraping/' target="_blank"> https://robertorocha.info/on-the-ethics-of-web-scraping/ </a>

<a href='https://www.octoparse.com/blog/10-myths-about-web-scraping' target="_blank"> https://www.octoparse.com/blog/10-myths-about-web-scraping/ </a>

