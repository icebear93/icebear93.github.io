---
layout: single
title:  "Data Crawling 1"
categories: ML/DL


author_profile: false
typora-root-url: ../
---

# What is Data Crawling?

Data crawling, also known as web crawling or web scraping, is the process of automatically gathering information from websites on the internet. It involves systematically navigating through web pages, extracting relevant data, and storing it for further analysis or use.

Data crawling is typically performed by software programs called web crawlers or bots. These crawlers visit web pages, follow hyperlinks, and retrieve the content of the pages. They can be designed to scrape various types of data such as text, images, videos, links, and other structured or unstructured information.

Here's a step-by-step overview of how data crawling typically works:

1. Start URL: The crawler begins by specifying one or more starting URLs from which it will initiate the crawling process.
2. Retrieval: The crawler retrieves the HTML content of the initial URL(s) and parses it to extract relevant data and identify additional links to follow.
3. Following links: The crawler follows the discovered links to visit other web pages. This process is repeated recursively to crawl through multiple layers of linked pages.
4. Data extraction: Upon reaching each web page, the crawler extracts the desired data using techniques such as HTML parsing, XPath, regular expressions, or other data extraction methods specific to the website's structure.
5. Storage: The extracted data is typically stored in a structured format, such as a database, spreadsheet, or JSON/XML files, for further processing, analysis, or integration into other systems.



## Basic Python syntax and grammar for Crawling

(Most of the explanations will be given with examples)

### Regular expression

``` python
import re

re.search([^pattern], string) # get the opposite of the pattern
re.search(^pattern, string) # (mostly used in search function) check if the string starts with the pattern
re.search("hello$", "hihello") # check if it ends with hello
re.match("hi | hello", "hi") # check if it contains 'hi' or 'hello'
[0-9]+ # number repeats more than once
[0-9]* # number repeats more than 0
re.match("a*b", "b") # a can be repeated from 0 to infi, however b should end the string
re.match("ab?c", "ab") # b can be repeated for 0 or 1
re.match("a.c", "ac") # check if there is a number or character at the position . 
re.match("(hi){2}", "hihiabcd") # hi should be repeated twice and () specifies what to repeat
re.match("[0-9]{3}-[0-9]{4}-[0-9]{4}", "010-1234-56789")  # this matches for it only reads data till 8, to make sure there is no exception, consider adding 'if' 
re.search("\d+ \*+ \d+", "3 ** 2") # if you need to use a special character itself in a regular expression, you use the backslash
m = re.match("(\d+)-(\d+)-(\d+)", "010-1234-5678") # grouping functionality: when using parentheses in a regular expression, they create a group. Parentheses are simply used to represent a group and are not considered as part of the pattern.
m.group(3) -> '5678'
m.group(0) or m.group() ->'010-1234-5678'  (get all)
m.groups() # When using the m.groups() method, the parts of the pattern that have been grouped using parentheses in the regular expression are returned as a tuple.
m = re.match("(?P<nationcalcode>\d+)-(?P<ln>\d+)-(?P<sn>\d+)-(?P<tn>\d+)", "82-010-1234-5678")
 # In regular expressions, you can define pattern names using the format (?P<name>pattern). Both m.group('ln') and m.group(2) retrieve the matched substring corresponding to the second group in the regular expression. When you use the re.match() function to compare the regular expression with the given string, if a matching part is found, the m object is returned. Subsequently, both m.group('ln') and m.group(2) retrieve the substring that corresponds to the second group, which is "010" in this case.
re.sub(pattern, "replacement_string" or function, string) # This function is used to substitute the matched substrings that correspond to the specified regular expression pattern with a different string or the result of a function in the given input string.
```

| Regular Expression |                                                         |
| ------------------ | ------------------------------------------------------- |
| \d                 | match number                                            |
| \D                 | match that is not number                                |
| \s                 | match whitespace or character                           |
| \S                 | match that is not whitespace or character               |
| \w                 | match number or lcharacter                              |
| \W                 | match that is not number or character                   |
| Dot(.)             | match everything except '\n'                            |
| *                  | match if the letter in front of '*' repeats more than 0 |
| +                  | match if the letter in front of '+' repeats more than 1 |



### url lib.request

``` py
import urllib.request as ur

data = ur.urlopen(url) 
# get url and open 

img = data.read() 
with open('mypic.png', mode = 'wb') as f:
  f.write(img)
# get url image and save as 'mypic.png'

data = data.decode('utf-8')
# make 'data' comprehensible
```



### Selenium

```py
pip install selenium # num 1 web scraper
from selenium import webdriver
driver = webdriver.Chrome("/Users/jsp/drv111/chromedriver.exe") # when you use chrome ; you also have to install chrome driver

driver = webdriver.Safari() # when you use safari

url = "https://www.melon.com/chart/index.htm"
driver.get(url) # read url page
html = driver.page_source # get contents from url
soup = BeautifulSoup(html, "html.parser")
```



