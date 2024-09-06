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

| Test           | Description |
|:---------------|:------------|
| `-cmin n`      | Match files or directories whose content or attributes were last modified exactly _n_ minutes ago |
| `-cnewer file` | Match files or directories who contents or attributes were last modified more recently than those of _file_ |
| `-ctime n`     | Match files or directories who contents or attributes were last modified _n*24_ hours ago |

### `grep`



### `locate`



### `du`



### `df`



### `ln`



## Practice: Searching for files, checking disk usage, creating and managing hard and symbolic links.

## Exercise: Find and list files by size, type, or modification date, and practice linking files.