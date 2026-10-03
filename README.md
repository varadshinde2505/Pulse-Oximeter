# Pulse Oximeter System

A low-cost, portable, IoT-enabled pulse oximeter built around an Arduino Uno. It measures blood oxygen saturation (SpO₂) and pulse rate non-invasively using photoplethysmography (PPG), shows the readings locally, and sends them to a web platform for remote monitoring.

Academic project: K. J. Somaiya Institute of Technology, Mumbai, Dept. of Electronics and Telecommunication Engineering (AY 2024-25, ICC-Minor, Sem-IV).
Guide: Prof. Pradnya Kamble.
Team: Ayush Sharma, Varad Shinde, Prathamesh Takey.

![System design](pulse/docs/images/system-design.jpeg)

## Features

- Real-time SpO₂ and pulse rate readings on a local display
- Wireless transmission to a healthcare web interface (HTTP/MQTT)
- Database storage for long-term monitoring
- Noise filtering for cleaner signals
- Breadboard prototype, cheap and easy to reproduce
- About ±2% deviation against a commercial pulse oximeter

## Problem statement

Traditional pulse oximeters are expensive, bulky, and usually lack connectivity, which limits continuous and remote monitoring. This project builds a compact, affordable, wireless alternative.

## Hardware

| Component | Purpose |
| --- | --- |
| Arduino Uno | Main microcontroller |
| MAX30100 / MAX30103 PPG sensor | SpO₂ and pulse rate sensing |
| I2C display (LCD in the wiring diagram, OLED/SSD1306 in the slides) | Local readout |
| Breadboard, jumper wires | Prototyping |
| Resistors, battery or USB power | Circuit stability and power |

### Wiring

| Sensor pin | Arduino pin |
| --- | --- |
| VIN | 3.3V |
| GND | GND |
| SDA | A4 |
| SCL | A5 |

| Display pin | Arduino pin |
| --- | --- |
| VCC | 5V |
| GND | GND |
| SDA | A4 |
| SCL | A5 |

The sensor and display share the I2C bus (A4/A5).

![Circuit diagram](pulse/docs/images/circuit-diagram.png)

## Software

- Firmware: C/C++ (Arduino IDE) or MicroPython
- Libraries: MAX30100/MAX30103 sensor driver, SSD1306 or I2C LCD library, Wi-Fi/networking libraries (HTTP/MQTT)
- Web interface and database for receiving, storing and displaying readings

## How it works

1. Connect the sensor and display to the Arduino as shown above.
2. Firmware reads raw PPG data, filters it, and computes SpO₂ and pulse rate.
3. Readings are shown on the local display.
4. Readings are sent over Wi-Fi to the web platform and stored in a database.

![Flow diagram](pulse/docs/images/flow-diagram.png)

## Results

- Readings display in real time with minimal delay
- Data reaches the web platform and is stored for remote monitoring
- About ±2% deviation versus a commercial oximeter
- Motion artifacts cause slight variation; better filtering can reduce them

![Results](pulse/docs/images/results.png)

## Applications

Telemedicine, home care, fitness and sports, sleep monitoring, emergency use, research, high-altitude and aerospace use, preventive healthcare, education.

## Future scope

- Advanced filtering to reduce motion artifacts
- ML-based detection of irregular heart patterns and abnormal SpO₂ trends
- Mobile app and secure cloud storage
- Battery optimisation and a compact wearable version
- Extra biosensors (temperature, blood pressure)

## Repository structure

```
.
├── README.md
├── docs/
│   ├── PULSE_OXIMETER.pptx     # project presentation
│   └── images/
├── firmware/                   # add your Arduino code here
└── web/                        # add your web interface code here
```

## Publication

A research paper on this system was presented at ICAST 2024-25 and published by CRC Press / Taylor & Francis.

## License

Add a license of your choice (MIT is a common default for projects like this).
