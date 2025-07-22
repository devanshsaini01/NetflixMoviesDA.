```python
import pandas as pd
```


```python
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```


```python
df = pd.read_csv('mymoviedb.csv',lineterminator = '\n')
```


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
      <th>Release_Date</th>
      <th>Title</th>
      <th>Overview</th>
      <th>Popularity</th>
      <th>Vote_Count</th>
      <th>Vote_Average</th>
      <th>Original_Language</th>
      <th>Genre</th>
      <th>Poster_Url</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2021-12-15</td>
      <td>Spider-Man: No Way Home</td>
      <td>Peter Parker is unmasked and no longer able to...</td>
      <td>5083.954</td>
      <td>8940</td>
      <td>8.3</td>
      <td>en</td>
      <td>Action, Adventure, Science Fiction</td>
      <td>https://image.tmdb.org/t/p/original/1g0dhYtq4i...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2022-03-01</td>
      <td>The Batman</td>
      <td>In his second year of fighting crime, Batman u...</td>
      <td>3827.658</td>
      <td>1151</td>
      <td>8.1</td>
      <td>en</td>
      <td>Crime, Mystery, Thriller</td>
      <td>https://image.tmdb.org/t/p/original/74xTEgt7R3...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2022-02-25</td>
      <td>No Exit</td>
      <td>Stranded at a rest stop in the mountains durin...</td>
      <td>2618.087</td>
      <td>122</td>
      <td>6.3</td>
      <td>en</td>
      <td>Thriller</td>
      <td>https://image.tmdb.org/t/p/original/vDHsLnOWKl...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2021-11-24</td>
      <td>Encanto</td>
      <td>The tale of an extraordinary family, the Madri...</td>
      <td>2402.201</td>
      <td>5076</td>
      <td>7.7</td>
      <td>en</td>
      <td>Animation, Comedy, Family, Fantasy</td>
      <td>https://image.tmdb.org/t/p/original/4j0PNHkMr5...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2021-12-22</td>
      <td>The King's Man</td>
      <td>As a collection of history's worst tyrants and...</td>
      <td>1895.511</td>
      <td>1793</td>
      <td>7.0</td>
      <td>en</td>
      <td>Action, Adventure, Thriller, War</td>
      <td>https://image.tmdb.org/t/p/original/aq4Pwv5Xeu...</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 9827 entries, 0 to 9826
    Data columns (total 9 columns):
     #   Column             Non-Null Count  Dtype  
    ---  ------             --------------  -----  
     0   Release_Date       9827 non-null   object 
     1   Title              9827 non-null   object 
     2   Overview           9827 non-null   object 
     3   Popularity         9827 non-null   float64
     4   Vote_Count         9827 non-null   int64  
     5   Vote_Average       9827 non-null   float64
     6   Original_Language  9827 non-null   object 
     7   Genre              9827 non-null   object 
     8   Poster_Url         9827 non-null   object 
    dtypes: float64(2), int64(1), object(6)
    memory usage: 691.1+ KB



```python
df['Genre'].head()
```




    0    Action, Adventure, Science Fiction
    1              Crime, Mystery, Thriller
    2                              Thriller
    3    Animation, Comedy, Family, Fantasy
    4      Action, Adventure, Thriller, War
    Name: Genre, dtype: object




```python
df.duplicated().sum()
```




    np.int64(0)




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
      <th>Popularity</th>
      <th>Vote_Count</th>
      <th>Vote_Average</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>9827.000000</td>
      <td>9827.000000</td>
      <td>9827.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>40.326088</td>
      <td>1392.805536</td>
      <td>6.439534</td>
    </tr>
    <tr>
      <th>std</th>
      <td>108.873998</td>
      <td>2611.206907</td>
      <td>1.129759</td>
    </tr>
    <tr>
      <th>min</th>
      <td>13.354000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>16.128500</td>
      <td>146.000000</td>
      <td>5.900000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>21.199000</td>
      <td>444.000000</td>
      <td>6.500000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>35.191500</td>
      <td>1376.000000</td>
      <td>7.100000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>5083.954000</td>
      <td>31077.000000</td>
      <td>10.000000</td>
    </tr>
  </tbody>
</table>
</div>


Exploratary Summary

