# The Bourne Again Shell BASH

### Redirects

#### Stdin, Stdout, Stderr

linux redirects all outputs to a file called stdout

This is a temporary file that gets printed on the command line and then destroyed. 
ls actually writes the contents of a directory to the stdout file

`>` is called a redirect, and it tells it where to put the contents that result from the program just inputed

so ls == ls > stdout
and ls > ls-output.txt just creates a new file ls-output.txt with  what would have been shown to the screen.
if you make an error like `$ ls nonexitentDirectory > ls-output.txt` the output would still be No such file or directory on the shell. That is because there was an error, so the output was not sent to stdout, but to stderr. 
Likewise stdin listens to the inputs from the keyboard. 

input is labeled as 0, output as 1, and error as 2

So to redirect the error, you use a 2 operator 
`$ ls -l /bin/usr 2> ls-error.txt` 

`$ ls -l /bin/usr > ls-output.txt 2>&1` redirects both

if you want to redirect the stderr & stdout use the `&>` signal

this redirects all to the file. 

/dev/null can be used to dump the output and discard it

set noclobber to force you to use `>|` instead of `>` in order to overwrite a file

using `$ > filename.txt` is the fastest way to empty a file.

#### redirect to Dev/null
A simple way to tell the output to bug off.

### Cat

Concattenate, output a file. 

### Pipes

Take the stdout of a previous script and put it as an output of the previous one.
However, be careful if you want to redirect the errors to a file you'd have to redirect using the 2>&1 | redirect

### Tee
takes the stdin and and inputs it to the next command. 

### Arithmetic Expressions
Take the following form `$((expression))`

i.e. `$echo $((4 + 4))` outputs $8 these can be nested `echo $(($((5+2))+3))` outputs `10`

### Brace expansion

you can use {} to make a sequence of outputs as dictated by the vlue within the braces.
`$ echo Number_{1..5}`
ouputs
`Number_1 Number_2 Number_3 Number_4 Number_5` it understands a comma separated list or a range.
{z...a} is valid as well as {001...10}

### Command Substitution
using the `$()` pattern tells the shell to do a command, it is also applicable with the \` (or backtic)
