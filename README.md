# LEDMatrix_Clock8001Client
This is a modified version of the LED Matrix Clock project that integrates Clock8001 UDP time sync, DS3231 RTC, web configuration, and automatic MM:SS fallback when hours are zero.

🕒 Displays time cleanly on a 32×8 LED matrix (4x MAX7219 modules)
🌐 Web interface for configuration
📡 Syncs time via UDP (Clock8001) and optionally NTP
🧠 Optional DS3231 RTC support
🔁 IP address scrolls once on boot

# ✅ Features
Fixed-position display of HH:MM:SS (or MM:SS when hours are zero)

Receives time via UDP from Clock8001 on port 1245

Automatic fallback to MM:SS when hour is 00

Configuration via onboard web interface (SSID/password, brightness, RTC toggle, display mode)

Scrolls the IP address at boot for easy identification

Includes support for reversing the LED matrix orientation via pin

DS3231 Real-Time Clock (optional, configurable via web UI)

OTA reboot via web interface

# 🧱 Hardware Requirements
32×8 LED Matrix (4 modules using MAX7219)

ESP8266 board (e.g. NodeMCU or Wemos D1 mini)

DS3231 RTC module (optional, but supported)

Optional orientation pin (GPIO16 used for flip detection)

Recommended display available here:
https://www.aliexpress.com/item/1005006038630745.html?spm=a2g0o.productlist.main.3.2e19xSgIxSgIvR&algo_pvid=2317a5b2-14a8-43c3-b7d9-8846f9d89285&algo_exp_id=2317a5b2-14a8-43c3-b7d9-8846f9d89285-1&pdp_npi=4%40dis%21AUD%2127.59%2127.59%21%21%21129.96%21129.96%21%40210313e917294119806227360eea63%2112000035948797670%21sea%21AU%21115880849%21X&curPageLogUid=o6XdcoAv7kMW&utparam-url=scene%3Asearch%7Cquery_from%3A

# 🔌 UDP Format (Clock8001)
This clock listens for UDP broadcasts on port 1245. It expects packets that contain:
/clock/state,issssiHHMMSS
The last 6 characters are extracted and interpreted as HHMMSS in ASCII, or located via search if null characters are present.

# 🌐 Web Configuration
When first powered or after Wi-Fi failure, the device enters AP mode as:

SSID: MatrixClock_Config
IP:   192.168.4.1

# Configurable via web:

Wi-Fi SSID / password

Brightness (0–15)

Time offset (hh:mm:ss)

RTC on/off toggle

Display mode: HH:MM:SS or MM:SS

Date scroll (legacy, not active in fixed mode)

# 📂 Files Included
LEDMatrix_Clock8001Client.ino – Main code

- Fonts for time rendering (font1, font2)

- Web UI served from ESP8266

- RTC logic

- UDP parsing with fallback handling

- MAX7219 initialization and rendering logic

# 👷‍♂️ Credits
Originally based on a HACK Labs project.
Modified and maintained by Adrian Davis for Clock8001 integration and visual stability.
