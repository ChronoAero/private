# Variables

> Boxes to store values.

Now, instead of the `Hello World` program before, consider the following:

```c
#include <stdio.h>

int main(){
    int a = 3; 
    a = a + 4;
    printf("%d", a);
}
```
You may guess what the program outputs or run it. Here, we would like to introduce the concept of variables in a program. (The output of the program will be `7`, we will explain why)

Variables are boxes to save some data. You can operate (e.g. add it up) and change the value inside the box.

## Primitive Data Types

We will explain about the first part of the first line: `int a = 3;`

In C, we have to tell the computer what type does the box store (i.e. how big the box is and what we will put inside it). `int` (integer) is one such type.

> Note: If you have programmed in language like Python before, unfortunately type is not dynamic in C. You need to explicitly state it (this is why C is fast).

We will first introduce some primitive data types (there are more, but less likely to be used):

<table>
<thead>
<tr>
    <th width="212" align="center">Type</th>
    <th width="276" align="center">Description</th>
    <th align="center">Example Literal</th>
</tr>
</thead>
<tbody>
    <tr>
        <td align="center"><code>char</code></td>
        <td align="center">8-bit integer* for storing an ASCII character</td>
        <td align="center"><code>'a'</code></td>
        </tr><tr>
        <td align="center"><code>int</code></td>
        <td align="center">16-bit/32-bit signed integer**</td>
        <td align="center"><code>1</code></td>
        </tr><tr>
        <td align="center"><code>float</code></td>
        <td align="center">32-bit, single-precision floating point value (i.e. dotted number)</td>
        <td align="center"><code>3.012f</code></td>
        </tr><tr>
        <td align="center"><code>double</code></td>
        <td align="center">64-bit, double-precision floating point value (i.e. a longer dotted number)</td>
        <td align="center"><code>5.012345</code></td>
    </tr>
</tbody>
</table>

* One bit is one `0` or `1` stored in the memory of the computer
* \*Whether `char` is signed or unsigned is machine-dependent.
* \*\*Size is compiler-dependent and machine-dependent.

Please pay attention to the syntax of the literal given on the last column.


<details>
* [Primitive Types](primitive-types.md) (char, int, float, double)
* [The Boolean Type](the-boolean-type.md) (bool)
* [Standard Integer Types](standard-integer-types.md) (uint8\_t, int64\_t, ...)
</details>


## How to Make a Variable?

We must tell the computer that we are about to use a variable with some name before we use it. This action is called a **declaration**. We can declare one with this syntax: `<type> <variable_name>;`.

We can only declare a variable with the same name once per scope (we'll talk about that later). For now, please avoid using the same name twice.

```c
int some_integer; // Declaring some_integer as a integer
char c; //Declaring c as a character
float f; //Declaring f as a 32-bit, single-precision floating point value
```

If you declare it in the such way. Your variable will usually contain random garbage value. You can change its value by doing something called assignment. You can do so only **after the declaration.** (You need to make the box before you modify the content).

The syntax for assignment is `<variable-name> = <new-value>;` 

```c
int some_integer;
char c;
float f;

some_integer = 3;
c = 'A';
f = 5.6f;
```

You can also use the following shorter syntax to assign a value directly after the declaration.

```c
int some_integer = 3;
char c = 'A';
f = 5.6f;
```

Note that the left hand side of an assignment operator must be a non-literal. Something like `2=3;` will not work

## Self Tests (For Concept Check)

Q1. Will the following code error?

```c
#include <stdio.h>
int main(){
    x = 7; //Should be similar to python right?
}
```
<details>
    <summary>Ans</summary>
    It will error, variable x is not declared before assigned to a value. Please pay attention to the difference between the declaration syntax and the assignment syntax.
</details>

Q2. What is wrong with the following code?
```c
#include <stdio.h>
int main(){
    char c = "A";
}
```
<details>
    <summary>Ans</summary>
    char literals must be quoted with single quote. Double quote has another use, we will explain that later.
</details>