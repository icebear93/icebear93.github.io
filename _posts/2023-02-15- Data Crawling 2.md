---
layout: single
title:  "Data Crawling 2; how to navigate instagram using selenium"
categories: ML/DL


author_profile: false
typora-root-url: ../
---

# Click event on web using Selenium

During data crawling, automation is a critical technique that helps you save time and energy. Following example will give you an idea about how you can make a 'click' event on the web page or any other events that help you automate your data crawling process.



## Maneuvering Instagram 

(Most of the explanations will be given with examples)

### Log-in to instagram

``` python
input_box = driver.find_elements(By.CSS_SELECTOR, "input._aa4b._add6._ac4d")
# You can interact with web pages, such as logging in, clicking, and entering text, by using "# driver.find_elements(By.CSS_SELECTOR" to specify the target. Note that when you want to fetch multiple instances of the same target, you use 'elements' (plural form of element).
input_box[0].send_keys("ID") # Enter your ID
input_box[1].send_keys("PW") # enter your PW
input_box[1].submit() # Think of it as "Enter."
```



### Clicking on the first photo on Instagram and swiping right/left to navigate.

``` py
img = driver.find_elements(By.CSS_SELECTOR, 'div._aagw')
img[0].click() # Click
right = driver.find_elements(By.CSS_SELECTOR, "div._aaqg._aaqh")
right[0].click() # Right click
left = driver.find_elements(By.CSS_SELECTOR, "div._aaqf._aaqh")
left[0].click() # Left click
```



---

# Tips and scribbles

*  When others view my code, I'll simply explain it in a straightforward and clear manner. Avoid using fancy jargon like "run block" and instead say "I have defined functions. I executed the code. I converted it to Excel format."

*  CSV: Comma Separated Value format.

*  Three types of visualization: matplotlib, plotly, tableau

* counter library

  * ```py
    from collections import Counter
    
    tags_counts = Counter(tags_total) # 딕셔너리 형태로 만들어주고,  내가 추출한 내용 중에 겹치는 내용을 전부 세어줌
    tags_counts.most_common(50) # 가장 많이 사용된 탑 50 출력; 이건 리스트로 출력
    ```

* eval("['a', 'b', 'c']") -> ['a', 'b', 'c']: The eval function can quickly convert a string into a list. Caution: eval('[a, b, c]') won't work.

* A small taste of word cloud

  ``` py
  pip install wordcloud
  from wordcloud import WordCloud
  ```

  ``` py
  # korean font setting
  import platform
  
  if platform.system() == 'Windows':   # for window
      font_path = "c:/Windows/Fonts/malgun.ttf"
  elif platform.system() == "Darwin":   # for mac
      font_path = "/Users/$USER/Library/Fonts/AppleGothic.ttf"
      
      
      
      wordcloud=WordCloud(font_path= font_path, 
                      background_color="white",
                      max_words=100,
                      relative_scaling= 0.3,
                      width = 800,
                      height = 400
                   ).generate_from_frequencies(tts)  
  plt.figure(figsize=(15,10))
  plt.imshow(wordcloud)
  plt.axis('off') # Remove axis values
  plt.savefig('mywc.png') # save as an image file
  ```

  

---

# Reference

* https://plotly.com/
* https://matplotlib.org/
* https://www.tableau.com/



