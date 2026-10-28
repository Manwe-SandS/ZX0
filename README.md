# ZX0 unpacker for BK-0010

Small [ZX0](https://github.com/einar-saukas/ZX0) decompressors for the Elektronika BK-0010 (PDP-11), written in PDP-11 assembly.

(c) Manwe/SandS, 2024
https://manwe.pdp-11.ru

PDP-11 version by Manwe, 02-may-2024, thanks to reddie.

## Files

| File | Format | Packed with | Unpacker size |
|---|---|---|---|
| `unpack-zx0-classic.mac` | ZX0 v1 classic | `zx0 -c` | 80 bytes |
| `unpack-zx0-v2.mac` | ZX0 v2.2 standard | `zx0` | 86 bytes |
| `packed-classic.zx0`, `packed-v2.zx0` | sample packed data used by the examples | | |

The classic format gives the smaller unpacker. Get the compressor here: https://github.com/einar-saukas/ZX0

## Usage

The unpacker is a subroutine `Unpack`:

- `R1` = source data address (compressed)
- `R2` = address for decompressing data

Each source file is a complete example: it calls `Unpack` for a packed file included with `insert_file` and unpacks it to address 40000 (octal). It is written for [PDPy11](https://github.com/imachug/pdpy11) syntax.

To run the unpacker several times, uncomment the `MOV +-1,(R3)` line at the start of `Unpack`, which resets the offset kept inside the code.
