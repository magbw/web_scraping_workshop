---
title: API's
nav: API's
topics: What are API's; Why use API's; Do to access API's
description: >
      Many websites offer API's for retrieving their content. If a website has an API, use it.
---

## What is an API? (Application Programming Interface)
API is the acronym for Application Programming Interface, which is a software tool that allows two applications to talk to each other. In the case of collecting web data, this is a database that stores the webpages data and something that can read, display or store that data (i.e. a webbrowser, a programming language such as python or some other program on your computer, or a cloud based application).

If a website has an API, then use it. Generally, it won't let us collect data that your not allowed to collect, and its by far the easiest way to collect a websites data.

Check here for (by no means comprehensive) lists of websites with API access:

<a href='https://apilist.fun/' target='_blank'>API list</a>

<a href='https://github.com/public-apis/public-apis' target='_blank'>Public APIs</a>

Guardian.co.uk <a href='https://open-platform.theguardian.com/' target='_blank'>API</a>

Australian news sources <a href='https://mediastack.com/sources/australia-news-api' target='_blank'>API</a> 



## How do we use an API

You use URL's to collect a websites data with an API, this is refered to as an `API request`. There will be certain sections of the API request that can be manipulated to collect specific data. You will need to check out the websites API documentation for details.

Once you have a formulated a suitable API request, you will need to pull the data (i.e. get it onto your computer). This is most commonly achieved using a programming language. We generally use  R or Python.  If you are comfortable with either of these languages check these guides.

<a href='https://cran.r-project.org/web/packages/httr/vignettes/api-packages.html' target='_blank'> r-project</a>

<a href='https://www.dataquest.io/blog/python-api-tutorial/' target='_blank'> Python API Tutorial </a>

Some commonly used websites, such as Twitter, have packages that can be used to interact with the API. Packages that use Twitter API's:

R: rtweet 

python: Tweepy

### Twitter API
You will need to setup a <a href='https://developer.twitter.com/en/products/twitter-api/academic-research' target='_blank'>twitter academic account</a> to use their API.


## Lets try it ourselves
NatureServe is a biodiversity conservation group that classifies, maps and sets biodiversity conservation goals.
They have a huge range of biodiversity data for the Americas. There are a few pieces of information we need to create a get URL. 
*This tutorial has been developed using the Mozilla Firefox browser, for ease of use we suggest you use this browser for coding and development.* <a href='https://www.mozilla.org/en-US/firefox/new/' target='_blank'> Download firefox here <a/>

### API request
First we need to formulate an API request. 
This can consist of the following:
* **endpoint** Think of an endpoint as the base URL for a website
* **relative path** for the dataset of interest 
* **an id** if we're after a specific case/species/type
* **token** access tokens may be required

All this information can usually be found in the websites API documentation
https://explorer.natureserve.org/api-docs/

NatureServe API endpoint:
https://explorer.natureserve.org/

Relative path to get data for species data:
api/data/taxon/

The id for a specific species:
ELEMENT_GLOBAL.2.154701

Put it all together and paste it into your webbrowser to display the data.
https://explorer.natureserve.org/api/data/taxon/ELEMENT_GLOBAL.2.154701

If you open the API request in firefox, it displays nicely, and there is a save button to download it.

{% include figure.html img="SaveAPIfirefox.png" alt="JSON formatted in firefox" caption="JSON formatted in firefox" width="75%" %}

You can install the <a href="https://chrome.google.com/webstore/detail/json-viewer/gbmdgpbipfallnflgajpaliibnhdgobh" target="_blank">json viewer extension </a> so tht it is displayed nicely.

This is JSON formatted data, you can also pull from most API's in XML and HTML. You will most likely need to use a programming language to pull the data from the websites database onto your computer (or any other location you want to store/analyse the data).

### Pull the data into python

```python
import requests
import os
import json

url = 'https://explorer.natureserve.org/api/data/taxon/ELEMENT_GLOBAL.2.154701'
result = requests.get(url).json()

# Write the data to a json formatted text file on your computer
os.chdir('/Users/Documents/')
with open('ELEMENT_GLOBAL.2.154701.txt', 'w') as convert_file: 
     convert_file.write(json.dumps(result))

```

### Pull the data into R
```R
require(httr)
require(rjson)

url <- 'https://explorer.natureserve.org/api/data/taxon/ELEMENT_GLOBAL.2.154701'

get_request <- httr::GET(url)
results <- httr::content(get_request, as='text')
results_parsed <- fromJSON(results)
```

## Another Example with covid data

Lets have a look at another API that provides global covid-19 statistics: <a href="https://api.covid19api.com/" target="_blank">https://api.covid19api.com/</a>
Lets look at the <a href="https://documenter.getpostman.com/view/10808728/SzS8rjbc" target="_blank">documentation</a>

{% include figure.html img="covidAPI.png" alt="quotes tag"  width="75%" %}

Select python as the language and requests as the package, it will provide you the code. Unfortunately it doesn't show the code for R.

The left column contains all the different datasets we can get with API requests. Click on the default tab then "view more" button to look at some examples of the relative paths for data we can get from this API.

{% include figure.html img="allData.png" alt="quotes tag"  width="75%" %}

{% include figure.html img="relativePaths.png" alt="quotes tag"  width="75%" %}

This is the relative path from the example above: /dayone/country/:country/status/:status/live
This API request requires 2 id's, :country is the id for the target country and :status is the id for the target status.

Lets use this relative path to get the infection data for Canada from the date of first confirmed case. 

We can get a list of countries by adding country to the base URL, i.e. https://api.covid19api.com/countries. Paste the full URL "https://api.covid19api.com/countries" into you web-browser, ideally firefox (it will be far easier to read).

Use the find function click "crtl F" in the browser and a search bar will pop up, search Canada.

{% include figure.html img="canada.png" alt="quotes tag"  width="75%" %}

Our API request.
endpoint: https://api.covid19api.com
relative path: /dayone/country/:country/status/:status/live
country id: canada
status id: confirmed

https://api.covid19api.com/dayone/country/canada/status/confirmed/live

```python
import requests
import os
import json

url = 'https://api.covid19api.com/dayone/country/canada/status/confirmed/live'
result = requests.get(url).json()

# Write the data to a json formatted text file on your computer
os.chdir('/Users/Documents/')
with open('canada_covid_daily.txt', 'w') as convert_file: 
     convert_file.write(json.dumps(result))

```