# C
[Readme](../README.md)

- [C](#c)
	- [C program structure](#c-program-structure)
	- [Naming Conventions](#naming-conventions)
	- [Data types](#data-types)
		- [Examples](#examples)
		- [Bytes](#bytes)
	- [Boilerplates](#boilerplates)
		- [Enum](#enum)
		- [Pointers](#pointers)
		- [Structs](#structs)

## C program structure

```C
pre-processor directives
global declarations

main()
{
    local variable deceleration
    statement sequences
    function invoking
}

```
## Naming Conventions
| Type                | Naming convention |
| ------------------- | ----------------- |
| Functions           | lower_case        |
| Local variable      | firstName         |
| Constant            | ALL_CAPS         |
| Structs and typedef | CamelCase         |
| Pointers            | CamelCase         |

## Data types

> signed is with +- unsigned is without

| Data Type | C µC          | Length  |
| --------- | :------------ | :------ |
| bool      | ```bool```    | 1 bit   |
| char      | ```int8_t```  | 2 bytes |
| short     | ```int16_t``` | 4 bytes |
| int       | ```int32_t``` | 8 bytes |
| float     | ```float```   |         |

### Examples
```C
char text[101];
sprintf(text, "string data")
float voltage = 0.0;
```

### Bytes

| What        | Notation |
| ----------- | :------: |
| and         | ```&```  |
| or          | ```\|``` |
| not         | ```^```  |
| xor         | ```~```  |
| shift left  | ```<<``` |
| shift right | ```>>``` |



## Boilerplates
### Enum

```c
enum States {
	idle=0,
	white,
	red1,
	red2

};
```
### Pointers
> a pointer is a start address for data. The type sets the size of data.

| What                               | Code                                       | Example                                                                                    |
| ---------------------------------- | :----------------------------------------- | :----------------------------------------------------------------------------------------- |
| Make new pointer                   | ```data_type * pointer_name;```            | ```int * pointer_name;```                                                                  |
| Create pointer and normal variable | ```data_type* pointer_var, var;```         | ```int* pointer_var, var_name;``` <br> ```var_name=5;```<br>```pointer_var = &var_name;``` |
| Get pointer of varriable           | ```&var_name```                            | ```int * pointer_name = &var_name;```                                                      |
| Get value behind pointer           | ```*pointer_name```                        | ```int var_name = *pointer_name;```                                                        |
| Ask for pointer as argument        | ```void function_name(Person * pPerson)``` | ```function_name;```                                                                       |


### Structs
> A struct is a combination of objects
- Header file

```c
//defining
#if !defined(PERSOON_DEFINED)
	#defined PERSOON_DEFINED
	typedef struct
	{
		char voornaam[50];
		char achternaam[50];
		float gewicht;
	}Persoon;
#endif
```
- C file
```c
#include "Person.h"
int main(void)
{
	Person me;
	sprintf( me.lastname, "Amerlinck");
	sprintf( me.name, "Jarne");
	me.hight= 1.86;

```	

### Functions

```c
return_type function_name(data_type-parameters){
    //code
}
//  Example of function to add two numbers

int add(int a, int b){
    return a+b;
}

```





```C



char text[101];





input maken
//via datasheets

# sout
sprintf(var, "formatted stuff", vars);

# AD-Converter
R15 is voor kortsluiting

# Pointers


ask pointer as var      void functionsName(Person * pPerson)
give pointer            &var



# Struct
//defining
#if !defined(PERSOON_DEFINED)
	#defined PERSOON_DEFINED
	typedef struct
	{
		char voornaam[50];
		char achternaam[50];
		float gewicht;
	}Persoon;
#endif

Persoon ik;
ik.gewicht;
PersoonPrinter(&ik);
// gebruik van pointers voor efficientie
void PersoonPrinter(Persoon * pPerson){// * is voor de pointer
    pPerson->voornaam
}


# Timers
    hardmatige timer (flipflop)
    automatisch tellen
    zonder tussenkomst CPU

    Ook via interupts
# enum
//de =0 moet er zelf niet staan
enum States {
	idle=0,
	white,
	red1,
	red2

};

# Wifi module
van text to getal		atio() 
```