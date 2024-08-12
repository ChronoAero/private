# Typedef

> let's be lazy and write less stuff

## Typedef

**typedef**: Keyword for users to give a data type a new name.

```c
typedef int INTEGER;

INTEGER a, b;
/**
 * identifier `INTEGER` is treated as `int`
 * so `a` and `b` would be treated as `int`.
 * /
```

`typedef` can also be used to simplify user-defined data types.

```c
typedef struct USTMember {
    char name[20];
    int ID;
    int age;
} Student;

// The following are equivalent:
struct USTMember john;
Student john;
```

```c=
typedef enum Day{
    Monday,
    Tuesday,
    Wednesday,
    Thursday,
    Friday,
    Satuarday,
    Sunday
} day;

// The following are equivalent
enum Day today = Monday;
day today = Monday;
```
