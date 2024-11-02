# Enhance!
Medium\
Forensics\
picoCTF 2022\
svg\
Author: LT 'syreal' Jones
#### Description
Download this image file and find the flag. [Download image file](https://artifacts.picoctf.net/c/102/drawing.flag.svg)
## Solution
Download the file and start with finding out the filetype with `file`.

Seeing this is an SVG there are lots of strings associated with this filetype.  Let's see what `strings` shows us.
```bash
strings drawing.png.svg
```

Well, there is a variable called **tspan** that has the portions of the flag assigned. 

`strings drawing.png.svg | grep tspan`

At this point we can copy out each line and erase what we do not need OR we could practice our command line foo.

`strings drawing.flag.svg | grep tspan | grep -oP '(?<=>).*?(?=<)' | tr -d "\n" | tr -d " "`

Let’s break it down step by step:

1. **`strings drawing.flag.svg`**:
    
    - The `strings` command extracts printable strings from binary files. Here, it's used on the `drawing.flag.svg` file, which is typically a text-based XML file (SVG) but may contain binary data as well. The command will output sequences of printable characters (usually at least 4 characters long) from the file.
2. **`| grep tspan`**:
    
    - The output of the `strings` command is then piped (`|`) into `grep tspan`. The `grep` command searches for lines that contain the substring `tspan`, which is an SVG element used for styling and positioning text. This filters the output to include only lines that have `tspan`, effectively narrowing the focus to lines related to text span elements.
3. **`| grep -oP '(?<=>).*?(?=<)'`**:
    
    - This command uses `grep` again with the `-oP` options:
        - `-o`: Outputs only the matching parts of the lines, rather than the entire line.
        - `-P`: Enables Perl-compatible regular expressions.
    - The regex `(?<=>).*?(?=<)` is used to match and capture everything between `>` and `<`. Specifically:
        - `(?<=>)`: A positive look behind that asserts what precedes is a `>`.
        - `.*?`: Matches any character (`.`) any number of times (`*`), but the `?` makes it non-greedy, so it captures as few characters as possible until it finds the next condition.
        - `(?=<)`: A positive lookahead that asserts what follows is a `<`.
    - This means the command extracts the text content of the `tspan` elements, omitting the tags themselves.
4. **`| tr -d "\n"`**:
    
    - The `tr` command translates or deletes characters. Here, `-d "\n"` removes all newline characters from the output, effectively concatenating all lines into a single line.
5. **`| tr -d " "`**:
    
    - This `tr` command removes all spaces from the concatenated string, producing a continuous string of characters without any spaces or newlines.

![Screenshot 2024-10-29 at 5 08 27 PM](https://github.com/user-attachments/assets/89846e38-c3d4-4dcb-8db4-dc0a748f7a2e)

### Flag
`picoCTF{3...}`
