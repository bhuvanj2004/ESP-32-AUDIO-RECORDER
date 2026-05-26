# ESP-32-AUDIO-RECORDER
This repo contains the code for designing a .wav audio recorder using ESP32 development board, an INMP441 MEMS microphone, and a SD Card Reader. This captures audio when a button is triggered and stops when it is disconnected.

# ESP32 I2S WAV Audio Recorder

An embedded audio recording system built using the ESP32, INMP441 I2S MEMS microphone, and microSD card module.  
The system captures digital audio using the ESP32 I2S peripheral and stores it as standard WAV files on an SD card.

---

# Features

- Real-time audio recording using I2S
- WAV file generation
- SD card storage using SPI
- Automatic file naming
- DMA-based audio transfer
- GPIO-triggered recording
- LED recording status indication

---

# Hardware Used

| Component | Description |
|---|---|
| ESP32 Dev Board | Main microcontroller |
| INMP441 | I2S MEMS Microphone |
| MicroSD Card Module | Audio storage |
| MicroSD Card | WAV file storage |
| LED | Recording indicator |
| Push Button / GPIO Trigger | Start-stop recording |

---

# System Architecture

![Block Diagram](images/block_diagram.png)

---

# Audio Signal Flow

```text
Sound Waves
    ↓
INMP441 MEMS Microphone
    ↓
Internal ADC + PCM Conversion
    ↓
I2S Serial Audio
    ↓
ESP32 I2S Peripheral
    ↓
DMA Buffers
    ↓
Audio Processing
    ↓
16-bit PCM WAV Conversion
    ↓
SPI Communication
    ↓
microSD Card Storage
```

---

# Pin Configuration

| ESP32 Pin | Connected To |
|---|---|
| GPIO 26 | I2S WS |
| GPIO 25 | I2S SD |
| GPIO 33 | I2S SCK |
| GPIO 18 | SD SCK |
| GPIO 19 | SD MISO |
| GPIO 23 | SD MOSI |
| GPIO 5  | SD CS |
| GPIO 14 | Recording Trigger |
| GPIO 2  | Status LED |

---

# Working Principle

1. ESP32 initializes SPI and I2S peripherals.
2. The INMP441 microphone sends digital audio via I2S.
3. ESP32 receives audio samples using DMA buffers.
4. Samples are converted into 16-bit PCM format.
5. WAV headers are generated dynamically.
6. Audio data is written onto the SD card as `.wav` files.

---

# Software Flow

```text
Initialize System
       ↓
Initialize SD Card
       ↓
Initialize I2S Driver
       ↓
Wait for GPIO Trigger
       ↓
Start Recording
       ↓
Read Audio using DMA
       ↓
Convert to 16-bit PCM
       ↓
Write WAV Data to SD Card
       ↓
Stop Recording
       ↓
Update WAV Header
       ↓
Save File
```

---

# Sample Output

Recorded files are stored as:

```text
/rec0.wav
/rec1.wav
/rec2.wav
```

---

# Future Improvements

- WiFi audio streaming
- Bluetooth audio transfer
- Noise filtering
- Audio compression
- Real-time playback
- AI-based voice activity detection

---

# Applications

- Embedded audio logging
- IoT voice recording
- Portable voice recorder
- Smart surveillance systems
- Speech dataset collection

---

# Author

Bhuvan  
Electronics and Communication Engineering  
RV College of Engineering

---

# License

This project is open-source under the MIT License.
