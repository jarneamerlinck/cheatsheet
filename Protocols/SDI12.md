# Protocol SDI12
[Readme](../README.md)
## Information

> SDI12 = Serial Digital Interface at 1200 baud

- 1200 Baud
- Over 12V
- One data wire
- ASCII Caracters
- Asynchronous Transmission
- Master/slave(s)
- 62 Addresses posible (“0” to “9”, “A” to “Z”, or “a” to “z”)


## Working
Master slave communication with address. An address is given by manufacter but can be changed. Master sends an command and the slave anwsers. Multiple slaves can be on the same wire. For more then 62 slaves you need another SDI12 interface.
### Commands
- a is the address of the slave.
- {} are not part of the command but indicate what can stand there.

| What                            |  Command  | Extra info                                                  |
| ------------------------------- | :-------: | ----------------------------------------------------------- |
| Address Query                   |    ?!     | All devices will anser                                      |
| Acknowledge Active              |    a!     |                                                             |
| Send Identification             |    al!    | request compatible level, firmware version and model nummer |
| Change address of slave         |   aAb!    | b is the new address                                        |
| Start Measurement               |    aM!    |                                                             |
| Additional Measurement Commands | aM{1..9}! |                                                             |