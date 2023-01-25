# Regex Tutorial

## Summary

This tutorial will contain explanation of Regex components that includes Anchors, Quantifiers, Grouping Constructs, Bracket Expressions, Character Classes, The OR Operator, Flags and Character Escapes.  

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

### Anchors
In regular expressions, an anchor is a special character or sequence of characters that asserts a specific position in the input string, such as the start or end of the string, or the presence of a word boundary.
Here is an example of using anchors in JavaScript to match a specific pattern in a string:
let input = "The quick brown fox jumps over the lazy dog.";
let pattern = /^The/; // Anchor for start of string
let match = input.match(pattern);
console.log(match); // Output: ["The"]

In this example, the regular expression /^The/ uses the ^ anchor to assert that the input string must start with the characters "The". The input.match(pattern) method is used to find the first match of the pattern in the input string, and it returns an array containing the matching substring.
Here is an example of using \b anchor:

let input = "The cat in the hat";
let pattern = /\bcat\b/; // word boundary for cat
let match = input.match(pattern);
console.log(match); // Output: ["cat"]
In this example, the regular expression /\bcat\b/ uses the \b anchor to assert that the word "cat" should be surrounded by word boundaries.
And this is an example of using \B:
let input = "I caught a catfish";
let pattern = /\Bcat\B/; 
let match = input.match(pattern);
console.log(match); // Output: null

let input = "I caught a catfish";
let pattern = /\Bcat\B/; 
let match = input.match(pattern);
console.log(match); // Output: null
In this example, the regular expression /\Bcat\B/ uses the \B anchor to assert that the word "cat" should not be surrounded by word boundaries.

### Quantifiers
In regular expressions, quantifiers are used to specify the number of times a character or a group of characters should appear in the input string.

There are several types of quantifiers in JavaScript regular expressions:
*: Matches zero or more occurrences of the preceding character or group. For example, the regular expression /ca*t/ will match "ct", "cat", "caat", "caaaat", etc.
+: Matches one or more occurrences of the preceding character or group. For example, the regular expression /ca+t/ will match "cat", "caat", "caaaat", etc., but not "ct".
?: Matches zero or one occurrences of the preceding character or group. For example, the regular expression /ca?t/ will match "ct" and "cat", but not "caat" or "caaaat".
{n}: Matches exactly n occurrences of the preceding character or group. For example, the regular expression /ca{2}t/ will match "caat", but not "ct" or "cat".
{n,}: Matches n or more occurrences of the preceding character or group. For example, the regular expression /ca{2,}t/ will match "caat", "caaaat", etc., but not "ct" or "cat".
{n,m}: Matches between n and m occurrences of the preceding character or group. For example, the regular expression /ca{1,2}t/ will match "cat" and "caat", but not "ct" or "caaaat".
Here is an example of using a quantifier in JavaScript:
let input = "The quick brown fox jumps over the lazy dog.";
let pattern = /[a-z]{3,}/g; // at least 3 lowercase letter
let matches = input.match(pattern);
console.log(matches); // Output: ["quick", "brown", "jumps", "over", "the", "lazy"]

In this example, the regular expression /[a-z]{3,}/g uses the {3,} quantifier to match any sequence of at least 3 lowercase letters. The g flag is used to perform a global search, which returns all matches in the input string as an array.

### Grouping Constructs
In regular expressions, grouping constructs are used to group characters or sub-expressions together, in order to apply quantifiers or other special characters to the entire group.
There are two types of grouping constructs in JavaScript regular expressions:
Parentheses (): Used to group characters or sub-expressions together. For example, the regular expression /(cat|dog)/ will match "cat" or "dog" in the input string.
Capturing groups (): used to capture the matched characters, which can be accessed later through the match method. For example, the regular expression /(cat) (dog)/ will match "cat dog" in the input string, and the matched "cat" and "dog" can be accessed separately.
Here is an example of using a grouping construct in JavaScript:
let input = "The cat in the hat";
let pattern = /(cat)/; // capturing group
let match = input.match(pattern);
console.log(match[1]); // Output: "cat"

In this example, the regular expression /(cat)/ uses a capturing group to match the word "cat" in the input string, and the matched substring can be accessed using the match[1] syntax, where 1 is the index of the first capturing group.
Another example:
let input = "The quick brown fox jumps over the lazy dog.";
let pattern = /(th[oe])/ig; // group and match either "the" or "tho"
let matches = input.match(pattern);
console.log(matches); // Output: ["The", "the", "the"]

