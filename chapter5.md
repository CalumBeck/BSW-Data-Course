---
  title: "Introduction to Machine Learning"
  description: "This final chapter will give you a taste of the all-powerful Machine Learning. You will learn how to preprocess your data and apply a Decision Tree algorithm to predict the home planet of a given customer."
---

## Dicerolls

```yaml
type: NormalExercise 
xp: 100 
key: cb1eac1984   
```


A new casino has opened on mars, and they need your help! 

In one of the games, a customer pays 1 markle, the local martian currency, to roll 2 dice. If they can roll a 10 or higher, they win 5 markles. However, the low gravity on Mars means that the dice keep bouncing away! 

The casino would like to trial a computer version, in which 2 random numbers between 1 and 6 are generated instead of using real dice. A customer called Zworby has volunteered to trial the game, and would like to play 100  times.

You will need to make use of a random number generator. A useful way to learn how to do things is use stack overflow. 

 [https://stackoverflow.com/questions/3996904/generate-random-integers-between-0-and-9](url)


`@instructions`
Create a for loop, which generates 2 dice rolls, 100 times.

For each pair of dice rolls, add their sum to the list created for you. So you end up with a list of 100 numbers, each number represents the sum of 2 dice rolls.

`@hint`


`@pre_exercise_code`

```{python}

```


`@sample_code`

```{python}
#List of dice rolls
Dicerolls = []

#Make any neccesary imports here
from ___ import ___

#Create a for loop below to append the sum of 2 dice rolls to the Dicerolls list, 100 times.
```

`@solution`

```{python}
#List of dice rolls
Dicerolls = []

#Make any neccesary imports here
from random import randint

#Create a for loop below to append the sum of 2 dice rolls to the Dicerolls list, 100 times.
for i in range(100):
  Dicerolls.append(randint(1, 6) + randint(1, 6))
```

`@sct`

```{python}
Ex().has_code(randint(1,6))
success_msg("Well done!")
```
