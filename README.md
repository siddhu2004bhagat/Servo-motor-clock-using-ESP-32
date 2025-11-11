⏰ Servo Clock Using ESP32 and NTP

This project implements a digital clock using ESP32, multiple servo motors, and a 7-segment display structure. It fetches the current time over WiFi using an NTP server and updates the servo-driven segments in real-time.

✨ Features

⏱ Displays current time (hours and minutes) on servo-driven 7-segment digits.

🌐 Real-time synchronization using NTP server.

🕰 Works in different time zones (default: IST, UTC+5:30).

⚙️ Supports calibration for precise segment positions.

🔧 Modular design for Hour Tens, Hour Units, Minute Tens, Minute Units.

🛠 Hardware Requirements

ESP32 Dev Board

8 Servo Motors (for 4 digits × 7 segments)

I2C PWM servo drivers (2 × PCA9685)

Jumper wires and power supply for servos

Optional: breadboard or custom PCB for connections

💻 Software Requirements

Arduino IDE or compatible editor

Libraries:

WiFi.h (ESP32 core)

time.h

Wire.h

SevenSegment library for servo-driven digits

Access to WiFi network for NTP synchronization

⚡ Setup Instructions

Connect the hardware:

ESP32 SDA → Servo driver SDA

ESP32 SCL → Servo driver SCL

Servo motors connected to PWM channels of PCA9685 boards.

Configure WiFi and timezone:

Set ssid and password for your WiFi network.

Set TimeZone as per your region.

🟢 Calibration (Mandatory First Step)

⚠️ Highlighted Step:

Before running the clock normally, uncomment the CalibrateServos(); line in setup().

Upload the code to the ESP32.

The servos will move all segments to 88:88 – this allows you to physically adjust and fine-tune each segment.

After calibration, comment out CalibrateServos(); again, then upload the code again to start the real-time clock. ✅

Run the clock:

After calibration, the code fetches time from the NTP server and updates each servo to reflect the current hour and minute. ⏰

🧩 How It Works

Time Sync: The ESP32 connects to your WiFi and requests the current time from pool.ntp.org. 🌐

Time Conversion: Hour and minute values are split into tens and units. 🔢

Servo Update: Each segment of the 7-segment display is controlled by a servo, which moves to its ON/OFF position according to the number to display. 🎯

Looping: The clock checks the time every 250ms and updates servos only when minutes change, reducing unnecessary servo movement. 🔄

⚠️ Notes

Servos should have sufficient power to avoid jitter. 🔋

Ensure the calibration step is done before running the clock normally – this is essential for proper functioning. 🛠

Timezone can be adjusted by modifying the TimeZone variable. 🌍

🛠 Troubleshooting

Servos not moving: Check connections and PCA9685 addresses. ❌

WiFi not connecting: Confirm SSID/password and WiFi strength. 📶

Incorrect time: Ensure NTP server is reachable and timezone is set correctly. ⏳

📚 References

NTP Protocol Documentation 🌐

ESP32 WiFi and Time Libraries 💻

PCA9685 Servo Driver Datasheet ⚙️
