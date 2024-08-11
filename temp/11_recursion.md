<script type="text/x-mathjax-config"> MathJax.Hub.Config({ tex2jax: { skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'], inlineMath: [['$','$']] } }); </script> <script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

[Back to Main](index.html) | [Previous Page](09_functions.html)


# Recursion

> a function calling itself, calling itself, calling itself, ...

Now, let's say that you have a function `int f()`, can you do the following?

```c
void f(){
    print("Spam\n");
    f();
}
```
Yes, in fact, you can! The code will print `Spam` indefinitely. This is called a recursive function: a function that calls itself to repeat something.

The example above may seem quite useless, consider the following program instead:


Usually, to compute factorial $n!$, the product of all numbers in $[1, n]$ (For example: $6! = 6 \cdot 5 \cdot 4 \cdot 3 \cdot 2 \cdot 1 =720$). Usually we will use `for` loop to compute it. However, if you think about it:

$$ n! = \left\{ \begin{array}{ll} 1  & n = 1 ~~\textsf{(base case)}\\ n \cdot (n-1)! & n \gt 1 ~~\textsf{(recursive case)}  \end{array} \right.$$

Let's say that we have $6!$:

$6! = 6 \cdot 5! = 6 \cdot 5 \cdot 4! = 6 \cdot 5 \cdot 4 \cdot 3! = 6\cdot 5 \cdot 4 \cdot 3 \cdot 2! = 6 \cdot 5 \cdot 4 \cdot 3 \cdot 2 \cdot 1! = 6 \cdot 5 \cdot 4 \cdot 3 \cdot 2 \cdot 1 = 720$

```c
int factorial(int x){
    if(x==0) {return 1;} //base case
    return x * factorial(x-1); //recursive case
}
```

To make a recursive function, usually we will think about how the state the value of the function given an argument in terms of the value of the function given another argument (recursive case). Moreover, to guarantee that the function will stop calling itself, you need to implement a base case for the function.

Additionally you may also consider the following example (you can call more than one instance of the function):


$$ \textsf{fibonacci}(n) = \left\{ \begin{array}{ll} 0 & n = 0 ~~\textsf{(base case)} \\ 1  & n = 1 ~~\textsf{(base case)}\\ \textsf{fibonacci}(n-1) + \textsf{fibonacci}(n-2) & n \gt 1 ~~\textsf{(recursive case)}  \end{array} \right.$$


```c
int fibonacci(int n) {
    if (n <= 1) {
        return n;
    } else {
        return fibonacci(n - 1) + fibonacci(n - 2);
    }
}
```

> By using recursion, it may increase time complexity and space complexity. However, there is a more efficient way to compute recursive functions in some cases using something called *dynamic programming*.


## Self-Tests

[I will make ruler here]

[Make a program to compute powers using recursion]

[I will make an adjacent object in matrix printout problem]

[Use the backtracking combinatorics as a determine output problem]


#### Self-tests:

Imagine we are given a list of array, we need to print all the combination of the array element with 3 in a group and sort it from small to big using Bubble sort:

    //declar the function protype beforehand
    void combinationUtil(int arr[], int data[], int start, int end, int index, int r);

    /* arr[]  ---> Input Array
    data[] ---> Temporary array to store current combination
    start & end ---> Starting and Ending indexes in arr[]
    index  ---> Current index in data[]
    r ---> Size of a combination to be printed */
    
    void combinationUtil(int arr[], int data[], int start, int end, int index, int r)
    {

    }


    // The main function that prints all combinations of size r
    // in arr[] of size n. This function mainly uses combinationUtil()
    void printCombination(int arr[], int n, int r)
    {

    }
    
    
    int BubbleSort(int* array, int len) {

    }

    int main() {
        int array[5] = {34,16,67,98,13};
        int n = sizeof(arr)/sizeof(arr[0]);
        int r = 3;
        BubbleSort(array,n);
        printCombination(arr, n,r);

    }



[Continue to The Next Page](11_multi_file_programming.html)
