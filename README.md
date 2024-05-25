# Js - CODING PRACTICE
________________________________________________________________________________________________________________________________
## 1)
```
var price=100
var product ="icecream"
var tax=10
var tot=price+tax
console.log(tot)
console.log(product)
```
## OUTPUT
```
Output:

110
icecream
```
_________________________________________________________________________

## 2)
```
var fruit="pineapple"
var count=5
var price=70
var tot = count*price
console.log(fruit)
console.log(tot)
```
## OUTPUT
```
Output:

pineapple
350
```
_________________________________________________________________________
## 3)
```
var a=10
var b="ashmi"
var c=null
var d=true
var e
console.log(a)
console.log(b)
console.log(c)
console.log(d)
console.log(e)
```
## OUTPUT
```
Output:

10
ashmi
null
true
undefined
```


```
# Python for RSA asymmetric cryptographic algorithm.
# For demonstration, values are
# relatively small compared to practical application
import math


def gcd(a, h):
	temp = 0
	while(1):
		temp = a % h
		if (temp == 0):
			return h
		a = h
		h = temp


p = 3
q = 7
n = p*q
e = 2
phi = (p-1)*(q-1)

while (e < phi):

	# e must be co-prime to phi and
	# smaller than phi.
	if(gcd(e, phi) == 1):
		break
	else:
		e = e+1

# Private key (d stands for decrypt)
# choosing d such that it satisfies
# d*e = 1 + k * totient

k = 2
d = (1 + (k*phi))/e

# Message to be encrypted
msg = 12.0

print("Message data = ", msg)

# Encryption c = (msg ^ e) % n
c = pow(msg, e)
c = math.fmod(c, n)
print("Encrypted data = ", c)

# Decryption m = (c ^ d) % n
m = pow(c, d)
m = math.fmod(m, n)
print("Original Message Sent = ", m)
```
```
[22:50, 24/05/2024] Ilaya👻: import string
import itertools

def vigenere_encrypt(plaintext, key):
    ciphertext = []
    key_chars = [c.upper() for c in key]
    key_len = len(key_chars)
    text_len = len(plaintext)
    key_index = 0

    for i in range(text_len):
        if plaintext[i].isalpha():
            shift = (ord(key_chars[key_index]) - ord('A'))
            encrypted_char = chr((ord(plaintext[i].upper()) - ord('A') + shift) % 26 + ord('A'))
            ciphertext.append(encrypted_char)
            key_index = (key_index + 1) % key_len
        else:
            ciphertext.append(plaintext[i])

    return ''.join(ciphertext)

def vigenere_decrypt(ciphertext, key):
    plaintext = []
    key_chars = [c.upper() for c in key]
    key_len = len(key_chars)
    text_len = len(ciph…
[22:50, 24/05/2024] Ilaya👻: def rail_fence_encrypt(plaintext, rails):
    ciphertext = [''] * len(plaintext)
    rail_fence = [[''] * len(plaintext) for _ in range(rails)]

    dir_down = False
    row = 0

    for i, char in enumerate(plaintext):
        if row == 0 or row == rails - 1:
            dir_down = not dir_down
        rail_fence[row][i] = char
        row += 1 if dir_down else -1

    k = 0
    for i in range(rails):
        for j in range(len(plaintext)):
            if rail_fence[i][j] != '':
                ciphertext[k] = rail_fence[i][j]
                k += 1

    return ''.join(ciphertext)

def rail_fence_decrypt(ciphertext, rails):
    plaintext = [''] * len(ciphertext)
    rail_fence = [[''] * len(ciphertext) for _ in range(rails)]

    dir_down = None
    row = 0

    for i in range(len(ciphertext)):
        if row == 0:
            dir_down = True
        if row == rails - 1:
            dir_down = False

        rail_fence[row][i] = '*'
        row += 1 if dir_down else -1

    index = 0
    for i in range(rails):
        for j in range(len(ciphertext)):
            if rail_fence[i][j] == '*' and index < len(ciphertext):
                rail_fence[i][j] = ciphertext[index]
                index += 1

    row = 0
    dir_down = None

    for i in range(len(ciphertext)):
        if row == 0:
            dir_down = True
        if row == rails - 1:
            dir_down = False

        if rail_fence[row][i] != '*':
            plaintext[i] = rail_fence[row][i]

        row += 1 if dir_down else -1

    return ''.join(plaintext)

def main():
    print("Choose an option:")
    print("1. Encryption")
    print("2. Decryption")
    choice = int(input("Enter your choice: "))

    text = input("Enter the text: ").strip()
    rails = int(input("Enter the number of rails: "))

    if choice == 1:
        ciphertext = rail_fence_encrypt(text, rails)
        print("Encrypted Text:", ciphertext)
    elif choice == 2:
        decrypted_text = rail_fence_decrypt(text, rails)
        print("Decrypted Text:", decrypted_text)
    else:
        print("Invalid choice.")

if _name_ == "_main_":
    main()
```
