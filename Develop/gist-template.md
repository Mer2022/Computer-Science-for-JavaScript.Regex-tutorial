# Title (replace with your title)

Introductory paragraph (replace this with your text)

## Summary

Briefly summarize the regex you will be describing and what you will explain. Include a code snippet of the regex. Replace this text with your summary.

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

### Character Classes

### The OR Operator

### Flags

### Character Escapes

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
