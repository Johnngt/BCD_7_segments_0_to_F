<!---

This file is used to generate your project datasheet. Please fill in the information below and delete any unused
sections.

You can also include images in this folder and reference them in the markdown. Each image must be less than
512 kb in size, and the combined size of all images must be less than 1 MB.
-->

## How it works

A 7-segment decoder (0 to F) is a combinational digital circuit that converts a 4-bit binary input into the signals needed to display a hexadecimal digit (0–9, A–F) on a 7-segment display.

1. Inputs

The decoder receives 4 bits:

Hex	Binary (D C B A)
0	0000
1	0001
2	0010
3	0011
4	0100
5	0101
6	0110
7	0111
8	1000
9	1001
A	1010
B	1011
C	1100
D	1101
E	1110
F	1111
2. Segments

A 7-segment display contains seven LEDs named:

Plain Text
--a--
| |
f b
| |
--g--
| |
e c
| |
--d--

Each segment can be ON (1) or OFF (0).

3. Example Output Table
Hex	a	b	c	d	e	f	g
0	1	1	1	1	1	1	0
1	0	1	1	0	0	0	0
2	1	1	0	1	1	0	1
3	1	1	1	1	0	0	1
4	0	1	1	0	0	1	1
5	1	0	1	1	0	1	1
6	1	0	1	1	1	1	1
7	1	1	1	0	0	0	0
8	1	1	1	1	1	1	1
9	1	1	1	1	0	1	1
A	1	1	1	0	1	1	1
B	0	0	1	1	1	1	1
C	1	0	0	1	1	1	0
D	0	1	1	1	1	0	1
E	1	0	0	1	1	1	1
F	1	0	0	0	1	1	1
4. How the Decoder Works

For every 4-bit input, the decoder checks which hexadecimal value it represents and activates the correct segments.

Example:

Input = 0101 (5)
The decoder turns ON segments:
a, c, d, f, g
Turns OFF:
b, e

5. Implementation in Verilog

If you're working in Wokwi or Tiny Tapeout, the decoder is usually implemented with a case statement:

Verilog
always @(*) begin
case (bcd)
4'h0: seg = 7'b1111110;
4'h1: seg = 7'b0110000;
4'h2: seg = 7'b1101101;
4'h3: seg = 7'b1111001;
4'h4: seg = 7'b0110011;
4'h5: seg = 7'b1011011;
4'h6: seg = 7'b1011111;
4'h7: seg = 7'b1110000;
4'h8: seg = 7'b1111111;
4'h9: seg = 7'b1111011;
4'hA: seg = 7'b1110111;
4'hB: seg = 7'b0011111;
4'hC: seg = 7'b1001110;
4'hD: seg = 7'b0111101;
4'hE: seg = 7'b1001111;
4'hF: seg = 7'b1000111;
endcase
end

Since you currently have a Wokwi project named "BCD_7_segments_0_to_F" open, this is likely the exact idea being implemented: a 4-bit value from 0000 to 1111 is decoded into the seven control signals that draw the hexadecimal characters 0–F on a 7-segment display.


## How to test

Method 1: Test All Inputs Manually

Connect 4 switches to the inputs:

D (MSB)
C
B
A (LSB)

Run the simulation.

Change the switches from 0000 to 1111.

## External hardware

List external hardware used in your project :
Display 7 segments
