"# LoRa-ABP-TTN-Atmega-BMP280" 


BSFrance 32u4 Lora and Adafruit Feather 32u4 both work and have been tested. 

For both these boards,  Connect Pin 6 and IO1 on the board together.

After you have downloaded and installed the latest version of Arduino IDE, you will need to start the IDE and navigate to the Preferences menu.

Add a URL to the new Additional Boards Manager URLs option.

https://adafruit.github.io/arduino-board-index/package_adafruit_index.json

Once the Board Manager opens, click on the category drop down menu on the top left hand side of the window and select Contributed.  Install "Adafruit AVR Boards" 


In Arduino turn on versose mode (for compilation and upload). See preferences. 


Install windows adafruit drivers...(not sure if necessary). Drivers here: https://github.com/adafruit/Adafruit_Windows_Drivers/releases/tag/2.3.1


Open the Arduino IDE and use the top menu to navigate to Sketch ? Include Library ? Manage Libraries... which will open the Library Manager dialog box.

In the Library Manager dialog box, enter BMP280 in the filter field to find the BMP280 driver and install.

Also click the I2C-Sensor-Lib iLib item and install it for I²C communications with the BMP280 module.


Install LoRa libraries
Download zip file from https://github.com/matthijskooijman/arduino-lmic
Unzip
Copy arduino-lmic-master to ......./Arduino/libraries

Download zip file from here
https://github.com/LowPowerLab/LowPower
Unzip
copy LowPower-master to ......./Arduino/libraries

Restart Arduino IDE


Compile and upload code
