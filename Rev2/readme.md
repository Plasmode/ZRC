ZRC rev2 uses SIMM30 memory as its main memory. It can accommodate up to 32 meg memory.  Rev2 is derived from ZRC [SIMM30 memory tester](../SIMM30_memory_tester) prototype

![rev2ZRC](ZRC_rev2_topview.jpg)

### Features
- Z80 at 14.7MHz
- Dual SIMM-30 sockets
- EPM7128SQC100 CPLD
  - Emulate MC6850 serial port
  - DRAM controller
  - 256 banks of 32K RAM
  - Glue logic
- Compact Flash interface
- RC2014 Bus Interface
- I2C Bus
### Design Files
- [Schematic](zrc_rev2_simm30_scm.pdf)
- [Gerber photoplots](zrc_r2_gerber.zip)
- [CPLD design](zrc_rev2_simm30_cpld_design_files_8meg_256banks.zip) files
- Bill of Materials
- Memory map

### Software
- [ROMCPLD](../Rev1/software/ZRC_rev1_64byteROM_in_CPLD.zip), 64-byte bootstrap ROM resides in CPLD
- [Serial loader](../Rev1/software/zrc_rev1_software_zrserloader.zip), 256-byte program loaded by ROMCPLD into 0xB000. ← load the binary file ZRSerld.bin
- [ZRCMon](../Rev1/software/ZRC_rev1_software_zrcmon_v07.zip), rev0.7,
- [ROMWBW for ZRC](../Rev1/software/ZRC_rev1_software_RomWBW_intelHEX.zip). This is ROMWBW binary image converted to Extended Intel Hex file to be loaded into ZRC

## TODO
explain CPLD can only handle 8meg DRAM
software compatible with rev1 of ZRC?
explain how software are loaded 
create bill of materials
create memory map
