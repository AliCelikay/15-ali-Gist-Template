# Email Validation GIST Template

Regex(Regular Expression) is a way to search through a string of text(can be letters, numbers, or special characters) in an advanced way so we can perform tasks such as validation, grabbing certain texts, find and replace, etc. There is a website that can help you test out regex expression and you can follow along with this document. 

## Summary

In this document I will be describing all the components in a regex equation that will allow you to match email with the expression `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

## Table of Contents
- [Anchors](#anchors--and)
- [Quantifiers](#quantifiers--and-n)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components
___
Email Regex for Reference:

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`
___

## Anchors: ^ and $

Anchors match a position before, after, or between characters. 

In our email example the anchors used are the caret `^` symbol and the dollar `$` symbol.

The caret `^` symbol matches the first position of a line and must be placed before the text you are trying to find.
___
Example:

Regex: /^T/

Text: <mark>T</mark>he fat cat ran down the street.
___

As you can see the capital T is the first position in the line and therefore get highlighted.

Next, the dollar symbol `$` matches the end position and must be placed after the text you are tring to find. 
___
Example:

Regex: / \ .$ /

Text: The fat cat ran down the street<mark>.</mark>
___

In our text the final position is a period `.` symbol. There is a unique regex code used to find symbols and that is the back slash ` \ `. The backslash goes first and then your symbol will follow, ` \ (symbol)`.  

___
Example:

Regex: / \ !$ /

Text: The fat cat ran down the street<mark>!</mark>
___


## Quantifiers: + and {(n)}

Quantifiers specify how many instances of a character or group must be present in the text for a match to be found.

In our email example the quantifiers used are the plus sign `+` and the curly brackets `{}`

The addition symbol `+` will match at least one of your search text in a row.
___
Example:

Regex: /e+/

Text: The fat cat ran down the str<mark>ee</mark>t.
___

In our email example the `[a-z0-9_.-]+` code means that the characters inside of the square brakets are expected to appear more than once.

The same is true for `[\da-z\.-]+` this code as well.

Next, the curly brackets `{(n)}` and these symbols will match all the search text that are attached to each other n number of times.
___
Example:

Regex: /\w{4}/

Text: The fat cat ran <mark>down</mark> the <mark>stre</mark>et. It was <mark>sear</mark>|<mark>chin</mark>g for a <mark>mous</mark>e to eat.
___
In our example, the symbol '\w' will return all the words. And in this case, we said return all words that are 4 characters long. You can take this a step further and add a comma with another number.
___
Example 2:

Regex: /\w{4,5}/

Text: The fat cat ran <mark>down</mark> the <mark>stree</mark>t. It was <mark>searc</mark>|<mark>hing</mark> for a <mark>mouse</mark> to eat.
___
In this example the return was a match of all words that are 4 to 5 characters long.

In our email example `[a-z.]{2,6}` means to match the characters inside of the square brackets that are a minimum of 2 characters long and a maximum of 6 characters long.


## Grouping Constructs: ( )
Grouping characters inside of parenthesis allows us to specifically do special things only to the search text inside of the parenthesis and everything you put after the grouping parenthesis will effect the entire grouping and not just a single character.

___
Example:

Regex: /(eat)?t/

Text: The fa<mark>t</mark> ca<mark>t</mark> ran down <mark>t</mark>he s<mark>t</mark>ree<mark>t</mark>. I<mark>t</mark> was searching for a mouse <mark>t</mark>o <mark>eat</mark>.
___
In our example, we are searching for all instances of 't' and the instances of 'eat'.

In our email example, the parenthesis inside of `^([a-z0-9_\.-]+)@` allows for a matching at the beginning of the email and an `@` symbol to the right of the characters inside of the parenthesis.

`@([\da-z\.-]+)\.` for this code we are matching an `@` symbol to the left of the characters inside of the parenthesis and a `.` symbol to the right of the characters in the parenthesis.

Lastly, `\.([a-z\.]{2,6})$` in this code we are matching a `.` to the left of the characters in parenthesis and an ending of the line position with the `$` symbol.

## Bracket Expressions: [ ]
In the square brackets, we can put any characters that we want to match, especially in ranges.
___
Example:

Regex: /[a-z]at/

Text: The f<mark>at</mark> c<mark>at</mark> ran down the <mark>st</mark>re<mark>et</mark>. It was searching for a mouse to e<mark>at</mark>.
___
In this example, we are matching every letter in the alphabet with the character 't'. We can also do that same with capital letters, and numbers: [A-Z0-9].

In our email example, `[a-z0-9_\.-]+` this means to match any combination of all lowercase letters, numbers from 0-9, an underscore, period, and a dash symbol.

The same is true for `[\da-z\.-]+` except the `\d` matches any single digit with the rest of the characters.

Lastly, `[a-z\.]{2,6}` this code allows us to match any lowercase letter in the alphabet and a period in a row of 2-6 characters long.

## Character Classes
There is a list of regex code for classifying a list of characters.

* [abc] Will return an characters in the squar brackets

* [^abc] Will exclude all the characters in the bracket when returning a match

* [a-z] Will return all the characters in the alphabet range

* . Will return all characters  except newline

* \w Will return every word or number and excludes whitespaces

* \d Will return any digit 0-9

* \s Will return all whitespaces, tabs, and line breaks

## The OR Operator: |
The OR operator lets us search for different set of search texts.
___
Example:

Regex: /(t|T)he/

Text: <mark>The</mark> fat cat ran down <mark>the</mark> street.
___
In this example, we are searching for either lowercase 't' or capital 'T' in combination with the set 'he' and we are able to match 'The' and 'the'.

We have no or operator in our email example.

## Flags
There are a list of flags that you can put at the end of the two forward slashes that helps you specify your searches.

* /A/ Forward slashes by itself will return a case-sensitive version of the text, meaning it will only return a capital 'A' or nothing if text has no capital 'A'

* /A/i The 'i' at the end will return all 'a' and 'A'

* /A/g The 'g' at the end looks for multiple occurrences of the text in the foreword slashes in multiple lines. In this case it will look for specifically uppercase 'A' in multiple lines

* //s The 's' at the end will treat an expression of many lines as a single-line.

* //m The 'm' at the end allows for symbols '^' and '$' attach the beginning and end of each line of text.

* //y The 'y' makes a the expression in the slashes stick to a desired position from where it would start to search

* //u The 'u' only works for characters outside of the UTF-16.

We have no flags in our email example, therefore the first case hold true for our purposes.

## Character Escapes
The symbol '\' has the name character escape and will return the literal symbol character from text.

* \ . Will return a period
* \   By itself returns spaces
* \ :  Will return a colon

Our email example was matching a few periods, therefore, the first case is true for our purposes.

## Author

Hi, my name is Ali Celikay. I am working towards being a junior full stack web developer so that I may be able to work full time and continue to persue my Computer Science degree. 

Checkout my other projects in my GitHub repository link below!

[GitHub/AliCelikay](https://github.com/AliCelikay?tab=repositories)
