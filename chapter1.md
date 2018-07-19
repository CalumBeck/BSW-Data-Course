---
title: Getting started
description: >-
  In this chapter you will learn how to kick off your data analysis project. This includes equipping your working environment with powerful libraries, importing the data you want to analyze and checking if the data import has been successful.

---
## Creating Calculations

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



`@sample_code`
```{python}
#Lines beggining with a # are called comments and are ignored when the code is run
#Python can add
print (5 + 5)

#Python can divide
print (10 / 2)

#Python can multiply
print (8 * 4)

#Write your own sum below

```
`@solution`
```{python}
#Lines beggining with a # are called comments and are ignored when the code is run
#Python can add
print (5 + 5)

#Python can divide
print (10 / 2)

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
## Valuable Variables 

```yaml
type: NormalExercise
lang: python
xp: 100
skills: 2
key: '98e9001084'
```
Sometimes we might need to keep track of a value that we want to use more than once, or change when something happens. 

To do this we can use a variable. In Python, variables can be used to label pieces of code or values so they can be 
used later. Variables can be assigned using `=`; For example `x = 5` assigns the value of `5` to the variable `x`.

`@instructions`
Did you remember how to multiply? Try multiplying the variables `x` and `y` and printing the result.


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
## Some Lovely Lists

```yaml
type: NormalExercise
lang: python
xp: 100
skills: 2
key: dd553a1bba
```
A really useful way to keep track of data, is to make a list. Lists are a series of elements contained in square brackets. For example, `CoolShapes = ['Circle', 'Rhombus', 'Triangle']` creates a list of 3 strings, which are bits of text  inside " (double-quotes) or ' (single-quotes). Strings are an example of a type of data, another one is integers which we have used in the last exercise. Python lists can contain multiple types in the same list, it can even contain other lists!

`@instructions`
Make your own list called Employees, with 3 strings for your employee names. Your current employees are Jerome, Sarah and Pete. 


`@sample_code`
```{python}
#List of some cool shapes
CoolShapes = ['Circle', 'Rhombus', 'Triangle']

#List of Employees: Jerome, Sarah and Pete. 

```
`@solution`
```{python}
#List of some cool shapes
CoolShapes = ['Circle', 'Rhombus', 'Triangle']

#List of Employees: Jerome, Sarah and Pete. 
Employees = ['Jerome', 'Sarah', 'Pete']
```
`@sct`
```{python}
Ex().has_equal_ast()
success_msg("That's a lovely list you've made there, good stuff!")
```

---
## Hiring Heather

```yaml
type: NormalExercise
lang: python
xp: 100
skills: 2
key: '6634919059'
```
In this task we will be using some methods from Pythons built in `Library`.

`Libraries` are collections of code that have been written by other developers and packaged for anyone to use. 
They contain useful packets of code called modules or methods. We'll use a method from the built in Library called
`append()`, which is used to add an element to the end of a list. The method is applied to a list using a dot like so 
`Name_of_List.append(element)` It takes what is called the `argument` in the brackets, where you write the element you 
would like to add, and it appends it on to the list.

`@instructions`
We've hired a new employee called Heather. 

We need to add her name, as a string, to the list of Employees.


`@sample_code`
```{python}
#List of Employees: Jerome, Sarah and Pete. 
Employees = ['Jerome', 'Sarah', 'Pete']

#Fill in the blanks to add the new employee, Heather, to the list
_.append(_)

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


