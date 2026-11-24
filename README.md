JitterQube
A full Jitter-themed UI for the Waveshare ESP32-S3-Touch-LCD-1.83 (240x284, ST7789P + CST816D touch). Black and steel with a single red accent, square corners, red corner brackets, JetBrains Mono, and the JitterTech icon plates.

Preview

Features
Boot splash: emblem, wordmark, spinning ring, progress bar
Home: ring clock that sweeps seconds in red, RTC time and date, terminal prompt with blinking cursor
Menu: 2x3 grid of icon plates
IMU: tilt reticle with live X/Y/Z bars (QMI8658)
Wi-Fi: network scanner with signal strength
System: chip, CPU, heap, PSRAM, uptime, battery
SD / Audio: placeholder screens, not implemented yet
Hardware

Waveshare ESP32-S3-Touch-LCD-1.83: ESP32-S3R8, 1.83" IPS 240x284, CST816D touch, QMI8658 IMU, PCF85063 RTC, AXP2101 power.

Requirements
Arduino IDE with the ESP32 board package
Waveshare's bundled libraries (examples/arduino/libraries in their repo): LVGL 8.4, GFX Library for Arduino, Arduino_DriveBus, SensorLib, Mylibrary
Optional: XPowersLib for the battery readout (without it the home screen shows BAT --)
Install
Board: ESP32S3 Dev Module, USB CDC On Boot Enabled, PSRAM OPI PSRAM, Flash 16MB.
Point Arduino at Waveshare's bundled libraries folder.
Replace that folder's lv_conf.h with this project's lv_conf.h. Four lines differ from Waveshare's: FPS overlay off, UNSCII fonts on, LVGL memory 48K to 64K.
Open JitterOS/JitterOS.ino and upload.
Usage

Boot, then Home. Tap or swipe up for the Menu, then pick Clock, IMU, Wi-Fi or System. Use the red < in the header to go back. The RTC is set from the build time the first time it is found unset.

Customize
What	Where
Colors, layout, screens	JitterOS/jitter_ui.cpp (palette defines at the top)
Tilt dot direction	JITTER_IMU_FLIP_X / JITTER_IMU_FLIP_Y in jitter_ui.cpp
Icons, emblem, wordmark	python3 tools/gen_assets.py <JitterTech/tools> <wallpaper.png> JitterOS
Fonts	python3 tools/gen_fonts.py fonts JitterOS
Simulator

Run the real UI on a desktop with no board:

bash sim/build.sh <path to the lvgl library folder containing lvgl.h>

Screenshots land in sim/out/.
