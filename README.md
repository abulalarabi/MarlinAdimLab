# Marlin 2.1 for AdimLab Gantry

This is a customized fork of the original [Marlin firmware](https://github.com/MarlinFirmware/Marlin), pre-configured specifically for the **AdimLab Gantry** 3D printer.  
> ⚠️ **Note:** This configuration is **only compatible** with the white motherboard (featuring the **ATmega2560**).

---

## 🔧 If you have Thermistor Issue

### Problem

In some cases, the hotend temperature constantly reads **200°C+**, even when idle.  
This issue is often caused by a **damaged ADC pin** on the ATmega2560 chip.

### Default Configuration

In this firmware, the hotend thermistor (`TH0`) is assigned to **analog pin A6**.

---

### ✅ If Your Hotend Thermistor Works Fine

You can resolve this by doing one of the following:

- **Option 1:** Copy the original `pins` folder from the [Marlin firmware](https://github.com/MarlinFirmware/Marlin) into this project.

- **Option 2:** Manually update the pin assignment in  
  `Marlin/src/pins/mega/pins_HJC2560C_REV2.h`:

  ```cpp
  //
  // Temperature Sensors
  //
  #define TEMP_0_PIN    6  // Analog Input --> Change this to 8
  #define TEMP_1_PIN    9  // Analog Input
  ```

---

### 🛠️ Set the Correct Thermistor Type

Ensure that **Thermistor Type 1** is selected in your configuration.

In the `Configuration.h` file, find the section:

```cpp
/**
 * ================================================================
 *  Custom/Dummy/Other Thermal Sensors
 * ================================================================
 *     0 : Not used
 *  1000 : Custom - Specify parameters in Configuration_adv.h
 *
 *   !!! Use these for Testing or Development purposes. NEVER for production machines. !!!
 *   998 : Dummy Table that ALWAYS reads 25°C or the temperature defined below.
 *   999 : Dummy Table that ALWAYS reads 100°C or the temperature defined below.
 */
#define TEMP_SENSOR_0 51  // --> Change this to 1
#define TEMP_SENSOR_1 0
```

---
