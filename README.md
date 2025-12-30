# 🩺 DIGITAL PHONOCARDIOGRAPH

<p align="center">
  <img src="docs/images/pcg_overview.jpg" width="700" alt="Digital Phonocardiograph Overview">
</p>

An **ESP32-based Digital Phonocardiograph (PCG)** designed for **acoustic heart sound acquisition, signal processing, and abnormality detection**.  
The system integrates **real-time audio capture**, **frequency-domain analysis**, **embedded DSP**, and **data logging** into a standalone biomedical instrumentation platform.

---

## 📸 DEMONSTRATION

<p align="center">
  <img src="docs/images/demo.gif" width="600" alt="Phonocardiograph in Operation">
</p>

---

# 📌 PROJECT CONTEXT

- **Academic Level:** Undergraduate – Electronics & Communication Engineering  
- **Project Type:** Embedded biomedical instrumentation project  
- **Focus Areas:**
  - Embedded systems & firmware design  
  - Digital signal processing (DSP)  
  - Biomedical instrumentation  
  - Real-time frequency analysis  
  - Hardware–software co-design  

The objective was to design a **low-cost, portable phonocardiograph** capable of capturing and analyzing heart sounds under **microcontroller resource constraints**.

---

# 📐 SYSTEM OVERVIEW

<p align="center">
  <img src="docs/images/system_block_diagram.png" width="650" alt="System Block Diagram">
</p>

The system consists of **four core subsystems**:

1. **Acoustic Signal Acquisition**  
2. **Digital Signal Processing (DSP)**  
3. **Decision & Alert Logic**  
4. **Visualization & Data Logging**  

Heart sounds are captured digitally, processed in real time, and stored for offline analysis.

---

# 🔧 HARDWARE ARCHITECTURE

<p align="center">
  <img src="docs/images/hardware_setup.jpg" width="600" alt="Hardware Setup">
</p>

## CORE HARDWARE COMPONENTS

- **Microcontroller:** ESP32  
- **Microphone:** I2S digital MEMS microphone  
- **Display:** SSD1306 OLED (128×64)  
- **Storage:** SD card module  
- **User Interface:** Push button  
- **Alert System:** Buzzer  

The use of a **digital I2S microphone** eliminates the need for analog preamplifiers and ADC stages, significantly reducing noise and distortion for low-amplitude heart sounds.

---

# ⚡ POWER SYSTEM

- Battery-powered operation  
- Regulated supply for ESP32 and peripherals  
- Isolated digital audio acquisition  
- Stable operation during continuous DSP execution  

Power integrity is critical due to the sensitivity of biomedical acoustic signals.

---

# 🧠 FIRMWARE & CONTROL ARCHITECTURE

The firmware is modular and structured into:

- Audio acquisition (I2S driver)  
- FFT and DSP processing  
- Feature extraction logic  
- Heart rate estimation  
- Abnormality detection  
- OLED visualization  
- WAV file generation and SD logging  

This architecture enables **real-time processing** while remaining scalable for future algorithmic upgrades.

---

# 📊 SIGNAL PROCESSING PIPELINE

## 🔢 SAMPLING CONFIGURATION

- **Sampling rate:** 4 kHz  
- **FFT size:** 512 points  
- **Windowing:** Hamming window  

This configuration balances **frequency resolution**, **time resolution**, and **computational load**.

---

## 📈 FREQUENCY-DOMAIN ANALYSIS

Each recorded frame undergoes:

1. Windowing to minimize spectral leakage  
2. FFT computation  
3. Magnitude spectrum extraction  
4. Band-wise energy analysis  

Only the positive frequency spectrum is used for analysis.

---

## 🎵 FREQUENCY BAND INTERPRETATION

| Frequency Band | Clinical Interpretation |
|---------------|------------------------|
| < 80 Hz | Primary heart sounds (S1, S2) |
| 80–200 Hz | Transitional components |
| > 200 Hz | Murmur-related energy |

Excessive high-frequency energy is treated as a **potential abnormality indicator**.

---

# ❤️ HEART RATE ESTIMATION

Heart rate is estimated by analyzing dominant low-frequency components over time and converting peak periodicity into **beats per minute (BPM)**.

This method is computationally lightweight and well-suited for embedded execution.

---

# ⚠️ ABNORMALITY DETECTION

A recording is flagged as abnormal if:

- BPM lies outside the physiological range (50–120 BPM)  
- High-frequency spectral energy exceeds predefined thresholds  
- Irregular spectral patterns are observed  

## EXAMPLE OUTPUTS

<p align="center">
  <img src="docs/images/oled_normal.jpg" width="350" alt="Normal Output">
  <img src="docs/images/oled_abnormal.jpg" width="350" alt="Abnormal Output">
</p>

When abnormalities are detected:
- OLED displays warning status  
- Buzzer alert is triggered  
- File metadata reflects diagnostic flags  

---

# 💾 DATA LOGGING

- Audio stored as **16-bit mono WAV files**  
- Custom WAV header generation  
- Compatible with MATLAB, Python, Audacity, etc.  

Example filename:


This enables **offline validation and dataset creation**.

---

# 🧪 TESTING & VALIDATION

- Verified I2S audio integrity  
- FFT output validation using known signals  
- Real-time OLED feedback testing  
- SD card write stability testing  
- Continuous operation stress testing  

---

# 🎯 APPLICATIONS

- Digital phonocardiography research  
- Embedded biomedical instrumentation  
- Low-cost cardiac screening prototypes  
- DSP education on microcontrollers  

---

# 🔮 FUTURE IMPROVEMENTS

- S1/S2 segmentation algorithms  
- Wavelet-based heart sound analysis  
- Machine learning–based classification  
- Multi-sensor acoustic fusion  
- Clinical dataset validation  

---

# 📜 DISCLAIMER

This project is **strictly for educational and research purposes**.  
It is **not a certified medical device** and must not be used for clinical diagnosis.

