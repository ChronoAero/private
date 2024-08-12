# Enum

> Enum gives meaningful names to not-meaningful numbers

## Enumeration

**Enumeration** (aka Enum): User-defined data type for assigning names to constants, so the code becomes more legible.

> We will use `UPPER_SNAKE_CASE` most of the time for enums.

```c
enum week {
    SUNDAY, 
    MONDAY, 
    TUESDAY, 
    WEDNESDAY, 
    THURSDAY, 
    FRIDAY, 
    SATURDAY
};
/**
 * SUNDAY corresponds to 0
 * MONDAY corresponds to 1
 * ...
 * SATURDAY corresponds to 6
 * /
```

#### Sample Code

```c
#include <stdio.h> 

enum week {
    SUNDAY, 
    MONDAY = 0, 
    TUESDAY = 3
};
  
int main() { 
   printf("%d, %d, %d\n", sunday, monday, tuesday); 
   return 0; 
}
```

Output:

```
0, 0, 3
```

You can also declare enum variables.

```c
// creating an enum variable called `day` of type `week`

enum week {
    SUNDAY, 
    MONDAY, 
    TUESDAY
} day;

/*--- OR ---*/

enum week {
    SUNDAY, 
    MONDAY, 
    TUESDAY
};
enum week day;
```

#### Sample Code

```c
#include <stdio.h> 
  
enum week {
    SUNDAY, 
    MONDAY = 3, 
    TUESDAY
}; 
  
int main() { 
    enum week day; 
    day = tuesday; 
    printf("%d\n", day); 
    return 0;
}
```

Output:

```
4
```

Enums are useful when we want to define multiple variables which can be grouped together.


## `enum` (Enumeration)*

`enum` is another way to declare our own data type.

> Enum gives meaningful names to not-meaningful numbers

You can declare `enum` using the following syntax:

```
enum <enum-name> {
    <list-of-enum>
};
```

```c
enum Day{
    SUNDAY, //corresponds to 0
    MONDAY, //corresponds to 1
    TUESDAY, // 2
    WEDNESDAY, // 3
    THURSDAY, // 4
    FRIDAY,  // 5
    SATURDAY // 6
};
```

This allows us to write actual words to represent numbers such as `SUNDAY` in our code instead of `0`.

> We will use `UPPER_SNAKE_CASE` most of the time for enums.

For instance:
```c
enum Day{
    SUNDAY,
    MONDAY,
    TUESDAY,
    WEDNESDAY,
    THURSDAY,
    FRIDAY,
    SATURDAY
}

Day day = MONDAY; //let 1 be Monday, 2 be Tuesday, ...

switch (day) {//value to compare against with the cases
    case SATURDAY: //jump here if day==6
    case SUNDAY: //jump here if day==7
        printf("There are no lectures today\n");
        break; //exit from the switch statemtent
    case MONDAY: //jump here if day==1
    case TUESDAY: //jump here if day==2
    case WEDNESDAY: //jump here if day==3
        printf("We have robotics tutorial today\n");
    case THURSDAY: //jump here if day==4
    case FRIDAY: //jump here if day==5
        printf("We have lectures today\n");
        break;
    default: //jump here if matches none of the cases, optional
        printf("Invalid day\n");
}
```

This gives more meaning to numbers in the code. Additionally, the values allowed for variables with `Day` as enum will be restricted in the range $[0,6]$, hence we will not mistakenly assign an invalid day value to it.