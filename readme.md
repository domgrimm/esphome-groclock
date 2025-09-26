# ESPHome Groclock V2

<img src=https://github.com/domgrimm/esphome-groclock/raw/refs/heads/main/resources/wake_photo.jpeg width=250><img src=https://github.com/domgrimm/esphome-groclock/raw/refs/heads/main/resources/sleep_photo.jpeg width=250>

A complete ESPHome project that emulates a Groclock toddler sleep trainer, designed to run on multiple ESP32-S3 display boards with different form factors and capabilities.

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
- **IP Address Display**: Tap screen/button to show device IP
- **Smart Screen Control**: Double-tap/double-press to toggle backlight (wake screen only)
- **Screen Off Timer**: Automatically turn off screen after configurable delay
- **Ambient Lighting**: Optional RGB LED lighting that matches screen colors

### **Startup Sequence**
- **Setup Screen**: Shows fallback hotspot instructions with configuration URL if configured SSID isn't available
- **Automatic Transition**: Seamlessly moves to wake screen once WiFi connects

### **Brightness Controls**
- **Current Brightness**: Adjust overall screen brightness
- **Sleep Brightness**: Control brightness during sleep screen
- **Wake Brightness**: Control brightness during wake screen
- **Screen Off Timer**: Automatically turn off screen after configurable delay
- **Auto Ambient Lighting**: Toggle automatic ambient lighting that matches screen colors

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

### **Supported Hardware**
- **Guition ESP32-S3-4848S040**: 4" 480x480 square display with touchscreen
- **Spotpear Ball V2**: 1.28" 240x240 circular display with button control
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

### **3. Choose Your Device Configuration**
Select the appropriate configuration file for your hardware:

#### **For Guition ESP32-S3-4848S040 (Square Display)**
Use `Guition4848S040.yaml`:
- 4" 480x480 square display
- Capacitive touchscreen support
- Full-size UI elements

#### **For Spotpear Ball V2 (Circular Display)**
Use `BallV2.yaml`:
- 1.28" 240x240 circular display
- Button-based interaction (no touchscreen)
- Compact UI optimized for circular screen
- Ambient RGB lighting support
- Media player functionality

### **4. Customize Device Name**
Edit your chosen configuration file and update the substitutions:
```yaml
substitutions:
  name: "Your Groclock Name"
  friendly_name: "Your Friendly Name"
```

### **5. Screen Rotation (Guition Only)**
To change rotation, edit the `screen_rotation` value in `Guition4848S040.yaml`:
```yaml
substitutions:
  screen_rotation: "90"  # Change to desired rotation
```
Match your mounting orientation:
- **0**: Normal orientation (default)
- **90**: Rotate 90° clockwise
- **180**: Rotate 180° (upside down)
- **270**: Rotate 270° clockwise

### **6. Upload to Device**
1. Connect the ESP32-S3 board via USB
2. In ESPHome, add your chosen configuration file
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

#### **Guition ESP32-S3-4848S040 (Touchscreen)**
- **Single Tap**: Show IP address for 10 seconds
- **Double Tap**: Toggle backlight on/off (wake screen only)
- **Web Interface**: Full control via ESPHome web interface

#### **Spotpear Ball V2 (Button Control)**
- **Single Press**: Show IP address for 10 seconds
- **Double Press**: Toggle backlight on/off (wake screen only)
- **Ambient Lighting**: Automatic color matching or manual control
- **Media Player**: Audio playback support via Home Assistant
- **Web Interface**: Full control via ESPHome web interface

## ⚙️ Configuration

### **Timer Settings**
Configure up to 3 sleep/wake time pairs:
- **Timer 1**: Always active
- **Timer 2**: Toggleable
- **Timer 3**: Toggleable

### **Brightness Settings**
- **Current Brightness**: 0-100%
- **Sleep Brightness**: 0-100% (default: 30%)
- **Wake Brightness**: 0-100% (default: 100%)
- **Screen Off Delay**: 0.5-24 hours (default: 0.5 hours)
- **Auto Ambient Lighting**: Toggle automatic ambient lighting (Ball V2 only)

