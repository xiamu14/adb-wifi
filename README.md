# ADB QR Code Pairing & Connect

Android 11+ wireless debugging tool with QR code pairing and auto-connect support.

## Features

- **Pair Only** (default): Scan QR code to pair device
- **Pair and Connect**: Scan QR code to pair, then auto-connect with custom port
- **Connect Only**: Skip pairing, just scan QR to get IP and connect

## Usage

### 1. Pair Only (default)
```bash
python main.py
```
Scans QR code and pairs the device. No automatic connection.

### 2. Pair and Connect
```bash
python main.py -p
# or
python main.py --pair-connect
```
After pairing successfully, prompts you to enter the connect port (default: 5555), then executes `adb connect ip:port`.

### 3. Connect Only (skip pairing)
```bash
python main.py -c
# or
python main.py --connect
```
Scans QR code to read device IP, prompts for port, and connects directly without pairing. Use this when device is already paired.

### 4. Help
```bash
python main.py -h
```

## Steps

1. Run the script with desired mode
2. On your Android device:
   - Go to **Developer options** ’ **Wireless debugging** ’ **Pair device with QR code**
3. Scan the QR code displayed in terminal
4. If using pair-connect or connect mode, enter the connection port when prompted
5. Press Enter to exit

## Requirements

- Python 3.6+
- python-zeroconf
- qrcode

Install dependencies:
```bash
pip install zeroconf qrcode
```

## Example

```bash
# Pair and auto-connect
$ python main.py -p
[QR Code displayed]
Mode: Pair and Connect
Scan QR code to pair, then you'll be prompted for connect port.
[Developer options]-[Wireless debugging]-[Pair device with QR code]

Service debug added.
adb pair 192.168.1.100:37891 123456

Pair successful!
Enter connect port (default 5555): 5555

Executing: adb connect 192.168.1.100:5555
connected to 192.168.1.100:5555
```
