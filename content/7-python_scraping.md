---
title: Programmatically scrape using python 
nav: Python
topics: Python; Beautiful Soup; Selenium
description: >
    Why use python
    Useful python packages for webscraping 
---

## Python for webscraping
Python is well suited for programatically scraping data from websites. There are three major packages used to webscraping in python.<br>
**Beautifulsoup** is used for extracting and parsing (breaking down) webpage content from static pages <br> 
**selenium** is used to navigate webpages, input data into text fields, take screenshots and interact with dymanic pages <br>
**scrapy** is a framework for webscraping, look into it once you become comfortable with coding. We will not work with scrapy in the workshop, however, <a href='https://librarycarpentry.org/lc-webscraping/04-scrapy/index.html' target='_blank'>this </a> workshop offers a nice overview.

## Beautiful Soup

Beautiful soup is useful for scraping all content of a website, this includes the html content.
To get started we need to import requests, this package will return a http response from the page we are interested in scraping.
We will also import BeautifulSoup from the bs4 package, and import selenium.

```python
import requests
from bs4 import BeautifulSoup
import selenium

quotes_url = 'https://quotes.toscrape.com/' 
html_text = requests.get(quotes_url).text 
quotes_soup = BeautifulSoup(html_text, 'html.parser')

print(quotes_soup)
```

First we created a variable called quotes_url, this is the url or webpage that you want to scrape. 
Then we pass it to the requests function get, which gets a response from the webpage and returns all the html text back as a single chunk. You can see the output of this by running "print(html_text)" in your python console.
Now we can use beautiful soup to parse this into something that is readable, in this case html content. Run "print(quotes_soup)". This is now the same html as is visible when we use a browser to inspect the webpage. You can copy this text, save it as .html and then open it using your web browser. It will only contain the text, the links will not work. This is because we have only scraped the data from the main page, we have not scraped any of the data from the links. Also, it will not look pretty, again, this is because we have not collected the website code that dictates its style.

Now that we have scraped all the text from the main page of quotes to scrape, we should collect the specific information that we are after.

Collecting specific information can be easy if there are html tags for it. For example, we can extract quotes using their tag.

Lets inspect a quote using our browser. The following image shows that the quotes sit within the body, then under the span tag.
{% include figure.html img="quotesTag.png" alt="quotes tag"  width="75%" %}

We can use the tag and class to access quotes. This will get the first quote.


```python
quote = quotes_soup.find_all('span', class_='text')

print(quote)
```
This has returned us a list with all the quotes on the first page. We still have some html code that we are probably not interested in. 
We can access the text of an individual quote using the .text command. We will subset our quote list to the first element and return the text. Remember [] are used to subset a list, and 0 will return the first element in the list quote.

```python
print(quote[0].text)
```
Lets retrieve the text only for the quotes. We will use a loop to go through the list. We will add the quote text to a new list called quotes.


```python
quotes = [] # create a new empty list to append the text to at the end of each loop iteration
for i in quote:
    quotes.append(i.text)

print(quotes)
```
  
That looks good.

## Challenge
Use your web browser to inspect the authors and figure out how you can get their names.

<details style="border:3px; border-style:solid; border-color:#000000; padding: 1em;"><summary><h2>Solution</h2></summary>
<p>

Lets you our web browser to inspect author.

{% include figure.html img="authorTag.png" alt="authors tag"  width="75%" %}
</p>
<p>
```python
author = quotes_soup.find_all('small', class_='author')

authors = []
for i in author:
    authors.append(i.text)

print(authors)
```
</p>
</details>

Now we need to scrape the quotes from all of the pages.
First we need to figure out how to move to the next page, use your browser to inspect the next page button.

{% include figure.html img="href.png" alt="next page"  width="75%" %}

It contain a href tag. This is a url, although it does not include the base url: https://quotes.toscrape.com. We can use this url to move to the next page, then we can scrape data from it. If we start at 1 page, scrape data, move to page 2 scrape data, ect, until we finish at the last page then we will have scraped all pages.
So...... how do we do this?

First we need to create a list that contains the url's for all the pages. i.e. ["https://quotes.toscrape.com/page/1/","https://quotes.toscrape.com/page/2/","https://quotes.toscrape.com/page/3/"]
Second, we can use the list of url's to loop through each page and collect its html content and add it to a list. i.e. ["html content page 1","html content page 2","html content page 3"]
Finally we can extract the individual quotes and authors from the list of html content.
```python
pages = [] 
for i in range(0,20):
    page = "https://quotes.toscrape.com" + '/page/' + str(i) + '/' # create a string of the url, with each loop the page number increases by one 
    pages.append(page) # write each url to a string

print(pages)

# lets create a list containing all the html content for each author and each quote
quote_soup = []
author_soup = []
for i in range(1,len(pages)):
    quotes_url = pages[i] 
    html_text = requests.get(quotes_url).text 
    quotes_soup = BeautifulSoup(html_text, 'html.parser')
    quote = quotes_soup.find_all('span', class_='text')
    author = quotes_soup.find_all('small', class_='author')
    quote_soup = quote_soup + quote
    author_soup = author_soup + author   

print(author) 

authors = []
quotes = []
for i in range(1,len(author_soup)):    
    authors.append(author_soup[i].text)
    quotes.append(quote_soup[i].text)

print(authors)
```

