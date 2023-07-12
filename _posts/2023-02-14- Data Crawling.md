---
layout: single
title:  "Data Crawling 1"
categories: Data Crawling


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

### Regular expression

``` python
```

| 정규표현식 | 설명                                                         |
| ---------- | ------------------------------------------------------------ |
| \d         | 숫자와 매치                                                  |
| \D         | 숫자가 아닌 것과 매치                                        |
| \s         | whitespace 문자와 매치, 맨 앞의 빈 칸은 공백문자를 의미한다. |
| \S         | whitespace 문자가 아닌 것과 매치                             |
| \w         | 문자+숫자와 매치                                             |
| \W         | 문자+숫자가 아닌 문자와 매치                                 |
| Dot(.)     | 정규 표현식의 dot메타 문자는 줄바꿈 문자인 \n을 제외한 모든 문자와 매치됨을 의미한다. |
| 반복(\*)   | ca*t : *문자 바로 앞에 있는 a가 0번 이상 반복되면 매치       |
| 반복(+)    | ca+t : +문자 바로 앞에 있는 a가 1번 이상 반복되면 매치       |



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
pip install selenium # 웹 스크래핑 1순위 도구
from selenium import webdriver
driver = webdriver.Chrome("/Users/jsp/drv111/chromedriver.exe") #크롬 사용시

driver = webdriver.Safari() #사파리 사용시

url = "https://www.melon.com/chart/index.htm"
driver.get(url) # url 페이지를 읽어옴
html = driver.page_source #url에서 글 가져옴
soup = BeautifulSoup(html, "html.parser")
```



### BeautifulSoup : html parser

``` py
from bs4 import BeautifulSoup

soup = BeautifulSoup(data, 'html.parser')
# prep stage for data parsing

soup.find("title")
# title 태그 안의 값을 추출/ find를 쓰면 위에서 부터 차례로 내려가다가 첫번째로 일치하는 부분만 출력 
soup.find("description").string
# string 부분만 깔끔하게 출력
weather = re.sub("<br />", "", weather)
# re.sub함수를 이용한 weather 내의 글 내가 원하는 데로 수정 및 정리
soup.find_all("wf")
# 일치하는 결과물 전체를 출력, 결과의 자료구조는 list
soup.find('html').find('body').find('ul').find('li').find('a').string
# 이런식으로 범위를 좁혀서 사용 가능함
li.attrs['href']
# href 속성값 추출
soup.select_one("#fr-list")
# id 검색할때는 select_one 사용. 가장 첫번째 매치만 출력. id 앞에는 # 붙여야함. find와 다른점임
soup.select_one("#ve-list > li") 
# 자식에 해당하는 부분을 > 로 표시해서 narrow down 가능함
soup.select_one("#ve-list > li[data-lo='us']")
# 이런식의 narrow down 도 가능. 자유도가 높음
soup.select_one("#ve-list > li.red")
# class 로 접근하기 -> class 참조는 점기호를 이용하여 참조
soup.select("#ve-list > li")
# find all과 같은 역할. 자료구조가 List


```



---

# Tips and scribbles

* click event can be triggered by using selenium

---

# Reference

* 



