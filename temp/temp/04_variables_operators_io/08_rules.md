# Rules and Conventions

### The Idea of a Variable


### Naming Convention and Rules

There are several ways people name their variables, as illustrated in the names:

* `PascalCase`
* `camelCase`
* `snake_case`
* `UPPER_SNAKE_CASE`
* `kebab-case` (Cannot be used in C)

Depending on the organization or the project, you may be asked to use a certain naming convention. They are always used to differentiate between variables, functions, macros, and constants, but different people use different styles.

Secondly, in C and in many other languages, these are some points you must follow in naming a variable, otherwise, you may cause an error during compilation.

* The name should begin with a letter or underscore.

  > :negative\_squared\_cross\_mark: **NOT to do this:**
  >
  > ```c=
  > int 520ilovetimwoo;
  > ```
  >
* After the first character, you may include numbers.

  > :heavy\_check\_mark: **This is acceptable:**
  >
  > ```c=
  > int ilovetimwoo520;
  > ```
  >
* No reserved keywords. E.g. You can't use `int` or `return` as a name.

  > :negative\_squared\_cross\_mark: **NOT to do this:**
  >
  > ```c=
  > int int;
  > float return;
  > ```
  >

#### **Remember, names are case-sensitive.**

**Please assign meaningful names, do not name variables randomly**. As your code becomes more complex, you will forget about what they are. It is also clearer to your peer developers if the names are clear. When you are naming a numerical variable, name it something descriptive, such as `rpm`, `velocity`, `id`, instead of `abc`, `hi`, or `hhh`, which no one would understand. When you are naming a boolean variable, name it a logical statement, like `is_repeat`, `found_path`, `has_changed`, etc.

> [classwork-02](../homework/homework-2-swapping-contents.md)
