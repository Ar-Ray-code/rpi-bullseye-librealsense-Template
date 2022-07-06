# rpi-bullseye-librealsense-Template
[WIP] Raspbian-bullseye (64bit) built package installation and examples

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
