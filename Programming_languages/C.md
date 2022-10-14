# C
[Readme](../README.md)

- [C](#c)
	- [C program structure](#c-program-structure)
	- [Naming Conventions](#naming-conventions)
	- [Data types](#data-types)
		- [Operators](#operators)
			- [Normal operators](#normal-operators)
			- [Bytes operators](#bytes-operators)
		- [Examples](#examples)
	- [Boilerplates](#boilerplates)
		- [Strings](#strings)
			- [String format](#string-format)
		- [Switch](#switch)
		- [Enum](#enum)
		- [Pointers](#pointers)
		- [Structs](#structs)
		- [UART for STM32 cube](#uart-for-stm32-cube)
			- [Private includes](#private-includes)
			- [Private define](#private-define)
			- [Private variables](#private-variables)
			- [Private function prototypes](#private-function-prototypes)

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
| Constant            | ALL_CAPS          |
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
| float     | ```float```   | 4 Bytes |

### Operators
#### Normal operators

| Operator                                            | Notation   | example                 |
| --------------------------------------------------- | ---------- | ----------------------- |
| Addition                                            | ```+```    | ```i+y``` <br>```7+6``` |
| Substraction                                        | ```-```    | ```i-y``` <br>```7-6``` |
| Multiplication                                      | ```*```    | ```i*y``` <br>```7*6``` |
| Division                                            | ```/```    | ```i/y``` <br>```7/6``` |
| remainder                                           | ```%```    | ```i%y``` <br>```7%6``` |
| Increment (after operation) <br> (before operation) | ```++```   | ```i++``` <br>```++i``` |
| Decrement (after operation) <br> (before operation) | ```--```   | ```i--``` <br>```--i``` |
|                                                     |
| Not                                                 | ```!```    | ```7 !< 0```            |
| AND                                                 | ```&&```   | ```1 && O```            |
| OR                                                  | ```\|\|``` | ```1\|\| O```           |

#### Bytes operators

| Operator    | Notation |
| ----------- | :------: |
| and         | ```&```  |
| or          | ```\|``` |
| not         | ```^```  |
| xor         | ```~```  |
| shift left  | ```<<``` |
| shift right | ```>>``` |

### Examples
```C
char text[101];
sprintf(text, "string data")
float voltage = 0.0;
```

## Boilerplates

### Strings
- Use code to be able to print it over usart

```C
/* USER CODE BEGIN 0 */
#ifdef __GNUC__
  /* With GCC/RAISONANCE, small printf (option LD Linker->Libraries->Small printf
     set to 'Yes') calls __io_putchar() */
  #define PUTCHAR_PROTOTYPE int __io_putchar(int ch)
#else
  #define PUTCHAR_PROTOTYPE int fputc(int ch, FILE *f)
#endif /* __GNUC__ */
/**
  * @brief  Retargets the C library printf function to the USART.
  * @param  None
  * @retval None
  */
PUTCHAR_PROTOTYPE
{
  /* Place your implementation of fputc here */
  /* e.g. write a character to the EVAL_COM1 and Loop until the end of transmission */
  HAL_UART_Transmit(&huart2, (uint8_t *)&ch, 1, 0xFFFF);

  return ch;
}
/* USER CODE END 0 */
```

- example

```C
sprintf(string, "Count is %d \n\r", count);
printf(string);
```

- Text to number

```c
atio() 
```
#### String format

| Datatype | Notation |
| -------- | :------: |
| Digit    | ```%d``` |
| Float    | ```%f``` |
| String   | ```%s``` |
| Pointer  | ```%x``` |


### Switch

```c
switch (<expression>) {
	case <const-expression-1>:
		<statement>
		break;
	case <const-expression-2>:
		<statement>
		break;
	case <const-expression-3>: // here we combine case 3 and 4
	case <const-expression-4>:
		<statement>
		break;
	default: // optional
		<statement>
```
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

| What                               | Code                                              | Example                                                                                    |
| ---------------------------------- | :------------------------------------------------ | :----------------------------------------------------------------------------------------- |
| Make new pointer                   | ```data_type * pointer_name;```                   | ```int * pointer_name;```                                                                  |
| Create pointer and normal variable | ```data_type* pointer_var, var;```                | ```int* pointer_var, var_name;``` <br> ```var_name=5;```<br>```pointer_var = &var_name;``` |
| Get pointer of varriable           | ```&var_name```                                   | ```int * pointer_name = &var_name;```                                                      |
| Get value behind pointer           | ```*pointer_name```                               | ```int var_name = *pointer_name;```                                                        |
| Ask for pointer as argument        | ```return_type function_name(Person * pPerson)``` | ```void print_person(Person * pPerson);```                                                 |


### Structs
> A struct is a combination of objects
- Header file

```c
//defining
#if !defined(PERSON_DEFINED)
	#defined PERSON_DEFINED
	typedef struct
	{
		char firstname[50];
		char lastname[50];
		float height;
	}Person;
#endif
```
- C file
```c
#include "Person.h"
int main(void)
{
	Person me;
	sprintf( me.lastname, "Amerlinck");
	sprintf( me.firstname, "Jarne");
	me.height= 1.86;

```	

### Functions
- Define  function

```c
return_type function_name(data_type-parameters);
```
- Make function

```c
return_type function_name(data_type-parameters){
    //code
}

```
- example


```c
int add(int a, int b);
int add(int a, int b){
    return a+b;
}

```

### UART for STM32 cube

The code below needs to be used with STM32 Cube MX generated code for UART2.

#### Private includes
> /\* USER CODE BEGIN Includes \*/

```C
#include <stdio.h>
```

#### Private define

> /\* USER CODE BEGIN PD \*/

```C
#ifdef __GNUC__
  /* With GCC/RAISONANCE, small printf (option LD Linker->Libraries->Small printf
     set to 'Yes') calls __io_putchar() */
  #define PUTCHAR_PROTOTYPE int __io_putchar(int ch)
#else
  #define PUTCHAR_PROTOTYPE int fputc(int ch, FILE *f)
#endif /* __GNUC__ */
```

#### Private variables

> /\* USER CODE BEGIN PV \*/

```C
char string[101];
```

#### Private function prototypes

> /\* USER CODE BEGIN PFP \*/

```C
/**
  * @brief  Retargets the C library printf function to the USART.
  * @param  None
  * @retval None
  */
PUTCHAR_PROTOTYPE
{
  /* Place your implementation of fputc here */
  /* e.g. write a character to the EVAL_COM1 and Loop until the end of transmission */
  HAL_UART_Transmit(&huart2, (uint8_t *)&ch, 1, 0xFFFF);

  return ch;
}
```

- Example print ([This is also needed](#strings))

```C
sprintf(string, "Count is %d \n\r", count);
printf(string);
```
