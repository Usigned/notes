# Bits, Bytes and Integers

[TOc]

## Representing information as bits

### Everything is bits

- **each bit is 0 or 1**
- **By encoding/interpreting sets of bits in various ways**
  - Computers determine what to do (instructions)
  - and represent and manipulate(control) numbers, sets, strings, etc
- **Why bits? Electronic Implementation**
  - easy to store with bistable elements
  - Reliably transmitted on noisy and inaccurate wires
- **Base 2 Number Representation**
  - $15213_{10}$as$11101101101101_2$
  - $1.20_{10}$as$1.00110011[0011]..._2$
  - $1.5213\times 10^4$as$1.1101101101101\times2^{13}$

### Encoding Byte Values

- **Byte = 8 bits**
  - Binary $00000000_2$ to $11111111_2$
  - Decimal $0_{10}$ to $255_{10}$
  - Hexadecimal $00_{16}$ to $FF_{16}$
- To memorize : A ~ 10, D~ 13, F~15

### Example Data Representation

| C Data Type | Typical 32-bit | Typical 64-bit | x86-64 |
| ----------- | :------------: | :------------: | :----: |
| char        |       1        |       1        |   1    |
| short       |       2        |       2        |   2    |
| int         |       4        |       4        |   4    |
| long        |       4        |       8        |   8    |
| float       |       4        |       4        |   4    |
| double      |       8        |       8        |   8    |
| long double |       -        |       -        | 10/16  |
| pointer     |       4        |       8        |   8    |

## Bit-level manipulations

### Boolean Algebra

- And
- Or
- Not
- Exclusive-Or( Xor)

### General Boolean Algebra

- **Operation on Bit Vectors**
  - &
  - |
  - ^
  - ~
- **All of the Properties of Boolean Algebra apply**

### Example: Representing & Manipulating Sets

- **Representation**
- **Operations**
  - & Intersection
  - | Union
  - ^ Symmetric difference 
  - ~ Complement

### Bit-Level Operations in C

- **Operations &, |, ~, ^ Available in C**
- **Examples(Char data type)**
  - ~0x41 -> 0xBE
    - ~01000001 -> 10111110
  - ~0x00 -> 0xFF
  - 0x69 & 0x55 -> 0x7D
    - 01101001 & 01010101 -> 01111101

### Contrast: Logic Operations in C

- **Contrast to logical operators**
  - &&, ||, !
    - View 0 as "False"
    - anything nonzero as "True"
    - **always return 0 or1**
    - <font color='red'>Early termination</font>
- **Examples**
  - !0x41 -> 0x00
  - !0x00 -> 0x01
  - 0x69 && 0x55 -> 0x01
  - 0x69 || 0x55 -> 0x01
  - **p && *p (avoids null pointer access)**

### Shift Operations

- **Left shift: x << y**
  - shift vector x left y positions
    - Throw away extra bits on left
  - Fill with 0's on right
- **Right shift: x >> y**
  - shift vector x right y positions
    - Throw away extra bits on the right
  - Logical shift
    - Fill with 0's in left
  - Arithmetic shift
    - Replicate most significant bit in left
  - Undefined Behavior
    - shift amount <0 or $\ge$ word size

## Integers

### Representation: Unsigned and Signed

#### Encoding Integers

**Unsigned**
$$
B2U(X) = \sum_{i=0}^{w-1}x_i\cdot2^i
$$
**Two's Complement**
$$
B2T(X) = -x_{w-1}\cdot 2^{w-1}+\sum_{i=0}^{w-2}x_i\cdot 2^i
$$
*X is a bit vector*

- **C short 2 bytes long**
- **Sign Bit**
  - For 2's complement, most significant bit indicates sign
    - 0 for nonnegative
    - 1 for negative

#### Numeric Ranges

- Unsigned Values
  - UMin = 0
  - UMax = $2^w-1$
- Two's complement values
  - TMin = $-2^{w-1}$
  - TMax = $2^{w-1}-1$-TMin -1
- Other values
  - Minus 1

#### Values for Different Word Sizes

|      | 8    | 16      | 32             | 64                         |
| ---- | ---- | ------- | -------------- | -------------------------- |
| UMax | 255  | 65,535  | 4,294,967,295  | 18,446,744,073,709,551,615 |
| TMax | 127  | 32,767  | 2,147,483,647  | 9,223,372,036,854,775,807  |
| TMin | -128 | -32,768 | -2,147,483,648 | -9,223,372,036,854,775,808 |

- Observations
  - |TMin| = TMax +1
    - Asymmetric range
  - UMax = 2*TMax +1

#### Unsigend & Signed Numeric Values

- Equivalence
- Uniqueness
- Can Invert Mappings
  - $U2B(X) = B2U^{-1}(X)$
  - $T2B(X) = B2T^{-1}(X)$

### Conversion,  casting

#### Mapping Between Signed & Unsigned

**Two's Complement to Unsigned**
$$
x -> T2B -> B2U -> ux
$$
**Unsigned to Two's Complement**
$$
ux -> U2B -> B2T->x
$$

- <font color = 'red'>keep bit representation and reinterpret</font>

#### Relation between Signed & Unsigned

**Large negative weight **

*becomes*

**Large positive weight**

#### Summary 

**Casting Signed Unsigned: Basice Rules**

- Bit pattern is maintained
- But reinterpreted
- Can have unexpected effects: adding or subtracting $2^w$



## Representations in memory, pointers, strings

