# Methods and Python Documentation 

## Methods
- Built-in objects in Python have a variety of methods you can use. 

```python
mylist = [1,2,3]

# some useful methods for lists, already seen .append(), .pop()

mylist.append(4)
mylist
# [1,2,3,4]
mylist.pop()
mylist
# [1,2,3]

# too many methods to go through for this course, otherwise hours and hours of video. But can discover methods on your own. In Jupyter noteback can hit . then tab once you've created an object and then see all the methods available. Can also use the help function. 

mylist.insert # shift tab after the method call and it will tell you what it is. 
# If not using jupyter notebook, can use the built in help function: help(mylist.insert) -- will return the doc string.

# third option is to view the python documention. https://docs.python.org/3/
```

# Introduction to Functions
- Creating clean repeatable code is a key part of becomming an effective programmer
- **Functions** allow us to create blocks of code that can be easily executed many times, without needing to constantly rewrite the entire block of code. 
- Functions will be a huge leap forward in your capabilityes as a Python programmer. 
- This also means the problems you will solve can be a lot harder! 
- It is very important to get practice combining everything you've learned so far (control flow, loops, etc) with functions to become an effective programmer. 
- This may be a point in your progress where you may get discouraged or frustrated. Don't worry. This is completely normal and very common!
- We will guide you step by step, be patient with yourself and practice, practice, practice!!

# def keyword

- Creating a function in python requires a very specific syntax, including the **def** keyword, correct indentation and proper structure. 

```python
# keyword telling python this is a function
def name_of_function():
# snake case, whatever you decide the function should be named. Snake casing is all lowercase with underscores between words. 
# Parenthesis at the end. Later on we can pass in arguments/parameters into the function. A colon indicates an upcoming indented block. Everything indented is "inside" the function 
    '''
    Docstring explains function
    '''
    # optional: Multi-line string to describe the function
    # Note everything inside the function is indented. 
    print("Hello") # Code goes inside the function. 

name_of_function() # Function can then be executed/called to see the result
# Hello -- Resulting output. 

# Functions can become more complex by accepting an argument to be passed by the user such as say: name_of_function(name) print("Hello" + name) 
# name_of_function("Jose")
# Hello Jose
```

- Typically we use the **return** keyword to send back the result of the function, instead of just printing it out.
- **return** allows us to assign the output of the functin to a new variable.

- In general, will rarely have `print()` inside of a function as used in example above. Because we would just call it outside. 
- Typically we use the **return** keyword to send back the result of the function instead of just printing it out.
- **return** allows us to assign the output of the function to a new variable.
- We'll have a deeper discussion of the **return** keyword later on. 

```python
def add_function(num1, num2):
    return num1+ num2 # return allows us to save the result to a variable, which print does not. Means when we call add_function(1,2) it will inside of the function do 1 + 2 = 3, and with return we can save the result to a variable. 

result = add_function(1,2)
print(result)
# 3
```

Most functions use return, rarely will a function just print. 

# Basics of Python Functions

```python
def say_hello():
    print("hello")

say_hello()
# hello

def say_hello(name):    
    print(f'Hello {name}')

say_hello('Jose')
# Hello Jose

# default value to avoid getting an error if you accidentally call the function without an argument:
def say_hello(name='Default'):
    print(f'Hello {name}')

sayHello()
# Hello Default

def add_num(num1,num2):
    return num1+num2

result = add_num(10,20)
result
# 30

def print_result(a,b):
    print(a+b)

def return_result(a,b):
    return a+b

# Can't do this: result = print_result(10,20) will not return it or print anything out. Type of result is NoneType
print_result(10, 20)
# 30 -- no Output cell like with return 

return_result(10,20)
# 30 - Jupyter notebook shows an output cell for it. Out[40]
result = return_result(10,20)
result
# 30

# not common to do this
def myfunc(a,b):
    print(a+b)
    return a+b

result = myfunc(10,20)
# 30

result
# 30

def sum_numbers(num1, num2):
    return num1+num2
    # not checking that it's actually returning numbers. 

sum_numers(10, 20)
# 30
sum_numers('10', '20')
# '1020'

# probably should make sure to verify the type of data before returning the result if use has to input things.

```

What's the main difference between print and return in a function? Return's result will allow you to save them as a variable. 

# Logic with Python Functions

Simple function that checks if something is even, and expand from there. Already know a bit of python logic

```python
# Mod Operator - shows the remainder after division
2 % 2 
# 0
3 % 2
# 1
41 % 40
# 1

# If a number is even, that number mod 2, should be equal to 0. Then we knew it's even, if not, it's not even. 
20 % 2 == 0
# True 
21 % 2 == 0
# False

# Lets construct this into a function. 
def even_check(num):
    result = num % 2 == 0
    return result 

even_check(20)
# True 
even_check(21)
# False

# For beginners it's easy to separate out onto two lines. Instead, we could just directly return it 
def even_check(number):
    return number % 2 == 0

# RETURN TRUE IF ANY NUMBER IS EVEN INSIDE A LIST
def check_even_list(num_list):
    for number in num_list:
        if number % 2 == 0:
            return True 
        else:
            # pass keyword just means don't do anything
            pass
        # return False # WRONG!!!! Because means the if/else will only be able to check one number, doesn't go further if there's other even numbers after initially False as there's a return call on either condition. So the return false should be an indentation with the for loop after everything has been completed. So it should be here. A super common mistake beginners make is thinking that all return statements have to be indented on the same spot. They don't. 
    return False

check_even_list([1,3,5])
# returns nothing
check_even_list([2,4,5])
# True 
# edge cases 
check_even_list([2,1,1,1])
# True 
check_even_list([1,1,1,2])
# True

# Let's expand the function even more in complexity and return all the even numbers in the list. 
def check_even_list(num_list):
    # return all the even numbers in a list

    # placeholder variables
    even_numbers = []

    for number in num_list:
        if number % 2 == 0:
            even_numbers.append(number)
        else:
            pass

     return even_numbers

check_even_list([1,2,3,4,5])
# [2, 4]
check_even_list([1,3,5])
# []
```

