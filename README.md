# SD2SP2 Nano

This PCB allows a microSD card to be adapted into serial port 2 of the Nintendo GameCube.

![An SD2SP2 Nano installed into serial port 2 of a Spice Orange GameCube](https://github.com/ndoo/SD2SP2/blob/master/Photos/Installed.jpg?raw=true "SD2SP2 Installed")

### Bill of Materials

| Reference Designator | Part                                             | Digi-Key Part                                                                                                               |
|----------------------|--------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------|
| C1,C2                | Capacitor, Ceramic, 10µF, 16V, 0603              | [1276-6769-1-ND](https://www.digikey.com/product-detail/en/samsung-electro-mechanics/CL10X106MO8NRNC/1276-6769-1-ND/5961628) |
| J1                   | Connector, Micro SD Card, Push-Pull, Right Angle | [WM6825CT-ND](https://www.digikey.com/product-detail/en/molex/1050270001/WM6825CT-ND/3045221)                                |

### Ordering

![Assembled SD2SP2 Nanos with microSD cards installed](https://github.com/ndoo/SD2SP2/blob/master/Photos/Boards.png?raw=true "SD2SP2 Boards")

The PCB must be ordered in 1.2mm thickness, with ENIG copper finish to ensure reliable electrical contact and minimal oxidation over time. I had my PCBs made at [JLCPCB](https://jlcpcb.com/).

The SD2SP2 Nano falls below the minimum board dimensions permitted by [Seeed Studio’s Fusion PCB service](http://www.seeedstudio.com/fusion_pcb.html), though panelizing the PCB can work around PCB fab houses which enforce a minimum size. I&rsquo;d actually recommend panelization, it would really drive down the cost of fabricating this tiny PCB.

### Assembly

Ideally, the PCB would be reflow-soldered, and all components were kept on a single side to make it a speedy affair. Hand-soldering instructions are provided below; the sample boards pictured above were hand soldered.

You will probably want (unless you are very skilled, patient and careful):

* Solder wick, to clean up solder bridges that may form across the narrowly-spaced pins of the microSD slot
* High-temperature (Kapton) tape to mask gold contacts from solder (accidentally tinning the gold contacts results in a non-reversible metallurgical reaction)

1. Solder C1 and C2 (they are non-polar and can be soldered in any orientation)
2. Place J1 on the PCB and solder pin 1 (pin farthest from gold plated connector)
3. Ensure J1&rsquo;s pins are precisely aligned; the small pitch will lead to pins shorting if misaligned (re-heat pin 1 as needed to reposition J1)
4. Use kapton tape to mask the longest gold plated connector on the top side, next to C1&rsquo;s silkscreen label
5. Solder the corner of J1&rsquo;s shield next to C1&rsquo;s silkscreen label
6. Solder the remaining pins of J1 - you may need solder wick to clean up solder bridges (P1-P5 and G1) across the closer-spaced pins
7. Solder the remaining shield corners of J1
8. Clean the board of any flux residue using isopropyl alcohol (or as directed by the flux/solder product you used)

### How it works

The EXI bus exposed from the GameCube&rsquo;s two serial ports uses an SPI-based protocol which is compatible with SD cards in SPI mode. [Swiss](https://github.com/emukidid/swiss-gc/releases) v0.4r682 or newer adds support for SD cards on serial port 2, identical to and in addition to existing memory card "SDGecko" adapter support.

The most common use-case for this seems to be using a &lt;4GB SD card in the SDGecko to load Swiss using Action Replay’s `autoexec.dol` feature, while using a larger microSD card in the SD2SP2 for storing homebrew and backups.

If you already have an IPL replacement modchip that boots into Swiss, or alternative loaders for Swiss such as the PSO exploit, then perhaps you may want an SD2SP2 for a cleaner front panel look for your GameCube, or to enable the use of 2 standard GameCube memory cards (which may be desirable for region switch consoles, as separate memory cards are needed between USA and JPN regions).

### Future Improvements

* Remove tented vias under silkscreen of "GC Front" text for aesthethic reasons
* Change the rounded edge of the connector to square edges, so that the board can be panelized adjacent to each other with V-cuts rather than requiring CNC milling
* Reduce the width of the microSD slot pads (P1-P5 and G1) and add a silkscreen barrier to prevent solder from bridging the pins during hand soldering

### Credits

This PCB was adapted from [citrus3000psi&rsquo;s original project](https://github.com/citrus3000psi/SD2SP2). I pruned previous revisions of the PCB from this repository, so please refer to the original repository for the original files.

The credits below are retained from the original README:

> Special thanks to:
> * MockyLock for the idea
> * Extrems & emu_kidid for doing the real work needed to make this possible