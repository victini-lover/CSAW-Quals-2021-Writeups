# Gotta Decrypt Them All
Category: crypto
Points: 175
Solves: 235

## Description
You are stuck in another dimension while you were riding Solgaleo. You have Rotom-dex with you to contact your friends but he won't activate the GPS unless you can prove yourself to him. He is going to give you a series of phrases that only you should be able to decrypt and you have a limited amount of time to do so. Can you decrypt them all?

## Notes
The goal of the challenge was to get people used to performing simple decoding and decryption methods used routinely in CTFs. The idea was to get newcomers a little used to how crypto works. To give it a twist, I chose to put a time limit of 10 seconds to ensure that people used a script to solve it rather than doing it manually.

## Flag
flag{We're_ALrEadY_0N_0uR_waY_7HE_j0UrnEY_57aR75_70day!}

## Solution
After connecting to the server, people are given morse code. Decoding it leads them to numbers which are the decimal ASCII representation of letters and numbers. 

Converting the decimal numbers to ASCII, they see that there are capital letters, lowercase letters, numbers and the equal to sign. This is base64 and they need to decode it. 

After decoding the Base64 text, they will get text that is in the format of "N = some number, e = 3, c = some number". This is RSA encryption and the flaw that they had to realize was that the public exponent was super small and the ciphertext was short. This implies that the ciphertext can be recoved by just taking the cube root of the ciphertext.

After taking the cube root and converting the number to bytes to ASCII, they are greeted some random text. As a hint, the theme was Pokemon and the first ciphertext was a fixed string "Pokemon Names". Becasue of that, people can recognize that the last stage of decryption needs them to apply a Caeser shift of 13.

This needs to be done for 6 different ciphertexts and after decrypting them and sending it to the server, people would get the flag from the server.

For the script implementation, please check out `solver.sage`. The reason that SageMath was used is because standard Python was having precision issues for taking the cube root.
