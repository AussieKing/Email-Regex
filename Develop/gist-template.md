## Table of Contents

- [Regex](#Regex)
- [Email Address](#email-address)
- [Components](#components)
- [Quantifier](#quantifier)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex:

### What is it?

Regex, or Regular Expressions, is a sequence of characters used to define a search pattern. 
It is used in computer science and programming for matching/manipulating strings of text based on specific patterns.

Regex are a combination of literal characters and special characters (also know as "metacharacters") that hold special functions within the regex syntax. 
These special characters enable to apply different rules for pattern matching in text.

Some of the uses for Regex are:

- Searching for specific patterns or substrings within a larger text.
- Validating input data, such as email addresses, phone numbers, or URLs.
- Extracting specific information from text.
- Replacing or manipulating parts of a string.

Regular expressions are supported in many programming languages, making them a versatile and widely adopted technique for text manipulation and analysis.
They can vary in difficulty from relatively simple to very complex.

This specifi Gist will only cover one type of Regex, the email validation type.


## Email address:

An email address typically consists of two main parts:
  1. Local Part (Username): 
  This is the portion before the "@" symbol and identifies the specific mailbox or user within the email system. 
  The local part can include a combination of alphanumeric characters (a-z, A-Z, 0-9), as well as certain special characters such as dots (.), underscores (_), and hyphens (-). 
  However, the specific rules for valid characters and their placement within the local part may vary depending on the email service provider or system.

  2. Domain Part: 
  This is the portion after the "@" symbol and specifies the domain or the mail server that handles the email. 
  It typically consists of two or more domain labels separated by dots. 
  Each domain label can contain lowercase letters (a-z), digits (0-9), and hyphens (-). 
  The last domain label represents the top-level domain (TLD), such as .com, .net, .org, or country-specific TLDs like .us, .uk, etc.
  it is worth noting that the Domain can also include subdomains.  Here, we'll use my email as an example:
  example "fede@gmail.com". We'll also create a subdomain example and a Chinese characters example.

  In the email address "fede@gmail.com", the domain part is "gmail.com". The domain part can be further divided into two subparts:

    - Subdomain: A subdomain is an optional part that appears before the main domain. It is separated from the main domain by a dot (.) and can provide additional context or organization to the domain. In our example, there is no subdomain present. An example of a subdomain could be "subdomain.example.com", where "subdomain" is the subdomain.

    - Main Domain: The main domain represents the primary address or the highest level of the domain hierarchy. It is the part that directly identifies the domain and its associated mail server. In our example, the main domain is "gmail.com".

  Creating a subdomain example:
    Let's create a subdomain example using the email address "fede@gmail.com". Suppose we want to create a subdomain called "sub.fede@gmail.com". Here, "sub" is the subdomain that we have added before the main domain. The email address now includes a subdomain in the domain part.

  Using Chinese characters example:
    Email addresses can include internationalized domain names (IDN), which allow the use of non-ASCII characters, such as Chinese characters, in domain names. For example, let's consider the email address "你好@example.com". Here, "你好" means "hello" in Chinese and serves as the domain part of the email address. The domain part "example.com" remains the same, but it is represented by Chinese characters instead of Latin characters.
    It's important to note that the support for internationalized domain names (IDN) and the specific characters allowed in domain names can vary depending on the email service provider and the email system being used.
    
  Now that we have an idea of what Regula Expressions are, let's break down 
  ```regex
  /^([a-z0-9_\.-]+)@(gmail\.com|yahoo\.com|hotmail\.com)$/
  ```
  

## Components
  
  ### Quantifier
  ```([a-z0-9_\.-]+).``` : This captures the username portion of the email. Here's a breakdown of them: 
    * (asterisk): The asterisk quantifier indicates zero or more occurrences of the preceding element. It matches when the preceding element is present or not. For example, a* matches "a", "aa", "aaa", and so on.

    + (plus): The plus quantifier denotes one or more occurrences of the preceding element. It matches when the preceding element is present at least once. For example, a+ matches "a", "aa", "aaa", and so forth.

    ? (question mark): The question mark quantifier represents zero or one occurrence of the preceding element. It matches when the preceding element is either present or not. For example, colou?r matches both "color" and "colour".

    {n} (exact count): The curly braces with a specific number inside specify an exact count of the preceding element. For example, a{3} matches "aaa" exactly.
  
    {n,} (minimum count): The curly braces with a minimum number inside specify a minimum count of the preceding element. For example, a{2,} matches "aa", "aaa", "aaaa", and so on.

    {n,m} (range count): The curly braces with minimum and maximum numbers inside define a range of counts for the preceding element. For example, a{2,4} matches "aa", "aaa", and "aaaa".

  These quantifiers allow to create more flexible and specific patterns in regular expressions by specifying the number of repetitions needed for certain elements in the pattern.


  ### OR Operator

  The OR operator in regular expressions allows for alternative matching options.

  In regular expressions, the OR operator is represented by the pipe symbol |. It allows you to specify multiple alternatives, any of which can be matched. The regular expression engine will attempt to match each alternative in order.


  ### Character Classes
  In our example, this character class ``` [a-z0-9_\.-] ``` matches any lowercase letter (a-z), digit (0-9), underscore (_), dot (.), or hyphen (-). It represents the valid characters that can appear in the local part (username) of the email address.


  ### Flags:
  Flags are additional settings that can be applied to a regular expression to modify its behavior. Here are the commonly used flags in regular expressions:

  i (case-insensitive): This flag makes the pattern matching case-insensitive. For example, /apple/i would match "apple", "Apple", "APPLE", or any variation of letter case.

  g (global search): This flag enables global searching, meaning the regular expression will match all occurrences in the input string, not just the first one.

  m (multiline): This flag enables multiline mode, which changes how the ^ and $ anchors behave. In multiline mode, ^ matches the start of each line, and $ matches the end of each line, instead of just the start and end of the entire string.

  To apply flags to a regular expression, they are typically appended after the closing delimiter of the regular expression. For example:
  ``` /regex/i
  /regex/g
  /regex/m
  ```


  ### Grouping and Capturing:
  Grouping and capturing are important features in regular expressions that allow you to group and capture specific parts of the matched text. They are typically achieved using parentheses () in the regular expression pattern. Here's how grouping and capturing work:

  - Grouping: Parentheses () are used to group together multiple elements in a regular expression. This allows you to treat the grouped elements as a single unit and apply quantifiers, alternations, or other operations to them.
    ```/(ab)+/``` : (ab) is a group that matches the sequence "ab" one or more times. The parentheses define the grouping, and the + quantifier is applied to the group, indicating one or more occurrences of the group.
    
  - Capturing: In addition to grouping, parentheses () also create capture groups. Capture groups allow you to extract and reference the matched portions of the input string. Each pair of parentheses creates a separate capture group. 
    ``` /(\d{2})-(\d{2})-(\d{4})/ ``` : (\d{2}), (\d{2}), and (\d{4}) are three capture groups that match and capture the day, month, and year portions of a date formatted as "dd-mm-yyyy". The matched values within the capture groups can be accessed or referenced later for further processing.

  Capture groups are typically numbered in the order of their opening parentheses from left to right. In some programming languages, you can also assign names to capture groups for easier referencing.

  ### Bracket Expressions:
  Bracket expressions, also known as character classes, are used in regular expressions to define a set of characters from which a single character can be matched. They allow you to specify a range or a group of characters that can appear at a certain position in the input string.
  - Basic Bracket Expression: A basic bracket expression is defined by enclosing a set of characters within square brackets []. It matches any single character that matches any of the characters within the brackets. 
    ``` /[abc]/ ``` : In this example, [abc] matches a single character that can be either "a", "b", or "c".
    
  - Range in Bracket Expression: A range within a bracket expression allows you to define a continuous range of characters. It is specified using a hyphen - between two characters.
    ``` /[a-z]/ ``` : In this example, [a-z] matches any lowercase letter from "a" to "z". Similarly, [0-9] matches any digit from 0 to 9.
    
  - Negation in Bracket Expression: A caret ^ at the beginning of a bracket expression negates the match. It matches any character that is not within the specified set. 
    ``` /[^0-9]/ ``` : In this example, [^0-9] matches any character that is not a digit.

  Bracket expressions allow you to define custom character sets and specify the acceptable characters at a particular position in the input string. They provide a flexible way to match a single character from a set or a range of characters.


  ### Greedy and Lazy Match:
  In regular expressions, the terms "greedy" and "lazy" refer to the behavior of quantifiers when matching patterns.

  Greedy Match: By default, quantifiers in regular expressions are greedy. A greedy match attempts to match as much as possible while still allowing the overall pattern to match successfully. It means that the quantifier tries to consume as many characters as it can.
  - Greedy: ``` /.*foo/ ``` : In this example, .* is a greedy match, which matches zero or more of any character. When followed by the literal string "foo", it will match the longest possible sequence of characters that ends with "foo".
  
  Lazy Match : A lazy match, also known as a non-greedy match, is the opposite of a greedy match. It attempts to match as little as possible while still allowing the overall pattern to match successfully. It means that the quantifier tries to consume as few characters as it can. A lazy match is indicated by appending a ? after the quantifier. 
  - Lazy : ``` /.*?foo/ ``` : In this example, .*? is a lazy match, which matches zero or more of any character, but in a non-greedy way. It will match the shortest possible sequence of characters that ends with "foo".

  Lazy matching is particularly useful when you want to match the smallest possible substring that satisfies the pattern, especially in cases where there are multiple occurrences of the pattern.


  ### Boundaries:
  In regular expressions, boundaries allow you to specify certain positions in the input string where a match should occur. Boundaries help define the context or position of a pattern within the text.
  - ^ (caret): The caret symbol at the beginning of a regular expression denotes the start of a line or the start of the input string. It asserts that the following pattern should match only at the beginning.
  ``` /^start/ ``` 
  - dollar sign `$` : The dollar sign at the end of a regular expression denotes the end of a line or the end of the input string. It asserts that the preceding pattern should match only at the end.
  ``` /end$/ ```
  - \b (word boundary): The \b assertion matches a word boundary position. It represents the position between a word character (\w) and a non-word character (\W). It helps to match whole words or specific boundaries within a word.
  ``` /\bword\b/ ```
  - \B (non-word boundary): The \B assertion matches a position that is not a word boundary. It represents the position where two word characters or two non-word characters are adjacent. It can be used to match specific positions within a word. 
  ``` /\Bing\B/ ```
  
  
  ### Back References:
  Back references in regular expressions allow you to refer back to previously captured groups within the same regular expression pattern. They enable you to match the same text that was previously captured, facilitating more complex pattern matching and validations. 
  - Capturing Groups: Parentheses () are used to create capturing groups in a regular expression. Each capturing group captures and stores the matched text for later reference
  ``` /(ab)c\1/ ```
  - Numeric Back References: Back references are represented using a backslash \ followed by a number. The number corresponds to the order of the capturing group.
  ``` /(apple) (orange) \2 \1/ ```
  

  ### Look-ahead and Look-behind
  Look-ahead and look-behind are advanced techniques in regular expressions that allow you to assert conditions on the text ahead or behind a specific pattern without including that text in the actual match. They are also known as zero-width assertions as they do not consume characters during the matching process.
  - Positive Look-ahead ((?=...)): A positive look-ahead assertion is represented by (?=...). It specifies that the pattern inside the look-ahead should match the text following the current position, without including that text in the match. The match occurs only if the look-ahead pattern is satisfied. :
  ``` /\w+(?=ing)/ ```
  - Negative Look-ahead ((?!...)): A negative look-ahead assertion is represented by (?!...). It specifies that the pattern inside the negative look-ahead should not match the text following the current position. The match occurs only if the look-ahead pattern is not satisfied.
  ``` /\d+(?!\.)/ ```
  - Positive Look-behind ((?<=...)): A positive look-behind assertion is represented by (?<=...). It specifies that the pattern inside the look-behind should match the text preceding the current position, without including that text in the match. The match occurs only if the look-behind pattern is satisfied.
  ``` /(?<=\$)\d+/ ```
  - Negative Look-behind ((?<!...)): A negative look-behind assertion is represented by (?<!...). It specifies that the pattern inside the negative look-behind should not match the text preceding the current position. The match occurs only if the look-behind pattern is not satisfied.
  ``` /(?<!no-)apple/ ```
  

### Author
Freddy D started coding this year, for the first time! Hooked from the get-go,  now enrolled in University of Adelaide Full-Stak Web Development Bootcamp (via edX). Loves cooking, exercise, and learning new things!