# Handy Boot Loaders
Boot loaders for Atari Lynx

## Compiling Boot Loaders

The boot loaders need some additional files:

- `romsize.i`: contains the size of the ROM in bytes
- `harddefs.i`: hardware definitions as found in `6502:includes`
- `checkstring.src`: string based 16-byte hexadecimal value with checksum value
- `romdir.i`: only for `boot-epyx35.src` to include first two directory entries into loader

The compilation requires all files to be present in the same folder as the boot loader source file. You can find examples of these files in the [includes](./includes/) folder.

Compile with listing and symbols:

```
asm boot-epyx55.src +s +l +oboot.bin
```

If you want to use the DEBUG or BUILDCHECK versions, you can either alter the source code to uncomment the corresponding equate value.

```
;DEBUG		.EQ 1
;BUILDCHECK	.EQ 1
```

Alternatively, you can compile with the flag defined for compilation:

```
asm boot-epyx55.src +s +l +DDEBUG
asm boot-epyx55.src +s +l +DBUILDCHECK
```

The result will be two compiled files binaries and accompanying files with build information:

|Filename|Content|
|---|---|
|`boot-epyx35.bin`|Binary file with uploadable markers for Handebug|
|`boot2.bin`|Second stage of boot loader|
|`boot-epyx35.lst`|Listing file|
|`boot-epyx35.sym`|Symbols file for debugging in Handebug|