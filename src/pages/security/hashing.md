# Hashing

A hash function is a function `f: A -> B` which is one-to-one and creates a
chaotic system There are several types of hashing algorithms, each suitable for
different use-cases. For example, for checking a password hash one would want a
slow and cryptographically secure algorithm while a faster one can be used for
e.g. checksums.

One can increase work factor if computational hardware improves.

## SHA

## MD

## bcrypt

bcrypt is a password hashing algorithm. It is based on the bluefish cipher and
incorporates a work factor. This makes it more difficult to brute-force using
e.g. parellelized attacks. It also incorporates salt by default.

## scrypt

scrypt is a hashing algorithm.

## argon2

argon2 is a hashing algorithm.
