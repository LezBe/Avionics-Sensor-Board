# BMP581 Footprint

## Original Schematic Reference

The BMP581 schematic copied from `LezBe/BMPunit` references this footprint name:

`QFN10_BMP581_BOS`

The actual `.kicad_mod` file was not committed in the BMPunit repository, so it could not be preserved here.

## Required Verification

Before the BMP581 is placed on the integrated PCB, add a KiCad footprint and verify all pad dimensions, pad numbering, orientation, solder-mask settings, and courtyard against the Bosch BMP581 datasheet, especially Section 8.2 (Landing pattern).

Official Bosch datasheet:

https://www.bosch-sensortec.com/media/boschsensortec/downloads/datasheets/bst-bmp581-ds004.pdf

## CAD Resource

Ultra Librarian lists a BMP581 symbol, footprint, and 3D model and provides a KiCad 6+ export:

https://app.ultralibrarian.com/details/6b707625-f695-11ec-9c51-0a34d6323d74/Bosch-Sensortec/BMP581

If that footprint is downloaded for this project, commit the resulting `.kicad_mod` here only after checking it against Bosch's official landing pattern.

## Manufacturing Gate

**Do not release Gerbers containing the BMP581 until the footprint review is complete.**
