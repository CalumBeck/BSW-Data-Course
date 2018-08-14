---
  title: "Explore the data"
  description: "Before any serious analytics can begin, it is important to understand your data better. We do this by performing Exploratory Data Analysis (EDA). A few of the available EDA methods will be covered in this chapter."
---

## Lets get some info!

```yaml
type: NormalExercise 
lang: python
xp: 100 
skills: 2
key: 108d33a707   
```


We will begin by getting some very broad information about the DataFrame `df`. For this purpose you will use the `info()` method.

After you submit the solution, take some time to read the success message that will help you interpret the results.


`@instructions`
Use the `info()` method on `df`

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
key: b8cf4b8501   
```


The `info()` method has given you some high-level insight into the dataset as a whole.

What about some statistical description of the individual columns? For this purpose we will use the `describe()`method.

This time you will use a variable to store the code. A variable is like a container that converts lengthy code into a short character string. You have already defined a variable before by creating `df` DataFrame.

Make sure you print the variable and take some time to interpret the output.


`@instructions`
1) Use the `describe()` method on `df`

2) Assign your code to a variable called `description`

3) Print out the variable `description`

`@pre_exercise_code`

```{python}
import pandas as pd
df = pd.read_csv('https://assets.datacamp.com/production/repositories/2588/datasets/73d9f6626d0059203da53d733f5f781c4c9aed32/mars_data.csv')
```

`@sample_code`

```{python}
#Your code below
____ = df.____()

#Print the variable below
print(____)
```

`@solution`

```{python}
#Your code below
description = df.describe()

#Print the variable below
print(description)
```

`@sct`

```{python}
Ex().has_equal_ast()
success_msg("Wow, you just received a lot of useful information with a single `describe()` method!")
```

---

## Visualise the data

```yaml
type: NormalExercise 
lang: python
xp: 100 
skills: 2
key: 7e71720519   
```


Statistical analysis is great, but sometimes a visualization can be an extremely powerful tool to understand the data quickly and effectively. For this purpose you will import a new library called `matplotlib`.

We will focus on understanding the distributions of our data by creating a histogram. This will help your statistical analysis in the upcoming chapter. 

After you submit the exercises, let's take some time to interpret the results.


`@instructions`
1) Import the `matplotlib.pyplot` library as `plt`

2) Create a histogram of the `lifetime_value` variable by using `hist()`

A histogram of the `age` variable has already been created for you as an example. 

3) Display the histogram by using `plt.show()`

`@hint`


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
plt.hist(df['age'])
plt.show()

#Create a histogram to show the distribution of the lifetime value variable 
plt.___(df['____'])
____
```

`@solution`

```{python}
#Import the required modules
import matplotlib.pyplot as plt

#Create a histogram to show the distribution of age variable
plt.hist(df['age'])
plt.show()

#Create a histogram to show the distribution of lifetime value variable 
plt.hist(df['lifetime_value'])
plt.show()
```

`@sct`

```{python}
Ex().has_equal_ast()
success_msg("Great work! Note that your data is right skewed - the distribution plots are asymmetrical, with long tails stretching to the right. We will have to do something about this in the future exercises.")
```

---

## Writing a function

```yaml
type: NormalExercise 
lang: python
xp: 100 
skills: 2
key: a97d1d137c   
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
key: efa8b20bb4   
```


Well done! Now you have a much better understanding of the Mars Banking data. You achieved this by, firstly, having a high-level overview with the `info()` method. Then you explored the statistical features of the columns by using `describe()`. Finally, you visually examined the distribution of the values across multiple variables. 

Remember, you found that both `age` and `lifetime_value` columns are right skewed. This means that you will have to transform the values of these columns to effectively apply statistical methods. You will learn more about this in the next chapter.

You also engaged in some data engineering by creating a new column with transaction zone values fixed.


`@instructions`
Click `Submit Answer` once you are ready to proceed!

`@hint`


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

plt.hist(df['age'])
plt.show()

plt.hist(df['lifetime_value'])
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

plt.hist(df['age'])
plt.show()

plt.hist(df['lifetime_value'])
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
