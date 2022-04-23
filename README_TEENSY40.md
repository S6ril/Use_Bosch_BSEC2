# How to use BSEC2 Arduino Library from Bosch with TEENSY 40


## Setup your Arduino Environnement

For that I take compiler information from the [Forum Teensy](https://forum.pjrc.com/threads/61374-Using-the-BME680-with-IAQ-with-the-Teensy-3-1-3-2?highlight=bsec):

* Install `Arduino IDE`
* Install `Teensyduino` like usual.
* Then modify your platform.txt.

    You can find this file:
    * Windows:

        ```
        C:\Program Files (x86)\Arduino\hardware\teensy\avr
        ```

    Open this file in administrator, or simply copy it on desktop, modifies it and past it again in this folder.

    And modify like below:

    ```
    ## Link
    compiler.libraries.ldflags=
    recipe.c.combine.pattern="{compiler.path}{build.toolchain}{build.command.linker}" {build.flags.optimize} {build.flags.ld} {build.flags.ldspecs} {build.flags.cpu} -o "{build.path}/{build.project_name}.elf" {object_files} "{build.path}/{archive_file}" {compiler.libraries.ldflags} "-L{build.path}" {build.flags.libs}
    ```

* Restart Arduino IDE.

## Download

### Arduino library from Bosch

Download all library needed (you can find it in `Library` folder, already modify for Teensy 40).
* [Bosch-BSEC2-Library](https://github.com/BoschSensortec/Bosch-BSEC2-Library)
* [Bosch-BME68x-Library](https://github.com/BoschSensortec/BME68x-Sensor-API)

And add it to Arduino library: Sketch menu -> Include Library -> Add Zip Library


### Update the library (if you want to repeat the process)

❗ I change the src folder, to match Teensy 40 compiler complain. ❗

The library is already modified in this Github repo.

You can find on [Bosch BSEC2 Software](https://www.bosch-sensortec.com/software-tools/software/bme688-software/) the BSEC 2.x Software (not the integration example).
Download it, it will ask for an email address and send a link to download. 

> Tips : [Email](https://www.fakemail.net/)

Now you have the zip archive, you will find in `algo\normal_version\bin` a lot of version of the BSEC2 algorithm. 
Find the version which match your device:
* For Teensy 40, i take `gcc\Cortex_M7\`
You will extract those files in the library folder. 


I explain where to extract it:

* Go to the library `src` folder :
```
Documents\Arduino\libraries\Bosch-BSEC2-Library-master\src
```
* Make a new folder `imxrt1062`
* Inside make a new folder `fpv5-d16-hard`
* Now past all file depending of your microcontroller.

Finally my folder looks like:
```
Documents\Arduino\libraries\Bosch-BSEC2-Library-master
|   keywords.txt
|   library.properties
|   LICENSE.md
|   README.md
|
+---examples
+---src
    |   bsec2.cpp
    |   bsec2.h
    +---atmega2560
    +---config
    +---cortex-m0plus
    +---cortex-m3
    +---cortex-m4
    +---esp32
    +---esp8266
    +---imxrt1062
    |   \---fpv5-d16-hard
    |           bsec_datatypes.h
    |           bsec_interface.h
    |           libalgobsec.a
    |           libalgobsec.a.Size.log
    \---inc
```

Now you can restart Arduino IDE, and use BSEC algorithm.

Go back [How to use](README.md).
