# Protocol SPI
[Readme](../README.md)
## Information

SPI = Serial Peripheral Interface

- Not default baut rate
- minimum 2 data wires
- Packets of 10 bits
- synchronous Transmission
- Master/Slave(s)

## Working
- 3 wires + 1 for each slave 
  - MISO en <span style="text-decoration:overline">SS</span> are optional
  
| Short                                            |           Long            | info                              |
| ------------------------------------------------ | :-----------------------: | --------------------------------- |
| SLCK/SCK                                         |       serial clock        | Clock speed from master to slaves |
| MOSI                                             | Master Output Slave Input | Data from master to slave         |
| MISO                                             | Master Input Slave Output | Data from slave to master         |
| <span style="text-decoration:overline">SS</span> |       Slave Select        | Data from slave to master         |

### Setup

1. Add Clock to used pins
2. Add Clock to used SPI-module
3. Used pins on alternate function
4. Set corresponding clockrate
5. (Only if not using the <span style="text-decoration:overline">SS</span> pin) Enalble Software slave management
6. Set Master mode
7. Set FIFO reception threshold on 1/4 (8-bit trigger)
8. Enalbe SPI