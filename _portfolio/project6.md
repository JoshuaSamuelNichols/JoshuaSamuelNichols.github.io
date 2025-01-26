---
title: Nashville Music School Student's Nationality Analysis
subtitle: Insights uncovered through Python-powered exploratory data analysis and visualizations.
image: assets/img/portfolio/06-full.jpg
alt: 

caption:
  title: Student Nationality
  subtitle: Jupyter Notebook, Python, Analytics
  thumbnail: assets/img/portfolio/06-thumbnail.jpg
---
# Nashville Music School (NMS) Nationality Analysis: Exploring Student Diversity


---

## Introduction


From 2015 to 2024, more than 100 students have engaged in private e-learning music lessons with me. Now, the burning question: Where in the world do these international students come from? *(Good Mythical Morning reference!)* There was such a diverse amount of students joining the school, I wanted to create a project that captures the experience that I gained.


## Python Libraries Import


```python
import pandas as pd
import matplotlib.pyplot as plt
```

## Data Import

I am using a consolidated Excel database without the students' names for confidentiality purposes


```python
df = pd.read_csv('NMSNationalityData.csv')
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
      <th>Country</th>
      <th>Count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Belgium</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Bolivia</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Brazil</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Croatia</td>
      <td>2</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Egypt</td>
      <td>4</td>
    </tr>
    <tr>
      <th>5</th>
      <td>El Salvador</td>
      <td>1</td>
    </tr>
    <tr>
      <th>6</th>
      <td>England</td>
      <td>9</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Ethiopia</td>
      <td>1</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Fiji</td>
      <td>1</td>
    </tr>
    <tr>
      <th>9</th>
      <td>France</td>
      <td>10</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Germany</td>
      <td>3</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Ghana</td>
      <td>2</td>
    </tr>
    <tr>
      <th>12</th>
      <td>India</td>
      <td>5</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Ireland</td>
      <td>6</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Israel</td>
      <td>3</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Italy</td>
      <td>4</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Ivory Coast</td>
      <td>1</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Jamaica</td>
      <td>1</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Japan</td>
      <td>2</td>
    </tr>
    <tr>
      <th>19</th>
      <td>Kazahkstan</td>
      <td>3</td>
    </tr>
    <tr>
      <th>20</th>
      <td>La Reunion</td>
      <td>3</td>
    </tr>
    <tr>
      <th>21</th>
      <td>Lithuania</td>
      <td>1</td>
    </tr>
    <tr>
      <th>22</th>
      <td>Madagascar</td>
      <td>1</td>
    </tr>
    <tr>
      <th>23</th>
      <td>Mongolia</td>
      <td>1</td>
    </tr>
    <tr>
      <th>24</th>
      <td>Morocco</td>
      <td>1</td>
    </tr>
    <tr>
      <th>25</th>
      <td>Namibia</td>
      <td>1</td>
    </tr>
    <tr>
      <th>26</th>
      <td>New Zealand</td>
      <td>1</td>
    </tr>
    <tr>
      <th>27</th>
      <td>Nigeria</td>
      <td>2</td>
    </tr>
    <tr>
      <th>28</th>
      <td>Papua New</td>
      <td>1</td>
    </tr>
    <tr>
      <th>29</th>
      <td>Phillipines</td>
      <td>2</td>
    </tr>
    <tr>
      <th>30</th>
      <td>Portugal</td>
      <td>2</td>
    </tr>
    <tr>
      <th>31</th>
      <td>Russia</td>
      <td>1</td>
    </tr>
    <tr>
      <th>32</th>
      <td>Scotland</td>
      <td>1</td>
    </tr>
    <tr>
      <th>33</th>
      <td>South Africa</td>
      <td>1</td>
    </tr>
    <tr>
      <th>34</th>
      <td>South Korea</td>
      <td>1</td>
    </tr>
    <tr>
      <th>35</th>
      <td>Spain</td>
      <td>2</td>
    </tr>
    <tr>
      <th>36</th>
      <td>Sweden</td>
      <td>2</td>
    </tr>
    <tr>
      <th>37</th>
      <td>Switzerland</td>
      <td>3</td>
    </tr>
    <tr>
      <th>38</th>
      <td>Togo</td>
      <td>1</td>
    </tr>
    <tr>
      <th>39</th>
      <td>Uganda</td>
      <td>3</td>
    </tr>
    <tr>
      <th>40</th>
      <td>USA</td>
      <td>5</td>
    </tr>
    <tr>
      <th>41</th>
      <td>Vietnam</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>



## Total of Students at Nashville Music School


```python
total_students = df['Count'].sum()
total_students
```




    100



## Plot


```python
plt.figure(figsize=(12,6))
plt.bar(df['Country'], df['Count'])
plt.xlabel('Country')
plt.ylabel('Count')
plt.title('Number of Nashville Music School Students by Country')
plt.xticks(rotation=45, ha='right')
plt.tight_layout()
plt.show()
```


   
![png](output_10_0.png)
   


The majority of the students would be from France, England, India, Ireland and the USA as Geneva is a very diverse francophone and anglophone region. The region of [Auvergne-Rhône-Alpes](https://en.wikipedia.org/wiki/Auvergne-Rh%C3%B4ne-Alpes) in France, is primarily French speaking, so that would explain the high amounts of students from France attending.

### Data Sorting by Count


```python
df_sorted = df.sort_values(by='Count', ascending=False)

