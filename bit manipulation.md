
#BitManipulation is the act of manipulating bits, like changing bits of an integer. At the heart of bit manipulation are the bit-wise operators:

**NOT (~):** Bitwise NOT is a unary operator that flips the bits of the number i.e., if the current bit is 000, it will change it to 111 and vice versa.

```text
N = 5 = 101 (in binary)
~N = ~(101) = 010 = 2 (in decimal)
```

**AND (&):** In bitwise AND if both bits in the compared position of the bit patterns are 111, the bit in the resulting bit pattern is 111, otherwise 000.

```text
A = 5 = 101 (in binary) 
B = 1 = 001 (in binary) 
A & B = 101 & 001 = 001 = 1 (in decimal)
```

**OR ( | ):** Bitwise OR is also similar to bitwise AND. If both bits in the compared position of the bit patterns are 000, the bit in the resulting bit pattern is 000, otherwise 111.

```text
A = 5 = 101 (in binary) 
B = 1 = 001 (in binary) 
A | B = 101 | 001 = 101 = 5 (in decimal)
```

**XOR (^):** In bitwise XOR if both bits are 000 or 111, the result will be 000, otherwise 111.

```text
A = 5 = 101 (in binary) 
B = 1 = 001 (in binary) 
A ^ B = 101 ^ 001 = 100 = 4 (in decimal)
```

**Left Shift (<<):** Left shift operator is a binary operator which shifts some number of bits to the left and appends 000 at the end. One left shift is equivalent to multiplying the bit pattern with 222.

```text
A = 1 = 001 (in binary) 
A << 1 = 001 << 1 = 010 = 2 (in decimal)
A << 2 = 001 << 2 = 100 = 4 (in decimal)

B = 5 = 00101 (in binary)
B << 1 = 00101 << 1 = 01010 = 10 (in decimal)
B << 2 = 00101 << 2 = 10100 = 20 (in decimal)
```

**Right Shift (>>):** Right shift operator is a binary operator which shifts some number of bits to the right and appends 000 at the left side. One right shift is equivalent to dividing the bit pattern with 222.

```text
A = 4 = 100 (in binary) 
A >> 1 = 100 >> 1 = 010 = 2 (in decimal)
A >> 2 = 100 >> 2 = 001 = 1 (in decimal)
A >> 3 = 100 >> 3 = 000 = 0 (in decimal)

B = 5 = 00101 (in binary)
B >> 1 = 00101 >> 1 = 00010 = 2 (in decimal)
```

  

To find the hamming weight of a number, we can use what is called a **mask**. This mask will have a single set bit, initially the least significant one (representing the number `1`, at position `0`). We will AND this mask with the number, and if the result is non-zero, it means the bit is set in the number. We can thus increment the hamming weight by 1 and then continue to the next position by left-shifting the mask, which moves the single bit over to the next position (this is the same as multiplying it by two).

There are two ways we can end this process.

1. Iterate 31 times (since this is the maximum size of an integer)
2. When we find a set bit in the number, flip it to a 0 (with XOR). When the number becomes 0, then we know there are no more set bits and can end.