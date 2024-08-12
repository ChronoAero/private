# String

> `#include <string.h>`

### Character Array

In C, there is no built-in `string` type. As an alternative, we use **character arrays** to represent a string:

```c
char name[] = "Danny";
```

Although the length of `Danny` is `5`, there is an invisible character `'\0'` at the end, which C uses to indicate the end of the character array. Hence, the size of `name` array is actually `6`.

Just like normal arrays, you can initialize char arrays using `{}` (note that here, we have to a xx`'\0'` character by ourselves):

```c
char day[] = {'2', '4', '-', '0', '7', '-', '2', '0', '2', '0', '\0'};
```

Then you can print the character array using a loop:

```c=
int i = 0;
while (day[i] != '\0') {
    // i++ is post-increment,
    // that means it returns the original value of i,
    // before adding 1 to i
    printf("%c", day[i++]);
}

printf("\n");
```

### strlen()

TODO:

### strcpy()

TODO:

### strcmp()

TODO:
