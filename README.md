"# LoRa-ABP-TTN-Atmega32u4-BMP280" 


ATmega32u4

BSFrance LoRa32u4 and Adafruit Feather 32u4 LoRa Radio (RFM9x) both work and have been tested.

Tested with single channel Dragino gateway, connected to TTN. 

ABP mode. 

LMIC library by matthijskooijman. Also this program is based on example code provided with the LMIC library. 

Sleep mode of Atmega32u4 also used to save battery life. 

Sensor is GY BME/P280     (BMP280 with Temperature, Height and Pressure) 

This setup assumes the BMP280 will operate in I2C mode (and not SPI). 

MAKE SURE TO FOLLOW ALL STEPS

On your LoRa dev board Connect Pin 6 and IO1  together (required for LMIC LoRa library).  

Wire up BMP280 as follows for I2C mode:

BMP280 : Atmega  
VCC : 3V  
GND : GND  
SCL : 3  
SDA : 2  
CSB : no connection  
SD0 : no connection  
  

TTN console
=============================
Create an account in TTN. 
In TTN, create an application and add a device. In device settings change mode to ABP. Save. Make a note of the following three parameters for this device. These will later be programmed onto the chip. 

- Network Session Key
- App Session Key
- Device Addres

Important: In the device setting page, disable "Frame Counter Checks", as code does not handle this at the moment.  

In Arduino IDE
=============================
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
copy LowPower-master to
C:\Users\XXXXX\Documents\Arduino\libraries

Restart Arduino IDE

Copy the provided code (Lora-ABP-TTN-BMP280) into Arduino IDE and save as a new program. 
Modify the provided code and update 3 parameters.

- LoRaWAN NwkSKey, network session key
- LoRaWAN AppSKey, application session key
- LoRaWAN end-device address (DevAddr)

Replace them with the values copied from TTN. 

In Arduino ensure Board is set to Adafruit Feather 32u4 (works fine for BSFrance also)

Compile and upload the code. 

Note: To fit the program onto the chip, most print statements are commented out. Can only have a few enabled at a given time. 
(There are ways to reduce memory usage but I have not tested, by disabling some features in config.h (like beacon tracking and ping slots, which are not typically needed), some space can be freed up. )

Verify data is received in TTN. 

To do:

1) Check status of BMP280 sensor when Atmega is in sleep mode. I think this may need to be put to sleep. 
2) Clean up config (defined(CFG_eu868) change to AU915 and verify frequencies. I have set them all to 915 since using single channel gateway. Seems to work fine, but probably not the best setup. 
3) Proper testing of sleep mode and how this is working with LMIC, yet to measure current draw. 



