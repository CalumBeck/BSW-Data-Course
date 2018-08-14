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


On the right you can see some python script, called _script.py_, which you can write code in to, and then run by hitting the Run Code button. The output will be shown in the IPython shell in the bottom right of the page. 

You can also use the reset button to restore the original code, and the Submit Answer button when you think you have completed the instructions and wish to progress to the next task.

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

#Write your own sum on the next line

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


Sometimes we might need to keep track of a value that we want to use more than once, or change when something happens. 

To do this we can use a variable. In Python, variables can be used to label pieces of code or values so they can be 
used later. Variables can be assigned using `=`; For example `x = 5` assigns the value of `5` to the variable `x`.


`@instructions`
Did you remember how to multiply? Try multiplying the variables `x` and `y` and printing the result.

If you forgot how to multiply, feel free to use the hint!

`@hint`
To multiply 2 variables, called `a` and `b`, we use `a * b`

`@pre_exercise_code`

```{python}

```


`@sample_code`

```{python}
#Assign variable x
x = 5

#Assign variable y
y = 2

#Add x and y
print (x + y)

#Multiply x and y

```

`@solution`

```{python}
#Assign variable x
x = 5

#Assign variable y
y = 2

#Add x and y
print (x + y)

#Multiply x and y
print (x * y)
```

`@sct`

```{python}
Ex().has_equal_ast()
success_msg("Awesome! You're one step closer to mastering Python")
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


A really useful way to keep track of data, is to make a list. Lists are a series of elements contained in square brackets. For example, `CoolShapes = ['Circle', 'Rhombus', 'Mobius Strip']` creates a list of 3 strings, which are bits of text  inside " (double-quotes) or ' (single-quotes). Strings are an example of a type of data, another one is integers which we have used in the last exercise. Python lists can contain multiple types in the same list, it can even contain other lists!


`@instructions`
Make your own list called Employees, with 3 strings for your employee names. Your current employees are Jerome, Sarah and Pete.

`@hint`


`@pre_exercise_code`

```{python}

```


`@sample_code`

```{python}
#List of some cool shapes
CoolShapes = ['Circle', 'Rhombus', 'Mobius Strip']

#List of Employees: Jerome, Sarah and Pete

```

`@solution`

```{python}
#List of some cool shapes
CoolShapes = ['Circle', 'Rhombus', 'Mobius Strip']

#List of Employees: Jerome, Sarah and Pete. 
Employees = ['Jerome', 'Sarah', 'Pete']
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


In this task we will be using a method from Pythons built in `Library`.

`Libraries` are collections of code that have been written by other developers and packaged for anyone to use. 
They contain useful packets of code called modules or methods. 

We'll use a method from the built in Library called `append()`, which is used to add an element to the end of a list. 

The method is applied to a list using a dot like so `Name_of_List.append(element)`
It takes whatever is contained in the brackets, known as the argument, and adds it to
the list you're applying append to.


`@instructions`
We've hired a new employee called Heather. 

We need to add her name, as a string, to the list of Employees. If you need help, use the hint.

`@hint`
If we wanted to append `Square` to the `CoolShapes` list, we would write `CoolShapes.append('Square')`
Try the same but with the list `Employees` rather than `CoolShapes` and `Heather` instead of `Square`

`@pre_exercise_code`

```{python}
import pandas as pd 
mars_data = 'https://assets.datacamp.com/production/repositories/2588/datasets/e8c7de0372cfe29b1be7bad2b16e28e2e9a56d01/mars_data.csv'
```

`@sample_code`

```{python}
#List of Employees: Jerome, Sarah and Pete. 
Employees = ['Jerome', 'Sarah', 'Pete']

#Add the new employee, Heather, to the list
```

`@solution`

```{python}
#List of Employees: Jerome, Sarah and Pete. 
Employees = ['Jerome', 'Sarah', 'Pete']

#Fill in the blanks to add the new employee, Heather, to the list
Employees.append('Heather')
```

`@sct`

```{python}
Ex().has_equal_ast()
success_msg("Heather is officially hired!")
```

---

## The wonderful world of for loops

```yaml
type: NormalExercise 
xp: 100 
key: 40da23b9da   
```


Now we're going to use a really useful tool, loops. Often we will need to do a similar task multiple times, and it can easier to use a loop rather than write out multiple lines of very similar code. 

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

`@pre_exercise_code`

```{python}

```


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
