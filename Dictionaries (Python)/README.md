## Dictionaries method in Python /(concept) 
### =>> _*.values(), .keys(), .items() methods in Dictionaries*_

##### Here is a brief snippets of code related to Dictionaries' concept in Python

```python

students_score = {"Alice": 85, "Bob": 92, "Charlie": 78}

for score in students_score:
    # print(score)
    print(f"key is {score}: and corresponding value is {students_score[score]}")
```

_Output :_
```bash
key is Alice: and corresponding value is 85
key is Bob: and corresponding value is 92
key is Charlie: and corresponding value is 78
```
### How to get dictionary values - 

#### _by using .values()_
```python 
students_score.values()
```
_Output:_
```bash
dict_values([85, 92, 78])
```

#### _by using .keys()_
 ```python
 students_score.keys()
 ```
 _Output:_
 ```bash
 dict_keys(['Alice', 'Bob', 'Charlie'])
 ```
 
 #### _by using .items()_
 ```python
 students_score.items()
 ```
 _Output:_
 ```bash
 dict_items([('Alice', 85), ('Bob', 92), ('Charlie', 78)])
 ```
 *returned in form of TUPLES*
 
 
 <br>
 

 # List Unpacking (concept) in Dictionaries
 ```python
 students_score = {"Alice": 85, "Bob": 92, "Charlie": 78}     #List UnPacking Concept

for key,value in students_score.items():
    # print(score)
    print(f"key is {key} and corresponding value is {value}")
    
  ````
  ```bash
key is Alice and corresponding value is 85
key is Bob and corresponding value is 92
key is Charlie and corresponding value is 78

```

<br> 

# Dictionary Comprehension  
_(to write a code in single line - to enhance efficiency + code readibility)_

```python
values : dict[int,int] = {x:x for x in range(5)}  #in case of list we give (key + value)
print(values)  # Output: {0: 0, 1: 1, 2: 2, 3: 3, 4: 4}
```
```bash
{0: 0, 1: 1, 2: 2, 3: 3, 4: 4}
```
_There is a "list function" ENUMERATE ==>> provide INDEX & the VALUE PRESENT ON THAT INDEX_

```python
fruits : list [str] = ["apple", "banana", "orange"]
#fruits_dict : dict [int,str] = {i:fruit for i, fruit in enumerate(fruits)}
#print (fruits_dict)

print("")

for i, fruit in enumerate(fruits):
    print(f"Index: {i}, Fruit: {fruit}")
```

```bash


Index: 0, Fruit: apple
Index: 1, Fruit: banana
Index: 2, Fruit: orange
```

<br>

# Topic =>> **Functions**


_Functions_

```python
#simple function to greet

# Defining the function (part 1)
def greet():                             # DEFINE the function
    print("Hello, world!")


# Invokation/Calling   (part 2)
greet()                                  # CALL the function

greet()


greet()


#In Python 1st define ==>  then CALL the function 2nd




def add():
  #pass
  x = 4                   # but this is HARD CODED forn
  y=4
  print(x+y)

add()

def add2(x,y):      #  ==>  these x & y are PARAMETERS
  result = x+y
  return result

add2(2,3)     # ==>  these 2 & 3 are ARGUMENTS
```

_Output:_
```bash
Hello, world!
Hello, world!
Hello, world!
8
5
```

#### There is another usecase for "return" keyword
### to stop code execution ->> use "return"

```python
# Return multiple values

def return_multiple_values():
    value1 = 10
    value2 = "Hello"
    value3 = [1, 2, 3]
    return value1, value2, value3          # like we made tuple  using   my_tup = 1, 2, 3

result = return_multiple_values()
print(result)
```

_Output:_
```bash
(10, 'Hello', [1, 2, 3])
```

```python
def subtraction (x,y):
  return x-y

print (subtraction(4,2))            #positional arguments



def full_name (first_name, last_name):
  print(f"{first_name} {last_name}")

full_name("Faizan", "Shah")

full_name("Shah", "Faizan")       # the positional argument will asign to corresponding parameter
```
_Output_
```bash
2
Faizan Shah
Shah Faizan
```





