# `printf()`

> Variables are cool, but how to print them on the screen?

## Standard Input / Output

> \#include \<stdio.h> // std = STanDard, io = Input Output

A program communicates with the outside using standard input and standard output. The most common ways to input and output in C, are reading and writing to and from the console and files.

### Console Output

We can use the function `printf()` from `<stdio.h>` to print to the console, as shown in the Hello World example. According to [cppreference](https://en.cppreference.com/w/c/io/fprintf):

```c
int printf ( const char * format, ... );
```

The function returns the number of characters written.

### How to print some words

Example 1 :

Your code:

```c
printf("Hello World!");
```

Your screen:

```
Hello World!
```

Example 2  :

Your code:

```c
printf("Hello");
printf("Hi");// it will continue to print behind whatever you printed earlier
```

Your screen:

```
HelloHi
```

Your code:

```c
printf("Hello\n"); // '\n' is a special character that tells the screen
printf("Hi");      // to print on the next line, just like pressing ENTER when typing
```

Your screen:

```
Hello
Hi
```

## Format string

The first parameter is the **format string**. Ordinary characters can be directly printed, but the **`%` character followed by flag characters** is used to specify a substitute with a value when the string is printed. To specifically print out one `%` character, one must **escape** it using `"%%"`.

The remaining `...` means one or more parameters, specifically the value to be printed, ordered accordingly to the **specifiers** in the format string.

Below is a table for the commonly used ones:


| Specifier |          Explanation          |
| :-------: | :----------------------------: |
|   `%%`   |    Writes one `%` character    |
|   `%c`   |       Writes a character       |
|   `%d`   |       Writes an integer       |
|   `%x`   |  Writes an integer in base 16  |
|   `%f`   | Writes a floating point number |

The above table is very crude, so please refer to [cppreference](https://en.cppreference.com/w/c/io/fprintf)'s format section for the complete explanation.

The more parameters of after the format string will replace the specifiers when it is printed. They will be printed according to their order (The first parameter after the format string replaces the first specifier, ....)

The following is an example:

```c
printf("No specifiers.\n");
printf("%d specifier.\n", 1);
printf("%d specifiers for %c%c%c.\n", 4, 'i', 'n', 't');

//Console Output
/*
No specifiers.
1 specifier.
4 specifiers for int.
*/
```

You can also pass variables as the parameter, theur values will be printed.

```c
int a = 3;
printf("Writing an integer: %d", a); // Writing an integer: 3

printf("\n"); // '\n' means next line, just like pressing ENTER when typing

float b = 3.14f;
printf("Writing a float: %f\n", b); // Writing a float: 3.14

printf("printing a: %d and b: %f together in 1 line", a, b);
// printing a: 3 and b: 3.14 together in 1 line
```

> [classwork-03a](../homework/homework-3-introduce-yourself.md#level-1)
