
How to add a DS18B20 room temperature sensor the the tilt pi that publishes to a MQTT broker.

1) First you need a MQTT broker. I recommend to create a free "Cute Cat" account at [CloudMQTT](https://www.cloudmqtt.com/).

2) Then gather the parts as shown. A DS18B20 module, 3 single pin dupont cable and a 4.7K ohm resistor.

![Parts](https://raw.githubusercontent.com/HouseOfBeck/tiltpi_ds18b20/master/parts.jpg)

The DS18B20 is a one wire device that publishes temperature directly.

The pinout of the DS18B20 module is shown. Note, if you have a different module the pins could be different and if incorrectly connected to the Pi it could damage it.

![DS18B20 Schematic](https://raw.githubusercontent.com/HouseOfBeck/tiltpi_ds18b20/master/module.jpg)

One wire requires the use of a pullup resistor. This resistor gets soldered in between the 3.3V and Signal pins. The easiest way to do this is to add it directly to the module as shown. 

![Pullup Resistor](https://raw.githubusercontent.com/HouseOfBeck/tiltpi_ds18b20/master/layout.jpg)

With the Raspberry Pi powered off make the connections as shown. Solder it between the 2&3 on the first row of open holes from the bottom.

![Schematic](https://raw.githubusercontent.com/HouseOfBeck/tiltpi_ds18b20/master/connection.jpg)

3) Now boot the pi and configure one wire.
   First configure the operating system to enable one-wire
   
   ```
   raspi-config
   ```
   
   Next, add ds18b20 support to node-red. 
   
   ```
   npm install node-red-contrib-ds18b20-sensor
   ```
   
4) Now using the web browser navigate to the node-red instance running on your raspberry pi. Once there import the ds18b20.flow
file.

![Node Red Flow](https://raw.githubusercontent.com/HouseOfBeck/tiltpi_ds18b20/master/flow.png)

5) Configure the MQTT node using the account information (username, password, broker IP and port) from step 1. The MQTT node will show a connected message when ready.

6) Now you need a MQTT client. It's easiest to use one on your smartphone. TAndroid has one built in. If using an iPhone/iPad I recommend using [IoT OnOff](https://www.iot-onoff.com/)


