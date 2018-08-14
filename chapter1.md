---
  title: "Getting started"
  description: "In this chapter you will learn how to kick off your data analysis project. This includes equipping your working environment with powerful libraries, importing the data you want to analyze and checking if the data import has been successful."
---

## Python as a calculator

```yaml
type: NormalExercise 
lang: python
xp: 100 
skills: 2
key: 286ddf980c   
```


On the right, you can see some Python script, which can be run by hitting Run Code. The output will be shown in the 
IPython shell in the bottom right of the page. You can also use the reset button to restore the original code, and 
the Submit Answer button when you think you have completed the instructions and wish to progress to the next task.

In this task we want to use Python to complete some simple calculations, some examples have been written for you. 

In the code we have used `print` statements. They print the result of whatever is contained in their brackets to 
the IPython shell so that you can see it.  Hit run code to see how it works, then you can try writing your own!


`@instructions`
Calculate `12 + 9`, and tell python to print the answer, just like the examples already written.

`@hint`


`@pre_exercise_code`

```{python}

```


`@sample_code`

```{python}
#Lines beggining with a # are called comments and are ignored when the code is run
#Python can add
print (5 + 5)

#Python can multiply
print (8 * 4)

#Write your own sum below

```

`@solution`

```{python}
#Lines beggining with a # are called comments and are ignored when the code is run
#Python can add
print (5 + 5)

#Python can multiply
print (8 * 4)

#Write your own sum below
print (12 + 9)
```

`@sct`

```{python}
Ex().has_equal_ast()
success_msg("12 + 9 = 21! Who'd have thunk it!")
```

---

## Making variables great again

```yaml
type: NormalExercise 
lang: python
xp: 100 
skills: 2
key: 56c6ebec11   
```


Now that you have imported `pandas` library, we can focus on acquiring the data. This means pointing pandas to a data source, so it can transform it into a `DataFrame`. In very broad terms a DataFrame is simply a data structure with observations and variables (you can think of it as a spreadsheet with rows and columns).

Pandas contains useful methods, here we will use its method for reading csv files. Which we do using `pd.read_csv()` which tells python to use the `read_csv()` method from `pandas` (which we labelled `pd`). 

In Python, variables can be used to label pieces of code or values so they can be used later. Variables can be assigned using `=`; For example `x = 5` assigns the value of `5` to the variable `x`.


`@instructions`
1) Use `pd.read_csv()` to tell Python to import a CSV file. 

2) We need to specify the filename we want to read inside the brackets of the `read_csv()` method. 
   In this case the filename is  `mars_data`.

3) Assign the code to a variable `df` (abbreviation of DataFrame)

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

## Make your own list

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

## Hiring Heather

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

---

## The wonderful world of for loops

```yaml
type: NormalExercise 
xp: 100 
key: 40da23b9da   
```


Now we're going to use a really useful tool, loops. Often we will need to do a similiar task multiple times, and it can easier to use a loop rather than write out multiple lines of very similiar code. 

In this task, we are going to use a `for` loop to create a list of square numbers. 

A square number can be made using `x**2`, which would give the square of `x`. 

We will also use the `range()` function, which produces a list of numbers, starting from 0, up to the number written inside the brackets


`@instructions`
Run the existing code to see an example of how the `for` loop and `range()` function work. 

Then write your own for loop, adding the square numbers up to 10 to the empty list created for you.

Use the hint if you get stuck.

`@hint`
`List_of_Squares.append(i**2)` is the code to add the square of i to the list. Copy the example for loop, replacing the print statement with the append code. 
Remember to use a `:` at the end of the for statement, and indent the code being looped over.

`@sample_code`

```{python}
#Prints the square numbers from 0 to 10
for i in range(10):
    #This indented code is looped over
    print(i**2)

#Creates an empty list to append the square numbers to
List_of_Squares = []

#Create your own for loop below to append the square numbers to the empty list



#Print the final list
print (List_of_Squares)
```

`@solution`

```{python}
#Prints the square numbers from 0 to 10
for i in range(10):
    #This indented code is looped over
    print(i**2)

#Creates an empty list to append the square numbers to
List_of_Squares = []

#Create your own for loop below to append the square numbers to the empty list
for i in range(10):
    List_of_Squares.append(i**2)

#Print the final list
print (List_of_Squares)
```

`@sct`

```{python}
Ex().has_equal_ast()
success_msg("Great Work! Now we can get started working on some Martian data")
```