### **Screen Control**
- **Manual Override**: Screen stays off when manually turned off
- **Natural Transitions**: Screen turns on automatically for sleep/wake period changes
- **Double Tap/Press**: Toggle screen on/off (wake screen only)
- **Ambient Lighting**: Automatic color matching with screen or manual control (Ball V2 only)

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
2. **Touch Response**: Ensure clean screen surface (Guition only)
3. **Button Response**: Check button functionality (Ball V2 only)
4. **Time Display**: Check timezone and NTP server settings
5. **Screen Control**: Double-tap/double-press to toggle screen if it's off
6. **Ambient Lighting**: Check auto ambient lighting toggle (Ball V2 only)

### **Timer Issues**
1. **Time Format**: Verify 12-hour format (AM/PM)
2. **Next-Day Logic**: Ensure wake time is after sleep time
3. **Star Countdown**: Check that stars are visible and positioned correctly

### **Common Problems**
- **Device Not Booting**: Check power supply and USB connection
- **Web Interface Unavailable**: Verify device IP and network connectivity
- **OTA Updates Failing**: Ensure stable WiFi connection during updates
- **Screen Won't Turn On**: Try double-tapping/double-pressing the screen
- **No Audio Output**: Check speaker enable switch and audio configuration (Ball V2 only)
- **Ambient Lighting Issues**: Verify auto ambient lighting toggle and LED configuration (Ball V2 only)

## 📁 File Structure

```
esphome-groclock/
├── BallV2.yaml              # Spotpear Ball V2 configuration
├── Guition4848S040.yaml     # Guition ESP32-S3-4848S040 configuration
├── secrets.yaml             # WiFi credentials (create this)
├── readme.md               # This documentation
├── resources/
│   ├── tz.yaml            # Timezone definitions
│   ├── LCD.ttf            # LCD font file
│   ├── sun.png            # Sun image for wake screen
│   ├── star.png           # Star image for sleep screen
│   ├── wake_photo.jpeg    # Wake screen photo
│   └── sleep_photo.jpeg   # Sleep screen photo
└── LICENSE                 # Project license
```

## 🔧 Technical Details

### **Hardware Specifications**

#### **Guition ESP32-S3-4848S040**
- **Board**: Guition ESP32-S3-4848S040
- **Display**: 4" 480x480 IPS LCD
- **Touch**: Capacitive touchscreen (GT911)
- **Processor**: ESP32-S3 dual-core 240MHz
- **Memory**: 8MB Flash, 2MB PSRAM
- **Connectivity**: WiFi, Bluetooth LE

#### **Spotpear Ball V2**
- **Board**: Spotpear Ball V2
- **Display**: 1.28" 240x240 circular IPS LCD (GC9A01A)
- **Input**: Single button (GPIO0)
- **Audio**: ES8311 DAC with I2S audio support
- **Lighting**: WS2812 RGB LED strip
- **Processor**: ESP32-S3 dual-core 240MHz
- **Memory**: 8MB Flash, 2MB PSRAM
- **Connectivity**: WiFi, Bluetooth LE

### **Software Components**
- **Framework**: ESP-IDF
- **Display Drivers**: 
  - ST7701S (Guition ESP32-S3-4848S040)
  - GC9A01A (Spotpear Ball V2)
- **Touch Driver**: GT911 (Guition only)
- **Audio**: ES8311 DAC with I2S support (Ball V2 only)
- **Graphics**: LVGL 8.4.0
- **Font**: Custom LCD font with full character support

### **Network Configuration**
- **Primary**: WiFi station mode with fallback
- **Fallback**: Access Point mode with device name
- **Timeout**: 30-second AP timeout, 60-second reboot timeout
- **Power Save**: Disabled for responsive operation

### **Display Configuration**

#### **Guition ESP32-S3-4848S040**
- **Resolution**: 480x480 pixels
- **Color Depth**: 16-bit RGB565
- **Buffer Size**: 15% of available memory
- **Refresh Rate**: Optimized for smooth operation

#### **Spotpear Ball V2**
- **Resolution**: 240x240 pixels (circular)
- **Color Depth**: 16-bit RGB565
- **Buffer Size**: 15% of available memory
- **Refresh Rate**: Optimized for smooth operation
- **UI Scaling**: Compact elements optimized for circular display


## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.
