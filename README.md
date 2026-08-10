# Indoor Positioning System (IPS)

GPS signals are generally unavailable or unreliable inside buildings, which is why **Indoor Positioning Systems (IPS)** are used to determine the location of objects or people in environments where satellite-based positioning cannot operate reliably.

This project explores two distinct approaches for indoor localization and tracking:

- an **UHF RFID-based tracking system**, using passive UHF RFID tags, a fixed RFID reader, and an **ESP8266** for communication and data transmission;
- a **Bluetooth Low Energy (BLE)-based localization system**, using RSSI measurements, dynamic radio-channel calibration, distance estimation, trilateration, and an **ESP32-based custom hardware platform**.

The two approaches address indoor positioning from different perspectives.  
The RFID system focuses on detecting and tracking tagged objects through known reader coverage areas, while the BLE system estimates the position of a target using radio-signal measurements.

## Studied Approaches

### UHF RFID Tracking

The first concept is based on **passive UHF RFID technology**.

<p align="center">
  <img src="assets/rfid/uhf-rfid-system-architecture.png" width="700">
</p>

<p align="center">
  <em>UHF RFID tracking system architecture.</em>
</p>
 

Passive RFID tags attached to objects are detected by fixed UHF RFID readers installed at predefined locations. When a tag enters the reader's coverage area, the reader retrieves its unique identifier.

The RFID reader communicates with an **ESP8266** through an **RS232-to-TTL converter**. The ESP8266 then uses Wi-Fi connectivity to transmit the detected tag information toward a local server, where the data can be stored, processed, and visualized.

This architecture provides a way to identify tagged objects and monitor their movement through known indoor detection areas.

### BLE Indoor Localization

The second concept is based on **Bluetooth Low Energy (BLE)** and aims to estimate the position of a target inside an indoor environment.

<p align="center">
  <img src="assets/ble/ble-localization-architecture.png" width="700">
</p>

<p align="center">
  <em>BLE localization process based on calibration, ranging and positioning.</em>
</p>

The system uses a BLE transmitter associated with the target and **three fixed BLE anchors** whose positions are known.

The anchors measure the received signal strength (**RSSI**) from the target. Since RSSI values are strongly affected by the indoor environment, the proposed method first performs a dynamic calibration of the radio-propagation parameters.

The calibrated RSSI measurements are then converted into estimated distances between the target and each anchor. These distances are finally processed using **2D trilateration** to estimate the position of the target as coordinates `(x, y)`.

An **ESP32** was selected as the hardware platform for the BLE system because it integrates BLE and Wi-Fi capabilities and can be used as the basis of the localization node.
