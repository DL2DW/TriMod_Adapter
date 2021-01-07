# TriMod Adapter

![](https://github.com/DL2DW/TriMod_Adapter/blob/main/Images/TriMod_CBM_Adapter.jpg)



## IEEE-488 for the Commodore 1541 Disk Drive

With the help of this adapter, you can turn a VC1541 into a 2031LP in no time. And it is just as easy to switch back again.

So to speak, the best of two different worlds. Once the Commodore 1541 with the CBM bus for Commodore C64 and C128. And switchable as 2031LP for the PET and CBM world with GPIB (IEEE-488) interface.

The idea came from Andre Fachat and was published in 64'er magazine in the 1980s. He was the first to come up with the idea of turning a 1541 into a 2031LP.

I took up this idea again and even made the whole thing switchable. So you can always use the "1541 mode" again without removing the adapter again.



# Technical

Commodore had derived the 2031LP from the 1541 at that time. If you look at both schematics, they only differ in one detail.

And this is the connection to the outside world. 

On the 1541, the VIA 6522 is only partially used, because port A is not connected. Port B provides the lines for the CBM bus, which communicate with the computer via a 74LS14 and 74LS06 driver.

In contrast, port A is also required for the 2031LP. This provides the 8 parallel data lines, while port B is responsible for the control lines of the GPIB bus. Here the two drivers SN75160 and SN75161 are used.

And these are basically the actual differences, to put it simply.

So the 1541 can be easily converted to a 2031 with an adapter board. Of course, the Kernal has to be exchanged accordingly.

So that the adapter does not have to be removed every time you want to use the CBM bus, I have made the whole switchable.

With the help of CD4066 4-fold switches, the lines can be easily switched. At the same time the integrated Kernal adapter is also switched.



![](https://github.com/DL2DW/TriMod_Adapter/blob/main/Images/TriMod_CBM_Adapter_assembled.jpg)



A 27128 EPROM is required for the Kernal. First (address 0x0000) the binary for the 1541 mode is written and afterwards (address 0x2000) the binary for the IEEE-488 mode.

With setting the jumper the mode can be switched. Of course this should be done only in the switched off state.



# BOM

Here is the list of components. 

|      | Description                                                  | Part                  | References           | Value                       | Quantity Per PCB |
| ---- | ------------------------------------------------------------ | --------------------- | -------------------- | --------------------------- | ---------------- |
| 1    | Unpolarized capacitor                                        | C                     | C1 C2 C3 C4 C5 C6 C7 | 100nF                       | 7                |
| 2    | Diode                                                        | D                     | D1 D2                | 1N4148                      | 2                |
| 3    | Generic connector, single row, 01x12, script generated (kicad-library-utils/schlib/autogen/connector/) | Conn_01x12            | J4 J5                | Conn_01x12                  | 2                |
| 4    | Generic connector, double row, 02x12, top/bottom pin numbering scheme (row 1: 1...pins_per_row, row2: pins_per_row+1 ... num_pins), script generated (kicad-library-utils/schlib/autogen/connector/) | Conn_02x12_Top_Bottom | J3                   | IEEE-488 Connector          | 1                |
| 5    | Generic connector, single row, 01x20, script generated (kicad-library-utils/schlib/autogen/connector/) | Conn_01x20            | J1 J2                | PIN Header to PCB 6522 1-20 | 2                |
| 6    | Jumper, 2-pole, open                                         | Jumper_2_Open         | JP1                  | Jumper                      | 1                |
| 7    | Resistor                                                     | R                     | R1 R4                | 10k                         | 2                |
| 8    | Resistor                                                     | R                     | R5                   | 1k                          | 1                |
| 9    | Resistor                                                     | R                     | R2 R3 R6             | 3k3                         | 3                |
| 10   | 2x DIP Switch, Single Pole Single Throw (SPST) switch, small symbol | SW_DIP_x02            | SW1                  | IEEE-488 Device ID          | 1                |
| 11   | OTP EPROM 128 KiBit, [Obsolete 2004-01]                      | 27C128                | U8                   | 27C128                      | 1                |
| 12   | Quad Analog Switches                                         | 4066                  | U1 U2                | 4066                        | 2                |
| 13   |                                                              | 7406N                 | U4                   | 7406N                       | 1                |
| 14   | Quad 2-input XOR                                             | 74LS86                | U3                   | 74LS86                      | 1                |
| 15   |                                                              | MOS6522               | U5                   | MOS6522                     | 1                |
| 16   |                                                              | SN75160               | U6                   | SN75160                     | 1                |
| 17   |                                                              | SN75161               | U7                   | SN75161                     | 1                |



If you liked my project, I would be very happy about a small coffee donation.

[![ko-fi](https://www.ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/R6R62T6RN)



# License

The contents of this repository, with the exception of the Docs and Software directories, are released under the following license:

- the "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License" (CC BY-NC-SA 4.0) full text of this license is included in the [LICENSE.CC-NC-BY-SA-4.0](https://github.com/DL2DW/TriMod_Adapter/blob/main/LICENSE.CC-NC-BY-SA) file and a copy can also be found at https://creativecommons.org/licenses/by-nc-sa/4.0/

