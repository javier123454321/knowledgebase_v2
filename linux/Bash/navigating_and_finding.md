# Moving around the shell

### Basics moving
cd
your directory `.`
parent directory `..`

see items in a directory 
`$ ls`

### Finding

#### Find vs Locate
- **Locate** uses a database to look for files in the directory
- **Find** allows you to look for a file by  -name -iname -owner -size -type

#### types:

- **b** Block special device file
- **c** Character special device file
- **d** Directory
- **f** Regular file
- **l** Symbolic link

size uses +m to declare > 1mb
#### sizes:
- **b** 512-byte blocks. This is the default if no unit is specified.
- **c** Bytes.
- **w** 2-byte words.
- **k** Kilobytes (units of 1024 bytes).
- **M** Megabytes (units of 1048576 bytes).
- **G** Gigabytes (units of 1073741824 bytes).

You can chain find commands and use logical operators.

### GREP
allows you to filter the stdout by given name
