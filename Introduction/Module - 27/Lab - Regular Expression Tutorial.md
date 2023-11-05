## Part 1: Complete the regexone.com tutorial.
a. Open a web browser and navigate to https://regexone.com/ from your host computer. Regex One is a
tutorial that provides you with lessons to learn about regular expression patterns.

b. After you have finished with the tutorial, record the function of some of the metacharacters that are used
in regular expressions.

- $ - It matches the end of a line or the end of a string, indicating that the pattern should be found at the very end of the text being matched.
- * - It matches zero or more occurrences of the preceding element.
- . - It  matches any single character except for a newline. It's a wildcard that can represent any character in a text string.
- [ ] - They are used to create a character class, which allows us to specify a set of characters from which one character should be matched. For example, "[abc]" would match any single character that is either 'a,' 'b,' or 'c.'
- \. -  It is used to match a literal period (dot) character. In regular expressions, the dot (.) is a metacharacter that matches any character except for a newline, so if we want to match a period character specifically, we need to escape it with a backslash ().  
- \d - It is a shorthand character class that matches any digit from 0 to 9.
- \D - It is a shorthand character class that matches any character that is not a digit.
- ^ - It is a metacharacter to indicate the start of a line or the start of a string. When placed at the beginning of a regular expression pattern, it asserts that the pattern must match at the beginning of the text being searched.
- {m} - It is used as a quantifier to specify that the preceding element or character should be matched exactly "m" times.
- {n,m} - It is used as a quantifier to specify a range of allowed repetitions for the preceding element or character. It indicates that the element should be matched at least "n" times and at most "m" times.
- abc|123 - It match either "abc" or "123," and if either of these patterns is found in the text being searched, it will be considered a match.

 ## Part 2: Describe the provided regular expression pattern.
 - ^83 - It matches strings that start with the characters "83" at the beginning of a line or string.
- [A-Z]{2,4} - The regex pattern '[A-Z]{2,4}' matches sequences of uppercase letters (A to Z) that are 2 to 4 characters in length.
- 05:22:2[0-9] - matches a string that starts with "05:22:2" followed by any digit from 0 to 9, allowing us to match times like "05:22:20," "05:22:21," and so on up to "05:22:29."
- \.com - This is commonly used to identify domain names with the ".com" top-level domain (TLD) in text.
- complete|GET - The regex pattern 'complete|GET' matches either the word "complete" or the word "GET" in a text.
- 0{4} - The regex pattern '0{4}' matches exactly four consecutive occurrences of the digit 0.

## Part 3: Verify your answers.
a. Launch and log in to the CyberOps Workstation VM (username: analyst / password: cyberops).

b. Open a terminal and navigate to the following folder:

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/e9877dc2-e2f9-4a09-8dce-8c88a7d0fb12)

c. Use the less command to open the logstash-tutorial.log file.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/33dbdd50-4fb1-462a-a33f-ebe380c51eeb)

d. At the bottom of the screen, you will see logstash-tutorial.log: highlighted. This is the cursor at which
you will enter the regular expression. Precede the regular expression with a forward slash (/). For
example, the first pattern in the above table is ^83. Enter /^83.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/73ff8025-c776-45a5-a259-53042628b4e9)

e. For the next expression, enter /[A-Z]{2,4} at the colon (:) prompt.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/bb1eb623-f2a7-43d6-8637-b51089373824)

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/f38d5a50-e8ae-4e11-916b-720206afa35e)

f. Enter the rest of the regular expressions from the table in Step 2. Make sure all the expressions are
preceded with a forward slash (/). Continue until you have verified your answers. Press q to exit the
logstash-tutorial.log file.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/01895a00-d471-4017-9d42-c4127e782360)

g. Close the terminal and shut down the VM.

