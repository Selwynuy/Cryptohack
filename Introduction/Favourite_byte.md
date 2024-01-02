# Favourite byte
## Description
For the next few challenges, you'll use what you've just learned to solve some more XOR puzzles.

I've hidden some data using XOR with a single byte, but that byte is a secret. Don't forget to decode from hex first.

73626960647f6b206821204f21254f7d694f7624662065622127234f726927756d
## Solution
```
from pwn import xor
data = bytes.fromhex('73626960647f6b206821204f21254f7d694f7624662065622127234f726927756d')
# data = b"sbi`d\x7fk h! O!%O}iOv$f eb!'#Ori'um"

for char in range(256):
        result = xor(char,data)
        print(result)
```
There will be 256 results, just scroll down or up to find the expected flag

Flag: crypto{0x10_15_my_f4v0ur173_by7e}
