# Frida-Setup
Frida setup on PC and Emulator

```
Install Python
```

```
pip install frida-tools
```
Make it env variable

```
frida --version
```

```
adb shell
   uname -m
```
```
https://github.com/frida/frida/releases/download/{version}/frida-server-{version}-android-{uname}.xz
```
unzip it

push to tmp

```
adb push "C:\Users\User\Downloads\frida-server-17.9.1-android-x86_64\frida-server-17.9.1-android-x86_64" /data/local/tmp/frida-server
```
