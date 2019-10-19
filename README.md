# Mesh Demo Examples

This application group demonstrates implementation of BLE Mesh Models. Applications included are:

- color_light:
    - Colored light shows implementation of the Light HSL, Hue and Saturation models.
- dimmer:
    - Implementation of a simple dimmer based on the Level Client model.
- light_dimmable:
    - Implementation of a dimmable light based on the BLE Mesh Light Lightness Server model.
- light_smart:
    - Implementation of a smart light based on the Light Lightness and LC models.
- low\_power\_led:
    - Implementation of a low power LED system, includes Low Power Server and Friend Node.
- on\_off\_switch:
    - Implementation of an On Off Switch.
- sensor_hub:
    - Sensor hub app showing implementation of the BLE Mesh Sensor Server model.
- sensor_motion:
    - Motion sensor app showing implementation of the BLE Mesh Sensor Server model.
- sensor_temperature:
    - Temperature sensor app showing implementation of BLE Mesh Sensor Server model.
- switch_smart:
    - Implementation of a motion sensor combined with the on off button functionality.

Each app directory has a read_me.txt file which provides details of the application and usage.

### Supported board

These apps are meant for the WICED BT board name mentioned in the name of the app repo. Every board may not support all apps listed above.
# wiced_btsdk

## Folder structure
All BTSDK code examples need 'wiced\_btsdk' repo to build and test the apps. 'wiced\_btsdk' includes the 'dev-kit' and 'tools' folders:

**dev-kit**

This folder contains the files that are needed to build the embedded BT apps.

* baselib : Files for chips supported by BTSDK. For example CYW20819, CYW20719, etc.

* bsp : Files for BSPs (platforms) supported by BTSDK. For example CYW920819EVB-02, CYW920721B2EVK-01, etc.

* btsdk-include : Common header files needed by all apps and libraries.

* btsdk-tools : Build tools needed by BTSDK.

* libraries : Profile libraries used by BTSDK apps such as audio, BLE, HID, etc.

**tools**

This folder contains tools and utilities need to test the embedded BT apps.

* btsdk-host-apps-bt-ble : Host apps (Client Control) for BLE and BR/EDR embedded apps, demonstrates use of WICED HCI protocol to control embedded apps.

* btsdk-host-apps-mesh : Host apps (Client Control) for Mesh embedded apps, demonstrates use of WICED HCI protocol to control embedded apps.

* btsdk-peer-apps-ble: Peer apps for embedded BLE apps.

* btsdk-peer-apps-mesh: Peer apps for embedded Mesh apps.

* btsdk-peer-apps-ota: Peer apps for embedded apps that support Over The Air Firmware Upgrade.

* btsdk-utils: Utilities used in BTSDK such as BTSpy, wmbt, ecdsa256, etc.

See README.md in the sub folders for more information.


## Building code examples

**Using the ModusToolbox IDE**
1. Install ModusToolbox 2.0
2. In the ModusToolbox IDE, click the **New Application** link in the Quick Panel (or, use **File > New > ModusToolbox IDE Application**).
3. Pick your board for BTSDK.
4. First select 'wiced\_btsdk'. This project contains the SDK. It is used by all BTSDK applications. You will need to create this project just once in the working directory (i.e. Eclipse workspace).
   Note: Do not change the name of this project. All BTSDK apps use this project name in application makefiles.

5. After the 'wiced\_btsdk' project is created, click the **New Application** link again, and select the board and application you want to use.
6. Select the application in the IDE. In the Quick Panel, select **Build** to build the application.
7. To program the board (download the application), select **Program** in the Quick Panel.


**Using command line**
1. Install ModusToolbox 2.0.
2. On Windows, use Cygwin from \ModusToolbox\tools_2.0\modus-shell\Cygwin.bat to build apps.
3. git clone 'wiced\_btsdk' repo first. As mentioned earlier, this project contains the SDK used by all apps. You will need to create this project just once in the working directory. For example:
   > git clone http://(url link)/wiced_btsdk
