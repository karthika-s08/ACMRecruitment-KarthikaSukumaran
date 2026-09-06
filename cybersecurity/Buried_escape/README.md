# BURIED_ESCAPE

file release.zip to find it is a zip.archive.
used unzip to extract the archive, which created the release/ directory.

cd release/ and then ls to find evidence.png
But when used file on evidence.png, showed it was a JPEG

used xxd evidence.png | head and xxd evidence.png | tail to inspect the hexadecimal contents at the beginning and end of the file.

grep -aob PK evidence.png used. PK is commonly seen in zip files. 
found 6552: PK

### Investigating byte 6552
xxd -s 6552 -l 32 evidence.png

used tail -c +6553 evidence.png > hidden.zip to extract the data from that point into hidden.zip.

### hidden.zip
file hidden.zip showed it is a zip archive. 
unzip 
found it needed password.

### finding password
which zip2john to file if it exists in Kali
zip2john hidden.zip > ziphash.txt to save info in that file
john ziphash.txt was used to crack the ZIP password.

used the recovered password with unzip hidden.zip to extract flag.pdf.

### mutool
ls to see flag.pdf
used the recovered password with unzip hidden.zip to extract flag.pdf.
used mutool info flag.pdf to check structure of pdf file
and used mutool draw -F txt flag.pdf to extract text from pdf and display in terminal
