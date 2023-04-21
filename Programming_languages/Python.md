---
topic: Python
type: language
site: https://www.python.org/
status: core
included_topics: 
 - ML
 - frontend
 - CI/CD
history:
  found: 2021/04/21
  tried: 2021/04/21
  used: 2021/04/21
  core: 2023/04/21
  hold: 
os:
  - linux
  - windows
  - mac
---

# Python
[Readme](../README.md)

- [Python](#python)
  - [Information](#information)
    - [Naming Conventions](#naming-conventions)
  - [Data Type](#data-type)
  - [Default Commands](#default-commands)
    - [Operators](#operators)
      - [Math](#math)
      - [Comparison](#comparison)
      - [Bool](#bool)
    - [Strings](#strings)
      - [Normal](#normal)
      - [String Formats](#string-formats)
    - [Lists](#lists)
      - [Index](#index)
      - [Commands](#commands)
    - [Functions and Classes](#functions-and-classes)
      - [Lambdas](#lambdas)
    - [Loops](#loops)
    - [Libraries](#libraries)

## Information
- No need for ; at the end of the line
### Naming Conventions

| Type                       | Public             | Internal            |
| :------------------------- | :----------------- | :------------------ |
| Packages                   | lower_with_under   |                     |
| Modules                    | lower_with_under   | _lower_with_under   |
| Classes                    | CapWords           | _CapWords           |
| Exceptions                 | CapWords           |                     |
| Functions                  | lower_with_under() | _lower_with_under() |
| Global/Class Constants     | CAPS_WITH_UNDER    | _CAPS_WITH_UNDER    |
| Global/Class Variables     | lower_with_under   | _lower_with_under   |
| Instance Variables         | lower_with_under   | _lower_with_under   |
| Method Names               | lower_with_under() | _lower_with_under() |
| Function/Method Parameters | lower_with_under   |                     |
| Local Variables            | lower_with_under   |                     |

## Data Type

| Data Type | Example                                        | Extra info       |
| --------- | :--------------------------------------------- | ---------------- |
| str       | ```"text"  ```                                 |                  |
| int       | ```2  ```                                      |                  |
| float     | ```2.3 ```                                     |                  |
| complex   | ```3 +4j ```                                   |                  |
|           |
| list      | ```["apple", "banana", "cherry"] ```           |                  |
| tuple     | ```("apple", "banana", "cherry")  ```          |                  |
| range     | ```range(6)   ```                              |                  |
| dict      | ```{"name" : "John", "age" : 36} ```           |                  |
| set       | ```{"apple", "banana", "cherry"} ```           |                  |
| frozenset | ```frozenset({"apple", "banana", "cherry"})``` | unchangeable set |
|           |
| bool      | ```True  ```                                   |                  |
| bytes     | ```b"Hello" ```                                |                  |
| NoneType  | ```None```                                     |                  |

## Default Commands
### Operators
#### Math

| What                            | Notation |
| ------------------------------- | :------: |
| Exponent                        |    **    |
| Modulus/Remainder               |    %     |
| Integer division (no remainder) |    //    |
| Division                        |    /     |
| Multiplication                  |    *     |
| Subtraction                     |    -     |
| Addition                        |    +     |

#### Comparison

| What                     | Notation |
| ------------------------ | :------: |
| Equal to                 |    ==    |
| Not equal to             |    !=    |
| Not equal to alternative |    <>    |
| Less than                |    <     |
| Greater Than             |    >     |
| Less than or Equal to    |    <=    |
| Greater than or Equal to |    >=    |

#### Bool

| What      | Notation |
| --------- | :------: |
| Not       |   not    |
| Inversion |    !     |
| Or        |    or    |
| And       |   and    |


### Strings
#### Normal
i=  2

| What        | Code                                                                                      | Result                                 | Result Type |
| ----------- | :---------------------------------------------------------------------------------------- | :------------------------------------- | :---------- |
| Concatinate | ```"str 1" + "str 2"    ```                                                               | "str 1str2"                            | str         |
| Repeat      | ```"str 1" *3   ```                                                                       | "str 1str 1str 1"                      | str         |
| slicing     | ```"str_1"[i]``` <br> ```"str 1"[-1]``` <br> ```"str 1"[1:3]``` <br> ```"str 1"[::-1] ``` | "r"   <br> "1" <br> "tr_" <br> "1 rts" | str         |
| Membership  | ```"r" in "string1" ```                                                                   | true                                   | bool        |
| All upper   | ```"str 1".upper() ```                                                                    | "STR 1"                                | str         |
| All lower   | ```"STR 1".lower() ```                                                                    | "str 1"                                | str         |
| First upper | ```"STR 1".capitalize()  ```                                                              | "Str 1"                                | str         |
#### String Formats

| Type     | notation |
| -------- | :------: |
| decimal  |    %d    |
| str      |    %s    |
| float    |    %c    |
| Caracter |    %f    |


float = 347.12345678
digit = 24

| What                             | Code                          | Result                  | Result Type |
| -------------------------------- | :---------------------------- | :---------------------- | :---------: |
| no type format                   | ```f"other of {float}" ```    | "other of 347.12345678" |             |
| float x after digit              | ```f"other of {float:.f2}"``` | "other of 347.12"       |             |
| start with                       | ```f"_{digit:03d}_"  ```      | "_024_"                 |             |
| take x characters and fil before | ```f"_{digit:>4}_"  ```       | "_  24_"                |             |
| take x characters and fil center | ```f"_{digit:^4}_"  ```       | "_ 24 _"                |             |
| take x characters and fil after  | ```f"_{digit:<4}_"  ```       | "_24  _"                |             |
### Lists
#### Index
x is an int
a = [1, 2, 3, 4, 5]

| What     | Notation                          | Result                                    |
| -------- | :-------------------------------- | :---------------------------------------- |
| Index x  | ```a[0]```<br>```a[2]```          | 1  <br>3                                  |
| Index -x | ``` a[-1]``` <br>```a[-2]  ```    | 5  <br>4                                  |
| range    | ```a[1:3]   ```                   | [2, 3]                                    |
| skip     | ```a[::2]```  <br>  ```a[::-1]``` | ```[1, 3, 5]```<br> ```[5, 4, 3, 2, 1]``` |
#### Commands
- the example list has Child_type as type
- a = [2, 1, 3, 4, 5]
- index =2
- value = 3
  
| What               | Notation                                                                                              | Result                  | Result type |
| ------------------ | :---------------------------------------------------------------------------------------------------- | :---------------------- | :---------- |
| Indices            | ```a[index]  ```                                                                                      | 4                       | Child_type  |
| remove             | ```a.remove(index) ```                                                                                | None                    | None        |
| count              | ```a.count(value) ```                                                                                 | 1                       | int         |
| sort               | ```a.sort() ```                                                                                       | None                    | None        |
| sorted             | ```sorted(a)  ```                                                                                     | [1, 2, 3, 4, 5]         | list        |
| insert             | ```a.insert(index, item)     ```                                                                      | None                    | None        |
| pop                | ```a.pop() <br>a.pop(index)  ```                                                                      | 5 <br> 4                | Child_type  |
| List Comprehension | [EXPRESSION for ITEM in LIST \<if CONDITIONAL\>]  <br> ```[x**2 for x in range(10) if x % 2 == 0] ``` | <br> [0, 4, 16, 36, 64] | list        |

### Functions and Classes 
- Function
```python
# Full notation
def calculate_division(x: int, y: int) -> float:
  """A one-line summary
    divides x by y

    Parameters
    ----------
    x:  int
        x of point 1
    y:  int
        y of point 1
    
    Returns
    -------
    divides : float
        x/y
    Notes
    -----
     
    """
  return x/y


# Short no limits on params and return type
def calculate_division(x, y):
  return x/y
```
- Class
```python
# Full notation
class Example_class():
    """
    This class is used as an example
    ...

    Atributes
    ----------
    nr:  int
        number of hey
    class_var: str
        class string info

    Methods
    -------
    hey() -> string:
        returns  hey

    Examples
    -----
    >>> example = Example_class()
    >>> example.hey()
    """
    class_var = "hey"
    def __init__(self, nr: int):
        self._nr = nr
       

    def hey(self) -> str:
        """A one-line summary
        returns  hey
        Returns
        -------
        text: str
            returns hey

        """
        return "hey"
      
    @staticmethod
    def is_adult(age:int) -> bool:
		  """A one-line summary
        is a static methode so no need for an object
      Parameters
      ----------
      x:  int
        x of point 1
      Returns
      -------
      text: bool
          returns if age is adult

      """

      return "I am a static method"

    @classmethod
    def class_method(cls):
		  """A one-line summary
        is a class methode so no need for an object
      Returns
      -------
      text: str
          returns hey

      """
      return "hey"

    def __call__(self, inputs):
		  """Object as function
        so you can obj(inputs)
      Returns
      -------
      text: str
          returns hey

      """
      return "hey"
  
# Short no limits on params and return type
class Example_class(Super_class):
    class_var = "hey"
    def __init__(self, nr):
        self._nr = nr
       
    def hey(self):
        return "hey"
```
#### Lambdas
> Lambdas are functions as one liners

```python
lambda x:x+2
print(x(3)) # will print 5 as 3 +2 is 5

```
- Lambdas as arguments

```python

def function_name(lm):
  print(lm(3))

function_name(lambda x:x+2) # will print 5
```
- One liner

```python
[function_name(n, inputs) for n in array]
```
### Loops
- for loop
```python
# Full notation
list_of_items = [1, "2a", 3.4]
for item in list_of_items:
  print(item)
# 1
# 2a
# 3.4
```
- while loop
```python
# Full notation
list_of_items = [1, "2a", 3.4]
i = 0
while i < 5:
  print(i)
  i = i + 1
# 0
# 1
# 2
# 3
# 4
```
### [Libraries](Python_libraries.md#python-libraries)
