# Regex Guide

What in the world Regex? Where and why would we use them?

## Summary

RegEx, or more fomally knows as a Regular Expression, is a sequence of characters that specifies a search pattern. In JavaScript, regular expressions are also objects. They can be used for a variety of things, such as to "find" or "find and replace" operations on strings, or for input validation! These patterns are used with the match(), matchAll(), replace(), replaceAll(), search(), and split() methods of String.

In this guide, I will be using a RegEx that can match any given URL as an example, I will explain certain components of it and then break it down!

Heres a code snippet of the RegEx:

    /^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/

## **Table of Contents**

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes/sets)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Breakdown](#breakdown)

## **Regex Components**

### ***Anchors***

Anchors do not match any character at all. Instead, they match a position before, after, or between characters. They can be used to “anchor” the regex match at a certain position. The caret ^ matches the position before the first character in the string. Applying ^a to abc matches a. ^b does not match abc at all, because the b cannot be matched right after the start of the string, matched by ^. Similarly, $ matches right after the last character in the string. c$ matches c in abc, while a$ does not match at all.

### ***Quantifiers***

Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found.The quantities n and m are integer constants. Ordinarily, quantifiers are greedy; they cause the regular expression engine to match as many occurrences of particular patterns as possible. Appending the ? character to a quantifier makes it lazy; it causes the regular expression engine to match as few occurrences as possible.

| Greedy Quanifiers | Lazy Quantifiers | Description |
| :---        |    :----:   |          ---: |
| * | *? | Match zero or more times. |
| + | +? | Match one or more times. |
| ? | ?? | Match zero or one time. |
| { n } | { n }? | Match exactly n times. |
| { n ,} | { n ,}? | Match at least n times. |
| { n , m } | { n , m }? | Match from n to m times. |

### ***Character Classes/Sets***

A character class matches only a single character. You can also use a hyphen inside a character class to specify a range of characters. Typing a caret after the opening square bracket negates the character class. The result is that the character class matches any character that is not in the character class. If you don’t want a negated character class to match line breaks, you need to include the line break characters in the class.

### ***Grouping and Capturing***

By placing part of a regular expression inside round brackets or parentheses, you can group that part of the regular expression together. This allows you to apply a quantifier to the entire group or to restrict alternation to part of the regex. Only parentheses can be used for grouping. Square brackets define a character class, and curly braces are used by a quantifier with specific limits.

### ***Bracket Expressions***

Similar to character classes/sets, matches a single character that is contained within the brackets. For example, [abc] matches "a", "b", or "c", and [a-z] specifies a range which matches any lowercase letter from "a" to "z".

### ***Greedy and Lazy Match***

The + sign is a perfect example of something called a greedy match. A greedy match adds as many characters as it can for +, and then shortens that one by one via backtracking (In other words, it shortens the match for the quantifier by one character), if the rest of the pattern doesn’t match.

On the other hand, we have lazy match, the lazy mode of quantifiers is the opposite to the greedy match friend, it will try to repeat a minimal amount of times. We can make a greedy match, lazy just by putting a question mark '?' after the quantifier, so that it becomes *? or +? or even ?? for '?'.

To make things clear: usually a question mark ? is a quantifier by itself (zero or one), but if added after another quantifier (or even itself) it gets another meaning – it switches the matching from greedy to lazy.

## ***Breakdown***

So lets breakdown the URL RegEx from above.

    ^

The beggining, the anchor that starts it all, it matches the first capturing group.

    (https?:\/\/)

The first capturing group, withing this group, we have a **https** character matches for each individual character, which are followed by a ?, which means this group can match multiple URLs such as HTTPS, HTTP, etc.

Single **:** character match, which is followed by \/\/.

The backslashes \\, signify that whatever comes after them, is going to be an escaped character, or "special" character, anything thats not exactly a Letter or Digit, in this case, the forward slashes //, so **\/\/** matches the **//**.

So the first capturing group matches variations of ***https://*** | ***http://*** | etc.

    ([\da-z\.-]+)\.

The second capturing group.

    [\da-z\.-]

Matches any digit (0-9), specified with ***\d***.

***a-z*** matches a lowercase character in the range of ***a*** to ***z***.

Matches ***.*** via an escaped character backslash \ .

***-*** Matches a - if there is one.

Now the + quantifier match one or multiple precedding sets, so you can either have a simple ***https://example***, or ***https://example.example*** match.

    ([a-z\.]{2,6})

The third capturing group.

Has another character set which matches any character in the range a-z, also matches a . Nothing new.

    {2,6}

This is a quantifier, is specifies to match 2-6 of precedding tokens.

This capturing group is whats going to match ***com***,***net***,***gov***, etc. of the URL.

    ([\/\w \.-]*)

The last and final capturing group

Has another character set, this set matches a forward slash /, which is followed by ***\w***, which will match any *word* that comes after the /.

That is then followed by . and - matchers.

The whole set is followed by a * quantifier which specific it can match 0 or more of the preceeding character sets.

All in all, this capturing group will match what comes after the ***.com***, example **.com/test/something**

    \/?$

? specifies there will be 0 or 1 match to our forward slash / at the end of the URL.

The ***$*** is our ending anchor, simple as that!

## ***Author***

Email: semionaevdokimov@icloud.com
