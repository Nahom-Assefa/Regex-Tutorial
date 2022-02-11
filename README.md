# Regex Tutorial Starter Code

## Introductory Paragraph

Regular expressions are extremely useful in extracting information from any text by searching for one or more matches of a specific pattern. The application of Regex consists of: passwords, emails, parsing/replacing strings, translating data to other formats, and web scraping. In this tutorial we will be exploring how to utilize Regex for email validation to create parameters for an acceptable entry input.

## Summary

/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

This is one of several often used regular expressions for cross-checking an email input. It is important to note there is no regular expression that matches all possible valid email addresses. However, the RFC 5322 standard is widely regarded as covering majority of even the edge cases. In this gist, I will explain anchors, quantifiers, bracket expressions, and more.

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

### Anchors

Anchors belong to the family of regex tokens that don't match any characters, but that assert something about the string or the matching process. Anchors assert that the engine's current position in the string matches a well-determined location: for instance, the beginning of the string, or the end of a line.

/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/ The first anchor in the match email regex is the caret symbol. This caret indicates that the following character(s) must be at the beginning. Caret works differently if it is used within a character set because then it serves as the negate symbol. The anchor at the end is the $ symbol. Much like the ^ the $ states that a search must end with the preceding characters. 

### Quantifiers

Quantifiers tell the engine to match one or more instances of something to the left of it. This can be a character class, a certain character, or a group. These quantifiers are classified as greedy, docile, lazy, helpful, or possessive.

/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/ The first + for example applies to [a-z0-9_\.-]. The plus quantifier + will match one or more of the character to its left. Note this is different than * which will match zero or more of the character or character set to its left. The left of our + shows a character set. This is considered "greedy" behavior, meaning it will find as many instances of it as possible.

The final grouping of slash / and characters or hyphens followed by another slash can appear any amount of additional times.

The curly brackets here {2,6} are a "match at least" quantifier that say the preceding characters must show up between two and six times. Generally .com but can be .io, .org, .gov among many others.

## OR Operator
The "or" operator will add a logical operation that will accept one thing or another. It uses the | symbol known as pipe. Our example does not use any or operators. This character separates terms contained within each (...) group. Ex. (dogs | cats).

## Character Classes 
A character set determines which characters will be accepted. This expression is wrapped in brackets, and a single match occurs if the character is within the set.

Backslash \ is an escaping character- can also indicate a literal. If a special character is to be used, a backslash must be used to escape it, so it searches for the special character instead of utilizing the actual character. This backslash goes directly in front of that character. 

[a-z0-9_\.-]+ here we have \. which is an example of escaping special character functionality. This is simply a regular period.

On our example, notice [\da-z\.-]. Match any digit with the metacharacter \d. Match any characters from a to z with a-z. \da-z\ is telling it to find any digit or letter. \w is a metacharacter for any alphanumeric character. The \s is for whitespace. The \t is for tabs.

## Flags
The six flags that can be found in a regex are i, g, m, s, u, and y. We don't need any flags to find a URL, because a URL is on a single line.
g : matches the pattern multiple times.
i : makes the regex case insensitive.
m : enables multi-line mode where ^ and $ match the start and end of the entire string. 
    Without this, multi-line strings match the beginning and end of each line.
u : enables support for unicode.
s : short for single line, it causes the . to also match new line characters.

## Grouping And Capturing 
The grouping operator () is used for capturing a group. The regex engine captures this group and treats it as a unit. In our case here: ([a-z0-9_\.-]+) the grouping will capture whatever output is produced from that character set.

## Bracket Expressions 
Bracket expressions allow us to match a range of characters. The square brackets [] can be populated with character classes or a list of characters. Multiple classes or characters inside state that any of the rules will create a match, it does not have to match every single one in fact without a quantifier it will return a single instance. 

## Greedy and Lazy Match
Greedy - finds as many instances as possible
Lazy- finds the minimal amount of matches as possible

## Boundaries
Forward slash / indicates the boundaries of a regular expression.

## Back-references
Once some part of a string is identified, it can be referenced later in the regex instead of explicitly listing it again. This example \3 is not looking for a 3. It is looking for your third described capturing group. What if you wanted to reuse the eigth capturing group again? You can use \8. 

## Look-ahead and look-behind 
Lookahead and lookbehind, collectively called “lookaround”, are zero-length assertions. The difference is that lookaround actually matches characters, but then gives up the match, returning only the result: match or no match. That is why they are called “assertions”. They do not consume characters in the string, but only assert whether a match is possible or not. Lookaround allows you to create regular expressions that are impossible to create without them, or that would get very longwinded without them.

## Credits 
I referenced these links for this analysis: 
1) https://regex101.com/
2) https://youtu.be/r6I-Ahc0HB4 (tutorial #1-16)
3) https://www.regular-expressions.info/lookaround.html
4) https://docs.microsoft.com/en-us/dotnet/standard/base-types/quantifiers-in-regular-expressions
5) https://stackabuse.com/validate-email-addresses-with-regular-expressions-in-javascript/


## Author
Written by Nahom Assefa. I am a full-stack developer receiving my credentials from the University Of Minnesota. 
Github - https://github.com/Nahom-Assefa
Linkedin- https://www.linkedin.com/in/nahom-assefa-163ba414b/