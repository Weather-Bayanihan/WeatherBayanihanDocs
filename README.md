# WeatherBayanihanIoT
Docs and step by step guide on building your own IoT Weather Devices

## Contents
 - [About](#about)
 - [Quick start](#quick-start)
   - [Arduino Board Manager esp8266](#1-arduino-board-manager-esp8266)
   - [Arduino Sketch](#2-arduino-sketch)
   - [Hardware PIN Configurations](#3-hardware-pin-configurations)
   - [Connecting to the device](#4-connecting-to-the-device)
     - Powering up the device
     - Managing the IoT Device thru its Station Wi-Fi and Portal
     - Connecting the device to the Internet
     - Adding device identifications
     - Checking weather data
 - [Troubleshooting](#troubleshooting)


## About
WeatherBayanihanIoT Project is a prebuilt Arduino code that uses an ESP8266 and a number of sensors to collect weather related data such as Humidity, Temperature, and Pressure.

- **Quick Start** All Arduino and ESP8266 libraries and other dependencies are included in the project.  
- **Configurable** All related configurations are set in variables and header files. Libraries are also separately managed. For an instance, WiFi connectivity, Sensors, and LCD Screens are managed separately.
- **Modular** Each function of the projects are not dependent to each other and can be managed separately. For an instance, you may be able to turn off WiFi connectivity separately and other functions such as Sensors and LCD will still work.
- **Fast** No delays and uses non-blocking code.

## Quick Start
### 1. Arduino Board Manager esp8266

**This code is made to work with ESP8266 version 2.7.4 or 2.7.3.**

Install esp8266 core libraries using Arduino Board Manager. Go to Arduino IDE, Tools, Board, Board Manager. Search for "esp8266" and install version 2.7.4. Detailed instructions are available in the official [Arduino / ESP8266 Documentation Site](https://arduino-esp8266.readthedocs.io/en/latest/installing.html#instructions)
![WeatherBayanihan-ArduinoBoardManager](https://raw.githubusercontent.com/Weather-Bayanihan/WeatherBayanihanDocs/main/img/WeatherBayanihan-ArduinoBoardManager1.PNG)

*The only supported version for this library is 2.7.4 or 2.7.3. There are breaking changes to the Release 3.0.0 which is the latest version as of this writing. More information is located here: https://github.com/esp8266/Arduino/releases*

### 2. Arduino Sketch  
**Clone (or download) the Repository and run with your Arduino IDE**  The main branch should complie without any error. You may need to familiarize yourself with the following important CPP and header files (or modules) that composes the project. 

https://github.com/Weather-Bayanihan/WeatherBayanihanIoT

- **WeatherBayanihanIoT** The Arduino Sketch. Shared configurations and variables are included in this file as preprocessor directives 
- **ConfigurableSerial** Manages the Serial Communications. This turns on or off Printing Serial for debugging.
- **SimpleWifiManager** Manages the WiFi connection and Captive Base Station Portal.
- **SimpleLCDManager** Manages how to print in LCD Screen
- **SensorManager** Manages which sensors are enabled or disabled. 
- **WeatherBayanihanIoTClientManager** Contains the HTTP Client and how to send data to [https://api.weather-bayanihan.ph/](https://api.weather-bayanihan.ph/) 


![WeatherBayanihan-ArduinoIDE](https://raw.githubusercontent.com/Weather-Bayanihan/WeatherBayanihanDocs/main/img/WeatherBayanihan-ArduinoIDE1.PNG)


### 3. Hardware PIN Configurations  
This library was tested in three (3) configurations and combinations of sensors and LCD. The following are the PIN outs of each.
1. Using ESP8266 with DHT11 and BMP180
2. Using ESP8266 with only BME280
3. Using ESP8266 with only BME280 with LCD Display 20x4 I2C 


#### Using ESP8266 with DHT11 and BMP180

![WeatherBayanihan-PINOUT-ESP8266-DHT11-BMP180](https://raw.githubusercontent.com/Weather-Bayanihan/WeatherBayanihanDocs/main/img/WeatherBayanihan-PINOUT-ESP8266-DHT11-BMP180.png)

#### Using ESP8266 with only BME280

![WeatherBayanihan-PINOUT-ESP8266-BME280](https://raw.githubusercontent.com/Weather-Bayanihan/WeatherBayanihanDocs/main/img/WeatherBayanihan-PINOUT-ESP8266-BME280.png)


#### Using ESP8266 with only BME280 with LCD Display 20x4 I2C 

![WeatherBayanihan-PINOUT-ESP8266-BME280-i2C-LCD](https://raw.githubusercontent.com/Weather-Bayanihan/WeatherBayanihanDocs/main/img/WeatherBayanihan-PINOUT-ESP8266-BME280-i2C-LCD.png)


### 4. Connecting to the device 
1. **Powering up the device**  
  - Connect the AC Adapter to the ESP8266 thru a 220V outlet.  
  - For versions with red LED, the device should light-up.  
 
2. **Managing the IoT Device thru its Station Wi-Fi and Portal**   
  - Wait for about 5 Minutes for the device to perform start-up. The device should broadcast itself as a Wi-Fi Station and its name as its SSID.  
  - Open the network connection of your mobile phone. Search for SSID of IoT Device (N) where N is the number of your device. Use “hello123” as your password.  

![weather-bayanihan-04-connectingtodevice1](https://raw.githubusercontent.com/Weather-Bayanihan/WeatherBayanihanDocs/main/img/weather-bayanihan-04-connectingtodevice1.png)
![weather-bayanihan-04-connectingtodevice2](https://raw.githubusercontent.com/Weather-Bayanihan/WeatherBayanihanDocs/main/img/weather-bayanihan-04-connectingtodevice2.png)

  - Click connect or join and wait for the device to connect. Note that there could be a significant delay on connecting on the first try depending on the mobile phone or laptop used to configure the IoT Device 

![weather-bayanihan-04-connectingtodevice3](https://raw.githubusercontent.com/Weather-Bayanihan/WeatherBayanihanDocs/main/img/weather-bayanihan-04-connectingtodevice3.png)
![weather-bayanihan-04-connectingtodevice4](https://raw.githubusercontent.com/Weather-Bayanihan/WeatherBayanihanDocs/main/img/weather-bayanihan-04-connectingtodevice4.png)

  - Once connected to the Wi-Fi a Captive Portal may appear, depending on the phone model you are using. To standardize this guide, exit the captive portal by clicking cancel and if asked, click use without internet. guide will focus on configuring the device outside of the captive portal.

![weather-bayanihan-04-connectingtodevice5](https://raw.githubusercontent.com/Weather-Bayanihan/WeatherBayanihanDocs/main/img/weather-bayanihan-04-connectingtodevice5.png)
![weather-bayanihan-04-connectingtodevice6](https://raw.githubusercontent.com/Weather-Bayanihan/WeatherBayanihanDocs/main/img/weather-bayanihan-04-connectingtodevice6.png)

  - Using a mobile phone that is connected to the Wi-Fi network of the IoT Device, open a web browser and navigate to http://11.1.1.1/ (Address: eleven, one, one, one) and the IoT Device Portal should appear 

![weather-bayanihan-04-connectingtodevice7](https://raw.githubusercontent.com/Weather-Bayanihan/WeatherBayanihanDocs/main/img/weather-bayanihan-04-connectingtodevice7.png)

 3. **Connecting the device to the Internet**  
  - Make sure that you are connected to the station Wi-Fi of IoT Device and is able to browse the IoT Device Portal (http://11.1.1.1/). The device is already connected to the internet if it shows the “Connected To” panel with blue background 

![weather-bayanihan-04-connectingtodevice8](https://raw.githubusercontent.com/Weather-Bayanihan/WeatherBayanihanDocs/main/img/weather-bayanihan-04-connectingtodevice8.png)

 - While in the IoT Device portal, choose the Wi-Fi SSID that that has a reliable internet connection. Provide the password in the password box and tap connect. 

![weather-bayanihan-04-connectingtodevice9](https://raw.githubusercontent.com/Weather-Bayanihan/WeatherBayanihanDocs/main/img/weather-bayanihan-04-connectingtodevice9.png)
![weather-bayanihan-04-connectingtodevice10](https://raw.githubusercontent.com/Weather-Bayanihan/WeatherBayanihanDocs/main/img/weather-bayanihan-04-connectingtodevice10.png)

 - The connection between the IoT Device and the mobile phone may disconnect at this point. Wait for the IoT device to connect to the. The IoT Device will retry five (5) times if it is unable to connect. The IoT Device portal should indicate the status of its connection on its top most part of the page  

![weather-bayanihan-04-connectingtodevice11](https://raw.githubusercontent.com/Weather-Bayanihan/WeatherBayanihanDocs/main/img/weather-bayanihan-04-connectingtodevice11.png) 

 4. **Adding device identifications**  
 - The device Id is used in order for the Weather Bayanihan system to recognize a pre-built IoT device. In these steps, the pre-built IoT Device accepts the device Id generated thru the device registration in Weather Bayanihan PH  
 - Make sure that you are connected to the station Wi-Fi of IoT Device and is able to browse the IoT Device Portal (http://11.1.1.1/). On the IoT Device Portal, click the change button in the Device Name panel to open it Device Identification Page. The Device Name panel also indicates the current device name

![weather-bayanihan-04-connectingtodevice13](https://raw.githubusercontent.com/Weather-Bayanihan/WeatherBayanihanDocs/main/img/weather-bayanihan-04-connectingtodevice13.png) 

 - On the Device Identification Page, this should indicate the current device name in the blue panel. The default device name and default password (“hello123”) can be reused for this step. Although any device name or new password can be used. Note that if the device name or its password has been changed, the Wi-Fi connection between the mobile phone and the IoT Device should be re-configured. Do not yet click the change button.

![weather-bayanihan-04-connectingtodevice14](https://raw.githubusercontent.com/Weather-Bayanihan/WeatherBayanihanDocs/main/img/weather-bayanihan-04-connectingtodevice14.png) 

 - The connection between the IoT Device, the mobile phone and Wi-Fi may disconnect at this point. Wait for the IoT device to restart. 

 5. **Checking weather data**  
 - Log-in to www.weather-bayanihan.ph if you are not logged-in yet. 
 - Navigate to the registered devices page and open the device details of the registered device. Newest data should now be available as a pop-up of the pin in the device details Map. Data from the device should also be shown in the graphs 
   
![weather-bayanihan-05-weatherdata4](https://raw.githubusercontent.com/Weather-Bayanihan/WeatherBayanihanDocs/main/img/weather-bayanihan-05-weatherdata4.png)
![weather-bayanihan-05-weatherdata5](https://raw.githubusercontent.com/Weather-Bayanihan/WeatherBayanihanDocs/main/img/weather-bayanihan-05-weatherdata5.png)


## Troubleshooting 
1.	Unable to connect to station 
- Check if the device is powered on. 
- Wait for 5 mins after boot and retry.
- On the mobile phone, tap forget the station Wi-Fi network and try again. 
- Check password of the station Wi-Fi. Default password is “hello123”. 
- Known Issue: Establishing the connection between the mobile phone and demo device may take too long for first time use. 

2.	Unable to connect the Demo Device to the Wi-Fi
- Check if the device is powered on. 
- Wait for 5 mins after boot and retry.
- Check your Wi-Fi password.
- Known Issue: The station may have an issue on a crowded network where there are more than 8 to 10 Wi-Fi broadcasting at the same time. 

3.	Device not sending data
- Check if the device is powered on. 
- Check device internet connectivity as shown in the first line of the LCD.
- The device should send data during boot-up sequence. Restarting the demo device should test the sending data thru boot-up.
- Check Device Id. Update the device Id once more as described in the “Adding device identifications” step. 
- The device is unable to sense weather data. The device will not be able to send zero data or will not be accepted by Weather Bayanihan service. Check connections of the device
