# Indoor Positioning System (IPS)

Indoor positioning is challenging because GPS signals are generally unavailable or unreliable inside buildings.  
This project studies and designs an **Indoor Positioning System (IPS)** based mainly on **Bluetooth Low Energy (BLE)**, RSSI measurements, and trilateration.

The project was developed as an engineering project at **ENSA Tangier – Université Abdelmalek Essaâdi**, in the field of Electronic and Automatic Systems Engineering.

## Project Overview

The objective of the project is to estimate the position of a mobile object inside an indoor environment using wireless radio signals.

The proposed BLE localization system uses:

- **3 fixed BLE anchors**
- A mobile BLE transmitter
- RSSI measurements
- Dynamic radio-channel calibration
- RSSI-to-distance estimation
- 2D trilateration
- An ESP32-based custom hardware platform

The project also includes a study of an alternative **UHF RFID-based tracking architecture**.

<p align="center">
  <img src="assets/ble-localization-system.png" width="600">
</p>

<p align="center">
  <em>Proposed BLE indoor localization architecture</em>
</p>

## How It Works

The BLE positioning system is divided into three main stages:

1. **Calibration**

   The propagation characteristics of the indoor environment are estimated dynamically using RSSI measurements between known BLE anchors.

2. **Ranging**

   The RSSI measured between the target and each anchor is converted into an estimated distance using a log-distance path-loss model.

3. **Positioning**

   The three estimated distances are used with 2D trilateration to calculate the position of the target.

The final position is represented by the estimated coordinates:

\[
(x, y)
\]

## Main Technologies

- Bluetooth Low Energy (BLE)
- ESP32
- RSSI
- Trilateration
- RFID / UHF RFID
- Python
- Altium Designer
- Li-Ion battery management
- TP4056 battery charger

## Hardware Design

A custom **IPS-BLE PCB** was designed using **Altium Designer**.

The board integrates the ESP32 platform, battery power circuitry, Li-Ion charging and protection circuits, and the required interfaces for the localization node.

PCB schematics, 2D layout, and 3D renders are included in the `hardware/` section of this repository.

## Repository Contents

```text
assets/        Project figures and diagrams
docs/          Technical documentation
hardware/      Altium PCB design and hardware documentation
software/      Localization algorithms and experiments
references/    Main references used during the project