# Display the sorted list of countries
sorted_countries_list = df_sorted[['Country', 'Count']]
print(sorted_countries_list.to_string(index=False))
```

         Country  Count
          France     10
         England      9
         Ireland      6
           India      5
             USA      5
           Egypt      4
           Italy      4
         Belgium      3
      La Reunion      3
      Kazahkstan      3
          Israel      3
          Uganda      3
     Switzerland      3
         Germany      3
           Japan      2
     Phillipines      2
        Portugal      2
         Croatia      2
           Ghana      2
           Spain      2
          Sweden      2
         Nigeria      2
     South Korea      1
    South Africa      1
        Scotland      1
          Russia      1
            Togo      1
       Papua New      1
       Lithuania      1
     New Zealand      1
         Namibia      1
         Morocco      1
        Mongolia      1
      Madagascar      1
         Bolivia      1
         Jamaica      1
     Ivory Coast      1
            Fiji      1
        Ethiopia      1
     El Salvador      1
          Brazil      1
         Vietnam      1
   

# Frequency Analysis

### Most Frequent


```python
df = df.sort_values(by='Count', ascending=False)

top_countries = 10
df_top = df.head(top_countries)

plt.figure(figsize=(10, 8))
plt.pie(df_top['Count'], labels=df_top['Country'], autopct='%1.1f%%', startangle=90, counterclock=False, wedgeprops=dict(width=0.4))
plt.axis('equal')  
plt.title('Top 10 Most Frequent Countries of Students')
plt.show()
```


   
![png](output_16_0.png)
   



```python
print(df_top.to_string(index=False))
```

       Country  Count
        France     10
       England      9
       Ireland      6
         India      5
           USA      5
         Egypt      4
         Italy      4
       Belgium      3
    La Reunion      3
    Kazahkstan      3
   

### Least Frequent


```python
df_lowest_counts = df[df['Count'].isin([1, 2])]

df_lowest_counts_sorted = df_lowest_counts.sort_values(by='Count')

sorted_lowest_counts_list = df_lowest_counts_sorted[['Country', 'Count']]
print(sorted_lowest_counts_list.to_string(index=False))
```

         Country  Count
       Papua New      1
     El Salvador      1
        Ethiopia      1
            Fiji      1
     Ivory Coast      1
         Jamaica      1
         Bolivia      1
      Madagascar      1
        Mongolia      1
         Morocco      1
         Namibia      1
     New Zealand      1
       Lithuania      1
         Vietnam      1
            Togo      1
          Russia      1
        Scotland      1
    South Africa      1
     South Korea      1
          Brazil      1
         Nigeria      2
          Sweden      2
           Spain      2
           Ghana      2
         Croatia      2
        Portugal      2
     Phillipines      2
           Japan      2
   

These nationalities were least frequently found at the school.

# Statistics

### Annual Retention Statistics


```python
data = {'Year': [2015, 2016, 2017, 2018, 2019, 2020, 2021, 2022, 2023, 2024],
        'Number of Students': [4, 13, 12, 11, 19, 24, 36, 23, 17, 2]}