# Tuple unpacking with Python Functions

```python
# have seen before we can loop through a list of tuples and unpack them 

stock_prices = [('APPL',200), ('GOOG',400), ('MSFT',100)]
for item in stock_prices:
    print(item)

# ('APPL', 200)
# ('GOOG', 400)
# ('MSFT', 100)

for ticker,price in stock_prices:
    print(ticker)
# APPL
# GOOG
# MSFT

work_hours = [('Abby',100),('Billy',4000),('Cassie',800)]

def employee_check(work_hours):

    current_max = 0
    employee_of_month = ''

    for employee,hours in work_hours:
        # keep comparing through list of tuples, and switching when it's higher
        if hours > current_max:
            current_max = hours
            employee_of_month = employee
        else:
            pass

    # Return tuple 
    return (employee_of_month, current_max)

employee_check(work_hours)
# ('Cassie', 800)

# Can do two things, say: 
result = employee_check(work_hours)
# ('Cassie', 800)

# OR just before with the for loop, can do:
name,hours = employee_check(work_hours)
name
# 'Cassie'
hours
# 400

# Can do tuple unpacking with this function call, but to avoid unpacking too many, say calling for 3 variables when there's only 2 in reality (which will throw an error), can assign the value to a variable:
item = employee_check(work_hours)
# And then start exploring that variable:
item
('Billy', 4000)
```

# Interactions between python functions 
- Typically a python script or notebook contains several functions interacting with each other 
- Let's create a few functions to mimic the carnival guessing game "Three Cup Monte."

- Our simple game won't actually show the cups or ball, instead we will simply mimic the effect with a Python list.
- Our simple version will also not show the shuffle to the user, so the guess is completely random.

```python
# How to shuffle a list at random in python. Python has a built in random module. 
example = [1,2,3,4,5,6,7]
from random import shuffle
shuffle(example)
example
# [5, 2, 1, 3, 6, 7, 4]

result = shuffle(example)
result # All happens in place, so nothing is returned 

# Our own version of shuffle that returns the example list 
def shuffle_list(mylist):
    shuffle(mylist)
    return mylist

result = shuffle_list(example)
result 
# [5, 6, 1, 7, 4, 2, 3]

mylist = ['', 'O', ''] # O is the red ball and we will call...
shuffle_list(mylist)
# ['O', '', ''] and the O will shuffle around.

def player_guess():
    guess=''

    # Can implement a while loop to see if the guess is correct
    while guess not in ['0', '1', '2']:
        # Can guess 1 of 3 positions
        guess = input("Pick a number: 0, 1, or 2")

    return int(guess)

player_guess()
# Pick a number: 0, 1 or 2, 1
# 1 
# can save the output 
myindex = player_guess()
# Pick a number: 0, 1, or 2

# One more function to check if the guess is correct or not, and this is where the functions interact with one another
def check_guess(mylist, guess):
    if mylist[guess] == 'O':
        print('Correct!')
    else:
        print("Wrong guess!")
        print(mylist)

# Initial list 
mylist = ['', 'O', '']
# Shuffle that list 
mixexup_list = shuffle_list(mylist)
# User guess 
guess = player_guess()
# Check guess
check_guess(mixedup_list, guess)
```

# Python Function Coding Exercises:

