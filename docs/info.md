<!---

This file is used to generate your project datasheet. Please fill in the information below and delete any unused
sections.

You can also include images in this folder and reference them in the markdown. Each image must be less than
512 kb in size, and the combined size of all images must be less than 1 MB.
-->

## How it works

This chip implements a 4-bit ripple-carry binary adder built structurally by cascading four 1-bit full adder modules (fulladder). The circuit takes two 4-bit binary operands (a[3:0] and b[3:0]) along with a carry-in (cin); each stage computes its corresponding sum bit (s[0] through s[3]) using XOR gates (a ^ b ^ cin) and generates a carry-out (a & b | a & cin | b & cin) that propagates internally through the cout1, cout2, and cout3 wires to the next more significant bit. At the end of the chain, the chip outputs the 4-bit result on s[3:0] and the final carry-out on cout4, allowing it to represent unsigned binary sums from 0 to 31.

## How to test

Start the simulation and apply the following test vectors to the switches to validate both the addition logic and the proper carry propagation across all stages:
Basic addition without carry: Set a = 0011 (3), b = 0100 (4), cin = 0. The LEDs should display cout4 = 0 and s = 0111 (7).
Internal carry propagation: Set a = 0111 (7), b = 0001 (1), cin = 0. This verifies that the carry travels from fa0 to fa3; the result should be cout4 = 0 and s = 1000 (8).
cin verification: Set a = 0000 (0), b = 0000 (0), cin = 1. Only s[0] should turn on (s = 0001, cout4 = 0).
Overflow (cout4): Set a = 1111 (15), b = 0001 (1), cin = 0. The carry must cross all four stages: the s[3:0] LEDs should remain at 0000 and only cout4 = 1 (16) should turn on.
Maximum edge case: Set a = 1111 (15), b = 1111 (15), cin = 1. All output LEDs should turn on (cout4 = 1, s = 1111, equivalent to 31).

## External hardware

Leds...
