# Text files and Text Streams

    zcat        # view gzip files
    bzcat       # view bzip2 files
    xzcat       # view XZ compessed files

## file statics

    nl
    nl -b a     # number all lines including blank lines
    wc          # word count
    wc -l       # line count
    wc -w       # word count
    wc -c       # char or byte count
    
    od          # octal dump. prints out a file in octal or other format
    od -c       # shows char format - new lines \n
    od -a       # ascii format - new lines: 'nl', spaces 'sp'

## Message Digests
Hashed value of a file (finger print)

    md5sum
    sha256sum
    sha512sum

    md5sum -c       # check.. has it changed

# Text manipulation

# Sort
Sort does not change the contents of the file

    sort file.txt               # sorts on first char/column
    sort -n file.txt            # sorts numeric
    sort -t "," -k2 file.txt    # -t delimiter, -k column number
    sort -u file.txt            # unique lines

# Uniq
Displays unique lines of a file.  Unique consecutive lines

# tr   - translate

cat file.txt | tr ',' ':'       # rplaces , with :
cat file.txt | tr -d ','        # deletes comma's
cat file.txt | tr 'A-Z' 'a-z'   # Replaces all uppercase with lowercase

# cut

    cut -d',' -f2,3       # -d delimiter ','  -f field 2 and 3

# paste
Combines two files in parallel

    paste file1 file2
    paste -d ',' file1 file2        # delimit w a ','
    paste -d ',' -s file1 file2     # -s serial

# sed  stream editor
Know basic replacement  

    sed 's/term/replacement/g' file.txt         # this does not change the file
    sed 's/term/replacement/g' file.txt > file2.txt
    sed -i 's/term/replacement/g' file.txt      # -i make the changes in the file

# split
Splits a file into smaller files: xaa, xab, xac, xa...

    split -b 100 file           # split into 100 byte files: xaa xab xac
    split -b 100k file          # or 100M or 100G
    split -d -n2 --verbose file # -d use digit file names. -n2 number of files to create