```python
# Functions 1
# Write a function called myfunc that prints the string 'Hello World'.

# For example:

# def myfunc():
#    print('Some text')

def myfunc():
   print('Hello World')

# Functions 2: print Hello Name
# Define a function called myfunc that takes in a name, and prints 'Hello Name' 

# NOTE: Define the function, but do not run it!

# Also, do not use f-strings, as they are not supported in this Coding Exercise.

# For example:

# def myfunc(name):
#    print('My name is {}'.format(name))

def myfunc(name):
    print('Hello ' + name)

# OR 

def myfunc(name):
    print('Hello {}'.format(name))

# Functions #3 - simple Boolean
# Define a function called myfunc that takes in a Boolean value (True or False). If True, return 'Hello', and if False,  return 'Goodbye'

# Remember, don't run the function, simply provide the definition.

# For example, a function that returns 'Inside' if a is True and 'Outside' if a is False could look like:

# def myfunc(a):
#     if a == True:
#         return 'Inside'
#     elif a == False:
#         return 'Outside'
# This is all you need to enter!

# To give an idea what the above function would look like when tested:

# myfunc(False)
# Output: 'Outside'

def myfunc(a):
    if a == True:
        return 'Hello'
    elif a == False:
        return 'Goodbye'

# Functions #4 - using Booleans
# Define a function called myfunc that takes three arguments, x, y and z.
# If z is True, return x.  If z is False, return y.

# Remember, don't run the function, simply provide the definition.

# For example, a function that returns a if c is True and b if c is False might look like:

# def myfunc(a,b,c):
#     if c == True:
#         return a
#     else:
#         return b
# This is all you need to enter!

# To give an idea what the function would look like when tested:

# myfunc('Hello','Goodbye',False)
# Output: 'Goodbye'

def myfunc(x,y,z):
    if z == True:
        return x
    elif z == False:
        return y

# Functions #5: simple math
# Define a function called myfunc that takes in two arguments and returns their sum.

# Remember, don't run the function, simply provide the definition.

# For example, a function that takes in two arguments and returns their product might look like:

# def myfunc(a,b):
#     return a*b
# This is all you need to enter!

# To give an idea what the above function would look like when tested:

# myfunc(5,12)
# Output: 60

def myfunc(a,b):
    return a + b

# Functions #6: is even
# Define a function called is_even that takes in one argument, and returns True if the passed-in value is even, False if it is not.

# Remember, don't run the function, simply provide the definition.

# For example, a function that returns True if a value is divisible by 3 might look like:

# def is_evenly_divisible_by_3(n):
#     if n%3 == 0:
#         return True
#     else:
#         return False
# This is all you need to enter!

# To give an idea what the above function would look like when tested:

# is_evenly_divisible_by_3(15)
# Output: True
# Added note: this exercise requires that the function return True or False. Print statements will not work here.

def is_even(x):
    if x % 2 == 0:
        return True 
    else:
        return False

# Functions #7: is greater
# Define a function called is_greater that takes in two arguments, and returns True if the first value is greater than the # second, False if it is less than or equal to the second.

# Remember, don't run the function, simply provide the definition.

# For example, a function that returns True if the first value is less than the second might look like:

# def is_less(c,d):
#     if c < d:
#         return True
#     else:
#         return False
# This is all you need to enter!

# To give an idea what the above function would look like when tested:

# is_less(5,9)

def is_greater(x,y):
    if x > y:
        return True 
    elif x <= y:
        return False 
```

# *args and **kwargs in Python

Two functional parameters *args and **kwargs. (Star args, and double star kwargs). Stands for arguments and keyword arguments. Eventually working with python, you're going to want a way to accept an arbitrary number of arguments and keyword arguments w/o having to define in your function calls. 

```python
def myfunc(a,b):
    # Returns 5% of the sum of a and ab
    return sum((a,b)) * 0.05

myfunc(40, 60)
# 5.0

# What if I had more numbers or parameters to pass in? A and B are examples of positional arguments. 40 is assigned to a as it was in the first position, first argument, and 60 is b as it was in the second position, second argument. But what if we wanted to work with more than two numbers? We could assign more parameters. Could do this:

def myfunc(a,b,c=0,d=0,e=0):
    return sum((a,b,c,d,e)) * 0.05

# Problem is, we'll eventually hit a limit of how many parameters where we can pass in. So this is where we can use star args which alows us to take an arbitrary number of arguments:

# allows us to treat this as a tuple of parameters coming in
def myfunc(*args):
    returm sum(args) * 0.05

myfunc(40,60)
# 5
myfunc(40,60,100,1,34)
# 11.75

# If we print out what *args looks like as a function, it just looks like a tuple:
myfunc(40,60,100,1,34)
#(40, 60, 100, 1, 34)

#*args is useful with the tuple because we can loop through it, iterate, etc. It doesn't have to be args. So long as the star is there, it can be any keyword you want. It's an arbitrary choice. By convention you should always use args. 

def myfunc(*args):
    for item in args:
        print(item)

myfunc(40,60,100,1,34)
# 40
# 60
# 100
# 1
# 34

# **kwargs instead of creating a tuple of values, builds a dictionary of key-value pairs 
def myfunc(**kwargs):
    print(kwargs)
    if 'fruit' in kwargs:
        print('My fruit of choice is {}'.format(kwargs['fruit']))
    else:
        print('I did not find any fruit here')

myfunc(fruit='apple', veggie='lettuce')
# kwargs returns a dictionary we can play around with inside of our function
# {'fruit': 'apple', 'veggie': 'lettuce'}
# My fruit of choice is apple

# kwargs is also arbitrary. What indicates it should be a dictionary are the two stars. 

# Can use *args and **kwargs in combination:
def myfunc(*args, **kwargs):
    print(args)
    print(kwargs)
    print('I would like {} {}'.format(args[0], kwargs['food']))

# Because we said args first and then kwargs in the function, it has to go in that order. Has to be in the same order we prescribed otherwise would get an error.
myfunc(10,20,30, fruit='orange', food='eggs', animal='dog')
# (10, 20, 30)
# {'fruit': 'orange', 'food': 'eggs', 'animal': 'dog'}
# I would like 10 eggs

# This is all very useful when we start using outside libraries. 
```

# Functions #8: *args
Define a function called myfunc that takes in an arbitrary number of arguments, and returns the sum of those arguments.

Remember, don't run the function, simply provide the definition.

For example, a function that returns a count of the number of arbitrary arguments might look like:

def myfunc(*args):
    return len(args)
This is all you need to enter!

To give an idea what the above function would look like when tested:

