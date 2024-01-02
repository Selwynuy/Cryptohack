# XOR Properties
## Description
In the last challenge, you saw how XOR worked at the level of bits. In this one, we're going to cover the properties of the XOR operation and then use them to undo a chain of operations that have encrypted a flag. Gaining an intuition for how this works will help greatly when you come to attacking real cryptosystems later, especially in the block ciphers category.

There are four main properties we should consider when we solve challenges using the XOR operator

Commutative: A ⊕ B = B ⊕ A
Associative: A ⊕ (B ⊕ C) = (A ⊕ B) ⊕ C
Identity: A ⊕ 0 = A
Self-Inverse: A ⊕ A = 0

Let's break this down. Commutative means that the order of the XOR operations is not important. Associative means that a chain of operations can be carried out without order (we do not need to worry about brackets). The identity is 0, so XOR with 0 "does nothing", and lastly something XOR'd with itself returns zero.

Let's put this into practice! Below is a series of outputs where three random keys have been XOR'd together and with the flag. Use the above properties to undo the encryption in the final line to obtain the flag.

KEY1 = a6c8b6733c9b22de7bc0253266a3867df55acde8635e19c73313
KEY2 ^ KEY1 = 37dcb292030faa90d07eec17e3b1c6d8daf94c35d4c9191a5e1e
KEY2 ^ KEY3 = c1545756687e7573db23aa1c3452a098b71a7fbf0fddddde5fc1
FLAG ^ KEY1 ^ KEY3 ^ KEY2 = 04ee9855208a2cd59091d04767ae47963170d1660df7f56f5faf
## Hint
Before you XOR these objects, be sure to decode from hex to bytes.
## Solution
```
from pwn import *
from Crypto.Util.number import *
"""
KEY1 = a6c8b6733c9b22de7bc0253266a3867df55acde8635e19c73313
KEY2 ^ KEY1 = 37dcb292030faa90d07eec17e3b1c6d8daf94c35d4c9191a5e1e
KEY2 ^ KEY3 = c1545756687e7573db23aa1c3452a098b71a7fbf0fddddde5fc1
FLAG ^ KEY1 ^ KEY3 ^ KEY2 = 04ee9855208a2cd59091d04767ae47963170d1660df7f56f5faf
"""

key1 = bytes.fromhex('a6c8b6733c9b22de7bc0253266a3867df55acde8635e19c73313')
key1 = bytes_to_long(key1)

#key1 = 268011609358571820305085369857896955256986936039734864838603539

key21 = bytes.fromhex('37dcb292030faa90d07eec17e3b1c6d8daf94c35d4c9191a5e1e')
key21 = bytes_to_long(key21)

#key21 = 89766933348497060915487216344088108257338583381171202642566686

key23 = bytes.fromhex('c1545756687e7573db23aa1c3452a098b71a7fbf0fddddde5fc1')
key23 = bytes_to_long(key23)

#key23 = 310668460597809861169401602527868010306079563156612591698993089

keyf132 = bytes.fromhex('04ee9855208a2cd59091d04767ae47963170d1660df7f56f5faf')
keyf132 = bytes_to_long(keyf132)

#keyf132 = 7925437572770502412911705592931284224290531909827285778128815

#let's first try to get key2
key2 = key1^key21

#key2 = 233131678106482661238672080114331736309154844705032145066618125


#then let's try to get key3
key3 = key2^key23

#key3 = 128958830766673989760840084136775616066553869841642599800320716

#now that we have all the values key1, key2, and key3, we can get the flag

flag = key1^key2^key3^keyf132

#flag = 159805433661873705497880084580614789222721324997857681199215485

print(long_to_bytes(flag))
```
Flag: crypto{x0r_i5_ass0c1at1v3}
