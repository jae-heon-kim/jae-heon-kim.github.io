---
layout: post
title:  "pandas data process"
---

# PYTHON PROGRAMMING FUNDAMENTALS  


# Pandas 의 장점
- Allows the use of labels for rows and columns
- 기본적인 통계데이터 제공
- NaN values 를 알아서 처리함.
- 숫자 문자열을 알아서 로드함.
- 데이터셋들을 merge 할 수 있음.
- It integrates with NumPy and Matplotlib


```python
import pandas as pd    #numpy를 바로 사람이 쓰기엔 빡세서 rapping을 해서 사람 편하도록 pandas라는 라이브러리를 만들었다.
```


```python

```


```python

```

## Pandas Series 데이터 생성하기


```python
my_index = ['eggs', 'apples', 'milk', 'bread']
```


```python
my_data = [30,6,'Yes', 'No']
```


```python
pd.Series(data=my_data)   #1차원 데이터를 판다스에선 Series라고 부름, 또한 2차원 데이터와 통일성을 위해 세로로 사용
```




    0     30
    1      6
    2    Yes
    3     No
    dtype: object




```python
# 왼쪽 0, 1, 2, 3들을 index라고 부르는데 판다스의 index는 컴퓨터의 index랑은 다름(컴퓨터의 index는 출력에 표시되지 않았음)
# 30, 6, Yes, No는 data라고 부름
```


```python
pd.Series(data=my_data, index=my_index) #현재 판다스의 index는 aggs, apples ...이고 컴퓨터의 index는 0,1,2,3 임
```




    eggs       30
    apples      6
    milk      Yes
    bread      No
    dtype: object




```python
groceries =pd.Series(data=my_data, index=my_index)
```


```python
groceries
```




    eggs       30
    apples      6
    milk      Yes
    bread      No
    dtype: object




```python
groceries.shape  #넘파이도 가능
```




    (4,)




```python
groceries.size   #넘파이도 가능
```




    4




```python
groceries.ndim   #넘파이도 가능
```




    1




```python
groceries.index  #넘파이는 불가능 판다스꺼
```




    Index(['eggs', 'apples', 'milk', 'bread'], dtype='object')




```python
groceries.values
```




    array([30, 6, 'Yes', 'No'], dtype=object)




```python

```


```python
'bread' in groceries
```




    True




```python
30 in groceries
```




    False




```python
30 in groceries.values
```




    True




```python

```

## Accessing and Deleting Elements in Pandas Series - 레이블과 인덱스


```python
groceries
```




    eggs       30
    apples      6
    milk      Yes
    bread      No
    dtype: object




```python
#groceries[0]
groceries['eggs']
```




    30




```python
groceries.eggs
```




    30




```python
groceries[['eggs','milk']]
```




    eggs     30
    milk    Yes
    dtype: object




```python
groceries[['eggs','milk','bread']]
```




    eggs      30
    milk     Yes
    bread     No
    dtype: object




```python

```

## Arithmetic Operations on Pandas Series  #연산


```python
my_index = ['apples', 'oranges', 'bananas']
```


```python
my_data = [10, 6, 3]
```


```python
fruits = pd.Series(data=my_data, index=my_index)
```


```python
fruits
```




    apples     10
    oranges     6
    bananas     3
    dtype: int64




```python
fruits = fruits + 5
```


```python
fruits
```




    apples     15
    oranges    11
    bananas     8
    dtype: int64




```python
fruits = fruits*2
```


```python
fruits
```




    apples     30
    oranges    22
    bananas    16
    dtype: int64




```python
#fruits.apples - 5
fruits = fruits['apples']-5
```


```python
fruits
```




    25




```python

```

# 실습
import pandas as pd

## 1. 다음과 같은 레이블과 값을 가지는 Pandas Series 를 만드세요. 변수는 dist_planets 로 만드세요.

### distance_from_sun = [149.6, 1433.5, 227.9, 108.2, 778.6]

### planets = ['Earth','Saturn', 'Mars','Venus', 'Jupiter']

### dist_planets = 



## 3. 거리를 빛의 상수 c( 18 ) 로 나눠서, 가는 시간이 얼마나 걸리는 지 계산하여 저장하세요.
### time_light = 

## 3. Boolean indexing을 이용해서 가는 시간이 40분보다 작은것들만 셀렉트 하세요.
### close_planets = 


```python
distance_from_sun = [149.6, 1433.5, 227.9, 108.2, 778.6]
```


```python
planets = ['Earth','Saturn', 'Mars','Venus', 'Jupiter']
```


```python
dist_planets = pd.Series(data = distance_from_sun, index = planets)
```


```python
dist_planets
```




    Earth       149.6
    Saturn     1433.5
    Mars        227.9
    Venus       108.2
    Jupiter     778.6
    dtype: float64




```python
time_light = dist_planets / 18
```


```python
time_light
```




    Earth       8.311111
    Saturn     79.638889
    Mars       12.661111
    Venus       6.011111
    Jupiter    43.255556
    dtype: float64




```python
close_planets = time_light[time_light<40]
```


```python
close_planets
```




    Earth     8.311111
    Mars     12.661111
    Venus     6.011111
    dtype: float64



## Pandas Dataframe

### 레이블로 생성하기


```python
import pandas as pd

# We create a dictionary of Pandas Series 
items = {'Bob' : pd.Series(data = [245, 25, 55], index = ['bike', 'pants', 'watch']),
         'Alice' : pd.Series(data = [40, 110, 500, 45], index = ['book', 'glasses', 'bike', 'pants'])}


```


```python
pd.DataFrame(data=items)    #2차원 데이터는 DataFrame이라고 하고 bike book glasses ... 이 인덱스, Bob Alice를 column이라고 함
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>245.0</td>
      <td>500.0</td>
    </tr>
    <tr>
      <th>book</th>
      <td>NaN</td>
      <td>40.0</td>
    </tr>
    <tr>
      <th>glasses</th>
      <td>NaN</td>
      <td>110.0</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>25.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>55.0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python

```

### 1.

 `fruit_sales` 데이터프레임을 아래처럼 만드시오