myfunc(5,6,7,8)
##  Output: 4
Added note: this exercise requires that the function return the sum. Print statements will not work here.

```python
def myfunc(*args):
    return sum(args)
```

# Functions #9: pick evens
Define a function called myfunc that takes in an arbitrary number of arguments, and returns a list containing only those arguments that are even.

Remember, don't run the function, simply provide the definition.

To give an idea what the function would look like when tested:

myfunc(5,6,7,8)
## Output: [6, 8]
Added note: this exercise requires that the function return a list. Print statements will not work here.

```python
def myfunc(*args):
    lists = []
    for item in args:
        if item % 2 == 0:
            lists.append(item)
    return lists
```

# Functions #10: skyline
Define a function called myfunc that takes in a string, and returns a matching string where every even letter is uppercase, and every odd letter is lowercase. Assume that the incoming string only contains letters, and don't worry about numbers, spaces or punctuation. The output string can start with either an uppercase or lowercase letter, so long as letters alternate throughout the string.

Remember, don't run the function, simply provide the definition.

To give an idea what the function would look like when tested:

myfunc('Anthropomorphism')
##  Output: 'aNtHrOpOmOrPhIsM'
Added note: this exercise requires that the function return a string. Print statements will not work here.

```python
def myfunc(str):
    newStr = []

    for i in rang(len(str)):
        if i % 2 == 0:
            newStr.append(str[i].lower())
        else: 
            newStr.append(str[i].upper())
        return ''.join(newStr)
```

# Function Practice Problems

- Learning about functions increases your Python skills exponentially.
- This also means that the difficulties of problems you can solve also increases drastically. 
- Let's get some practice with converting problem statements into Python code. 

# Function Practice Exercises 
```python
# Function Practice Exercises

# Problems are arranged in increasing difficulty:
# * Warmup - these can be solved using basic comparisons and methods
# * Level 1 - these may involve if/then conditional statements and simple methods
# * Level 2 - these may require iterating over sequences, usually with some kind of loop
# * Challenging - these will take some creativity to solve

## WARMUP SECTION:

#### LESSER OF TWO EVENS: Write a function that returns the lesser of two given numbers *if* both numbers are even, but returns the greater if one or both numbers are odd
    lesser_of_two_evens(2,4) --> 2
    lesser_of_two_evens(2,5) --> 5

def lesser_of_two_evens(a,b):
    if a % 2 == 0 and b % 2 == 0:
        if a > b:
            return b
        else:
            return a
    else: 
        if a < b:
            return b
        else:
            return a 

lesser_of_two_evens(2,5)

# Check
lesser_of_two_evens(2,4)

# Check
lesser_of_two_evens(2,5)

#### ANIMAL CRACKERS: Write a function takes a two-word string and returns True if both words begin with same letter
    animal_crackers('Levelheaded Llama') --> True
    animal_crackers('Crazy Kangaroo') --> False

def animal_crackers(text):
    splits = text.split()

    if splits[0][0] == splits[1][0]:
        return True 
    else:
        return False

# Check
animal_crackers('Levelheaded Llama')

# Check
animal_crackers('Crazy Kangaroo')

#### MAKES TWENTY: Given two integers, return True if the sum of the integers is 20 *or* if one of the integers is 20. If not, return False

    makes_twenty(20,10) --> True
    makes_twenty(12,8) --> True
    makes_twenty(2,3) --> False

def makes_twenty(n1,n2):
    if n1 == 20 or n2 == 20:
        return True
    elif n1 + n2 == 20:
        return True 
    else:
        return False

makes_twenty(10,10)
# True

# Check
makes_twenty(20,10)

# Check
makes_twenty(2,3)

# LEVEL 1 PROBLEMS

#### OLD MACDONALD: Write a function that capitalizes the first and fourth letters of a name
     
    old_macdonald('macdonald') --> MacDonald
    
# Note: `'macdonald'.capitalize()` returns `'Macdonald'`

def old_macdonald(name):
    return name[0].capitalise() + name[1:3] + name[3].capitalize() + name[4:]

# Check
old_macdonald('macdonald')
# 'MacDonald'

#### MASTER YODA: Given a sentence, return a sentence with the words reversed

    master_yoda('I am home') --> 'home am I'
    master_yoda('We are ready') --> 'ready are We'
    
# Note: The .join() method may be useful here. The .join() method allows you to join together strings in a list with some connector string. For example, some uses of the .join() method:

#    >>> "--".join(['a','b','c'])
#    >>> 'a--b--c'

# This means if you had a list of words you wanted to turn back into a sentence, you could just join them with a single space string:

#    >>> " ".join(['Hello','world'])
#    >>> "Hello world"

def master_yoda(text):
    string = text.split()
    string.reverse()
    newstring = ' '.join(string)
    return newstring

# Check
master_yoda('I am home')

# Check
master_yoda('We are ready')

#### ALMOST THERE: Given an integer n, return True if n is within 10 of either 100 or 200

    almost_there(90) --> True
    almost_there(104) --> True
    almost_there(150) --> False
    almost_there(209) --> True
    
NOTE: `abs(num)` returns the absolute value of a number

def almost_there(n):
    pass

# Check
almost_there(104)

# Check
almost_there(150)

# Check
almost_there(209)

# LEVEL 2 PROBLEMS

#### FIND 33: 

Given a list of ints, return True if the array contains a 3 next to a 3 somewhere.

    has_33([1, 3, 3]) → True
    has_33([1, 3, 1, 3]) → False
    has_33([3, 1, 3]) → False

def has_33(nums):
    pass

# Check
has_33([1, 3, 3])

# Check
has_33([1, 3, 1, 3])

# Check
has_33([3, 1, 3])

#### PAPER DOLL: Given a string, return a string where for every character in the original there are three characters
    paper_doll('Hello') --> 'HHHeeellllllooo'
    paper_doll('Mississippi') --> 'MMMiiissssssiiippppppiii'

def paper_doll(text):
    pass

# Check
paper_doll('Hello')

# Check
paper_doll('Mississippi')

#### BLACKJACK: Given three integers between 1 and 11, if their sum is less than or equal to 21, return their sum. If their sum exceeds 21 *and* there's an eleven, reduce the total sum by 10. Finally, if the sum (even after adjustment) exceeds 21, return 'BUST'
    blackjack(5,6,7) --> 18
    blackjack(9,9,9) --> 'BUST'
    blackjack(9,9,11) --> 19

def blackjack(a,b,c):
    pass

# Check
blackjack(5,6,7)

# Check
blackjack(9,9,9)

# Check
blackjack(9,9,11)

#### SUMMER OF '69: Return the sum of the numbers in the array, except ignore sections of numbers starting with a 6 and extending to the next 9 (every 6 will be followed by at least one 9). Return 0 for no numbers.
 
    summer_69([1, 3, 5]) --> 9
    summer_69([4, 5, 6, 7, 8, 9]) --> 9
    summer_69([2, 1, 6, 9, 11]) --> 14

def summer_69(arr):
    pass

# Check
summer_69([1, 3, 5])

# Check
summer_69([4, 5, 6, 7, 8, 9])

# Check
summer_69([2, 1, 6, 9, 11])

# CHALLENGING PROBLEMS

#### SPY GAME: Write a function that takes in a list of integers and returns True if it contains 007 in order

     spy_game([1,2,4,0,0,7,5]) --> True
     spy_game([1,0,2,4,0,5,7]) --> True
     spy_game([1,7,2,0,4,5,0]) --> False


def spy_game(nums):
    pass

# Check
spy_game([1,2,4,0,0,7,5])

# Check
spy_game([1,0,2,4,0,5,7])

# Check
spy_game([1,7,2,0,4,5,0])

#### COUNT PRIMES: Write a function that returns the *number* of prime numbers that exist up to and including a given number
    count_primes(100) --> 25

By convention, 0 and 1 are not prime.

def count_primes(num):
    pass
                

# Check
count_primes(100)

### Just for fun:
#### PRINT BIG: Write a function that takes in a single letter, and returns a 5x5 representation of that letter
    print_big('a')
    
    out:   *  
          * *
         *****
         *   *
         *   *
HINT: Consider making a dictionary of possible patterns, and mapping the alphabet to specific 5-line combinations of patterns. <br>For purposes of this exercise, it's ok if your dictionary stops at "E".

def print_big(letter):
    pass

print_big('a')

## Great Job!
```
# Function Practice Exercises: Solutions 

