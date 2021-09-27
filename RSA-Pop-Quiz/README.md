# RSA Pop Quiz
Category: crypto
Points: 390
Solves: 137

## Description
Your crypto professor is back again! After having taught you some things about RSA, they have sprung another pop quiz. According to them, it is harder and longer. You should still be able to crack it, right?

## Notes
I learned about these attacks by playing previous CTFs, reading the blog `bitsdeep.com` and reading papers discussing the various attacks possible on the RSA cyptosystem. 

The goal of the challenge was to introduce people to the various attacks that are possible on RSA and get them interested in learning other attacks that were not done as a part of the challenge.

The RSA parameters for Parts 1,2 and 4 were pre-computed and saved to a json file to save on computation time during the CTF. The parameters vulnerable to Wiener's attack were generated using a script I wrote called `wiener_attack_generator.py`. The parameters where the primes generated are sexy primes were saved into a json file using a script I wrote called `sexy_primes_generator.py`. The parameters for the partial key leakage were generated using a script I wrote called `partial_key_generator.py`.

## Flag
flag{l00K5_L1K3_y0u_H4v3_p4223D_7h3_D1ff1Cul7_r54_p0p_Kw12_w17H_fLy1N9_C0L0r2}

## Solution
For Part 1, 

For Part 2, 

For Part 3, 

For Part 4, 

For the entire script implementation including server interaction, please check out `solution.sage`.