### BeautifulSoup : html parser

``` py
from bs4 import BeautifulSoup

soup = BeautifulSoup(data, 'html.parser')
# prep stage for data parsing

soup.find("title")
# Extracts the value inside the title tag. When using find, it starts from the top and returns the first matching element only.

soup.find("description").string
# Extracts and outputs the contents of the string part within the description tag.

weather = re.sub("<br />", "", weather)
# Uses the re.sub function to modify and tidy up the text in the 'weather' variable as desired. In this case, the code substitutes '<br />' part to ''.

soup.find_all("wf")
# Outputs all matching results. The result is stored in a list data structure.

soup.find('html').find('body').find('ul').find('li').find('a').string
# It is possible to narrow down the search by using this method to find elements step by step.

li.attrs['href']
# Extracts the value of the 'href' "attribute"

soup.select_one("#fr-list")
# When searching by ID, use 'select_one'. It only returns the first match. The ID must be preceded by a # sign. This is the point that differs from 'find'.

soup.select_one("#ve-list > li") 
# Narrow down the search by specifying the child elements with the '>' sign.

soup.select_one("#ve-list > li[data-lo='us']")
# It is possible to narrow down the search even further by specifying attribute values. It provides greater flexibility.

soup.select_one("#ve-list > li.red")
# Accessing elements by class. Use a dot to reference the class.

soup.select("#ve-list > li")
# Performs a similar function as 'find_all'. The result is stored in a list data structure.



```



---

# Tips and scribbles

*  My preference; I use re.findall for regular expressions and soup.select for bs.

* This is a sample code for you to grasp the concept of crawling

  ``` py
  # get bbc link
  bbc='https://www.bbc.com/news'
  data=urllib.request.urlopen(bbc).read()
  soup=BeautifulSoup(data,'html.parser')
  links=soup.find_all('link')
  for i in links:
      print(i.attrs['href']) #모든 링크 출력
  ```

  ``` py
  # get bbc article title and contents
  ukraine='https://www.bbc.com/news/world-europe-62884668' #우크라이나 전쟁 bbc 뉴스기사
  data=urllib.request.urlopen(ukraine).read()
  soup=BeautifulSoup(data,'html.parser')
  print(soup.title.string) #기사제목
  text=soup.find_all('p')
  for i in text:
      print(i.string) #글 출력
  ```

  ``` py
  # get coaching staffs list for Dusan Bears
  
  url = "https://www.doosanbears.com/players/coachStaff"
  
  res = urllib.request.urlopen(url)
  data = res.read()
  data = data.decode('utf-8')
  
  soup = BeautifulSoup(data, 'html.parser')
  
  
  # list_coach 리스트에 '이름(등번호)'로 요소 추가
  coach = [str(co) for co in soup.find_all("p") if co.find("strong")]
  list_coach = []
  
  pat = re.compile("<p><strong>(\d*)</strong>([가-힣]+)</p>")
  for c in coach:
      list_coach.append(pat.sub("\g<2>(No.\g<1>) ", c))
      
      
  # link_coach 리스트에 코칭스태프 소개 링크 마지막 숫자 추가 
  links = soup.find_all("a")
  link_coach = []
  for li in links:
      li_href =  li.attrs['href']
      if re.match("/players/coachStaff/\d+", li_href):
          link_coach.append(li_href.split('/')[-1])
  
          
  # 결과 출력      
  for i in range(len(link_coach)):
      url_tot = url + '/' + link_coach[i]
      print(list_coach[i], url_tot)
  ```

  ``` py
  # you can make a list using the code below and use pandas to save as excel
  
  song_data = []
  rank = 1
  for i in range (50):
      title = songs[i].select("a.title")[0].text.strip()
      singer = songs[i].select("a.artist")[0].text
      song_data.append(['Genie', rank, title, singer])
      rank += 1
  
  import pandas as pd
  
  col = ['서비스', '순위', '타이틀', '가수']
  
  df = pd.DataFrame(song_data, columns = col)
  
  df.to_excel("genie.xlsx", index = False)
  
  ```

  

* difference between string and text in bs

``` py
print(songs[1].select("span > a")[0].string)
print(songs[1].select("span > a")[1].text)
#string 과 text의 차이점 
#string은 태그 안에 다른 태그가 추가로 있거나 태그 안에 아무것도 없는 경우, None으로 출력 받고 싶을 때 쓴다
#text는 문자열만 출력하게 해준다. 내용이 없으면 그냥 공란으로 출력된다.
```



---

# Reference

* https://devjs9.tistory.com



