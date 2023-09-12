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

- Series: A series stores data of the same type in a one-dimensional structure.
- DataFrame: A DataFrame stores data of various types in a two-dimensional structure; each column is a Series.
- Matrix: A matrix stores data of the same type in a two-dimensional structure.

In the code snippet `f = pd.Series([1, -2, 0, 5, np.nan])`, `f.isna()` is used to check if the values inside `f` are NaN (Not a Number).

![img](https://blog.kakaocdn.net/dn/bB57eI/btr6g8Fjk9E/DK3DdcXzIjC0iv5g74ujM1/img.png)

- `f[f.isna()]`: This expression retrieves values from `f` where `f.isna()` is `True`. In other words, it performs boolean indexing, extracting data based on a condition, which is commonly used.

- Boolean Indexing: It involves selecting data from a variable using a condition, i.e., `variable[condition]`. It extracts data where the condition is true.

- `s.dropna()`: This function removes NaN (missing) values from `s`. NaN, nan, and None are all considered missing values. Remember that the result should be assigned to a variable to store the changes.

- `s[s.notna()]`: This expression selects values in `s` that are not NaN (i.e., not missing).

DataFrame:

![img](https://blog.kakaocdn.net/dn/cEEkHH/btr5YUnKnEZ/CVkbTSTAK1U7lBRsil8Z0k/img.png)

- `data.dropna()`: Removes rows containing NaN values from the DataFrame.
- `data.dropna(how='all')`: Removes rows only if all values in the row are NaN.
- `data[4] = np.nan`: Adds NaN values to the 4th column of the DataFrame.

![img](https://blog.kakaocdn.net/dn/v8Fgw/btr6oJq9Xfu/hkEFuoCvjfVVGkfipcdH00/img.png)

`data.dropna(axis='columns', how='all')`: This code removes columns where all values are NaN when considering the column axis (axis='columns').

![img](https://blog.kakaocdn.net/dn/whicS/btr59ZWtAUv/PckkPCvBKDZFhclkG5KI70/img.png)



`pd.DataFrame(np.random.standard_normal((7, 3)))`: This line generates data following a standard normal distribution with 7 rows and 3 columns and stores it in a DataFrame.

![img](https://blog.kakaocdn.net/dn/1i9Nk/btr6qPdg9PG/wgvxEKDWyxTVxCfQA50K0k/img.png)



### numpy basics 

여기서 부터 이어서 작성!!!!!!!! da day1

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

