mt7601u
=======

Ralink Wireless Adapter Driver

BOYPT Changes:

* include `linux/sched/signal.h` to avoid `implicit declaration of function ‘kill_pid’`
* use `kernel_read` for kernel 4.14+

Build Status
=======
The latest build status of master branch
![Build Status](https://travis-ci.org/terence-deng/mt7601u.svg?branch=master)

Build Requirements
=======
Debian/Ubuntu user can run below commands to install the dependencies
```Bash
apt-get update && apt-get install -y git wget gcc make build-essential linux-headers-$(uname -r)
```

CentOS/Redhat/Fedora user can run below commands to install the dependencies
```Bash
yum install -y git wget gcc make kernel-devel
```

Build Driver
=======
Start build
```Bash
make clean
make all
```
Or
```Bash
./build.sh
```

Crossing Building
=======
```
# pwd => /home/ubuntu/Workdir/linux
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- scripts

# cd ../mt7601u
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- LINUX_SRC=/home/ubuntu/Workdir/linux
```

Test Driver
=======
Load the driver
```Bash
./load.sh
```

Or copy all 3 .ko files to `/lib/modules/(kernel version)/`, then run `depmod -a`, the module will auto-loaded on inserting the usb dongle.

Unload the driver
```Bash
./unload.sh
```