![](https://i.imgur.com/CHPn7ZF.png)


```python
items = {'Apples' : pd.Series(data=[35,41], index = ['2017 Sales', '2018 Sales']), 
        'Bananas' : pd.Series(data=[21,34], index=['2017 Sales', '2018 Sales'])}
```


```python
pd.DataFrame(data = items)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Apples</th>
      <th>Bananas</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2017 Sales</th>
      <td>35</td>
      <td>21</td>
    </tr>
    <tr>
      <th>2018 Sales</th>
      <td>41</td>
      <td>34</td>
    </tr>
  </tbody>
</table>
</div>




```python

```


```python
my_data = {'Bob':['I Liked It', 'It was awful.'], 'Sue':['Pretty good.','Bland.']}
my_index = ['Product A', 'Product B']
```


```python
reviews = pd.DataFrame(data = my_data, index = my_index)
```


```python
reviews
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Sue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Product A</th>
      <td>I Liked It</td>
      <td>Pretty good.</td>
    </tr>
    <tr>
      <th>Product B</th>
      <td>It was awful.</td>
      <td>Bland.</td>
    </tr>
  </tbody>
</table>
</div>




```python
reviews.index
```




    Index(['Product A', 'Product B'], dtype='object')




```python
reviews.to_csv('review.csv')
```


```python

```


```python
tomorrow = pd.read_csv('review.csv')
```


```python
tomorrow
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>Bob</th>
      <th>Sue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Product A</td>
      <td>I Liked It</td>
      <td>Pretty good.</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Product B</td>
      <td>It was awful.</td>
      <td>Bland.</td>
    </tr>
  </tbody>
</table>
</div>




```python
tomorrow = pd.read_csv('review.csv', index_col=0)
```


```python
tomorrow
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Sue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Product A</th>
      <td>I Liked It</td>
      <td>Pretty good.</td>
    </tr>
    <tr>
      <th>Product B</th>
      <td>It was awful.</td>
      <td>Bland.</td>
    </tr>
  </tbody>
</table>
</div>




```python

```

### NaN 은 해당 항목에 값이 없음을 뜻합니다.  (Not a Number)


```python

```


```python
# We create a dictionary of Pandas Series without indexes
data = {'Bob' : pd.Series([245, 25, 55]),
        'Alice' : pd.Series([40, 110, 500, 45])}

```


```python
df = pd.DataFrame(data = data)
```


```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>245.0</td>
      <td>40</td>
    </tr>
    <tr>
      <th>1</th>
      <td>25.0</td>
      <td>110</td>
    </tr>
    <tr>
      <th>2</th>
      <td>55.0</td>
      <td>500</td>
    </tr>
    <tr>
      <th>3</th>
      <td>NaN</td>
      <td>45</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.shape
```




    (4, 2)




```python
df.ndim   #차원
```




    2




```python
df.index
```




    RangeIndex(start=0, stop=4, step=1)




```python
df.columns
```




    Index(['Bob', 'Alice'], dtype='object')




```python
df.values
```




    array([[245.,  40.],
           [ 25., 110.],
           [ 55., 500.],
           [ nan,  45.]])




```python

```


```python

```

### 인덱스 및 컬럼 생성하기


```python
items = {'Bob' : pd.Series(data = [245, 25, 55], index = ['bike', 'pants', 'watch']),
         'Alice' : pd.Series(data = [40, 110, 500, 45], index = ['book', 'glasses', 'bike', 'pants'])}

```


```python
df = pd.DataFrame(data = items)
```


```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>245.0</td>
      <td>500.0</td>
    </tr>
    <tr>
      <th>book</th>
      <td>NaN</td>
      <td>40.0</td>
    </tr>
    <tr>
      <th>glasses</th>
      <td>NaN</td>
      <td>110.0</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>25.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>55.0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python

```


```python

```

## Accessing Elements in Pandas DataFrames


```python
import pandas as pd
```


```python
# We create a list of Python dictionaries
items2 = [{'bikes': 20, 'pants': 30, 'watches': 35}, 
          {'watches': 10, 'glasses': 50, 'bikes': 15, 'pants':5}]


```


```python
store_items = pd.DataFrame(data = items2,index = ['store1','store2'])
```


```python
store_items
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>watches</th>
      <th>glasses</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store1</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>store2</th>
      <td>15</td>
      <td>5</td>
      <td>10</td>
      <td>50.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
###### 판다스의 데이터프레임에서!!! 데이터를 억세스 하는 방법!!!!!
```


```python
# 1. 컬럼의 값을 가져오는 방법 => 변수에 바로 대괄호 사용!!   또는 변수오른쪽에 바로 점 붙이고 컬럼명(여러컬럼 가져오기는 힘들다.)
```


```python
store_items['pants']
```




    store1    30
    store2     5
    Name: pants, dtype: int64




```python
store_items.pants
```




    store1    30
    store2     5
    Name: pants, dtype: int64




```python
store_items[['bikes','watches']]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>watches</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store1</th>
      <td>20</td>
      <td>35</td>
    </tr>
    <tr>
      <th>store2</th>
      <td>15</td>
      <td>10</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 2. 행과 열을 이용해서 데이터를 가져오는 방법

### 2-1. loc[] 로 데이터를 가져오는 방법 => loc는 사람이 부르는 인덱스와 컬럼의 진한 글씨로 데이터를 억세스 한다!
#loc 은 location의 약자임
```


```python
store_items
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>watches</th>
      <th>glasses</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store1</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>store2</th>
      <td>15</td>
      <td>5</td>
      <td>10</td>
      <td>50.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
store_items.loc[ 'store1' , 'pants' ]
```




    30




```python
store_items.loc[ 'store1' , ['pants','watches']  ]
```




    pants      30.0
    watches    35.0
    Name: store1, dtype: float64




```python

```


```python
### 2-1. iloc[] 로 데이터를 가져오는 방법   #반복문 사용할 때 유용하다!
```


```python
store_items.iloc[0 , 1  ]
```




    30




```python
store_items.iloc[0 , [1,2]]
```




    pants      30.0
    watches    35.0
    Name: store1, dtype: float64




```python

```


```python
store_items
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>watches</th>
      <th>glasses</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store1</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>store2</th>
      <td>15</td>
      <td>5</td>
      <td>10</td>
      <td>50.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
store_items.loc['store2', 'pants'] = 6
```


```python
store_items
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>watches</th>
      <th>glasses</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store1</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>store2</th>
      <td>15</td>
      <td>6</td>
      <td>10</td>
      <td>50.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
store_items.loc['store2', ['pants','watches'] ] =[8,12]
```


```python
store_items
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>watches</th>
      <th>glasses</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store1</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>store2</th>
      <td>15</td>
      <td>8</td>
      <td>12</td>
      <td>50.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
store_items.loc['store2', 'pants'] += 6
```


```python
store_items
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>watches</th>
      <th>glasses</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store1</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>store2</th>
      <td>15</td>
      <td>14</td>
      <td>12</td>
      <td>50.0</td>
    </tr>
  </tbody>
</table>
</div>



## 컬럼 추가


```python
store_items['shirts'] = [15,2]
```


```python
store_items
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>watches</th>
      <th>glasses</th>
      <th>shirts</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store1</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>NaN</td>
      <td>15</td>
    </tr>
    <tr>
      <th>store2</th>
      <td>15</td>
      <td>14</td>
      <td>12</td>
      <td>50.0</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>




```python

```


```python
# pants와 shirts의 값을 합해서, suits 컬럼을 만드시오
```


```python
store_items['suits'] = store_items['pants'] + store_items['shirts']
```


```python
store_items
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>watches</th>
      <th>glasses</th>
      <th>shirts</th>
      <th>suits</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store1</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>NaN</td>
      <td>15</td>
      <td>45</td>
    </tr>
    <tr>
      <th>store2</th>
      <td>15</td>
      <td>14</td>
      <td>12</td>
      <td>50.0</td>
      <td>2</td>
      <td>16</td>
    </tr>
  </tbody>
</table>
</div>




```python

```


```python
#store1과 store2를 더해서 store3 인덱스를 만드시오
```


```python
#store_items.loc['store3'] = store_items.loc['store1']+store_items.loc['store2']
```


```python
#store_items
```


```python

```


```python
new_item = [{'bikes':20, 'pants':30, 'watches':35, 'glasses':4}]
```


```python
new_store = pd.DataFrame(data = new_item, index=['store3'])
```


```python
new_store
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>watches</th>
      <th>glasses</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store3</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>4</td>
    </tr>
  </tbody>
</table>
</div>




```python
store_items = store_items.append(new_store)
```


```python
store_items
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>watches</th>
      <th>glasses</th>
      <th>shirts</th>
      <th>suits</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store1</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>NaN</td>
      <td>15.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>store2</th>
      <td>15</td>
      <td>14</td>
      <td>12</td>
      <td>50.0</td>
      <td>2.0</td>
      <td>16.0</td>
    </tr>
    <tr>
      <th>store3</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>4.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
#loc로 슬라이싱 할때는, loc는 사람이 쓰는 인덱스와 컬럼으로 하는것이므로 +1을 해주지 않아도 됨
store_items.loc['store2':'store3',]   

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>watches</th>
      <th>glasses</th>
      <th>shirts</th>
      <th>suits</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store2</th>
      <td>15</td>
      <td>14</td>
      <td>12</td>
      <td>50.0</td>
      <td>2.0</td>
      <td>16.0</td>
    </tr>
    <tr>
      <th>store3</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>4.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python

```


```python
store_items
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>watches</th>
      <th>glasses</th>
      <th>shirts</th>
      <th>suits</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store1</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>NaN</td>
      <td>15.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>store2</th>
      <td>15</td>
      <td>14</td>
      <td>12</td>
      <td>50.0</td>
      <td>2.0</td>
      <td>16.0</td>
    </tr>
    <tr>
      <th>store3</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>4.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
store_items.loc['store1':'store3', :]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>watches</th>
      <th>glasses</th>
      <th>shirts</th>
      <th>suits</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store1</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>NaN</td>
      <td>15.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>store2</th>
      <td>15</td>
      <td>14</td>
      <td>12</td>
      <td>50.0</td>
      <td>2.0</td>
      <td>16.0</td>
    </tr>
    <tr>
      <th>store3</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>4.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
store_items.iloc[ : , 1:3+1]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>pants</th>
      <th>watches</th>
      <th>glasses</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store1</th>
      <td>30</td>
      <td>35</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>store2</th>
      <td>14</td>
      <td>12</td>
      <td>50.0</td>
    </tr>
    <tr>
      <th>store3</th>
      <td>30</td>
      <td>35</td>
      <td>4.0</td>
    </tr>
  </tbody>
</table>
</div>




```python

```


```python
# 행 삭제, 열 삭제 => drop 함수 이용
```


```python
store_items
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>watches</th>
      <th>glasses</th>
      <th>shirts</th>
      <th>suits</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store1</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>NaN</td>
      <td>15.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>store2</th>
      <td>15</td>
      <td>14</td>
      <td>12</td>
      <td>50.0</td>
      <td>2.0</td>
      <td>16.0</td>
    </tr>
    <tr>
      <th>store3</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>4.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
store_items.drop('watches', axis = 1)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>glasses</th>
      <th>shirts</th>
      <th>suits</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store1</th>
      <td>20</td>
      <td>30</td>
      <td>NaN</td>
      <td>15.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>store2</th>
      <td>15</td>
      <td>14</td>
      <td>50.0</td>
      <td>2.0</td>
      <td>16.0</td>
    </tr>
    <tr>
      <th>store3</th>
      <td>20</td>
      <td>30</td>
      <td>4.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
store_items.drop('store2', axis = 0)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>watches</th>
      <th>glasses</th>
      <th>shirts</th>
      <th>suits</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store1</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>NaN</td>
      <td>15.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>store3</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>4.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python

```


```python
store_items
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>watches</th>
      <th>glasses</th>
      <th>shirts</th>
      <th>suits</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store1</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>NaN</td>
      <td>15.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>store2</th>
      <td>15</td>
      <td>14</td>
      <td>12</td>
      <td>50.0</td>
      <td>2.0</td>
      <td>16.0</td>
    </tr>
    <tr>
      <th>store3</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>4.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
store_items.drop(['store1','store3'], axis=0)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>watches</th>
      <th>glasses</th>
      <th>shirts</th>
      <th>suits</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store2</th>
      <td>15</td>
      <td>14</td>
      <td>12</td>
      <td>50.0</td>
      <td>2.0</td>
      <td>16.0</td>
    </tr>
  </tbody>
</table>
</div>




```python

```


```python
store_items.drop(['pants','glasses','suits'], axis=1)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>watches</th>
      <th>shirts</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store1</th>
      <td>20</td>
      <td>35</td>
      <td>15.0</td>
    </tr>
    <tr>
      <th>store2</th>
      <td>15</td>
      <td>12</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>store3</th>
      <td>20</td>
      <td>35</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python

```


```python
store_items
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>watches</th>
      <th>glasses</th>
      <th>shirts</th>
      <th>suits</th>
      <th>name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store1</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>NaN</td>
      <td>15.0</td>
      <td>45.0</td>
      <td>A</td>
    </tr>
    <tr>
      <th>store2</th>
      <td>15</td>
      <td>14</td>
      <td>12</td>
      <td>50.0</td>
      <td>2.0</td>
      <td>16.0</td>
      <td>B</td>
    </tr>
    <tr>
      <th>store3</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>4.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>C</td>
    </tr>
  </tbody>
</table>
</div>




```python
store_items['name'] = ['A', 'B', 'C']
```


```python
store_items
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>watches</th>
      <th>glasses</th>
      <th>shirts</th>
      <th>suits</th>
      <th>name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store1</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>NaN</td>
      <td>15.0</td>
      <td>45.0</td>
      <td>A</td>
    </tr>
    <tr>
      <th>store2</th>
      <td>15</td>
      <td>14</td>
      <td>12</td>
      <td>50.0</td>
      <td>2.0</td>
      <td>16.0</td>
      <td>B</td>
    </tr>
    <tr>
      <th>store3</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>4.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>C</td>
    </tr>
  </tbody>
</table>
</div>




```python
store_items.set_index('name')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>watches</th>
      <th>glasses</th>
      <th>shirts</th>
      <th>suits</th>
    </tr>
    <tr>
      <th>name</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>NaN</td>
      <td>15.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>B</th>
      <td>15</td>
      <td>14</td>
      <td>12</td>
      <td>50.0</td>
      <td>2.0</td>
      <td>16.0</td>
    </tr>
    <tr>
      <th>C</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>4.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python

```

## Dealing with NaN


```python
# We create a list of Python dictionaries
items2 = [{'bikes': 20, 'pants': 30, 'watches': 35, 'shirts': 15, 'shoes':8, 'suits':45},
{'watches': 10, 'glasses': 50, 'bikes': 15, 'pants':5, 'shirts': 2, 'shoes':5, 'suits':7},
{'bikes': 20, 'pants': 30, 'watches': 35, 'glasses': 4, 'shoes':10}]


```


```python
store_items2 = pd.DataFrame(data=items2, index = ['store 1', 'store 2', 'store 3'])
```


```python
store_items2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>watches</th>
      <th>shirts</th>
      <th>shoes</th>
      <th>suits</th>
      <th>glasses</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 1</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>15.0</td>
      <td>8</td>
      <td>45.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>store 2</th>
      <td>15</td>
      <td>5</td>
      <td>10</td>
      <td>2.0</td>
      <td>5</td>
      <td>7.0</td>
      <td>50.0</td>
    </tr>
    <tr>
      <th>store 3</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>NaN</td>
      <td>10</td>
      <td>NaN</td>
      <td>4.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
store_items2.isna()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>watches</th>
      <th>shirts</th>
      <th>shoes</th>
      <th>suits</th>
      <th>glasses</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 1</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
    </tr>
    <tr>
      <th>store 2</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>store 3</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
</div>




```python
store_items2.isna().sum()   #axis를 주지 않으면 자동으로 col별로 더함 store_items2.isna().sum(axis=0)과 같다
```




    bikes      0
    pants      0
    watches    0
    shirts     1
    shoes      0
    suits      1
    glasses    1
    dtype: int64




```python
# NaN 데이터를 처리하는 전략을 짤 수 있음!
```


```python
# 1. 삭제하는 경우
```


```python
store_items2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>watches</th>
      <th>shirts</th>
      <th>shoes</th>
      <th>suits</th>
      <th>glasses</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 1</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>15.0</td>
      <td>8</td>
      <td>45.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>store 2</th>
      <td>15</td>
      <td>5</td>
      <td>10</td>
      <td>2.0</td>
      <td>5</td>
      <td>7.0</td>
      <td>50.0</td>
    </tr>
    <tr>
      <th>store 3</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>NaN</td>
      <td>10</td>
      <td>NaN</td>
      <td>4.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
store_items2.dropna()   #NaN데이터 삭제
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>watches</th>
      <th>shirts</th>
      <th>shoes</th>
      <th>suits</th>
      <th>glasses</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 2</th>
      <td>15</td>
      <td>5</td>
      <td>10</td>
      <td>2.0</td>
      <td>5</td>
      <td>7.0</td>
      <td>50.0</td>
    </tr>
  </tbody>
</table>
</div>




```python

```


```python
# 2. 다른 값으로 채우는 전략
```


```python
# 2-1. 특정 값으로 셋팅
```


```python
store_items2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>watches</th>
      <th>shirts</th>
      <th>shoes</th>
      <th>suits</th>
      <th>glasses</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 1</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>15.0</td>
      <td>8</td>
      <td>45.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>store 2</th>
      <td>15</td>
      <td>5</td>
      <td>10</td>
      <td>2.0</td>
      <td>5</td>
      <td>7.0</td>
      <td>50.0</td>
    </tr>
    <tr>
      <th>store 3</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>NaN</td>
      <td>10</td>
      <td>NaN</td>
      <td>4.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
store_items2.fillna(0)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>watches</th>
      <th>shirts</th>
      <th>shoes</th>
      <th>suits</th>
      <th>glasses</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 1</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>15.0</td>
      <td>8</td>
      <td>45.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>store 2</th>
      <td>15</td>
      <td>5</td>
      <td>10</td>
      <td>2.0</td>
      <td>5</td>
      <td>7.0</td>
      <td>50.0</td>
    </tr>
    <tr>
      <th>store 3</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>0.0</td>
      <td>10</td>
      <td>0.0</td>
      <td>4.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
store_items2.fillna('NO data')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>watches</th>
      <th>shirts</th>
      <th>shoes</th>
      <th>suits</th>
      <th>glasses</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 1</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>15.0</td>
      <td>8</td>
      <td>45.0</td>
      <td>NO data</td>
    </tr>
    <tr>
      <th>store 2</th>
      <td>15</td>
      <td>5</td>
      <td>10</td>
      <td>2.0</td>
      <td>5</td>
      <td>7.0</td>
      <td>50.0</td>
    </tr>
    <tr>
      <th>store 3</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>NO data</td>
      <td>10</td>
      <td>NO data</td>
      <td>4.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 2-2. 앞의 행이나 뒤의 행의 값, 또는 앞의 칼럼이나 뒤의 컬럼값으로 셋팅
```


```python
store_items2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>watches</th>
      <th>shirts</th>
      <th>shoes</th>
      <th>suits</th>
      <th>glasses</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 1</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>15.0</td>
      <td>8</td>
      <td>45.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>store 2</th>
      <td>15</td>
      <td>5</td>
      <td>10</td>
      <td>2.0</td>
      <td>5</td>
      <td>7.0</td>
      <td>50.0</td>
    </tr>
    <tr>
      <th>store 3</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>NaN</td>
      <td>10</td>
      <td>NaN</td>
      <td>4.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
store_items2.fillna(method = 'ffill', axis = 0)  ## ffill 은 forward fill의 약자로 앞의 데이터로 채우라는 말
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>watches</th>
      <th>shirts</th>
      <th>shoes</th>
      <th>suits</th>
      <th>glasses</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 1</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>15.0</td>
      <td>8</td>
      <td>45.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>store 2</th>
      <td>15</td>
      <td>5</td>
      <td>10</td>
      <td>2.0</td>
      <td>5</td>
      <td>7.0</td>
      <td>50.0</td>
    </tr>
    <tr>
      <th>store 3</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>2.0</td>
      <td>10</td>
      <td>7.0</td>
      <td>4.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
store_items2.fillna(method='bfill', axis = 0)  ##bfill 은 backword fill의 약자로 뒤의 데이터로 채우라는 말
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>watches</th>
      <th>shirts</th>
      <th>shoes</th>
      <th>suits</th>
      <th>glasses</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 1</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>15.0</td>
      <td>8</td>
      <td>45.0</td>
      <td>50.0</td>
    </tr>
    <tr>
      <th>store 2</th>
      <td>15</td>
      <td>5</td>
      <td>10</td>
      <td>2.0</td>
      <td>5</td>
      <td>7.0</td>
      <td>50.0</td>
    </tr>
    <tr>
      <th>store 3</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>NaN</td>
      <td>10</td>
      <td>NaN</td>
      <td>4.0</td>
    </tr>
  </tbody>
</table>
</div>




```python

```


```python
# 2-3. 컬럼의 평균값, 컬럼의 최대값, 컬럼의 최소값... 이런걸로 채우고 싶다.
```


```python
store_items2.mean()
```




    bikes      18.333333
    pants      21.666667
    watches    26.666667
    shirts      8.500000
    shoes       7.666667
    suits      26.000000
    glasses    27.000000
    dtype: float64




```python
store_items2.max()
```




    bikes      20.0
    pants      30.0
    watches    35.0
    shirts     15.0
    shoes      10.0
    suits      45.0
    glasses    50.0
    dtype: float64




```python
store_items2.min()
```




    bikes      15.0
    pants       5.0
    watches    10.0
    shirts      2.0
    shoes       5.0
    suits       7.0
    glasses     4.0
    dtype: float64




```python
store_items2.std()
```




    bikes       2.886751
    pants      14.433757
    watches    14.433757
    shirts      9.192388
    shoes       2.516611
    suits      26.870058
    glasses    32.526912
    dtype: float64




```python
store_items2.fillna(store_items2.mean())  #지가 알아서 다 평균으로 채워줌... 대단하네 판다스..
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bikes</th>
      <th>pants</th>
      <th>watches</th>
      <th>shirts</th>
      <th>shoes</th>
      <th>suits</th>
      <th>glasses</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>store 1</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>15.0</td>
      <td>8</td>
      <td>45.0</td>
      <td>27.0</td>
    </tr>
    <tr>
      <th>store 2</th>
      <td>15</td>
      <td>5</td>
      <td>10</td>
      <td>2.0</td>
      <td>5</td>
      <td>7.0</td>
      <td>50.0</td>
    </tr>
    <tr>
      <th>store 3</th>
      <td>20</td>
      <td>30</td>
      <td>35</td>
      <td>8.5</td>
      <td>10</td>
      <td>26.0</td>
      <td>4.0</td>
    </tr>
  </tbody>
</table>
</div>




```python

```

# 실습


```python
import pandas as pd
import numpy as np

# 각 유저별 별점을 주는것이므로, 1 decimal 로 셋팅.
pd.set_option('precision', 1)

# 책 제목과 작가, 그리고 유저별 별점 데이터가 있다.

books = pd.Series(data = ['Great Expectations', 'Of Mice and Men', 'Romeo and Juliet', 'The Time Machine', 'Alice in Wonderland' ])
authors = pd.Series(data = ['Charles Dickens', 'John Steinbeck', 'William Shakespeare', ' H. G. Wells', 'Lewis Carroll' ])

user_1 = pd.Series(data = [3.2, np.nan ,2.5])
user_2 = pd.Series(data = [5., 1.3, 4.0, 3.8])
user_3 = pd.Series(data = [2.0, 2.3, np.nan, 4])
user_4 = pd.Series(data = [4, 3.5, 4, 5, 4.2])

#  np.nan values 는 해당 유저가 해당 책에는 아직 별점 주지 않은것이다.
# labels: 'Author', 'Book Title', 'User 1', 'User 2', 'User 3', 'User 4'. 
# 아래 그림처럼 나오도록 만든다.




```

![%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202019-12-27%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%206.28.49.png](attachment:%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202019-12-27%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%206.28.49.png)


```python
# 1. 딕셔너리를 만들고,    2. 데이터프레임으로 만든 후,    3. nan을  평균값으로 채운다.

```


```python
my_data = {'Book Title' : books, 'Author' : authors, 'User1' : user_2, "User3" : user_3, 'User4' : user_4}
```


```python
df = pd.DataFrame(my_data)
```


```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Book Title</th>
      <th>Author</th>
      <th>User1</th>
      <th>User3</th>
      <th>User4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Great Expectations</td>
      <td>Charles Dickens</td>
      <td>5.0</td>
      <td>2.0</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Of Mice and Men</td>
      <td>John Steinbeck</td>
      <td>1.3</td>
      <td>2.3</td>
      <td>3.5</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Romeo and Juliet</td>
      <td>William Shakespeare</td>
      <td>4.0</td>
      <td>NaN</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>The Time Machine</td>
      <td>H. G. Wells</td>
      <td>3.8</td>
      <td>4.0</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Alice in Wonderland</td>
      <td>Lewis Carroll</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>4.2</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.fillna(df.mean())
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Book Title</th>
      <th>Author</th>
      <th>User1</th>
      <th>User3</th>
      <th>User4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Great Expectations</td>
      <td>Charles Dickens</td>
      <td>5.0</td>
      <td>2.0</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Of Mice and Men</td>
      <td>John Steinbeck</td>
      <td>1.3</td>
      <td>2.3</td>
      <td>3.5</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Romeo and Juliet</td>
      <td>William Shakespeare</td>
      <td>4.0</td>
      <td>2.8</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>The Time Machine</td>
      <td>H. G. Wells</td>
      <td>3.8</td>
      <td>4.0</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Alice in Wonderland</td>
      <td>Lewis Carroll</td>
      <td>3.5</td>
      <td>2.8</td>
      <td>4.2</td>
    </tr>
  </tbody>
</table>
</div>




```python

```

## Loading Data into a Pandas DataFrame


```python
df = pd.read_csv('GOOG.csv')
```


```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Date</th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Adj Close</th>
      <th>Volume</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2004-08-19</td>
      <td>49.7</td>
      <td>51.7</td>
      <td>47.7</td>
      <td>49.8</td>
      <td>49.8</td>
      <td>44994500</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2004-08-20</td>
      <td>50.2</td>
      <td>54.2</td>
      <td>49.9</td>
      <td>53.8</td>
      <td>53.8</td>
      <td>23005800</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2004-08-23</td>
      <td>55.0</td>
      <td>56.4</td>
      <td>54.2</td>
      <td>54.3</td>
      <td>54.3</td>
      <td>18393200</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2004-08-24</td>
      <td>55.3</td>
      <td>55.4</td>
      <td>51.5</td>
      <td>52.1</td>
      <td>52.1</td>
      <td>15361800</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2004-08-25</td>
      <td>52.1</td>
      <td>53.7</td>
      <td>51.6</td>
      <td>52.7</td>
      <td>52.7</td>
      <td>9257400</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>3308</th>
      <td>2017-10-09</td>
      <td>980.0</td>
      <td>985.4</td>
      <td>976.1</td>
      <td>977.0</td>
      <td>977.0</td>
      <td>891400</td>
    </tr>
    <tr>
      <th>3309</th>
      <td>2017-10-10</td>
      <td>980.0</td>
      <td>981.6</td>
      <td>966.1</td>
      <td>972.6</td>
      <td>972.6</td>
      <td>968400</td>
    </tr>
    <tr>
      <th>3310</th>
      <td>2017-10-11</td>
      <td>973.7</td>
      <td>990.7</td>
      <td>972.2</td>
      <td>989.2</td>
      <td>989.2</td>
      <td>1693300</td>
    </tr>
    <tr>
      <th>3311</th>
      <td>2017-10-12</td>
      <td>987.5</td>
      <td>994.1</td>
      <td>985.0</td>
      <td>987.8</td>
      <td>987.8</td>
      <td>1262400</td>
    </tr>
    <tr>
      <th>3312</th>
      <td>2017-10-13</td>
      <td>992.0</td>
      <td>997.2</td>
      <td>989.0</td>
      <td>989.7</td>
      <td>989.7</td>
      <td>1157700</td>
    </tr>
  </tbody>
</table>
<p>3313 rows × 7 columns</p>
</div>




```python
df.describe()    #데이트의 컬럼들중에서 숫자로 되어있는 컬럼들만 가져와서 통계표시해준것
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Adj Close</th>
      <th>Volume</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>3313.0</td>
      <td>3313.0</td>
      <td>3313.0</td>
      <td>3313.0</td>
      <td>3313.0</td>
      <td>3.3e+03</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>380.2</td>
      <td>383.5</td>
      <td>376.5</td>
      <td>380.1</td>
      <td>380.1</td>
      <td>8.0e+06</td>
    </tr>
    <tr>
      <th>std</th>
      <td>223.8</td>
      <td>225.0</td>
      <td>222.5</td>
      <td>223.9</td>
      <td>223.9</td>
      <td>8.4e+06</td>
    </tr>
    <tr>
      <th>min</th>
      <td>49.3</td>
      <td>50.5</td>
      <td>47.7</td>
      <td>49.7</td>
      <td>49.7</td>
      <td>7.9e+03</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>226.6</td>
      <td>228.4</td>
      <td>224.0</td>
      <td>226.4</td>
      <td>226.4</td>
      <td>2.6e+06</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>293.3</td>
      <td>295.4</td>
      <td>289.9</td>
      <td>293.0</td>
      <td>293.0</td>
      <td>5.3e+06</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>536.7</td>
      <td>540.0</td>
      <td>532.4</td>
      <td>536.7</td>
      <td>536.7</td>
      <td>1.1e+07</td>
    </tr>
    <tr>
      <th>max</th>
      <td>992.0</td>
      <td>997.2</td>
      <td>989.0</td>
      <td>989.7</td>
      <td>989.7</td>
      <td>8.3e+07</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Date</th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Adj Close</th>
      <th>Volume</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2004-08-19</td>
      <td>49.7</td>
      <td>51.7</td>
      <td>47.7</td>
      <td>49.8</td>
      <td>49.8</td>
      <td>44994500</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2004-08-20</td>
      <td>50.2</td>
      <td>54.2</td>
      <td>49.9</td>
      <td>53.8</td>
      <td>53.8</td>
      <td>23005800</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2004-08-23</td>
      <td>55.0</td>
      <td>56.4</td>
      <td>54.2</td>
      <td>54.3</td>
      <td>54.3</td>
      <td>18393200</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2004-08-24</td>
      <td>55.3</td>
      <td>55.4</td>
      <td>51.5</td>
      <td>52.1</td>
      <td>52.1</td>
      <td>15361800</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2004-08-25</td>
      <td>52.1</td>
      <td>53.7</td>
      <td>51.6</td>
      <td>52.7</td>
      <td>52.7</td>
      <td>9257400</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.tail()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Date</th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Adj Close</th>
      <th>Volume</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3308</th>
      <td>2017-10-09</td>
      <td>980.0</td>
      <td>985.4</td>
      <td>976.1</td>
      <td>977.0</td>
      <td>977.0</td>
      <td>891400</td>
    </tr>
    <tr>
      <th>3309</th>
      <td>2017-10-10</td>
      <td>980.0</td>
      <td>981.6</td>
      <td>966.1</td>
      <td>972.6</td>
      <td>972.6</td>
      <td>968400</td>
    </tr>
    <tr>
      <th>3310</th>
      <td>2017-10-11</td>
      <td>973.7</td>
      <td>990.7</td>
      <td>972.2</td>
      <td>989.2</td>
      <td>989.2</td>
      <td>1693300</td>
    </tr>
    <tr>
      <th>3311</th>
      <td>2017-10-12</td>
      <td>987.5</td>
      <td>994.1</td>
      <td>985.0</td>
      <td>987.8</td>
      <td>987.8</td>
      <td>1262400</td>
    </tr>
    <tr>
      <th>3312</th>
      <td>2017-10-13</td>
      <td>992.0</td>
      <td>997.2</td>
      <td>989.0</td>
      <td>989.7</td>
      <td>989.7</td>
      <td>1157700</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.isna()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Date</th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Adj Close</th>
      <th>Volume</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>3308</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3309</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3310</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3311</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3312</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
<p>3313 rows × 7 columns</p>
</div>




```python
df.isna().sum()
```




    Date         0
    Open         0
    High         0
    Low          0
    Close        0
    Adj Close    0
    Volume       0
    dtype: int64




```python
df.head(3)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Date</th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Adj Close</th>
      <th>Volume</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2004-08-19</td>
      <td>49.7</td>
      <td>51.7</td>
      <td>47.7</td>
      <td>49.8</td>
      <td>49.8</td>
      <td>44994500</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2004-08-20</td>
      <td>50.2</td>
      <td>54.2</td>
      <td>49.9</td>
      <td>53.8</td>
      <td>53.8</td>
      <td>23005800</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2004-08-23</td>
      <td>55.0</td>
      <td>56.4</td>
      <td>54.2</td>
      <td>54.3</td>
      <td>54.3</td>
      <td>18393200</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Adj Close</th>
      <th>Volume</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>3313.0</td>
      <td>3313.0</td>
      <td>3313.0</td>
      <td>3313.0</td>
      <td>3313.0</td>
      <td>3.3e+03</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>380.2</td>
      <td>383.5</td>
      <td>376.5</td>
      <td>380.1</td>
      <td>380.1</td>
      <td>8.0e+06</td>
    </tr>
    <tr>
      <th>std</th>
      <td>223.8</td>
      <td>225.0</td>
      <td>222.5</td>
      <td>223.9</td>
      <td>223.9</td>
      <td>8.4e+06</td>
    </tr>
    <tr>
      <th>min</th>
      <td>49.3</td>
      <td>50.5</td>
      <td>47.7</td>
      <td>49.7</td>
      <td>49.7</td>
      <td>7.9e+03</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>226.6</td>
      <td>228.4</td>
      <td>224.0</td>
      <td>226.4</td>
      <td>226.4</td>
      <td>2.6e+06</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>293.3</td>
      <td>295.4</td>
      <td>289.9</td>
      <td>293.0</td>
      <td>293.0</td>
      <td>5.3e+06</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>536.7</td>
      <td>540.0</td>
      <td>532.4</td>
      <td>536.7</td>
      <td>536.7</td>
      <td>1.1e+07</td>
    </tr>
    <tr>
      <th>max</th>
      <td>992.0</td>
      <td>997.2</td>
      <td>989.0</td>
      <td>989.7</td>
      <td>989.7</td>
      <td>8.3e+07</td>
    </tr>
  </tbody>
</table>
</div>




```python
# date 컬럼은 describe 못할까?
```


```python
df['Date'].describe()
```




    count           3313
    unique          3313
    top       2015-07-21
    freq               1
    Name: Date, dtype: object




```python
df['High'].describe()
```




    count    3313.0
    mean      383.5
    std       225.0
    min        50.5
    25%       228.4
    50%       295.4
    75%       540.0
    max       997.2
    Name: High, dtype: float64




```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 3313 entries, 0 to 3312
    Data columns (total 7 columns):
     #   Column     Non-Null Count  Dtype  
    ---  ------     --------------  -----  
     0   Date       3313 non-null   object 
     1   Open       3313 non-null   float64
     2   High       3313 non-null   float64
     3   Low        3313 non-null   float64
     4   Close      3313 non-null   float64
     5   Adj Close  3313 non-null   float64
     6   Volume     3313 non-null   int64  
    dtypes: float64(5), int64(1), object(1)
    memory usage: 181.3+ KB



```python

```


```python
df.max()   #각 컬럼별 max값
```




    Date         2017-10-13
    Open              992.0
    High              997.2
    Low               989.0
    Close             989.7
    Adj Close         989.7
    Volume         82768100
    dtype: object




```python
df.mean()
```




    Open         3.8e+02
    High         3.8e+02
    Low          3.8e+02
    Close        3.8e+02
    Adj Close    3.8e+02
    Volume       8.0e+06
    dtype: float64




```python
df.std()
```




    Open         2.2e+02
    High         2.2e+02
    Low          2.2e+02
    Close        2.2e+02
    Adj Close    2.2e+02
    Volume       8.4e+06
    dtype: float64




```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Date</th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Adj Close</th>
      <th>Volume</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2004-08-19</td>
      <td>49.7</td>
      <td>51.7</td>
      <td>47.7</td>
      <td>49.8</td>
      <td>49.8</td>
      <td>44994500</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2004-08-20</td>
      <td>50.2</td>
      <td>54.2</td>
      <td>49.9</td>
      <td>53.8</td>
      <td>53.8</td>
      <td>23005800</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2004-08-23</td>
      <td>55.0</td>
      <td>56.4</td>
      <td>54.2</td>
      <td>54.3</td>
      <td>54.3</td>
      <td>18393200</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2004-08-24</td>
      <td>55.3</td>
      <td>55.4</td>
      <td>51.5</td>
      <td>52.1</td>
      <td>52.1</td>
      <td>15361800</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2004-08-25</td>
      <td>52.1</td>
      <td>53.7</td>
      <td>51.6</td>
      <td>52.7</td>
      <td>52.7</td>
      <td>9257400</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>3308</th>
      <td>2017-10-09</td>
      <td>980.0</td>
      <td>985.4</td>
      <td>976.1</td>
      <td>977.0</td>
      <td>977.0</td>
      <td>891400</td>
    </tr>
    <tr>
      <th>3309</th>
      <td>2017-10-10</td>
      <td>980.0</td>
      <td>981.6</td>
      <td>966.1</td>
      <td>972.6</td>
      <td>972.6</td>
      <td>968400</td>
    </tr>
    <tr>
      <th>3310</th>
      <td>2017-10-11</td>
      <td>973.7</td>
      <td>990.7</td>
      <td>972.2</td>
      <td>989.2</td>
      <td>989.2</td>
      <td>1693300</td>
    </tr>
    <tr>
      <th>3311</th>
      <td>2017-10-12</td>
      <td>987.5</td>
      <td>994.1</td>
      <td>985.0</td>
      <td>987.8</td>
      <td>987.8</td>
      <td>1262400</td>
    </tr>
    <tr>
      <th>3312</th>
      <td>2017-10-13</td>
      <td>992.0</td>
      <td>997.2</td>
      <td>989.0</td>
      <td>989.7</td>
      <td>989.7</td>
      <td>1157700</td>
    </tr>
  </tbody>
</table>
<p>3313 rows × 7 columns</p>
</div>




```python
df['Close'].max()
```




    989.679993




```python
df.High.max()
```




    997.210022




```python
df[['Close','High']].max()
```




    Close    989.7
    High     997.2
    dtype: float64




```python

```


```python

```

# PANDAS OPERATIONS


```python
df = pd.DataFrame({'Employee ID':[111, 222, 333, 444],
                   'Employee Name':['Chanel', 'Steve', 'Mitch', 'Bird'],
                   'Salary [$/h]':[35, 29, 38, 20],
                   'Years of Experience':[3, 4 ,9, 1]})
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Employee ID</th>
      <th>Employee Name</th>
      <th>Salary [$/h]</th>
      <th>Years of Experience</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>111</td>
      <td>Chanel</td>
      <td>35</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>222</td>
      <td>Steve</td>
      <td>29</td>
      <td>4</td>
    </tr>
    <tr>
      <th>2</th>
      <td>333</td>
      <td>Mitch</td>
      <td>38</td>
      <td>9</td>
    </tr>
    <tr>
      <th>3</th>
      <td>444</td>
      <td>Bird</td>
      <td>20</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 경력이 3년 이상인 직원들의 데이터를 가져와라!
```


```python
df['Years of Experience'] >= 3
```




    0     True
    1     True
    2     True
    3    False
    Name: Years of Experience, dtype: bool




```python
df.loc[df['Years of Experience'] >= 3 ]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Employee ID</th>
      <th>Employee Name</th>
      <th>Salary [$/h]</th>
      <th>Years of Experience</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>111</td>
      <td>Chanel</td>
      <td>35</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>222</td>
      <td>Steve</td>
      <td>29</td>
      <td>4</td>
    </tr>
    <tr>
      <th>2</th>
      <td>333</td>
      <td>Mitch</td>
      <td>38</td>
      <td>9</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.iloc[df['Years of Experience'] >= 3 ]    ##iloc는 안된다
```


    ---------------------------------------------------------------------------

    NotImplementedError                       Traceback (most recent call last)

    <ipython-input-511-5e64c11749f4> in <module>
    ----> 1 df.iloc[df['Years of Experience'] >= 3 ]    ##iloc는 안된다
    

    ~\anaconda3\lib\site-packages\pandas\core\indexing.py in __getitem__(self, key)
        893 
        894             maybe_callable = com.apply_if_callable(key, self.obj)
    --> 895             return self._getitem_axis(maybe_callable, axis=axis)
        896 
        897     def _is_scalar_access(self, key: Tuple):


    ~\anaconda3\lib\site-packages\pandas\core\indexing.py in _getitem_axis(self, key, axis)
       1485 
       1486         if com.is_bool_indexer(key):
    -> 1487             self._validate_key(key, axis)
       1488             return self._getbool_axis(key, axis=axis)
       1489 


    ~\anaconda3\lib\site-packages\pandas\core\indexing.py in _validate_key(self, key, axis)
       1342             if hasattr(key, "index") and isinstance(key.index, Index):
       1343                 if key.index.inferred_type == "integer":
    -> 1344                     raise NotImplementedError(
       1345                         "iLocation based boolean "
       1346                         "indexing on an integer type "


    NotImplementedError: iLocation based boolean indexing on an integer type is not available



```python
df.columns
```




    Index(['Employee ID', 'Employee Name', 'Salary [$/h]', 'Years of Experience'], dtype='object')




```python
# 경력이 3년 이상인 직원들의 이름을 가져와라
```


```python
df['Years of Experience'] >=3
```




    0     True
    1     True
    2     True
    3    False
    Name: Years of Experience, dtype: bool




```python
df.loc[df['Years of Experience'] >=3, ['Employee Name','Salary [$/h]']]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Employee Name</th>
      <th>Salary [$/h]</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Chanel</td>
      <td>35</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Steve</td>
      <td>29</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Mitch</td>
      <td>38</td>
    </tr>
  </tbody>
</table>
</div>




```python

```


```python
# 경력이 3년 이상이고, 시급은 30달러 이상인 직원의 데이터를 가져오시오
```


```python
(df['Years of Experience'] >= 3) & (df['Salary [$/h]'] >= 30)
```




    0     True
    1    False
    2     True
    3    False
    dtype: bool




```python
df.loc[(df['Years of Experience'] >= 3) & (df['Salary [$/h]'] >= 30),]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Employee ID</th>
      <th>Employee Name</th>
      <th>Salary [$/h]</th>
      <th>Years of Experience</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>111</td>
      <td>Chanel</td>
      <td>35</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>333</td>
      <td>Mitch</td>
      <td>38</td>
      <td>9</td>
    </tr>
  </tbody>
</table>
</div>




```python

```


```python
# 컬럼의 이름 바꾸기
```


```python
df    #Employee ID -> ID
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Employee ID</th>
      <th>Employee Name</th>
      <th>Salary [$/h]</th>
      <th>Years of Experience</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>111</td>
      <td>Chanel</td>
      <td>35</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>222</td>
      <td>Steve</td>
      <td>29</td>
      <td>4</td>
    </tr>
    <tr>
      <th>2</th>
      <td>333</td>
      <td>Mitch</td>
      <td>38</td>
      <td>9</td>
    </tr>
    <tr>
      <th>3</th>
      <td>444</td>
      <td>Bird</td>
      <td>20</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.rename(columns={'Employee ID' : 'ID'}, inplace = True)   #inplace 는 이 메모리의 데이터 자체를 바꿔라!
```


```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>Employee Name</th>
      <th>Salary [$/h]</th>
      <th>Years of Experience</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>111</td>
      <td>Chanel</td>
      <td>35</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>222</td>
      <td>Steve</td>
      <td>29</td>
      <td>4</td>
    </tr>
    <tr>
      <th>2</th>
      <td>333</td>
      <td>Mitch</td>
      <td>38</td>
      <td>9</td>
    </tr>
    <tr>
      <th>3</th>
      <td>444</td>
      <td>Bird</td>
      <td>20</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python

```


```python
df.rename(columns = {'Employee Name' : 'Name', 'Salary [$/h]' : 'Salary'}, inplace=True)
```


```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>Name</th>
      <th>Salary</th>
      <th>Years of Experience</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>111</td>
      <td>Chanel</td>
      <td>35</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>222</td>
      <td>Steve</td>
      <td>29</td>
      <td>4</td>
    </tr>
    <tr>
      <th>2</th>
      <td>333</td>
      <td>Mitch</td>
      <td>38</td>
      <td>9</td>
    </tr>
    <tr>
      <th>3</th>
      <td>444</td>
      <td>Bird</td>
      <td>20</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python

```


```python
df.rename(columns = {'Years of Experience' : 'Experience'} , inplace=True)
```


```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>Name</th>
      <th>Salary</th>
      <th>Experience</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>111</td>
      <td>Chanel</td>
      <td>35</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>222</td>
      <td>Steve</td>
      <td>29</td>
      <td>4</td>
    </tr>
    <tr>
      <th>2</th>
      <td>333</td>
      <td>Mitch</td>
      <td>38</td>
      <td>9</td>
    </tr>
    <tr>
      <th>3</th>
      <td>444</td>
      <td>Bird</td>
      <td>20</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python

```

# APPLYING FUNCTIONS


```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>Name</th>
      <th>Salary</th>
      <th>Experience</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>111</td>
      <td>Chanel</td>
      <td>35</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>222</td>
      <td>Steve</td>
      <td>29</td>
      <td>4</td>
    </tr>
    <tr>
      <th>2</th>
      <td>333</td>
      <td>Mitch</td>
      <td>38</td>
      <td>9</td>
    </tr>
    <tr>
      <th>3</th>
      <td>444</td>
      <td>Bird</td>
      <td>20</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
df['Name']
```




    0    Chanel
    1     Steve
    2     Mitch
    3      Bird
    Name: Name, dtype: object




```python
# apply 함수는, 해당 컬럼의 값을, 오른쪽 ㅁapply 함수안에 넣은 len의 인자로 df['Name']을 넣어라 라는 뜻
```


```python
df['Name'].apply(len)
```




    0    6
    1    5
    2    5
    3    4
    Name: Name, dtype: int64




```python
df['length'] = df['Name'].apply(len)
```


```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>Name</th>
      <th>Salary</th>
      <th>Experience</th>
      <th>length</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>111</td>
      <td>Chanel</td>
      <td>35</td>
      <td>3</td>
      <td>6</td>
    </tr>
    <tr>
      <th>1</th>
      <td>222</td>
      <td>Steve</td>
      <td>29</td>
      <td>4</td>
      <td>5</td>
    </tr>
    <tr>
      <th>2</th>
      <td>333</td>
      <td>Mitch</td>
      <td>38</td>
      <td>9</td>
      <td>5</td>
    </tr>
    <tr>
      <th>3</th>
      <td>444</td>
      <td>Bird</td>
      <td>20</td>
      <td>1</td>
      <td>4</td>
    </tr>
  </tbody>
</table>
</div>




```python

```

#                                       ****************중요***************                                   Salary 컬럼의 값이 35 이상이면'고연봉', 그렇지 않으면 '저연봉' 이라는 정보고, 새로운 컬럼 '연봉'을 만드세요.


```python
def get_grade(salary):
    if salary >35:
        return '고연봉'
    else:
        return '저연봉'
```


```python
df['연봉'] = df['Salary'].apply(get_grade)
```


```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>Name</th>
      <th>Salary</th>
      <th>Experience</th>
      <th>length</th>
      <th>연봉</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>111</td>
      <td>Chanel</td>
      <td>35</td>
      <td>3</td>
      <td>6</td>
      <td>저연봉</td>
    </tr>
    <tr>
      <th>1</th>
      <td>222</td>
      <td>Steve</td>
      <td>29</td>
      <td>4</td>
      <td>5</td>
      <td>저연봉</td>
    </tr>
    <tr>
      <th>2</th>
      <td>333</td>
      <td>Mitch</td>
      <td>38</td>
      <td>9</td>
      <td>5</td>
      <td>고연봉</td>
    </tr>
    <tr>
      <th>3</th>
      <td>444</td>
      <td>Bird</td>
      <td>20</td>
      <td>1</td>
      <td>4</td>
      <td>저연봉</td>
    </tr>
  </tbody>
</table>
</div>




```python

```


```python

```

# SORTING AND ORDERING


```python
df = pd.DataFrame({'Employee ID':[111, 222, 333, 444], 
                   'Employee Name':['Chanel', 'Steve', 'Mitch', 'Bird'], 
                   'Salary [$/h]':[35, 29, 38, 20], 
                   'Years of Experience':[3, 4 ,9, 1]})
df

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Employee ID</th>
      <th>Employee Name</th>
      <th>Salary [$/h]</th>
      <th>Years of Experience</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>111</td>
      <td>Chanel</td>
      <td>35</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>222</td>
      <td>Steve</td>
      <td>29</td>
      <td>4</td>
    </tr>
    <tr>
      <th>2</th>
      <td>333</td>
      <td>Mitch</td>
      <td>38</td>
      <td>9</td>
    </tr>
    <tr>
      <th>3</th>
      <td>444</td>
      <td>Bird</td>
      <td>20</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.sort_values('Years of Experience', ascending=False, inplace = True)
```


```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Employee ID</th>
      <th>Employee Name</th>
      <th>Salary [$/h]</th>
      <th>Years of Experience</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2</th>
      <td>333</td>
      <td>Mitch</td>
      <td>38</td>
      <td>9</td>
    </tr>
    <tr>
      <th>1</th>
      <td>222</td>
      <td>Steve</td>
      <td>29</td>
      <td>4</td>
    </tr>
    <tr>
      <th>0</th>
      <td>111</td>
      <td>Chanel</td>
      <td>35</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>444</td>
      <td>Bird</td>
      <td>20</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.sort_values(['Years of Experience','Salary [$/h]'], ascending=[False,True])
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Employee ID</th>
      <th>Employee Name</th>
      <th>Salary [$/h]</th>
      <th>Years of Experience</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2</th>
      <td>333</td>
      <td>Mitch</td>
      <td>38</td>
      <td>9</td>
    </tr>
    <tr>
      <th>1</th>
      <td>222</td>
      <td>Steve</td>
      <td>29</td>
      <td>4</td>
    </tr>
    <tr>
      <th>0</th>
      <td>111</td>
      <td>Chanel</td>
      <td>35</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>444</td>
      <td>Bird</td>
      <td>20</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python

```

# CONCATENATING AND MERGING

![image.png](attachment:image.png)
Reference: https://pandas.pydata.org/pandas-docs/stable/merging.html


```python
df1 = pd.DataFrame({'A': ['A0', 'A1', 'A2', 'A3'],
                    'B': ['B0', 'B1', 'B2', 'B3'],
                    'C': ['C0', 'C1', 'C2', 'C3'],
                    'D': ['D0', 'D1', 'D2', 'D3']},
index=[0, 1, 2, 3])
```


```python
df1
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>A0</td>
      <td>B0</td>
      <td>C0</td>
      <td>D0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>A1</td>
      <td>B1</td>
      <td>C1</td>
      <td>D1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>A2</td>
      <td>B2</td>
      <td>C2</td>
      <td>D2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>A3</td>
      <td>B3</td>
      <td>C3</td>
      <td>D3</td>
    </tr>
  </tbody>
</table>
</div>




```python

```


```python
df2 = pd.DataFrame({'A': ['A4', 'A5', 'A6', 'A7'],
                    'B': ['B4', 'B5', 'B6', 'B7'],
                    'C': ['C4', 'C5', 'C6', 'C7'],
                    'D': ['D4', 'D5', 'D6', 'D7']},
index=[4, 5, 6, 7]) 
```


```python
df2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>4</th>
      <td>A4</td>
      <td>B4</td>
      <td>C4</td>
      <td>D4</td>
    </tr>
    <tr>
      <th>5</th>
      <td>A5</td>
      <td>B5</td>
      <td>C5</td>
      <td>D5</td>
    </tr>
    <tr>
      <th>6</th>
      <td>A6</td>
      <td>B6</td>
      <td>C6</td>
      <td>D6</td>
    </tr>
    <tr>
      <th>7</th>
      <td>A7</td>
      <td>B7</td>
      <td>C7</td>
      <td>D7</td>
    </tr>
  </tbody>
</table>
</div>




```python

```


```python
df3 = pd.DataFrame({'A': ['A8', 'A9', 'A10', 'A11'],
                    'B': ['B8', 'B9', 'B10', 'B11'],
                    'C': ['C8', 'C9', 'C10', 'C11'],
                    'D': ['D8', 'D9', 'D10', 'D11']},
index=[8, 9, 10, 11])
```


```python
df3
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>8</th>
      <td>A8</td>
      <td>B8</td>
      <td>C8</td>
      <td>D8</td>
    </tr>
    <tr>
      <th>9</th>
      <td>A9</td>
      <td>B9</td>
      <td>C9</td>
      <td>D9</td>
    </tr>
    <tr>
      <th>10</th>
      <td>A10</td>
      <td>B10</td>
      <td>C10</td>
      <td>D10</td>
    </tr>
    <tr>
      <th>11</th>
      <td>A11</td>
      <td>B11</td>
      <td>C11</td>
      <td>D11</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.concat([df1,df2,df3])
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>A0</td>
      <td>B0</td>
      <td>C0</td>
      <td>D0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>A1</td>
      <td>B1</td>
      <td>C1</td>
      <td>D1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>A2</td>
      <td>B2</td>
      <td>C2</td>
      <td>D2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>A3</td>
      <td>B3</td>
      <td>C3</td>
      <td>D3</td>
    </tr>
    <tr>
      <th>4</th>
      <td>A4</td>
      <td>B4</td>
      <td>C4</td>
      <td>D4</td>
    </tr>
    <tr>
      <th>5</th>
      <td>A5</td>
      <td>B5</td>
      <td>C5</td>
      <td>D5</td>
    </tr>
    <tr>
      <th>6</th>
      <td>A6</td>
      <td>B6</td>
      <td>C6</td>
      <td>D6</td>
    </tr>
    <tr>
      <th>7</th>
      <td>A7</td>
      <td>B7</td>
      <td>C7</td>
      <td>D7</td>
    </tr>
    <tr>
      <th>8</th>
      <td>A8</td>
      <td>B8</td>
      <td>C8</td>
      <td>D8</td>
    </tr>
    <tr>
      <th>9</th>
      <td>A9</td>
      <td>B9</td>
      <td>C9</td>
      <td>D9</td>
    </tr>
    <tr>
      <th>10</th>
      <td>A10</td>
      <td>B10</td>
      <td>C10</td>
      <td>D10</td>
    </tr>
    <tr>
      <th>11</th>
      <td>A11</td>
      <td>B11</td>
      <td>C11</td>
      <td>D11</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.concat([df3, df2, df1])
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>8</th>
      <td>A8</td>
      <td>B8</td>
      <td>C8</td>
      <td>D8</td>
    </tr>
    <tr>
      <th>9</th>
      <td>A9</td>
      <td>B9</td>
      <td>C9</td>
      <td>D9</td>
    </tr>
    <tr>
      <th>10</th>
      <td>A10</td>
      <td>B10</td>
      <td>C10</td>
      <td>D10</td>
    </tr>
    <tr>
      <th>11</th>
      <td>A11</td>
      <td>B11</td>
      <td>C11</td>
      <td>D11</td>
    </tr>
    <tr>
      <th>4</th>
      <td>A4</td>
      <td>B4</td>
      <td>C4</td>
      <td>D4</td>
    </tr>
    <tr>
      <th>5</th>
      <td>A5</td>
      <td>B5</td>
      <td>C5</td>
      <td>D5</td>
    </tr>
    <tr>
      <th>6</th>
      <td>A6</td>
      <td>B6</td>
      <td>C6</td>
      <td>D6</td>
    </tr>
    <tr>
      <th>7</th>
      <td>A7</td>
      <td>B7</td>
      <td>C7</td>
      <td>D7</td>
    </tr>
    <tr>
      <th>0</th>
      <td>A0</td>
      <td>B0</td>
      <td>C0</td>
      <td>D0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>A1</td>
      <td>B1</td>
      <td>C1</td>
      <td>D1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>A2</td>
      <td>B2</td>
      <td>C2</td>
      <td>D2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>A3</td>
      <td>B3</td>
      <td>C3</td>
      <td>D3</td>
    </tr>
  </tbody>
</table>
</div>




```python

```


```python
# Creating a dataframe from a dictionary     #기술팀의 직원 정보
raw_data = {
        'Employee ID': ['1', '2', '3', '4', '5'],
        'first name': ['Diana', 'Cynthia', 'Shep', 'Ryan', 'Allen'], 
        'last name': ['Bouchard', 'Ali', 'Rob', 'Mitch', 'Steve']}
df_Engineering_dept = pd.DataFrame(raw_data, columns = ['Employee ID', 'first name', 'last name'])
df_Engineering_dept
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Employee ID</th>
      <th>first name</th>
      <th>last name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Diana</td>
      <td>Bouchard</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Cynthia</td>
      <td>Ali</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>Shep</td>
      <td>Rob</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>Ryan</td>
      <td>Mitch</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>Allen</td>
      <td>Steve</td>
    </tr>
  </tbody>
</table>
</div>




```python
raw_data = {
        'Employee ID': ['6', '7', '8', '9', '10'],
        'first name': ['Bill', 'Dina', 'Sarah', 'Heather', 'Holly'], 
        'last name': ['Christian', 'Mo', 'Steve', 'Bob', 'Michelle']}
df_Finance_dept = pd.DataFrame(raw_data, columns = ['Employee ID', 'first name', 'last name'])
df_Finance_dept
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Employee ID</th>
      <th>first name</th>
      <th>last name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>6</td>
      <td>Bill</td>
      <td>Christian</td>
    </tr>
    <tr>
      <th>1</th>
      <td>7</td>
      <td>Dina</td>
      <td>Mo</td>
    </tr>
    <tr>
      <th>2</th>
      <td>8</td>
      <td>Sarah</td>
      <td>Steve</td>
    </tr>
    <tr>
      <th>3</th>
      <td>9</td>
      <td>Heather</td>
      <td>Bob</td>
    </tr>
    <tr>
      <th>4</th>
      <td>10</td>
      <td>Holly</td>
      <td>Michelle</td>
    </tr>
  </tbody>
</table>
</div>




```python
raw_data = {
        'Employee ID': ['1', '2', '3', '4', '5', '7', '8', '9', '10'],
        'Salary [$/hour]': [25, 35, 45, 48, 49, 32, 33, 34, 23]}
df_salary = pd.DataFrame(raw_data, columns = ['Employee ID','Salary [$/hour]'])
df_salary
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Employee ID</th>
      <th>Salary [$/hour]</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>25</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>35</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>45</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>48</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>49</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>32</td>
    </tr>
    <tr>
      <th>6</th>
      <td>8</td>
      <td>33</td>
    </tr>
    <tr>
      <th>7</th>
      <td>9</td>
      <td>34</td>
    </tr>
    <tr>
      <th>8</th>
      <td>10</td>
      <td>23</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_all = pd.concat([df_Engineering_dept,df_Finance_dept])
```


```python
df_all
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Employee ID</th>
      <th>first name</th>
      <th>last name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Diana</td>
      <td>Bouchard</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Cynthia</td>
      <td>Ali</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>Shep</td>
      <td>Rob</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>Ryan</td>
      <td>Mitch</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>Allen</td>
      <td>Steve</td>
    </tr>
    <tr>
      <th>0</th>
      <td>6</td>
      <td>Bill</td>
      <td>Christian</td>
    </tr>
    <tr>
      <th>1</th>
      <td>7</td>
      <td>Dina</td>
      <td>Mo</td>
    </tr>
    <tr>
      <th>2</th>
      <td>8</td>
      <td>Sarah</td>
      <td>Steve</td>
    </tr>
    <tr>
      <th>3</th>
      <td>9</td>
      <td>Heather</td>
      <td>Bob</td>
    </tr>
    <tr>
      <th>4</th>
      <td>10</td>
      <td>Holly</td>
      <td>Michelle</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_salary
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Employee ID</th>
      <th>Salary [$/hour]</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>25</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>35</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>45</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>48</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>49</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>32</td>
    </tr>
    <tr>
      <th>6</th>
      <td>8</td>
      <td>33</td>
    </tr>
    <tr>
      <th>7</th>
      <td>9</td>
      <td>34</td>
    </tr>
    <tr>
      <th>8</th>
      <td>10</td>
      <td>23</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.merge(df_all, df_salary, on='Employee ID')     ### merge는 딱 두가지 데이터프레임밖에 못합친다. on은 무엇을 매개로 합칠지 정해줌
                                                  ### 그러나 ID 6번 행이 사라졌다
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Employee ID</th>
      <th>first name</th>
      <th>last name</th>
      <th>Salary [$/hour]</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Diana</td>
      <td>Bouchard</td>
      <td>25</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Cynthia</td>
      <td>Ali</td>
      <td>35</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>Shep</td>
      <td>Rob</td>
      <td>45</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>Ryan</td>
      <td>Mitch</td>
      <td>48</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>Allen</td>
      <td>Steve</td>
      <td>49</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>Dina</td>
      <td>Mo</td>
      <td>32</td>
    </tr>
    <tr>
      <th>6</th>
      <td>8</td>
      <td>Sarah</td>
      <td>Steve</td>
      <td>33</td>
    </tr>
    <tr>
      <th>7</th>
      <td>9</td>
      <td>Heather</td>
      <td>Bob</td>
      <td>34</td>
    </tr>
    <tr>
      <th>8</th>
      <td>10</td>
      <td>Holly</td>
      <td>Michelle</td>
      <td>23</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.merge(df_all, df_salary, on='Employee ID', how='left')  ### how는('left') 는 왼쪽 데이터프레임에 있는 것을 모두 표시해라!
```


    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    <ipython-input-605-b6838987659e> in <module>
    ----> 1 pd.merge(df_all, df_salary, on='Employee ID', how='all')  ### how는 왼쪽 데이터프레임에 있는 것을 모두 표시해라!
    

    ~\anaconda3\lib\site-packages\pandas\core\reshape\merge.py in merge(left, right, how, on, left_on, right_on, left_index, right_index, sort, suffixes, copy, indicator, validate)
         87         validate=validate,
         88     )
    ---> 89     return op.get_result()
         90 
         91 


    ~\anaconda3\lib\site-packages\pandas\core\reshape\merge.py in get_result(self)
        682             self.left, self.right = self._indicator_pre_merge(self.left, self.right)
        683 
    --> 684         join_index, left_indexer, right_indexer = self._get_join_info()
        685 
        686         llabels, rlabels = _items_overlap_with_suffix(


    ~\anaconda3\lib\site-packages\pandas\core\reshape\merge.py in _get_join_info(self)
        907             )
        908         else:
    --> 909             (left_indexer, right_indexer) = self._get_join_indexers()
        910 
        911             if self.right_index:


    ~\anaconda3\lib\site-packages\pandas\core\reshape\merge.py in _get_join_indexers(self)
        885     def _get_join_indexers(self):
        886         """ return the join indexers """
    --> 887         return get_join_indexers(
        888             self.left_join_keys, self.right_join_keys, sort=self.sort, how=self.how
        889         )


    ~\anaconda3\lib\site-packages\pandas\core\reshape\merge.py in get_join_indexers(left_keys, right_keys, sort, how, **kwargs)
       1430     if how in ("left", "right"):
       1431         kwargs["sort"] = sort
    -> 1432     join_func = {
       1433         "inner": libjoin.inner_join,
       1434         "left": libjoin.left_outer_join,


    KeyError: 'all'



```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```

# EXCELLENT JOB!


```python

```