```python
# Warm up
def lesser_of_two_evens(a,b):
    if a%2 == 0 and b%2 == 0:
        # BOTH NUMBERS ARE EVEN! 
        if a < b: 
            result = a 
        else:
            result = b
    else: 
        # ONE OR BOTH NUMBERS ARE ODD! 
        if a > b:
            result = a 
        else:
            result = b
    return result 

# Can clean up this code by using the min() function and max() function. 
def lesser_of_two_evens(a,b):
    if a%2 == 0 and b%2 == 0:
        # BOTH NUMBERS ARE EVEN! 
        # result = min(a,b)
        return min(a,b)
    else: 
        # ONE OR BOTH NUMBERS ARE ODD! 
       # result = max(a,b)
       return max(a,b)
    # return result

# animal crackers
def animal_crackers(text):
    wordlist = text.split()

    first = wordlist[0]
    second = wordlist[1]

    return first[0] == second[0]

def animal_crackers(text):
    wordlist = text.split()
    # could check that the text is write case: wordlist = text.lower().split()

    return wordllist[0[0] == wordlist[1][0]

# Makes Twenty 

def makes_twenty(n1,n2):
    if n1 + n2 == 20:
        return true 
    elif n1 == 20:
        return True 
    elif n2 == 20:
        return True 
    else:
        return False

# Better way to write it 
def makes_twenty(n1,n2):
    return (n1+n2) == 20 or n1==20 or n2==20
```

# Functions Practice Problems Solutions Level 1

```python
def old_macdonald(name):
    first_letter = name[0]
    inbetween = name[1:3]
    fourth_letter = name[3]
    rest = name[4:]

    return first_letter.upper() + inbetween + fourth_letter.upper() + rest

def old_macdonald(name):
    first_half = name[:3]
    second_half = name[3:]

    return first_half.capitalize() + second_half.capitalise()

# Master Yoda 

def master_yoda(text):
    wordlist = text.split()
    reversed_wordlist = wordlist[::-1]
    return ' '.join(reversed_word_list)

# Using join to get the wordlist back together. 
mylist = ['a', 'b', 'c'c]
'--'.join(mylist)
#'a--b--c' will concatenate and fill in between every piece of the list. 
# '' blank string or ' ' to get abc or a b c

# Almost There 
def almost_there(n):
    # want to check if 100 - n the abosolute value of that is <= 10 

    return (abs(100-n) <= 10) or (abs(200-n) <= 10)
```

