# Introduction to Regular Expressions

Regular expressions, commonly known as regex, are a powerful tool for searching and manipulating text. A regular expression is a pattern that matches a set of strings, helping us to identify or replace specific parts of a text.

Regex has a wide range of applications and can be used in programming languages such as JavaScript to perform tasks such as form validation, text parsing, data extraction, and data cleaning.

Regex syntax uses special characters to define patterns, and we can create complex patterns by combining these characters.

## Creating and Using Regex Patterns

What did you learn while building this project? What challenges did you face and how did you overcome them?

To create a regex pattern, we enclose it within forward slashes (/). For instance, the regex pattern /cat/ will match the string 'cat' in a text.

- We can use the .test() method in JavaScript to search for a pattern in a string. For example, the following code will check whether the word 'cat' is present in the string:

```javascript
let str = "The cat is sleeping";
let regex = /cat/;
console.log(regex.test(str)); // true
```

We can also use the .match() method to find all occurrences of a pattern in a string. For example:

```javascript
let str = "The cat is sleeping, and another cat is playing";
let regex = /cat/g;
console.log(str.match(regex)); // [ 'cat', 'cat' ]
```

Additionally, we can use the .replace() method to replace a matched pattern in a string with a new string. For instance:

```javascript
let str = "The cat is sleeping";
let regex = /cat/;
console.log(str.replace(regex, "dog")); // 'The dog is sleeping'
```

## Regex Modifiers and Character Classes

Regex modifiers are special characters that we can add to a pattern to modify its behavior. Here are some commonly used modifiers:

- i: makes the pattern case-insensitive.
- g: matches all occurrences of a pattern in a string.
- m: enables multiline matching.

For example, the following code matches all occurrences of the word 'cat' case-insensitively:

```javascript
let str = "The Cat is sleeping and another cat is playing";
let regex = /cat/gi;
console.log(str.match(regex)); // [ 'Cat', 'cat' ]
```

Regex also has special character classes that we can use to match specific types of characters. Here are some commonly used character classes:

- \w: matches any word character (a-z, A-Z, 0-9, and \_).
- \d: matches any digit (0-9).
- \s: matches any whitespace character (space, tab, newline, etc.).

We can also use negated character classes to match any character except those in the class. For example, the regex pattern /[^0-9]/ matches any character that is not a digit.

## Problems with Regex

Here are some examples of problems related to Regex in JavaScript:

1. Greedy Matching:
   Consider the following example:

```javascript
const text = "The quick brown fox jumps over the lazy dog.";
const regex = /.*fox/;
const result = text.match(regex);
console.log(result[0]); // The quick brown fox
```

In this example, the regex pattern /._fox/ is greedy, so it matches the longest possible substring that ends with "fox". Instead, we can use the non-greedy quantifier ._? to match the shortest possible substring:

```javascript
const text = "The quick brown fox jumps over the lazy dog.";
const regex = /.*?fox/;
const result = text.match(regex);
console.log(result[0]); // The quick brown fox
```

2. Backtracking:
   Consider the following example:

```javascript
const text = "aaaaaaab";
const regex = /a+a+b/;
const result = text.match(regex);
console.log(result[0]); // aaaaaaab
```

In this example, the regex pattern /a+a+b/ causes backtracking, as it tries to match as many "a"s as possible before matching "b". This can lead to slow performance, especially when working with large strings. Instead, we can use a non-backtracking pattern:

```javascript
const text = "aaaaaaab";
const regex = /a{7}b/;
const result = text.match(regex);
console.log(result[0]); // aaaaaaab
```

3. Character Escaping:
   Consider the following example:

```javascript
const text = "The quick brown fox jumps over the lazy dog.";
const regex = /brown./;
const result = text.match(regex);
console.log(result[0]); // brown
```

In this example, the regex pattern /brown./ matches "brown" followed by any character. However, if we want to match the period character instead of any character, we need to escape it:

```javascript
const text = "The quick brown fox jumps over the lazy dog.";
const regex = /brown\./;
const result = text.match(regex);
console.log(result[0]); // brown.
```

4. Overcomplicated Patterns:
   Consider the following example:

```javascript
const text = "The quick brown fox jumps over the lazy dog.";
const regex = /(quick|slow) (brown|gray|black) (fox|dog)/;
const result = text.match(regex);
console.log(result[0]); // quick brown fox
```

In this example, the regex pattern /quick|slow|brown|gray|black|fox|dog/ is overly complicated, as it matches any combination of "quick", "slow", "brown", "gray", "black", "fox", or "dog". Instead, we can simplify the pattern by breaking it down into smaller, more manageable parts:

```javascript
const text = "The quick brown fox jumps over the lazy dog.";
const regex1 = /(quick|slow)/;
const regex2 = /(brown|gray|black)/;
const regex3 = /(fox|dog)/;
const result1 = text.match(regex1);
const result2 = text.match(regex2);
const result3 = text.match(regex3);
console.log(`${result1[0]} ${result2[0]} ${result3[0]}`); // quick brown fox
```

## Practice Exercises

1. Create a regex pattern to match a string that starts with "Hello" and ends with "world".
1. Create a regex pattern to match a string that contains only letters and spaces.
1. Create a regex pattern to match a string that contains only numbers.
1. Create a regex pattern to match a string that contains an email address.
1. Create a regex pattern to match a string that contains a US phone number (10 digits with or without hyphens).
1. Create a regex pattern to match a string that contains a URL starting with "http://" or "https://".
1. Create a regex pattern to match a string that contains a date in the format "MM/DD/YYYY".
1. Create a regex pattern to match a string that contains a credit card number (Visa, Mastercard, or American Express).
1. Create a regex pattern to match a string that contains a hashtag (starts with "#" and followed by alphanumeric characters).
1. Create a regex pattern to match a string that contains a word that starts with a capital letter and has at least 4 characters.



### more resources

https://gist.github.com/dsdeepak17/09e28abb7b9b2b2102a6a5e2f2b6bb17