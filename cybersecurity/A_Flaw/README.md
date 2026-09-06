#A_Flaw

file chal_rev2 to find the file type.

chmod +x "./chal_rev2" to make the file executable.
when typed ./chal_rev2 to execute, it asked for authentication token.
When put AAA as a trial token it showed invalid token key with 0x11223344
Try adjusting payload offset = how far my input has to go before it reaches the authentication key

## Finding offset
python3 -c 'print("A"*40)' | grep -i token
used 40 as an initial value. no change in invalid token key.
used 44 and saw a changed in invlalid token key.
with enough A's(48), I got 0x41414141, which showed that A's were overwriting the authentication value.

## Finding relevent info
objdump -d -M intel "./chal_rev2"
Inspected compiled binaries(showed whats inside) to disassemble and show assembly using intel syntax.

Find call with <read@plt>
got cmp 0x44444444 and jne below. `cmp` compares the values and `jne` means jump if not equal.
0x41=A
0x44=D

The 44 A's are considered padding. Why?

Before call <read@plt> there is lea rax,[rbp-0x30] and after there is mov eax,DWORD PTR [rbp-0x4]
So since 0x30=48 adn 0x4=4
48-4=44 A's as padding.
then DDDD because 0x44444444 is the value the program checks for, and D = 0x44

Got the key with the command 
python3 -c 'print("A"*44 + "DDDD")' | ./"chal_rev2"
