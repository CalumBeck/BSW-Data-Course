---
  title: "Introduction to Machine Learning"
  description: "This final chapter will give you a taste of the all-powerful Machine Learning. You will learn how to preprocess your data and apply a Decision Tree algorithm to predict the home planet of a given customer."
---

## Import libraries for Machine Learning

```yaml
type: NormalExercise 
lang: python
xp: 100 
skills: 2
key: 8a8f6f6a7c   
```


Your manager approached you stating that the system used for capturing customer's home planet has gone down. However, since other variables are not affected, maybe you can build a Decision Tree that would automatically predict the customer's planet of origin?

Machine Learning is a complex and difficult science that takes years to master. Luckily, there are plenty of libraries that make it easy to implement a basic model without much prior training.

We will focus on the `sklearn` library that contains all the necessary functions for a Machine Learning project.


`@instructions`
1) Select the `tree` module from the sklearn library and import the `DecisionTreeClassifier`

2) Select the `metrics` module from the `sklearn` library and import `accuracy_score`

The code to import the `train_test_split` functions has already been written for you.

`@sample_code`

```{python}
#Import function to divide your data into training and learning parts from the cross_validation module of sklearn library
from sklearn.cross_validation import train_test_split

#Import the Decision Tree algorithm from the tree module
from sklearn.____ import ____

#Import function to test the accuracy of your prediction
from ____.____ import ____
```

`@solution`

```{python}
#Import function to divide your data into training and learning parts
from sklearn.cross_validation import train_test_split

#Import the Decision Tree algorithm
from sklearn.tree import DecisionTreeClassifier 

#Import function to test the accuracy of your prediction
from sklearn.metrics import accuracy_score
```

`@sct`

```{python}
Ex().has_equal_ast()
success_msg("Now you are ready to kick things off, good work!")
```

---

## Separate the dependent variable

```yaml
type: NormalExercise 
lang: python
xp: 100 
skills: 2
key: 1aa751294c   
```


The second task is to divide your data into two sets: one containing the dependent variable (if a person was born on Earth or Mars) that you want to predict, the other containing the features that will be used to predict the class of the dependent variable.


`@instructions`
1) Use the `drop` method on your data to delete the `home_planet` column. This will be assigned to the variable `x`

2) Select the `home_planet` column only and assign it to the variable `y`

`@pre_exercise_code`

```{python}
import pandas as pd
df = pd.read_csv('https://assets.datacamp.com/production/repositories/2588/datasets/73d9f6626d0059203da53d733f5f781c4c9aed32/mars_data.csv')
```

`@sample_code`

```{python}
#Keep all columns except the home_planet one
x = df.drop(['____'], axis=1)

#Select the home_planet column only
____ = df['home_planet']
```

`@solution`

```{python}
#Keep all columns except the home_planet one
x = df.drop(['home_planet'], axis=1)

#Select the home_planet column only
y = df['home_planet']
```

`@sct`

```{python}
Ex().has_equal_ast()
success_msg("Good job!")
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


The next step is to split your data into a training and testing sets.

This means that your model will take the training features `x` and learn the outcomes of each permutation by looking at `y`.


`@instructions`
1) Pass the `x` and `y` variables to the `train_test_split` function

2) Set the `test_size` parameter to be `0.2`. This means that 80% of the data will be used for training and 20% for testing

`@hint`


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

## Create and run a simple Decision Tree model

```yaml
type: NormalExercise 
lang: python
xp: 100 
skills: 2
key: fa17f9a513   
```


Now that the variables are transformed, it is time to give another shot at finding the correlation between them. Since the distribution of the transformed variables is closer to a normal one, the assumption is that the correlation coefficient should have greater accuracy.


`@instructions`
1) Use the `corr()` function to find the correlation between the transformed values

2) Assign the code to the variable `new_correlation`

3) Print the newly assigned variable

`@hint`


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

## Test your model

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

---

## Bring it all together

```yaml
type: NormalExercise 
lang: python
xp: 100 
skills: 2
key: 1ee398e3ac   
```


Look at you, the star analyst of Soaring Eagle Bank! You have learned about the `sklearn` library, how to separate the dependent variable, split your data into training and testing datasets, implement a Decision Tree and test the accuracy of your model. Wow, that is a lot and you have achieved all of that with just a few lines of code!


`@instructions`
Click `Submit Answer` once you are ready to finish the course

`@pre_exercise_code`

```{python}
import pandas as pd
df = pd.read_csv('https://assets.datacamp.com/production/repositories/2588/datasets/73d9f6626d0059203da53d733f5f781c4c9aed32/mars_data.csv')
```

`@sample_code`

```{python}
from sklearn.cross_validation import train_test_split
from sklearn.tree import DecisionTreeClassifier 
from sklearn.metrics import accuracy_score

x = df.drop(['home_planet'], axis=1)
y = df['home_planet']
x_train, x_test, y_train, y_test = train_test_split(x,y,test_size=0.2)

dt = DecisionTreeClassifier(random_state=42)
dt.fit(x_train, y_train)
predictions = dt.predict(x_test)

print(accuracy_score(y_test,predictions))
```

`@solution`

```{python}
from sklearn.cross_validation import train_test_split
from sklearn.tree import DecisionTreeClassifier 
from sklearn.metrics import accuracy_score

x = df.drop(['home_planet'], axis=1)
y = df['home_planet']
x_train, x_test, y_train, y_test = train_test_split(x,y,test_size=0.2)

dt = DecisionTreeClassifier()
dt.fit(x_train, y_train)
predictions = dt.predict(x_test)

print(accuracy_score(y_test,predictions))
```

`@sct`

```{python}
Ex().has_equal_ast()
success_msg("This is it! Well done for completing the journey!")
```
