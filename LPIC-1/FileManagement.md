# File Management

    touch -m    # modify timestamp
    file        # get file type

# Directories

    cd -        # returns to the previous dirctory 

# find
find searches the file system.. high cpu and disk io  

    find ./ -name my.sh         # recursively seaches for the file
    find / -name passwd
    find ./ -ctime 1            # files that have been changed in the last 24h period
    find ./ -atime 2            # files that have been accessed in the last 48h 
    find ./ -newer myfile       # files newer than myfile as a reference
    find ./ -empty
    find ./ -empty -type f      # -type f = file, d = directory

## find w -exec
Execute a command on the findings  

    find ./ -empty -type f -exec rm -f {} \;    # run 'rm -f' on each found file

    

# Compression

    dd if=infile of=outputfile
    dd if=/dev/vda of=/tmp/mbr.img bs=512 count=1
    dd if=/dev/urandom of=myfile bs=1024 count=10

## tar
Wraps files and folders into an archive file  
No compression

    tar -cf bu.tar mydir        # -c create, -f out file
    tar -tf bu.tar              # list files in the tarball
    tar -xf bu.tar              # extract the files from the tarball

    tar -czf bu.tar.gz mydir         # -z  use gzip com
    tar -czf bu.tgz mydir            # alternate name extention
    tar -cjf bu.tar.bz2 mydir        # -j  use bzip2 com

    tar -xzf bu.tar.gz          # -x  extract 
    tar -xvjf bu.tar.gz         # -v  verbose 

## gzip, bzip2, 

    gzip file               # replaces the orig file w file-name.gz
    gunzip file.gz

    bzip2 file
    bunzip2 file.bz2

    xz file
    unxz file.xz





