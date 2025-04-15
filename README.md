# Turing Machine

The Turing Machine is a hugely popular module which produces random sequences of configurable length which can be held constant, or allowed to change slowly over time. Think of it like a sample-hold for sequences.

The circuit here is based on the [Music Thing Modular Turing Machine](https://github.com/TomWhitwell/TuringMachine) with some minor tweaks. The changes I've made are thus:
* Added polarity protection so that a backward power header doesn't fry anything (twin series schotty diodes: BAT54SL),
* Full surface mount design on a single PCB,
* Simpler input power filtering,
* Expanded length choices to include 7, 9, 11, and 13 (in addition to the default 2, 3, 4, 5, 6, 8, 12, and 16).
* Schmitt trigger with hysteresis on clock input to handle input signals which aren't perfectly smooth (alleviating the tendancy of the Music Thing Modular circuit to double-clock)

This module should be a drop-in replacement for the Musing Thing Modular version with the same width and same basic panel layout. I've altered it somewhat to fit with the aesthetic and practices of my DIY build, however the pinouts for expansion modules adhere exactly to the original. This repo inherits the same license as the original Turing Machine: [CC-BY-SA](https://creativecommons.org/licenses/by-sa/3.0/)

The KiCAD project here uses the library/footprints [found in my companion repo](https://github.com/thismatters/EurorackKiCAD).

## Width

10hp

## Inputs

Jacks:
- Clock (required input) -- Max clock rate: 1300Hz; higher frequencies will cause bit smearing.
- CV for setting "Change" rate

Knobs:
- Change rate
- Sequence length (12 position switch)
- Scale

Write switch for setting the current bit high or low.

## Outputs

Jacks:
- CV output of of sequence
- Whitenoise
- Pulse whenever the current bit is high

LEDs:
- 8x for the current binary representation of the output tone
- 1x for the pulse
- 1x for the clock input

## Vendors

There are part numbers in the [BOM](turing-machine.csv) for many of the parts (not for basic passives though) at the following vendors:

* [Mouser](https://www.mouser.com): Needs no introduction. Get your ICs from here (or [digikey](https://www.digikey.com)).
* [Tayda Electronics](https://www.taydaelectronics.com/): Good supplier for passive components; audio jacks, and potentiometers. Their audio jacks are slightly smaller than the thonkiconn from thonk.
* [Love My Switches](https://lovemyswitches.com/): Has [really good knobs](https://lovemyswitches.com/anodized-aluminum-knob-the-lo-fi-1-4-smooth-shaft-12-5mm-od/) to go on those potentiometers!
* [OSHPark](https://oshpark.com/): Fast and (relatively) cheap PCB manufacturer. [V1 board works great!](https://oshpark.com/shared_projects/wF94N3Eb)


## Changelog

### V1

* [x] Fixed pinout for DAC0800 which is different for SOIC than PDIP
* [x] Write switch rotated 180deg
* [x] Filters between shift registers removed (max clock rate confirmed at around 1330Hz (E6))
* [x] Schmitt trigger supplements op-amp in gate input stage
* [x] Flipped trimmer and added hole to front panel so that trimming can happen _in-situ_, added note to PCB about how the trimmer should be oriented.
