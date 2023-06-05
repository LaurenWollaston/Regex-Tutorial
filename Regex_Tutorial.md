# Regex Tutorial

Regex, short for Regular Expression, is a tool that can make sure some text is conforming to a specific set of parameters. It dates back to the beginnings of computer science and has great practical use in modern computing. 

## Summary

The purpose of this tutorial is to break down the regex expression 

```/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/```

Which checks to see if the input matches a url. The intent is to demystefy regex because it can look intimidating at first, but is a simpler than it seems. 

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

### Anchors

`/` is the open and close indicating the beginning and end of the expression, but the `^` immediately following the opening of the expression signals the beginning of the string. What comes after this will define what the regex is checking for. 
Similarly, `$` before the final `/` signals the end of the string, that the regular expression does not have to check for anything beyond what you've written. Specifically `^` is the place before the first character, and `$` after the last. 

### Quantifiers
    There are a couple different quantifiers in this expression.
`?` asks for 0 or 1 of the preceding elements in the string. The string matches as few ? elements as needed. 
In `(https?:\/\/)?`, the ? after the https is saying that the http before it might also include an s, but doesn't have to. The ? after the ) is saying that the string it checks may have the whole thing in parentheses in it, but doesn't have to. 

`+`  asks for 1 of the preceeding elements. 
In `([\da-z\.-]+)` the plus means that the string will have something matching the preceeding characters. As in, after the https:// if there is one there will be some text matching that []. 

In `([a-z\.]{2,6})`, the `{2,6}` is a quantifier saying that there will be between 2-6 of the previous. This is checking for the end to the url, the .com or .net. 

In `([\/\w \.-]*)*` the `*` is a quantifier that asks for 0 or more of the previous elements. It is similar to the `?`, except that can only take one. What this is saying is that there could be 0 or more items consisting of 0 or more characters that conform to that character set. 

There is another `?` at the end of the expression, saying that it might end in a `/`. 



### Character Classes
Character sets are defined with [], specifying which characters will be accepted. `([\da-z\.-]+)`, `([a-z\.]{2,6})`, and `([\/\w \.-]*)` all have character sets. Looking at `[\da-z\.-]`, and break it down. `\d` asks for digits, anything 0-9. `a-z` is asking for any letters a through z. `\.` is asking for `.`, and - is looking for `-`. 
Looking at `[\/\w \.-]`. The `\/` is looking for a `/`, the `\w` is looking for a "word character", meaning anything a to z, 0-9, _. Essentially a condensed way to write `[A-Za-z0-9_]`. Just like in the last one the `\.` and `-` are looking for `.` and `-`.

### Grouping and Capturing

Grouping is just using parentheses `()` to group tokens. It is used all over the expression and allows us to check if its a url because it lets us be selective with what we check. The whole expression is mostly grouped into four parts: `(https?:\/\/)`, `([\da-z\.-]+)`, `([a-z\.]{2,6})`, and `([\/\w \.-]*)`. These are checking for different parts of the url. 
    `(https?:\/\/)` - http or https
    `([\da-z\.-]+)` - for the domain and/or subdomain. 
    `([a-z\.]{2,6})` - For the site extention
    `([\/\w \.-]*)` - something after a `/`



### Bracket Expressions

Bracket expressions are checking for matching characters. In this expression, we have `[\da-z\.-]`, `[a-z\.]`, and `[\/\w \.-]`.
    `[\da-z\.-]` - the `\d` is a digit, 0-9. `a-z` is all english letters. `\.` is `.` and `-` is `-`.
    `[\/\w \.-]` - `\/` is `/`, `\w` is a word character, `\.` is `.` and `-` is `-`.

### Greedy and Lazy Match

Greedy and lazy matches are terms for the `+` and `?` quantifiers. `+` is greedy because it tries to find the longest match it can, while `?` is lazy because it tries to find the shortest. 
In `(https?:\/\/)?`, the first `?` after https, checks for either 0 or 1 s attatched to the end of http. the `?` after the group checks for 0 or 1 of that group.
In `([\da-z\.-]+)`, the plus is saying there is going to be 1 or more of the expression before it. If you have `http://website`, it would accept that, and if you had `http://www.website` it would accept that also. 


## Author
Lauren Wollaston
I made this to use a gist. My [github](https://github.com/LaurenWollaston)
