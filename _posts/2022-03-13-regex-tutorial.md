---
title: Regex Tutorial
subtitle:
date: 2022-03-13         20:00 +0100
last_modified_at:
tags: [regex,regular-expressions,tutorial]
---

<style>
w { background: #F5F5F5 }
y { background: PaleGoldenrod }
h { background: Aquamarine }
z { background: LightBlue }
r { color: FireBrick  }
o { color: Orange }
n { color: Green }
d { color: DodgerBlue }
v { color: Magenta }
l { color: LimeGreen }
g { color: DarkGray }
</style>


## 1. History of Regex

Regular expressions (Regex) were first introduced in 1951, when mathematician Stephen Cole Kleene described regular languages using his mathematical notation called regular events. In 1973 Ken Thompson written a program called `grep`. It is a command-line utility for searching plain-text data sets for lines that match a regular expression. Its name comes from the ed command `g/re/p` (**g**lobally search for a **r**egular **e**xpression and **p**rint them). Grep was originally developed for the Unix operating system, but later available for all Unix-like systems (eg. Linux, MacOS, BSD, Solaris).

**Regular expressions are not a programming language - they are used for matching, searching and replacing text by describing search patterns**. It allows you to find text patterns, extract parts from long strings or validate data submitted by users.

Today, Regex is widely supported in programming languages (Java, JavaScript, Perl, Python, C#, etc.), text processing programs, advanced text editors, and some other programs. Regex is an essential skill for any computer programmer to have.


## 2. Getting started

### 2.1 Different regular expression engines

There are different implementations or versions of Regular Expression, these are the most popular:
- C/C++
- Java
- JavaScript
- .NET
- Perl
- PHP
- Python
- Ruby
- Unix
- Apache
- MySQL

### 2.2 Choose a regular expression engine to get started

- [RegExr](https://regexr.com/){:target="_blank"} - **recommended for beginners**, online tool, no installation required, cross-platform, supports JavaScript and PHP engines
- [Regex101](https://regex101.com/){:target="_blank"} - online tool, no installation required, cross-platform, supports PHP, JavaScript, Python, Golang and Java engines
- [RegExPal](https://regexpal.com/){:target="_blank"} - online tool, no installation required, cross-platform, supports JavaScript and PHP engines
- grep, egrep - Essential command line tools in Unix and Unix-like systems
- [Visual Studio Code](https://code.visualstudio.com/){:target="_blank"} - text editor for Microsoft Windows, Linux and macOS
- [Atom](https://atom.io/){:target="_blank"} - text editor for macOS, Linux, Microsoft Windows and Chrome OS
- [Notepad++](https://notepad-plus-plus.org/){:target="_blank"} - text editor for Microsoft Windows
- [TextMate](https://macromates.com/){:target="_blank"} - text editor for macOS


## 3. Parts of Regex syntax

Bellow is an example of Regular expression with marked sections of syntax. This particular syntax can be used to check whether entered email address is valid.

<b><g>/</g><r>^</r><h><l>(</l></h><y><o>[</o>a-z0-9_.-<o>]</o></y><z><d>+</d></z><h><l>)</l></h>@<h><l>(</l></h><y><o>[</o>a-z0-9_.-<o>]</o></y><z><d>+</d></z><h><l>)</l></h><v><span>&#65340;.</span></v><h><l>(</l></h><y><o>[</o>a-z.<o>]</o></y><z><d>{2,6}</d></z><h><l>)</l></h><r>$</r><g>/gi</g></b>

**<g>Delimiters and Flags</g>, Literal Characters, <v>Escapes</v>,**  
**<o>Character Sets</o>, <l>Groups</l>, <d>Quantifiers</d>, <r>Anchors</r>**


## 4. Delimiters

Delimiters indicate the start and end of the regular expression pattern. It depends on Regex implementation, most frequently it is delimited with forward slashes `/abc/` (JavaScript, PHP, Perl), where "abc" is a regular expression. Forward slashes are not part of the expression, they are just the delimiters, that hold it. In some implementations you can find e.g. double quotes `"abc"` (Python) or backticks <code>&#96;abc&#96;</code> (Golang) as delimiters.


## 5. Flags

There are different search modes (flags) which can be used within regular expressions:

| Flags | Syntax | Meaning |
|--|--|--|
| standard | `/abc/` | Find first match |
| **g**lobal | `/abc/g` | Find all matches, look globally |
| Case **i**nsentitive | `/abc/i` | Find matches regardless of uppercase or lowercase letters |
| **m**ultiline | `/abc/m` | Find text that stretches across more than one line |

> **NOTE:** It is not recommended to use *Case insensitive mode*, safer way is to set case sensitivity within syntax


## 6. Literal characters

Literal characters from `a` to `z`, which represent themselves.

| Example | Text matching | |
|--|--|--|
| `/al/` | se<b><y>al</y></b>, sell, salad, proposal, silk | [Try it](https://regexr.com/6do3g) |
| `/al/g` | se<b><y>al</y></b>, sell, s<b><y>al</y></b>ad, propos<b><y>al</y></b>, silk | [Try it](https://regexr.com/6do0p) |


## 7. Metacharacters

Non-letter characters `\.*+-{}[]^$|?():!=`, which have special meanings.

| Metacharacter | Meaning |
|--|--|
| `.` | Any character except newline character ([Wildcard](#h-71-wildcard)) |
| `[]` | A set of characters ([Character sets](#h-73-character-sets)) |
| `^` | Starts with ([Anchors](#h-77-anchors)) |
| `$` | Ends with ([Anchors](#h-77-anchors)) |
| `*` | Zero or more occurrences ([Quantifiers](#h-74-quantifiers)) |
| `+` | One or more occurrences ([Quantifiers](#h-74-quantifiers)) |
| `?` | Zero or one occurrence ([Quantifiers](#h-74-quantifiers)) |
| `{}` | Exactly the specified number of occurrences ([Quantifiers](#h-74-quantifiers)) |
| `()` | Character group ([Groups](#h-75-groups)) |
| `| ` | Either or ([Alternation](#h-76-alternations)) |
| `\ ` | Escape the next metacharacter and treat it as literal character ([Escapes](#h-72-escapes)) |
| `\t` | Tab character ([Shorthand character classes](#h-78-shorthand-character-classes)) |
| `\n` | New line in Unix and Unix-like systems (Linux, macOS, BSD) |
| `\r\n` | New line in Microsoft Windows |


### 7.1 Wildcard

Wildcard metacharacter `.` **matches any single character except newline**. If you need to match period or dot symbol use an escape metacharacter before period `\.`

| Example | Text matching | |
|--|--|--|
| `/9.00/g` | <b><y>9.00</y></b> <b><y>9500</y></b> <b><y>9-00</y></b> | [Try it](https://regexr.com/6do5c) |
| `/9\.00/g` | <span><b><y>9.00</y></b> 9500 9-00</span> | [Try it](https://regexr.com/6do5f) |


### 7.2 Escapes

Backslash metacharacter `\ ` **escapes the next metacharacter** - this means the next metacharacter will be treated as literal character.

Escaping is only for metacharacters. Literal characters should never be escaped as it gives them different meaning (see [Shorthand character classes](#h-78-shorthand-character-classes)). Quotation marks do not need to be escaped as they are usually not metacharacters.

| Example | Text matching | |
|--|--|--|
| `/9.00/g` | <b><y>9.00</y></b> <b><y>9500</y></b> <b><y>9-00</y></b> | [Try it](https://regexr.com/6do5c) |
| `/9\.00/g` | <span><b><y>9.00</y></b> 9500 9-00</span> | [Try it](https://regexr.com/6do5f) |


### 7.3 Character sets

With square brackets `[]` you **match one of several characters inside brackets**.

Metacharacters inside square brackets usually does not need to be escaped - except `]-^\ `.

| Character set | Meaning | 
|--|--|
| `[abcd]` | character `a`, `b`, `c` or `d` |
| `[a-d]` | character `a`, `b`, `c` or `d` |
| `[^ab]` | any character except `a` and `b` |
| `[123]` | any of the digits `1`, `2` or `3` |
| `[0-9]` | any digit |
| `[7-9][0-9]` | any two-digit numbers from `70` to `99` |
| `/[70-99]/g` | any three-digit numbers starting with `7` and ending with `9` |
| `[a-z]` | any lowercase character |
| `[A-Za-z]` | any uppercase or lowercase character |

| Example | Text matching | |
|--|--|--|
| `/s[ea]l/g` | seal, <b><y>sel</y></b>l, <b><y>sal</y></b>ad, propo<b><y>sal</y></b>, silk | [Try it](https://regexr.com/6drdk) |
| `/s[aei]l/g` | seal, <b><y>sel</y></b>l, <b><y>sal</y></b>ad, propo<b><y>sal</y></b>, <b><y>sil</y></b>k | [Try it](https://regexr.com/6drdq) |
| `/se[a-z]/g` | <span><b><y>sea</y></b>l, <b><y>sel</y></b>l, salad, proposal, silk</span> | [Try it](https://regexr.com/6dre3) |
| `/s[^a]l/g` | seal, <b><y>sel</y></b>l, salad, proposal, <b><y>sil</y></b>k | [Try it](https://regexr.com/6gsrl) |
| `/s[^ei]l/g` | seal, sell, <b><y>sal</y></b>ad, propo<b><y>sal</y></b>, silk | [Try it](https://regexr.com/6dre6) |
| `/s[a.]l/g` | seal, sell, <b><y>sal</y></b>ad, propo<b><y>sal</y></b>, silk | [Try it](https://regexr.com/6gssj) |


### 7.4 Quantifiers

The metacharacters `*`, `+`, `?` or `{}` are used to **specify how many times a preceding subpattern can occur**. These metacharacters act differently in different situations.

| Quantifier | Meaning | Alternative |
|--|--|--|
| `*` | Matches **zero or more repetitions** of the preceding character | `{0,}` |
| `+` | Matches **one or more repetitions** of the preceding character | `{1,}` |
| `?` | Matches **zero or one repetition** of the preceding character | `{0,1}` |
| `{n}` | Matches **exactly _n_ repetitions** of the preceding character | |
| `{min,}` | Matches **_min_ or more repetitions** of the preceding character | |
| `{0,max}` | Matches **_max_ or less repetitions** of the preceding character | |
| `{min,max}` | Matches **at least _min_ repetitions but no more than _max_ repetitions** of the preceding character | |

#### 7.4.1 Greedy

- Generally, a greedy quantifiers will match the longest possible string.
- By default, all quantifiers are greedy.
- Regex match as much as possible before giving control to the next expression part

#### 7.4.2 Lazy

- Generally, a lazy quantifiers will match the shortest possible string.
- To make quantifiers lazy, just append `?` to the existing quantifier, e.g. `*?`, `+?`, `{0,2}?`.
- Regex match as little as possible before giving control to the next expression part

#### 7.4.3 Examples

| Example | Text matching | |
|--|--|--|
| `/s.?a/g` | <b><y>sea</y></b>l, sell, <b><y>sa</y></b>lad, propo<b><y>sa</y></b>l, silk | [Try it](https://regexr.com/6gvio) |
| `/s.+a/g` | <b><y>seal, sell, salad, proposa</y></b>l, silk | [Try it](https://regexr.com/6gvjd) |
| `/s.+?a/g` | <b><y>sea</y></b>l, <b><y>sell, sa</y></b>lad, proposal, silk | [Try it](https://regexr.com/6gvj4) |
| `/s.*a/g` (greedy) | <b><y>seal, sell, salad, proposa</y></b>l, silk | [Try it](https://regexr.com/6gvjm) |
| `/s.*?a/g` (lazy) | <b><y>sea</y></b>l, <b><y>sell, sa</y></b>lad, propo<b><y>sa</y></b>l, silk | [Try it](https://regexr.com/6gvk2) |
| `/s.{1}a/g` | <b><y>sea</y></b>l, sell, salad, proposal, silk | [Try it](https://regexr.com/6gvms) |
| `/s.{1,2}a/g` | <b><y>sea</y></b>l, sell, <b><y>sala</y></b>d, proposal, silk | [Try it](https://regexr.com/6gvmm) |
| `/s.{1,}l/g` (greedy) | <b><y>seal, sell, salad, proposal, sil</y></b>k | [Try it](https://regexr.com/6gvnq) |
| `/s.{1,}?l/g` (lazy) | <b><y>seal</y></b>, <b><y>sel</y></b>l, <b><y>sal</y></b>ad, propo<b><y>sal</y></b>, <b><y>sil</y></b>k | [Try it](https://regexr.com/6gvoc) |

### 7.5 Groups

Groups are a way to **treat multiple characters as a single unit**. They are created by placing the characters to be grouped inside a set of parentheses `()`  
Groups can be used for:
    - Create a group of alternation expression
    - Apply repetition operators to a group
    - Capture group for use in matching and replacing

| Example | Text matching | |
|--|--|--|
| `/s(a|e|i)l/g` (same as `s[aei]l`) | seal, <b><y>sel</y></b>l, <b><y>sal</y></b>ad, propo<b><y>sal</y></b>, <b><y>sil</y></b>k | [Try it](https://regexr.com/6h59f) |
| `/s(a|e|i){0,1}a/g` | <b><y>sea</y></b>l, sell, <b><y>sa</y></b>lad, propo<b><y>sa</y></b>l, silk | [Try it](https://regexr.com/6h5dm) |
| `/(dark)?blue/g` | light<b><y>blue</y></b>, <b><y>darkblue</y></b>, dark<b><y>darkblue</y></b> | [Try it](https://regexr.com/6ha4t) |
| `/(dark){0,}blue/g` | light<b><y>blue</y></b>, <b><y>darkblue</y></b>, <b><y>darkdarkblue</y></b> | [Try it](https://regexr.com/6ha56) |
| `/^[0-9a-f]{2}(:[0-9a-f]{2}){5}$/i` | <b><y>23:32:A5:98:F1:CD</y> | [Try it](https://regexr.com/6ha37) |


### 7.6 Alternations

You can use the vertical bar `|` metacharacter to **match any one of a series of patterns**, where the `|` character separates each pattern.  
Metacharacter `|` is used as an "OR" operator

| Example | Text matching | |
|--|--|--|
| `/s(a|e|i)l/g` | seal, <b><y>sel</y></b>l, <b><y>sal</y></b>ad, propo<b><y>sal</y></b>, <b><y>sil</y></b>k | [Try it](https://regexr.com/6h59f) |
| `/(dark|light)blue/g` | blue, <b><y>lightblue</y></b>, <b><y>darkblue</y></b>, dark<b><y>darkblue</y></b> | [Try it](https://regexr.com/6ha64) |
| `/(dark|light)?blue/g` | <b><y>blue</y></b>, <b><y>lightblue</y></b>, <b><y>darkblue</y></b>, dark<b><y>darkblue</y></b> | [Try it](https://regexr.com/6ha6d) |
| `/(dark|light){0,}blue/g` | <b><y>blue</y></b>, <b><y>lightblue</y></b>, <b><y>darkblue</y></b>, <b><y>darkdarkblue</y></b> | [Try it](https://regexr.com/6ha6j) |
| `/dark(blue|green)?/g` (greedy) | <b><y>dark</y></b>, <b><y>darkblue</y></b>, <b><y>darkgreen</y></b> | [Try it](https://regexr.com/6ha72) |
| `/dark(blue|green)??/g` (lazy) | <b><y>dark</y></b>, <b><y>dark</y></b>blue, <b><y>dark</y></b>green | [Try it](https://regexr.com/6ha7b) |


### 7.7 Anchors

Anchors are **referencing a position**, not an actual character

| Anchors | Meaning | 
|--|--|
| `^` | Start of string/line |
| `$` | End of string/line |
| `\A` (not all engines) | Start of string, never end of line |
| `\Z` (not all engines) | End of string, never end of line |
| `\b` | Word boundary (start/end of word) |
| `\B` | Not a word boundary |

| Example | Text matching | |
|--|--|--|
| `/^\w+ \w+$/g` | <b><y>San Francisco</y></b> | [Try it](https://regexr.com/6ha9d) |
| `/^\w+ \w+$/g` | San Francisco San Francisco | [Try it](https://regexr.com/6haa2) |
| `/\b\w+\b\w+\b/g` | San Francisco San Francisco | [Try it](https://regexr.com/6haa5) |
| `/\b\w+\b \b\w+\b/g` | <b><y>San Francisco</y></b> <b><y>San Francisco</y></b> | [Try it](https://regexr.com/6haa8) |
| `/\B\w+\B/g` | S<b><y>a</y></b>n F<b><y>rancisc</y></b>o S<b><y>a</y></b>n F<b><y>rancisc</y></b>o | [Try it](https://regexr.com/6haab) |

### 7.8. Shorthand character classes

Other characters with special meaning

| Shorthand | Meaning |
|--|--|
| `\n` | New line |
| `\r` | Carriage return |
| `\t` | Tab |
| `\v` | Vertical tab |
| `\d` | Any digit: `[0-9]` |
| `\w` | Any word character including underscore: `[a-zA-Z0-9_]` |
| `\w\-` | Any word character including underscore and hyphen: `[a-zA-Z0-9_\-]` |
| `\s` | Whitespace: `[\t\r\n]` |
| `\D` | Not digit: `[^\d]` or `[^0-9]` |
| `\W` | Not word character: `[^\w]` or `[^a-zA-Z0-9_]` |
| `\S` | Not whitespace: `[^\s]` or `[^\t\r\n]` |

> All letters, digits, underscores and dashes can be matched with `[\w\-]`

> No digits or whitespace characters can be matched with `[^\d\s]`. Don't use `[\D\S]`, it means "either no digits or no whitespace characters"


## 8. Further resources

- [Learning Regular Expressions](https://www.linkedin.com/learning/learning-regular-expressions-2){:target="_blank"} by [Kevin Skoglund](https://github.com/kevinskoglund){:target="_blank"}
- [RegExr](https://regexr.com/){:target="_blank"} - RegExr is a HTML/JS based tool for creating, testing, and learning about Regular Expressions
- [W3 Schools: Python RegEx](https://www.w3schools.com/python/python_regex.asp){:target="_blank"}