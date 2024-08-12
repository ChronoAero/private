# Macros

> macros helps you "find and replace all" when you compile your code

### Macros

Associates a name with a piece of code. During preprocessing, the compiler will replace all encounters of the name with the corresponding code. Macros are defined with the `#define` directive.

```c
#define SIZE 5

//  All occurrences of `SIZE` will be replaced by `5`.
int array[SIZE];
for (int i = 0; i < SIZE; i++) {
	scanf(" %d", &array[i]);
}
for (int i = 0; i < SIZE; i++) { 
    printf("%d \n", array[i]); 
}
```

### Macro Functions

Macros can take arguments and can be used like functions.

**Sample Code**

```c
#include <stdio.h>

#define PI 3.14159265
#define CIRCLE_AREA(r) (r*r*PI)

int main() {
    float radius = 10.0, area;
  
    area = CIRCLE_AREA(radius);
    printf("Area of the circle : %ld", area);
  
    return 0;
}
```
