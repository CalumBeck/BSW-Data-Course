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


Now that you have a model ready, you need to assess how well it works. The `accuracy_score` function will compare your model's predictions with the actual class labels contained in `y_test` variable and return a percentage of correct guesses. 

The However, remember that this only a basic test and to truly assess your model a much deeper analysis is required that is beyond the scope of this course.


`@instructions`
1) Use the `predict` method on the `x_test` variable to generate class predictions

2) Use the `accuracy_score` function to see what is the percentage of correct predictions

`@pre_exercise_code`

```{python}
import pandas as pd
from sklearn.cross_validation import train_test_split
from sklearn.tree import DecisionTreeClassifier
from sklearn.metrics import accuracy_score
df = pd.read_csv('https://assets.datacamp.com/production/repositories/2588/datasets/73d9f6626d0059203da53d733f5f781c4c9aed32/mars_data.csv')
x = df.drop(['home_planet'], axis=1)
y = df['home_planet']
x_train, x_test, y_train, y_test = train_test_split(x,y,test_size=0.2)
dt = DecisionTreeClassifier(random_state=42)
dt.fit(x_train, y_train)
```

`@sample_code`

```{python}
#Make predictions using the model you developed
predictions = dt.____(x_test)

#Test the accuracy of your model
print(____(y_test,predictions))
```

`@solution`

```{python}
#Make predictions using the model you developed
predictions = dt.predict(x_test)

#Test the accuracy of your model
print(accuracy_score(y_test,predictions))
```

`@sct`

```{python}
Ex().has_equal_ast()
success_msg("Awesome work! Your model predicted well, but clearly could achieve better results by better optimization.")
```
