# Necroware's MMX-VRM

This project is a Voltage Regulator Module for the Socket 7 mainboards as
defined by Intel in it's Pentium® Processor Flexible Motherboard Design
Guidelines. You can upgrade VRM capable Socket 7 mainboards with this mainboard
to be able to use dual-voltage CPUs like Pentium MMX, AMD-K6 and others.

![GamePort Adapter](./photo.jpg)

## Voltage selection

Various voltages can be set using the SW1 switch on the module.

SW1.1 | SW1.2 | SW1.3 | Voltage | CPU Examples
------|-------|-------|---------|-------------------------------
OFF   | OFF   | OFF   | 3.2V    | AMD K6 (only 233)
ON    | OFF   | OFF   | 2.9V    | AMD K6, IBM 6x86MX
OFF   | ON    | OFF   | 2.8V    | Intel Pentium MMX, IBM 6x86L, Rise MP6
ON    | ON    | OFF   | 2.6V    | ???
OFF   | OFF   | ON    | 2.5V    | ???
ON    | OFF   | ON    | 2.4V    | AMD K6-II (AHX)
OFF   | ON    | ON    | 2.3V    | AMD K6-II (AGR)
ON    | ON    | ON    | 2.2V    | AMD K6-II (AFX and others)


## Bill of materials

Part    | Count | LCSC#    | Comment
--------|-------|----------|--------------------------------------------
C1, C2  |   2   | C442583  | 820u Capacitor THT Radial D10.0mm P5.00mm
C3      |   1   | C431006  | 10nF Capacitor SMD 1206
D1, D2  |   2   | C2758579 | 1N5820 Diode SMD SMA 
J1      |   1   | C132129  | Connector 02x15 pins 2.54mm
L1, L2  |   2   | C182153  | 47uH Inductor SMD: 10.4x10.4mm
R1      |   1   | C352163  | 0K   Resistor SMD 1206 
R3      |   1   | C488999  | 9K   Resistor SMD 1206
R4      |   1   | C488915  | 6.3K Resistor SMD 1206
R5      |   1   | C488724  | 2.9K Resistor SMD 1206
R6      |   1   | C204679  | 1.6K Resistor SMD 1206
R2, R7  |   2   | C406728  | 1K   Resistor SMD 1206
SW1     |   1   | C52648   | DIP6 Switch THT 3 buttons 9.78x9.8mm 2.54mm
U1, U2  |   2   | C74188   | LM2596S-ADJ DC-DC Converter SMD TO-263-5

## Links
* [Intel Pentium Mainboard Design Guidelines](./docs/24318702.pdf)
* [LM2596S-ADJ datasheet](./docs/XL2596S-12E1_C74191.pdf)

