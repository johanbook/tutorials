# Encryption

Encryption is the act of obscuring data such that only a receiving part can
properly understand it.

Encryption can be done using keys. There is symmetric encryption (same key for
encryption and decryption) and asymmetric encryption (different key for
encryption and decryption). For asymmetric encryption the key pair is called
private and public key.

## Digital Signature

One can create a signature by encrypting a hash with a private key. The
signature can then be decrypted with corresponding public key and hash used to
verify whatever was signed. If something is signed the receiving part can be
confirm the message has not been tampered with and is in fact from the sender.

Such a signature can be juridically binding.

### Certificate

Contains time of validity, purpose, public key of entity and encryption method.

There are different levels of certificates. Level 1 which is only verification
that the one is owning the domain, level 2 which requires proof of owning brand
and level 3 where CEO have identified in person.

## Encryption Algorithms

Here are some encryption algorithms.

### AES

Advanced Encryption Standard (AES) is an symmetric key algorithm. It is a block
cipher.

### RSA

RSA is a asymmetric key algorithm. It relies on

```
(m^e)^d = (m^d)^e = m (mod n)
```

for some specific large integers `e`, `d` and `n`. Even though knowing `e` it is
difficult to find `d`. The public key is `(e, n)` while the private key is
`(d, n)`.

#### Key Generation

1. Choose two distinct large prime numbers `p` and `q`.
2. Compute the modulus `n = pq`.
3. Some step I do not understand yet.
4. Select value for `e`. It is often chosen to be around `2^16 + 1`. Small
   values for `e` can be insecure.
5. Calculate `d` as the inverse of `e` somehow.

### One Time Pad

One Time Pad (OTP) is an uncrackable symmetric key algorithm. The encryption key
must be generated anew for each new message and should be at least as large as
the message.

### Caesar Cipher

A Caesar Cipher is a substitution cipher where one shifts letters. One example
is ROT13 where one shifts 13 letters. ROT13 is its own inverse (due to the
English alphabet has 26 letters). Note that all ROT ciphers are their own
inverse.
