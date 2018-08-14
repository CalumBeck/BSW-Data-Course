---
  title: "Explore the data"
  description: "Before any serious analytics can begin, it is important to understand your data better. We do this by performing Exploratory Data Analysis (EDA). A few of the available EDA methods will be covered in this chapter."
---

## Import the required libraries

```yaml
type: NormalExercise 
lang: python
xp: 100 
skills: 2
key: 5f798c6519   
```


We will begin by getting some very broad information about the DataFrame `df`. For this purpose you will use the `info()` method.

After you submit the solution, take some time to read the success message that will help you interpret the results.


`@instructions`
Use the `info()` method on `df`

`@hint`


`@pre_exercise_code`

```{python}
import pandas as pd
df = pd.read_csv('https://assets.datacamp.com/production/repositories/2588/datasets/73d9f6626d0059203da53d733f5f781c4c9aed32/mars_data.csv')
```

`@sample_code`

```{python}
#Your code below
df.____()
```

`@solution`

```{python}
df.info()
```

`@sct`

```{python}
Ex().has_equal_ast()
success_msg("Success! You can see that the DataFrame has 110 rows of data and 6 columns. Furthermore, you can see the column names and the variable types that populate them.")
```

---

## Describe the data

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

## Visualise the data

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

## Write a function to fix the data

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

---

## Bring it all together

```yaml
type: NormalExercise 
lang: python
xp: 100 
skills: 2
key: 1f72e72c18   
```


Well done! Now you have a much better understanding of the Mars Banking data. You achieved this by, firstly, having a high-level overview with the `info()` method. Then you explored the statistical features of the columns by using `describe()`. Finally, you visually examined the distribution of the values across multiple variables. 

Remember, you found that both `age` and `lifetime_value` columns are right skewed. This means that you will have to transform the values of these columns to effectively apply statistical methods. You will learn more about this in the next chapter.

You also engaged in some data engineering by creating a new column with transaction zone values fixed.


`@instructions`
Click `Submit Answer` once you are ready to proceed!

`@pre_exercise_code`

```{python}
import pandas as pd
df = pd.read_csv('https://assets.datacamp.com/production/repositories/2588/datasets/e8c7de0372cfe29b1be7bad2b16e28e2e9a56d01/mars_data.csv')
```

`@sample_code`

```{python}
import matplotlib.pyplot as plt

df.info()

df.describe()

df['age'].plot.hist()
plt.show()

df['lifetime_value'].plot.hist()
plt.show()

def zone_change(x):
    if x == 1:
        return 2
    if x == 2:
        return 1
    if x == 3:
        return 4
    if x == 4:
        return 3

df['new_zones'] = df.zone.apply(zone_change)
```

`@solution`

```{python}
import matplotlib.pyplot as plt

df.info()

df.describe()

df['age'].plot.hist()
plt.show()

df['lifetime_value'].plot.hist()
plt.show()

def zone_change(x):
    if x == 1:
        return 2
    if x == 2:
        return 1
    if x == 3:
        return 4
    if x == 4:
        return 3

df['new_zones'] = df.zone.apply(zone_change)
```

`@sct`

```{python}
Ex().has_equal_ast()
success_msg("Let's march to the next chapter!")
```
