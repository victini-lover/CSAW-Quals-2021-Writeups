# Save-the-Tristate
> Category: misc
> Points: 474
> Solves: 68

## Description
So it was just another day in Danville when Phineas and Ferb were making a new device to communicate with Meep as he travels across the galaxy. To make a device suitable for galatic communication and secure enough to be safe from alien hackers, they decide to protect their device with QKD! Unfortunately, due to Phineas & Co singing their usual musical numbers about their inventions, Doofenshmirtz has caught wind of this technology and wants to use it to take over the Tristate area, using his brand new Qubit-Disrupt-inator. Naturally I, Major Monogram, have to send you, Perry the Platypus, on a mission to stop Doofenshmirtz from disrupting Phineas and Ferb's qubits with his diabolical inator. So grab your tiny fedora and doo-bee-doo-bee-doo-ba-doo your way over to stop Doofenshmirtz! Mission:
<ul>
  <li>Receive # of qubits that translate to the flag</li>
  <li>Measure qubits in your own basis</li>
  <li>Monogram tells you how many qubits were measured correctly, but not which ones</li>
  <li>Go back and fix it</li>
  <li>Get it right</li>
</ul>

## Notes
This challenge was insipired by the Google CTF 2019. We used a writeup published by scryh (`https://devel0pment.de/?p=1533`).


## Flag
flag{MO0O0O0O0M PH1NE4S & F3RB R T4LK1NG 2 AL1ENS 0V3R QKD!!!}

## Solution
Send in as many bases as you'd like, we will tell them how many are right or wrong.
Get the bases in the right order
Apply bases to the proper input (complex numbers)
Get correct output of bits
Translate to ASCII - 8 bit chunks
GET FLAG


How many bases to guess (give number)
What are your guesses (send + and x in specific order)
Match to the order of our array (send back how many are correct)
Do as many times as they want and check any number of bases each time
They can progressively get the right order, piece by piece

set up basis once, randomly, so everyone has a unique challenge
Randomly generate set of bases, once they get the right order, calculate the bits,

Save key in one file, and the flag in the other.
Convert key to binary, put binary through bases, convert to ASCII -> password!
Give password to get flag!

Given the binary of the flag and the arrows (conjugates), apply the bases to each arrow directly, and each resulting diagonal arrow must be corrected.
Perform bases on given arrows, throw out resulting diagonals.
Encoding for addition, decoding for subtraction - give hint with the bases
Perform rotation on conjugate
'x' - add 45 degrees
'+' - no change
