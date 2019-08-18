The purpose of this article is to share the resources around setting up Hardware for Raspberry Pi on a virtual worker.
# Installing Raspberry Pi on Virtual Machine. 
## Why do we need to opt for Raspberry Pi on Virtual Machine.
You’ve probably heard of emulation. It essentially enables us to run software on systems where it would otherwise be incompatible. Windows itself has emulation built in, in the form of compatibility mode. It is useful for testing out projects when your Pi isn’t handy.

Virtual machines are the default option these days for anyone wanting to try out a new operating system without upsetting their delicate digital life. VMware and VirtualBox are often recommended to anyone wanting to try Linux for the first time, for instance, or with a desire to access an older version of Windows. It’s even possible to run some older versions of Mac OS X in a virtual machine.

While this makes them ideal for other forms of OS emulation/virtualization, it means that any operating system that runs on ARM chipsets cannot be installed and tested.

Well, several reasons spring to mind. First, using QEMU to run a virtualized Raspberry Pi environment lets you try out Raspbian without all of the messing around that is involved with writing a disk image to SD. While NOOBs is a better approach, neither is a fast setup, so virtualization gives anyone wanting to dip a toe in the pie, as it were, a quick chance to do so.

Second, a virtual Raspberry Pi offers the chance to gauge how the various apps will run, as well as enable debugging and troubleshooting on your standard PC. This might be useful to children using Scratch or other development tools. Making screenshots on the Raspberry Pi is simple enough, but exporting them can be tricky – virtualization circumvents that. It’s also good practice to test a new operating system in a virtualized environment.
It may not feature a physical computer, but it can be a time saver, and a bit of a game changer in some scenarios.

## Steps to install Raspberry Pi as an Emulator. 
* Installing Virtual box on Windows Machine. 
  VirtualBox is a powerful x86 and AMD64/Intel64 virtualization product for enterprise as well as home use. 
    * You can download the Virtual box from https://www.virtualbox.org/wiki/Downloads 
    * Choose the right version of your operating system. 
    * After you’ve downloaded the executable, install VirtualBox by following the installation wizard’s instructions.
    * Change the Type to Linux and Version to Debian 64-bit.
    * Select Next.
    * Set 1024MB RAM in the next window.
    * Set 8-10GB of disk space in the next window and then select Create.
    * VirtualBox may take a few seconds to create the virtual machine. Once complete, it should appear in the left pane of the main VirtualBox window.
    * Select Start in the main VirtualBox window to start the VM.
* Download Debian Raspberry Pi Desktop
  * You can download Raspberry Pi Desktop from https://www.raspberrypi.org/downloads/raspberry-pi-desktop/ 
  * Select Install when prompted.
  * Set up language and keyboard and use Guided Installation.
  * Select the drive you want to install and the partitioning scheme. Defaults should do.
  * Select to install the GRUB bootloader when prompted. Select /dev/sda from the options.  
  * Allow the VM to boot into Raspberry Pi Desktop.
  * You should now see the Raspberry Pi Desktop. We have almost completed the installation and have just a couple of configuration changes to make.

* Configuration for Raspberry Pi Desktop.
  * Open Terminal from the Raspberry Pi Desktop.
  * Type ‘sudo apt update’ and hit Enter to update Raspberry Pi.
  * Type ‘sudo apt install virtualbox-guest-dkms virtualbox-guest-x11 linux-headers-$(uname -r)’ and hit Enter to install VirtualBox guest - extensions.
  * Navigate to Devices, Shared Clipboard and set it to Bidrectional.
  * Type ‘sudo reboot’ and hit Enter to reboot your virtual machine to enable the updates.
  * Open Terminal once more.
  * Type ‘sudo adduser pi vboxsf’ and hit Enter to enable file sharing.
  * Type ‘shutdown -h now’ and hit Enter and wait for Raspberry Pi to shut down.
  * In the main VirtualBox window, select the Raspberry Pi VM.
  * Select Settings and Shared Folders.
  * Select the add icon on the right of the window and add the folders you want to share between Windows and Raspberry Pi.
  * Select Auto-mount in the selection window.
You now have a fully functional Raspberry Pi Desktop running on Windows.       
      
You can emulate Raspberry Pi rather easier in Windows 10 if you have VirtualBox. You download the OS, install it in VirtualBox and run Raspberry Pi within the virtual machine. It works with most architecture types and most versions of Windows 10 so you should be fine. VirtualBox is free too.
      
Also, Microsoft Azure has a downloadable Raspberry Pi emulator and also a neat client simulator online. These two are easy ways to experiment with Raspberry Pi without buying the hardware. It is also a useful way to simulate your code purely in software before installing it onto hardware.

# Future Scope
* To train a Recurrent Neural Network on a virtual worker for Raspberry PI via PySyft