->We have a dataframe consisting of 9827 rows & 9 columns.
->Our dataset looks a bit tidy with no NaNs nor duplicate values.
->Release_Date column needs to be casted into date time and to extract only the year value.
->Overview, Origina_language and Poster-Url wouldn't be so useful during analysis,so we'll drop them.
->There is noticible outlier in popularity column.
->Vote_Average better be categorised for proper analysis.
->Genre column has comma separated values and white spaces that needs to be handled and casted into category. 

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
      <th>Release_Date</th>
      <th>Title</th>
      <th>Overview</th>
      <th>Popularity</th>
      <th>Vote_Count</th>
      <th>Vote_Average</th>
      <th>Original_Language</th>
      <th>Genre</th>
      <th>Poster_Url</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2021-12-15</td>
      <td>Spider-Man: No Way Home</td>
      <td>Peter Parker is unmasked and no longer able to...</td>
      <td>5083.954</td>
      <td>8940</td>
      <td>8.3</td>
      <td>en</td>
      <td>Action, Adventure, Science Fiction</td>
      <td>https://image.tmdb.org/t/p/original/1g0dhYtq4i...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2022-03-01</td>
      <td>The Batman</td>
      <td>In his second year of fighting crime, Batman u...</td>
      <td>3827.658</td>
      <td>1151</td>
      <td>8.1</td>
      <td>en</td>
      <td>Crime, Mystery, Thriller</td>
      <td>https://image.tmdb.org/t/p/original/74xTEgt7R3...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2022-02-25</td>
      <td>No Exit</td>
      <td>Stranded at a rest stop in the mountains durin...</td>
      <td>2618.087</td>
      <td>122</td>
      <td>6.3</td>
      <td>en</td>
      <td>Thriller</td>
      <td>https://image.tmdb.org/t/p/original/vDHsLnOWKl...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2021-11-24</td>
      <td>Encanto</td>
      <td>The tale of an extraordinary family, the Madri...</td>
      <td>2402.201</td>
      <td>5076</td>
      <td>7.7</td>
      <td>en</td>
      <td>Animation, Comedy, Family, Fantasy</td>
      <td>https://image.tmdb.org/t/p/original/4j0PNHkMr5...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2021-12-22</td>
      <td>The King's Man</td>
      <td>As a collection of history's worst tyrants and...</td>
      <td>1895.511</td>
      <td>1793</td>
      <td>7.0</td>
      <td>en</td>
      <td>Action, Adventure, Thriller, War</td>
      <td>https://image.tmdb.org/t/p/original/aq4Pwv5Xeu...</td>
    </tr>
  </tbody>
</table>
</div>




```python
#->Release_Date column needs to be casted into date time and to extract only the year value.
```


```python
df["Release_Date"] = pd.to_datetime(df["Release_Date"])

print(df["Release_Date"].head())
```

    0   2021-12-15
    1   2022-03-01
    2   2022-02-25
    3   2021-11-24
    4   2021-12-22
    Name: Release_Date, dtype: datetime64[ns]



```python
df["Release_Date"] = pd.to_datetime(df["Release_Date"])

print(df["Release_Date"].dtypes)
```

    datetime64[ns]



```python
df["Release_Date"] = pd.to_datetime(df["Release_Date"]).dt.year
df["Release_Date"].dtype
```




    dtype('int32')




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
      <th>Release_Date</th>
      <th>Title</th>
      <th>Overview</th>
      <th>Popularity</th>
      <th>Vote_Count</th>
      <th>Vote_Average</th>
      <th>Original_Language</th>
      <th>Genre</th>
      <th>Poster_Url</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2021</td>
      <td>Spider-Man: No Way Home</td>
      <td>Peter Parker is unmasked and no longer able to...</td>
      <td>5083.954</td>
      <td>8940</td>
      <td>8.3</td>
      <td>en</td>
      <td>Action, Adventure, Science Fiction</td>
      <td>https://image.tmdb.org/t/p/original/1g0dhYtq4i...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2022</td>
      <td>The Batman</td>
      <td>In his second year of fighting crime, Batman u...</td>
      <td>3827.658</td>
      <td>1151</td>
      <td>8.1</td>
      <td>en</td>
      <td>Crime, Mystery, Thriller</td>
      <td>https://image.tmdb.org/t/p/original/74xTEgt7R3...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2022</td>
      <td>No Exit</td>
      <td>Stranded at a rest stop in the mountains durin...</td>
      <td>2618.087</td>
      <td>122</td>
      <td>6.3</td>
      <td>en</td>
      <td>Thriller</td>
      <td>https://image.tmdb.org/t/p/original/vDHsLnOWKl...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2021</td>
      <td>Encanto</td>
      <td>The tale of an extraordinary family, the Madri...</td>
      <td>2402.201</td>
      <td>5076</td>
      <td>7.7</td>
      <td>en</td>
      <td>Animation, Comedy, Family, Fantasy</td>
      <td>https://image.tmdb.org/t/p/original/4j0PNHkMr5...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2021</td>
      <td>The King's Man</td>
      <td>As a collection of history's worst tyrants and...</td>
      <td>1895.511</td>
      <td>1793</td>
      <td>7.0</td>
      <td>en</td>
      <td>Action, Adventure, Thriller, War</td>
      <td>https://image.tmdb.org/t/p/original/aq4Pwv5Xeu...</td>
    </tr>
  </tbody>
