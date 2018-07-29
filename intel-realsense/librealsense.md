# LibRealSense

## LibRealSense

> Cross-platform camera capture for Intel® RealSense™ F200, SR300 and R200 [Github](https://github.com/IntelRealSense/librealsense)

## Installation

[Librealsense Installation](https://github.com/IntelRealSense/librealsense/blob/master/doc/installation.md)

```bash
abraham@aarcemor-desk:~/librealsense$ 
[55933.116046] uvcvideo: Found UVC 1.10 device Intel RealSense 3D Camera R200 (8086:0a80)
[55933.116912] input: Intel RealSense 3D Camera R200 as /devices/pci0000:00/0000:00:14.0/usb4/4-2/4-2:1.0/input/input17
[55933.117216] uvcvideo: Unknown video format 2036315a-0000-0010-8000-00aa00389b71
[55933.117218] uvcvideo: Found UVC 1.10 device Intel RealSense 3D Camera R200 (8086:0a80)
[55933.117998] uvcvideo: Unable to create debugfs 4-2 directory.
[55933.118059] input: Intel RealSense 3D Camera R200 as /devices/pci0000:00/0000:00:14.0/usb4/4-2/4-2:1.2/input/input18
[55933.118324] uvcvideo: Unknown video format 30315752-0000-0010-8000-00aa00389b71
[55933.118326] uvcvideo: Found UVC 1.10 device Intel RealSense 3D Camera R200 (8086:0a80)
[55933.119164] uvcvideo: Unable to create debugfs 4-2 directory.
[55933.119235] input: Intel RealSense 3D Camera R200 as /devices/pci0000:00/0000:00:14.0/usb4/4-2/4-2:1.4/input/input19
```

```bash
abraham@aarcemor-desk:~$ git clone https://github.com/IntelRealSense/librealsense.git
Cloning into 'librealsense'...
remote: Counting objects: 13387, done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 13387 (delta 0), reused 0 (delta 0), pack-reused 13383
Receiving objects: 100% (13387/13387), 3.71 MiB | 1.06 MiB/s, done.
Resolving deltas: 100% (9520/9520), done.
Checking connectivity... done.
```

```bash
abraham@aarcemor-desk:~$ sudo apt-get install qtcreator
Reading package lists... Done
Building dependency tree       
Reading state information... Done
qtcreator is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 399 not upgraded.
abraham@aarcemor-desk:~$
```

```bash
abraham@aarcemor-desk:~$ cd librealsense/
abraham@aarcemor-desk:~/librealsense$ ls
appveyor.yml     COPYING                 librealsense.vc14  scripts
AUTHORS          doc                     librealsense.xc    src
CLA.md           examples                LICENSE            unit-tests
CMakeLists.txt   include                 Makefile
config           librealsense.qtcreator  package.xml
CONTRIBUTING.md  librealsense.vc12       readme.md
abraham@aarcemor-desk:~/librealsense$
```

```bash
abraham@aarcemor-desk:~/librealsense$ sudo scripts/install_glfw3.sh 
-- Installing: /usr/local/lib/libglfw.so.3.2
-- Installing: /usr/local/lib/libglfw.so.3
-- Installing: /usr/local/lib/libglfw.so
Done installing glfw3!
``

```sh
abraham@aarcemor-desk:~/librealsense$ sudo scripts/install_qt.sh 
...
Setting up libqt5scripttools5:amd64 (5.2.1+dfsg-1ubuntu1) ...
Setting up libqt5svg5-dev (5.2.1-1) ...
Setting up qtdeclarative5-folderlistmodel-plugin:amd64 (5.2.1-3ubuntu15.1) ...
Setting up qtscript5-dev (5.2.1+dfsg-1ubuntu1) ...
Setting up qttools5-dev (5.2.1-8build1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
Done installing qt5!
abraham@aarcemor-desk:~/librealsense$
```

```text
abraham@aarcemor-desk:~/librealsense$ ls
appveyor.yml    CONTRIBUTING.md  librealsense.qtcreator  obj
AUTHORS         COPYING          librealsense.vc12       package.xml
bin             doc              librealsense.vc14       readme.md
CLA.md          examples         librealsense.xc         scripts
CMakeLists.txt  include          LICENSE                 src
config          lib              Makefile                unit-tests
abraham@aarcemor-desk:~/librealsense$ make 
abraham@aarcemor-desk:~/librealsense$ sudo make install
install -m755 -d /usr/local/include/librealsense
cp -r include/librealsense/* /usr/local/include/librealsense
cp lib/librealsense.so /usr/local/lib
ldconfig
abraham@aarcemor-desk:~/librealsense$
```

```bash
abraham@aarcemor-desk:~/librealsense$ sudo cp config/99-realsense-libusb.rules /etc/udev/rules.d/
abraham@aarcemor-desk:~/librealsense$ sudo udevadm control --reload-rules && udevadm trigger
```

```bash
abraham@aarcemor-desk:~/librealsense$ ./scripts/patch-uvcvideo-ubuntu-mainline.sh
Reading package lists... Done
Building dependency tree       
...
  LD [M]  /home/abraham/uvc_patch/linux-lts-utopic-3.16.0/drivers/media/usb/uvc/uvcvideo.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/abraham/uvc_patch/linux-lts-utopic-3.16.0/drivers/media/usb/uvc/uvcvideo.mod.o
  LD [M]  /home/abraham/uvc_patch/linux-lts-utopic-3.16.0/drivers/media/usb/uvc/uvcvideo.ko
make: Leaving directory `/home/abraham/uvc_patch/linux-lts-utopic-3.16.0'
```

```bash
abraham@aarcemor-desk:~/librealsense$ ./scripts/install-r200-udev-fix.sh
```

```bash
abraham@aarcemor-desk:~/librealsense$ sudo ./scripts/install_dependencies-4.4.sh
```