In this example, the regular expression /(th[oe])/ig uses a capturing group (th[oe]) to match either "the" or "tho" in the input string, and the matched substrings are stored in an array and returned by the match() method.

### Bracket Expressions
In regular expressions, bracket expressions are used to match a set of characters in a specific position of the input string. Bracket expressions are defined using square brackets [].
Here are some examples of using bracket expressions in JavaScript regular expressions:
[abc]: Matches any single character that is either "a", "b", or "c".
[^abc]: Matches any single character that is not "a", "b", or "c".
[a-z]: Matches any single lowercase letter.
[A-Z]: Matches any single uppercase letter.
[0-9]: Matches any single digit.
Here is an example of using a bracket expression in JavaScript:
let input = "The quick brown fox jumps over the lazy dog.";
let pattern = /[a-z]{3,}/g; // at least 3 lowercase letter
let matches = input.match(pattern);
console.log(matches); // Output: ["quick", "brown", "jumps", "over", "the", "lazy"]

In this example, the regular expression /[a-z]{3,}/g uses a bracket expression [a-z] to match any lowercase letter, and the {3,} quantifier to match at least 3 occurrences of the bracket expression. The g flag is used to perform a global search, which returns all matches in the input string as an array.
Here is another example:
let input = "123-456-7890";
let pattern = /[0-9]{3}-[0-9]{3}-[0-9]{4}/; // match phone number
let match = input.match(pattern);
console.log(match); // Output: ["123-456-7890"]

In this example, the regular expression /[0-9]{3}-[0-9]{3}-[0-9]{4}/ uses bracket expressions [0-9] to match any digit and the quantifiers {3} and {4} to match 3 and 4 digits respectively. The pattern is matching a phone number format and returns an array with the matched phone number
You can also use predefined character classes, such as \d to match any digit, \w to match any word character, and \s to match any whitespace character. These predefined character classes have the same effect as the corresponding bracket expressions but are more concise to write.



### Character Classes
In regular expressions, character classes are a shorthand way to match a specific set of characters. Character classes are defined using special characters or sequences of characters.
JavaScript supports several predefined character classes:
\d: Matches any digit (equivalent to [0-9]).
\w: Matches any word character (letters, digits, and underscores; equivalent to [A-Za-z0-9_]).
\s: Matches any whitespace character (spaces, tabs, and line breaks).
. : Matches any character except a new line \n
\D: Matches any non-digit character (equivalent to [^0-9]).
\W: Matches any non-word character (equivalent to [^A-Za-z0-9_]).
\S: Matches any non-whitespace character (equivalent to [^ \t\r\n\f]).
Here is an example of using a character class in JavaScript:
let input = "The quick brown fox jumps over the lazy dog.";
let pattern = /\w+/g; // word characters
let matches = input.match(pattern);
console.log(matches); // Output: ["The", "quick", "brown", "fox", "jumps", "over", "the", "lazy", "dog"]

In this example, the regular expression /\w+/g uses the \w character class to match any word character, and the + quantifier to match one or more occurrences of the character class. The g flag is used to perform a global search, which returns all matches in the input string as an array.
Another example:
let input = "123-456-7890";
let pattern = /\d{3}-\d{3}-\d{4}/; // match phone number
let match = input.match(pattern);
console.log(match); // Output: ["123-456-7890"]

In this example, the regular expression /\d{3}-\d{3}-\d{4}/ uses the \d character class to match any digit, and the quantifiers {3} to match 3 digits, and - to match the dash character. The pattern is matching a phone number format and returns an array with the matched phone number.
Using predefined character classes can make your regular expressions more concise, readable and efficient.

### The OR Operator
The OR operator, also known as the "pipe" operator, is used to match one of several possible patterns in a regular expression. In JavaScript, the OR operator is represented by the | character.
Here is an example of using the OR operator in a JavaScript regular expression:
let input = "The cat in the hat";
let pattern = /cat|dog/; // match either "cat" or "dog"
let match = input.match(pattern);
console.log(match); // Output: ["cat"]

In this example, the regular expression /cat|dog/ uses the | operator to match either the substring "cat" or the substring "dog" in the input string. The match() method returns an array containing the first match that it finds, in this case, "cat"
You can chain multiple | to match multiple patterns, for example:
let input = "The cat in the hat";
let pattern = /cat|dog|bird/; // match either "cat" or "dog" or "bird"
let match = input.match(pattern);
console.log(match); // Output
This expression will match the first occurrence of "cat", "dog" or "bird"
You can also group patterns together and use the | operator to match any of the group, for example:
let input = "The cat in the hat";
let pattern = /(cat|dog|bird) in the/; // match either "cat in the" or "dog in the" or "bird in the"
let match = input.match(pattern);
console.log(match); // Output: ["cat in the", "cat"]

