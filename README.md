"# LoRa-ABP-TTN-Atmega-BMP280" 

ATmega32u4

BSFrance LoRa32u4 and Adafruit Feather 32u4 LoRa Radio (RFM9x) both work and have been tested.
Tested with single channel Dragino gateway, connected to TTN. 
ABP mode. 
Sensor is GY BME/P280     (BMP280 with Temperature, Height and Pressure) 
This setup assumes the BMP280 will operate in I2C mode (and not SPI). 

For both the Lora dev boards (BSFrance/Adafruit),  Connect Pin 6 and IO1  together (required for LMIC LoRa library).

Wire up BMP280 as follows for I2C mode:

BMP280 : Atmega
VCC : 3V
GND : GND
SCL : 3
SDA : 2
CSB : no connection
SD0 : no connection



After you have downloaded and installed the latest version of Arduino IDE, you will need to start the IDE and navigate to the Preferences menu.

Add a URL to the new Additional Boards Manager URLs option.

https://adafruit.github.io/arduino-board-index/package_adafruit_index.json

Once the Board Manager opens, click on the category drop down menu on the top left hand side of the window and select Contributed.  Install "Adafruit AVR Boards" 




Install windows adafruit drivers...(not sure if necessary). Drivers here: https://github.com/adafruit/Adafruit_Windows_Drivers/releases/tag/2.3.1

In Arduino turn on versose mode (for compilation and upload). See preferences. 


Open the Arduino IDE and use the top menu to navigate to Sketch -> Include Library -> Manage Libraries... which will open the Library Manager dialog box.

In the Library Manager dialog box, enter BMP280 in the filter field to find the BMP280 driver and install.
Install the BMP280 driver. 

Also click the I2C-Sensor-Lib iLib item and install it. This is required for I²C communications with the BMP280 module.


Install LoRa libraries
Download zip file from https://github.com/matthijskooijman/arduino-lmic
Unzip
Copy arduino-lmic-master to your arduino library folder.
C:\Users\XXXXX\Documents\Arduino\libraries

Download zip file from here
https://github.com/LowPowerLab/LowPower
Unzip
copy LowPower-master to ......./Arduino/libraries

Restart Arduino IDE


Compile and upload code
