# ESPHome Groclock V2

<img src=https://github.com/domgrimm/esphome-groclock/raw/refs/heads/main/resources/wake_photo.jpeg width=250><img src=https://github.com/domgrimm/esphome-groclock/raw/refs/heads/main/resources/sleep_photo.jpeg width=250>

A complete ESPHome project that emulates a Groclock toddler sleep trainer, designed to run on a Guition ESP32-S3-4848S040 display board.

## 🚀 Features

### **Core Sleep/Wake Functionality**
- **3 Configurable Timers**: Set up to 3 separate sleep/wake time pairs
- **Toggleable Timers**: Enable/disable timers 2 and 3 as needed
- **Next-Day Logic**: Automatically handles wake times that occur the next day
- **Star Countdown**: Visual countdown with 12 stars disappearing clockwise from 1pm position

### **Display & UI**
- **Sleep Screen**: Dim blue background with star image and animated countdown
- **Wake Screen**: Yellow background with sun image
- **Time Display**: Shows current time in HH:MM format (toggleable)
- **IP Address Display**: Tap screen to show device IP
- **Smart Screen Control**: Double-tap to toggle backlight (wake screen only)
- **Screen Off Timer**: Automatically turn off screen after configurable delay

### **Startup Sequence**
- **Setup Screen**: Shows fallback hotspot instructions with configuration URL if configured SSID isn't available
- **Automatic Transition**: Seamlessly moves to wake screen once WiFi connects

### **Brightness Controls**
- **Current Brightness**: Adjust overall screen brightness
- **Sleep Brightness**: Control brightness during sleep screen
- **Wake Brightness**: Control brightness during wake screen
- **Screen Off Timer**: Automatically turn off screen after configurable delay

### **Network & Configuration**
- **WiFi Connection**: Primary network with fallback hotspot
- **Web Interface**: Full web server with organized controls
- **Timezone Support**: Full timezone selection

### **Diagnostics & Monitoring**
- **WiFi Signal Strength**: Real-time signal monitoring
- **Uptime Tracking**: Device uptime display
- **Web Logging**: View logs through web interface
- **Restart Capability**: Remote device restart

## 📋 Requirements

### **Hardware**
- Guition ESP32-S3-4848S040 display board
- USB-C cable for flashing
- Power supply (5V)

### **Software**
- ESPHome (latest version)
- Home Assistant (optional, for integration)

## 🔧 Installation

### **1. Clone the Repository**
```bash
git clone https://github.com/domgrimm/esphome-groclock.git
cd esphome-groclock
```

### **2. Configure WiFi**
Create a `secrets.yaml` file in the project directory:
```yaml
wifi_ssid: "YOUR_WIFI_SSID"
wifi_password: "YOUR_WIFI_PASSWORD"
```

### **3. Customize Device Name**
Edit `groclock.yaml` and update the substitutions:
```yaml
substitutions:
  name: "Your Groclock Name"
  friendly_name: "Your Friendly Name"
```

### **4. Upload to Device**
1. Connect the ESP32-S3 board via USB
2. In ESPHome, add the `groclock.yaml` configuration
3. Upload the firmware to your device

## 🎮 Usage

### **Initial Setup**
1. **Power On**: Device shows "Initializing..." with animated dots
2. **WiFi Connection**: If WiFi connects, shows wake screen immediately
3. **Fallback Mode**: If no WiFi after 30 seconds, shows setup screen
4. **Hotspot Setup**: Connect to "{DeviceName} Fallback" WiFi network
5. **Configuration**: Visit http://192.168.4.1 to configure WiFi
6. **Complete**: Device transitions to wake screen once connected

### **Daily Operation**
1. **Wake Screen**: Shows sun image with current time
2. **Sleep Time**: At configured sleep time, switches to sleep screen
3. **Star Countdown**: Stars disappear clockwise as time progresses
4. **Wake Time**: At wake time, shows wake screen
5. **Screen Off**: After configurable delay, screen turns off

