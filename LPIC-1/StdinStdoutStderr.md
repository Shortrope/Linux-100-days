# STDOUT STDIN STDERR

0   stdin  
1   stdout  
2   stderr  

    2> error.lob
    2>&1 > other.log

## tee
Reads data from stdin and writes to stdout and files  
Can view output at various stages of a long chain of commands  

    cmd | tee file | cmd | tee file2 | cmd | tee file3
    ls -d /usr/share/doc/lib[xX]* |tee lib-docs.txt

## xargs
accepst input from stdin.  
Commonly used with the `find` command  

    find ./test/ -empty -exec rm {} \;
    find ./test/ -empty | xargs rm -f
    find / -xdev -size +70M | xargs ls -alh

`xargs` can operate on all args at one time  
`-exec` works on each item individually

    grep -l "junk" test/file_* | xargs -I {} mv {} test/bak/


