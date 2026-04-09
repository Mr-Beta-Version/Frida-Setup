---

# Frida Setup Guide (PC + Android Emulator)

This guide walks through installing and running **Frida** on a PC and connecting it to an Android emulator.

---

## 1. Install Python

Download and install Python (recommended 3.8+).
Make sure Python is added to your system environment variables (PATH).

Verify installation:

```bash
python --version
```

---

## 2. Install Frida Tools

Install Frida CLI tools using pip:

```bash
pip install frida-tools
```

Verify installation:

```bash
frida --version
```

---

## 3. Check Emulator Architecture

Connect to your emulator:

```bash
adb shell
```

Check CPU architecture:

```bash
uname -m
```

Common outputs:

* `x86_64` → Emulator (most cases)
* `arm64` → ARM device

---

## 4. Download Frida Server

Download the matching Frida server version for your architecture:

```
https://github.com/frida/frida/releases/download/{version}/frida-server-{version}-android-{architecture}.xz
```

Example:

```
frida-server-17.9.1-android-x86_64.xz
```

---

## 5. Extract the File

Unzip the downloaded `.xz` file:

```bash
xz -d frida-server-*.xz
```

---

## 6. Push Frida Server to Emulator

Transfer the binary to the device:

```bash
adb push "C:\Users\User\Downloads\frida-server-17.9.1-android-x86_64" /data/local/tmp/frida-server
```

---

## 7. Set Permissions and Run

Open shell:

```bash
adb shell
```

Navigate and set permissions:

```bash
cd /data/local/tmp
chmod 700 frida-server
```

Run the server:

```bash
./frida-server
```

Keep this running.

---

## 8. Test Connection

On your PC, run:

```bash
frida-ps -U
```

If successful, you’ll see a list of running processes on the emulator.

---

## Notes

* Make sure Frida **client and server versions match exactly**
* Emulator usually does **not require root**, but real devices often do
* If `frida-ps -U` fails:

  * Check if server is running
  * Verify correct architecture
  * Ensure ADB is connected (`adb devices`)

---

## Optional Tips

* Run Frida server in background:

```bash
./frida-server &
```

* Kill existing server:

```bash
pkill frida-server
```

---
