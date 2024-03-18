# Psion3-Wari
This game was released as freeware in 1997. The code is now made available for those interested in such things.

## Compiling Wari

You will need:

- **DOS:** A DOS computer, VM or emulator (tested with DOSBox Staging 0.81.0)
- **SDK:** Psion SIBO C SDK 2.20
- **Compiler:** JPI/Clarion TopSpeed C 3.10
- **Make:** Either of the following.
  - GNU Make for DOS (from DJGPP - tested with 4.4) with the latest version of `CWSDPMI.EXE`
  - Borland Make (tested with 3.6)

### Using GNU Make
```batch
make
```

### Using Borland Make
```batch
make -fwari.mak
```

