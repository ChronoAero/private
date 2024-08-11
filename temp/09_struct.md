# Struct

> At times, the data types provided by C might not be enough...

`struct` (for structure) is a user-defined data type for combining data items with different types into one.

Syntax:
```
struct <struct_name> {
    <data_type1> <data_name1>;
    <data_type2> <data_name2>;
    <data_type3> <data_name3>;
    ...
};
```
To declare a variable with the struct as the data type:

```
struct <struct_name> <variable_name>;
```

To assign values to the data inside of the struct (can only do this on the declaration):
```
struct <struct_name> <variable_name> = {data1, data2, ...};
```

For example, if we would like to make a struct to contain the information of UST members.

```c
struct USTMember {
    char name[20];
    int ID;
    int age;
};

//declaration of a variable of type UST Member
/*
    here, name = "Mark", ID = 29823163, age = 17
*/
struct USTMember student1 = {"Mark", 29823163, 17};
//structs can be partially initialized, however uninitalized data will contain garbage value
struct USTMember student2 = {"Sam", 23478912};
//It is also OK to not initialize anything
struct USTMember student3; 


//If you would like to declare a variable right after declaring the structure of the struct, you may use the following shorthand syntax (put the variable name before the semicolon):

struct USTProfessor{
    char name[20];
    int ID;
    char department[5];
} professor1 = {"Tyler", 12362133, "COMP"};

```

You can access members of the structure using the dot operator `.`. For example: `Student.ID` or `Student.age`.

More things to note and some examples:

```c
#include <stdio.h>
#include <string.h>

struct USTMember {
    char name[20];
    int ID;
    int age;
};

void print_info(struct USTMember student) { 
    printf("Student Name : %s\n", student.name); //accessing data members
    printf("Student ID : %d\n", student.ID);
    printf("Student Age : %d\n", student.age);   
}

int main() {
    struct USTMember student1;

    /*if you need to change the values after initialization, you need to edit it for each member*/
    strcpy(student1.name, "John");
    student1.ID = 1010;
    student1.age = 18;
    
    print_info(student1);

    struct USTMember student2;

    /* However, you can also do the following, in this case all contents of student1 (including the content of the arrays) will be copied memberwise. In other words, student2.name = "John", student2.ID=1010, student2.age = 18*/
    student2 = student1; 

    struct USTMember student_array[5] = {
        {"Colin", 21378931, 17}, 
        {"Edward", 21346758}
    }; //You can also declare array of structs. As usual, members that are not stated explicitly will be garbage values.

    return 0;
}
```

However, at times, it might be too long to write `struct X`, you may want to make a `typedef` for it.

If the struct is used in the same file:
```c
typedef struct Color{
    int R; int G; int B;
} Color;

Color violet = {255, 0, 255};
```

If the struct will be used in other files (also works for the same file):
```c
struct Color{
    int R; int G; int B;
};

typedef struct Color Color;

Color violet = {255, 0, 255};
```

`struct`s can be tinkered around with to make data structures.

[Continue to The Next Page](10_functions.html)

