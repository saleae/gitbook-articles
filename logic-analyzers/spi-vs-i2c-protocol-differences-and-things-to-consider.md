# SPI vs I2C Protocol Differences and Things to Consider

## SPI vs I2C Protocol Differences and Things to Consider

When it comes to communicating between chips on a printed circuit board, two protocols are extremely popular: Serial Peripheral Interface \(SPI\) and Inter-Integrated Circuit \(IIC or I2C\). These wired protocols are considered "little" or "low-end," as they do not have the speed, robustness, and distances boasted by other protocols, such as USB, Ethernet, SATA, etc.

However, SPI and I2C are still popular, as they are easy to implement, requiring few components and little code, over their heavyweight cousins. Both rely on serial communication to pass data and support multiple devices on one bus. Many microcontrollers, sensors, and interfaces, such as LCDs, rely on SPI and I2C to talk to each other.

If you are designing a product and need to choose between SPI and I2C, which one do you pick?

### SPI

SPI was developed in the 1980s by Motorola as a way to communicate between their early microcontrollers and onboard peripherals, such as EEPROM. Motorola, nor any other organization, maintains any sort of standardization of the SPI protocol. As a result of this "de facto" standard, implementations can vary from manufacturer to manufacturer. Make sure you read the datasheet for each SPI-enabled part very carefully!

SPI uses four active signal lines \(which do not include power and ground lines\) to communicate between parts. These lines include:

* SCLK: Serial Clock \(controlled by master\)
* MOSI: Master Out Slave In \(controlled by master\)
* MISO: Master In Slave Out \(controlled by slave device\)
* SS: Slave Select \(controlled by master\)

With these four lines, a controlling device \(master\) can communicate with another peripheral device \(slave\).

%%%1 to 1 SPI diagram%%%

While you can have only one master on the SPI bus, you can add any number of peripherals. However, for each peripheral you add, you must add an additional SS line. In the example diagram, we must use three I/O lines, each controlling a separate peripheral.

%%%1 to 3 SPI diagram%%%

When the master device wishes to send data to or receive date from a peripheral, is starts communication by pulling the corresponding SS line low. At the same time, it activates the clock line \(toggling SCLK high and low at a given frequency\). The master device sends out data on the MOSI line while simultaneously sampling the MISO line. As a result, data can be sent between a master device and a peripheral device at the same time \(full-duplex\).

%%%SPI timing diagram%%%

SPI has four different modes that can be set, which determine how the clock operates. The master and peripheral devices must use the same mode. Mode 0 is by far the most common mode found among devices.

* Mode 0: data sampled on rising clock edge, clock idles low
* Mode 1: data sampled on falling clock edge, clock idles low
* Mode 2: data sampled on falling clock edge, clock idles high
* Mode 3: data sampled on rising clock edge, clock idles high

SPI does not specify any particular voltage levels, maximum speed rates, or addressing schemes. As a result, it is up to you to decide these factors. SPI speeds can easily exceed 10 Mbps, so make sure you read the datasheets for all your parts, as that will determine the acceptable voltages, speed limits, and supported modes.

### I2C

Philips Semiconductor \(now known as NXP Semiconductors\) created the I2C specification in 1982 to help standardize communication between chips on the same board. Using or implementing I2C does not cost anything, but NXP charges fees to allocate slave addresses.

I2C uses 2 lines \(not including power and ground\) for communication:

* SDA: Serial Data
* SCL: Serial Clock

Any number of master devices and any number of slave devices can theoretically be attached to the same bus. Both SDA and SCL lines are required to be open-drain lines. As a result, devices can only pull each line low. A pull-up resistor is required on each line to pull the line back up to high.

%%%Block diagram of several I2C devices on 1 bus%%%

To begin communication, a master device will issue a START condition, where the SDA line is pulled low while the SCL line is still high. The master then sends out the 7-bit address of the intended recipient on the bus, followed by a write bit \(0\) or read bit \(1\). If a device on the bus has that particular address, it will respond by pulling the SDA line low \(ACK bit\).

Data can then be sent by the master or peripheral device in packets of 1 byte at a time; each byte should be acknowledged by the recipient with an ACK bit. Once communication is complete, the master will issue a STOP condition by releasing the SDA line \(which will be pulled high\) and releasing the SCL line \(will also be pulled high\).

### Comparison



### Uses



### Conclusion



