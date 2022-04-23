# How to use BSEC2 Arduino Library from Bosch with ESP32


## Setup your Arduino Environnement

For that I follow [README.md](https://github.com/BoschSensortec/Bosch-BSEC2-Library) from BSEC2 Library:

* Install Arduino IDE
* Install ESP32 board
    * Go to File->Preferences
    * Insert the following link into the "Additional Boards Manager URLs":
        ```
        https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
        ```
    * Go to Tools->Board->Boards Manager and search for "esp32"
    * Install the esp32 package

* Then modify your platform.txt.

    You can find this file:
    * Windows:
        ```
        C:\Users\username\AppData\Local\Arduino15\packages\esp32\hardware\esp32\x.x.x
        ```

    * Linux:
        ```
        home\username\.arduino15\packages\esp32\hardware\esp32\x.x.x
        ```
    
    And modifie like below:
    ```
    # These can be overridden in platform.local.txt
    compiler.c.extra_flags=
    compiler.c.elf.extra_flags=
    #compiler.c.elf.extra_flags=-v
    compiler.cpp.extra_flags=
    compiler.S.extra_flags=
    compiler.ar.extra_flags=
    compiler.elf2hex.extra_flags=
    compiler.libraries.ldflags=
    ```
    And at the line 151:

    ```
    ## Combine gc-sections, archives, and objects
    recipe.c.combine.pattern="{compiler.path}{compiler.c.elf.cmd}" "-Wl,--Map={build.path}/{build.project_name}.map" "-L{compiler.sdk.path}/lib" "-L{compiler.sdk.path}/ld" {compiler.c.elf.flags} {compiler.c.elf.extra_flags} {build.extra_flags} -Wl,--start-group {object_files} "{archive_file_path}" {compiler.c.elf.libs} {compiler.libraries.ldflags} -Wl,--end-group -Wl,-EL -o "{build.path}/{build.project_name}.elf"
    ```

And restart Arduino IDE.

## Download

Download all librairy needed (you can find it in `Library` folder).
* [Bosch-BSEC2-Library](https://github.com/BoschSensortec/Bosch-BSEC2-Library)
* [Bosch-BME68x-Library](https://github.com/BoschSensortec/BME68x-Sensor-API)

And add it to Arduino library: Sketch menu -> Include Library -> Add Zip Library

Go back [How to use](README.md)