</table>
</div>




```python
#->Overview, Origina_language and Poster-Url wouldn't be so useful during analysis,so we'll drop them.
```


```python
cols= ['Overview','Original_Language','Poster_Url']
df.drop(cols,axis=1, inplace= True)
df.columns
```




    Index(['Release_Date', 'Title', 'Popularity', 'Vote_Count', 'Vote_Average',
           'Genre'],
          dtype='object')




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
      <th>Release_Date</th>
      <th>Title</th>
      <th>Popularity</th>
      <th>Vote_Count</th>
      <th>Vote_Average</th>
      <th>Genre</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2021</td>
      <td>Spider-Man: No Way Home</td>
      <td>5083.954</td>
      <td>8940</td>
      <td>8.3</td>
      <td>Action, Adventure, Science Fiction</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2022</td>
      <td>The Batman</td>
      <td>3827.658</td>
      <td>1151</td>
      <td>8.1</td>
      <td>Crime, Mystery, Thriller</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2022</td>
      <td>No Exit</td>
      <td>2618.087</td>
      <td>122</td>
      <td>6.3</td>
      <td>Thriller</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2021</td>
      <td>Encanto</td>
      <td>2402.201</td>
      <td>5076</td>
      <td>7.7</td>
      <td>Animation, Comedy, Family, Fantasy</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2021</td>
      <td>The King's Man</td>
      <td>1895.511</td>
      <td>1793</td>
      <td>7.0</td>
      <td>Action, Adventure, Thriller, War</td>
    </tr>
  </tbody>
</table>
</div>



categorizing Vote_Average column

We would cut the Vote_Average values and make 4 categories: popular, average ,below_average, not_popular to describe it more, using categorize_col() function provided above.


```python
#User Defined Function 

def categorize_col(df, col, labels):
    
    edges = [df[col].describe()['min'],
             df[col].describe()['25%'],
             df[col].describe()['50%'],
             df[col].describe()['75%'],
             df[col].describe()['max']]
    
    df[col] = pd.cut(df[col],edges , labels = labels, duplicates = 'drop')
    return df
```


```python
labels = ['Not_Popular','Below_Average','Average','Popular']

categorize_col(df, 'Vote_Average', labels)

df['Vote_Average'].unique()
```




    ['Popular', 'Below_Average', 'Average', 'Not_Popular', NaN]
    Categories (4, object): ['Not_Popular' < 'Below_Average' < 'Average' < 'Popular']




```python
df['Vote_Average'].value_counts()
```




    Vote_Average
    Not_Popular      2467
    Popular          2450
    Average          2412
    Below_Average    2398
    Name: count, dtype: int64




```python
df.dropna(inplace=True)
df.isna().sum()
```




    Release_Date    0
    Title           0
    Popularity      0
    Vote_Count      0
    Vote_Average    0
    Genre           0
    dtype: int64




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
      <th>Release_Date</th>
      <th>Title</th>
      <th>Popularity</th>
      <th>Vote_Count</th>
      <th>Vote_Average</th>
      <th>Genre</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2021</td>
      <td>Spider-Man: No Way Home</td>
      <td>5083.954</td>
      <td>8940</td>
      <td>Popular</td>
      <td>Action, Adventure, Science Fiction</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2022</td>
      <td>The Batman</td>
      <td>3827.658</td>
      <td>1151</td>
      <td>Popular</td>
      <td>Crime, Mystery, Thriller</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2022</td>
      <td>No Exit</td>
      <td>2618.087</td>
      <td>122</td>
      <td>Below_Average</td>
      <td>Thriller</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2021</td>
      <td>Encanto</td>
      <td>2402.201</td>
      <td>5076</td>
      <td>Popular</td>
      <td>Animation, Comedy, Family, Fantasy</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2021</td>
      <td>The King's Man</td>
      <td>1895.511</td>
      <td>1793</td>
      <td>Average</td>
      <td>Action, Adventure, Thriller, War</td>
    </tr>
  </tbody>