df_students_per_year = pd.DataFrame(data)

plt.figure(figsize=(12, 6))
colors = plt.cm.viridis(df_students_per_year['Number of Students'] / max(df_students_per_year['Number of Students']))
bars = plt.bar(df_students_per_year['Year'], df_students_per_year['Number of Students'], color=colors)

plt.xticks(df_students_per_year['Year'])

for bar in bars:
    yval = bar.get_height()
    plt.text(bar.get_x() + bar.get_width()/2, yval, round(yval, 1), ha='center', va='bottom')

plt.xlabel('Year')
plt.ylabel('Number of Students')
plt.title('Number of Students per Year')
plt.show()
```


   
![png](output_23_0.png)
   


This plot illustrates the total number of students per year, capturing a dynamic snapshot of the music school's growth and evolution. It's noteworthy that the student body comprises individuals with varying durations of engagement, including those who enrolled once, stayed for multiple years, took breaks, or returned later.

### Average amount of students during pandemic years


```python
df_students_per_year = pd.DataFrame(data)

df_selected_years = df_students_per_year[(df_students_per_year['Year'] >= 2019) & (df_students_per_year['Year'] <= 2023)]

average_students = df_selected_years['Number of Students'].mean()
std_deviation_students = df_selected_years['Number of Students'].std()
min_students = df_selected_years['Number of Students'].min()
max_students = df_selected_years['Number of Students'].max()

print(f"Statistics for the years 2019-2023:")
print(f"Average Number of Students: {average_students:.2f}")
print(f"Standard Deviation: {std_deviation_students:.2f}")
print(f"Minimum Number of Students: {min_students}")
print(f"Maximum Number of Students: {max_students}")

```

    Statistics for the years 2019-2023:
    Average Number of Students: 23.80
    Standard Deviation: 7.40
    Minimum Number of Students: 17
    Maximum Number of Students: 36
   

### Total Student Count (Including Recurring)


```python
df_students_per_year = pd.DataFrame(data)

total_students = df_students_per_year['Number of Students'].sum()

print(f"Total Number of Students: {total_students}")
```

    Total Number of Students: 161
   

# Conclusions


### Where are they from?
Given the data on the number of students, **English-speaking** and **French-speaking** students have the highest numbers in frequencies.

### What does this imply?
This observation implies Geneva's appeal as an educational hub, particularly for those interested in traditional [African-American standardized music](https://en.wikipedia.org/wiki/African-American_music) courses. The diverse student representation aligns seamlessly with Geneva's international and multicultural environment.


### Pandemic?
Despite the challenges posed by the global pandemic, the music school witnessed a remarkable surge in student enrollment, reaching its peak between 2019 and 2022. This resilience and sustained interest in music education during challenging times reflect the enduring impact and significance of the institution.

### Statistics
The diversity of student experiences, including those who stayed for several years, pursued education abroad, or returned after breaks, contributes to the rich tapestry of the music school's history. Each year tells a unique story of musical growth and shared learning experiences. The correlation between student enrollment and the linguistic diversity of the region underscores the inclusive and international nature in Geneva.


# Socials

Follow me on:
- [GitHub](https://github.com/JoshuaSamuelNichols)
- [LinkedIn](https://www.linkedin.com/in/mrnichols/)
- [Medium](https://medium.com/@nichols.tech)
- [Main Instagram](https://instagram.com/Nichols.Tech)
- [NMS Instagram](https://instagram.com/NashvilleMusicSchool)
- [NMS Facebook](https://facebook.com/NashvilleMusicSchool)

**Disclaimer:**

The information presented in this document is provided by Nashville Music School (NMS), a legal business registered with the French Registry of Businesses and Enterprises. NMS is committed to offering accurate and reliable data to the best of its ability. However, the content is intended for informational purposes only and should not be considered as professional advice.

NMS complies with the General Data Protection Regulation [GDPR](https://gdpr.eu/) and actively practices data privacy.


*Thank you for your understanding.*

{:.list-inline}
- Date: January 2024
- Dataset: Personal 
- Category: Data Analysis, EDA