# Functions Practice Solutions Level 2

```python
# Find 33

def has_33(nums):
    # want to go to the second to last digit, so we can check the last digit. If we went to the last digit there would be nothing to check
    # goes through every single index position in the list, up to the second to last one. 
    for i in range(0,len(nums)-1):
        # then check if the last two numbers are 3 to make '33'
        if nums[i] == 3 and nums[i+1] == 3:
            return True 

    return False

# Alternative way to write the logic, doesn't look as nice:
    if nums[i:i+2] == [3,3]

# Paper Doll

def paper_doll(text):
    # trick is to start with an empty string and just keep concatenating to that string 

    result = ''

    for char in text:
        result += char*3
    return result

# Blackjack

def blackjack(a,b,c):

    # sum is the sam as saying a+b+c
    if sum([a,b,c]) <= 21:
        return sum([a,b,c])
    # if there's an 11 in there, and the sum put together is less than or equal to 31
    elif 11 in [a,b,c] and sum([a,b,c]) <= 31:
        return sum([a,b,c])-10
    else:
        return 'BUST'

# Summer of '69 
def summer_69(arr):

    total = 0
    add = True 

    for num in arr:
        while add:
            if num!= 6:
                total += num
                break 
            else:
                add = False 
        while not add: # while add != True
            if num != 9:
                break
            else:
                add = True
                break 
    return total
```

# Function Exercises Challenging Problems Solutions 

```python
# Spy Game
# 007 doesn't have to be consecutive
def spy_game(nums):
    code = [0,0,7,'x']
    # [0, 7, 'x']
    # [7, 'x']
    # ['x'] length=1

    # iterate through and see if hey, number is equal to first num in this code list. Then pop it off at the first index, so next iteration is looking for next 0, then 7. And so on until we have 007. and ['x'] length=1
    for num in nums:
        if num == code[0]:
            code.pop(0)
    return len(code) == 1

# Count Primes: Write a function that returns the number of prime numbers that exist up to and including a given number 
# By convenction we'll treat 0 and 1 as not prime
def count_primes(num):

    # check for 0 or 1 input
    if num < 2:
        return 0
    ###########################
    # 2 or greater if not returned before this
    ##########################

    # Store our prime numbers
    primes = [2]
    # Counter going up to the input num
    x = 3

    # x is going through every number up to input num
    while x <= num:
        # step size of 2 because even number beyond 2 are not primes. 
        # Check if x is prime
        for y in range(3,x,2):
            if x%y == 0:
                # not a prime number 
                x += 2
                break
        # If we can successfully go throug the for loop and not break out of it, then we have a prime number somewhere 
        else: # if we went through the entire for loop and it didn't break, then we'll execute below. For/else is a challenge can only do it because of the break statement. 
            primes.append(x)
            x += 2
    print(primes)
    return len(primes)
# clever trick, don't have to check every number up to x. could say for y in primes: 

def print_big(letter):
    patterns = {1:'  *  ',2:' * * ',3:'*   *',4:'*****',5:'**** ',6:'   * ',7:' *   ',8:'*   * ',9:'*    '}
    alphabet = {'A':[1,2,4,3,3],'B':[5,3,5,3,5],'C':[4,9,9,9,4],'D':[5,3,3,3,5],'E':[4,9,4,9,4]}
    for pattern in alphabet[letter.upper()]:
        print(patterns[pattern])
```
# Lambda Expressions Map and Filter 
Way to quickly create anonymous functions, a function that's used once and then never again. Don't name them, never really reference them again. 

```python
def square(num):
    return num**2

my_nums = [1,2,3,4,5]

# Want to apply square to all numbers in my list. Can do a for loop, easier to do it using map. 
for item in map(square, my_nums):
    print(item)
# Have to iterate through, otherwise just get a memory space. 
# 1
# 4
# 9
# 16
# 25

list(map(square, my_nums))
[1, 4, 9, 16, 25]

def splicer(mystring):
    if len(mystring) % 2 == 0: 
        return 'EVEN'
    else:
        return mystring[0]

names = ['Andy', 'Eve', 'Sally']
list(map(splicer, names))
['EVEN', 'E', 'S']

# When using the map function, passing in square or splicer, not calling them to execute within the map. Map itself executes them. Do not add in the parentheses to call them. Just pass the function itself as an argument. 

# Filter function - filter by a function that returns either true or false. 
def check_even(num):
    return num % 2 == 0 

mynums = [1,2,3,4,5,6]

list(filter(check_even, mynums))
# [2, 4, 6]

# or can iterate through it:
for n in filter(check_even, mynums):
    print(n)
# 2
# 4
# 6

# Lambda expressions and see why they are useful: 

def square(num):
    result = num ** 2 
    return result

square(3)
# 9

# Slowly step by step, turn square into a lambda expression
def square(num):
    return num ** 2 

# if we run, it's the exact same thing. 
# Can also write this all on one line:
def square(num): return num ** 2

# almost in the form of a lambda expression. A lambda is also known as an anonymous function. Some functionality you only intend to use one time. 

# replace def keyword with lambda, and remove the return (it's implied)
square = lambda num: num ** 2
square(5)
# 25

# Typically don't name them. Instead going to use it in conjunction with other functions such as map and filter. 

# Here's where they shine:

list(map(lambda num:num**2, mynums))
# [1, 4, 9, 16, 25, 36]

def check_even(num): 
    return num%2 == 0

list(filter(lambda num: num%2 == 0, mynums))
# [2, 4, 6]

# Lambda expressions can be used for a variety of things. Say we want the first character of the strings. 

list(map(lambda name:name[0], names))
# ['A', 'E', 'S']

# say we wanted to reverse the names
list(map(lambda x:x[::-1], names))
# ['ydnA', 'evE', 'yllaS']

# can even pass in multiple arguments to a lambda expression. But not every single complex function will directly translate to a lambda. Should only use lambda's when you can read it clearly. 
```
# Nested Statements and Scope 