</table>
</div>



# we'd split the genres into a list and then explode our dataframe to a have a only one genre per row for each movie


```python
df["Genre"]= df["Genre"].str.split(', ')

df=df.explode('Genre').reset_index(drop=True)
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
      <th>Release_Date</th>
      <th>Title</th>
      <th>Popularity</th>
      <th>Vote_Count</th>
      <th>Vote_Average</th>
      <th>Genre</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2021</td>
      <td>Spider-Man: No Way Home</td>
      <td>5083.954</td>
      <td>8940</td>
      <td>Popular</td>
      <td>Action</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2021</td>
      <td>Spider-Man: No Way Home</td>
      <td>5083.954</td>
      <td>8940</td>
      <td>Popular</td>
      <td>Adventure</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2021</td>
      <td>Spider-Man: No Way Home</td>
      <td>5083.954</td>
      <td>8940</td>
      <td>Popular</td>
      <td>Science Fiction</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2022</td>
      <td>The Batman</td>
      <td>3827.658</td>
      <td>1151</td>
      <td>Popular</td>
      <td>Crime</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2022</td>
      <td>The Batman</td>
      <td>3827.658</td>
      <td>1151</td>
      <td>Popular</td>
      <td>Mystery</td>
    </tr>
  </tbody>
</table>
</div>




```python
#casting column into category

df['Genre']= df['Genre'].astype('category')

df['Genre'].dtype
```




    CategoricalDtype(categories=['Action', 'Adventure', 'Animation', 'Comedy', 'Crime',
                      'Documentary', 'Drama', 'Family', 'Fantasy', 'History',
                      'Horror', 'Music', 'Mystery', 'Romance', 'Science Fiction',
                      'TV Movie', 'Thriller', 'War', 'Western'],
    , ordered=False, categories_dtype=object)




```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 25552 entries, 0 to 25551
    Data columns (total 6 columns):
     #   Column        Non-Null Count  Dtype   
    ---  ------        --------------  -----   
     0   Release_Date  25552 non-null  int32   
     1   Title         25552 non-null  object  
     2   Popularity    25552 non-null  float64 
     3   Vote_Count    25552 non-null  int64   
     4   Vote_Average  25552 non-null  category
     5   Genre         25552 non-null  category
    dtypes: category(2), float64(1), int32(1), int64(1), object(1)
    memory usage: 749.6+ KB



```python
df.nunique()
```




    Release_Date     100
    Title           9415
    Popularity      8088
    Vote_Count      3265
    Vote_Average       4
    Genre             19
    dtype: int64




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
      <th>Release_Date</th>
      <th>Title</th>
      <th>Popularity</th>
      <th>Vote_Count</th>
      <th>Vote_Average</th>
      <th>Genre</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2021</td>
      <td>Spider-Man: No Way Home</td>
      <td>5083.954</td>
      <td>8940</td>
      <td>Popular</td>
      <td>Action</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2021</td>
      <td>Spider-Man: No Way Home</td>
      <td>5083.954</td>
      <td>8940</td>
      <td>Popular</td>
      <td>Adventure</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2021</td>
      <td>Spider-Man: No Way Home</td>
      <td>5083.954</td>
      <td>8940</td>
      <td>Popular</td>
      <td>Science Fiction</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2022</td>
      <td>The Batman</td>
      <td>3827.658</td>
      <td>1151</td>
      <td>Popular</td>
      <td>Crime</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2022</td>
      <td>The Batman</td>
      <td>3827.658</td>
      <td>1151</td>
      <td>Popular</td>
      <td>Mystery</td>
    </tr>
  </tbody>
</table>
</div>



Completely preprocessed Data.

# Data Visualization


