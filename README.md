# Amiga Kick

Diagnostic Kickstart ROM for the Amiga: A1000 through A4000.

On boot it runs a March-U RAM test along with a 24-stage hardware diagnostic, then drops into the AMIGAMON machine-language monitor with EhBASIC.

This is a work in progress. Consider it extremely alpha and untested. Feedback welcomed!

Serial console: Paula UART, 9600 8N1. Output is mirrored to the video screen.

## Files

| File | Use |
|---|---|
| `amigamon.bin` | 512 KB, 16-bit machines, CPU byte order, for emulators |
| `amigamon_swapped.bin` | 512 KB, 16-bit machines, byte-swapped. One 27C400 EPROM (A500, A600, A2000) |
| `amigamon_1m.bin` | 1 MB, 32-bit machines, CPU byte order, for emulators |
| `amigamon_1m_32bit_hi.bin`, `_lo.bin` | 32-bit machines (A1200, A3000, A4000), byte-swapped, 512 KB each (27C400) |
| `amigamon_256k.bin` | 16-bit machines, 256 KB, CPU byte order, for emulators |
| `amigamon_256k_swapped.bin` | 16-bit machines, 256 KB, byte-swapped. One 27C200 EPROM (Kickstart 1.x sockets) |
| `superkick_amigamon.adf` | SuperKickstart ADF for early A3000s with the V36 boot ROM |

## Burning to a OneROM or an EPROM

The plain `.bin` files are in CPU byte order. A OneROM or a real EPROM
needs the two bytes of each 16-bit word traded first, so the ROM header
`11 14 4E F9` becomes `14 11 F9 4E`. The `_swapped` files are ready to
burn. The 32-bit split halves are byte-swapped as well.

## License

Amiga Kick and the AMIGAMON monitor are public domain, released under the
[Unlicense](https://unlicense.org). This covers all code not listed below.

The ROM images also contain code and music by other authors, each under its
own terms. Because the 512 KB and 1 MB images include GPL-3.0 code, those
images as a whole are distributed under GPL-3.0. The public domain parts stay
public domain when taken out on their own.

| Code | Author | License | In which images |
|---|---|---|---|
| AGFA-MON, including its CP437 font | Anonymous | Public domain (Unlicense) | All |
| EhBASIC 68K 3.54 | Lee Davison | Free for non-commercial use. | All |
| [ttft](https://github.com/ianromanick/ttft) (Terminal Tetris) | Ian Romanick | GPL-3.0-only | 512 KB and 1 MB only |
| [ptplayer](https://aminet.net/package/mus/play/ptplayer) 6.4 | Frank Wille | Public domain (Unlicense) | All |
| ProTracker modules | xtd, rez, dreamfish, Cover Action Team, wotw, emax | Copyright their authors | All (six of seven in 256 KB) |

This section is a work in progress.

## Credits

| Reference | Used for |
|---|---|
| WhichAmiga 1.3.3 (Harry "Piru" Sintonen) | Model classifier, CPU/FPU and address-bus detection, ported from its source |
| DiagROM (John "Chucky" Hertell) | Comparison testing |
| Amiga Test Kit (Keir Fraser) | The feature set of the `J` floppy test |
| [ReAmiga 3000 KiCad project](https://github.com/iansbremner/ReAmiga-3000---KiCAD) (Ian Bremner, from John "Chucky" Hertell's reverse engineering) | The A3000 chip and pin names that `W`, `A` and `K` print |
| March U (van de Goor and Gaydadjiev, 1997) | Boot RAM test and `U` |
| Jack Ganssle's memory test patterns | Bus-stress pass of the boot RAM test |
| AmigaOS 3.1 Kickstart disassembly | Boot stage order, memory sizing, autoconfig, SCSI/IDE addresses, floppy timing |
| Amiga Hardware Reference Manual, Motorola 680x0 manuals, MOS 8520 datasheet, Commodore chip specs | Register, exception frame and chip behavior |
| [vasm](http://sun.hasenbraten.de/vasm/) (Volker Barthelmann, Frank Wille) | Assembling the ROM |
| [FS-UAE](https://fs-uae.net/), WinUAE, [Copperline](https://github.com/LinuxJedi/Copperline) | Testing on every Amiga model |
