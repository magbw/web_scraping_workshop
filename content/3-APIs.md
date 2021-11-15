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

Here is the same data displayed in Chrome. You can install the <a href="https://chrome.google.com/webstore/detail/json-viewer/gbmdgpbipfallnflgajpaliibnhdgobh" target="_blank">json viewer extension </a> so tht it is displayed nicely.

```
{"elementGlobalId":154701,"circumscripConfidence":null,"classificationLevel":{"id":17,"classificationLevelNameEn":"Species","classificationLevelNameEs":"Especies","classificationLevelNameFr":"Espèce"},"classificationStatus":{"id":1,"classificationStatusDescEn":"Standard","classificationStatusDescEs":"Estándar","classificationStatusDescFr":"Standard"},"iucn":{"id":5,"iucnDescEn":"Vulnerable","iucnDescEs":"Vulnerable","iucnDescFr":"Vulnérable","iucnCode":"VU"},"nameCategory":{"id":4,"nameCategoryDescEn":"Vascular Plant","nameCategoryDescEs":"Planta vascular","nameCategoryDescFr":"Plante vasculaire","nameTypeCd":"P","nameTypeDesc":"Botanical"},"rankMethodUsed":{"id":1,"rankMethodUsedDescEn":"Legacy Rank calculation - Excel v3.1x","rankMethodUsedDescEs":null,"rankMethodUsedDescFr":null,"rankMethodUsedExternalDescEn":"Ranked by calculator","rankMethodUsedExternalDescEs":null,"rankMethodUsedExternalDescFr":null},"formattedScientificName":"<i>Hydrastis canadensis</i>","scientificName":"Hydrastis canadensis","scientificNameAuthor":"L.","primaryCommonName":"Goldenseal","relatedItisNames":"<i>Hydrastis canadensis</i> L. (TSN 18781)","uniqueId":"ELEMENT_GLOBAL.2.154701","elcode":"PDRAN0F010","conceptRefFullCitation":"Kartesz, J.T. 1994. A synonymized checklist of the vascular flora of the United States, Canada, and Greenland. 2nd edition. 2 vols. Timber Press, Portland, OR.","conceptName":"<i>Hydrastis canadensis</i>","taxonomicComments":"<i>Hydrastis canadensis</i> occurs in eastern North America and is a monotypic genus. In the most current taxonomic revision <i>Hydrastis </i>is placed in Hydrastidaceae, with one other monotypic genus, <i>Glaucidium,</i> which is restricted to Japan (Tobe 2003).","roundedGRank":"G3","conservationStatusFactorsEditionDate":"2013-04-29","conservationStatusFactorsEditionAuthors":"Oliver, L.","primaryCommonNameLanguage":"EN","recordType":"SPECIES","elementNationals":[{"elementNationalId":211679,"classifConfidence":null,"nation":{"id":225,"nameEn":"United States","nameEs":"Estados Unidos","nameFr":"États-Unis","isoCode":"US","region":"United States"},"roundedNRank":"N3","elementSubnationals":[{"elementSubnationalId":294228,"subnation":{"id":34,"nameEn":"North Carolina","nameEs":"Carolina del Norte","nameFr":"Caroline du Nord","subnationCode":"NC","dnationId":225},"roundedSRank":"S3","srank":"S3","speciesSubnational":{"elementSubnationalId":294228,"hybrid":false,"exotic":false,"native":true}},{"elementSubnationalId":621497,"subnation":{"id":29,"nameEn":"Minnesota","nameEs":"Minnesota","nameFr":"Minnesota","subnationCode":"MN","dnationId":225},"roundedSRank":"S1","srank":"S1","speciesSubnational":{"elementSubnationalId":621497,"hybrid":false,"exotic":false,"native":true}},{"elementSubnationalId":380016,"subnation":
```

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

###

Lets have a look at another API that provides global covid-19 statistics: <a href="https://api.covid19api.com/" target="_blank">https://api.covid19api.com/</a>
Lets look at the documentation: <a href="https://documenter.getpostman.com/view/10808728/SzS8rjbc" target="_blank">https://documenter.getpostman.com/view/10808728/SzS8rjbc</a>

{% include figure.html img="covidAPI.png" alt="quotes tag"  width="75%" %}

Select python as the language and requests as the package, it will provide you the code. Unfortunately it doesn't show the code for R.

The left column contains all the different datasets we can get. 

Click on the summary field and get the URL, or API call "https://api.covid19api.com/summary". The base URL is "https://api.covid19api.com/" and the relative path is "summary". Paste this URL into your web browser.

Lets look at the data we can get from this API and the relative paths that we can append to the base URL to get this data.

{% include figure.html img="allData.png" alt="quotes tag"  width="75%" %}




Lets work through getting the infection data for 14th November 2021 for Canada. First we need to figure out if we can get the daily infection rate for the country Canada.

We can get a list of countries by adding country to the base URL, i.e. https://api.covid19api.com/countries. Paste the full URL "https://api.covid19api.com/countries" into you web-browser, ideally firefox (it will be far easier to read).

Use the find function click "crtl F" in the browser and a search bar will pop up, search Canada.

{% include figure.html img="canada.png" alt="quotes tag"  width="75%" %}



```python
import requests
import os
import json

url = 'https://api.covid19api.com/countries'
result = requests.get(url).json()



url = 'https://api.covid19api.com/premium/country/testing/south-africa'
result = requests.get(url).json()

# Write the data to a json formatted text file on your computer
os.chdir('/Users/Documents/')
with open('ELEMENT_GLOBAL.2.154701.txt', 'w') as convert_file: 
     convert_file.write(json.dumps(result))

```