```python
sns.set_style('whitegrid')

```

## What is the most frequent genre of movies released on Neteflix


```python
df['Genre'].describe()
```




    count     25552
    unique       19
    top       Drama
    freq       3715
    Name: Genre, dtype: object




```python
sns.catplot(y ='Genre', data = df, kind = 'count',
           order = df['Genre'].value_counts().index,
            color = '#4287f5')
plt.title('Genre column distribution')
plt.show()
```


    
![png](output_35_0.png)
    


## Which has highest votes in vote avg column?


```python
sns.catplot(y= 'Vote_Average', data = df, kind= 'count',
           order = df["Vote_Average"].value_counts().index,
            color= "#4287f5")
plt.title('Votes distribution')
plt.show()
```


    
![png](output_37_0.png)
    


## WHat movie got the highest popularity? whats its genre?


```python
df[df['Popularity'] == df['Popularity'].max()]
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
      <th>Release_Date</th>
      <th>Title</th>
      <th>Popularity</th>
      <th>Vote_Count</th>
      <th>Vote_Average</th>
      <th>Genre</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2021</td>
      <td>Spider-Man: No Way Home</td>
      <td>5083.954</td>
      <td>8940</td>
      <td>Popular</td>
      <td>Action</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2021</td>
      <td>Spider-Man: No Way Home</td>
      <td>5083.954</td>
      <td>8940</td>
      <td>Popular</td>
      <td>Adventure</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2021</td>
      <td>Spider-Man: No Way Home</td>
      <td>5083.954</td>
      <td>8940</td>
      <td>Popular</td>
      <td>Science Fiction</td>
    </tr>
  </tbody>
</table>
</div>



## What movie got the lowest popularity?Whats its genre?


```python
df[df['Popularity'] == df['Popularity'].min()]
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
      <th>Release_Date</th>
      <th>Title</th>
      <th>Popularity</th>
      <th>Vote_Count</th>
      <th>Vote_Average</th>
      <th>Genre</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>25546</th>
      <td>2021</td>
      <td>The United States vs. Billie Holiday</td>
      <td>13.354</td>
      <td>152</td>
      <td>Average</td>
      <td>Music</td>
    </tr>
    <tr>
      <th>25547</th>
      <td>2021</td>
      <td>The United States vs. Billie Holiday</td>
      <td>13.354</td>
      <td>152</td>
      <td>Average</td>
      <td>Drama</td>
    </tr>
    <tr>
      <th>25548</th>
      <td>2021</td>
      <td>The United States vs. Billie Holiday</td>
      <td>13.354</td>
      <td>152</td>
      <td>Average</td>
      <td>History</td>
    </tr>
    <tr>
      <th>25549</th>
      <td>1984</td>
      <td>Threads</td>
      <td>13.354</td>
      <td>186</td>
      <td>Popular</td>
      <td>War</td>
    </tr>
    <tr>
      <th>25550</th>
      <td>1984</td>
      <td>Threads</td>
      <td>13.354</td>
      <td>186</td>
      <td>Popular</td>
      <td>Drama</td>
    </tr>
    <tr>
      <th>25551</th>
      <td>1984</td>
      <td>Threads</td>
      <td>13.354</td>
      <td>186</td>
      <td>Popular</td>
      <td>Science Fiction</td>
    </tr>
  </tbody>
</table>
</div>



## Which year has the most filmmed movies?


```python
df['Release_Date'].hist()
plt.title("Release date column distribution")
plt.show()
```


    
![png](output_43_0.png)
    

Conclusion
Q1: WHat is the most frequent genre in the dataset?
-> Drama genre is the most frequent in our dataset and has appeared more than 14% of the time among 19 other genres.

Q2: What genre has highest votes?
-> We have 25.5% of our dataset with popular vote(6520rows).Drama again gets the highest popularity among fans by being having more than 18.5% of movies popularity.

Q3: What movie got the lowest popularity?whats its genre?
-> Spider Man: No Way Home has the highest popularity in our dataset and it has genre of Action, Adventure, and Science Fiction.

Q4: What movie got the lowest popularity?whats its genre?
-> The United States, thread has the lowest rate in our dataset and it has genre of music, drama, war, sci-fi and history.

Q5: Which year has the most Filmmed movies?
-> Year 2020 has the highest Filmmed rate in our dataset.