#Programming #Regex #bash 

`\d` – any number
`.` – (dot) wildcard
`[abc]` – any one of characters inside of brackets
`[^b]` – hat = not (not b)
`\w` – English letters/numbers
`[a-c]` – letters a to c inclusive
`.{5}` – any character 5 times
`abc{3,5}` – abccc (3 to five c's)
`a+` – 1 or more a's
`a*` - 0 or more a's
`s?` – optional s
`\s` – whitespace
`^success$` – starting and ending
`(extract)` – extract info from brackets
`/abc/` – starting and ending delimiter
`/XYZabc/i` – i = case sensitive
`I love (cats|dogs)` – | = or
`/D` – not number
`/W` - not word
`/S` - not whitespace

`/^\/dev\//` - bash scripting, regex expressions are bookended by `/`
	`\` - escapes the following character

```c
#include <regex.h>

// regex_t datatype. receives a compiled regex
regex_t regex;
// datatype array to capture groups
regmatch_t pmatch[1];

//regex compile returns 0 if match, else !0
regcomp(ptr to regex_t, ptr to pattern or "pattern", REG_EXTENDED|(flags));

// saves result in pmatch. returns 0 on success
regexec(&regex, string, 1, pmatch, 0

// frees compiled regex resources
regfree(&regex)
```

```c
#include <regex.h>

bool validate_username (const char *username)
{
    regex_t regex;
    const char *pattern = "^[a-z0-9_]{4,16}$";

    if (regcomp(&regex, pattern, REG_EXTENDED) != 0) 
        return 0;

    int result = regexec(&regex, username, 0, NULL, 0);

    regfree(&regex);

    return (result == 0);
}
```