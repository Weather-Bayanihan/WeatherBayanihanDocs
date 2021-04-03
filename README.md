# WeatherBayanihanIoT
Docs and step by step guide on building your own IoT Weather Devices

## Contents
 - [About](#about)
 - [Quick start](#quick-start)
   - [Arduino Sketch](#1-arduino-sketch)
   - [Hardware PIN Configurations](#2-hardware-pin-configurations)

## About
WeatherBayanihanIoT Project is a prebuilt Arduino code that uses an ESP8266 and a number of sensors to collect weather related data such as Humidity, Temperature, and Pressure.

- **Quick Start** All Arduino and ESP8266 libraries and other dependencies are included in the project.  
- **Configurable** All related configurations are set in variables and header files. Libraries are also separately managed. For an instance, WiFi connectivity, Sensors, and LCD Screens are managed separately.
- **Modular** Each function of the projects are not dependent to each other and can be managed separately. For an instance, you may be able to turn off WiFi connectivity separately and other functions such as Sensors and LCD will still work.
- **Fast** No delays and uses non-blocking code.

## Quick Start

### 1. Arduino Sketch  
**Clone (or download) the Repository and run with your Arduino IDE**  The main branch should complie without any error. You may need to familiarize yourself with the following important CPP and header files (or modules) that composes the project.

- **WeatherBayanihanIoT** The Arduino Sketch. Shared configurations and variables are included in this file as preprocessor directives 
- **ConfigurableSerial** Manages the Serial Communications. This turns on or off Printing Serial for debugging.
- **SimpleWifiManager** Manages the WiFi connection and Captive Base Station Portal.
- **SimpleLCDManager** Manages how to print in LCD Screen
- **SensorManager** Manages which sensors are enabled or disabled. 
- **WeatherBayanihanIoTClientManager** Contains the HTTP Client and how to send data to [https://api.weather-bayanihan.ph/](https://api.weather-bayanihan.ph/) 


![WeatherBayanihan-ArduinoIDE](https://raw.githubusercontent.com/Weather-Bayanihan/WeatherBayanihanDocs/main/img/WeatherBayanihan-ArduinoIDE1.PNG)


### 2. Hardware PIN Configurations  
This library was tested in three (3) Configurations. 
1. Using ESP8266 with DHT11 and BMP180
2. Using ESP8266 with only BME280
3. Using ESP8266 with only BME280 with LCD Display 20x4 I2C 


#### Using ESP8266 with DHT11 and BMP180

![WeatherBayanihan-PINOUT-ESP8266-DHT11-BMP180](https://raw.githubusercontent.com/Weather-Bayanihan/WeatherBayanihanDocs/main/img/WeatherBayanihan-PINOUT-ESP8266-DHT11-BMP180.png)

#### Using ESP8266 with only BME280

![WeatherBayanihan-PINOUT-ESP8266-BME280](https://raw.githubusercontent.com/Weather-Bayanihan/WeatherBayanihanDocs/main/img/WeatherBayanihan-PINOUT-ESP8266-BME280.png)


#### Using ESP8266 with only BME280 with LCD Display 20x4 I2C 

![WeatherBayanihan-PINOUT-ESP8266-BME280-i2C-LCD](https://raw.githubusercontent.com/Weather-Bayanihan/WeatherBayanihanDocs/main/img/WeatherBayanihan-PINOUT-ESP8266-BME280-i2C-LCD.png)
