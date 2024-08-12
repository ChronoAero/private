# Program time

## Program Time

There are three main time periods of a compiled program:

*   Compile time

    During compilation. The compiler catches syntax errors and other compile-time errors here. If there is an error, the program will not be built.
*   Link time

    The compiler links different bits of compiled code after compilation. In future compilations, the compiler will only compile changed files and run the linker again. Linking error may occur if references to objects are not found, or when compiling for embedded systems, memory allocations exceed maximum memory allowance.
*   Runtime

    This is when the program is running. Unless the program is in **debug mode**, errors here may result in the program crashing without any messages. During debugging, fatal runtime errors will trigger a **breakpoint** and an error message, and the erroneous line is displayed.
