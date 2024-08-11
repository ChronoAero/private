<script type="text/x-mathjax-config"> MathJax.Hub.Config({ tex2jax: { skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'], inlineMath: [['$','$']] } }); </script> <script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

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

### Function Definition and `return`

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

void print_addition(int a, int b) {
    const int sum = a + b; // by adding const before the type, the value of the variable is constant
    printf("%d + %d = %d", a, b, sum); // you can call other functions inside a function too!
    return; //return nothing
}
```

To call a function (run what is inside and set the parameters to some value), use the syntax:

```
<function_name>(<parameters>)
```

`return` means the value that will replace the function call after it is evaluated.

Then we can call it by `square(3)` for example, it would return `9`. It means that we put `9` at the calling place.

```c
printf("%d", square(3));
printf("%d", 9); //what it means by return x*x = return 3*3 = return 9
```

If a function has `void` as the `return_type`. It will return *nothingess* to the location. Hence we usually will not pass the value. However, the lines inside the function will still be run. Hence,

```c
printf("%d", print_additon(2,3));
printf("%d", <nothingness>); //compilation error
```

However:
```c
print_addition(2,3); //runs what is in the body:

//equivalent to:
const int sum = 2 + 3; // by adding const before the type, the value of the variable is constant
printf("%d + %d = %d", 2, 3, sum); // you can call other functions inside a function too!
```
Hence the code will output
```
2 + 3 = 5
```

More example:

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

## Self tests 
Q1. RPS Interview

One again, Ping faces a rock, paper, and scissor questions during his interview. Can you help him?

```c
#include <stdio.h>
#include <stdlib.h> //include random number generator from here, we will leave this for you to explore.

/*
There are three outcomes for the function of print_game_result: "DRAW!", "COMPUTER WINS!", or "PLAYER WINS!"

For print_choice, we need to:
To print out the choice picked by the computer or the user, if the choice is not in the range [0, 3) please return a non-zero number.

For print_game_result, we need to:
Tell whether the computer wins or the user wins

*/

// 0/1/2 is used to represent ROCK/PAPER/SCISSORS
const int ROCK = 0, PAPER = 1, SCISSORS = 2;
// Define the game functions here
int print_choice(char player, int choice);
void print_game_result(int computer_choice, int user_choice);

// TODO BEGIN



// TODO END

int main()
{
    int seed; // To seed the random number generator
    printf("Enter a seed for the game:\n");
    scanf("%d", &seed);
    srand(seed); // Initialize random number generator
    int computer_choice = rand()%3; // rand() produces an integer which is in the range [0, 3)
    int user_choice = rand()%3; // then converted to ROCK/PAPER/SCISSORS
    if (print_choice('C', computer_choice) != 0) return -1; // -1 signals an error to the int main()
    if (print_choice('U', user_choice) != 0) return -1; // -1 signals an error to the int main()
    print_game_result(computer_choice, user_choice);
    return 0;
}
```

Implement the functions `print_choice` and `print_game_result` as stated in the comments above. Such that, for example, given the following input as the randomness seed:
```
2218
```
Output:
```
Enter a seed for the game:
C chooses: rock
U chooses: paper
PLAYER WINS!
```
Input:
```
2219
```
Output:
```
Enter a seed for the game:
C chooses: rock
U chooses: scissors
COMPUTER WINS!
```
Input:
```
2220
```
Output:
```
Enter a seed for the game:
C chooses: paper
U chooses: paper
DRAW!
```


<details>

```c
#include <stdio.h>
#include <stdlib.h> //include random number generator from here, we will leave this for you to explore.

/*
There are three outcomes for the function of print_game_result: "DRAW!", "COMPUTER WINS!", or "PLAYER WINS!"

For print_choice, we need to:
To print out the choice picked by the computer or the user, if the choice is not in the range [0, 3) please return a non-zero number.

For print_game_result, we need to:
Tell whether the computer wins or the user wins

*/

// 0/1/2 is used to represent ROCK/PAPER/SCISSORS
const int ROCK = 0, PAPER = 1, SCISSORS = 2;
// Define the game functions here
int print_choice(char player, int choice);
void print_game_result(int computer_choice, int user_choice);

// TODO BEGIN

int print_choice(char player, int choice){
    if(choice<0 || choice>=3) { return -1; } 
    printf("%c chooses: %s\n", player, choice==ROCK? "rock" : (choice==PAPER ? "paper" : "scissors") );
    return 0;
}

void print_game_result(int computer_choice, int user_choice){
    if(computer_choice == user_choice){
        printf("DRAW!"); return;
    }
    if( (computer_choice == 0 && user_choice == 2) || (computer_choice==1 && user_choice == 0) || (computer_choice==2 && user_choice == 1)){
        printf("COMPUTER WINS!"); return;
    }
    printf("PLAYER WINS!"); return;
}


//TODO END

int main()
{
    int seed; // To seed the random number generator
    printf("Enter a seed for the game:\n");
    scanf("%d", &seed);
    srand(seed); // Initialize random number generator
    int computer_choice = rand()%3; // rand() produces an integer which is in the range [0, 3)
    int user_choice = rand()%3; // then converted to ROCK/PAPER/SCISSORS
    if (print_choice('C', computer_choice) != 0) return -1; // -1 signals an error to the int main()
    if (print_choice('U', user_choice) != 0) return -1; // -1 signals an error to the int main()
    print_game_result(computer_choice, user_choice);
    return 0;
}
```

<summary>Ans</summary>

</details>

Q2. Calculate $e^x$ in C

Earlier, we implemented the function for computing a number to the power of another, i.e. $\textsf{power}(a,b) = a^b$. However our method only works for integer $b$. We cannot really compute $2^{1.414}$ this way.

Let's generalize this with some calculus knowledge. It is possible to compute $e^{x}$ by an infinte sum.

$$e^x = \lim_{N \to \infty} \sum_{i=0}^N \frac{x^i}{i!}=1+x+\frac{x^2}{2!}+\frac{x^3}{3!}+...=\sum_{i=0}^N \frac{x^i}{i!}=1+x+\frac{x^2}{2}+\frac{x^3}{6}+...$$

Note that $n!$ is the factorial, the product of the numbers in range $[1,n]$. For example $6! = 6 \cdot 5 \cdot 4 \cdot 3 \cdot 2 \cdot 1 =720$

Note that we can use $a^b = e^{(b\ln(a))}$.

Assume that we only consider the first $50$ term, i.e. $N=50$. Implement a code to show:

$e = 2.7182...$

$e^{2.111}= 8.2564...$

$2^{1.414} = 2.6647...$ given that $\ln(2) = 0.6931472$

To make things easier for you, try to implement $\textsf{pow}(a,b)$ to power `double` to `int` and $\textsf{factorial}(n)$ to compute $n!$ (please return a `double` for more precision) first.

<details>
One of such possible answer is the following (note that the solution prints the number in 5 decimal places, just check the first 4)

```c
#include <stdio.h>

double pow(double a, int b){
    double prod = 1;
    for(int i=0; i<b; i++){
        prod *= a;
    }
    return prod;
}

double factorial(int n){
    double prod = 1;
    for(int i=1; i<=n; i++){
        prod *= i;
    }
    return prod;
}

double exp(double x){
    int sum = 0;
    for(int i=0; i<50; i++){
        sum += pow(x, i)/factorial(x);
    }
}

int main(){
    printf("%.5f\n", exp(1));
    printf("%.5f\n", exp(2.111));
    printf("%.5f\n", exp(0.6931472*1.414));
}
```

<summary>Ans</summary>
</details>


[Continue to The Next Page](10_recursion.html)