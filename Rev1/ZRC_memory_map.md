# ZRC Memory Map
ZRC has a 2 meg x 8 DRAM that is mapped to the Z80 memory space as follow:

- Z80's top 32K memory is always mapped to top of 2meg DRAM physical memory at location 0x1F8000-0x1FFFFF
- Z80's bottom 32K memory is mapped to any 32K block of the 2meg DRAM via the bank select register as follow:
  - Bank select register is write only register located at I/O address 0x1F
  - Bank select register is 0x1F at reset which maps the highest 32K DRAM block to Z80's high and low 32K memory.
  - Bank select register may contains value from 0x0 to 0x1F; 0x0 maps DRAM's lowest 32K block to Z80's low 32K memory; 0x1 maps DRAM's next lowest 32K block to Z80's low 32K memory, so on.
ZRC has a simple serial port operating at a fixed baud rate of 115200 N-8-1. The transmit register has no buffer and the receive register has one buffer. The following is I/O address of the serial port:

- I/O address 0x80 is serial status register with read access where bit 0 is serial data ready and bit 1 is serial transmit empty. Data bits 2 to 7 are undefined.
- I/O address 0x80 is serial command register with write access where
  - writing '1' to both bit 0 and bit 1 causes it to reset,
  - writing '1' to bit 6 drives RTS output high, writing '0' to bit 6 drives RTS output low; RTS is low at reset.
  - writing '1' to bit 7 enables receive data ready interrupt; writing '0' to bit 7 disables receive data ready interrupt. Interrupt is disabled at reset.
- I/O address 0x81 is serial transmit (write) and serial receive (read).
  - An I/O write to serial transmit will cause serial transmit empty bit to go low and immediately start the serial transmission. Serial transmit empty bit will go high when transmission is completed.
  - When serial data ready bit is high, there is valid data in serial receive buffer. An I/O read of the serial receive will read the valid data and cause serial data ready bit to go low.
