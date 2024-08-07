# Casting

> how to change data type mid way in the code

### Casting

Assigning a variable or literal in another type to a variable is possible through **casting**. Saving a lower-bit value to a higher-bit container is often safe, but the converse is always unsafe because information is lost by losing bits.&#x20;

(i.e.&#x20;

putting things from a small box to a big box is safe as we can put everything inside the big box,&#x20;

but putting things from a big box to a small box is unsafe because the small box might not have enough space to hold everything and the remaining things might be losted.)

Below are some examples:

```c
int main(){
    bool b = true;
    int n = b; // compiler casts a boolean to an integer, n would be 1 because true -> 1; false -> 0

    char c = 'c';
    n = c; // compiler casts a character to an integer, by using ASCII conversion, n is now 99

    float f = 0.55f;
    n = f; // compiler casts a float to an integer, by truncating the floating point value, n is now 0, same goes with double

    uint8_t p = 6;
    uint16_t q = p; // compiler casts a 8-bit to a 16-bit, since 16-bit can hold larger values, q is also 6

    q = 678;
    p = q; // compiler casts a 16-bit to a 8-bit, since 8-bit cannot store a number this large, it overflows and goes back to 166 (678 in binary with only last 8 bits)

    int16_t j = -5;
    uint16_t k = j; // compiler casts a signed to unsigned, since it cannot store a negative number, it underflows and goes to 65531 (-5 in binary's two's compliment and converts to unsigned)
  
    return 0;
}
```

The type conversion above is an **implicit casting**, i.e. the compiler itself figures out the converted type. Usually, instead, we would prefer a safer approach, that we specify the converted type in our codes.

```c
float f = 2.5f;
int n = (int)f; //n is now 2
```
