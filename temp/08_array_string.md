<script type="text/x-mathjax-config"> MathJax.Hub.Config({ tex2jax: { skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'], inlineMath: [['$','$']] } }); </script> <script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

[Back to Main](index.html) | [Previous Page](07_control_flow.html)


# Array and String

> Array are just many boxes put together in a line.

> There are some topics that are less important, they will be marked with `*` in the title. But we may need a slight understanding of it for the next parts.

## Arrays

Variables are nice, but what if we need to store a hundred integers?

```c
int var_0;
int var_1;
int var_2;
int var_3;
.
.
.
int var_99;
```

Although this method is possible, it is not efficient or feasible. Hence, we use **Array**.

An array is another type of variable. It is a container for multiple values of the same type. Arrays carry type information and can only carry one type of value in one array. Think of arrays as cabinets, and each value belongs in one drawer in a cabinet.

An array must have a **constant length**, specified either at declaration or interpreted at initialization.

Refer to [cppreference](https://en.cppreference.com/w/c/language/array) for more details.

### Array Declaration

The following is the syntax for declaration 
```
<element_type> <array_name>[<size (optional for the first number)>];
```

The `[]` (square brackets) specifies an array.

The following is an example of declaring a float array with length 10;

```c
float numbers[10];
```

### Array Initialization

An array can be initialized alongside a declaration with values, by using the initializer expression, like so:

```c
int natural_numbers[20] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}; //remaining spaces are filled with 0s
```

If you initialize using the initializer expression, you are not required to specify the array length. It will count the number of elements and set the length as that (the minimum size possible)

```c
int natural_numbers[] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}; //will be an array of size 10 instead
```

Uninitialized arrays in functions store **garbage values** as initial values. If you want to initialize them as all `0`s do the following:

```c
int garbage[20]; //everything inside will be garbage value
int blank[20] = {}; //everything will be 0 filled
```

**Arrays cannot be re-assigned**, so you cannot use the initializer expression after the declaration statement, nor assign them to another array variable.

### Array Access

Array items do not have a name we can call, but they are arranged in an orderly fashion within an array. We can access items using an **index**. 

We count from `0` in programming, so we can call, e.g. the 0th item in array x. The index can be a variable containing an integer, or simply an integer literal. The following is the syntax of array access: 

```
<array_name>[<index>]
```

For example:

```c
int numbers[10]; //numbers = {3, <garbage>, <garbage>, ...}
numbers[0] = 3; //accessing to modify the value inside
int y = numbers[0]; //accessing to get the value; y is 3 now
```

> Please be aware about **Boundary Issue**: **Accessing an array out of bounds** (negative or any number $\geq \textsf{size}$ ) is **undefined behavior**, it may or may not generate error when accessed. ([Read more](https://www.geeksforgeeks.org/accessing-array-bounds-ccpp/)). Accessing outside of program memory will produce a "SIGSEGV Signal Segmentation Fault" runtime error.

Arrays are usually used for loops, to iterate over the length of the array for data manipulation.

This example populates the array with natural numbers:

```c
int n[100];

for (int i = 0; i < 100; i++) {
    n[i] = i+1;
}

//now n will be {1, 2, 3, 4, ..., 99, 100};
```

Another example, this program will find the mean (average value) of the values in an array.

```c
int data[10] = {1, 4, 5, 6, 3, 2, 4, 3, 2, 7};

int sum = 0;
for(int i=0; i<10; i++){
    sum += data[i];
}

double mean = sum/10.0; //please refer to the section about casting
printf("%.3f", mean); //prints 3.700, note %.3f is used instead of %d
```

### Multidimensional Arrays

Arrays can have multiple dimensions. The arrays we have explored above are called 1D arrays.

To declare arrays with additional dimensions, just do as follows:

```c
int map[5][10];
```

The above declares a $5 \times 10$ array.

To access a cell, it can be done as:

```
map[<index>][<index>]
```

Alternatively, you can consider multidimensional arrays as matrices. For example:

```c
int map[4][3];
map[0][0] = 1;
map[0][1] = 5;
map[0][2] = 2;
map[1][0] = 3;
map[1][1] = 4;
map[1][2] = 9;
map[2][0] = 7;
map[2][1] = 6;
map[2][2] = 4;
map[3][0] = 5;
map[3][1] = 5;
map[3][2] = 3;
```

You can also initialize it as the following:
```c
int map[4][3] = {
    {1, 5, 2},
    {3, 4, 9},
    {7, 6, 4},
    {5, 5, 3}
};
```

`map[4][3]` can be written in the matrix as below:

$$\textsf{map} = \begin{bmatrix}  1& 5 & 2 \\ 3 & 4 & 9 \\ 7 & 6 & 4 \\ 5 & 5 & 3\end{bmatrix}$$

When accessing the variable, think about like this:

Let's assume that we want to access `map[2][1]`, we see it like this:
```
{
    {1, 5, 2}, //0
    {3, 4, 9}, //1
    {7, 6, 4}, //2
    {5, 5, 3}  //3
}
```
We want to take the item at index `2`:
```
{7, 6, 4}
```
And then we proceed to take the item at index `1`, which is `6`

## String (Character Array)

> `"Hello World\n"` re-explored.

### Character Array

You may not realize, but we actually have used array in our `Hello World` program.

In C, there is no built-in `string` type. As an alternative, we use **character arrays** to represent a string:

```c
char name[] = "Danny";
```

Although the length of `Danny` is `5`, there is an invisible character `'\0'` at the end, which C uses to indicate the end of the character array. Hence, the size of `name` array is actually `6`.

Basically this is the same as:

```c
char name[] = {'D', 'a', 'n', 'n', 'y', '\0'}; //size is determined by compiler, which is the minimum possible: 6
```

Note that in the case, you need to explicitly write `\0`

This `\0` (null character) is needed for C to be able to print it properly (The print will stop upon finding this `\0` character).

```c
//this is a slightly more tedious way of printing "Danny"
int i = 0;
char name[] = "Danny";
while (name[i] != '\0') {
    // remember that i++ is post-increment,
    // that means it returns the original value of i,
    // before adding 1 to i
    printf("%c", day[i++]);
}

printf("\n");
```

### `printf` and `scanf` for Strings

There is a placeholder in format string for strings: `%s`

To receive the input of a string, you can use:

```c
char input[100]; //make a sufficiently big array
scanf("%s", input); //no need for the &, an array actually stores the address (more about it in advanced materials)
```
This method will take all characters until it detects a whitespace or newline. For example if you input `This is a loong string`, the array `input` will only contain `This`. It also automatically store your input with `\0` at the end.


```c
char hello[] = "Hello World!";
printf("My first program in C prints %s :)", hello);
```

It will print `My first program in C prints Hello World! :)` (null character is removed upon insertion to the format string)


## The `<string.h>` Library*

There is also a library that can help you in working with strings. You can use `#include <string.h>` to add it to your workspace.

### `strlen()`: Counts how long a string is (excluding null char)
```c
char name[] = "Danny";
int len = strlen(name);
printf("len: %d\n", len); //prints 5

//Under the hood, it works by counting the amount of characters before \0
char hello[] = {'H', 'e', 'l', 'l', 'o', '\0', 'w', 'o', 'r', 'l', 'd'};
len = strlen(hello);
printf("len: %d\n", len); //prints 5
printf(hello); //prints "Hello" only
```

### `strcpy()`: Copies all the contents of the second tring to the first one

```c
char from[] = "Danny";
char to[6]; //note that it must have sufficient size; more is fine but less may lead to errors

strcpy(to, from);
printf(to); //prints Danny

strcpy(to, "Robot"); //from can be literal string
printf(to); //prints Robot
```

### `strcmp()`: Compares the string. If they have the same length and content, it will evaluate to `0`. Otherwise, any non-zero number.

```c
char str1[] = "Hello";
char str2[] = "Hello";

int cmp = strcmp(str1, str2); 
printf("cmp: %d\n", cmp); //prints 0

strcpy(str2, "Robot"); //make str2 = Robot (use strcpy instead of assignment)
cmp = strcmp(str1, str2);
printf("cmp: %d\n", cmp); //prints -10 (non-zero)

char str3[6] = "Hello "; //notice the whitespace
cmp = strcmp(str1, str3);
printf("cmp: %d\n", cmp); //prints -32 (non-zero)
```

## Self-Test (For Concept Checking)

[I will add count mode and median here]

[Make an exercise for string here too]

[Make a matrix question here (yeah, let's do 2x2 eigenvalues)]

[Continue to The Next Page](09_struct.html)