4. git clone the BTSDK app repo [ mtb-examples-(board)-btsdk-(type) ]. The application repo directory should be at the same folder level as 'wiced_btsdk'. For example:
   > git clone http://(url link)/mtb-examples-CYW920819EVB-02-btsdk-hid

5. The 'wiced\_btsdk' repo contains references to other repos. To download all the required collateral, cd to root folder and use 'make getlibs'. For example:
   > cd wiced_btsdk
   > make getlibs
6. To build the app call make build. For example:
   > cd ../mtb-examples-CYW920819EVB-02-btsdk-hid
   > cd hid/ble_mouse/
   > make build
7. To program (download to) the board, call:
   > make qprogram
8. To build and program (download to) the board, call:
   > make program

   Note: make program = make build + make qprogram

## ModusToolbox Tools

Tools installed by ModusToolbox installer:
- Device Configurator:
      Tool to create custom pin mapping for your device.
- Bluetooth Configurator:
      Create and configure BLE GATT Database and BR/EDR SDP records for your application.

## SDK software features

- Dual mode Bluetooth stack included in the ROM (BR/EDR and BLE).
- BT stack and profile level APIs for embedded BT application development.
- WICED HCI protocol to simplify host/MCU application development.
- APIs and drivers to access on-board peripherals
- Bluetooth protocols include GAP, GATT, SMP, RFCOMM, SDP, AVDT/AVCT, BLE Mesh
- BLE and BR/EDR profile APIs, libraries and sample apps
- Support for Over-The-Air (OTA) upgrade.
- Device Configurator for creating custom pin mapping.
- Bluetooth Configurator for creating BLE GATT Database.
- Peer apps based on Android, iOS, Windows, etc. for testing and reference.
- Utilities for protocol tracing, manufacturing testing, etc.
- Documentation for APIs, datasheet, profiles and features.

## List of boards available for use with BTSDK

- CYW20819A1 chip: CYW920819EVB-02, CYBT-213043-MESH, CYBT-213043-EVAL
- CYW20820A1 chip: CYW920820EVB-02, CYW989820EVB-01
- CYW20721B2 chip: CYW920721B2EVK-01, CYW920721B2EVK-03
- CYW20719B2 chip: CYW920719B2Q40EVB-01

## Application settings

Application settings below can configured via makefile of the application or passed in via command line. Options below are available for all applications. Other application specific options might also be available and are documented in the read_me.txt for those applications.

- BT\_DEVICE\_ADDRESS
    Set the BDA (Bluetooth Device Address) for your device. The BT address is 6 bytes, for example 20819A10FFEE. By default, the SDK will set a random BDA for your device.


- UART
    - Set to the UART port you want the application to be downloaded. For example 'COM6' on Windows or '/dev/ttyWICED\_HCI\_UART0' on Linux or '/dev/tty.usbserial-000154' on macOS. By default, the SDK will auto detect the port.


- ENABLE_DEBUG
    - For HW debugging, select the option '1'. See the document [WICED-Hardware-Debugging](https://github.com/cypresssemiconductorco/btsdk-docs/blob/master/docs/WICED-Hardware-Debugging.pdf) for more information. This setting configures GPIO for SWD.
      - CYW920819EVB-02/CYW920820EVB-02: SWD signals are shared with D4 and D5, see SW9 in schematics.
      - CYBT-213043-MESH/CYBT-213043-EVAL: SWD signals are routed to P12=SWDCK and P13=SWDIO. Use expansion connectors to connect VDD, GND, SWDCK and SWDIO to your SWD Debugger probe.
      - CYW989820EVB-01: SWDCK (P02) is routed to the J13 DEBUG connector, but not SWDIO. Add a wire from J10 pin 3 (PUART CTS) to J13 pin 2 to connect GPIO P10 to SWDIO.
      - CYW920719B2Q40EVB-01: PUART RX/TX signals are shared with SWDCK and SWDIO. Remove RX and TX jumpers on J10 when using SWD. PUART and SWD cannot be used simultaneously on this board unless these pins are changed from the default configuration.
      - CYW920721B2EVK-01: SWD hardware debugging is not compatible with the CYW9BT_AUDIO board. PUART RX/TX signals are shared with SWDCK and SWDIO. Remove RX and TX jumpers on J10 when using SWD. PUART and SWD cannot be used simultaneously on this board unless these pins are changed from the default configuration.
      - CYW920721B2EVK-03: SWD hardware debugging is not supported.

## Downloading an application to a board

If you have issues downloading to the board, follow the steps below:
- Press and hold the 'Recover' button on the board.
- Press and hold the 'Reset' button on the board.
- Release the 'Reset' button.
- After one second, release the 'Recover' button.

## Using BSP (platforms)

All BSPs supported by BTSDK can be found in the \wiced_btsdk\dev-kit\bsp\ folder.

#### a. Selecting an alternative BSP

The application makefile has a default BSP. See "TARGET". The makefile also has a list of other BSPs supported by the application. See "SUPPORTED_TARGETS". To select an alternative BSP, set TARGET as one of the supported BSPs.

#### b. Custom BSP

**Multiple Apps**

To create and use a custom BSP that you want to use in mutiple applications, perform the following steps:
1. Select an existing BSP you wish to use as a template from the list of supported BSPs in the \wiced\_btsdk\dev-kit\bsp\ folder.
2. Make a copy in the same folder and rename it. For example \wiced\_btsdk\dev-kit\bsp\TARGET\_mybsp.
   **Note:** This can be done in the system File Explorer and then refresh the workspace in Eclipse to see the new project.  Delete the .git subfolder from the newly copied folder before refreshing in Eclipse.
   If done in the IDE, an error dialog may appear complaining about items in the .git folder being out of sync.  This can be resolved by deleting the .git subfolder in the newly copied folder.

3. In the new \wiced\_btsdk\dev-kit\bsp\TARGET\_mybsp folder, rename the existing/original (BSP).mk file to mybsp.mk.
4. In the application makefile, set TARGET=mybsp and add it to SUPPORTED\_TARGETS as well as TARGET\_DEVICE\_MAP.  For example: mybsp/20819A1
5. Update design.modus for your custom BSP if needed using the **Device Configurator** link under **Configurators** in the Quick Panel.
6. Update the application makefile as needed for other custom BSP specific attributes and build the application.

**Per App**

To create a custom configuration for your application from an existing BSP, perform the following steps:
1. Create a folder COMPONENT\_(BSP)\_design\_modus in your application. For example COMPONENT\_CYW920721B2EVK-03\_design\_modus
2. Copy the file design.modus from the reference BSP under \wiced\_btsdk\dev-kit\bsp\ and place the file in this folder.
3. In the application makefile, add the following two lines
   DISABLE\_COMPONENTS+=bsp\_design\_modus
   COMPONENTS+=(BSP)\_design\_modus
   (for example COMPONENTS+=CYW920721B2EVK-03\_design\_modus)
4. Building of the application will generate pin configuration source code under GeneratedSource folder in your application.


## Using libraries

All supported libraries (middleware) can be found in the \wiced_btsdk\dev-kit\libraries folder. To use a library in your application, do the following changes to the makefile in your application:
1. Update the makefile variable "COMPONENTS" to include the library.  For example:
   COMPONENTS += fw\_upgrade\_lib

2. Update the makefile variable "SEARCH\_LIBS\_AND\_INCLUDES" to point to the location of the library.  For example:
SEARCH\_LIBS\_AND\_INCLUDES+=$(CY\_SHARED\_PATH)/dev-kit/libraries/btsdk-ota
