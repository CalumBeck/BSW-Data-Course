---
  title: "Casino challenge"
  description: "This chapter is a little more challenging and independent. You are tasked with helping a casino who have a few issues with rolling dice. Rather than being told how to do something, you will need to use stack exchange to work it out yourself, which is a good way to work things out in future. "
---

## Roll the dice

```yaml
type: NormalExercise 
xp: 100 
key: cb1eac1984   
```


A new casino has opened on mars, and they need your help! 

In one of the games, a customer pays 1 markle, the local martian currency, to roll 2 dice. If they can roll a 10 or higher, they win 5 markles. However, the low gravity on Mars means that the dice keep bouncing away! 

The casino would like to trial a computer version, in which 2 random numbers between 1 and 6 are generated instead of using real dice. A customer called Zworby has volunteered to trial the game, and would like to play 100  times.

You will need to make use of a random number generator. A useful way to learn how to do things is use stack overflow. Follow the address below, and adapt the example given to simulate a dice roll.

https://stackoverflow.com/questions/3996904/generate-random-integers-between-0-and-9


`@instructions`
Create a for loop, which generates 2 dice rolls, 100 times.

For each pair of dice rolls, add their sum to the list created for you. So you end up with a list of 100 numbers, each number represents the sum of 2 dice rolls.

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
Ex().has_equal_ast()
success_msg("Well done!")
```

---

## We've lost the plot

```yaml
type: NormalExercise 
xp: 100 
key: 23bdd32abf   
```


Your colleague has tried to plot a histogram for the dice rolling trial. However, the code just isn't working, you've been called in to figure it out, and fix the problem!


`@instructions`
Hit run code, and read the error message in the IPython shell. See if you can work out how to fix the code, and get it running smoothly. Keep hitting run code and trying to fix the error until the code is working, then submit your answer.

`@hint`
The bugs are on lines 13 and 16. Your hints are that capitals matter! and look at line 6 to see what your import is called. If you need more help, we also made a plot in exercise 3.3, can you replicate that here?

`@pre_exercise_code`

```{python}

```


`@sample_code`

```{python}
#List of dice rolls
Dicerolls = []

#Make any neccesary imports here
from random import randint
import matplotlib.pyplot as plt

#Create a for loop below to append the sum of 2 dice rolls to the Dicerolls list, 100 times.
for i in range(100):
  Dicerolls.append(randint(1, 6) + randint(1, 6))

#Create a histogram of dicerolls
plt.hist(dicerolls)

#Plot the histogram
plot.show()
```

`@solution`

```{python}
#List of dice rolls
Dicerolls = []

#Make any neccesary imports here
from random import randint
import matplotlib.pyplot as plt

#Create a for loop below to append the sum of 2 dice rolls to the Dicerolls list, 100 times.
for i in range(100):
  Dicerolls.append(randint(1, 6) + randint(1, 6))
  
plt.hist(Dicerolls)
plt.show()
```

`@sct`

```{python}
Ex().has_equal_ast()
success_msg("The code is running smoothly! Fantastic fixing skills you have there.")
```

---

## Profit profit profit

```yaml
type: NormalExercise 
xp: 100 
key: ed4c231dbe   
```


The casino wants to know if they've made any money from Zworby. 

Zworby has rolled 2 dice 100 times, using the system you have created. The results have been added to a list called Dicerolls already, so you don't need to make another list. Print out Dicerolls if you don't believe it. 

The casino would like to know if they have made any money. The rules of the game are that Zworby pays 1 markle each time she rolls 2 dice, and if the total is 10 or higher, she wins 5 markles. 

There is also additional costs to the casino, of 0.05 markles per double dice roll, which cover things such as electricity bills and advertising for the game. So the total cost for 100 double rolls is 5 markles. 

If you complete this exercise, try to work out if the casino is statistically likely to make or lose money on this game.


`@instructions`
Work out the total profit, or loss that the casino has made from the trial, using the results contained in the Dicerolls list already made for you. Remember to include the additional costs.

Assign this to a variable called 'profit', and print this variable. 

You may wish to make use of a counter. You can add 1 to a variable, in a loop for example, using `x += 1` which will add 1 to the value of `x` each time it is run.

`@hint`
Make a variable to count the number of times Zworby rolls a 10, 11, or 12. Set this to 0. Then make a for loop which goes through the Dicerolls list, adding 1 to the counter variable for each roll over 9, you can use an if statement for this. Finally, use this formula Profit = amount Zworby pays - amount Zworby wins - Additional costs to work out the profit made by the casino. You might want to go back to previous exercises on for loops and if statements for more help.

`@pre_exercise_code`

```{python}
Dicerolls = [9,
 7,
 6,
 8,
 6,
 9,
 10,
 6,
 7,
 8,
 5,
 11,
 9,
 8,
 9,
 3,
 7,
 8,
 4,
 11,
 8,
 6,
 6,
 8,
 2,
 10,
 11,
 6,
 7,
 7,
 11,
 9,
 8,
 5,
 3,
 3,
 2,
 2,
 8,
 8,
 9,
 8,
 6,
 9,
 4,
 10,
 7,
 8,
 8,
 5,
 2,
 7,
 7,
 5,
 5,
 4,
 7,
 4,
 7,
 8,
 8,
 11,
 6,
 5,
 4,
 9,
 2,
 8,
 10,
 7,
 4,
 9,
 4,
 9,
 10,
 8,
 7,
 8,
 7,
 8,
 7,
 7,
 9,
 9,
 6,
 7,
 3,
 7,
 11,
 12,
 9,
 7,
 8,
 6,
 7,
 6,
 10,
 12,
 6,
 7]
```

`@sample_code`

```{python}

```


`@solution`

```{python}
#Count variable to count the number of Zworby's winning rolls
count = 0
#for loop iterating over all the rolls
for i in Dicerolls:
  	#Winning rolls are those over 9
    if i > 9:
      	#Add 1 to the count for each winning roll
        count += 1
        
#Profit = amount Zworby pays - amount Zworby wins - Additional costs
profit = 100 - count * 5 - 5
#print the profit made
print (profit)
```

`@sct`

```{python}
Ex().has_printout(0)
```
