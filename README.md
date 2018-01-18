# 1-WireBeckhoffPLC
1-Wire Communication for Beckhoff PLCs

Currently supported 1-Wire adapters:

* **DS9097U** Universal 1-Wire COM Port Adapter

Currently supported 1-Wire sensors:

* **DS18S20** Temperature sensor
* **DS18B20** Temperature sensor

Currently supported Beckhoff modules:

* **EL6001** / **EL6002** Serial RS232 interfaces

1-Wire functions:

* **OneWireAdapterReset**: Resets the 1-Wire adapter by first sending a 0x00 byte at 4800 bps, followed by a 0xC1 byte at 9600 bps for baud rate calibration. Finally resets the 1-wire bus for adapter presence detection.

* **OneWireReset**: Resets the 1-Wire bus.

* **OneWireMatchROM**: Selects a sensor on the 1-Wire network ("Match ROM").

* **OneWireSkipROM**: Selects all sensors on the 1-Wire network ("Skip ROM").

* **OneWireCRC**: Plain 1-Wire CRC calculation...

Sensor functions:

* **DS1820ConvertTemperature**: Starts temperature conversion on all DS18S20 / DS18B20 sensors on the network.

* **DS1820ReadScratchPad**: Reads the "scratch pad" data from the selected temperature sensor, checks its CRC and calculates the temperature.

Example program:

Reads temperatures from two 1-Wire sensors.

Make sure to set the sensor ids / addresses in **temp_sensor_1_address** and **temp_sensor_2_address** first:

temp_sensor_1_address : ARRAY[1..8] OF BYTE := 16#10, 16#38, 16#9E, 16#55, 16#03, 16#08, 16#00, 16#69;
temp_sensor_2_address : ARRAY[1..8] OF BYTE := 16#10, 16#EF, 16#EF, 16#55, 16#03, 16#08, 16#00, 16#88;
