# Regular Expressions

    grep -i     # case insensitive
    grep -e     # use extended regex's

man 7 regex

    .           # a single character
    ^           # beginning of line
    $           # end of line
    [abc]       # one char of set
    [^abc]      # not one of the chars in the set
    *           # 0 or more of the preceding char
    abc|def     # or

## regex tools

### sed

    cat passwd | sec -n '/nologin$/p'

### egrep

    egrep 'bash$' passwd
    egrep -c 'bash$' passwd     # get count of matches

### fgrep
Searches based on strings rather than patterns  
Equivalent to `grep -F  
can use a file which contains the strings to search for

    fgrep -f strings passwd

    