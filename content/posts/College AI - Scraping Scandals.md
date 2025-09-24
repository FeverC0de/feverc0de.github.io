---
title: College AI - Part 1 - Scraping Scandals
date: 2025-09-24
tags:
  - python
  - scraper
---
# Chapter 0 - I'm Tired Boss

Inordinate amount of boredom fell upon me, after getting tired of the usual routine of going through multiple pages just to check my cafeteria menu, I decided to do the most convenient thing. Create a chatbot that can scrape the online menu data and provide an instant answer to whether or not they have sweet potato fries! How does one go about this journey? Well your enlightenment begins my dear padawan and soon you can scrape and create your own college cafeteria answering chatbot so all your friends (now existent) think you're cool!

# Chapter 1 - Scraping everything

Some of y'all may be familiar with the `requests` library, pretty much is your first step to becoming a web content thief.  we are going to want `requests.get(url)` since that allows us to store the HTML of a whole website in a single variable.

```python
import requests

url = "https://college-name.edu"

page = requests.get(url)
```

Nice! This single block of code is enough to get everything you need out of your college main page. 

Printing out `page.content` will give us what we need!

```HTML
...
<title>icon-instagram</title>\r\n <g id="icon-instagram-Main_Circle">\r\n <g>\r\n <path d="M16,0C`
...
```

Oh... well this made no sense to me. Though, I do get some relevant information at about an Instagram icon? Okay honestly, 90% of the stuff you see in the output is useless. We're going to want to find a way to strip away all the ugly HTML fluff and get beautiful coherent words and sentences.

... To be co

