---
title: Programmatically scrape using python 
nav: Python
topics: Python; Beautiful Soup; Selenium
description: >
    Why use python </br>
    Useful python packages for webscraping 
---

Beautiful soup is used for extracting and parsing (breaking down) webpage content;  selenium is used to navigate  webpages and input data into text fields; scrapy is a framework for webscraping, look into it once you become comfortable with coding. 

## Beautiful Soup

Beautiful soup is useful for scraping all content of a website, this includes the html content.

To get started we need to import requests, this package will let python connect to the webpage we want to access.
We will also import BeautifulSoup from the bs4 package, and import selenium.

```python
import requests
from bs4 import BeautifulSoup
import selenium

quotes_url = 'https://www.quotes.toscrape.com' 
html_text = requests.get(quotes_url).text 
quotes_soup = BeautifulSoup(html_text, 'html.parser')
```

# quotes_url = 'https://www.wikipedia.org/'

First we created a variable called quotes_url, this is the url or webpage that you want to scrape. 
Then we pass it to the requests function get, which gets a response from the webpage and returns all the html text back as a single chunk. You can see the output of this by running "print(html_text)" in your python console.
Now we can use beautiful soup to parse this into something that is readable, in this case html content. Run "print(quotes_soup)". This is now the same html as is visible when we use a browser to inspect the webpage. You can copy this text, save it as .html and then open it using your web browser.

Now that we have scraped all the text from the website, we should collect the information that we are after and discard the rest. 

## Challenge
Use your web browser to inspect the quotes to scrape webpage 'https://www.quotes.toscrape.com' and figure out how you can get the authors names of the quotes.
There is multiple ways this can be achieved.

<details style="border:3px; border-style:solid; border-color:#000000; padding: 1em;"><summary><h2>Solution</h2></summary>
<p>



</p>
</details>

## Selenium

