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


Now that you are familiar with the data, you can finally start exploring it in depth. 

Your manager has asked to find the total value of all the transactions on Mars that took place during the day. You can do this by using the `sum()` method on the `lifetime_value` column.


`@instructions`
1) Select the `lifetime_value` column of `df`

2) Apply the `sum()` method

3) Assign the calculation to the variable `total_value`

4) Print the results

`@pre_exercise_code`

```{python}
import pandas as pd
df = pd.read_csv('https://assets.datacamp.com/production/repositories/2588/datasets/73d9f6626d0059203da53d733f5f781c4c9aed32/mars_data.csv')
```

`@sample_code`

```{python}
#Calculate the total value
____ = df['____'].____

#Print out the results
print(____)
```

`@solution`

```{python}
total_value = 22005
```

`@sct`

```{python}
test_object('total_value')
success_msg("Good work! You can now report a profit of $22005 for the day!")
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

`@hint`


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

## Writing a function

```yaml
type: NormalExercise 
lang: python
xp: 100 
skills: 2
key: a97d1d137c   
```


Now that the variables are transformed, it is time to give another shot at finding the correlation between them. Since the distribution of the transformed variables is closer to a normal one, the assumption is that the correlation coefficient should have greater accuracy.


`@instructions`
1) Use the `corr()` function to find the correlation between the transformed values

2) Assign the code to the variable `new_correlation`

3) Print the newly assigned variable

`@pre_exercise_code`

```{python}
import pandas as pd
import numpy as np
df = pd.read_csv('https://assets.datacamp.com/production/repositories/2588/datasets/73d9f6626d0059203da53d733f5f781c4c9aed32/mars_data.csv')
df['log_age'] = np.log(df['age'])
df['log_value'] = np.log(df['lifetime_value'])
```

`@sample_code`

```{python}
#Find the new correlation
____ = df['log_value'].____(df['log_age'])

#Print out the result
print(____)
```

`@solution`

```{python}
#Find the new correlation
new_correlation = df['log_value'].corr(df['log_age'])

#Print out the result
print(new_correlation)
```

`@sct`

```{python}
Ex().has_equal_ast()
success_msg("Great! By transforming the variables, you were able to improve the coefficient from 0.2 to 0.329!")
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
