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

On most Linux systems, the `updatedb` command runs once per day to gather the names of all files onto a database. The
`locate` command does not search the entire live file system like `find` does, but rather queries the database containing
the list of files.

> ⚠️ Ubuntu server, which I am running, does not come preinstalled with a `locate` or `updatedb` command

### `du`

`du` stands for "disk usage." Use the `du` command to list all directories below the current director to see how much
space is consumed by each directory. Interesting arguments include but are not limited to:

| Argument | Description                                                   |
|:---------|:--------------------------------------------------------------|
| -h       | Print size in human-readable format                           |
| -L       | Follow symbolic links and measure the files they point to     |
| -c       | Print a total in the last line                                |
| -s       | Print total sizes only and not the sizes of each subdirectory |

### `df`

`df` stands for "disk free," and shows the size, used space, and free space of a given disk partition.

### `ln`

The `ln` command is used to create either hard or symbolic links. 
To create a hard link:
> ln _file link_

To create a symbolic link:
> ln -s _item link_

#### Hard Links

Hard links are the original Unix way of creating links, compared to symbolic links, which are more modern. By default,
every file has a single hard link that gives the file its name. When we create a hard link, we create an additional
directory entry for a file. Hard links have two important limitations:
1. A hard link cannot reference a file outside its own file system (read: disk or partition).
2. A hard link may not reference a directory.

A hard link is indistinguishable from the file itself. A directory listing (`ls`) will yield no specific indication of
the link. When a hard link is deleted, the link is removed but the contents of the file itself will remain until all
links to the file are deleted.

#### Symbolic Links

Symbolic links were created to overcome the limitations of hard links. They work by creating a special type of file
that contains a text pointer to the referenced file or directory. In this regard, they operate much the same way as a
Windows shortcut.

## Practice: Searching for files, checking disk usage, creating and managing hard and symbolic links.

One things I learned when creating links is that this doesn't work:

``` bash
~/playground $ ln -s ./test1/myfile ./test2/sym-myfile
```

Instead, you must use the whole path like this:

```bash
~/playground $ ln -s /playground/test1/myfile /playground/test2/sym-myfile
```

## Exercise: Find and list files by size, type, or modification date, and practice linking files.