# Regular Expression 

## Introduction

### Matching a specefic String


The simplest *regular expression* is  raw string. The goal is match the **full**
string. We should that in **python** the string should be preceded by a **r**


```python
import re

#Script to match mu
pattern = r'   '

#return a list of matches
match = re.matchall(pattern, big_string)
```

### Matching anything but new line

- The special character `.` matches anything but the **new line**
- In case we want to match the **.** character, we escape it using `\.`


    Let's try to match a string in the form **abc.def.ghi.jkx**. Where the
    characters (a--x) can be anything except newline

```python

pattern = r"^(.){3}\.(.){3}\.(.){3}\.(.){3}$"
```

### Matching Digit and non digit characters

- To match a digit use the special character `\d`
- To match a **non digit** use the special character `\D`

    Let's try to match the string **xxXxxXxxxx**. Where x is a digit and X is
    not a digit
```python

Pat = r'(\d){2}\D(\d){2}\D(\d){4}'
```

### Matching white space and non with space

- To match a **white space** use the special character `\s`
- Faithful to its philosophy, we use the `\S` to match a non space character

    Let's try to match the string **XXxXXxXX** where **x** denotes a white space
    and **X** is not.

```python
Pat = r'(\S){2}\s(\S){2}\s(\S){2}'
```

### Matching a word and not word character

- A word character including alphanumeric characters `[a-z],[A-Z],` and `[0-9]`
- We use the special character `\w` to match those.

    Lets match the string **xxxXxxxxxxxxxxXxxx** where **x** is a white
    character  and **X** is not.

    
```python
Pat = r'(\w){3}\W(\w){10}\W(\w){3}'
```

### Matching start and End

- To match the start of a clause, we use `^` character.
- For the end, we use `$`

    Consider the task of matching **Xxxx.** where 
    - **x** is a word character
    - **X** is a digit.
```python
Pat = r'^\d(\w){4}\.$'
```

## Character class

### Matching a specific character

In order to match a specific we use the `[]` operator. For example in order to
match a vowel, we use `[aeiou]`


## Excluding Specific characters

In order to exclude a set of character, we apply the `[^]`. For example, if want
a non vowel we use `[^aeiou]`


## Matching character ranges

To match a **continguous** range of characters we use `[begin-end]`. For
example, to match an **upper case** character we use `[A-Z]`.

## Repetitions

### Matching {x} repetition

- In order to specify a number of repetition we use `character{repet}`

1. `w{3}`: will match **three** w.
2. `[xyz]{3}` will match a character of 3 containing either `x,y,z`.

### Matching {x,y} repetitions

The tool `{x,y}` will match between **x** and **y** repetitions both inclusive.

1. `w{3,5}`: will match between three to five repetition of w
2. `[xyz]{5,}`:  will match five or **more**. 
3. `\d[1,4]`: will match any digit 1 to 4 times

### Matching zeror or more

To match **zero or more** instance of a character, we preced by the `*`.

1. `w*`: means **zero** or more **w** characters.
2. `[xyz]*`: will catch the character `x`, `y` or `z` 0 ore more times.


###  Matching one or more repetitions

To match a character **one or more times**, we use the quantifier `+`

1. `\w+`: one or more instance of a word character.
2. `[xyz]+`: match one or more instances of **xyz**


### Matching ending items

To match items at the end of a string, we use `$` anchor.


1. `s$`: match an **s** at the end.



## Grouping and Capturing

### Matching words with boundaries

The special character `\b` assert a **word boundary** position.

- A word boundary count as the **start** of a sentence.
- Also as the **end** of the sentence.
- Between two characters of a word.

For example the expression `\bcat\b` will match **A cat** but not **Acat**

### Capturing & non Capturing groups

Parentheses `()` around a regular expression can group that part of the
expression together. This allows to apply different **quantifiers** to that
group.

This parentheses also create a numbered capturing. It store that part of the
string.

- For example, the expression `it (not)? you fault` indicate an optional
  **not**.

The expression `(:?)` is used to create a **non capturing** group.

**Task**: 
    You have a string **S**. Your task is to write a regex which will match
    **S** with the following conditions
    1. **S** should have 3 or more consecutive repetitions of *OK*.

    
```python
Pattern =r'(ok){3,}' 
```

### Alternative matching

**Alternations**, denoted by `|`  character, match a single item out of several
possible items separated by the vertical bar.


- `(and|And|AND`): will match either **and**, **And** or **AND**.
 

## Backreference

### Matching the same string again and again


`\number`: reference the **number** capturing group. Very useful to match
previous matches.

- `(\w)(\w)(\d)\2`: will match **ab2b**
- `(\d)\1`:  will match the same digit repeated two times.



### Backreference to a Failed group

- Backreference to a capturing group that **match nothing** is different from
  backreference to a capturing group that **did not participate in the match**

1. Capturing group that match nothing.
    1. `(b?)o\1`: will match `o` since the first
   **b** is optional and will match  to nothing.
2. Captruing group that didn't participate in the match at all:
    1. `(b)?o\1`

### Branch Resert Group

a [branch reset group](www.regular-expressions.info/branchreset.html)  consiste
of alternations and capturing groups `(?|branch1|branch2)`. They share the same
capturing group.

For example, if we want to capture the start either with **Mr** or **Miss**, we
could write

    `^(?|(Mr)|(Miss)).name \1`

The second `\1` will only match either Mr  or Miss.



### Forward reference

[Forward reference][http://www.regular-expressions.info/backref2.html#forward)
Create a reference to reg that will appear **later**.
They are only useful if they reside in a repeating group.

Let's consider the example `(\2two|(one))+`

It could match the string **onetwo** or **twotwo**.


## Assertions

### Positive lookahead

[The](The.md) positive **loakahead** `(?=)` assert a direct follow up of a regular
expression.

    The lookahead is excluded from the match
    
    
- `c(?=o)`: assert a **c** directly followed by an **o**.


### Negative lookahead

the negative **lookahed** `(?!)`  assert expression not to be followed by a
regular expression. Again the lookahead is exluded from the capture.

- `c(?!o)`: assert a **c** not directly followed by an **o**.

###  Positive Lookbehind

A look behind is characterised by `(?<=)` which assume a regular_exp2 to precede
a match.


- `(?<=[a-z][aeiou]` will a match a **vowel** preceded by a letter.

### Negative lookbehind

A negative lookbehind will simply be charctized by `(?<!)`

- `(?<![a-z][aeiou]` will a match a **vowel** whic not preceded by a letter.
