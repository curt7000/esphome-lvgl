# ESPHome LVGL Configuration Repository

Welcome to my ESPHome LVGL configuration repository! This project provides a modular setup for ESP32 touch LCD devices using the LVGL graphics library, designed specifically for home automation and sensor monitoring.

*7-inch touch LCD display running ESPHome with LVGL interface, showing home automation controls including temperature display, printer status, air conditioning controls, and various smart home features.*

## Purpose

This repository contains ESPHome configurations for creating beautiful, touch-enabled displays for home automation. The setup is organized into modular components that can be mixed and matched to create custom interfaces for different rooms and use cases.

## Features

- **ESP32 Touch LCD Support**: Optimized for multiple ESP32-based touch LCD displays
- **Modular Design**: Organized components for easy customization
- **LVGL Interface**: Modern, responsive touch interface
- **Sensor Integration**: Built-in support for various sensors
- **Custom Themes**: Styled buttons and UI components
- **Network & Time**: Automatic network connectivity and time synchronization
- **Backlight Control**: Intelligent display brightness management

## Supported Devices

**[Guition ESP32-P4 JC1060P470](guition-esp32-p4-jc1060p470/README.md)** (7", ~£40)

![Guition ESP32-P4 JC1060P470](guition-esp32-p4-jc1060p470/guition-esp32-p4-jc1060p470.jpg)

**[Guition ESP32-S3 4848S040](guition-esp32-s3-4848s040/README.md)** (4.0", ~£16)

![Guition ESP32-S3 4848S040](guition-esp32-s3-4848s040/guition-esp32-s3-4848s040.jpg)

**[Waveshare ESP32-S3 Touch LCD 7"](waveshare-esp32-s3-touch-lcd-7/README.md)** (~£40)

![Waveshare ESP32-S3 Touch LCD 7](waveshare-esp32-s3-touch-lcd-7/waveshare-esp32-s3-touch-lcd-7.jpg)

## Where to Buy

| Device | Configuration | Where to Buy |
|--------|---------------|--------------|
| Guition ESP32-P4 JC1060P470 (7") | [template.yaml](guition-esp32-p4-jc1060p470/esphome/template.yaml) | [AliExpress](https://s.click.aliexpress.com/e/_c335W0r5) |
| Guition ESP32-S3 4848S040 (4.0") | [template.yaml](guition-esp32-s3-4848s040/esphome/template.yaml) | [AliExpress](https://s.click.aliexpress.com/e/_c3sIhvBv) |
| Waveshare ESP32-S3 Touch LCD 7" | [template.yaml](waveshare-esp32-s3-touch-lcd-7/esphome/template.yaml) | [AliExpress](https://s.click.aliexpress.com/e/_c37ljk8J) |

## Stands

Desk/desktop stands (3D printable models on MakerWorld):

| Device | Stand |
|--------|-------|
| Guition ESP32-P4 JC1060P470 (7") | [Link](https://makerworld.com/en/models/2387421-guition-esp32p4-jc1060p470-7inch-screen-desk-mount#profileId-2614995) |
| Guition ESP32-S3 4848S040 (4.0") | [Link](https://makerworld.com/en/models/2327976-touch-screen-desktop-stand-for-guition-4848s040#profileId-2543111) |
| Waveshare ESP32-S3 Touch LCD 7" | [Link](https://makerworld.com/en/models/1009516-desk-stand-for-7inch-waveshare-touch-screen#profileId-2439605) |

## Quick Start

### 1. Fork This Repository

**Important**: This repository contains configurations specific to my home setup. Please fork this repository and customize it for your own environment rather than using it directly.

### 2. Use a Device Template

Pick the `template.yaml` for your specific device. **Use the contents of that file as your ESPHome config** — in the ESPHome dashboard or CLI, create or edit your device configuration so it matches the contents of `template.yaml` (paths in the template are relative to the device folder, so keep the repo structure or adjust paths as needed).

```yaml
# Example: guition-esp32-s3-4848s040/esphome/template.yaml
substitutions:
  name: "your-device-name"
  friendly_name: "Your Room Sensor"
  room: "Your Room"
```

### 3. Update WiFi and Secrets

Set your WiFi credentials in the Esphome secrets file, in the esphome dashboard, in the top right under the secrets button.

```yaml
wifi_ssid: "Your_WiFi_SSID"
wifi_password: "Your_WiFi_Password"
```

### 4. Customize for Your Setup

Each template pulls in modular components that you can customize:

- **Device Configuration**: `device/device.yaml`
- **Sensors**: `device/sensors.yaml`
- **LVGL Interface**: `device/lvgl.yaml`
- **Add-ons**: Time, backlight, and network configurations in `addon/`
- **Assets**: Custom fonts and icons in `assets/`
- **Theme**: Button styling and UI components in `theme/`

## Getting Started with ESPHome

1. **Install ESPHome**: Follow the [ESPHome installation guide](https://esphome.io/guides/installing_esphome.html)

2. **Copy the repo**: Use the contents of each device's `esphome/template.yaml` as your ESPHome config (paste or import it as the main configuration for that device).

3. **Customize**: Update the substitutions and modify components as needed for your specific setup.

4. **Flash**: Compile and flash to your device — see **First-time flashing** below for the full process.

## First-time flashing

You need to put a **base image** on the device first (with your config and WiFi details). After that, you can usually use **OTA (over-the-air)** to flash updates over WiFi. The first flash is the only fiddly part; once it’s done, updates are straightforward.

### Recommended method: USB + ESPHome dashboard

1. **Run the ESPHome dashboard** (e.g. `esphome run` or your local ESPHome web UI).
2. **Connect the board with a USB cable** and open the dashboard in **Chrome**.
3. **Flash the device** from the dashboard. Chrome’s Web Serial support is used for the connection; other browsers may not work.
4. **Drivers**: If your computer doesn’t see the board, you may need USB drivers. ESPHome will prompt you when needed and provide links (e.g. CP210x, CH340) for your OS.
5. **Boot/reset once (if needed)**: Many boards ship with a demo firmware. If the first flash doesn’t take, put the board into **flashing mode** by holding the **boot** button and pressing **reset**, then try flashing again. You typically only need to do this once to replace the factory demo.
6. **After a successful flash**, the device should show up in the **ESPHome dashboard** and in **Home Assistant** as a discovered device. Later updates can usually be done over WiFi via OTA.

## Home Assistant Stateful Scenes

The lighting scene examples in this project assume you are using the Stateful Scenes integration for Home Assistant so scene state can be inferred reliably (for example, keeping a scene switch "on" when all scene entities match). Install and configure the add-on here: https://github.com/hugobloem/stateful_scenes.

---

**Remember**: This repository contains my personal home automation setup. Please fork and customize it for your own environment.
