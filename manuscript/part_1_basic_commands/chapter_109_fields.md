# Day 9 - Fields

{blurb, icon: quote-right}
-- _In the plus column, though she makes a hell of a cup of coffee._
Batman Returns (1992)
{/blurb}

Data is often structured, and many times a good way to split data is to use fields separated by a specific character. This is true for Comma-Separated Values files (CSV), but it is also true for other types of data. For example, the words in a sentence are separated by spaces, the numbers in an IP address are separated by dots (`192.168.0.1`), and hours, minutes, and seconds in a time string can be separated by colons (`08:41:12`).

It is thus definitely useful to learn how to pick a specific field or set of fields from a string, and the best way to do it in Unix is to use the command `cut`. This command has two important options: `-d` specifies the character used to split the fields, and `-f` specifies the fields themselves, counting from 1. Let's consider an example

``` sh
$ echo "12:34:56" | cut -d ":" -f 2
```

This splits the string `12:34:56` into three fields, namely `12`, `34`, and `56`, as the separator given to the command is the colon character, and then picks field number 2, which corresponds to minutes. Using command substitution we might then assign this to a variable

``` sh
$ minutes=$(echo "12:34:56" | cut -d ":" -f 2)
```

The `-d` option accepts a single character as a delimiter, and the default value is `TAB` as in the special character for tabulation, being that a common way to space fields. As you can see I wrapped the colon in quotes, which are not strictly necessary, but they become so when we want to use a space

``` sh
$ echo "This is a sentence with many words" | cut -d " " -f 4
```

My advice is to just always use the quotes, it is useless to waste time thinking if you need them or not. As we said, the field option accepts the number of a field, but it can also parse sequences  like `4-7`, lists like `4,7`, and combinations of the two. Read the manual page to discover all the supported formats.

* * *

## Exercises

Time for some exercises! At this point we have a pretty good amount of tools in our belt, so we can start performing useful tasks. Let's consider the simple.log file, which represents the part of the logs of a web server (a simplified version of an actual log of the Apache server). Remember that you can print the content of the file beforehand with either `cat` or `head`


{#exercise_9_01}
#### Exercise 9.01
Print fields 1,6,7, and 8 of the file `simple.log`

[Go to solution](#solution_9_01)

{#exercise_9_02}
#### Exercise 9.02
Extract the time of each request as HH:MM:SS

[Go to solution](#solution_9_02)


* * *

Speaking of cutting, we made it in one piece apparently. Well, at least I am still OK, on the bus on my way to the office. Where are you? If you are commuting I hope you'll get soon to your office or home, and in this second case that you can have a good time relaxing and not worrying too much about fields.

Suggested film for the evening: Edward Scissorhands (1991) - Cutting has never been more fun!