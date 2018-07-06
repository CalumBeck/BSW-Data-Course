---
title: Getting started
description: >-
  In this chapter you will learn how to kick off your data analysis project. This includes equipping your working environment with powerful libraries, importing the data you want to analyze and checking if the data import has been successful.


---
## Import the required libraries

```yaml
type: NormalExercise
lang: python
xp: 100
skills: 2
key: 286ddf980c
```

`Libraries` are collections of code that have been written by other developers and packaged for anyone to use.

Imagine libraries as tools for building a house - you would not make your own hammer, nails and bricks, but rather buy these items in a shop. Similarly, libraries equip you with useful code that can be easily reused. For free! 

Two of the most useful libraries are:

`pandas - for data manipulation and analysis.`

`numpy - for working with data arrays.`

`@instructions`
Import `pandas` library and name it `pd` for ease of use. 

The code to import the `numpy` library has already been written for you as an example.



`@sample_code`
```{python}
#Lines beggining with # symbol are called commments and are ignored when the code is run
#They can be used to decribe in plain english what the code is doing
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
key: 56c6ebec11
```

Now that you have imported `pandas` library, we can focus on acquiring the data. This means pointing pandas to a data source, so it can transform it into a `DataFrame`. In very broad terms a DataFrame is simply a data structure with observations and variables (you can think of it as a spreadsheet with rows and columns).

Pandas can import data from a variety of sources that include text files, databases, APIs and so on. For this particular project we will import a CSV (comma-separated value) file

In Python, variables can be used to label pieces of code or values, which can then be referred to, used or changed later. For example 'x = 5' assigns the value of '5' to the variable 'x'. 

`@instructions`
1) Use `pd.read_csv()` to tell Python you want to import a CSV file

2) Make sure you include the filename `mars_data`

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
## Check your data

```yaml
type: NormalExercise
lang: python
xp: 100
skills: 2
key: 713861b8dd
```

Congratulations! You have just imported your data...

...or have you? To check your data we will use the `head()` and `tail()` methods.

To view the output of your actions in the console you will you use the `print()` function.

`@instructions`
1) Use `tail()` method on the `df` object and specify the parameter of `10` inside the brackets to view the last 10 rows of the DataFrame.

The `head()` method has been written for you as an example (it returns 5 rows of data if you do not specify a number in the brackets).

2) Wrap the code you write in a `print()` function to "print out" the output

`@hint`


`@pre_exercise_code`
```{python}
import pandas as pd 
df = pd.read_csv('https://assets.datacamp.com/production/repositories/2588/datasets/e8c7de0372cfe29b1be7bad2b16e28e2e9a56d01/mars_data.csv')
```
`@sample_code`
```{python}
#Check the first 5 rows of the DataFrame (nothing will be displayed)
df.head()

#Check and print the first 5 rows of the DataFrame (output will be displayed in the console)
print(df.head())

#Check the last 10 rows of the DataFrame
____(df.____(____))
```
`@solution`
```{python}
#Check the first 5 rows of the DataFrame (nothing will be displayed)
df.head()

#Check and print the first 5 rows of the DataFrame (output will be displayed in the console)
print(df.head())

#Check the last 10 rows of the DataFrame
print(df.tail(10))
```
`@sct`
```{python}
Ex().has_equal_ast()
success_msg("Great! Take some time to explore the outputs.")
```





---
## Bring it all together

```yaml
type: NormalExercise
lang: python
xp: 100
skills: 2
key: 689f678c19
```

You have made good progress so far. Not only have you learned about the importance of libraries, but also imported the data for the upcoming analysis and checked if the import has been successful by using `tail()`. Lastly, you learned about the very common `print()` function. At this rate you will become an experienced data analyst in no time!

We also briefly touched upon variables by defining `df`. But more on that in the upcoming exercises...

For now, review the glorious code you have written.

`@instructions`
Click `Submit Answer` once you are ready to proceed!

`@hint`


`@pre_exercise_code`
```{python}
import pandas as pd 
mars_data = 'https://assets.datacamp.com/production/repositories/2588/datasets/e8c7de0372cfe29b1be7bad2b16e28e2e9a56d01/mars_data.csv'
```
`@sample_code`
```{python}
import pandas as pd

df = pd.read_csv(mars_data)

print(df.head())
```
`@solution`
```{python}
import pandas as pd

df = pd.read_csv(mars_data)

print(df.head())
```
`@sct`
```{python}
Ex().has_equal_ast()
success_msg("You have completed Chapter 1! Let's keep going.")
```




