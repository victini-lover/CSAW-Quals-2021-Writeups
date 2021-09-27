# Forgery
Category: crypto
Points: 405
Solves: 127

## Description
Felicity and Cisco would like to hire you as an intern for a new security company that they are forming. They have given you a black box signature verification system to test out and see if you can forge a signature. Forge it and you will get a passphrase to be hired!

## Notes
This challenge was inspired by the Cyber Apocalypse 2021 CTF hosted by Hack The Box.

The goal of this challenge was to have people learn about how improper implementation could easily break a signing system.

## Flag
flag{7h3_4rr0wv3r53_15_4w350M3!}

## Solution
This an ElGamal signature scheme. The issue is that the message needs to be hashed before it is signed using this system. Unfornuately, that was not done in this case. Also, another mistake made is that a `MASK` is applied to make the signature a certain size. But, the `MASK` is applied only after the checking the contents of the message. Therefore, you can place your message in the parts that will be masked out.

Therefore, you can do a one-parameter existential forgery for the given public key and get past the checking system. Usually, in one-parameter existential forgery, the message is pre-determined based on your calculations needed (see `https://en.wikipedia.org/wiki/ElGamal_signature_scheme#Existential_forgery` for the calculations). But, becuase of the `MASK`, it is easier to fool the system.

After submitting a forged signature, they would get the flag from the server.

For the script implementation, please check out `solution.py`.
