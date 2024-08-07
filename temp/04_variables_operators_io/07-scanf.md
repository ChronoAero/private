# Scanf

> How to ask user to input something

### Console Input

The function `int scanf(const char*, ...)` reads input from the console and stores it in the given variables. To read variables, specify the data type token and provide the address to the variable. The syntax for `scanf` is similar to `printf`, but an **ampersand** (`&`) is required before the variable name.

```c=
#include <stdio.h>

int main() {
    int user_input = 0;
    // enter an integer and press enter
    scanf("%d", &user_input); // your program will be stop here until enter is pressed
    printf("retrieved value: %d", user_input);
  
    return 0;
}
```

* `int scanf(const char *format, ...)`
  * `const char *format` is a _pointer_ to a **const**ant **char**acter. For now, don't worry about what a pointer is. You can think of the parameter as requiring a piece of text. For example: `"Danny"`, `"%d"`.
  * `...` refers to the variables for storing the information. Due to the nature of C (and because of pointers), you should add `&` in front of your variables. For example: `&GPA`.
    * You can pass any number of variables to receive information.
    * e.g. `scanf("%d %c %s", &int_input, &char_input, &str_input);` accepts "123 a haha" and results in `int_input = 123`, `char_input = 'a'`, `str_input = "haha"`.
    * Documentation: [scanf](https://www.cplusplus.com/reference/cstdio/scanf/)

> **Q**: What is the use of `&`?
>
> **A**: A variable consists of a name, value and address. `&` returns the address of the variable. This topic (pointers) will be taught in depth in later advanced notes which will not be covered in this tutorial.

> [classwork-03b](../homework/homework-3-introduce-yourself.md#level-2)
