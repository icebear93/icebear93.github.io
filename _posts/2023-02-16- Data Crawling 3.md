---
layout: single
title:  "Data Crawling 3; how to label data on the map by using folium"
categories: ML/DL


author_profile: false
typora-root-url: ../

---

# Data on the map; folium

 You can use folium library to mark data that you gathered from data crawling on a map. 

```py
!pip3 install folium
```

``` py
# folium map
folium.Map( location, zoom_start, tiles ...)

sb_map = folium.Map(location =[37.5, 126.98], 
                    #[latitude,longitude]
                    zoom_start = 11, 
                    # level of zoom for the map
                    tiles = 'Stamen Terrain' 
                    # Change the map style
)
```



## Three Examples..

(Most of the explanations will be given with examples)

### folium.GeoJson

``` python
sb_bubble = folium.Map(
    location= [37.573050, 126.979189],
    tiles = 'CartoDB positron',
    zoom_start = 10
)

def ss_style(feature):
    return{
        'color' : 'orange',
        'opacity' : 0.5,
        'dashArray' : '5.5',
        'fillOpacity' : 0.1, # fill opacity
        'weight' : 1 # thickness of the line
    }
    

folium.GeoJson(
    seoul_sgg_geo,
    style_function = ss_style
).add_to(sb_bubble)

sb_bubble

```

![SCR-20230816-ukhc](/images/2023-02-16- Data Crawling 3/SCR-20230816-ukhc-2200441.png)



### folium.Choropleth

``` py
# folium.Choropleth: This is used to color and display desired information on a map. It loads the geo_data and uses the key_on parameter to find the same name, such as SIG_KOR_NM, from the data in seoul_sgg_state (presumably a dataset). Now that the matching is done, it uses the columns to output Starbucks stores based on the administrative district names. In other words, the image below represents Starbucks stores by administrative district, using colors. The darker the color, the higher the number of Starbucks stores.

sb_choro = folium.Map(
    location=[37.573050, 126.979189],
    tiles='CartoDB dark_matter',
    zoom_start=11
)

folium.Choropleth(
    geo_data = seoul_sgg_geo2,
    data = seoul_sgg_stat,
    key_on = 'properties.SIG_KOR_NM', 
    columns = ['시군구명', '스타벅스_매장수'], # seoul_sgg_stat data 시군구명, 스타벅스 매장수
    
    
    fill_opacity = 0.7,
    line_color= 'yellow',
    line_opacity= 0.3,
    fill_color= 'YlGn'
).add_to(sb_choro) # add this option to map (in this case the map name is 'sb_choro')
```

![SCR-20230816-ukiq](/images/2023-02-16- Data Crawling 3/SCR-20230816-ukiq.png)



### folium.CircleMarker

#### Basic folium.circleMarker

```py
# folium.Marker or folium.circleMarker
folium.CircleMarker(
    location=[37.501087, 127.073069],
    fill = True,
    fill_color = 'green',
    fill_opacity = 0.9,
    weight = 0.1, # 테두리 선의 두께
    radius = 5

).add_to(sb_map) #형성한 마커를 지도위에 추가
```

#### Advanced folium.circleMarker

```py
top10 = seoul_sgg_stat['만명당_매장수'].quantile(0.9) # 90% status; meaning top 10% of the scale

for idx in seoul_sgg_stat.index:
    lat=seoul_sgg_stat.loc[idx, '위도']
    lon=seoul_sgg_stat.loc[idx, '경도']
    cnt_10t=seoul_sgg_stat.loc[idx, '만명당_매장수']
    if cnt_10t > top10:
        fcolor='red'
    else:
        fcolor='blue'
        
    folium.CircleMarker(
        location=(lat,lon),
        fill_color=fcolor,
        radius=cnt_10t*10,
        fill_opacity=0.2,
        weight=0.5,
        color='#FFFF00' #color='yellow'
    ).add_to(viz_map_1)
viz_map_1
```

![SCR-20230816-uiwn](/images/2023-02-16- Data Crawling 3/SCR-20230816-uiwn-2200563.jpeg)

---

# Tips and scribbles

* `pd.read_excel("seoul_sgg_stat.xlsx", **thousands = ','**)`: If there are commas in the thousands place within the contents of the Excel file, you can use the `thousands` parameter when reading the Excel file for the first time to remove them.

* Using dictionaries effectively in coding is good coding.

  

---

# Reference

* https://plotly.com/
* https://matplotlib.org/
* https://www.tableau.com/
*  https://python-visualization.github.io/folium/modules.html?highlight=geojson[**#folium**.features.GeoJson](https://python-visualization.github.io/folium/modules.html?highlight=geojson#folium.features.GeoJson)
* https://github.com/southkorea/seoul-maps/tree/master/kostat/2013 



