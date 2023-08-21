# Regex Tutorial: HEX

**Jayné M. Valverde**

The hexadecimal (also **base-16** or **hex**) numeral system is a ***positional numeral system*** that represents numbers using a base of 16; 16 distinct symbols. 
"0" - "9" representing values 0 to 9 and "A" - "F", or "a" - "f", representing values 10 to 15. 

One of the most common uses of the hex system are HEX color codes. A Hex code is a representation of how much Red, Green and Blue exist in a color (RGB format). <br>
* `#000000`  `#9E9EE9`  `#C06C84` 

## Summary
_________

**Regular Expressions**, or **regex**, are a series of special characters that define a search pattern. Both literal and meta characters are used; Literal characters are standard letters and numbers on the keyboard, while all other characters are considered meta.

The regex we will analyze today: `/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`

This particular regex will allow us to find any hex code, begining with (#), as well as, any code with 6 or 3 characters (digits and letters).

## Table of Contents
_________

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)


<!-- # Regex Components -->


## Anchors
_________
**Anchor**: `^` <br>
 
**Code Fragment**: `/^#`

**Description**: Anchors define the beginnings and endings of lines and words. They do not match a regular expression but, **assert** a set of rules on the string to follow or the matching process. 

**Example**: `^Hello` indicates the string starts with `Hello`.

The `^` anchor asserts that the engine's current position in the string is the beginning of the string, therefore has to match the character `#`. This is how the expression will distriguish a hexedecimal number from the decimal number. 
_________

**Anchor**: `$` <br>

**Code Fragment**: `$/`

**Description**: This character represents the end of a string or a line. Just like the `^` character, the `$` will check if a string matches a pattern, but, will confirm that pattern matches the end of the string. 

**Example**: `Goodbye$` indicates the string ends with `Goodbye`.

For the matching HEX values, the string must match 3 or 6 character patternes of a HEX value prior to the $ anchor. 

## Quantifiers
_________

**Quantifier:** `?` <br>

**Code Fragment**: `/^#?`

**Description**: The `?` character implies a boolean value: true or false, 0 or 1. 
This usually makes the symbol preceding the ? optional. 

**Example**: `/ou?r/` matches both "colour" and "color".

The use of `?` could be used to distinguish between the British and American English spelling (colour & color). <br>

_________

**Quantifier:** `{}` <br>

**Code Fragment**: `{6}` **Code Fragment**: `{3}` 

**Description**: *Quantifiers* set the limits of the string that your regex matches (or an individual section of the string). They frequently include the minimum and maximum number of characters that your regex is looking for. <br>

Quantifiers are inherently *greedy*, meaning they match as many occurrences of particular patterns as possible. If the `?` appened after it, it can be made *lazy*, meaning it will match as few occurences as possible. <br>

Within the HEX regex we are looking at, the quantifier is *greedy*.

**Example**: 6{3} indicates that 6 must be repeated 3 times. The matching string is 666. 

{n}, "n" is a positive integer and it matches exactly "n" occurrences of the preceding item. The `{6}` & `{3}` are quantifiers in this Hex Value expression. The numbers inside specify the number characters that need to be matched in the preceding character class `[a-f0-9]`. <br>
The quantifer allows "n" characters in a string composed of any characters `a-f` and or integers between `0-9`.

## OR Operator
_________
**OR Operator:** `|` <br>

**Code Fragment**: `([a-f0-9]{6}|[a-f0-9]{3})`

**Description**: Our Hex Value Expression has one big group, divided by an **OR operator** `|`. In the Code Fragment above there are two expressions: `[a-f0-9]{6}` and `[a-f0-9]{3})`. Meaning, out regex will match any of those two expressions. 

**Example**: 5|6 infers that either 5 or 6 or both integers are allowed within the string. 555, 666, 565, 656, 556, 665, 655 or 566. 

In this Hex Expression, a matching pattern may contain a strin gof 6 characters that are lowecase `a-f` and/or integers `0-9` and a string of 3 characters that are lowecase `a-f` and/or integers `0-9`. For a string to match it MUST have either 6 or 3 characters with the parameters set within the expression. 

## Character Classes
_________
**Code Fragment**: `a-f0-9`

**Description**: A **character class** defines a set of characters, any of which can occur in an input string to fulfill a match. 

**Example**: If we had a character class `m-p` then the character class would match a single characters between m and p. `"m" "n" "o" or "p"`.

In this Hex Expression, the character class only consists of lower case alphabetic characters `a-f` and integers between `0-9`. 

## Grouping and Capturing
_________
**Grouping & Capturing:** `()` <br>

**Code Fragment**: `([a-f0-9]{6}|[a-f0-9]{3})`

**Description**: Grouping is to **unify** a pattern, so that it is matched as a complete block. Grouping simply *groups up* a sequence into a single unit.

**Example**:`(CAT){4}` will match `CATCATCATCAT`. The *quantifier* would have the unit of characters 'CAT' repeat 4 times. 

The *grouping construct* for the Hex Expression is `([a-f0-9]{6}|[a-f0-9]{3})`. The grouped expression is explained in [Bracket Expressions](#bracket-expressions).

## Bracket Expressions
_________
**Bracket Expression:** `[]` <br>

**Code Fragment**: `[a-f0-9]`

**Description**: Anything inside a set of square brackets `[]` represents a range of characters that we want to match. These patterns are known as **bracket expressions**

**Example**: `[a-h]` is equivalent to `[abcdefgh]`.

The **bracket expression** `[]` in the Hex Expression requires the string to have lowercase characters between `a-f` or any integer between `0-9`.

## Author
_________

I am a web developer.

GitHub: [JayneValverde](https://github.com/JayneValverde) 