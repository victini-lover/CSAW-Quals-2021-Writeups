# Save-the-Tristate
Category: misc
Points: 474
Solves: 68

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

This challenge was meant to get people interested in reading about Quantum Key Distribution as well as the BB84 protocol.

## Flag
flag{MO0O0O0O0M PH1NE4S & F3RB R T4LK1NG 2 AL1ENS 0V3R QKD!!!}

## Solution
The way the challenge worked is by having people guess what order are the 256 bases chosen. The bases were `x` and `+`. The way that people could do it was by iteratively guessing what were the chosen bases and making sure that the server says that there are no errors. After getting all the right bases, the server sends the bits in polar co-ordinate form. Using the bases, we convert the polar co-ordinates into `1`s and `0`s. We translate the bits into ASCII and we get the message. Sending the message to the server gives us the flag.

For the entire script implementation, please check out `solution.py`.
