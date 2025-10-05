# DHT22 Temperature & Humidity Sensor Interface with Arduino

![DHT22 Temperature and Humidity Sensor with Arduino](https://circuitdigest.com/sites/default/files/projectimage_mic/DHT22-Sensor-with-Arduino.jpg)

## 📋 Project Overview

This project demonstrates how to interface the [DHT22 temperature and humidity sensor with Arduino](https://circuitdigest.com/microcontroller-projects/interface-dht22-sensor-module-with-arduino) UNO to measure ambient temperature and humidity. The DHT22 is a versatile, cost-effective digital sensor that provides high-accuracy measurements with a resolution of 0.1°C for temperature and 0.1% for humidity. The sensor readings are displayed on both the Serial Monitor and an optional OLED display.

## 🎯 Features

- **High Accuracy**: Temperature measurement with ±0.5°C accuracy
- **Wide Range**: Temperature range from -40°C to +125°C
- **Low Power**: Operates on 3.3V to 5V, suitable for battery-powered projects
- **Digital Output**: Uses single-bus digital communication protocol
- **Dual Display**: Shows readings on Serial Monitor and OLED display
- **Real-time Monitoring**: Continuous temperature and humidity readings

## 🔧 Components Required

| Component | Quantity | Description |
|-----------|----------|-------------|
| Arduino UNO | 1 | Microcontroller board |
| DHT22 Sensor Module | 1 | Temperature & Humidity sensor |
| [OLED Display](https://circuitdigest.com/microcontroller-projects/interfacing-oled-display-with-arduino) (SSD1306) | 1 | 128x64 I2C OLED display (optional) |
| Jumper Wires | 3-6 | For connections |
| Breadboard | 1 | For prototyping (optional) |

## 📐 Circuit Diagram

### Pin Connections

**DHT22 to Arduino:**
- VCC → 5V
- GND → GND
- DATA → Digital Pin 2

**OLED Display to Arduino (Optional):**
- VCC → 5V
- GND → GND
- SDA → A4
- SCL → A5

## 📚 About DHT22 Sensor

### Technical Specifications

- **Temperature Range**: -40°C to +125°C
- **Temperature Accuracy**: ±0.5°C
- **Humidity Range**: 0-100% RH
- **Humidity Accuracy**: ±2% RH
- **Operating Voltage**: 3.3V - 5V DC
- **Output Signal**: Digital signal via single-bus
- **Sampling Rate**: 1Hz (once per second)
- **Resolution**: 0.1°C / 0.1% RH

### How It Works

The DHT22 sensor consists of:
- **Capacitive Humidity Sensor**: Uses a moisture-holding substrate between two electrodes. As humidity changes, the resistance between electrodes varies proportionally.
- **NTC Thermistor**: Measures temperature changes through resistance variation.
- **Onboard MCU**: Processes sensor data and communicates via single-bus protocol.

### Communication Protocol

The DHT22 uses a proprietary single-bus communication protocol:
- Data transmission takes approximately 4ms
- Total data length: 40 bits (MSB format)
- Data format: 8-bit integral RH + 8-bit decimal RH + 8-bit integral T + 8-bit decimal T + 8-bit checksum
- The MCU sends a start signal, and DHT22 responds with all 40 bits of data

## 🛠️ Installation & Setup

### 1. Install Required Libraries

Install the following libraries through Arduino IDE Library Manager:
- **DHT sensor library** by Adafruit
- **Adafruit Unified Sensor Driver**
- **Adafruit GFX Library** (for OLED)
- **Adafruit SSD1306** (for OLED)

**Installation Steps:**
1. Open Arduino IDE
2. Go to `Sketch → Include Library → Manage Libraries`
3. Search for each library and click "Install"

### 2. Hardware Setup

1. Connect the DHT22 sensor to Arduino as per the pin connections above
2. (Optional) Connect the OLED display for visual output
3. Connect Arduino to your computer via USB cable

### 3. Upload Code

1. Open the provided Arduino sketch
2. Select the correct board: `Tools → Board → Arduino UNO`
3. Select the correct port: `Tools → Port → (Your Arduino Port)`
4. Click the "Upload" button

## 💻 Code Structure

### Key Components

```cpp
// Library includes
#include <Wire.h>
#include "DHT.h"
#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>

// Sensor configuration
#define DHTTYPE DHT22
uint8_t DHTPin = 2;
DHT dht(DHTPin, DHTTYPE);

// Variables for sensor data
float Temperature;
float Humidity;
float Temp_Fahrenheit;
```

### Main Functions

- **setup()**: Initializes serial communication, DHT sensor, and OLED display
- **loop()**: Continuously reads sensor data, validates it, and displays on Serial Monitor and OLED

## 📊 Expected Output

### Serial Monitor Output
```
Humidity: 55.20% Temperature: 24.50°C 76.10°F
Humidity: 55.30% Temperature: 24.60°C 76.28°F
```

### OLED Display Output
```
Temperature:
24.5 °C

Humidity:
55.2 %
```

## 🚀 Applications

- **HVAC Systems**: Climate control automation
- **Weather Stations**: Local weather monitoring
- **Indoor Air Quality**: Monitoring home/office environments
- **Smart Home**: Temperature-based automation
- **Agriculture**: Greenhouse monitoring
- **Data Centers**: Environmental monitoring

## 🔍 Troubleshooting

### Common Issues

**"Failed to read from DHT sensor!"**
- Check wiring connections
- Ensure sensor is powered properly
- Verify correct pin assignment in code
- Wait 2 seconds after power-up for sensor to stabilize

**Incorrect Readings**
- Ensure sensor is not exposed to direct heat sources
- Allow sensor to stabilize for a few seconds
- Check for loose connections

**OLED Display Not Working**
- Verify I2C address (default: 0x3C)
- Check SDA/SCL connections
- Test I2C scanner to confirm address

## 📖 Related Projects

- [Temperature-Controlled Fan using Arduino](https://circuitdigest.com/microcontroller-projects/automatic-temperature-controlled-fan-project)
- [ESP Mesh Network Configuration](https://circuitdigest.com/microcontroller-projects/how-to-configure-an-esp-mesh-network-using-arduino-ide-to-communicate-between-esp32-esp8266-and-nodemcu)
- [Automatic AC Temperature Controller](https://circuitdigest.com/microcontroller-projects/arduino-automatic-ac-temperature-control)
- [IoT Weather Station using NodeMCU](https://circuitdigest.com/microcontroller-projects/esp12-nodemcu-based-iot-weather-station)
- [Arduino Projects](https://circuitdigest.com/arduino-projects)

## 📝 Code Customization

### Modify Sensor Pin
```cpp
uint8_t DHTPin = 2; // Change to your preferred pin
```

### Change Temperature Unit
```cpp
// For Celsius only
Temperature = dht.readTemperature();

// For Fahrenheit
Temperature = dht.readTemperature(true);
```

### Adjust Reading Interval
```cpp
delay(1000); // Change delay time (in milliseconds)
```

## 📄 License

This project is open-source and available for educational and commercial purposes.

## 🔗 Reference

Full tutorial and detailed explanation available at:
[Interface DHT22 Sensor Module with Arduino](https://circuitdigest.com/microcontroller-projects/interface-dht22-sensor-module-with-arduino)

## 👥 Contributing

Feel free to fork this project and submit pull requests for improvements or bug fixes.

## 📧 Support

For questions and support, visit the Circuit Digest community forums or leave a comment on the project page.

---

**Note**: Ensure you use genuine DHT22 sensors for accurate readings. Many counterfeit sensors are available in the market with inferior performance.

**Happy Making! 🛠️**
