# STM32F103C8 — Technical Overview

**Date:** Friday, November 7, 2025  
**Core:** ARM Cortex-M3 32-bit RISC  
**Maximum CPU Frequency:** 72 MHz  

---

### CPU & Core Features
- **Core:** ARM 32-bit Cortex-M3 CPU
- **Architecture:** RISC (Reduced Instruction Set Computing)
- **Maximum Frequency:** 72 MHz
- **Performance:** High code efficiency and execution speed comparable to 8/16-bit MCUs with lower memory usage.

---

### Memory
| Type  | Capacity | Notes |
|--------|-----------|--------|
| Flash  | 64 / 128 KB | Non-volatile program storage |
| SRAM   | 20 KB | Volatile data memory |

---

### Clock System
- **Internal RC Oscillator (HSI):** 8 MHz (factory-trimmed)
- **External Crystal Oscillator (HSE):** 4 MHz
- **Internal Low-Speed RC:** 40 kHz
- **External 32.768 kHz Oscillator:** for RTC

### Clock Domains
| Bus | Max Frequency | Description |
|------|----------------|-------------|
| AHB | 72 MHz | High-speed bus |
| APB2 | 72 MHz | High-speed peripheral bus |
| APB1 | 36 MHz | Low-speed peripheral bus |

Prescalers are available to adjust frequencies for different domains.

---

### Power Modes
The STM32F103C8 provides several power-saving modes:

#### **Sleep Mode**
- CPU stopped, peripherals still running  
- Wake-up possible via interrupt/event  

#### **Stop Mode**
- Lowest power while retaining SRAM and registers  
- PLL, HSI RC, and HSE oscillators disabled  

#### **Standby Mode**
- Minimal power consumption  
- Internal voltage regulator off  
- Entire 1.8 V domain powered down  

---

### Timers
- **7 Timers total:**
  - 3 × 16-bit general-purpose (Input Capture, Output Compare, PWM)
  - 1 × 16-bit motor control PWM
  - 2 × watchdog timers
  - 1 × SysTick (24-bit down-counter)

---

### DMA
- **7-channel DMA controller** for fast, CPU-independent data transfers.

---

### I/O Ports
- **Up to 80 fast I/O ports**
- All pins mappable to 16 external interrupt vectors
- **5V tolerant inputs**

---

### Communication Interfaces
| Interface | Quantity | Features |
|------------|-----------|-----------|
| I²C | 2 | Standard communication |
| USART | 3 | Up to 4.5 Mbit/s (USART1), others up to 2.25 Mbit/s |
| SPI | 2 | Master/slave, up to 18 Mbit/s |
| CAN | 1 | Controller Area Network interface |
| USB | 1 | USB 2.0 full-speed (12 Mbit/s) |

---

### Operating Voltage
- **Range:** 2.0 V – 3.6 V

---

### RTC (Real-Time Clock)
- Continuous counters for clock/calendar functions  
- Alarm and periodic interrupt support  
- Clock sources:
  - 32.768 kHz external crystal/resonator/oscillator  
  - Internal low-power RC oscillator  
  - High-speed external clock divided by 128  

---

### NVIC (Nested Vectored Interrupt Controller)
- Handles **up to 43 maskable interrupt channels** (plus 16 from the Cortex-M3 core)
- **16 priority levels**
- Enables fast, nested interrupt handling

---

### Summary

| Category | Key Specs |
|-----------|------------|
| CPU | ARM Cortex-M3, 72 MHz |
| Flash | 64 KB / 128 KB |
| SRAM | 20 KB |
| ADC | 2 × 12-bit (16 channels) |
| Timers | 7 total |
| Interfaces | USART ×3, SPI ×2, I2C ×2, CAN, USB |
| Voltage | 2.0 – 3.6 V |
| I/O Pins | Up to 80 |
| DMA | 7 Channels |

---

### Around
* keil uVision4 5.43


### Credits
* Julian Adrian Viana Palomo
* Facultad de matematicas UADY 2025

### References
* Maxim Integrated. (2002). MAX7219/MAX7221: Serially interfaced, 8-digit LED display drivers (Rev. 2002). Maxim Integrated Products. https://datasheets.maximintegrated.com/en/ds/MAX7219-MAX7221.pdf
* STMicroelectronics. (2007). STM32F10xxx8/B/C/D/E: Medium-density performance line ARM®-based 32-bit MCU (UM0306, Rev. 7). STMicroelectronics. https://www.st.com/resource/en/reference_manual/cd00246267.pdf

---
