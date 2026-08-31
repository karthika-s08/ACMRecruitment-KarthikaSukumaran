## FINDING THE FILE TYPE

Downloaded the file in kali and opened terminal. 

Used ls and cd to find the file txtpyc
cat displayed encrypted file.

file txtpyc showed that it is a POSIX tar archive.
Used tar -xf to extract the tar archive

found a bzip2 compressed file and decompressed it with bzip2 -d
found the gzip compressed file and decompressed with gzip -d 
renamed files with appropriate extensions.

Found a zip archive file. Used unzip to to decompress the file.
found two files challenge.tar and .heheh

decompressed challenge.tar with tar.xf, bzip2 -d and gzip -d 
The resulting ASCII text contained 'sorry wrong way'

decompressed .heheh [first renamed .heheh to heheh]
Eventually obtained an ASCII text file named hidden_file containing the flag.
