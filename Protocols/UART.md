---
topic: UART
type: protocol
site: https://en.wikipedia.org/wiki/Universal_asynchronous_receiver-transmitter
sort: hardware
date: 2023/04/21
---
---
# Protocol UART
[Readme](../README.md)
## Information

> UART = Universal Asynchronous Receiver Transmitter
(Also called RS-232, RS-485, RS-422, ...)

- Not default baut rate
- Over 5V
- 2 data wires
- Packets of 10 bits
- (A)synchronous Transmission
- 1 on 1

## Working
###  Synchronous (Not used yet)

### Asynchronous 
- 10 bits data
  - 1 start bit (Low)
  - 8 databits
  - 1 end bit (High)
### Setup
1. Add Clock to used pins
2. Used pins on alternate function
3. Pick correct alternate function
4. Init UART with the corresponding params (bautrate, endbits)

