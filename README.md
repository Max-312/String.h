# s21_string+

Implementation of the string library.h with additions.


## Contents

1. [Chapter I](#chapter-i) \
    1.1. [Introduction](#introduction)
2. [Chapter II](#chapter-ii) \
    2.1. [Information](#information)
3. [Chapter III](#chapter-iii) \
    3.1. [Part 1](#part-1-implementation-functions-libraries-stringh)  
    3.2. [Part 2](#part-2-partial-implementation-of-the-sprintf function)  
    3.3. [Part 3](#part-3-optional-implementation-of-some-format-modifiers-of-the-sprintf function)  
    3.4. [Part 4](#part-4-optional-implementation-functions-sscanf)  
    3.5. [Part 5](#part-5-additional-implementation-of-special-functions-processing-strings)  




## Chapter I

## Introduction

In this project, you will have to develop your own implementation of the string library.h in the C programming language with some additions (with its own implementation of the sprintf and sscanf functions). The string.h library is the main library of the C language for string processing. As part of this project, you will work out the skills of interacting with string data and strengthen the structural approach.

## Chapter II

## Information

The C programming language contains a set of functions that implement operations with strings (character strings and byte strings) in its standard library. It supports operations such as copying, concatenation, labeling, and searching. For character strings in the standard library, there is a rule that strings must end with a terminating null character: a string of n characters is represented as an array of n + 1 elements, the last of which is the "NULL" character. \
The only string support, actually, in the C programming language is that the compiler converts quoted string constants into strings ending in zero.

### string.h Types

| № | Variable | Description |
| ------ | ------ | ------ |
| 1 | size_t | An unsigned integer type resulting from the sizeof keyword.
	
### string.h Macros

| № | Macro | Description |
| ------ | ------ | ------ |
| 1 | NULL | A macro that is the value of the null pointer constant.

### string.h Functions

| No. | Function | Description |
| ------ | ------ | ------ |
| 1 | void *memchr(const void *str, int c, size_t n) | Searches for the first occurrence of the c character (unsigned type) in the first n bytes of the string pointed to by the argument str. |
| 2 | int memcmp(const void *str1, const void *str2, size_t n) | Compares the first n bytes of str1 and str2. |
| 3 | void *memcpy(void *dest, const void *src, size_t n) | Copies n characters from src to dest. |
| 4 | void *memset(void *str, int c, size_t n) | Copies the c character (unsigned type) to the first n characters of the string pointed to by the str argument. |
| 5 | char *strncat(char *dest, const char *src, size_t n) | Adds the string pointed to by src to the end of the string pointed to by dest, up to n characters long. |
| 6	| char *strchr(const char *str, int c) | Searches for the first occurrence of the c character (unsigned type) in the string pointed to by the argument str. |
| 7 | int strncmp(const char *str1, const char *str2, size_t n) | Compares no more than the first n bytes of str1 and str2. |
| 8 | char *strncpy(char *dest, const char *src, size_t n) | Copies up to n characters from the string pointed to by src to dest. |
| 9 | size_t strcspn(const char *str1, const char *str2) | Calculates the length of the initial segment str1, which consists entirely of characters not included in str2. |
| 10 | char *strerror(int errnum) | Searches the internal array for the errnum error number and returns a pointer to the string with the error message. You need to declare macros containing arrays of error messages for mac and linux operating systems. Error descriptions are available in the original library. The current OS is checked using directives.|
| 11 | size_t strlen(const char *str) | Calculates the length of the string str, not including the terminating null character. |
| 12 | char *strpbrk(const char *str1, const char *str2) | Finds the first character in string str1 that matches any character specified in str2. |
| 13 | char *strrchr(const char *str, int c) | Searches for the last occurrence of the c character (unsigned type) in the string pointed to by the str argument. |
| 14 | char *strstr(const char *haystack, const char *needle) | Finds the first occurrence of the entire needle string (not including the trailing null character) that appears in the haystack string. |
| 15 | char *strtok(char *str, const char *delim) | Splits the string str into a series of tokens separated by delim. |

### sprintf and sscanf

- int sscanf(const char *str, const char *format, ...) - reads formatted input from a string.
- int sprintf(char *str, const char *format, ...) - sends formatted output to the string pointed to by str.

where:
- str − This is the C-string that the function processes as a data extraction source;
- format is a C-string containing one or more of the following elements: a whitespace character, a non-whitespace character, and format specifiers. The format specifier for printing functions follows the prototype: %[flags][width][.precision][length]specifier. The format specifier for scanning functions follows the prototype: %[*][width][length]specifier.

### sprintf and sscanf Specifiers

| № | Specifier | sprintf Result | sscanf result |
| --- | --- | --- | --- |
| 1 | c | Symbol | Symbol |
| 2 | d | Signed decimal integer | Signed Decimal integer |
| 3 | i | Signed decimal integer | Signed integer (can be decimal, octal or hexadecimal) |
| 4 | e | Scientific notation (mantissa/exponent) using the symbol e (the output of numbers must match up to e-6) | Decimal floating point number or scientific notation (mantissa/exponent) |
| 5 | E | Scientific notation (mantissa/exponent) using the symbol E | Decimal floating point number or scientific notation (mantissa/exponent) |
| 6 | f | Decimal floating point number | Decimal floating point number or scientific notation (mantissa/exponent) |
| 7 | g | Uses the shortest representation decimal number | Decimal floating point number or scientific notation (mantissa/exponent) |
| 8 | G | Uses the shortest representation of a decimal number | Decimal floating point number or scientific notation (mantissa/exponent) |
| 9 | o | Unsigned octal number | Unsigned octal number |
| 10 | s | Character String | Character String |
| 11 | u | Unsigned decimal integer | Unsigned Decimal integer |
| 12 | x | Unsigned Hexadecimal integer | Unsigned hexadecimal integer (any letters) |
| 13 | X | Unsigned Hexadecimal integer (capital letters) | Unsigned Hexadecimal integer (any letters) |
| 14 | p | Pointer address | Pointer address |
| 15 | n | Number of characters printed before %n | Number of characters read before %n |
| 16 | % | Character % | Character % |

### sprintf Flags

| No. | Flag | Description |
| --- | --- | --- |
| 1 | - | Left alignment within the specified field width. Right alignment is used by default (see the width subspecifier). |
| 2 | + | Forces you to explicitly specify a plus or minus sign (+ or -) even for positive numbers. By default, only negative numbers are preceded by a "-" sign. |
| 3 | (space) | If the sign is not output, a space is inserted before the value. |
| 4 | # | When used with the specifiers o, x or X, 0, 0x or 0X are inserted before the number, respectively (for values other than zero). When used with e, E and f, it "forces" the recorded output to contain a decimal point, even if it is not followed by any digits. By default, if no digits follow, the decimal point is not written. When used with g or G, the result is the same as with e or E, but the trailing zeros are not removed. |
| 5 | 0 | Fills the number on the left with zeros (0) instead of spaces, where the width specifier is specified (see width subspecifier). |

### sprintf and sscanf Width

| No. | Width | Description |
| --- | --- | --- |
| 1 | ( number) | The minimum number of characters to print. If the output value is shorter than this number, the result is padded with spaces. The value is not truncated, even if the result is larger. |
| 2 | * | In sprintf, the * sign means that the width is specified not in the format string, but as an additional argument of an integer value preceding the argument that needs to be formatted. In sscanf, the * sign placed after % and before the format specifier reads data of the specified type, but suppresses their assignment. |

### sprintf Precision

| № | .Accuracy | Description |
| --- | --- | --- |
| 1	| .number | For integer specifiers (d, i, o, u, x, X) − the precision determines the minimum number of digits to be written. If the recorded value is shorter than this number, the result is padded with leading zeros. The value is not truncated, even if the result is longer. The precision of 0 means that no characters are written for the value 0. For the specifiers e, E and f, this is the number of digits to be printed after the decimal point. For the g and G specifiers, this is the maximum number of significant digits that must be printed. For s, this is the maximum number of printable characters. By default, all characters are printed until a terminating zero is encountered. For type c, it has no effect. If the precision is not specified for the specifiers e, E, f, g and G, then by default its value is 6. If the precision is not specified for the other specifiers, then by default its value is 1. If the number is not specified (there is no explicit precision value), then by default it is 0. |
