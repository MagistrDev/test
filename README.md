# ZME_MAKE

## Table of Contents

- [build](#build)
- [upload](#upload)
- [upload_bin](#upload-bin)
- [boot](#examples)
- [BoardInfo](#troubleshooting)
- [eraseNVM](#faq)
- [writeNVM](#contributing)
- [arduino_size](#license)
- [arduino_dummy](#license)
- [arduino_preproc](#license)
- [trace](#license)
- [radiotest](#license)
- [serialmonitor](#license)
- [pinmap](#pinmap)

### Get the list of available commands:
> zme_make -h
```shell
$ zme_make -h
usage: zme_make.py [-h]
                   {build,upload,upload_bin,boot,boardInfo,eraseNVM,writeNVM,dumpNVM,arduino_size,arduino_dummy,arduino_preproc,trace,radiotest,serialmonitor,pinmap} ...

ZWave>ME make tool for ZUno G2. Version:0.402b18 DBG_MODE:True Welcome :)

positional arguments:
  {build,upload,upload_bin,boot,boardInfo,eraseNVM,writeNVM,dumpNVM,arduino_size,arduino_dummy,arduino_preproc,trace,radiotest,serialmonitor,pinmap}
    build               Builds a sketch.
    upload              Uploads a sketch to board.
    upload_bin          Uploads a binarie file to board.
    boot                Uploads bootloader.
    boardInfo           Extracts metadata from connected Z-Uno board
    eraseNVM            Erases device NVM data completely.
    writeNVM            Writes data to device NVM memory.
    dumpNVM             Dumps NVM from device.
    arduino_size        Returns memory size allocated by sketch.
    arduino_dummy       Dummy function to meet requirements of Arduino build system.
    arduino_preproc     Makes the right name of sketch.
    trace               Trace packages.
    radiotest           Starts radio test on Z-Uno.
    serialmonitor       Starts serial monitor on defined port.
    pinmap              Creates custom pinmapping for vendor configuration.

options:
  -h, --help            show this help message and exit
```

## BUILD
<div style="margin-left: 20px;">

### Description:
> Build sketch *.ino file before upload
### Usage:
```shell
$ zme_make build [-h] [-B BUILD_DIR] [-S SOURCE_DIR] [-T TOOLS_PATH] [-lcl LIBCLANG_PATH] [-D DEFINE] [-O OPTIONS] [-C CHIP_NAME] filename
``` 
### Options:
| Option | Value | Description |
|-|-|-|
|`-h, --help`||Show help message|
|`-B, --build_dir` | BUILD_DIR | The directory where all precompiled sketch files will be stored. |
|`-S, --source_dir`| SOURCE_DIR | Directories with the additional files |
|`-T, --tools_path`| TOOLS_PATH | Path to the directory where GNU Arm Embedded Toolchain is located. |
|`-lcl, --libclang_path` | LIBCLANG_PATH | Path to the directory where libclang is located. |
|`-D, --define`| DEFINE | global define flags. |
|`-O, --options`| OPTIONS | Additional build options, e.g., '-O clean'.|
|`-C, --chip_name`| CHIP_NAME | Z-Uno chip name. ZGM130S037HGN1 is default for Z-Uno 7 (rev6).|
| `filename` ||Filename of the sketch to be built.|

### Example:

```shell
$ zme_make build -B ./build -T /usr/bin -lcl ./libclang -S ./hardware/arduino/zunoG2/cores -S ./hardware/arduino/zunoG2/libraries -S /usr/bin/arm-none-eabi/include -c ZGM130S037HGN1 RadioBlink.ino 
          ***** Building sketch:D:\ZunoG2\srcs\RadioBlink.ino *****
          -----------------------------------------------------------------------------------------------
preprocessing "RadioBlink.ino"           ..............................2) MODERN MCH+
MODERN MCH+
preprocessing "RadioBlink.ino"           ..............................                            OK
          Core version: 03.12 Channels:1
          --- Full rebuild because of preprocessing changes!
          Chip depending configuration. Chip:ZGM130S037HGN1
Gathering project files                  ..............................                            OK
compiling "em_wdog.c"                    ..............................                            OK
......
......
......
linking "RadioBlink_ino.elf"             ..............................                            OK
result "RadioBlink_ino.hex"              ..............................                            OK
signed "RadioBlink_ino_signed.bin"       ..............................                            OK
          -----------------------------------------------------------------------------------------------
          OTA firmware file: D:\ZunoG2\build\RadioBlink\\RadioBlink_ino_signed.bin
          -----------------------------------------------------------------------------------------------
          Code size:17976 bytes CRC16:cca2 compiled:93 file(s) elapsed:24.645s
```
</div>

## UPLOAD
### Options
| Option | Value | Description |
|---|---|---|
| `-h, --help` | | Show this help message and exit |
| `-d, --device` | DEVICE | Device/COM-port name |
| `-B, --build_dir` | BUILD_DIR | Directory in which all the sketches will be built |
| `-p, --params` | PARAMS | Optional board configuration parameters |
| `-O, --options` | OPTIONS | Additional build options. For example, `"-O arduino_ide"` |
| `-fr, --frequency` | `{EU, RU, US, IN, HK, CN, JP, KR, IL, MY, ANZ, US_LR, US_LR_BK}` | Modify frequency setting of the device |
| `-i, --info` | `[INFO]` | Prints board information if selected |
| `-lb, --legacy_baud` | `[LEGACY_BAUD]` | Use legacy baud rate (115200). |
| `-lu, --lic_upload` | LIC_UPLOAD | Checks ZME server for new license during upload |
| `-c, --clean_nvm` | CLEAN_NVM | Cleans user and system NVM. |
| `-ub, --ultra_baud` | ULTRA_BAUD | Use higher baud rate for file uploading |
| `-ne, --no_exentended_sapi` | `[NO_EXENTENDED_SAPI]` | Don't use large SAPI frames. ZME SAPI extension disabled. |
| `-nab, --no_auto_baud` | `[NO_AUTO_BAUD]` | Don't use auto baud detection. Use precise baud rate. Option is useful for devices without `#DTR` pin. |
| `-a, --address` | ADDRESS | Custom address for update process |

### Example
```shell
$ zme_make upload RadioBlink.ino -B ./build -p main_pow=50 -p sec=0 -fr EU -d COM9
Closing port                             ..............................                            OK
Openning port                            ..............................                            OK
Syncing with Z-Uno                       ..............................                            OK
Syncing with Z-Uno                       ..............................                            OK
--- Sketch addr:00030800
          DEVICE CFG
                Z-Wave Region:EU
                Security mode:00 Freqi:00 maxTxDb:32 adjTxDb:00 LRTxDb:00 UART:230400 extra_flags:00
Writing NVM data                         ..............................                            OK
          Elapsed:1.5935
          Sketch crc16:5d30 size:46f8 (17.74 kB)
Pushing sketch                           ..............................                            OK
Closing port                             ..............................                            OK
```

### Example
```shell
$ zme_make build RadioBlink.ino -B %DIR_OUT%\ -T %CD%\gcc3.10\bin\ -lcl %CD%\libClang -S %CD%\github\hardware\arduino\zunoG2\cores -S %CD%\github\hardware\arduino\zunoG2\libraries -S %CD%\gcc3.10\lib\gcc\arm-none-eabi\10.3.1\include -S %CD%\github\hardware\arduino\zunoG2\cores -S %CD%\github\hardware\arduino\zunoG2\libraries -S %CD%\gcc3.10\lib\gcc\arm-none-eabi\10.3.1\include

          ***** Building sketch:D:\ZunoG2\srcs\RadioBlink.ino *****
          -----------------------------------------------------------------------------------------------
preprocessing "RadioBlink.ino"           ..............................2) MODERN MCH+
MODERN MCH+
preprocessing "RadioBlink.ino"           ..............................                            OK
          Core version: 03.12 Channels:1
          --- Full rebuild because of preprocessing changes!
          Chip depending configuration. Chip:ZGM130S037HGN1
Gathering project files                  ..............................                            OK
compiling "em_wdog.c"                    ..............................                            OK
......
......
......
linking "RadioBlink_ino.elf"             ..............................                            OK
result "RadioBlink_ino.hex"              ..............................                            OK
signed "RadioBlink_ino_signed.bin"       ..............................                            OK
          -----------------------------------------------------------------------------------------------
          OTA firmware file: D:\ZunoG2\build\RadioBlink\\RadioBlink_ino_signed.bin
          -----------------------------------------------------------------------------------------------
          Code size:17976 bytes CRC16:cca2 compiled:93 file(s) elapsed:24.645s
```


## UPLOAD BIN
### Usage:
```shell
$ zme_make upload_bin [-h] [-d DEVICE] [-lb [LEGACY_BAUD]] [-ub ULTRA_BAUD] [-e [EXENTENDED_SAPI]] [-nab [NO_AUTO_BAUD]] [-a ADDRESS] filename
```
### Options
| Option | Value | Description |
|---|---|---|
| `-h`, `--help` |  | show this help message and exit |
| `-d`, `--device`| DEVICE | Device/COM-port name |
| `-lb`, `--legacy_baud` | [LEGACY_BAUD] | Use legacy baudrate (115200). |
| `-ub`, `--ultra_baud` | ULTRA_BAUD | Use higher baudrate for file uploading |
| `-e`, `--exentended_sapi` | [EXENTENDED_SAPI] | Use large SAPI frames. ZME SAPI extension enabled.
| `-nab`, `--no_auto_baud` | [NO_AUTO_BAUD] | Don't use auto baud detection. Use precise baudrate. Option is useful for devices without #DTR pin. |
| `-a`, `--address` | ADDRESS | Custom address for update process |
| `filename` | | Binarie filename|

### Example
```shell
$ zme_make upload_bin -d COM11 .\build\RadioBlink\RadioBlink_ino_signed.bin
Closing port                             ..............................                            OK
Openning port                            ..............................                            OK
Syncing with Z-Uno                       ..............................                            OK
Syncing with Z-Uno                       ..............................                            OK
--- Sketch addr:00030800
          DEVICE CFG
                Z-Wave Region:EU
                Security mode:00 Freqi:00 maxTxDb:32 adjTxDb:00 LRTxDb:00 UART:230400 extra_flags:00
Writing NVM data                         ..............................                            OK
          Elapsed:1.5978
          Sketch crc16:5d30 size:46f8 (17.74 kB)
Pushing sketch                           ..............................                            OK
Closing port                             ..............................                            OK
```

## BOOT
### Usage:
```shell
$ zme_make boot [-h] [-c CATALOG] [-f FILENAME] [-d DEVICE] [-i [INFO]] [-lb [LEGACY_BAUD]] [-t [TEST]] [-ub ULTRA_BAUD] [-ne [NO_EXENTENDED_SAPI]] [-nab [NO_AUTO_BAUD]] [-a ADDRESS]
```

### Options
| Option | Value | Description |
|---|---|---|
|`-h`, `--help` | | show this help message and exit|
| `-c`, `--catalog` | CATALOG | Bootloader calalogue. Utility asks board information and selects needed bootloader automatically. Recomended mode.
| `-f`, `--filename` | FILENAME | Bootloader filename. This mode is only for experts!
| `-d`, `--device` | DEVICE | Device/COM-port name
| `-i`, `--info` | [INFO] | prints board information if selected
| `-lb`, `--legacy_baud` | [LEGACY_BAUD] | Use legacy baudrate (115200).
| `-t`, `--test` | [TEST] | Test written image by means of read back procedure. Reduce speed. Suitable for flash memory test.
| `-ub`, `--ultra_baud` | ULTRA_BAUD | Use higher baudrate for file uploading
| `-ne`, `--no_exentended_sapi` | [NO_EXENTENDED_SAPI] | Don't use large SAPI frames. ZME SAPI extension disabled.
| `-nab`, `--no_auto_baud` | [NO_AUTO_BAUD] | Don't use auto baud detection. Use precise baudrate. Option is useful for devices without #DTR pin.
|`-a`, `--address` | ADDRESS | Custom address for update process

### Example

```shell
$ zme_make boot -d com11 -c \hardware\arduino\zunoG2\bootloaders\
BOOTLOADER
Closing port                             ..............................                            OK
Openning port                            ..............................                            OK
Syncing with Z-Uno                       ..............................                            OK
Syncing with Z-Uno                       ..............................                            OK
          Using bootloader:\hardware\arduino\zunoG2\bootloaders\zuno_bootloader_HW0704.bin
Writing NVM data                         ..............................                            OK
          Elapsed:15.1096
Loading image                            ..............................                            OK
Rebooting Chip                           ..............................                            OK
Checking image                           ..............................                            OK
Waiting for bootloader                   ..............................                            OK
Closing port                             ..............................                            OK
```

## Board info
### Usage:
```shell
$ zme_make boardInfo [-h] [-d DEVICE] [-p PARAMS] [-n NIF] [-q QR_CODE] [-lb [LEGACY_BAUD]] [-lu LIC_UPLOAD] [-ub ULTRA_BAUD] [-nab [NO_AUTO_BAUD]] [-dp DUMP_PRODUCT]
```
### Options
| Option | Value | Description |
|---|---|---|
| `-h`, `--help` |  | show this help message and exit |
| `-d`, `--device` | DEVICE | Device/COM-port name |
| `-p`, `--params` | PARAMS | Optional board configuration parameters|
| `-n`, `--nif` | NIF | Sends a set of NIF frames via radio|
| `-q`, `--qr_code` | QR_CODE | Prints QR-code to selected image file. |
| `-lb`, `--legacy_baud` | [LEGACY_BAUD] | Use legacy baudrate (115200).|
| `-lu`, `--lic_upload` | LIC_UPLOAD | Checks ZME server for new license during upload
| `-ub`, `--ultra_baud` | ULTRA_BAUD | Use higher baudrate for file uploading
| `-nab`, `--no_auto_baud` | [NO_AUTO_BAUD] | Don't use auto baud detection. Use precise baudrate. Option is useful for devices without #DTR pin. |
| `-dp`, `--dump_product` | DUMP_PRODUCT | Dumps product Z-Wave metadata into specified json-file. You'll able to use this file for SmartStart QR-code production in zme_prog7 utility.

### Example
```shell
$ zme_make boardInfo -d com11
BOARD INFO
Closing port                             ..............................                            OK
Openning port                            ..............................                            OK
Syncing with Z-Uno                       ..............................                            OK
Syncing with Z-Uno                       ..............................                            OK
          ------------------------------------------------------------------------------------
                                        Z-Uno board information
          ------------------------------------------------------------------------------------

          FIRMWARE

                 VERSION:               03.12
                 BUILD_SEQUENCE:        00004328
                 BUILD_DATETIME:        2024-07-29T20:53:31(MSK)
                 SUPPORTED_HWREV:       0704
                 KEY HASH:              8e19cc54
                 SE VERSION:            00000000

          LIMITS

                 CODE:  456704 Bytes
                 RAM:   16384 Bytes

          HARDWARE

                 CHIP_FAMILY:    ZGM13 Module (00)
                 CHIP_TYPE:      ZGM130S037HGN1 (02)
                 CHIP_UID:       84 2E 14 FF FE 6A 28 9B
                 PROD_TIME:      2024-05-29T16:11:10(MSK)
                 PROD_SN:        2
                 LOCK:           UNLOCKED
                 EXT NVM:        0

          LICENSE

                 SUB_VENDOR:    0000
                 BITMASK:       0000000000000020
                 FEATURES:      [LONG_RANGE]
                 CRC16:         ff91

          NETWORK

                 HOMEID:        f65b8f92
                 NODEID:        9

          SECURITY

                S2 DSK:         46593-06376-32171-65094-27264-38172-33243-09871
                                _____
                S2 PIN:         46593
                QR-Code:        90010369013146593063763217165094272643817233243098710010040960179202200027700528000010078008030010403005
          ------------------------------------------------------------------------------------

          SKETCH

           -- NO VALID SKETCH --
          DEVICE CFG
                Z-Wave Region:EU
                Security mode:00 Freqi:00 maxTxDb:32 adjTxDb:00 LRTxDb:00 UART:230400 extra_flags:00
Reseting chip                            ..............................                            OK
DONE
```


## Erase NVM
### Usage:
```shell
$ zme_make eraseNVM [-h] [-d DEVICE] [-r [RAW_MODE]] [-a ADDRESS] [-s SIZE] [-ub ULTRA_BAUD] [-nab [NO_AUTO_BAUD]]
```
### Options
| Option | Value | Description |
|---|---|---|
| `-h`, `--help`|  | Show this help message and exit |
| `-d`, `--device` | DEVICE | Device/COM-port name |
| `-r`, `--raw_mode` | [RAW_MODE] | Big endian/Small endian conversion |
| `-a`, `--address` | ADDRESS | Address of memory in hexadecimals |
| `-s`, `--size` | SIZE | Size of memory area to dump |
| `-ub`, `--ultra_baud` | ULTRA_BAUD | Use higher baudrate for file uploading
| `-nab`, `--no_auto_baud` | [NO_AUTO_BAUD] | Don't use auto baud detection. Use precise baudrate. Option is useful for devices without #DTR pin.

### Example
```shell
$ zme_make eraseNVM -d com11
NVM Erase
Closing port                             ..............................                            OK
Openning port                            ..............................                            OK
Syncing with Z-Uno                       ..............................                            OK
Syncing with Z-Uno                       ..............................                            OK
Closing port                             ..............................                            OK
DONE
```

## WRITE NVM
### Usage:
```shell

```
### Options
| Option | Value | Description |
|---|---|---|

## DUMP NVM
### Usage:
```shell

```
### Options
| Option | Value | Description |
|---|---|---|

## ARDUINO SIZE
### Usage:
```shell
$ zme_make arduino_size [-h] [-B BUILD_DIR] filename
```
### Options
| Option | Value | Description |
|---|---|---|
| `-h`, `--help` | | show this help message and exit |
| `-B`, `--build_dir` | BUILD_DIR | Directory in which all the sketches will be built

### Example:
```shell
$ zme_make arduino_size -B D:\build\RadioBlink RadioBlink.ino 

.text   18168
.ram    1524
```

## ARDUINO DUMMY
### Usage:
```shell

```
### Options
| Option | Value | Description |
|---|---|---|

## ARDUINO PREPROC
### Usage:
```shell

```
### Options
| Option | Value | Description |
|---|---|---|

## с
### Usage:
```shell
$ zme_make trace [-h] [-d DEVICE] [-b BAUDRATE] [-fr {EU,US,ANZ,HK,MY,IN,IL,RU,CN,US_LR,US_LR_BK,EU_LR,JP,KR,FK}] [-tp TX_POWER] [-t {MODEM,PTI}] [-i INPUT] [-f FILTER] [-ir [INPUT_REENCODE]] [-o OUTPUT]
                         [-mp MAX_PACKAGES] [-mt MAX_TIME] [-p PROFILE] [-s SEND] [-r {off,payload,full,complex,hex_app}] [-dt {auto,z-uno,sapi}] [-nab [NO_AUTO_BAUD]]
```
### Options
| Option | Value | Description |
|---|---|---|
| `-h`, `--help` | | show this help message and exit |
| `-d`, `--device` | | Device file (UNIX) or COM-port (WINDOWS) |
| `-b`, `--baudrate` | BAUDRATE | Device's baudrate.|
| `-fr`, `--frequency`| {EU, US, ANZ, HK, MY, IN, IL, RU, CN, US_LR, US_LR_BK, EU_LR, JP, KR, FK} | Defines Z-Wave region (for MODEM mode ONLY). |
| `-tp`, `--tx_power` | TX_POWER | Defines Z-Wave tx power (for MODEM mode ONLY). |
| `-t`, `--transport_type` | {MODEM,PTI} | Select needed transport protocol
| `-i`, `--input` | INPUT | Imports specified file instead of device. Utility supports *.rtp, *.json, *.zlf files.|
| `-f`, `--filter` | FILTER | Filters data. |
| `-ir`, `--input_reencode` | [INPUT_REENCODE] | Reencodes incoming data during print|
| `-o`, `--output` | OUTPUT | Dumps all received packages to specified file |
| `-mp`, `--max_packages` | MAX_PACKAGES | Stops when the packet counter reaches the set value |
| `-mt`, `--max_time` | MAX_TIME | Stops after reaching the specified time interval |
| `-p`, `--profile` | PROFILE | JSON file with Z-Wave protocol descriptions. |
| `-s`, `--send` | SEND | Sends Z-Wave message. You can send multiple messages using this parameter multiple times. You can use several modes to send messages: RAW, APP, SLP. RAW mode sends the Z-Wave message as is, everything written in the second parameter is sent without additional checks. Format: -s RAW,CH,HEXSTR Where CH is the channel through which the message is sent (0 - 100 kbps, 1 - 40kbps, 2-9.6kbps), HEXSTR is a hexadecimal string. Example: -s RAW,0,AABBCCDD00010203 sends arbitrary data via a 100 kilobit (#0) channel. APP mode generates an application-level Z-Wave package based on data provided by the user separated by commas. The user must specify the channel, home id, source node_id, destination node_id, command class.command and further parameters of this Z-Wave command, in addition, optional parameters can be specified by enumeration. Format: -s APP,CH,HOMEID,SRC_NODE_ID,DST_NODE_ID,CC.CMD,[Param1,...,ParamN][,Option1=Value1,...,OptionM=ValueM] Where: CH is the channel through which the message is sent (0 - 100 kbps, 1 - 40kbps, 2-9.6kbps), HOMEID is address of needed Z-Wave Network, SRC_NODE_ID - address of sender (fake address in this case), SRC_NODE_ID - address of receiver (fake address in this case). If you use a dot in the address, the message will be wrapped in a Multichannel, CC.CMD - Application level command class and its  command. You can use text or hexadecimal format. For example BASIC.SET or equivalently 2001. Param1...ParamN - parameters of desired command, Option1.. ptionM - options of encoder Examples: -s APP,1,FD0F1122,1,50,SWITCH_BINARY.SET,255 - sends SwitchBinary.set(255) to NodeID 50 in FD0F1122 network -s APP,1,FD0F1122,1,50,SWITCH_BINARY.SET,0,is_ack=True - sends SwitchBinary.set(0) to NodeID 50 in FD0F1122 network and requests ACK from this node -s APP,1,FD0F1122,1,50,SWITCH_BINARY.SET,0,is_ack=True,crc16_encap=True - sends SwitchBinary.set(0) to NodeID 50 in FD0F1122 network and requests ACK from this node and wraps payload to crc16 CommandClass SLP mode simply inserts a delay between the previous and next packet. Format: -s SLP,time_in_seconds Example: -s APP,1,FD0F1122,1,50,SWITCH_BINARY.SET,255,is_ack=True -s SLP,20.0 -s APP,1,FD0F1122,1,50,SWITCH_BINARY.SET,0,is_ack=True Sends a BinarySwitch.Set(255) then waits 20 seconds and sends a Binary BinarySwitch.Set(0) -r {off,payload,full,complex,hex_app}, --raw_mode {off,payload,full,complex,hex_app} Defines the raw data printing mode. "off" - data is disabled, "payload" - only payload (starting from the application-level command class), "full" - print the entire package as it is, "complex" - print the package and then its payload in parentheses, "hex_app" - hexadecimal payload data only -dt {auto,z-uno,sapi}, --device_type {auto,z-uno,sapi} Selects device type
| `-nab`, `--no_auto_baud` | [NO_AUTO_BAUD] | Don't use auto baud detection. Use precise baudrate. Option is useful for devices without #DTR pin.

## RADIO TEST
### Usage:
```shell

```
### Options
| Option | Value | Description |
|---|---|---|

## SERIAL MONITOR
### Usage:
```shell

```
### Options
| Option | Value | Description |
|---|---|---|


## PINMAP
<div style="margin-left: 20px;">

### Usage:
```shell
zme_make.py pinmap [-h] [-c {ZGM130S037HGN1,ZGM230SB27HGN,ZGM230SA27HGN,EFR32ZG23B020F512IM48,EFR32ZG23B010F512IM48,EFR32ZG23A010F512GM40}] [-s [SWD_AS_UART]] [-v VENDOR] [-pt PRODUCTTYPE_ID] [-pi PRODUCT_ID] [-pow POWER_MAX] [-efr EXTERNAL_MEMORY_FREQUENCY] [-m MAP] [-l [PINNAME_LIST]]
```
### Options:
| Option | Value |Description|
|-|-|-|

| Option | Value |Description |
|---|---|---|
| `-h, --help` | | Show help message |
| `-c` | {chip_name} | Selects the chip model |
| `-s, --swd_as_uart ` | SWD_AS_UART | Maps SWD pins to SAPI UART. SWDCLC=TX SWDIO=RX SWDO=DBG_TX |
| `-v, --vendor` | VENDOR | set Z-Wave Vendor ID |
| `-pt, --producttype_id ` | PRODUCTTYPE_ID | set Z-Wave Product Type ID |
| `-pi, --product_id` | PRODUCT_ID | set Z-Wave Product ID |
| `-pow, --power_max` | POWER_MAX | Maximum power of the end device  |
| `-efr, --external_memory_frequency` | EXTERNAL_MEMORY_FREQUENCY | Frequency of the external NVM chip SPI interface in MHz  |
| `-m, --map` | MAP | Maps selected pins. Format:   `<pinname>=<port><pin>,..,<pinname>=<port><pin>`,`#<zunopinnumber>=<port><pin>`. Where `<port>`=A..F - the cortex port, pin = 0..15 |
| `-l , --pinname_list` | | Outputs all pin names   

<details><summary>

#### Default mapping of defined names and Pin number

</summary>
<div style="margin-left: 40px;">

### PWM pins name
>  _analogWrite() Writes an analog value (PWM wave) to a pin. Can be used to light a LED varying brightnesses or drive a motor at various speeds_

| Name | Pin number #|
|-----|-------|
| PWM1 | 13 |
| PWM2 | 14 |
| PWM3 | 15 |
| PWM4 | 16 |
### ADC
> _analogRead()
Reads the value from the specified analog pin. The Z-Uno board contains a 4 channel, 10-bit analog to digital converter. This means that it will map input voltages between 0 and Vcc (about 3 V) into integer values between 0 and 1023._

| Name | Pin number #|
|-----|-------|
| A0 | 3 |
| A1 | 4 |
| A2 | 5 |
| A3 | 6 |
### Serial
> _Serial() Used for communication between the Z-Uno board and another microcontroller or a computer via UART or USB._

### Serial0
| Name | Pin number #|
|-----|-------|
| RX0 | 25 |
| TX0 | 24 |
### Serial1
| Name | Pin number #|
|-----|-------|
| RX1 | 8 |
| TX1 | 7 |
### Serial 
> _default serial port for connect to PC (upload sketch and update device)_

| Name | Pin number #|
|-----|-------|
| RX2 | 27 |
| TX2 | 26 |

### SPI0
| Name | Pin number #|
|-----|-------|
| SCK | 0 |
| MISO | 1 |
| MOSI | 2 |
| SS | 8 |

### SPI1
| Name | Pin number #|
|-----|-------|
| SCK2 | 3 |
| MISO2 | 4 |
| MOSI2 | 7 |
| SS2 | 8 |
</div></details>

<details><summary>

#### Default mapping Pin number # ZUNO
</summary>
<div style="margin-left: 40px;">
<details><summary>ZGM230S* (Z-Wave 800 Series chips)</summary>
<div style="margin-left: 40px;">

| Pin number # | Chip port |Defined pin name| Description|
|:--:|:---:|:----:|--|
| 0  | PC00 |SCK|  |
| 1  | PC01 |MISO|  |
| 2  | PC02 |MOSI|  |
| 3  | PD00 |A0 / SCK2|  |
| 4  | PA06 |A1 / MISO2|  |
| 5  | PA05 |A2|  |
| 6  | PC04 |A3|  |
| 7  | PA09 |TX1 / MOSI2|  |
| 8  | PA08 |RX1 / SS / SS2|  |
| 9  | PC09 |SCL|  |
| 10 | PA10 |SDA|  |
| 11 | PD03 |  |
| 12 | PC05 |  |
| 13 | PB01 |PWM1|  |
| 14 | PB03 |PWM2|  |
| 15 | PB04 |PWM3|  |
| 16 | PB05 |PWM4|  |
| 17 | PB06 |  |
| 18 | PD01 |  |
| 19 | PC06 |  |
| 20 | PC02 |  |
| 21 | PC03 |  |
| 22 | PC04 |  |
| 23 | PD02 |BTN / SCL1|  |
| 24 | PA03 |TX0|  |
| 25 | PA04 |RX0 / SDA1|  |
| 26 | PA2  |TX2|  |
| 27 | PA1  |RX2|  |
| 28 | PB00 | | Pin for service green led |
| 29 | PB01 | | Pin for service red led|

</div></details>

<details><summary>ZGM130S* (Z-Wave 700 Series chips)</summary>
<div style="margin-left: 40px;">

| Pin number # | Chip port |Defined pin name| Description|
|:--:|:---:|:----:|--|
| 0  | PC00 |SCK|  |
| 1  | PC01 |MISO|  |
| 2  | PC02 |MOSI|  |
| 3  | PD00 |A0 / SCK2|  |
| 4  | PA06 |A1 / MISO2|  |
| 5  | PA05 |A2|  |
| 6  | PC04 |A3|  |
| 7  | PA09 |TX1 / MOSI2|  |
| 8  | PA08 |RX1 / SS / SS2|  |
| 9  | PC09 |SCL|  |
| 10 | PA10 |SDA|  |
| 11 | PD03 |  |
| 12 | PC05 |  |
| 13 | PB01 |PWM1|  |
| 14 | PB03 |PWM2|  |
| 15 | PB04 |PWM3|  |
| 16 | PB05 |PWM4|  |
| 17 | PB06 |  |
| 18 | PD01 |  |
| 19 | PC06 |  |
| 20 | PC02 |  |
| 21 | PC03 |  |
| 22 | PC04 |  |
| 23 | PD02 |BTN / SCL1|  |
| 24 | PA03 |TX0|  |
| 25 | PA04 |RX0 / SDA1|  |
| 26 | PA2  |TX2|  |
| 27 | PA1  |RX2|  |
| 28 | PB00 | ledg | Pin for service green led |
| 29 | PB01 | ledr | Pin for service service red led|
</div>
</details>
</div>
</details>
</div>
