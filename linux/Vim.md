# Vim

vim is a text editor that helps you edit files faster.
DuckDuckGo: search vim cheatsheet

### Exiting vim
(in Normal Mode)
without saving
- :q! 
- ZQ

with saving
- :wq 
- ZZ

### Insert mode 
- i to insert at the beggining of the character
- I to the beggining of line
I only adds before the 1st non " " character in a line
       test 

### Append
- a insert after current character
- A to append to the current line

### gg & G
- gg beggining of file
- G end of file
- `[[gg]]` or `[[G]]` go to line number (i.e. 13gg or 13G)

### running bash scripts in vim
:.! for running a script
!! in NORMAL mode
You can run any bash script in vim!!
i.e. `!! date`
> ` Thu, May 21, 2020 11:35:24 AM `

It replaces the current line with stdout of the bash terminal

### deleting (actually cutting)
- dw - delete word (delete to the end of the current word)
- de - delete end of word (leaves the trailing space)
- diw - delete inner work (delete current word regardless of where you are on it)
- d$ = D - delete to the end of the line
- d0 

### Operators
#### Common Operators
1. delete - d
1. change - c
1. yank - y
1. paste - p
1. format - =
1. toggle cAsE - ~

vim uses a syntaxt of operator then noun
delete inner word = diw
change inner word = ciw


### Finding 
- search forward = /
- search Backward = ?

n is to go to next instance and N is for previous instance

find and replace each instance
```
/ replace <enter>
ciw replacce
n. //finds next instance and repeats operation
```

replacce
replacce
