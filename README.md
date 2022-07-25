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

## Power Designs 3240 Transistorized Power Supply

This is a monster of a supply, designed around the limitations of the power germanium devices available at the time. The one I got has capacitor date codes from 1963.

Longevity and reliability was achieved through limiting the power dissipation in semiconductor devices. This took:

- a variac voltage preset stage to limit the LV transformer's primary voltage, thus reducing power dissipation during constant-voltage operation,
- a 4-ohm power resistor mounted on the back of the chassis, to dissipate the power that would otherwise have to be dealt with by the series regulator -- this makes constant-current operation possible.

Upon initial checkout, the voltmeter would not go below about 6V in spite of turning the voltage control all the way down.

The supply showed no obvious signs of servicing and looked pristine inside.  The two big Sprague Compulytic electrolytic smoothing capacitors have failed. After replacement, it was back to life and in-spec. It subsequently failed during a stress test, while driving 5A into a short. The voltage regulation seemed to work without load, but as soon as a load was applied, the output folded back to zero. The supply dissipated about 100W of power during the stress test.

I have reverse-engineered the secondary, low voltage section, including the panel controls. The primary section is simple enough not to need a schematic.


### A Historical Note

The first thing anyone would do is to look for the manufacturer's website. There used to be one, long ago, at powerdesigns.com. The website was under the Power Designs primary brand until the [end of 2001][PD1]. Technipower, LLC, D.B.A. Power Designs, became the "primary" brand in 2002, at technipowerllc.com. Both of those historic domains are now defunct. Finally, they got gobbled up into Unipower -- see https://unipower.com.

Over time, all mentions of laboratory power supplies have evaporated from Technipower's lineup. The last reference available on archive.org is from [2007-06-25][PD2]. At that time, their lineup included the following models:

- 4050: 40V/5A -- a very long-lived platform, it seems;
- TW1550: two ranges: 6V/5A and 15V/2.5A,
- TW5015: 50V/1.5A,
- TP1800: three independent sources: 50V/1.5A, 15V/2.5A, 6V/5A,
- 2040A Precision Power Source: two ranges: 10V/4A and 20V/2A.

By September 5th, 2007, a new website design was up, and the laboratory stuff seemed not to be listed anymore.

[PD1]: https://web.archive.org/web/20010817035051/www.powerdesigns.com/powerdes.htm

[PD2]: https://web.archive.org/web/20070625144324/www.technipowerllc.com/