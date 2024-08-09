[Back to Main](index.html) | [Previous Page](08_array_string.html)

# Functions

> Wrap a block of code with a name so we don't need to write the same thing many times

## Functions

A function is a collection of commands that perform tasks. `printf()` and `scanf()` are examples of functions. Functions provide **abstraction**, i.e. providing a simpler interface to hide complex implementations. We have already defined one before, it is `main()`, the entry point to our program. Functions perform different tasks and may even return values.

### Function Declaration

Being like variables, functions can only be accessed after the compiler knows about it, reading from the top. So to use a function in `main()` For example, it either has to be defined above, or declared above and defined elsewhere.

If a function is declared before, then the compiler knows about its existence and expects it to be defined sometime in the future as it reads from file to file. The definition can be in any place in any file, as long as it is in some place the compiler expects.

If the function is declared, and used, but not defined, then the compiler will generate a `reference to function not found` error.

The declaration/prototype is like so (note the semicolon at the end):
```
<return_type> <function_name>(<parameters...>);
```

In `<parameters...>`, each parameter can be simply `<data_type>` without a parameter name, since they are not used immediately, though leaving a name may provide more details to how the function can be used.

If your function does not take any parameters (i.e. `<parameters>` is empty), you can type in `void` or leave it as it is.

Here is an example:

```c
// this function accepts zero parameters
int get_current_time(void);

/**
 * The major difference is:
 * without putting void in the parentheses means this function has any number of parameters.
 * That means you pass any parameter into the function, but you cannnot access it.
 * 
 * However, in C++, there are no differences.
 */
int get_current_time2();

// this function accepts two integers
int addition(int a, int b);

//note that without the name, it is also fine
int addition(double, double);

// "void" return type means this function doesn't return anything
void robot_move(int pos_x, int pos_y, int pos_z);

/**
 * You can also pass a function as a parameter.
 * The declaration below accepts a function called "operation".
 * The details will be taught in the advanced reading.
 */
int calculator(int a, int b, int (*operation)(int, int));
```

> **Example of `void` parentheses and empty parentheses**:
>
> ```c
> #include <stdio.h>
>
> int test_funcs(void) {
>     return 2;
> }
>
> int test_funcs2() {
>     return 1;
> }
> int main() {
>     printf("test_funcs: %d\n", test_funcs());
>     printf("test_funcs2: %d\n", test_funcs2(0, 1, 2));
>     return 0;
> }
> ```
>
> <img src="https://i.imgur.com/RrAlq2F.png" alt="" data-size="original">
>
> Although the compiler throws a warning, the program works. However, if you change add extra arguments to `test_funcs`:
>
> ```c
> printf("test_funcs: %d\n", test_funcs(0, 1, 2));
> ```
>
> <img src="https://i.imgur.com/Eh1BNfZ.png" alt="" data-size="original">
>
> The program cannot be compiled successfully. For more details about empty parentheses, read [**this**](https://wiki.sei.cmu.edu/confluence/display/c/DCL20-C.+Explicitly+specify+void+when+a+function+accepts+no+arguments).

### Function Definition

Functions can be used by simply defining one. A declaration is not compulsory.

The most commonly used function definition syntax is as follows:

```c
<return_type> <function_name>(<parameters...>) {
    // your code
}
```

In `<parameters...>`, parameters are separated by a `,` (comma operator). Each parameter consist of `<type_specifier> <parameter_name>`. The type specifier specifies the type of parameter the function accepts, and the parameter name is some arbitrary name, used and only meaningful inside the function.

For example:

```c
int square(int x) {
    return x*x;
}

int addition(int a, int b) {
    const int sum = a + b; // by adding const before the type, the value of the variable is constant
    printf("%d + %d = %d", a, b, sum); // you can call other functions inside a function too!
    return sum; //return the result
}

int calculator(int a, int b, int (*operation)(int, int)) {
    // we can treat "operation" as a function (will be covered in advanced reading):
    return operation(a, b);
}
```

Then we can call it by `square(3)` For example, it would return `9` at the calling place.

### Function Call

A function call takes form of: `<function_name>(<parameters...>)`

A C function call/invocation is the same as those of mathematical functions, for which they accept parameters as inputs and return an output as a response, although C functions can also perform simple actions without any response. The parameters provided to a function call can be variables or literals, just anything that carries a value.

For example:

```c
#include <stdio.h>

int power(int a, int b) { //calculates a to the power of b, note that C does not have a**b (for evaluating powers) as in python
    int p = 1;
    for(int i=0; i<b; i++){
        p *= a;
    }
    return p; //return the result
}

int main(){
    printf("1 + 2 = %d\t", power(3, 4)); //prints 3^4 = 81 
    return 0;
}
```

[Continue to The Next Page](10_recursion.html)