---
layout: single
title:  "pandas & numpy; tool for data analysis"
categories: pandas&numpy


author_profile: false
typora-root-url: ../
---

# Data analysis

## pandas and numpy basics

both numpy and pandas libraries are super important tools for data analysis

### pandas basics

여기서 부터 작성!!!!!!!! da day1

### numpy basics 



1. 


## Form tag

```html
<body>
<!-- Form Tag: Responsible for sending user input to the server. For example, sending data like usernames and passwords to the server. -->
<!-- Two client-to-server communication methods: get (small data, fast but less secure) / post (large data, slower but more secure) -->

<!--<form action="server-page">-->
<!--    <table>-->
<!--        Sign-up Page-->
<!--    </table>-->
<!--</form>-->

<input type="date">
<input type="month">
<input type="week">
<input type="time">
<input type="datetime">
<input type="checkbox" value="Coding"> Do you like coding? <br>
<input type="number" min="0" max="5"> pieces
<input type="button" value="Announcement" onclick="window.open('1.html')"> Open
<input type="file">
</body>

```



![img](https://blog.kakaocdn.net/dn/BJKzy/btr1nwRaJ3C/DJF2BfMKt6HiAEklHV0wlK/img.png)



## Table tag

example code for table tag

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        table, th, td{
        border: 1px solid blue;
        border-collapse:collapse;
        }

    </style>
</head>
<body>
<table>
    <caption>상품 구성</caption>
    <thead>
    <tr>
        <th>용도</th>
        <th>갯수</th>
        <th>가격</th>
    </tr>
    </thead>

    <tbody>
    <tr>
    <td>선물용</td>
    <td rowspan = "2">11~15과</td>
    <td>30000</td>
    </tr>

    <tr>
    <td>가정용</td>
<!--    <td>10~13과</td>-->
    <td>20000</td>
    </tr>
    </tbody>

</table>

<table width = "500" height = "500">
    <tr>
            <td colspan="5"> </td>
        </tr>
        <tr>
            <td rowspan="4"> </td>
            <td colspan="4"> </td>
        </tr>
        <tr>

            <td> </td>
            <td rowspan="2"> </td>
            <td> </td>
            <td rowspan="3"> </td>
        </tr>
        <tr>
            <td> </td>
            <td> </td>
        </tr>
        <tr>
            <td colspan="2"> </td>
            <td> </td>
        </tr>
    </table>
</body>
</html>
```



![img](https://blog.kakaocdn.net/dn/tDlee/btr07AHpGbZ/ydvqgNsKT0DHClQqXtDTk0/img.png)



## Img tag

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<a href="http://www.naver.com">
<img src="img.png" alt="Salad" width="50%" height="50%">
</a>
<!-- If an error occurs while loading, the 'Salad' text will be displayed as a substitute for the image ('alt' attribute). -->

<object width="500" height="800" data="filename"></object>
<!-- The 'object' element can be used to display videos, audios, or PDF files on the web. -->

For playing videos, images, and audio:
<embed src="filename">
</body>
</html>

```





---

# Tips and scribbles

* Always remember, you actually have to code in order to make improvements!

  


---

# Reference

* https://ofcourse.kr/html-course/p-태그

