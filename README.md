

### 📌 Repo Description

> Board Support Package (BSP) for JC1060P4A1 (ESP32-P4). Provides out-of-the-box support for display (JD9365 MIPI-DSI), touch (GSL3680), audio (ES8311), and camera (OV2710). Includes full LVGL9.x integration with PPA hardware acceleration for high-performance graphics.

---

### 📄 README.md generate from AI

# JC1060P4A1 BSP (ESP32-P4)

This repository provides a **standalone Board Support Package (BSP)** for the **JC1060P4A1 development kit (ESP32-P4)**.  

It is designed to simplify application development by integrating drivers and initialization code for key peripherals, including **display, touch, audio, and camera**, with **LVGL v9.x and PPA acceleration support**.

---

## ✨ Features

- ✅ **PPA Hardware Acceleration**  
  - Seamless integration with **LVGL v9.x**  
  - Fixes missing/hidden PPA support in ESP-IDF v5.x official LVGL examples  

- ✅ **Display & Touch**  
  - **JD9365** MIPI-DSI LCD panel  
  - **GSL3680** capacitive touch controller  

- ✅ **Audio**  
  - **ES8311** audio codec with I2S and amplifier control  

- ✅ **Camera**  
  - **OV2710** sensor support  

- ✅ **BSP Layer**  
  - Easy-to-use initialization APIs (`bsp_display_start()`, `bsp_audio_codec_speaker_init()`, etc.)  
  - Abstracts away complex ESP-IDF driver setup  

---

## 📂 Structure

```

JC1060P4A1_BSP/
├── components/         # BSP source code
│   ├── display/        # Display and LVGL integration
│   ├── touch/          # Touch driver setup
│   ├── audio/          # ES8311 initialization
│   ├── camera/         # OV2710 integration
│   └── bsp/            # Core BSP (power, I2C, SD, USB, etc.)
├── CMakeLists.txt      # CMake integration
├── Kconfig             # Configurable options (enable/disable features)
└── README.md           # Documentation

````

---

## 🚀 Getting Started

### 1. Add BSP to your project

Clone into your `components/` folder:
```bash
cd your_project/components
git clone --recurse-submodules https://github.com/<yourname>/JC1060P4A1_BSP.git
````

### 2. Enable BSP in CMake

In your app’s `CMakeLists.txt`:

```cmake
idf_component_register(
    SRCS main.c
    REQUIRES JC1060P4A1_BSP
)
```

### 3. Configure and build

```bash
idf.py set-target esp32p4
idf.py menuconfig   # Configure BSP options (e.g. enable/disable PPA, touch, etc.)
idf.py build flash monitor
```

---

## 📌 Example Usage

```c
#include "bsp/display.h"
#include "bsp/audio.h"

void app_main(void) {
    // Start LVGL display with PPA acceleration
    lv_display_t *disp = bsp_display_start();

    // Initialize audio codec for speaker output
    esp_codec_dev_handle_t speaker = bsp_audio_codec_speaker_init();

    // Simple LVGL demo
    lv_obj_t *label = lv_label_create(lv_scr_act());
    lv_label_set_text(label, "Hello, JC1060P4A1!");
}
```

---

## 📜 License

This BSP is released under the [Apache 2.0](LICENSE) license.

```

---

⚡ Question for you:  
Do you want me to **include example apps (like lvgl_demo, audio_playback, camera preview)** inside this BSP repo, or should it stay a **pure BSP** (only libraries + APIs, no apps)?
```
