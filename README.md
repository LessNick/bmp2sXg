# bmp 2 sXg

Utility for converting images from windows bmp to sXg, an advanced graphics format for ZX Spectrum (ZX Evolution/PentEvo)

## Compile

FreeBSD:
`gcc -o bmp2sxg -std=c99 bmp2sxg.c`

Win32:
`mingw32-gcc -o bmp2sxg.exe -std=c99 bmp2sxg.c`

Also nice to be packed:
`upx -9 bmp2sxg`

## Usage:

`bmp2sxg <filename> [commands]
Commands:
  --debug   enable output debug information (default disabled)
  --64      cut palette to atm 64 colors limit (default disabled)
  --bg nn   set background color. where nn number from palette (default #00)`

# sXg File Struct

`0x0000 (0x04) #7f+"SXG" - 4 bytes size signature that this is an SXG file format`
`0x0004 (0x01) 1 byte size format version`
`0x0005 (0x01) 1 byte size background color (used for cleaning)`
`0x0006 (0x01) 1 byte size data packing type (#00 - data is not packed)`
`0x0007 (0x01) 1 byte size image format (1 - 16 colors, 2 - 256 color)`
`0x0008 (0x02) 2 byte size image width`
`0x000a (0x02) 2 byte size image height`

(to expand the title offsets are given below)
`0x000c (0x02) 2 byte size offset from current address to start of palette data`
`0x000e (0x02) 2 byte size offset from the current address to the start of the bitmap data`

The actual beginning of the palette data

`0x0010 (0x0200) 512 byte size palette`

and start data bitmap

`0x0210 (0xXXXX) data bitmap`

# Links

[ZX Art (Gallery)](https://zxart.ee/eng/graphics/database/pictureType:sxg/)
[About sXg (Article Russian)](https://hype.retroscene.org/blog/126.html)

# License

Source Copyright © 2009, 2023 Breeze\Fishbone and contributors. Distributed under the BSD License. See the file LICENCE.
