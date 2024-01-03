# Modular Arithmetic 2
## Description
We'll pick up from the last challenge and imagine we've picked a modulus p, and we will restrict ourselves to the case when p is prime.

The integers modulo p define a field, denoted Fp.

A finite field Fp is the set of integers {0,1,...,p-1}, and under both addition and multiplication there is an inverse element b for every element a in the set, such that a + b = 0 and a * b = 1.

Lets say we pick p = 17. Calculate 317 mod 17. Now do the same but with 517 mod 17.

What would you expect to get for 716 mod 17? Try calculating that.

This interesting fact is known as Fermat's little theorem. We'll be needing this (and its generalisations) when we look at RSA cryptography.

Now take the prime p = 65537. Calculate 27324678765465536 mod 65537.

## Hint
If the modulus is not prime, the set of integers modulo n define a ring.
Note that the identity element for addition and multiplication is different! This is because the identity when acted with the operator should do nothing: a + 0 = a and a * 1 = a.
## Solution
```
n = 17
print("a = ",pow(3,16,n))      # 3
print("b = ",pow(5,17,n))      # 5
print("c = ",pow(7,16,n))      # 1

n = 65537
print("d = ",pow(273246787654,65536,n))         # 1
```
The lesson to get here is a**(n-1) mod n is equal to 1 and a**n mod n is equal to a.
Flag: 1