When you create a variable name in python, it's stored in the namespace. Variable names also have a scope, and that scope determines visibility. 

```python
x = 25 
def printer():
    x = 50
    return x 

printer(x)
# 25

print(printer())
# 50 

# How does python which x assignment we're referring to in our code? Why doesn't the reassignment affect later on when we ask to print(x). The rules are LEGB rule format. LEGB stands for Local Enclosing Function Locals Global Built in
```
**LEGB RULE**: 
- **L: Local** - Names assigned in any way within a function (def or lamda), and not declared global in that function
- **E: Enclosing function locals** - Names in the local scope of any and all enclosing functions (def or lambda), from inner to outer.
- **G: Global (module)** - Names assigned at the top-level of a module file, or declared global in a def within the file. 
- **B: Built-in (Python)** - Names preassigned in the built-in names module: open, range, SyntaxError,...

```python
# Local
lambda num:num**2 
# num is local to the lambda expression 

# Enclosing function locals 
name = 'THIS IS A GLOBAL STRING'

def greet():
    # sets variable name equal to Sammy
    name = 'Sammy'
    # inside of the greet function we have another function
    def hello():
        print('Hello ' + name)
    # call and execute hellow
    hello()

greet()
# Hello Sammy

# When I execute greet() I'm calling and executing the greet function, it assigns name to Sammy, defined function hello, and then executes the function hello. Look in local namespace, within a function. If it can't find it, it goes to enclosing function locals (function within a function) and there, name is defined as Sammy.

# If we comment out Sammy within greet() and run the function again, we get back HELLO THIS IS A GLOBAL STRING. Again, first looked at locally, it's not there, then it's not in the enclosing function, so we then look globally and it's there at the global level. 

# GLOBAL
name = 'THIS IS A GLOBAL STRING'

def greet():
    # ENCLOSING
    name = 'Sammy'
 
    def hello():
        # LOCAL
        name = 'IM A LOCAL'
        print('Hello ' + name)

    hello()

greet()
# Hello IM A LOCAL

# Only level above global is the built in function level, which would be something like:
len #length
#<function len>
# Be careful not to overwrite the built in function names. 

x = 50 

def func(x):
    print(f'X is {x}')

func(x)
# X is 50 

# Reassigning X locally. 
x = 50 

def func(x):
    print(f'X is {x}')

    # LOCAL REASSIGNMENT! 
    x = 200 
    print(f'I JUST LOCALLY CHANGED X TO {x}')

func(x)
# X is 50 
# I JUST LOCALLY CHANGED X TO 200

print(x)
# 50 - get this back even though we reassigned x to be 200. It's happening because the reassignment is only happening in the local namespace inside the function. Doesn't effect anything at a higher scope. 

# Let's imagine you're in a situation where you did want to grab the global x and reassign to 200. How would we do that? Not grab x as a parameter for starters 

x = 50 

def func():
    # declare a global x, tells Python I want you to go to the namespace, jump to the global level, and grab the value there. It will affect the global x. 
    global x 
    print(f'X is {x}')

    # LOCAL REASSIGNMENT ON A GLOBAL VARIABLE
    x = 'NEW VALUE' 
    print(f'I JUST LOCALLY CHANGED GLOBAL X TO {x}')

print(x)
# 50 

func()
# X is 50
# I JUST LOCALLY CHANGED GLOBAL X TO NEW VALUE

# Should avoid using the  global keyword unless absolutely necessary. Should instead take it in as a parameter, do the reassignment, and then return the reassignment as the value itself:

def func(x):

    print(f'X is {x}')

    x = 'NEW VALUE' 
    print(f'I JUST LOCALLY CHANGED GLOBAL X TO {x}')
    return x

x = func(x)
# X is 50 
# I JUST LOCALLY CHANGED GLOBAL X TO NEW VALUE

x
# New Value
```

# Methods and Functions Homework overview

Functions and Methods Homework
Complete the following questions:

