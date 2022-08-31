# Basics of configurations #

## Configurability
The less dependen on "magic" that you are the more your skills can translate to other systems.

Fancy vimrcs don't translate to different systems. (especially true for plugins)

[[Vim]]'s greatest propsition is that you have access to it everywhere
If you need it to do something fancy, you can throw a script
```(try :.! date)```
or in Normal Mode, type ```'!! date'```

>output:
>Thu, May 14, 2020  7:24:00 PM

You can combine vi with your shell, and that is a great reason to use vi. 

### The Shell
Bash is the language of linux (and comes default with most - really all - distributions)

the .bashrc is loaded on the default and sometimes it is not set up to be editable. You can use the .bash_aliases file as a replacement for your .bashrc.

Aliases don't make commands, they replace the characters that you are typing with their alias.
if you want to disable the alias, you just write '\' before the word you are typing.

set-o allows you to kind of use vi to browse your history
