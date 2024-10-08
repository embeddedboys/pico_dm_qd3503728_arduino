### Arduino Porting For Pico_DM_QD3503728

[[中文]](README.md)[[English]](README.en.md)

- Display is based on TFT_eSPI
    ![TFT_eSPI](assets/pico_dm_qd3503728_arduino_2.jpeg)

### TODO

- [ ] refactor the ft6236u driver, make it support rotation.
- [ ] How to overclock the pico in arduio? does it effect the other libraries?
- [ ] upload this document to the github page

### Hardware Prequisites

- Raspberry Pi Pico (with BOOTSEL button)
- A Type-C USB cable

### Before you start

0. Get this repository via git clone or download the zip file

    ```bash
    git clone https://github.com/embeddedboys/pico_dm_qd3503728_arduino.git
    ```

1. Install pico board support in Arduino IDE

    > Referenced from [https://github.com/earlephilhower/arduino-pico](https://github.com/earlephilhower/arduino-pico)

    Open up the Arduino IDE and go to File->Preferences.

    In the dialog that pops up, enter the following URL in the "Additional Boards Manager URLs" field:

    https://github.com/earlephilhower/arduino-pico/releases/download/global/package_rp2040_index.json

    ![board url](assets/board_url.png)

    Hit OK to close the dialog.

    Go to Tools->Boards->Board Manager in the IDE

    Type "pico" in the search box and select "Add":

    ![install](assets/install.png)

2. Install these libraries via arduino library manager

    - TFT_eSPI
    - lvgl (version == 8.4.0)

3. Replace the `TFT_eSPI/User_Setup.h` with the one provided by this repository

```bash
cd pico_dm_qd3503728_arduino
cp User_Setup.h ~/Arduino/libraries/TFT_eSPI/
```

4. Copy the `lv_conf.h` under the `libraries` directory

```bash
cd pico_dm_qd3503728_arduino
cp lv_conf.h ~/Arduino/libraries/
```

5. If you want to build lvgl demos, you need to copy the `lvgl/demos`
directory under the `lvgl/src` directory, so did examples.

```bash
cd ~/Arduino/libraries/lvgl
cp demos/ -r src/
cp examples -r src/
```

Then the `Arduino` folder should be like this:

    ```bash
    libraries\
        lvgl\
        TFT_eSPI\
            User_Setup.h
        lv_conf.h
    ```

> (The `Arduino` folder usually at `C\Users\your_username\Documents\Arduino` on windows or `~/Arduino` on linux by default)

6. In `Arduino IDE`, go to `File->Open` and open `main/main.ino` which in this repository

7. Upload the sketch to your pico

    When the first time you upload the sketch, you need to press the BOOTSEL button on the pico then plug it to your computer. Otherwise, after you modified the sketch, you can upload it to your pico directly.

    Each time you upload the sketch, select the correct COM port is suggested.

8. Enjoy

    ![lvgl](assets/pico_dm_qd3503728_arduino.jpeg)
