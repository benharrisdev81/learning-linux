# Week 3: File and Directory Management

## Learn: Advanced file operations (`find`, `grep`, `locate`, `du`, `df`, `ln`).

### `find`

The "Linux Command Line" book describes `find` as "finding files the hard way." It searches specified directories and
their subdirectories for files based on a variety of attributes. The attributes are options, tests, and actions. 

#### Finding files by type

| File Type | Description                   |
|:----------|:------------------------------|
| b         | Block special device file     |
| c         | Character special device file |
| d         | Directory                     |
| f         | Regular file                  |
| l         | Symbolic link                 |

> To find all directories and subdirectories in your home directory: `find ~ -type d`

> To find all files in your home directory and subdirectories: `find ~ -type f`

#### Finding files by name

> To find every .txt file on the computer: `find / -type f -name *.txt`

#### Finding files by size

| Character | Unit                                                         |
|:----------|:-------------------------------------------------------------|
| b         | 512-byte blocks. This is the default if no unit is specified |
| c         | Bytes                                                        |
| w         | 2-byte words                                                 |
| k         | Kilobytes (units of 1,024 bytes)                             |
| M         | Megabytes (units of 1,048,576 bytes)                         |
| G         | Gigabytes (units of 1,073,741,824 bytes)                     |

> To find every .JPG file on the computer over a certain size: `find / -type f -name *.JPG -size +1M` 

#### Finding files through tests

| Test             | Description                                                                                                    |
|:-----------------|:---------------------------------------------------------------------------------------------------------------|
| `-cmin n`        | Match files or directories whose content or attributes were last modified exactly _n_ minutes ago              |
| `-cnewer file`   | Match files or directories who contents or attributes were last modified more recently than those of _file_    |
| `-ctime n`       | Match files or directories who contents or attributes were last modified _n*24_ hours ago                      |
| `-empty`         | Match empty files and directories                                                                              |
| `-group name`    | Matches files or directories belonging to group name (group name of numeric group ID)                          |
| `-iname pattern` | Like the `-name` test but case-sensitive                                                                       |
| `-inum n`        | Match files with inode number _n_. This is helpful for finding all of the hard links to a particular hard node |
| `-mmin n`        | Match files or directories whose contents were last modified _n_ minutes ago                                   |
| `-mtime n`       | Match files or directories whose contents were last modified _n*24_ hours ago.                                 |
| `-name pattern`  | Match files and directories with the specified wildcard _pattern_.                                             |
| `-newer file`    | Match files are directories whose contents were modified more recently than the specified _file_.              |
| `-nouser`        | Match files and directories that do not belong to a valid user. (deleted accounts, attackers, etc.)            |
| `-nogroup`       | Match files and directories that do not belong to a valid group.                                               |
| `-perm mode`     | Match files or directories that have permissions set to the specified _mode_ (either octal or symbolic)        |

### `grep`

`grep` is a powerful program used to find text patterns within files. It is used like this:

`grep pattern filename`

It can become very complex, as `grep` accepts regular expressions for the pattern argument. Here's a great example:

```bash
echo "This is a new file." newfile
grep new newfile
```

Suppose you have a directory `~/diary/` where you keep journal entries and you want to know how many entries contain
the word "anxiety."

`find ~/diary/* -type f | grep -r "anxiety"`

The `-r` argument recurses through specified files and/or directories.

### `locate`



### `du`



### `df`



### `ln`



## Practice: Searching for files, checking disk usage, creating and managing hard and symbolic links.

## Exercise: Find and list files by size, type, or modification date, and practice linking files.