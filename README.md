# Test and Measurement Equipment Reverse Engineering and Service Projects

This is where I keep the fruits of reverse engineering and service projects. It starts, usually, when a piece of equipment doesn't work, and there's no manufacturer documentation available - or the documentation is available only for a fee.

## KEPCO MPS-620M Power Supply

This is a dual supply: a 20V/1A bipolar tracking section, and a 6V/5A single output section. The 20V section was functional. The 6V section crowbar was triggered independent of front panel control settings. An electrolytic capacitor in the 6V sub-assembly had failed, causing excessive ripple on the amplifier supplies, and resultant triggering of the crowbar. Several Zener diodes were out of tolerance as well. Replacing those components brought the 6V section back to life. A 24h stress test was performed, running both supplies at full output current into dead shorts. No further trouble was found, and everything was in otherwise in spec.

I've reverse-engineered the circuits to make schematics. The service manual available online for this power supply has a parts list with component designators/references, but no schematics. Status, per assembly:

- **A1** 6V supply card: finished,
- **A2** output terminals, controls & crowbar done, TODO: meters, readout switch, mains circuits;
- **A3** ±20V supply card: mostly done, TODO: line voltage switch;
- **A4-A7**: finished.

First, the circuitry was reverse-engineered from the boards onto paper and pencil. Then it was redrawn in KiCad, checked against the hardware, and hopefully all discrepancies were corrected.

Incredibly enough, the manufacturer supports this instrument and it's still an orderable product per their website. The complete manual with schematics is available for purchase - but where's the joy in that? :)
