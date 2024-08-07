# Constants

> a locked box where we can't put new things inside

#### `const` Type Qualifier

According to [cppreference](https://en.cppreference.com/w/c/language/const), `const` is a type of qualifier in C, adding a "quality" of being constant to the "variable". A variable with such a qualifier in front is not allowed to be reassigned.

```c
const double PI = 3.141592654;
```

Typically, we name constants using the **UPPER\_SNAKE\_CASE** convention, which is discussed below.

Superficially, this protects unchangeable variables from changing, by emitting an error during compilation, making it safer. _But on a deeper level, this qualifier can change the program to a lower, more technical level in the compiler, possibly altering performance and space efficiency._
