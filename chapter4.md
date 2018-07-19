---
title: Analyse the data
description: >-
  In this chapter you will perform the main analysis work. This includes calculating the total sum of a column, transforming data and finding correlation between variables.


---
## Find the value sum of a column

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

`@hint`


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
## Find correlation between two variables

```yaml
type: NormalExercise
lang: python
xp: 100
skills: 2
key: b8cf4b8501
```

Your manager is convinced there is positive correlation between customer's age and their lifetime value. This means that the independent variable of age influences the dependent variable of profit. In other words, the older the customer, the more profit the bank receives from doing business with them. 

This dependency could exist for a variety of reasons. Also, correlation does not always mean causation, but the relationship is interesting to explore nonetheless.

Your task is to investigate the manager's hypothesis further. 

We will use the `corr()` pandas function to see if your manager is right.

`@instructions`
1) Use the `corr()` function to find the correlation between `age` and `lifetime_value'`

2) Assign the code to a variable `correlation`

3) Print the new variable

`@hint`


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
key: 7e71720519
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
import numpy as np
df = pd.read_csv('https://assets.datacamp.com/production/repositories/2588/datasets/73d9f6626d0059203da53d733f5f781c4c9aed32/mars_data.csv')
import seaborn as sns
import matplotlib.pyplot as plt
```
`@sample_code`
```{python}
#Transform the age variable 
df['log_age'] = np.____(df['age'])

#Transform the lifetime_value variable 
df['____'] = np.log(df['____'])

#The code below will help you visualise the transformed variables
plt.figure()
sns.distplot(df['log_age'])
plt.show()

plt.figure()
sns.distplot(df['log_value'])
plt.show()
```
`@solution`
```{python}
#Transform the age variable 
df['log_age'] = np.log(df['age'])

#Transform the lifetime_value variable 
df['log_value'] = np.log(df['lifetime_value'])

#The code below will help you visualise the transformed variables
plt.figure()
sns.distplot(df['log_age'])
plt.show()

plt.figure()
sns.distplot(df['log_value'])
plt.show()
```
`@sct`
```{python}
Ex().has_equal_ast()
success_msg("The data will satisfy statistical inference assumptions much better now!")
```





---
## Find correlation between transformed variables

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
## Visualize the correlation

```yaml
type: NormalExercise
lang: python
xp: 100
skills: 2
key: 1d3c536bd7
```

You have answered all the question your manager has asked you. Good job! 

However, to demonstrate your excellence, you can go beyond the basic expectations. Why not provide a chart that visualizes the correlation between `age` and `lifetime_value`? Your manager could use this in a presentation they are putting together.

To do this you will use the `seaborn` data visualization library. It is similar to `matplotlib`, but the visuals are more impressive!

`@instructions`
1) Import `seaborn` library as `sns`

2) Assign `log_age` as x and `log_value` as y values

3) Show the plot by using `plt.show()`

`@hint`


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
lang: python
xp: 100
skills: 2
key: efa8b20bb4
```

Awesome! As SEB's Mars data analyst you have used `sum()` to find the total value of transactions for the day and `corr()` to correlate variables. Not only that - you have changed the variables with a `log()` transformation to reflect the statistical assumptions more closely. Lastly, you learned about `Seaborn` data visualization library to produce a linear regression model chart.

`@instructions`
Click `Submit Answer` once you are ready to proceed!

`@hint`


`@pre_exercise_code`
```{python}
import pandas as pd
import numpy as np
df = pd.read_csv('https://assets.datacamp.com/production/repositories/2588/datasets/73d9f6626d0059203da53d733f5f781c4c9aed32/mars_data.csv')
import matplotlib.pyplot as plt
```
`@sample_code`
```{python}
import seaborn as sns

print('Total value is:', df['lifetime_value'].sum())

print('First correlation:', df['age'].corr(df['lifetime_value']))

df['log_age'] = np.log(df['age'])
df['log_value'] = np.log(df['lifetime_value'])

print('Correlation with transformed variables:', df['log_value'].corr(df['log_age']))

sns.lmplot(x='log_age', y='log_value', data=df)
plt.show()
```
`@solution`
```{python}
import seaborn as sns

print('Total value is:', df['lifetime_value'].sum())

print('First correlation:', df['age'].corr(df['lifetime_value']))

df['log_age'] = np.log(df['age'])
df['log_value'] = np.log(df['lifetime_value'])

print('Correlation with transformed variables:', df['log_value'].corr(df['log_age']))

sns.lmplot(x='log_age', y='log_value', data=df)
plt.show()
```
`@sct`
```{python}
Ex().has_equal_ast()
success_msg("Well done!")
```





