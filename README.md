# Marlin 2.1 for AdimLab Gantry

This is a customized fork of the original [Marlin firmware](https://github.com/MarlinFirmware/Marlin), pre-configured specifically for the **AdimLab Gantry** 3D printer.  
> ⚠️ **Note:** This configuration is **only compatible** with the white motherboard (featuring the **ATmega2560**).

---

# ✅ Update: If Your Hotend Thermistor Works Fine then Skip Rest of the Section

## 🔧 If you have Thermistor Issue

### Problem

In some cases, the hotend temperature constantly reads **200°C+**, even when idle.  
This issue is often caused by a **damaged ADC pin** on the ATmega2560 chip.
You can assign the hotend thermistor (`TH0`) to another analog pin, such as **analog pin A6**.

---
Then update the pin assignment in  
  `Marlin/src/pins/mega/pins_HJC2560C_REV2.h`:

  ```cpp
  //
  // Temperature Sensors
  //
  #define TEMP_0_PIN    8  // Analog Input --> Change this to 6
  #define TEMP_1_PIN    9  // Analog Input
  ```

---

### 🛠️ Update: Set the Correct Thermistor Type

By default **Thermistor Type 1** is selected in your configuration.

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
#define TEMP_SENSOR_0 1  // --> CHANGE THIS ACCORDINGLY IF YOU ARE USING SOMETHING ELSE (E.G., 51 IS YOU ARE USING 1K RESISTOR)
#define TEMP_SENSOR_1 0
```

---
