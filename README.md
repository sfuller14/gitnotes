# Regex Cheat Sheet

## Commonly Used Regex Operators

| Operator | Description |
| -------- | ----------- |
| `.` | Matches any character except newline |
| `*` | Matches 0 or more repetitions of the preceding character or group |
| `+` | Matches 1 or more repetitions of the preceding character or group |
| `?` | Matches 0 or 1 repetitions of the preceding character or group |
| `{n}` | Matches exactly n repetitions of the preceding character or group |
| `{n,}` | Matches n or more repetitions of the preceding character or group |
| `{,m}` | Matches up to m repetitions of the preceding character or group |
| `{n,m}` | Matches at least n and at most m repetitions of the preceding character or group |
| `\\d` | Matches any digit (equivalent to `[0-9]`) |
| `\\D` | Matches any non-digit character |
| `\\s` | Matches any whitespace character |
| `\\S` | Matches any non-whitespace character |
| `\\w` | Matches any alphanumeric character (equivalent to `[a-zA-Z0-9_]`) |
| `\\W` | Matches any non-alphanumeric character |
| `^` | Matches the start of the string |
| `$` | Matches the end of the string |
| `(abc)` | Matches the group 'abc' |
| `(?:abc)` | Non-capturing group |
| `abc|def` | Matches 'abc' or 'def' |
| `[abc]` | Matches any of the characters 'a', 'b', or 'c' |
| `[^abc]` | Matches any character except 'a', 'b', or 'c' |

## Lookarounds

| Lookaround | Description |
| ---------- | ----------- |
| `(?=abc)` | Positive lookahead. Asserts that what immediately follows the current position in the string is 'abc' |
| `(?!abc)` | Negative lookahead. Asserts that what immediately follows the current position in the string is not 'abc' |
| `(?<=abc)` | Positive lookbehind. Asserts that what immediately precedes the current position in the string is 'abc' |
| `(?<!abc)` | Negative lookbehind. Asserts that what immediately precedes the current position in the string is not 'abc' |

## Common Use Cases

- **Extract date from a string (mm-dd-yyyy format):** `\\b\\d{2}-\\d{2}-\\d{4}\\b`
    - This matches a string of the form 'mm-dd-yyyy' where each 'm', 'd', and 'y' is a digit.

- **Match an email address:** `\\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\\.[A-Za-z]{2,}\\b`
    - This matches an email address. The part before the '@' symbol can contain any alphanumeric character, as well as '.', '%', '+', and '-'. The domain name part can contain any alphanumeric character and '.', and it must end with a period followed by at least two letters.

- **Match a URL:** `https?://[A-Za-z0-9.-]+\\.[A-Za-z]{2,}`
    - This matches a URL that starts with 'http://' or 'https://', followed by any number of alphanumeric characters or '.', and ending with a '.' followed by at least two letters.

- **Match a phone number (US format):** `\\b\\(\\d{3}\\) \\d{3}-\\d{4}\\b`
    - This matches a phone number in the format `(123) 456-7890` where each '1', '2', '3', etc. is a digit.

- **Match a word at the beginning of a line:** `^\\w+`
    - This matches a word at the beginning of a line. The '^' symbol denotes the start of the line, and '\\w+' matches one or more word characters.

- **Match a word at the end of a line:** `\\w+$`
    - This matches a word at the end of a line. The '$' symbol denotes the end of the line, and '\\w+' matches one or more word characters.

## Using Regex with ripgrep

Ripgrep is a line-oriented search tool that recursively searches your current directory for a regex pattern. Here are a few examples of how to use regex with ripgrep:

- **Search for all lines containing 'abc' in all .txt files:** `rg 'abc' -g '*.txt'`
    - This command uses the regex pattern 'abc' to search through all .txt files in the current directory and its subdirectories.

- **Search for all lines starting with 'abc' in all .txt files:** `rg '^abc' -g '*.txt'`
    - The '^' symbol in the regex pattern '^abc' means that 'abc' must be at the start of the line.

- **Search for all lines ending with 'abc' in all .txt files:** `rg 'abc$' -g '*.txt'`
    - The '$' symbol in the regex pattern 'abc$' means that 'abc' must be at the end of the line.
