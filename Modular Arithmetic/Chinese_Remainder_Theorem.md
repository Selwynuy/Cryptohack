# Chinese Remainder Theorem
## Description
The Chinese Remainder Theorem gives a unique solution to a set of linear congruences if their moduli are coprime.

This means, that given a set of arbitrary integers ai, and pairwise coprime integers ni, such that the following linear congruences hold:

Note "pairwise coprime integers" means that if we have a set of integers {n1, n2, ..., ni}, all pairs of integers selected from the set are coprime: gcd(ni, nj) = 1.


x ≡ a1 mod n1
x ≡ a2 mod n2
...
x ≡ an mod nn


There is a unique solution x ≡ a mod N where N = n1 * n2 * ... * nn.

In cryptography, we commonly use the Chinese Remainder Theorem to help us reduce a problem of very large integers into a set of several, easier problems.

Given the following set of linear congruences:

x ≡ 2 mod 5
x ≡ 3 mod 11
x ≡ 5 mod 17


Find the integer a such that x ≡ a mod 935
## Hint
Starting with the congruence with the largest modulus, use that for x ≡ a mod p we can write x = a + k*p for arbitrary integer k.
## Solution
Code:
```
"""
x ≡ 2 mod 5
x ≡ 3 mod 11
x ≡ 5 mod 17

Find the integer a such that x ≡ a mod 935

"""
# X = (a1M1(M1^-1) + a2M2(M2^-1) + a3M3(M3^-1)) mod M

def eua(m,mod):                                 # extended euclidian algorithm
        for i in range(mod):
                if (m*i) % mod == 1:
                        return i
        return None

a1 = 2
a2 = 3
a3 = 5

m1 = 5
m2 = 11
m3 = 17

M = m1*m2*m3                    # M = 935

M1 = M//m1                      # M1 = 187
M2 = M//m2                      # M2 = 85
M3 = M//m3                      # M3 = 55

M1_inv = eua(M1,m1)             # M1_inv = 3
M2_inv = eua(M2,m2)             # M2_inv = 7
M3_inv = eua(M3,m3)             # M3_inv = 13

x = ((a1*M1*(M1_inv)) + (a2*M2*(M2_inv)) + (a3*M3*(M3_inv)))%M
print(x)

# Since x = a mod 935 and M in our equation is already 935, we just return x
```
I created this code with the help of this YT video https://www.youtube.com/watch?v=e8DtzQkjOMQ

Flag: 872
