Created folder permission-auditor
created file permission_auditor.sh

# IMP COMMANDS
find= searches through diretories
find . =searches in current file
-type f= find regular files
-perm 777=to find 777 permission files
-user root= to find files owned by root
-perm -4000= to find files with SUID bits. 4000 is the SUID bit. - means the file must have this bit set
ls -la=used to find all files
cat = used to open file contents

# MAKING FILES
mkdir = creates directories
touch - creates files




[#!/bin/bash]
This is called a shebang. helps to choose bash to run the script

[DIRECTORY="$1"]
assigns $1 as the directory variable
IMP NOT= There should be no spaces between '=' and '$'

[echo "Scanning directory: $DIRECTORY"]
prints the directory name

[echo "Files with 777 permissions:"
find "$DIRECTORY" -type f -perm 777]
This to find files with 777 permission.

777= owner, group other. usually of the numbers 4,3,1. Read write execute. 

[echo "Files owned by root:"
find "$DIRECTORY" -type f -user root]
Finds files owned by root

Root=

[echo "Files with SUID bits:"
find "$DIRECTORY" -type f -perm -4000]
find files with SUID bits














