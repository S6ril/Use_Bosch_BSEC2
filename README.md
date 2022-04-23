# How to use BSEC2 Arduino Library from Bosch with Teensy 40 and ESP32

## Installation

I set up this library with 2 controllers:
* ESP32, see [How to use with ESP32](README_ESP32.md)
* TEENSY 40, see [How to use with TEENSY](README_TEENSY40.md)

After installation setup, the usage is the same for both controllers.

## Use

* Now you can open the `basic` example and select the board from Tools menu.
* Change your I2C port pins with the variable `Wire`.
* Compile and run it!


## Error

* `BME68X error code : -2`

It is a connection issue.
Check the wiring of your sensor, and the I2C adress.

* `Unable to import Pyserial`. 

Install `Pyserial` with Python : 
```
pip install pyserial
```

# Modification

My basic exemple change a little comparing to basic example for Bosch.
I display in addition to normal example:
* iaq
* static iaq
* co2 eq
* voc eq 

I also change the device adress according to my sensor.

# Credits

Libraries:
* [Bosch-BSEC2-Library](https://github.com/BoschSensortec/Bosch-BSEC2-Library)
* [Bosch-BME68x-Library](https://github.com/BoschSensortec/BME68x-Sensor-API)

