# You either know, XOR you don't
## Description
I've encrypted the flag with my secret key, you'll never be able to guess it.
0e0b213f26041e480b26217f27342e175d0e070a3c5b103e2526217f27342e175d0e077e263451150104
## Hint
Remember the flag format and how it might help you in this challenge!
## Solution
```
from pwn import xor

data = bytes.fromhex('0e0b213f26041e480b26217f27342e175d0e070a3c5b103e2526217f27342e175d0e077e263451150104')
print(xor(b'crypto{},data))
# b'myXORke5hTX\x0fS[Uj>|~zH4kCFTX\x0fS[Uj>|~\x0eR[*hbv'

# we notice the first 7 characters 'myXORke' which corresponds to the first 7 characters 'crypto{'
# we then complete the key into 'myXORkey'

print(xor(b'myXORkey',data))
```
Flag: crypto{1f_y0u_Kn0w_En0uGH_y0u_Kn0w_1t_4ll}
