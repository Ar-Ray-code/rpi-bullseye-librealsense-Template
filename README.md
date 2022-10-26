# rpi-bullseye-librealsense-Template
[WIP] Raspbian-bullseye (64bit) built package installation and examples

<br>

## Install built package

- libfw
- zip

```bash
# apt
sudo apt-get install git libssl-dev libusb-1.0-0-dev pkg-config libgtk-3-dev libglfw3-dev libgl1-mesa-dev libglu1-mesa-dev -y

```

```bash
LIBREALSENSE_ZIP="librealsense2-aarch64.zip"

curl -O https://github.com/Ar-Ray-code/rpi-bullseye-librealsense-Template/releases/download/0.1.0/librealsense2-aarch64.zip -O ${LIBREALSENSE_ZIP}
unzip ./${LIBREALSENSE_ZIP}
sudo cp -ur ./librealsense2/* /usr/local/
rm -rf ./librealsense2-aarch64.zip ./librealsense2/
```

<br>

## Build and install librealsense

> 8GB RAM Raspberry Pi4 is required

```bash
cd ~/
git clone https://github.com/IntelRealSense/librealsense.git -b v2.50.0
cd ~/librealsense
mkdir  build  && cd build
cmake .. -DBUILD_EXAMPLES=true -DCMAKE_BUILD_TYPE=Release -DFORCE_LIBUVC=true
make -j4
sudo make install
rm -rf ~/librealsense/
sudo wget https://raw.githubusercontent.com/IntelRealSense/librealsense/master/config/99-realsense-libusb.rules -O /etc/udev/rules.d/99-realsense-libusb.rules
```
