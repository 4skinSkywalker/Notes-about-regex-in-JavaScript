# Notes about regex in JavaScript
This document is my collection of notes about regex regarding the JavaScript programming language.

## What is a regex?
A regex is a sequence of characters that defines a search pattern for text.

To make a regex in JavaScript you either uses a couple of double forward slashes or the RegExp constructor: ```/l[iy]nk/``` and ```new RegExp("l[iy]nk")``` mean the same thing.

## Literal characters and Metacharacters
In regex there are two broad categories of symbols you can use:
1. Literal characters (such as the "H" in "Hello")
2. Metacharacters (such as ```\d``` which stands for digit)

## Literal characters
Words, which by definition are sequences of literal characters, are themselves already regex.

Take for instance ```/Hello/``` which matches the word "Hello": a pattern that starts "H", followed by "e", followed by "l", followed by another "l", followed by a "o".

## Metacharacters
Metacharacters are special kind of symbols you can use in the regex to achieve more generic matches.

## Metacharacters: single character
You can have metacharacters that match just one character:
- ```\d``` matches a number from 0 to 9
- ```\w``` matches a word character, which is any alphanumeric
- ```\s``` matches a space (a normal space, a tab and in some cases also the newline)
- ```.``` (literal dot) matches any character whatsoever
- ```\D``` matches a NON number
- ```\W``` matches a NON word character
- ```\S``` matches a NON space

To escape the ```.``` you can use a backslash in front of it, infact "\." means a literal dot.

## Metacharacters: quantifiers
These are reserved symbols in a regex that are use to quantify how many characters of one kind to match:
- ```*``` matches 0 or more occurences
- ```+``` matches 1 or more occerences
- ```?``` matches 0 or 1 occurences (optional character)
- ```{min, max}``` matches from min to max occurences (ends included)
- ```{number}``` matches exactly number occurences

### Quantifiers: use case
Given
> Fredo said that ```color``` stays to ```colours``` as favorite stays to favourites.

```/colou?rs?/``` matches both "color" and "colours" as "?" makes "u" and "s" optional.

## Metacharacters: character class
Character class is one of the two ways to have an OR inside a regex.
The character class is defined with square brackets and it matches one of any character you have put inside the class.

The regex ```[abcd]``` matches an "a" or "b" or "c" or "d".

Note that "*", "+", ".", "(" and ")" in a character class are not interpreted as special characters, instead they are read as literal characters.

### Character class: special characters
Inside a character class you can have special characters, these have special meanings:
- ```[^abcd]``` the "^" at the very start of the class is called negation. It matches a character which is NOT "a" or "b" or "c" or "d". Keep in mind that it still have to match a character, therefore it's NOT like saying match this character NOT followed by these other characters.
- ```[0-9]``` the "-" in between numbers or letters (like so [a-z] or [A-Z]) is called range. It maches a character from 0 to 9 (ends included). You can change the start and the end in order to match different ranges.

To escape the special meaning of the two above:
- To escape negation ("^") just put anywhere but at the start of the class
- To escape the range ("-") just put it at the start of the class

### Character class: use case
Given
> A ```lynk``` is quite a ```link```.

```/l[iy]nk/```

Given
> Select ```row1```, ```row5``` and ```row9```

```/row[0-9]/```

Given
> Fredo and ```fredo```

```/[^F]redo/``` only matches "fredo" because of the use of negation to match a character which is not "F".

## Alternation
Alternation is the other way to have an OR inside a regex.

The difference between character class and alternation is that alternation let you define a whole pattern and not just a single character.

### Alternation: use case
Given
> ```sitename.com```, ```sitename.net```, ```sitename.org``` and sitename.it

```/sitename\.(com|net|org)/``` doesn't match "sitename.it" because there's not "it" in the alternation.

<!--metacharacter: position
metacharacter: capturing group
backreference
regex.test(string)
string.match(regex)
flags
regex.exec(string)
string.split(string)
string.split(regex)
string.replace(string, string)
string.replace(regex, string)
string.replace(regex, function) -->
