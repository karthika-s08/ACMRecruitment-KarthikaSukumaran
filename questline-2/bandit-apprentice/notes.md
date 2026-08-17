# level 0
commands used= ssh

# level 0-1
commands used= ls, cat
password found

# level 1-2
commands used= ls, cat ./
password found
normal cat cannot find file. So ./ is used.

# level 2-3
commands used= ls, cat "./"
password found
"" is used because filename contains spaces

# level 3-4
commands used= ls -a, cd, cat
password found
ls -a is used to find hidden files

# level 4-5
commands used= ls -h, cd, ls, file ./*, cat
password found
ls -h is used to find human readable files. files ./* is used to find all the files in the present directory

# level 5-6
commands used= ls, cd, find
password found
find . -type f  -size 1033c ! -executable is used. find is used to check current directery. -type f is used to find regular files. -size 1033c translates to 1033bytes. ! -executable means not executable.