Lets create a wordcloud of all the quotes we scraped, because, well, science!!!

```python
#pip install wordcloud
from wordcloud import WordCloud
import matplotlib.pyplot as plt # used to plot the wordcloud

# Create and generate a word cloud image of quotes
quotes=" ".join(map(str,quotes)) # turns the list of quotes into a single string of all quotes i.e. ['a', 'b', 'c'] -> 'a b c'
wordcloud = WordCloud().generate(quotes)

# Display the wordcloud image
plt.imshow(wordcloud, interpolation='bilinear')
plt.axis("off")
plt.show()

```

{% include figure.html img="Figure_1.png" alt="next page"  width="75%" %}

Often we're interested in scraping data that is associated with specific tags, such as a Twitter #tag. 
Lets scape quotes based on their tags.

{% include figure.html img="Quotes_tags.png" alt="next page"  width="75%" %}

Lets inspect the tag 'inspirational' to figure out how we can scrape it.

```html
<a class='tag' href='/tag/inspirational/page/1/'>inspirational</a>
```
Its an 'a' tag. This is a relative URL path. We can add the relative URL path to the quotes home page URL.
Paste this into your browser "https://quotes.toscrape.com/tag/inspirational/page/1". It displays all quotes with the inspirational tag. Notice that there is a next button at the bottom of the page, there's multiple page containing inspirational quotes.
We can reuse most of our previous code, all we really need to change is the URL.

```python
pages = [] 
for i in range(1,2):
    page = "https://quotes.toscrape.com" + '/tag/inspirational/page/' + str(i) + '/' # create a string of the url, with each loop the page number increases by one 
    pages.append(page) # write each url to a string

inspirational_soup = []
for i in range(0,len(pages)):
    quotes_url = pages[i] 
    html_text = requests.get(quotes_url).text 
    quotes_soup = BeautifulSoup(html_text, 'html.parser')
    inspirational_soup = quotes_soup.find_all('span', class_='text')

inspirational_quotes = []

for i in range(1,len(inspirational_soup)):    
    inspirational_quotes.append(inspirational_soup[i].text)

print(inspirational_quotes)

```
We have scrapped all the quotes with the tag 'inspirational'.


Sometimes we might need to interact with the webpage. This could be to click the next button, or we might want to search for a particular item. In these cases we need to programatically interact with the webpage, this is where selenium comes in handy.  

## Selenium
Selenium is used to ineract with dynamic webpages.
To use selenium you will need a webdriver. You can get a webdriver for chrome, although it can be difficult to use. I would suggest using the <a href='https://github.com/mozilla/geckodriver/releases' target='_blank'>firefox webdriver</a>
If you need to use the Chrome webdriver, make sure it is the same version as chrome. Here is setup and download <a href='https://chromedriver.chromium.org/' target='_blank'>instructions.</a>


Lets import selenium and webdriver to run the webpage in. We will also need to set up a webbrowser for selenium to run in.

```python
import selenium
from selenium import webdriver

driver = webdriver.Firefox()
```

A new firefox window will open when we run the above. This window is used to interact with the webpage.

```python
quotes_url = 'https://quotes.toscrape.com/'

driver.get(quotes_url)
```

Now lets use some xpath to click the next button to more onto the next page

```python

driver.find_element_by_xpath('//span[text()="→"]').click()
```
We've used selenium to click the next page button. 

Lets pull the quotes from the first page. We will do this the selenium way.

```python

import selenium
from selenium import webdriver

driver = webdriver.Firefox()

quotes_url = 'https://quotes.toscrape.com/'

driver.get(quotes_url)

quotes = driver.find_elements_by_class_name('text')
for quotes_text in quotes:
    print(quotes_text.text)

```

Now we can get the quotes from every page using selenium.

```python

driver = webdriver.Firefox()
quotes_url = 'https://quotes.toscrape.com/'
driver.get(quotes_url)

quotes = []
for i in range(1,20):
    q1 = driver.find_elements_by_class_name('text')
    quotes.append(q1)
    driver.find_element_by_xpath('//span[text()="→"]').click()

for quotes_text in quotes:
    print(quotes_text.text)

```