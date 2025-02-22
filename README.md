# Heart Rate Monitor with MAX30102 and OLED Display

This project utilizes a MAX30102 pulse sensor and an SSD1306 OLED display to measure and display heart rate data (BPM) in real-time. It calculates both instantaneous and average heart rates, providing visual feedback on the OLED screen and serial output.

## Features
- Real-time heart rate monitoring using MAX30102 sensor
- Display of IR value, current BPM, and average BPM on OLED
- Finger detection alert (no finger placement)
- Data output via Serial Monitor (115200 baud)

## Hardware Requirements
- ESP32 development board (e.g., `ESP32-S3-DevKitC-1-N16R8V` or `ESP-WROVER-KIT`)
- MAX30102 Pulse & Proximity Sensor
- SSD1306 OLED Display (128x64 pixels, I2C)
- Jumper wires and breadboard

## Wiring Guide
| MAX30102/SSD1306 | ESP32 Board          |
|-------------------|----------------------|
| VCC               | 3.3V                 |
| GND               | GND                  |
| SDA               | GPIO21 (default SDA) |
| SCL               | GPIO22 (default SCL) |

**Note:** Verify I2C pins for your specific ESP32 board variant.

## Installation
1. **PlatformIO Setup**  
   - Install [PlatformIO](https://platformio.org/) for your IDE (VSCode recommended).
   - Clone this repository.
   - Open the project in PlatformIO.

2. **Dependencies**  
   Libraries will be automatically installed by PlatformIO:
   - [SparkFun MAX3010x Library](https://github.com/sparkfun/SparkFun_MAX3010x_Sensor_Library)
   - [Adafruit SSD1306](https://github.com/adafruit/Adafruit_SSD1306)
   - [Adafruit GFX Library](https://github.com/adafruit/Adafruit-GFX-Library)

3. **Upload Code**  
   - Connect your ESP32 via USB.
   - Build and upload the code using PlatformIO.

## Usage
1. Power the board and ensure proper sensor connections.
2. Place your index finger firmly on the MAX30102 sensor.
3. View real-time data on:
   - **OLED Display**: Shows IR value, current BPM, and average BPM.
   - **Serial Monitor**: Outputs the same data at 115200 baud rate.

## Configuration
- **Sensor Averaging**: Adjust `RATE_SIZE` in the code to change the number of readings averaged (default: 4).
- **I2C Addresses**:
  - OLED: Default `0x3C` (update in `display.begin()` if different).
  - MAX30102: Automatically detected.

## Troubleshooting
- **Sensor Not Detected**: 
  - Check I2C connections and power supply.
  - Ensure no conflicts with other I2C devices.
- **No Display Output**:
  - Confirm OLED I2C address (try `0x3D` if `0x3C` fails).
- **Inconsistent Readings**:
  - Ensure steady finger pressure on the sensor.
  - Avoid ambient light interference.

## License
MIT License. See [LICENSE](LICENSE) for details.
