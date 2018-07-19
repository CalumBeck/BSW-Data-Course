---
title       : Introduction to Machine Learning
description : This final chapter will give you a taste of the all-powerful Machine Learning. You will learn how to preprocess your data and apply a Decision Tree algorithm to predict the home planet of a given customer.  
---
## Import libraries for Machine Learning

```yaml
type: NormalExercise
key: 8a8f6f6a7c
lang: python
xp: 100
skills: 2
```
Your manager approached you stating that the system used for capturing customer's home planet has gone down. However, since other variables are not affected, maybe you can build a Decision Tree that would automatically predict the customer's planet of origin?

Machine Learning is a complex and difficult science that takes years to master. Luckily, there are plenty of libraries that make it easy to implement a basic model without much prior training.

We will focus on the `sklearn` library that contains all the necessary functions for a Machine Learning project.


`@instructions`
1) Select the `tree` module from the sklearn library and import the `DecisionTreeClassifier`

2) Select the `metrics` module from the `sklearn` library and import `accuracy_score`

The code to import the `train_test_split` functions has already been written for you. 

`@pre_exercise_code`
```{python}

```

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
key: 1aa751294c
lang: python
xp: 100
skills: 2
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
## Split your data 

```yaml
type: NormalExercise
key: 6c98c363ad
lang: python
xp: 100
skills: 2
```
The next step is to split your data into a training and testing sets.

This means that your model will take the training features `x` and learn the outcomes of each permutation by looking at `y`. 

`@instructions`

1) Pass the `x` and `y` variables to the `train_test_split` function

2) Set the `test_size` parameter to be `0.2`. This means that 80% of the data will be used for training and 20% for testing

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
key: fa17f9a513
lang: python
xp: 100
skills: 2
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
## Test your model

```yaml
type: NormalExercise
key: ebb2499832
lang: python
xp: 100
skills: 2
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
key: 1ee398e3ac
lang: python
xp: 100
skills: 2
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
