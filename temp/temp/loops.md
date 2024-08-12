# Loops

> keep doing the same times until ...

### Iteration Statements

Iteration statements are used to repeat a section of code.

#### While loop

This statement will execute repeatedly as long as the condition is met. The format is as follows:

* `while (<expression>) <statement>`

The following is an example:

```c=
int i = 0;
while (i < 10) {
    printf("%d\n", i);
    i++; // you treat i++ as i = i + 1
}
```

The program checks if `i < 10`. If true, then the statements inside `{}` the block are executed. After the block is executed, the program loops back to `i < 10` and executes the block again, until the condition is false.

#### Do-while loop

This statement will execute, then repeatedly execute as long as the condition is met. The format is as follows:

* `do <statement> while (<expression>);`

```c=
do {
    //do something
} while (is_repeat);
```

If `is_repeated` is `true`, the statement will keep looping until `is_repeated` is `false`.

#### For Loop

Often, developers use while loops to execute code while counting. For loops were introduced to simplify this situation while encasing the **iterator** (the counting number) within the scope. The following example illustrates this.

```c=
//This program prints from 0 to 9
int i = 0;
while (i < 10) {
    printf("%d\n", i);
    i++;
}

//Written more concisely as:
for (int i = 0; i < 10; i++) {
    printf("%d\n", i);
}
```

The for-loop format is as follows:

* `for (<init_clause>; <expression (optional)>; <expression (optional)>) <statement>`

The 3 clauses in the parenthesis are usually called:

* **Initialization Expression**

  This expression is run before the statement. Usually, an iterator variable is declared and initialized here.
* **Condition**

  This expression is run before every iteration of the loop to determine whether the body of the loop would be run, or whether the loop ends here. Same as before, the body is run when this expression is a non-zero value.
* **Final Expression**

  This expression is run after every iteration of the loop. Usually, the iterator is incremented or decremented here.

This is the for-loop version of the number printing program above:

```c=
for (int i = 0; i < 10; i++) {
    printf("%d\n", i);
}
```

Of course, because the body is only a single line, the curly braces are not required. So it can become as so:

```c=
for (int i = 0; i < 10; i++)
    printf("%d\n", i);
```

In fact, you can omit one of the clauses or even all of them:

```c=
int i = 0;
for (; i < 10; i++) {
    printf("%d\n", i);
}
```

### Jump Statements

Jump statements alter the flow of the program by literally jumping to a different section of code to execute.

* `break;`

  This statement is only valid in loops and switch statements. It is used to exit the statement, _breaking_ the execution.

  Example:

  ```c=
  for (int i = 0; i < 20; i++) {
      printf("%i = d\n", i);
      if (i == 15) break;
  }
  ```
* `continue;`

  This statement is only valid in loops. It breaks from the current iteration and executes the final expression if the loop is a for loop, then it will move to the condition for comparison immediately, _continuing_ the loop.

  Example:

  ```c=
  for (int i = 0; i < 50; i++) {
      if (i % 2) continue; // skips the printf...
                           // i++ will run, then i < 50
      printf("i = %d\n", i);
  }
  ```
* `return <expression (optional)>;`

  This statement is only valid in functions. It terminates the function, and then _returns_ a resulting value to the caller. It is seen in the `main()` function, returning a program termination code to the operating system.

  `return;` is treated as returning `void`.
* `goto <identifier>;`

  This statement is used to jump to a certain label to continue program execution. **This statement is highly unrecommended, since it may create an erratic control flow as it can jump from scope to scope, and is harmful to debugging as it is difficult to follow the execution path of the program.**