This expression will match the first occurrence of "cat in the", "dog in the" or "bird in the" and the first capturing group will contain the matched animal.
The OR operator can be useful when you want to match multiple variations of a pattern, without having to write multiple regular expressions.

### Flags
In JavaScript, regular expression flags are used to modify the behavior of the regular expression. They are added after the regular expression and are specified as one or more letters following two forward slashes //.

Here are some common regular expression flags in JavaScript:
g: Global search. When this flag is set, the regular expression will search for all matches in the input string, rather than stopping after the first match.
i: Case-insensitive search. When this flag is set, the regular expression will match both uppercase and lowercase characters, regardless of the case of the input string.
m: Multi-line search. When this flag is set, the regular expression will treat the input string as multiple lines, rather than a single line. This allows the use of the ^ and $ anchors to match the start and end of each line, rather than the start and end of the entire input string.
Here is an example of using the g flag in JavaScript:
let input = "The quick brown fox jumps over the lazy dog.";
let pattern = /[a-z]{3,}/g; // at least 3 lowercase letter
let matches = input.match(pattern);
console.log(matches); // Output

In this example, the regular expression /[a-z]{3,}/g uses the g flag to perform a global search for all matches of the pattern in the input string. The match() method returns an array containing all the matches found.
Here is an example of using the i flag:
let input = "The Quick Brown Fox jumps over the lazy dog.";
let pattern = /the/i; // match word "the" regardless of the case
let matches = input.match(pattern);
console.log(matches); // Output: ["The",

In this example, the regular expression /the/i uses the i flag to match the word "the" regardless of the case. The match() method returns an array containing all the matches found.
Here is an example of using the m flag:
let input = "The quick brown\nfox jumps over the\nlazy dog.";
let pattern = /^The/gm; // match lines starts with "The"
let matches = input.match(pattern);
console.log(matches); // Output: ["The", "The"]

In this example, the regular expression /^The/gm uses the m flag to treat the input string as multiple lines. The ^ anchor asserts the start of the line, and the g flag performs a global search. The match() method returns an array containing all the matches found.

### Character Escapes
In regular expressions, character escapes are used to match special characters or sequences of characters that have a special meaning in regular expressions. In JavaScript, character escapes are represented by a backslash \ followed by the character or sequence to be matched.
Here are some common character escapes in JavaScript regular expressions:
\d: Matches any digit (equivalent to [0-9]).
\w: Matches any word character (letters, digits, and underscores; equivalent to [A-Za-z0-9_]).
\s: Matches any whitespace character (spaces, tabs, and line breaks).
\. : Matches a dot character.
\* : Matches a star character.
\\ : Matches a backslash character.
\+ : Matches a plus character.
\? : Matches a question mark character.
\^ : Matches a caret character.
\$ : Matches a dollar character.
\[ : Matches a left square bracket character.
\] : Matches a right square bracket character.
\( : Matches a left parenthesis character.
\) : Matches a right parenthesis character.
\{ : Matches a left curly brace character.
\} : Matches a right curly brace character.
\| : Matches a pipe character.
\: : Matches a colon character.
\! : Matches an exclamation mark character.
\= : Matches an equal sign character.
\> : Matches a greater than character.
\< : Matches a less than character.
Here is an example of using a character escape in JavaScript:
let input = "The quick brown fox jumps over the lazy dog.";
let pattern = /The\./; // match "The."
let match = input.match(pattern);
console.log(match); // Output: ["The."]

In this example, the regular expression /The\./ uses the \. character escape to match the period character that follows the word "The" in the input string.
Another example:
let input = "123-456-7890";
let pattern = /\d{3}-\d{3}-\d{4}/; // match phone number
let match = input.match(pattern);
console.log(match); // Output: ["123-456-7890"]


In this example, the regular expression /\d{3}-\d{3}-\d{4}/ uses the \d character escape to match any digit, and the quantifiers {3} to match 3 digits, and - to match the dash character. The pattern is matching a phone number format and returns an array with the matched phone number.
As you can see, using character escapes can make your regular expressions more precise, by allowing you to match specific characters or sequences that have a special meaning in regular expressions.


## Author

My name is Merrin and I am an aspiring web developer.
Github:  https://github.com/Mer2022
