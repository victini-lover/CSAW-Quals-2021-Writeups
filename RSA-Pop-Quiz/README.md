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
For Part 1, the hint points to Wiener's attack. So, you can use any online tool or Python library to do the continuous fractions needed to solve for the private key. I have used a Python library called owiener to get the private key.

For Part 2, the hint points to the fact that there is a known relationship between the two primes. Therefore, it becomes easy to factorize N and solve for the private key. For the factorization, you need to solve the quadratic equation p*(p+6) = N. You can also use Fermat's attack to solve part 2. The script `sexy_primes_solver.sage` is the solver for part 2.

For Part 3, there is a LSB oracle. The server will give you the last bit of the decrypted plaintext of your chosen ciphertext. The idea is to exploit the malleability of RSA: given a plaintext `P` whose ciphertext is `C = (P^e) % N` , if we multiply `C` by `2^e` we obtain `C' = ((2P)^e) % N` which is the encryption of `2P`. From here, we can narrow the range for which P exists by using the LSB. If it is 1, then `2P > N` else `2P < N`. From this, we can find the plaintext in `log N` steps. The script to do this manually is `lsb_oracle_solver.py`.

For Part 4, the server has leaked out the lower half bits of the private key. Using this paper (`http://honors.cs.umd.edu/reports/lowexprsa.pdf`), we can crack what is the private key. The basic idea is to brute force the possible values for `s` using the equation `(e*d) % 2^512 = 1+ k*(N-s+1)` where `k = [0...e]`. Then, we solve the various values for `p` using the equation `(p^2 - s*p + N) % 2^512 = 0`. Using the various values of `p`, we substitute it as `p0` in the equation `((2^512)*x + p0) % N = 0` and solve for `x`. We take the GCD of `(2^512)*x + p0` and `N` to get the actual prime `p`. Therefore, the factorization is done and the private key can be calculated. The script `partial_key_solver.sage` is the solver for part 4.
NOTE: An unintended solve for Part 4 is to get 17 different ciphertexts and solve the system of equations using Chinese Remainder Theorem. This attack is known as Hastad’s Broadcast Attack. A way to avoid this is to make sure that there is no way to get that many unique ciphertexts.

For the entire script implementation including server interaction, please check out `solution.sage`.
