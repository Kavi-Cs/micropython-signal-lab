# micropython-signal-FFT

# Linux Environment Setup

## 1. Grant Serial Port Access (restart your computer after this)
```bash
sudo usermod -a -G dialout kaveesha-induwara
```

## 2. Create a Virtual Environment
```bash
python3 -m venv esp_lab_env
```

## 3. Activate the Environment
```bash
source esp_lab_env/bin/activate
```

## 4. Install All Required Python Libraries
```bash
pip install esptool mpremote pyserial numpy matplotlib
```

Connect the board via USB, download the appropriate `.bin` file from [micropython.org/download](https://micropython.org/download), then flash it using the commands below. (The port may be `/dev/ttyACM0` or `/dev/ttyUSB0` — confirm with `ls /dev/tty*`.)

---

## 1. ESP32-S3 Board Instructions

### Hardware Setup
- **Signal Generator (+):** Connect to GPIO 4 on the ESP32-S3.
- **Signal Generator (−):** Connect to GND on the ESP32-S3.
- **Warning:** Voltage must be strictly between 0V and 3.3V.

### Firmware Flashing
After downloading the MicroPython `.bin` file, run the following commands in the terminal (port may be `/dev/ttyACM0` or `/dev/ttyUSB0`):

```bash
esptool.py --chip esp32s3 --port /dev/ttyACM0 erase_flash
esptool.py --chip esp32s3 --port /dev/ttyACM0 write_flash -z 0x0 firmware.bin
```

### MicroPython Code (`main.py`)
*# Saved main.py code*

### Uploading the Code
```bash
mpremote connect /dev/ttyACM0 cp main.py :
mpremote connect /dev/ttyACM0 reset
```

---

## 2. RP2040 (Raspberry Pi Pico) Board Instructions

### Hardware Setup
- **Signal Generator (+):** Connect to GP26 (Pin 31) on the RP2040.
- **Signal Generator (−):** Connect to GND on the RP2040.
- **Warning:** Voltage must be strictly between 0V and 3.3V.

### Firmware Flashing
1. Hold down the **BOOTSEL** button on the board while connecting it to the PC.
2. Copy & paste (drag and drop) the MicroPython `.uf2` file into the `RPI-RP2` drive that appears on your PC.

### Uploading the Code
```bash
mpremote connect /dev/ttyACM0 cp main.py :
mpremote connect /dev/ttyACM0 reset
```

---

## 3. PC Data Analysis & FFT Code (Common for Both Boards)

Save the code below as `pc_script.py`.

---

## 4. Daily Workflow

Once everything is set up initially, only **2 steps** are needed each time you open a terminal to work in the lab:

1. **Activate the virtual environment:**
   ```bash
   source esp_lab_env/bin/activate
   ```

2. **Run the PC script (to get the plots):**
   ```bash
   python3 pc_script.py
   ```
