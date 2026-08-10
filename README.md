# Indoor Positioning System (IPS)

GPS signals are generally unavailable or unreliable inside buildings, this is why Indoor positioning systems are used to pinpoint the location of certain objects inside structures where satellite signals cannot reach.

This project explores two distinct approaches for indoor localization : 

The first approach is based on **UHF RFID technology**. Passive RFID tags are detected by fixed UHF RFID readers installed at known locations. The reader is interfaced with an **ESP8266** through an RS232-to-TTL converter. The ESP8266 provides Wi-Fi connectivity to transmit tag detections to a server, where the information can be stored in a database and visualized. This concept is intended for indoor identification and movement tracking of tagged objects across predefined detection areas.

The second approach is based on **Bluetooth Low Energy (BLE)** and is designed to estimate the 2D position of a target. Three fixed BLE anchors measure the received signal strength (RSSI) of a BLE transmitter attached to the target. Because RSSI is strongly affected by the indoor environment, the system includes a periodic calibration stage to estimate the radio propagation parameters. The calibrated RSSI measurements are then converted into distances, which are used with 2D trilateration to estimate the target coordinates `(x, y)`.

For the BLE system, a dedicated **ESP32-based localization board** was also designed using **Altium Designer**. The hardware design includes the ESP32, power-management circuitry, Li-Ion battery charging using the TP4056, battery protection, and the required interfaces for the BLE localization node.

The repository documents the system architectures, localization methods, hardware design, PCB development, and the associated positioning algorithms.

## System Concepts

### UHF RFID Tracking

`RFID Tag → UHF RFID Reader → RS232/TTL → ESP8266 → Wi-Fi → Server / Database`

### BLE Localization

`BLE Target → 3 BLE Anchors → RSSI Calibration → Distance Estimation → Trilateration → (x, y)`
