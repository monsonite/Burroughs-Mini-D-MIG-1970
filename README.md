# Burroughs-Mini-D-MIG-1970

A transcription of the US Patent US 3,878,514 drawings for an 8-bit, bit serial CPU.

https://patentimages.storage.googleapis.com/8e/54/4c/11d72d5f62a1dd/US3878514.pdf

This machine is a source of inspiration because although designed in the very early 1970s, it predicted the use of a low pin-count controller, interfacing to peripherals via a clocked serial I/O bus. This is what we would now recognise as a microcontroller with an SPI bus.

Constructed first in 7400 series TTL and then implemented as an LSI chip, it had just 16 pins and was clocked at 10MHz.

It could execute an 8-bit arithmetic instruction in 1uS, and transfer bytes of data at 10 Mbits/s.

If implemented in the TTL devices that were available in 1970, it would run to about 50 packages, and the gate count would be around 600 gates.

The object of this project is to capture the logic diagrams from the patent and make them available in a form that may be utilised by DIY CPU constructors, either in 74HC, disctrete transistor DTL or VHDL/Verilog for FPGA/CPLD implementations.

My logic simulator is H. Neemann's "Digital" - available to download here on Github.

This is a work in progress, so please check back for progress reports and updates.


![image](https://github.com/user-attachments/assets/9041cefe-0a69-4ec2-9a12-f4d32c222738)


Here is how Burroughs described this CPU:

Microprogrammed processors 

BURROUGHS CORP 24 July 1973 [20 Nov 1972] 35171/73 
Heading G4A 

A microprogram memory 14 is addressed by command information received over a serial input bus DATA IN to retrieve selected microinstructions for controlling a logic unit which performs arithmetic and logic operations on data information received over the input bus and provides an output to a serial output bus DATA OUT. 

The logic unit includes a plurality of A registers A1-A3, a B register, a serial adder and logic circuit 30 and selection gates 36, 38, 40, 42 for routing the adder output to a selected A or B register and for selecting the X and Y inputs of the adder.

The B register may also be loaded from the input bus serially by bit or in parallel by a literal value (e.g. data, jump address, shift amount) from a microinstruction via decoder 46.

The microprogram memory 14 is addressed by a program counter MPCR which may be incremented by 1 or 2 and which is provided with parallel transfer paths 92 for exchanging its contents with those of an alternative program counter AMPCR which is used to store jump and return addresses and which can also be loaded serially from the adder 30 via gates 36 or in parallel with a literal value from decoder 46. 
 
Register AMPCR can be selected to provide the Y input to the adder, the other possibilities being the true and false outputs of the B register. 
 
The following types of microinstruction are described. 
 
The literal assignment microinstruction causes loading of the B register or AMPCR with a literal field contained in the microinstruction, and a variation of this microinstruction loads the literal value of the microinstruction into AMPCR and then transfers it to MPCR as a jump address. 
 
The condition test microinstruction has a condition field specifying one of the following condition registers to be tested (a) MST which is set by the most significant bit of the adder output (b) AOV which is set upon an overflow condition occurring in the adder (c) LST which is set by the least significant bit of the adder output (d) ABT which is set when the adder output is all 1's (e) three local condition registers LC1- LC3 and (f) an external condition register EXT settable by a control signal from another unit in the system of which the processor forms part. 
 
The microinstruction also includes a set field for setting one of the local condition registers LC1-LC3 if the specified condition register is set, and true and false successor fields which define the next microinstruction in the sequence, depending on the true or false result of the condition test, by specifying whether MPCR is to be incremented by 1 (STEP) or 2 (SKIP), or incremented by 1 and the result saved in AMPCR (SAVE), or whether MPCR is to receive the contents of AMPCR (JUMP). 
 
The logic unit microinstruction specifies one of 16 arithmetic and logic operations, Fig. 6 (not shown), the source registers for the X and Y inputs to the adder (the B register output may be complemented) and the destination register for the result. 
 
Some logic unit microinstructions provide for transfer of information to the B register from an external source while the adder output is transferred to a specified register, and if the B register is specified the adder output and externally supplied data are ORed together before entering the B register. 
 
The external (or device) microinstruction includes a literal value which is transmitted over the out bus via the memory buffer.


