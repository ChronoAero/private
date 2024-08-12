# More Types

> `#include <stdbool.h>`

Apart from the primitive types, we have boolean type.

> Boolean means true/false, yes/no, 1/0

## The Boolean Type

C has since added another type, the boolean type in the C99 standard version of C, as `_Bool`. It has also added the useful alias `bool`, (another name for `_Bool`,) as well as macros `true` and `false` to represent the values for convenience, but these **require the inclusion of `<stdbool.h>`**.


|  Type  |                                                   Description                                                   |
| :-----: | :--------------------------------------------------------------------------------------------------------------: |
| `_Bool` | A boolean value represented in a 1-bit integer. Assigning anything non-`0` to it is set to `1`, considered true. |
| `bool` |                                `true` evaluates to `1`; `false` evaluates to `0`                                |

### Variable Declaration

```c
// Declaring a bool variable with the name is_happy and set it to be true
bool is_happy = true; 
```

## Standard Integer Types

> `#include <stdint.h>`

#### Standard Integer Types

It is not convenient that `int` is sometimes 2 bytes and sometimes 4. It is more useful if we can control exactly how long `int` is, so we do not have to cater to different machine settings. With `<stdint.h>`, we have just that, more type definitions!

<table><thead><tr><th align="center">Short form</th><th width="295.7333577473958">Full name</th><th>Meaning</th></tr></thead><tbody><tr><td align="center"><code>uint8_t</code></td><td>unsigned char</td><td>unsigned 8 bits integer</td></tr><tr><td align="center">uint16_t</td><td>unsigned short</td><td>unsigned 16 bits integer</td></tr><tr><td align="center">uint32_t</td><td>unsigned long</td><td>unsigned 32 bits integer</td></tr><tr><td align="center">uint64_t</td><td>unsigned long long</td><td>unsigned 64 bits integer</td></tr><tr><td align="center">int8_t</td><td>signed char</td><td>signed 8 bits integer</td></tr><tr><td align="center">int16_t</td><td>signed short</td><td>signed 16 bits integer</td></tr><tr><td align="center">int32_t</td><td>signed long</td><td>signed 32 bits integer</td></tr><tr><td align="center">int64_t</td><td>signed long long</td><td>signed 64 bits integer</td></tr></tbody></table>

Both full name and short form work.

> :warning: **Warning**: Remember we said, **we had to manage the memory by ourselves**? Since C is low level, we get to have more choices regarding the memory of our variables. The reason we **must not use `int64_t` for every integer** we have, is because we have to **manage the performance as well as memory** use of our program, especially **for micro-controllers, that have little computational resources.**

Smaller variables are always faster and they consume less space than larger ones.

**Note:**

* `float` and `double` should only be used when necessary as floating point calculation normally takes more time.
* Our board has limited memory and processing power. So choose the most suitable data type to reduce memory usage.

### Variable Declaration

```c
int8_t a = 100;
uint8_t b = 200;
int16_t c = -500;
uint32_t d = 999999;
int64_t e = -9999999999;
```

> If you are really a newbie in programming, I believe you won't understand the parts below. Don't worry, the parts below are not important.

#### Signs and Modifiers

Signed integers will use half of the distinct bit combinations for negative numbers and the other for positive. The ranges are as follows:

![Signed range equation](https://latex.codecogs.com/svg.latex?%5Ctext%7BSigned%20Range%7D%20%3D%20%5B-2%5E%7B%5Ctext%7Bbit%7D-1%7D%2C2%5E%7B%5Ctext%7Bbit%7D-1%7D-1%5D)

![Unsigned range equation](http://latex.codecogs.com/svg.latex?%5Ctext%7BUnsigned%20Range%7D%20%3D%20%5B0%2C2%5E%7B%5Ctext%7Bbit%7D%7D-1%5D)

We can add the `signed` or `unsigned` modifiers to `char` and `int` to set the range the variable can hold. Read other modifiers on [C Language](http://c-language.com/c-tutorial/c-type-modifiers/).

For example, in order to store the integer 3,000,000,000 (3 billion), we need at least `unsigned long` or `uint32_t`. A signed `int` or `long` is not viable, as their maximum value is lower than 3 billion.

```c
#include <stdint.h>

int main() {
    unsigned int var0 = 1; // 32-bit unisgned integer
  
    /**
     * stdint.h defines integer types with different data size.
     * For example: uint8_t, uint16_t, uint32_t and uint64_t.
     */
    uint16_t var1 = 1; // 16-bit unsigned integer
    uint32_t var2 = 2; // 32-bit unisgned integer
    int8_t var3 = 3; // 8-bit signed integer
  
    return 0;
}
```

> :warning: **Warning**: Memory is very limited for some computers, such as embedded systems. It's a good practice that save memory as much as possible so that out-of-memory can be avoided. That's why we have `uint8_t`, `uint16_t`, etc.

#### Useful Tips

By including `<stdint.h>`, you obtain macros defined by the compiler that returns the limits of integer types. For instance, `INT_MAX` and `INT_MIN` are the maximum value and minimum value representable by the `int` type.

By including `<float.h>`, you obtain macros defined by the compiler that returns the limits of floating point types. For instance, `FLT_MAX` and `-FLT_MAX` are the maximum value and minimum value representable by the `float` type.

* **Macro**: Code that will be replaced with the defined replacement before compilation. e.g. If a macro is defined as `#define PI 3.14`, then the macro `PI` can be used as `deg = rad / PI * 180;`, which will be translated to `deg = rad / 3.14 * 180;` before compilation.
* The `-` in `-FLT_MAX` is not part of the macro, it is the unary minus operator, i.e. the negative sign.

To test for the bit size for different types on the machines, we can use the `sizeof()` operator. For example: `sizeof(int)` will tell us how big `int` really is on the machine that runs the program. You must include `<stdlib.h>` in order to use it.
