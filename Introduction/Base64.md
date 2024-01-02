# Base64
## Description
Another common encoding scheme is Base64, which allows us to represent binary data as an ASCII string using an alphabet of 64 characters. One character of a Base64 string encodes 6 binary digits (bits), and so 4 characters of Base64 encode three 8-bit bytes.

Base64 is most commonly used online, so binary data such as images can be easily included into HTML or CSS files.

Take the below hex string, decode it into bytes and then encode it into Base64.

72bca9b68fc16ac7beeb8f849dca1d8a783e8acf9679bf9269f7bf
## Hint
In Python, after importing the base64 module with import base64, you can use the base64.b64encode() function. Remember to decode the hex first as the challenge description states.
## Solution
```
import base64

flag = '72bca9b68fc16ac7beeb8f849dca1d8a783e8acf9679bf9269f7bf'

initial_output = bytes.fromhex(flag)

final_output = base64.b64encode(initial_output)

print(final_output)
```
Flag: crypto/Base+64+Encoding+is+Web+Safe/
