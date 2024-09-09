# Week 2: Understanding and Using Shell

## Learn: Basics of the shell (bash), environment variables, using `.bashrc` or `.zshrc`.

### Environment Variables

The shell stores two basic types of data in the environment:
 * shell variables - placed there by bash
 * environment variables - everything else

You can see all of the variables set for your current shell by typing `set`. A subset of your local variables is referred
to as environment variables. Environment variables are variables that are exported to any new shells opened from the
current shell. Type `env` to see environment variables. `alias` displays a list of aliases.

### Using `.bashrc` or `.zshrc`

The `ps` command shows information about processes currently running, which includes the terminal (bash, zsh, etc.)
Once learning which prompt you are using (bash or zsh or something else), then you can know which file (`.bashrc` or
`.zshrc`) contains the shell customization. You can also `echo $PS1` to display the prompt string.

## Practice: Customizing your shell prompt, creating and using aliases, and environment variables.

| Sequence | Value Displayed                                              |
|:---------|:-------------------------------------------------------------|
| `\a`     | ASCII bell                                                   |
| `\d`     | Current date in day, month, date format                      |
| `\h`     | Hostname of the local machine minus the trailing domain name |
| `\H`     | Full hostname                                                |
| `\j`     | Number of jobs running in the current shell session          |
| `\l`     | Name of the current terminal device                          |
| `\n`     | A newline character                                          |
| `\r`     | A carriage return                                            |
| `\s`     | Name of the shell program                                    |
| `\t`     | Current time in 24-hour hours:minutes:seconds format         |
| `\T`     | Current time in 12-hour format                               |
| `\@`     | Current time in 12-hour AM/PM format                         |
| `\A`     | Current time in 24-hour hours:minutes format                 |
| `\u`     | Username of the current user                                 |
| `\v`     | Version number of the shell                                  |
| `\V`     | Version and release numbers of the shell                     |
| `\w`     | Name of the current working directory                        |
| `\W`     | Last part of the current working directory name              |
| `\!`     | History number of the current command                        |
| `\#`     | Number of commands entered during this shell session         |
| `\$`     | Displays the $ character unless we have superuser (# instead)|
| `\[`     | Signals the start of a series of non-printable characters    |
| `\]`     | Signals the end of a series of non-printable characters      |

| Sequence     | Text Color | Sequence     | Text Color  |
|:-------------|:-----------|:-------------|:------------|
| `\033[0;30m` | Black      | `\033[1;30m` | Dark gray   |
| `\033[0;31m` | Red        | `\033[1;31m` | Light red   |
| `\033[0;32m` | Green      | `\033[1;32m` | Light green |
| `\033[0;33m` | Brown      | `\033[1;33m` | Light brown |
| `\033[0;34m` | Blue       | `\033[1;34m` | Light blue  |
| `\033[0;35m` | Purple     | `\033[1;35m` | Light purple|
| `\033[0;36m` | Cyan       | `\033[1;36m` | Light cyan  |
| `\033[0;37m` | Light gray | `\033[1;37m` | White       |

| Sequence      | Background Color | Sequence      | Background Color |
|:--------------|:-----------------|:--------------|:-----------------|
| `\033[0;40m`  | Black            | `\033[1;44m`  | Blue             |
| `\033[0;41m`  | Red              | `\033[0;45m`  | Purple           |
| `\033[0;42m`  | Green            | `\033[0;46m`  | Cyan             |
| `\033[0;43m`  | Brown            | `\033[0;47m`  | Light gray       |

You can find a massive list of special characters [here](https://en.wikipedia.org/wiki/List_of_Unicode_characters).
Use the escape codes and special characters to customize your prompt within the appropriate file (`.bashrc` or `.zshrc`).
For example: `PS1="$(echo -e '\u22D9') "`. `source ~/.bashrc` resets your prompt to whatever is stored in `.bashrc`.

## Exercise: Create custom aliases for commonly used commands and set environment variables you might need.

The `.bashrc` file includes aliases as well. I have entered the following:

`alias lr='ls -laAhF'`

## Open Questions
- [x] Using special characters within the custom prompt didn't work for me. Why?
- [ ] How can I add other things, like repo name, git branch, etc.?
- [ ] What sorts of things would require environment variables?