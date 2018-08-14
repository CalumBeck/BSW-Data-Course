---
  title: "Analyse the data"
  description: "In this chapter you will perform the main analysis work. This includes calculating the total sum of a column, transforming data and finding correlation between variables."
---

## Find the value sum of a column

```yaml
type: NormalExercise 
lang: python
xp: 100 
skills: 2
key: 8a8f6f6a7c   
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

## Find the correlation

```yaml
type: NormalExercise 
lang: python
xp: 100 
skills: 2
key: 1aa751294c   
```


Your manager is convinced there is positive correlation between customer's age and their lifetime value. This means that the independent variable of age influences the dependent variable of profit. In other words, the older the customer, the more profit the bank receives from doing business with them. 

This dependency could exist for a variety of reasons. Also, correlation does not always mean causation, but the relationship is interesting to explore nonetheless.

Your task is to investigate the manager's hypothesis further. 

We will use the `corr()` pandas function to see if your manager is right.


`@instructions`
1) Use the `corr()` function to find the correlation between `age` and `lifetime_value'`

2) Assign the code to a variable `correlation`

3) Print the new variable

`@pre_exercise_code`

```{python}
import pandas as pd
df = pd.read_csv('https://assets.datacamp.com/production/repositories/2588/datasets/73d9f6626d0059203da53d733f5f781c4c9aed32/mars_data.csv')
```

`@sample_code`

```{python}
#Find the correlation between the two variables
____ = df['age'].___(df['lifetime_value'])

#Print out the results
print(_____)
```

`@solution`

```{python}
#Find the correlation between the two variables
correlation = df['age'].corr(df['lifetime_value'])

#Print out the results
print(correlation)
```

`@sct`

```{python}
Ex().has_equal_ast()
success_msg("Looks like your manager's intuition was right and now you have some empirical evidence to support it!")
```

---

## Transform the data

```yaml
type: NormalExercise 
lang: python
xp: 100 
skills: 2
key: 6c98c363ad   
```


Your preliminary analysis looks very promising! However, do you remember when we looked at the distribution of the data in Chapter 2? Both, `age` and `lifetime_value` variables are skewed to the right and this is most definitely affecting our findings. 

Worry not! We can fix this by transforming the variables. To do this we will apply the numpy `log()` function to all the data points in the two columns. 

Your collegue has supplied you with a sample visualization code to illustrate the changes the transformations make. Take some time to review the output charts once you complete the instructions below.


`@instructions`
1) Apply the `log()` function to the `age` column and assign the results to a new column called `log_age`

2) Do the same for the `lifetime_value` column. Call the new column `log_value`

`@pre_exercise_code`

```{python}
import pandas as pd
from sklearn.cross_validation import train_test_split
df = pd.read_csv('https://assets.datacamp.com/production/repositories/2588/datasets/73d9f6626d0059203da53d733f5f781c4c9aed32/mars_data.csv')
x = df.drop(['home_planet'], axis=1)
y = df['home_planet']
```

`@sample_code`

```{python}
#Split your data
x_train, x_test, y_train, y_test = train_test_split(____,____,test_size=____)
```

`@solution`

```{python}
#Split your data
x_train, x_test, y_train, y_test = train_test_split(x,y,test_size=0.2)
```

`@sct`

```{python}
Ex().has_equal_ast()
success_msg("Now you have data to teach and test your model!")
```

---

## Find the new correlation

```yaml
type: NormalExercise 
lang: python
xp: 100 
skills: 2
key: fa17f9a513   
```


Now comes the fun part! You need to initialize a Decision Tree model and pass the training data to it, so it can learn the relevant features.

Note that you are also passing the dependent variables labels with `y_train`. This means that you are solving a `supervised learning` problem.


`@instructions`
1) Use the `DecisionTreeClassifer` to initiate the model. This will be assigned to the variable `dt`

2) Use the `fit` method on `dt` and pass the training variables, so that your model can learn

`@pre_exercise_code`

```{python}
import pandas as pd
from sklearn.cross_validation import train_test_split
from sklearn.tree import DecisionTreeClassifier 
df = pd.read_csv('https://assets.datacamp.com/production/repositories/2588/datasets/73d9f6626d0059203da53d733f5f781c4c9aed32/mars_data.csv')
x = df.drop(['home_planet'], axis=1)
y = df['home_planet']
x_train, x_test, y_train, y_test = train_test_split(x,y,test_size=0.2)
```

`@sample_code`

```{python}
#Initiate the model
dt = ____()

#Fit the model around the training variables
dt.____(x_train, y_train)
```

`@solution`

```{python}
#Initiate the model
dt = DecisionTreeClassifier()

#Fit the model around the training variables
dt.fit(x_train, y_train)
```

`@sct`

```{python}
Ex().has_equal_ast()
success_msg("Great, now you have a an intelligent model!")
```

---

## Visualise the correlation

```yaml
type: NormalExercise 
lang: python
xp: 100 
skills: 2
key: ebb2499832   
```


You have answered all the question your manager has asked you. Good job! 

However, to demonstrate your excellence, you can go beyond the basic expectations. Why not provide a chart that visualizes the correlation between `age` and `lifetime_value`? Your manager could use this in a presentation they are putting together.

To do this you will use the `seaborn` data visualization library. It is similar to `matplotlib`, but the visuals are more impressive!


`@instructions`
1) Import `seaborn` library as `sns`

2) Assign `log_age` as x and `log_value` as y values

3) Show the plot by using `plt.show()`

`@pre_exercise_code`

```{python}
import pandas as pd
import numpy as np
df = pd.read_csv('https://assets.datacamp.com/production/repositories/2588/datasets/73d9f6626d0059203da53d733f5f781c4c9aed32/mars_data.csv')
df['log_age'] = np.log(df['age'])
df['log_value'] = np.log(df['lifetime_value'])
import matplotlib.pyplot as plt
```

`@sample_code`

```{python}
#Import Seaborn
import seaborn as ____

#Plot the correlation
sns.lmplot(x='____', y='____', data=df)

#Show the plot
____
```

`@solution`

```{python}
#Import Seaborn
import seaborn as sns

#Plot the correlation
sns.lmplot(x='log_age', y='log_value', data=df)

#Show the plot
plt.show()
```

`@sct`

```{python}
Ex().has_equal_ast()
success_msg("Look at that! Your code has produced a beautiful visualization that illustrates the relationship between the two variables!")
```

---

## Bring it all together

```yaml
type: NormalExercise 
xp: 100 
key: f88ffb3cc1   
```