### **Controls**
- **Single Tap**: Show IP address for 10 seconds
- **Double Tap**: Toggle backlight on/off (wake screen only)
- **Web Interface**: Full control via ESPHome web interface

## ⚙️ Configuration

### **Timer Settings**
Configure up to 3 sleep/wake time pairs:
- **Timer 1**: Always active
- **Timer 2**: Toggleable
- **Timer 3**: Toggleable

### **Screen Rotation**
Rotate the display to match your mounting orientation:
- **0 degrees**: Normal orientation (default)
- **90 degrees**: Rotate 90° clockwise
- **180 degrees**: Rotate 180° (upside down)
- **270 degrees**: Rotate 270° clockwise

To change rotation, edit the `screen_rotation` value in `groclock.yaml`:
```yaml
substitutions:
  screen_rotation: "90"  # Change to desired rotation
```

### **Brightness Settings**
- **Current Brightness**: 0-100%
- **Sleep Brightness**: 0-100% (default: 30%)
- **Wake Brightness**: 0-100% (default: 100%)
- **Screen Off Delay**: 0.5-24 hours (default: 0.5 hours)

### **Screen Control**
- **Manual Override**: Screen stays off when manually turned off
- **Natural Transitions**: Screen turns on automatically for sleep/wake period changes
- **Double Tap**: Toggle screen on/off (wake screen only)

### **Timezone**
Select your timezone from the comprehensive list in `tz.yaml`

## 🔍 Troubleshooting

### **WiFi Connection Issues**
1. **Check Credentials**: Verify SSID and password in `secrets.yaml`
2. **Signal Strength**: Ensure good WiFi signal strength
3. **Fallback Hotspot**: Connect to device hotspot if primary WiFi fails
4. **Configuration**: Use web interface at device IP to configure

### **Display Issues**
1. **Brightness**: Adjust brightness settings in web interface
2. **Touch Response**: Ensure clean screen surface
3. **Time Display**: Check timezone and NTP server settings
4. **Screen Control**: Double-tap to toggle screen if it's off

### **Timer Issues**
1. **Time Format**: Verify 12-hour format (AM/PM)
2. **Next-Day Logic**: Ensure wake time is after sleep time
3. **Star Countdown**: Check that stars are visible and positioned correctly

### **Common Problems**
- **Device Not Booting**: Check power supply and USB connection
- **Web Interface Unavailable**: Verify device IP and network connectivity
- **OTA Updates Failing**: Ensure stable WiFi connection during updates
- **Screen Won't Turn On**: Try double-tapping the screen

## 📁 File Structure

```
esphome-groclock/
├── groclock.yaml             # Main configuration file
├── secrets.yaml              # WiFi credentials (create this)
├── readme.md                # This documentation
├── resources/
│   ├── tz.yaml             # Timezone definitions
│   ├── LCD.ttf             # LCD font file
│   ├── sun.png             # Sun image for wake screen
│   └── star.png            # Star image for sleep screen
└── LICENSE                  # Project license
```

## 🔧 Technical Details

### **Hardware Specifications**
- **Board**: Guition ESP32-S3-4848S040
- **Display**: 4.8" 480x480 IPS LCD
- **Touch**: Capacitive touchscreen
- **Processor**: ESP32-S3 dual-core 240MHz
- **Memory**: 8MB Flash, 2MB PSRAM
- **Connectivity**: WiFi, Bluetooth LE

### **Software Components**
- **Framework**: ESP-IDF
- **Display Driver**: ST7701S
- **Touch Driver**: GT911
- **Graphics**: LVGL 8.4.0
- **Font**: Custom LCD font with full character support

### **Network Configuration**
- **Primary**: WiFi station mode with fallback
- **Fallback**: Access Point mode with device name
- **Timeout**: 30-second AP timeout, 60-second reboot timeout
- **Power Save**: Disabled for responsive operation

### **Display Configuration**
- **Resolution**: 480x480 pixels
- **Color Depth**: 16-bit RGB565
- **Buffer Size**: 15% of available memory
- **Refresh Rate**: Optimized for smooth operation


## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.
