# ESPHome Groclock V2

<img src=https://github.com/domgrimm/esphome-groclock/raw/refs/heads/main/resources/wake_photo.jpeg width=250><img src=https://github.com/domgrimm/esphome-groclock/raw/refs/heads/main/resources/sleep_photo.jpeg width=250>

## Overview

A complete ESPHome toddler sleep trainer emulator, based on the [Groclock](https://www.target.com.au/p/the-gro-company-groclock/51891015) and designed for the [Guition ESP32-S3-4848S040](https://devices.esphome.io/devices/Guition-ESP32-S3-4848S040) 480×480 smart screen.

Can be integrated into Home Assistant or used standalone via a built-in web server.

## Features

### 🕐 **Sleep Timer System**
- **Three separate timers**: Configure up to three independent sleep/wake time pairs
- **Toggleable timers**: Enable/disable timers 2 and 3 as needed
- **Next-day logic**: Automatically handles wake times before sleep times (e.g., 10 PM sleep, 7 AM wake)
- **Smart timer selection**: Automatically uses the soonest upcoming wake time

### 🌟 **Star Countdown Display**
- **12-star circle**: Stars positioned around the sleep screen in a circle
- **Clockwise countdown**: Stars disappear starting from 1 PM position
- **Visual progress**: Shows remaining time until wake time
- **Smooth transitions**: Stars fade out as time progresses

### 📱 **Interactive Controls**
- **Double-tap backlight**: Toggle screen brightness on/off with double-tap (wake screen only)
- **Single-tap IP display**: Show device IP address in top-left corner for 10 seconds
- **Touch coordinates**: Logs touch events for debugging

### 🎨 **Visual Screens**
- **Wake screen**: Yellow background (#FFCE2B) with sun image and time display
- **Sleep screen**: Blue background (#5DC5FC) with star image and star countdown
- **Time display**: Optional digital clock on both screens
- **IP address**: Shows current device IP when tapped

### 💡 **Brightness Controls**
- **Current brightness**: Real-time brightness control slider
- **Sleep brightness**: Separate brightness setting for sleep screen (default: 30%)
- **Wake brightness**: Separate brightness setting for wake screen (default: 100%)
- **Screen off timer**: Automatic screen turn-off after configurable delay (default: 0.5 hours)

### ⚙️ **Configuration Options**
- **Timezone selection**: Full timezone support using `tz.yaml` package
- **Time display toggle**: Show/hide digital clock on screen
- **Screen off delay**: Adjustable delay before screen turns off (0.5-24 hours)
- **Timer enable/disable**: Toggle individual timers on/off

### 🌐 **Network & Integration**
- **WiFi connectivity**: Automatic connection with fallback hotspot
- **Home Assistant API**: Full integration support
- **OTA updates**: Over-the-air firmware updates
- **Web interface**: Built-in web server for configuration
- **IP address display**: Tap screen to show current IP address

### 📊 **Diagnostics**
- **WiFi signal strength**: Real-time signal monitoring
- **Uptime tracking**: Device uptime display
- **Web interface**: Comprehensive configuration and monitoring
- **Logging**: Clean, minimal logging suitable for production

## Hardware Requirements

- **Board**: Guition ESP32-S3-4848S040
- **Display**: 480×480 ST7701S LCD with GT911 touchscreen
- **Power**: 5V power supply (minimum 2A recommended)
- **Network**: 2.4GHz WiFi connection

## Installation

### 1. **Create secrets.yaml**
```yaml
wifi_ssid: "YOUR_WIFI_SSID"
wifi_password: "YOUR_WIFI_PASSWORD"
```

### 2. **Install via ESPHome**
- Use ESPHome Builder Home Assistant add-on
- Copy contents of `groclock-v2.yaml` to device configuration
- Change device name and WiFi details as needed

### 3. **Configure Settings**
- Set your timezone in the web interface
- Configure sleep/wake times for your schedule
- Adjust brightness settings as needed
- Enable/disable additional timers

## Usage

### **Basic Operation**
1. **Set sleep/wake times** in the web interface
2. **Enable desired timers** (Timer 1 is always active)
3. **Device automatically switches** between sleep and wake screens
4. **Stars countdown** during sleep mode
5. **Screen turns off** after configured delay

### **Interactive Features**
- **Double-tap screen** (wake mode): Toggle backlight on/off
- **Single-tap screen**: Show IP address for 10 seconds
- **Web interface**: Full configuration and monitoring

### **Timer Configuration**
- **Timer 1**: Always active, primary sleep schedule
- **Timer 2**: Optional, can be enabled/disabled
- **Timer 3**: Optional, can be enabled/disabled
- **Smart selection**: Uses soonest upcoming wake time

## Configuration

### **Time Settings**
- **Sleep Time 1-3**: Set bedtime for each timer
- **Wake Time 1-3**: Set wake time for each timer
- **Timer Enable**: Toggle timers 2 and 3 on/off

### **Brightness Controls**
- **Current Screen Brightness**: Real-time control
- **Sleep Screen Brightness**: Default 30%
- **Wake Screen Brightness**: Default 100%
- **Screen Off Delay**: 0.5-24 hours (default: 0.5 hours)

### **Display Options**
- **Show Time**: Toggle digital clock display
- **Timezone**: Select your local timezone

## Troubleshooting

### **Common Issues**
- **WiFi connection**: Check credentials in `secrets.yaml`
- **Power supply**: Ensure stable 5V power
- **Touchscreen**: Verify GT911 configuration
- **Display**: Check ST7701S settings

### **Debug Features**
- **Web interface**: Comprehensive device monitoring
- **Touch logging**: Shows touch coordinates
- **System logs**: Device status and diagnostics

## Technical Details

### **ESP32-S3 Configuration**
- **CPU**: 240MHz
- **Flash**: 16MB
- **PSRAM**: 8MB octal mode
- **Framework**: ESP-IDF

### **Display Configuration**
- **Driver**: ST7701S
- **Resolution**: 480×480
- **Touchscreen**: GT911
- **Graphics**: LVGL 8.4.0

### **Network Features**
- **WiFi**: 2.4GHz with fallback hotspot
- **API**: Home Assistant integration
- **OTA**: Over-the-air updates
- **Web Server**: Built-in configuration interface

## License

This project is open source and available under the [LICENSE](LICENSE) file.

## Contributing

Contributions are welcome! Please feel free to submit issues and pull requests.

---

**Note**: This is a complete rewrite of the original groclock project with enhanced features, improved reliability, and comprehensive documentation. 
