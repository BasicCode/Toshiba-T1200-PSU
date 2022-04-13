# Toshiba-T1200-PSU
A replacement power supply design for the Toshiba T1200 laptop computer from 1987. The Toshiba T1xxx series are notorious for power supply falures, and the power supply design is especially complex for the era. While the complicated design did allow for some innovative new power management features which had not been attempted before, it also allowed for a myriad of annoying failure modes. I say this only because I have not implemented most of the auxiliary features here, but they may be desirable in the future.<br />
<br />
This is the initial commit, revision 1, and has a few issues, but it works and the computer boots! It will no doubt be obvious that I am not an engineer, and I certainly don't specialise in SMPS circuit design. I have used modular power options where possible and have tried to follow the recommended design for the -22V SMPS circuit as closely as possible. Please feel free to improve on this design.

## Getting Started
This board is designed in KiCad 6.x, custom and third-party footprints are included in the repository, and the individual Gerber files are included. **I did most of the design using KiCad under Linux, and when I try to open the project on Windows it complains about incorrect path to files.** I'm not sure if this is a known fault or what.
* The board is designed to use 12V, like the original, however the invdividual switchmode supplies have different tollerances so you might be able to get away with other supplies but check the datasheets first.
* I used OSH Park to print the boards (https://oshpark.com/shared_projects/rPYG17Z9).
* The footprint for the DC Barrel Jack 12V input *should* fit the jack on the original PCB if you want to use that, however I have used a more standard size plug and a modern, off-the-shelf, 12V plug pack. The original power supply is rated for 2.2A.
* I measured the whole system at boot to draw approx. 700mA at 12V.
* There is NO output protection (I'm not sure if there ever will be), so if you build one of these then make sure to check the voltage rails before using it.

## Errata
These are actual faults that need to be fixed in future designs or when using this design.
* DC barrel jack is the correct placement if using the original jack, however modern ones are about 1mm longer at the front and don't quite fit.
* TMV1212 12V module has open-circuit voltage of 18V. A 10K ohm / 1mA load brings this down to 12V. Add a 10K resistor to the output.
* TMV1212S 12V module has the wrong footprint. It can be forced to fit with some bent leads but looks messy.
* PWR_SW footprint is incorrect. Too close to the front of the board, and incorrect lead spacing.

## TODO
These things would be nice to fix in the next revision.
* Create a public Digikey or Mouser parts list.
* There are two different 100nF capacitor sizes. This should be simplified to be both the same footprint.
* It would be nice if the silkscreen for D1, and D2 indicated the polarity more clearly.
* Text for PJ5 and PJ5 headers are obscured by the header.
* "Toshiba T1200 PSU" heading text could be bigger. Also could add an "Open Hardware" logo.

## Future Options
Although I don't plan to implement these features, I've tried to design the circuit with them in mind.
* HDD Power switch.
* Arduino-compatable system to interact with the TX/RX lines.
* LiPo charging, and boost circuit to run off one or two 18650s, OR NiCad.

