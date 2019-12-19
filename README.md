# Indoor Positioning Using ESP32, MQTT and BLE
A proof of concept demonstrating tracking of an asset in a warehouse using ESP32 stations to track an asset using BLE device attached to it.
The dashboard is built using React framework hosted by node.js server running on Raspberry Pi.
Dump the code of ESP32 station in ESP32 module and run the dashboard app on the Raspberry Pi.

# Credit to : 
 Initial Framework : https://github.com/jarkko-hautakorpi/iBeacon-indoor-positioning-demo

# Algorithm :
1) Each ESP32 module is connected to the Raspberry Pi 3B+ with their respective MAC addresses via MQTT Protocol

2) Each ESP32 module is hardcoded with MAC address of BLE device that needs to be tracked. This will filter out all other emitting BLE devices and only sniffs for the required device.  

3) ESP32 modules continuously scan for the BLE device. 

4) If BLE device is visible to all three ESP32 modules, then the server receive RSSI values (On the process of implementing the method of using more than three modules and when the BLE device is in indoor premise, then the server should filter out three highest RSSI values). 

5) Each ESP32 module sends their respective RSSI values and their MAC address as payload to the Raspberry PI 3B+ using MQTT Subscribe- Publish protocol. 

6) Trilateration algorithm is made to run on the received RSSI values and position is determined.

7) Using a React application the Position of the BLE Beacon is displayed on the Raspberry Pi display.

# Flowchart :

![image](https://user-images.githubusercontent.com/23289685/71164563-5e7d2800-2275-11ea-87c5-21ec9154e113.png)
