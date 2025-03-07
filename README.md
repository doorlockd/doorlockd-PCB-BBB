# doorlockd-PCB-BBB

Kicad drawing for doorlockd electronics on a Beagleboard black cape.
<img src="https://raw.githubusercontent.com/wie-niet/doorlockd-PCB-BBB/master/preview-rev0.02.png" alt="Preview doorlockd-PCB-BBB Rev0.02">

[<img src="https://raw.githubusercontent.com/wie-niet/doorlockd-PCB-BBB/master/schematic-rev0.02.png" alt="Schema doorlockd-PCB-BBB Rev0.02">](https://github.com/wie-niet/doorlockd-PCB-BBB/blob/master/schematic-rev0.02.pdf)




### component list
|Ref| |Value|
| --- | --- | --- |
|C1|C|1uF |
|C2|C|1uF|
|C3|CP|470u|
|D1|LED|LED|
|D2|1N4007|1N4007|
|D3|LED|LED|
|D4|1N4007|1N4007|
|J1|Conn_01x02|LED 1|
|J10|Conn_01x03|Duo LED|
|J11|Barrel_Jack_Switch|Barrel_Jack_Switch|
|J12|Conn_01x08|RFID RC522|
|J13|Conn_01x02|Solenoid 12V|
|J14|Conn_01x02|jumper|
|J2|Conn_01x02|Button 2|
|J3|Conn_01x02|LED 2|
|J4|Conn_01x02|Button 1|
|J5|Conn_01x02|Buzzer 12V|
|P8|Conn_02x23_Odd_Even|BeagleBone_Black_Header|
|P9|Conn_02x23_Odd_Even|BeagleBone_Black_Header|
|Q1|Q_NMOS_GDS|STU60N3LH5|
|Q2|Q_NMOS_GDS|STU60N3LH5|
|R1|R|Ω LED1 |
|R14|R|Ω DuoLED|
|R15|R|Ω DuoLED|
|R16|R|100|
|R17|R|2k2|
|R2|R|pull_up|
|R3|R|220|
|R4|R|Ω LED2|
|R5|R|pull_up|
|R6|R|220|
|R7|R|100|
|R8|R|2k2|
|U1|TSR_1-2450|TSR_1-2450|

#### LED resistor notes
Choose the resistors based on the LEDs you use.

|Led |resistors|
| --- | ---: |
|red | 100 ohm|
|green | 60 ohm|
|yellow | 48 ohm|
|blue |4 ohm|


### connected IO ports
| |port|chip,line<sup>\*1</sup>|name|
| --- | --- | --- | --- |
|IO|P8_17|gpiochip0 27|Button1|
|IO|P9_12|gpiochip1 28|Solenoid|
|IO|P9_14|gpiochip1 18|UILED1|
|IO|P8_18|gpiochip2 1|Button2|
|IO|P9_17|gpiochip0 5|RC522_SDA|
|IO|P9_22|gpiochip0 2|RC522_SCK|
|IO|P9_18|gpiochip0 4|RC522_MOSI|
|IO|P9_21|gpiochip0 3|RC522_MISO|
|IO|P9_15|gpiochip1 16|RC522_IRQ|
|IO|P9_23|gpiochip1 17|RC522_RST|
|IO|P8_13|gpiochip0 23|UI_DuoLED1r|
|IO|P8_19|gpiochip0 22|UI_DuoLED1g|
|IO|P9_16|gpiochip1 19|UILED2|
|IO|P8_9|gpiochip2 5|Buzzer|

<sub>*\*1):* GPIO Chip+line for gpiod, reference taken from https://elinux.org/Beagleboard:BeagleBone_cape_interface_spec </sub>

### Connecting PN532 board
This board was originally designed for use with the RC522 NFC reader,
but is also usable with the PN532 reader (which has better range and
reliability).

 - BBB SCK pin (`RC522_SCK`) is `UART2_RXD` -> connect to PN532 TX
 - BBB MISO pin (`RC522_MISO`) is `UART2_TXD` -> connect to PN532 RX
 - 5V can be taken from P9 pin 7 and/or 8 (needs extra pin soldered on)
