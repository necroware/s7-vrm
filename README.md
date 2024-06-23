# Necroware's S7-VRM

This project is a Voltage Regulator Module for the Socket 7 mainboards as
defined by Intel in it's Pentium® Processor Flexible Motherboard Design
Guidelines. You can upgrade VRM capable Socket 7 mainboards with this module to
be able to use dual-voltage CPUs like Intel Pentium MMX, AMD K6, AMD K6-2 etc.

*Disclaimer: this VRM can damage your mainboard, CPU or both. Please use at your
own risk.*

__WARNING:__ *inserting the module the wrong way around would put +12V on all
critical lanes. It would destroy the mainboard, the CPU, the memory and all
expansion cards. This can't happen on mainboards with VRM socket, because
there it is not possible to insert it in reverse. On free standing VRM pinheader,
it is may be a good idea to cut +12V pin 5 and the unused pin 22 to use them as
a key.*


![S7-VRM](./photo.jpg)

Youtube Videos:
- Part 1: https://youtu.be/CMiGVQbMC5U
- Part 2: https://youtu.be/J0NLGfocviU
- Part 3: https://youtu.be/kBPp9EAIC8I
- Part 4: https://youtu.be/XV0b5Tvf5gY

## Voltage selection

Various voltages can be set using the SW1 switch on the module (0=off, 1=on):

Voltage | Switches | CPU Examples
--------|----------|-------------------------------------------
  1.6V  |   0000   | AMD K6-2E+ / K6-3E+ / Mobile K6-2
  1.8V  |   1000   |
  2.0V  |   0100   | Cyrix MII (0,18µm version)
  2.1V  |   0010   | 
  2.2V  |   1100   | AMD Mobile K6 / K6-2(+) / K6-3(+)
  2.3V  |   1010   | 
  2.4V  |   0001   | AMD K6-2
  2.5V  |   0110   |
  2.6V  |   1001   | 
  2.7V  |   1110   |
  2.8V  |   0101   | Intel Pentium MMX, IBM 6x86L, Rise MP6 
  2.9V  |   0011   | AMD K6, IBM 6x86MX
  3.0V  |   1101   | 
  3.1V  |   1011   | AMD K6@233 (needs actually 3.2V)
  3.3V  |   0111   | Pentium 66-200 (Single Voltage)
  3.5V  |   1111   | AMD K5, Winchip C6 / 2

This VRM was designed primarily for dual voltage CPUs, like Pentium MMX and
K6, but the module can be used for single voltage CPUs as well. For example
3.3V can be used to power a non-MMX Pentium CPU. Also AMD K5 or Winchip CPUs
can be used with 3.5V voltage, which will diverge from the 3.3V  I/O voltage
supplied by a linear regulator on the mainboard. However those CPUs are
tolerant to that difference in voltage and the VRM would take the most load
from the on board linear voltage regulator and reduce the heat drastically. 

## Important remarks

The transistor Q1 with integrated pull-up resistor is optional. It is used for 
enable/disable signal and is unused on most mainbards.

The PCB is made for a through hole inductor, but if you have only SMD it is also
possible to solder that instead. Keep in mind that the inductor has to stand
the required current. Also slightly different inductors are allowed, everything
between 2µH and 4,7µH should work as well. With the higher inductance you get
less current ripple, also voltage ripple can look better, but the maximum
possible current will decrease. Playing with different inductors will also
influence the compensation network.

Capacitors C7 and C8 are used in so called compensation network and are
responsible for DC-DC converter activation and stability. Those parts are very
delecate and dependent on the ESR and values of the output capacitors C9-C12,
and the inductor L1. If your regulator shows stability issues or not starting
at all, try to remove the capacitor C8. If you change any other parts C7, C8 and
R1 have to be adapted accordingly.

## Bill of materials

Part        | Count | LCSC#    | Comment
------------|-------|----------|--------------------------------------------
C1, C15     | 2     | C13585   | 10u capacitor SMD 1206
C2, C14     | 2     | C51205   | 4.7u capacitor SMD 1206
C3, C6, C13 | 3     | C696845  | 0.1u capacitor SMD 1206
C4, C5      | 2     | C407862  | 3300u capacitor TH Radial D10.0mm, P5.00mm
C7          | 1     | C107186  | 220n capacitor SMD 1206
C8          | 1     | C541493  | 39p capacitor SND 1206
C9-C12      | 4     | C407858  | 1000u capacitor TH Radial D8.0mm, P3.5mm
D1          | 1     | C109000  | Switching diode
J1          | 1     | C2897435 | Connector angled 02x15 pins 2.54mm 
L1          | 1     | N/A      | 3.3µH inductor
Q1          | 1     | C13871   | biased NPN-Transistor 
Q2, Q3      | 2     | C496603  | N-MOSFET GDS at least 15A
Q4          | 1     | C454937  | biased PNP-Transistor
R1, R2, R5  | 3     | C136874  | 15K resistor SMD 1206
R3          | 1     | C132648  | 3K resistor SMD 1206
R4          | 1     | C870818  | 5K resistor SMD 1206
R6          | 1     | C137115  | 7,5K resistor SMD 1206
R7          | 1     | C870859  | 6k resistor SMD 1206
R8          | 1     | C706412  | 3,75K resistor SMD 1206
SW1         | 1     | C15781   | DIP6 Switch THT 4 buttons 2.54mm
U1          | 1     | C2657973 | ISL6545 DC-DC Controller

The inductor doesn't need to be very exact, anything between 2.5µH and 4.7µH
should work, but the sweet point is at around 3.3µH. The inductor can be self
made by using a T50 ferrite toroid. For example T50-26 with permeability 75µ
wrapped in 10 loops of 1.3 mm coper.

## Tested mainboards

This module should run with all mainboards, which provide the VRM module header
as specified in Intel Pentium Mainboard Design Guidelines. Most of such boards
were based on Intel Triton (i430FX) and VIA Apolo Master (MV series) chipsets,
but there were also quite a lot of later boards with newer chipsets (f.e.
i430VX), which supported such an external VRM as well. So far this VRM was
tested using various CPUs and voltages on following mainboards:

Manufacturer | Model           
-------------|---------------------
Asus         | P/I-P55TP4XE(G)
Gigabyte     | GA-586-ATE/P

## License

This work is licensed under the Creative Commons Attribution-ShareAlike 4.0
International License.

## Links
* [Intel Pentium Mainboard Design Guidelines](http://netwinder.osuosl.org/pub/misc/docs/i386/24318702.pdf)

