---
title: Programmatically scrape using python 
nav: Python
topics: Python; Beautiful Soup; Selenium
description: >
    Why use python 
    Useful python packages for webscraping 
---

    Beautiful soup is used for extracting and parsing (breaking down) webpage content;  selenium is used to navigate  webpages and input data into text fields; scrapy is a framework for webscraping, look into it once you become comfortable with coding. 

## Beautiful Soup

Beautiful soup is useful for scraping all content of a website, this includes the html content.

```python
import requests
from bs4 import BeautifulSoup

quotes_url = 'https://www.quotes.toscrape.com'
html_text = requests.get(quotes_url).text
quotes_soup = BeautifulSoup(html_text, 'html.parser')
```


## Selenium

