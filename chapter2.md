---
  title: "Import the data"
  description: "In this chapter you will learn how to kick off your data analysis project. This includes equipping your working environment with powerful libraries, importing the data you want to analyze and checking if the data import has been successful."
---

## Import the required libraries

```yaml
type: NormalExercise 
lang: python
xp: 100 
skills: 2
key: 5f798c6519   
```


In this task we want to import some `Libraries`

Two of the most useful libraries are:

`pandas - for data manipulation and analysis.`

`numpy - for working with data arrays.`


`@instructions`
Import `pandas` library and name it `pd` for ease of use. 

The code to import the `numpy` library has already been written for you as an example.

`@hint`


`@pre_exercise_code`

```{python}

```


`@sample_code`

```{python}
#Import numpy library and label it np
import numpy as np

#Import pandas library and label it pd
import ____ as ____
```

`@solution`

```{python}
import pandas as pd
```

`@sct`

```{python}
test_import("pandas", same_as = True)
success_msg("Good job! The required libraries have been imported.")
```

---

## Import the data

```yaml
type: NormalExercise 
lang: python
xp: 100 
skills: 2
key: ff0ef50ee7   
```


Now that you have imported `pandas` library, we can focus on acquiring the data. This means pointing pandas to a data source, so it can transform it into a `DataFrame`. In very broad terms a DataFrame is simply a data structure with observations and variables (you can think of it as a spreadsheet with rows and columns).

Pandas contains useful methods, here we will use its method for reading csv files. Which we do using `pd.read_csv()` which tells python to use the `read_csv()` method from `pandas` (which we labelled `pd`).


`@instructions`
1) Use `pd.read_csv()` to tell Python to import a CSV file. 

2) We need to specify the filename we want to read inside the brackets of the `read_csv()` method. 
   In this case the filename is  `mars_data`.

3) Assign the code to a variable `df` (abbreviation of DataFrame)

`@hint`


`@pre_exercise_code`

```{python}
import pandas as pd
mars_data = 'https://assets.datacamp.com/production/repositories/2588/datasets/73d9f6626d0059203da53d733f5f781c4c9aed32/mars_data.csv'
```

`@sample_code`

```{python}
#Complete the data import below
____ = pd.____(____)
```

`@solution`

```{python}
df = pd.read_csv(mars_data)
```

`@sct`

```{python}
test_data_frame("df", columns=['zone','product','lifetime_value','age','home_planet'])
success_msg("Nice! Now you have a dataset to work with.")
```

---

## Check the data

```yaml
type: NormalExercise 
lang: python
xp: 100 
skills: 2
key: 0a8799887e   
```


Statistical analysis is great, but sometimes a visualization can be an extremely powerful tool to understand the data quickly and effectively. For this purpose you will import a new library called `matplotlib`.

We will focus on understanding the distributions of our data by creating a histogram. This will help your statistical analysis in the upcoming chapter. 

After you submit the exercises, let's take some time to interpret the results.


`@instructions`
1) Import the `matplotlib.pyplot` library as `plt`

2) Create a histogram of the `lifetime_value` variable by using `hist()`

A histogram of the `age` variable has already been created for you as an example. 

3) Display the histogram by using `plt.show()`

`@pre_exercise_code`

```{python}
import pandas as pd
df = pd.read_csv('https://assets.datacamp.com/production/repositories/2588/datasets/e8c7de0372cfe29b1be7bad2b16e28e2e9a56d01/mars_data.csv')
```

`@sample_code`

```{python}
#Import the required modules
import matplotlib.pyplot as ____

#A histogram to show the distribution of the age variable
df['age'].plot.hist()
plt.show()

#Create a histogram to show the distribution of the lifetime value variable 
df['____'].plot.____()
____
```

`@solution`

```{python}
#Import the required modules
import matplotlib.pyplot as plt

#Create a histogram to show the distribution of age variable
df['age'].plot.hist()
plt.show()

#Create a histogram to show the distribution of lifetime value variable 
df['lifetime_value'].plot.hist()
plt.show()
```

`@sct`

```{python}
Ex().has_equal_ast()
success_msg("Great work! Note that your data is right skewed - the distribution plots are asymmetrical, with long tails stretching to the right. We will have to do something about this in the future exercises.")
```

---

## Bring it all together

```yaml
type: NormalExercise 
lang: python
xp: 100 
skills: 2
key: f350c11c21   
```


Oh no! Your colleague has just informed you that an error has been spotted in the backend processes of the bank. This error has led to transaction zones being mixed up. For example, zone 1 should have been labeled as zone 2, zone 3 as 4 and so on:

`Zone 1 --> 2`
`Zone 2 --> 1`
`Zone 3 --> 4`
`Zone 4 --> 3`

To mitigate this issue in your data you can define a function! With the right instructions, it will fix the problem quickly.


`@instructions`
1) Define a new function called `zone_change`

2) Assign the correct zones

3) Use the `apply` method on the `zone` column of `df` and assign the results to a new column called `new_zones`

`@pre_exercise_code`

```{python}
import pandas as pd
df = pd.read_csv('https://assets.datacamp.com/production/repositories/2588/datasets/e8c7de0372cfe29b1be7bad2b16e28e2e9a56d01/mars_data.csv')
```

`@sample_code`

```{python}
#Define a function that will replace the values
def ____(x):
    if x == 1:
        return 2
    if x == 2:
        return ____
    if x == 3:
        return ____
    if x == 4:
        return ____

#Apply the function to your data         
df['new_zone'] = df['zone'].____(zone_change)

#Display the data
print(df.head())
```

`@solution`

```{python}
#Define a function that will replace the values
def zone_change(x):
    if x == 1:
        return 2
    if x == 2:
        return 1
    if x == 3:
        return 4
    if x == 4:
        return 3

#Apply the function to your data        
df['new_zone'] = df['zone'].apply(zone_change)

#Display the data 
print(df.head())
```

`@sct`

```{python}
Ex().has_equal_ast()
success_msg("Good job! The new column reflects the true state of the data!")
```
