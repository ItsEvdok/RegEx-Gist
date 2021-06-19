# Matching URL Regex

What in the world Regex? Where and why would we use them? In this small tutorial I will hopefully be able to explain that to you while also showing you an example!

## Summary

Briefly summarize the regex you will be describing and what you will explain. Include a code snippet of the regex. Replace this text with your summary.

/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes/sets)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)

## Regex Components

### Anchors

Anchors do not match any character at all. Instead, they match a position before, after, or between characters. They can be used to “anchor” the regex match at a certain position. The caret ^ matches the position before the first character in the string. Applying ^a to abc matches a. ^b does not match abc at all, because the b cannot be matched right after the start of the string, matched by ^. Similarly, $ matches right after the last character in the string. c$ matches c in abc, while a$ does not match at all.

### Quantifiers

Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found.The quantities n and m are integer constants. Ordinarily, quantifiers are greedy; they cause the regular expression engine to match as many occurrences of particular patterns as possible. Appending the ? character to a quantifier makes it lazy; it causes the regular expression engine to match as few occurrences as possible.

| Greedy Quanifiers | Lazy Quantifiers | Description |
| :---        |    :----:   |          ---: |
| * | *? | Match zero or more times. |
| + | +? | Match one or more times. |
| ? | ?? | Match zero or one time. |
| { n } | { n }? | Match exactly n times. |
| { n ,} | { n ,}? | Match at least n times. |
| { n , m } | { n , m }? | Match from n to m times. |

### Character Classes/Sets

A character class matches only a single character. You can also use a hyphen inside a character class to specify a range of characters. Typing a caret after the opening square bracket negates the character class. The result is that the character class matches any character that is not in the character class. If you don’t want a negated character class to match line breaks, you need to include the line break characters in the class.

### Grouping and Capturing

By placing part of a regular expression inside round brackets or parentheses, you can group that part of the regular expression together. This allows you to apply a quantifier to the entire group or to restrict alternation to part of the regex. Only parentheses can be used for grouping. Square brackets define a character class, and curly braces are used by a quantifier with specific limits.

### Bracket Expressions

Similar to character classes/sets, matches a single character that is contained within the brackets. For example, [abc] matches "a", "b", or "c", and [a-z] specifies a range which matches any lowercase letter from "a" to "z".

### Greedy and Lazy Match

The + sign is a perfect example of something called a greedy match. A greedy match adds as many characters as it can for +, and then shortens that one by one via backtracking (In other words, it shortens the match for the quantifier by one character), if the rest of the pattern doesn’t match.

On the other hand, we have lazy match, the lazy mode of quantifiers is the opposite to the greedy match friend, it will try to repeat a minimal amount of times. We can make a greedy match, lazy just by putting a question mark '?' after the quantifier, so that it becomes *? or +? or even ?? for '?'.

To make things clear: usually a question mark ? is a quantifier by itself (zero or one), but if added after another quantifier (or even itself) it gets another meaning – it switches the matching from greedy to lazy.

## Author

Emaail: semionaevdokimov@icloud.com