```python
# Write a function that computes the volume of a sphere given its radius.

# The volume of a sphere is given as
 

def vol(rad):
    return 4/3*(3.14*(rad**3))
# Check
vol(2)

# 33.49333333333333
#Write a function that checks whether a number is in a given range (inclusive of high and low)

def ran_check(num,low,high):
    # need to be inclusive, range goes up to but does not include! 
    if num in range(low, high+1):
        print(f'{num} is in the range between {low} and {high}')
    else:
        print('The number is outside of the range')
# Check
ran_check(5,2,7)
# 5 is in the range between 2 and 7

# If you only wanted to return a boolean:

def ran_bool(num,low,high):
    if num in range(low, high):
        return True 
    else:
        return False
ran_bool(3,1,10)
# True
# Write a Python function that accepts a string and calculates the number of upper case letters and lower case letters.

# Sample String : 'Hello Mr. Rogers, how are you this fine Tuesday?'
# Expected Output : 
# No. of Upper case characters : 4
# No. of Lower case Characters : 33

# HINT: Two string methods that might prove useful: .isupper() and .islower()

# If you feel ambitious, explore the Collections module to solve this problem!

def up_low(s):
    upper = 0
    lower = 0
    for letter in s:
        if letter.isupper():
            upper+=1
        elif letter.islower():
            lower+=1
    print('No. of Upper case characters:', upper)
    print('No. of Lower case Characters:', lower)

s = 'Hello Mr. Rogers, how are you this fine Tuesday?'
up_low(s)
# Original String :  Hello Mr. Rogers, how are you this fine Tuesday?
# No. of Upper case characters :  4
# No. of Lower case Characters :  33
# Write a Python function that takes a list and returns a new list with unique elements of the first list.

# Sample List : [1,1,1,1,2,2,3,3,3,3,4,5]
# Unique List : [1, 2, 3, 4, 5]
def unique_list(lst):
    newlist = set(list)
    return set(newlist)

unique_list([1,1,1,1,2,2,3,3,3,3,4,5])
# [1, 2, 3, 4, 5]
# Write a Python function to multiply all the numbers in a list.

# Sample List : [1, 2, 3, -4]
# Expected Output : -24
def multiply(numbers):  
    newnum = 1
    for num in numbers:
        newnum = newnum*num 
    return newnum

multiply([1,2,3,-4])
# -24
# Write a Python function that checks whether a word or phrase is palindrome or not.

# Note: A palindrome is word, phrase, or sequence that reads the same backward as forward, e.g., madam,kayak,racecar, or a phrase "nurses run". Hint: You may want to check out the .replace() method in a string to help out with dealing with spaces. Also google search how to reverse a string in Python, there are some clever ways to do it with slicing notation.

def palindrome(s):
    reverse = s[::-1]
    if s == reverse:
        return True 
    else:
        return False

palindrome('helleh')
# True
# Hard:
# Write a Python function to check whether a string is pangram or not. (Assume the string passed in does not have any punctuation)

# Note : Pangrams are words or sentences containing every letter of the alphabet at least once.
# For example : "The quick brown fox jumps over the lazy dog"

# Hint: You may want to use .replace() method to get rid of spaces.

# Hint: Look at the string module

# Hint: In case you want to use set comparisons

import string

def ispangram(str1, alphabet=string.ascii_lowercase):
    for char in alphabet:
        if char not in str1.lower():
            return False 
    return True

ispangram("The quick brown fox jumps over the lazy dog")
# True
string.ascii_lowercase
'abcdefghijklmnopqrstuvwxyz'
```

Great Job!

# Methods and Functions Homework - Solutions

```python
def vol(rad):
    # Pi can be imported from math module, could say From Math import Pi
    return (4/3)*(3.14)*(rad**3)

def ran_check(num, low, high):
    if num in range(low, high+1):
        print(f'{num} is in range of {low} and {high}')
    else: 
        print('not in range)

# Two separate variables method
def up_lows(s):
    lowercase = 0
    uppercase = 0

    for char in s:
        if char.isupper():
            uppercase += 1
        elif char.islower():
            lowercase += 1
        else: 
            pass

    print(f'Original string: {s}')
    print(f'Uppercase count: {uppercase}')
    print(f'Lowercase count: {lowercase}')
 
# Dictionary answer 
def up_lows(s):
    d = {'upper':0, 'lower':0}

    for char in s:
        if char.isupper():
            d['upper'] += 1
        elif char.islower():
            d['lower'] += 1
        else: 
            pass

    print(f'Original string: {s}')
    print(f'Uppercase count: {d["upper"]}')
    print(f'Lowercase count: {d["lower"]}')

# Simplest and most pythonic way of doing it
def unique_list(lst):
    return list(set(lst))

# manual way
def unique_list(list):
    seen_numbers = []
    for num in lst:
        if number not in seen_numbers:
            seen_numbers.append(number)
    return seen_numbers

def multiply(numbers):
    total = 1 
    for num in numbers:
        total = total * num 
    return total

def palindrome(s):
    # REMOVE SPACES FROM STRING
    s = s.replace(' ','') # replace all spaces with nothing. 

    # Check if string is == reversed version of the string
    return s == s[::-1] # start all the way from the beginning, go to the end, grab a step size of 1, a step size of neg 1 means start all the way at the end and go backwards. 

import string 
def ispanagram(str1, alphabet=string.ascii_lowercase):
    # Create a set of the entire alphabet
    alphaset = set(alphabet)
    print(alphaset)
    # remove any spaces from the input string 
    str1 = str1.replace(' ', '')
    # Convert the input string into all lowercase
    str1 = str1.lower()
    print(str1)
    # Grab all unique letters from the string
    str1 = set(str1)
    # alphabet set == string set input
    return str1 == alphaset


def ispangram(str1, alphabet=string.ascii_lowercase):
    for char in alphabet:
        if char not in str1.lower():
            return False 
    return True
```