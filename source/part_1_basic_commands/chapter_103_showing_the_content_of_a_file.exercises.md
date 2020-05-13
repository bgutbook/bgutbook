{EXERCISE BEGIN 01}
Print the content of the file `examples.txt` numbering lines.
{EXERCISE SOLUTION 01}
According to the man page of `cat` the `-n` option numbers all output lines. So

``` sh
$ cat -n examples.txt
     1  dog
     2  cat
     3  elephant
     4  ostrich
     5  Dug the Dog
[...]
```

gives the desired result.
{EXERCISE END 01}

{EXERCISE BEGIN 02}
Check if the file `examples.txt` contains spaces at the end of any line.
{EXERCISE SOLUTION 02}
According to the man page of `cat` the `-E` option displays `$` at the end of each line. So

``` sh
$ cat -E examples.txt
dog$
cat$
elephant$
ostrich$
Dug the Dog$
[...]
```

shows you that each line terminates with a `$` immediately after the text, so there are no nasty "invisible" spaces. Later in the book we will learn how to check this without having to manually look at each line.
{EXERCISE END 02}
