# How to build PyTorch for Raspberry Pi

The building process is based on [this](https://nmilosev.svbtle.com/compling-arm-stuff-without-an-arm-board-build-pytorch-for-the-raspberry-pi) article. Unfortunately the author uses Fedora 30 which by default has GCC 9, and RPI has GCC 8 so it will not work.
So I used Fedora 29 installed in VirtualBox

1. Get VirtualBox from [here](https://www.virtualbox.org/wiki/Downloads)
2. Install Fedora 29 on it. You can download the image [here](https://download.fedoraproject.org/pub/fedora/linux/releases/29/Workstation/x86_64/iso/Fedora-Workstation-Live-x86_64-29-1.2.iso)
3. Make sure you enabled as much CPU cores as possible in your VM. 
4. Also you'll need at least 3Gb of /tmp directory size in Fedora in order to compile PyTorch.  By default Fedora sets the /tmp size to a half of RAM size. So make sure to allocate at least 6Gb to your VM. If you can't do it you'll have to manually increase the size of tmp directory (more details [here](https://unix.stackexchange.com/questions/402637/tmp-directory-size-in-fedora))
5. Now in your VM
	- Install qemu and qemu-user packages

		`sudo dnf install qemu-system-arm qemu-user-static`
	- Now you need the rootfs. The following command will install a ARM rootfs to your /tmp directory along with everything you need to build PyTorch.
	
		```
		sudo dnf install --releasever=29 --installroot=/tmp/F29ARM --forcearch=armv7hl --repo=fedora --repo=updates systemd passwd dnf fedora-release nano openblas-devel blas-devel m4 cmake python3-Cython python3-devel python3-yaml python3-setuptools python3-numpy python3-cffi python3-wheel gcc-c++ tar gcc git make tmux -y
		```
		And then  
		```
		sudo chroot /tmp/F29ARM
		``` 
		
		Check:  
		```
		bash-4.4# uname -a
		Linux localhost.localdomain 4.18.16-300.fc29.x86_64 #1 SMP Sat Oct 20 23:24:08 UTC 2018 armv7l armv7l armv7l GNU/Linux
		```
	- Some things are broken, but easy to fix. Mainly network and DNF [wrongly detects your arch](https://bugzilla.redhat.com/show_bug.cgi?id=1691430).
		```
		# Fix for 1691430
		sed -i "s/'armv7hnl', 'armv8hl'/'armv7hnl', 'armv7hcnl', 'armv8hl'/" /usr/lib/python3.7/site-packages/dnf/rpm/__init__.py
		alias dnf='dnf --releasever=29 --forcearch=armv7hl --repo=fedora --repo=updates'
		
		# Fixes for default python and network
		alias python=python3
		echo 'nameserver 8.8.8.8' > /etc/resolv.conf
		```

	- Get PyTorch source:
		```
		git clone https://github.com/pytorch/pytorch --recursive && cd pytorch
		git checkout v1.2.0
		git submodule update --init --recursive
		```
	- Since we are building for a Raspberry Pi we want to disable CUDA, MKL etc.
		```
		export NO_CUDA=1
		export NO_DISTRIBUTED=1
		export NO_MKLDNN=1 
		export BUILD_TEST=0 # for faster builds
		export MAX_JOBS=4 # I have 4 cores on my VM
		export NO_NNPACK=1
		export NO_QNNPACK=1 
		```
	- Build:
		```
		python setup.py bdist_wheel
		```

		It took about 10 hours on my VM

6. After the building process is finished you'll have `torch-1.2.0a0+8554416-cp37-cp37m-linux_armv7l.whl` in the `dist` directory. Copy it to your computer either via shared folders  in VirtualBox or some online file sharing service (I used https://dropmefiles.com) 
7. And now some tricky part. Any `.whl` is just a `zip` file. You need to modify it using some Zip File Manager (e.g. [7-Zip](https://www.7-zip.org/)). You need to rename file `/torch/_C.cpython-37m-arm-linux-gnueabi.so` to `/torch/_C.cpython-37m-arm-linux-gnueabihf.so` and `/torch/_dl.cpython-37m-arm-linux-gnueabi.so` to `/torch/_dl.cpython-37m-arm-linux-gnueabihf.so`. Also edit `torch-1.2.0a0+8554416.dist-info/RECORD` and change corresponding lines there, but DON'T CHANGE sha256.  



 