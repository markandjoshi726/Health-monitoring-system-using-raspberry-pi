# Health Monitoring System Using Raspberry Pi

An IoT-based patient health monitoring system built on the Raspberry Pi 3 Model B+. The system collects vital signs and environmental data from multiple sensors, transmits readings to an internet-connected server, and generates emergency alerts when readings cross predefined thresholds, enabling remote monitoring by doctors and caregivers.

## Features

- Real-time monitoring of heart rate, SpO2, and blood pressure
- Environmental monitoring (sound levels and patient movement/vibration)
- Threshold-based emergency alerts for prompt intervention
- Remote access to live health data over the internet
- Cost-effective and scalable design suitable for hospital and homecare settings

## Hardware

| Component | Purpose | Interface |
|-----------|---------|-----------|
| Raspberry Pi 3 Model B+ | Main controller and data processing | — |
| MAX30100 | Heart rate and SpO2 (pulse oximetry) | I2C (GPIO2/GPIO3) |
| KY-038 | Environmental sound/noise level detection | Digital + Analog |
| SW-420 | Patient movement/vibration detection | Digital |
| SSCMRRN005PGAA5 | Blood pressure (piezoresistive pressure sensor) | Analog |
| MCP3008 | ADC for analog sensors (Pi has no native analog input) | SPI |

## Software & Tools

- **Raspberry Pi OS (32-bit)** — operating system
- **Raspberry Pi Imager** — flashing the OS to microSD
- **Python 3** — sensor reading, data processing, and alert logic
- **PuTTY** — remote SSH access to the Pi
- **VNC Viewer** — remote GUI access

## System Architecture

Sensors capture patient vitals and environmental data, which the Raspberry Pi reads via I2C, SPI (through the MCP3008 ADC), and GPIO. The Pi processes the readings, compares them against safe thresholds, and pushes the data to a medical server for remote access. Alerts are triggered when any reading exceeds its defined limit.

## Getting Started

### Prerequisites

- Raspberry Pi 3 Model B+ with Raspberry Pi OS installed
- Sensors wired as described in the Hardware section
- Python 3 installed (included with Raspberry Pi OS)

### Setup

1. Flash Raspberry Pi OS to a microSD card using Raspberry Pi Imager.
2. Enable I2C and SPI interfaces:
   ```bash
   sudo raspi-config
   # Interface Options > enable I2C and SPI
   ```
3. Clone this repository:
   ```bash
   git clone https://github.com/<your-username>/<repo-name>.git
   cd <repo-name>
   ```
4. Install dependencies:
   ```bash
   pip3 install -r requirements.txt
   ```
5. Run the main script:
   ```bash
   python3 main.py
   ```

## Wiring Reference

- **MAX30100:** SDA → GPIO2, SCL → GPIO3 (I2C)
- **MCP3008:** connected via SPI; blood pressure and sound analog outputs routed through it
- **SW-420:** digital output to a GPIO pin

## Authors

- **Markand Joshi** — Department of Electronics & Communication, Institute of Technology, Nirma University
- **Pankti Hedau** — Department of Electronics & Communication, Institute of Technology, Nirma University

## License

This project is released under the MIT License. See the `LICENSE` file for details.
