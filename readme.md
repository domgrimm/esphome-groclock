# ESPHome Groclock Emulator

<img src=https://github.com/domgrimm/esphome-groclock/raw/refs/heads/main/resources/wake_photo.jpeg width=250><img src=https://github.com/domgrimm/esphome-groclock/raw/refs/heads/main/resources/sleep_photo.jpeg width=250>

### WIP

An ESPHome toddler sleep trainer, based on the [Groclock](https://www.target.com.au/p/the-gro-company-groclock/51891015) and written for the [Guition ESP32-S3-4848S040](https://devices.esphome.io/devices/Guition-ESP32-S3-4848S040).

Can be integrated into Home Assistant or used standalone via a built-in web server.

Install via the ESPHome Builder Home Assistant add-on. Copy the contents of `groclock.yaml` to the device configuration, changing the name and wifi details as needed.

### Features
* Set up to three separate sleep timers
* "Star countdown" around the outside of the sleep screen before wake up time
* Show/hide the current time
* Timezone picker
* Adjustable screen brightness for each mode

### To do:
* Web installer using [ESP Web Tools](https://esphome.github.io/esp-web-tools/)
* Adjust sleep timers on-device
* View wifi details (SSID, IP) on-device
* Initialising splash screen on startup
* Wifi AP details/QR code when not connected to wifi network
* Analogue clock option
* Ability to turn off/dim wake screen after period of inactivity
* Animate sun/star
* Toggle between 12H/24H digital clock