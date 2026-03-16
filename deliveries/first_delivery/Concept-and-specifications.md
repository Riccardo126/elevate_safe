# Concept and specifications

## Concept
ElevateSafe is an IoT-based elevator monitoring system designed primarily for older residential buildings. The goal is to provide automatic fault and condition monitoring for low-to-medium class buildings that operate on a low budget and currently lack such systems.

### Example 1
**Monitoring Older Infrastructure**: In residential complexes with aging elevators, the system provides a low-cost way to detect faults without needing to replace or heavily modify the existing electrical system

### Example 2
**Automated Fault Detection**: The system replaces manual checks by automatically alerting operators to mechanical issues or unusual conditions, which is critical for buildings that cannot afford high-end, built-in proprietary monitoring services.

### Storyboard

- *Activation: The sensing node is activated when it detects the elevator door opening.Data
- *Collection: Once active, the node monitors the elevator's state while it is moving using inertial and environmental sensors.
- *Transmission: Collected data is sent via LoRa from the sensing node in the building to a central node.
- Cloud Processing: The central node pushes the data to a web server and cloud infrastructure for final monitoring and user access.

  
## Technology

### Brief Description
The system architecture consists of multiple sensing nodes (one for each elevator) that communicate with a single central node using LoRa technology. This setup is designed to work in environments without public Wi-Fi in every building, centralizing data before sending it to a web server.

### Components
The project utilizes the following hardware components:

- Microcontroller Board: Heltec WiFi LoRa 32 (V3).
- Inertial Measurement Unit (IMU): LSM6DS3 (6-axis) which also includes a temperature sensor.
- Magnetic Sensor: AH3503 Hall sensor used in conjunction with Neodymium magnets (20x10x3mm).
- Light Sensor: 5506 Photoresistor.

## Evaluation

The goal of this section is providing information about "evalutation" of Project. This evaluation is based on the follow constraints:

- Battery/Energy: The system must run without frequent maintenance and avoid interference with the elevator's electrical system, requiring high battery capacity and energy optimization.
- Bandwidth: Due to the lack of building-wide Wi-Fi, the system must rely on a central processing node to aggregate data via LoRa.
- Frequency: While perfect latency is not required (as it is not a security system), the sensing nodes must reliably activate and run every time the elevator is in motion.

### Performance Evaluation

The performance of ElevateSafe is measured by its ability to maintain high availability during elevator operation while remaining in a low-power state otherwise. Success is defined by the reliable detection of door triggers and floor triggering (via the Hall sensor) and the successful long-range transmission of sensor data through building walls using the LoRa protocol.

| **Products** | **Power on Active** | **Power on Idle** |
|`Heltec WiFi LoRa 32 (V3)`|Requires high capacity for transmission and processing.|Optimized for low maintenance and energy efficiency.|
|`LSM6DS3 (6-axis IMU)`|Active during elevator movement to monitor conditions.|Remains in a power-saving state until the door opens.|
|`AH3503 Hall Sensor`|Detects magnetic field when the door opens to trigger the system.|Constant low-level monitoring to act as an activation switch.|
|`5506 Photoresistor`|Active for light sensing during elevator operation.|Minimal draw when the sensing node is not triggered.|