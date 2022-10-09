---
title: Regular Expressions
---

Regular expressions.

## Useful tools

- [RegExr: Learn, Build, & Test RegEx](https://regexr.com/)

## Useful patterns

` [^A-Za-z]+ ` - Match any special character, including accents and other things that some people won't consider "special". In VS Code this can be combined with Opt+Enter to select all matches and then Cmd+L to expand selection to all matching lines, which can then be easily edited or deleted. This can be useful for cleaning up a list.

` ^(?:[\t ]*(?:\r?\n|\r))+ ` - Match empty lines.

` ^(.*)(\r?\n\1)+$ ` - Match duplicate lines

Find: `^(\w+)\s*\n` Replace: `'$1'\n` – Wrap lines in `'`

## Character Classes (metacharacters?) in JavaScript regex

From [Character classes - JavaScript \| MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions/Character_Classes)


`.` | Matches any single character / Inside a character set, matches a literal dot
`\d` | Matches any digit (Arabic numeral). Equivalent to [0-9]. For example, /\d/ or /[0-9]/ matches "2" in "B2 is the suite number".
```
\D	
Matches any character that is not a digit (Arabic numeral). Equivalent to [^0-9]. For example, /\D/ or /[^0-9]/ matches "B" in "B2 is the suite number".

\w	
Matches any alphanumeric character from the basic Latin alphabet, including the underscore. Equivalent to [A-Za-z0-9_]. For example, /\w/ matches "a" in "apple", "5" in "$5.28", and "3" in "3D".

\W	
Matches any character that is not a word character from the basic Latin alphabet. Equivalent to [^A-Za-z0-9_]. For example, /\W/ or /[^A-Za-z0-9_]/ matches "%" in "50%".

\s	
Matches a single white space character, including space, tab, form feed, line feed, and other Unicode spaces. Equivalent to [ \f\n\r\t\v\u00a0\u1680\u2000-\u200a\u2028\u2029\u202f\u205f\u3000\ufeff]. For example, /\s\w*/ matches " bar" in "foo bar".

\S	
Matches a single character other than white space. Equivalent to [^ \f\n\r\t\v\u00a0\u1680\u2000-\u200a\u2028\u2029\u202f\u205f\u3000\ufeff]. For example, /\S\w*/ matches "foo" in "foo bar".

\t	Matches a horizontal tab.
\r	Matches a carriage return.
\n	Matches a linefeed.
\v	Matches a vertical tab.
\f	Matches a form-feed.
[\b]	Matches a backspace. If you're looking for the word-boundary character (\b), see Boundaries.
\0	Matches a NUL character. Do not follow this with another digit.
```