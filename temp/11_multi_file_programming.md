[Back to Main](index.html) | [Previous Page](10_recursion.html)


# Multi-file Programming

> Please don't write more than 1000 lines of code in 1 file

## File Types

C programs are stored as plain text in, often, 2 file types, with their conventional usages. Do follow the conventions, as there are practical and real differences you will see later on.

* `.c` **Source files** - These files contain function implementations.

  For example: the Hello ngaau daiWorld program is stored within `main.c` in my case in some arbitrary project folder that I have created for the tutorial.
* `.h` **Header files** - These files contain functions, structs, global variables, and macro declarations. _Basically, anything declared that can be accessed globally._

  For example: `stdio.h` is an actual header file stored in your computer, and is installed along with your choice of **C toolchain**. The path of different people would likely be different.

  The reason your IDE is able to detect where the libraries are because the installation of the toolchain also appended the source directories within your `PATH` (system environment variable), or the installation path is manually selected in your IDE settings.\*

  To include **compiler-defined** libraries, use `<>`. For example:

  ```c
  #include <stdio.h>
  #include <math.h>
  ```

  To include **user-defined** libraries, use `""`. For example:

  ```c
  #include "my_header_file.h"
  #include "your_header_file.h"
  ```

### Multi-file Programming

TODO:
