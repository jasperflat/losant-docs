# IoT Developer Kit Environment Setup

All Losant IoT Developer Kits use an ESP8266 based WiFi development board. Before you can flash the required firmware to these devices, you must setup your environment with the proper development tools. The below instructions will walk you through installing all necessary 3rd party tools. These instructions only need to be followed once and the same environment can be used for all Losant IoT developer kits.

## Install Arduino IDE
Download and install the Arduino IDE by following the instructions at:<br />
[https://www.arduino.cc/en/Main/Software](https://www.arduino.cc/en/Main/Software)

If you already have the Arduino IDE installed, it is strongly recommend that you ***download and install 1.6.7***. There have been issues with previous versions of the IDE not properly resolving libraries. We've also received reports that the newer 1.6.8 also has some issues preventing these workshops from working correctly.

## Install USB Drivers

The microcontroller boards requires a USB to UART driver that must be installed for programming. Download and install the driver for your platform by following the instructions at:

[https://www.silabs.com/products/mcu/Pages/USBtoUARTBridgeVCPDrivers.aspx](https://www.silabs.com/products/mcu/Pages/USBtoUARTBridgeVCPDrivers.aspx)

![Windows Driver Download](/images/getting-started/losant-iot-dev-kits/environment-setup/uart-driver-windows.png "Windows Download")

![Mac Driver Download](/images/getting-started/losant-iot-dev-kits/environment-setup/uart-driver-mac.png "Mac Driver Download")

## Configure Arduino IDE

Launch the Arduino IDE. Linux users typically have to open the IDE under sudo for correct permissions. In order for the board to show up as a board in Arduino, you must add the following to the “Additional Boards Manager URLs” field in the preferences. On Mac, the preferences can be found at `Arduino -> Preferences`.

```text
http://arduino.esp8266.com/stable/package_esp8266com_index.json
```

![Arduino Preferences](/images/getting-started/losant-iot-dev-kits/environment-setup/arduino-preferences.png "Arduino Preferences")

Restart the Arduino IDE.

Open the Board Manager at `Tools -> Board -> Boards Manager`. Change the Type field to `Contributed` and enter `esp8266` in the Search field. Select the esp8266 entry in the list and click the `Install` button.

![Install Board](/images/getting-started/losant-iot-dev-kits/environment-setup/install-board.png "Install Board")

Restart the Arduino IDE again. We can now configure the Arduino IDE to use the board we just installed.

Open the Arduino IDE, select the Tools menu, and change the Board to `Generic ESP8266 Module`.

![Select Board](/images/getting-started/losant-iot-dev-kits/environment-setup/select-board.png "Select Board")

After selecting the board, additional options will appear in the Tools menu. Ensure the other options are set to the following. The bold ones typically need changed from their defaults.

1. ***Flash Mode = QIO***
1. Flash Frequency = 40MHz
1. CPU Frequency = 80MHz
1. ***Flash Size = 4M 1M SPIFFS***
1. ***Reset Method = nodemcu***
1. Upload Speed = 115200

![Tools Menu](/images/getting-started/losant-iot-dev-kits/environment-setup/tools-menu.png "Tools Menu")

***Remove the microcontroller from the foam*** (if needed), and connect it to your computer with the supplied USB cable.

Use the `Tools -> Port` menu to select the port your device is connected to. This will change depending on your operating system. On a Mac, it’s always named `SLAB_USBtoUART`. On Windows it will be named `Com` and then a number, for example `Com3`.

![Select Port](/images/getting-started/losant-iot-dev-kits/environment-setup/select-port.png "Select Port")

If you don't see an entry under the port menu, double check the following:

1. Did you [install the USB driver](https://www.losant.com/kit#install-usb-drivers)?
1. Did you connect the microcontroller to your computer with the supplied USB cable?

## Install Libraries

The following workshops require a few dependencies to be installed. The first two libraries can be installed using Arduino's Library Manager. Open the manager from the `Sketch -> Include Library -> Manage Libraries` menu.

![Manage Libraries](/images/getting-started/losant-iot-dev-kits/environment-setup/manage-libraries.png "Manage Libraries")

The first required library is PubSubClient. Type that in the filter field, select the entry in the list and install the latest version.

![Install Pubsubclient](/images/getting-started/losant-iot-dev-kits/environment-setup/install-pubsubclient.png "Install Pubsubclient")

The next library is ArduinoJson. Repeat the the same process again, but this time choose the most recent non-beta version (5.0.8).

![Install ArduinoJson](/images/getting-started/losant-iot-dev-kits/environment-setup/install-arduinojson.png "Install ArduinoJson")

The last library is the Losant Arduino SDK. We'll include this library as a zip file. Download the zip from the following URL and save it somewhere convenience on your computer. You'll use this file in the next step.

[https://github.com/Losant/losant-sdk-arduino/archive/master.zip](https://github.com/Losant/losant-sdk-arduino/archive/master.zip)

Next, add the zip you just downloaded to your libraries using the `Sketch -> Include Library -> Add .ZIP Library` menu.

![Add Zip Library](/images/getting-started/losant-iot-dev-kits/environment-setup/add-zip-library-menu.png "Add Zip Library")

This will open a file browser. Simply select the zip you just downloaded.

Your environment is now properly setup to begin programming your dev kits with their needed firmware. Please continue to the instructions for each specific kit.

1. [Builder Kit Instructions](/getting-started/losant-iot-dev-kits/builder-kit/)
1. [Moisture Sensor Kit Instructions](/getting-started/losant-iot-dev-kits/moisture-sensor-kit/)
1. [Door Sensor Kit Instructions](/getting-started/losant-iot-dev-kits/door-sensor-kit/)
