# COMP541 Vivado Installation Guide

## System Requirements

In order to install the required software for this class, you will need one of the following:

* A computer running Windows with at least 80 GiB of free disk space, or an external storage device with at least 80 GiB free
* A computer running Linux with at least 80 GiB of free disk space, or an external storage device with at least 80 GiB free
* A computer running macOS with virtualization software running a Windows or Linux virtual machine with at least 80 GiB of storage space available to it (either on disk or with an external storage device)

Please note that in practice you may not need the full 80 GiB. Typically, students use between 60 and 80 GiB during the semester.

## 1. Windows
Running Windows natively makes this process relatively straightforward.

### Step 1: Download Vivado

Go to this URL: https://www.xilinx.com/support/download.html

Under Vivado ML Edition, download the Xilinx Unified Installer 2021.x: Windows Self Extracting Web Installer (EXE).

### Step 2: Install Vivado

Open the installer. Select _Vivado ML Standard_.

On the next screen, under Devices, the only box that needs to be checked is _Artix-7_ (under _7 series_). To save disk space, you may uncheck _SoCs_ and _UltraScale_ since we do not need them. On the following screens, use the default options.

> **Note:** It's fine if you would like to change the location of the installed software, but if you do, **be sure there are no spaces in the path name**, as it will cause errors in later labs.

Under _Installation Options_, be sure _Install Cable Drivers_ option is checked. Click _Install_.

> **Note:** A free license is included with _Vivado HL WebPACK_. While it has some project size limitations, it is more than adequate for our purposes.

### Step 3: Complete the first lab

Now, pick up with _Part I: Tutorial_ of Lab 1, available on the course website.

> **Troubleshooting:** In case of problems installing the software, submit a post to the Piazza discussion board. It is likely that other students are encountering the same issue. Seek help early instead of the day before the assignment is due!

## 2. Linux

Assuming you are using Ubuntu, the installation instructions are identical to the Windows instructions above, with two exceptions. The first is that you must download the _Linux Self Extracting Web Installer_ instead. Second, there is no option for cable drivers in the installer, so they must be installed manually. After completing Step 2 of the Windows install instructions, follow Step 2.5 below.
<!-- TODO: include hack for making other distros compatible -->
> **Note:** If you are using a distro besides Ubuntu, you are probably used to things not working right away, anyway. We encourage you to Read The Manual (and come to Office Hours!).

### Step 2.5: Install the cable drivers

Enter the following command as root, with `VIVADO_INSTALL_DIR` replaced with the location of your Vivado install location:
```bash
$ VIVADO_INSTALL_DIR/data/xicom/cable_drivers/lin64/install_script/install_drivers/install_drivers
```

## 3. macOS
As a Mac user, things are a little more ~~frustrating~~ complicated. You will need some sort of virtualization software. We have found both VirtualBox and Parallels to work. In this guide, we will be creating a Windows 10 Virtual Machine with VirtualBox.

> **Note:** The Windows ISO file (Step 4) may take a while to download depending on your connection. Feel free to go ahead and start downloading it before following steps 1–3.

### Step 1: Download VirtualBox

Go to this url: https://www.virtualbox.org/wiki/Downloads 

Click “OS X Hosts” to download the VirtualBox installer for macOS.

### Step 2: Install VirtualBox

Open the file you just downloaded, and double click on `VirtualBox.pkg`

![](./screenshots/virtualbox/00-pkg.png)

Follow install instructions for VirtualBox.

![](./screenshots/virtualbox/01-installer.png)

![](./screenshots/virtualbox/02-installer.png)

You may have to type in your password.

![](./screenshots/virtualbox/03-installer.png)

It is safe to move the installer to the trash after the install is complete.

### Step 3: Create new VM
Click “New” (the blue starburst).

![](./screenshots/virtualbox/04-main-menu.png)

Name the new machine something clear. You can’t go wrong with “Win10”

![](./screenshots/virtualbox/05-new.png)

Set the memory size to 4096MB, or half of your computer’s memory, whichever is more.

![](./screenshots/virtualbox/06-new-memory.png)

Select “Create a virtual hard disk now” and then “Create”

![](./screenshots/virtualbox/07-new-hard-disk.png)

Ensure “VDI” is selected, and then click “Continue”

![](./screenshots/virtualbox/08-hard-disk-file-type.png)

Ensure “Dynamically allocated” is selected, and then click “Continue”

![](./screenshots/virtualbox/09-storage-allocation.png)

Set the memory to at least 80GB, but we recommend 100GB. Then click “Create.”

![](./screenshots/virtualbox/10-storage-size.png)

Your VirtualBox window should roughly resemble this one.

![](./screenshots/virtualbox/11-menu-with-vm.png)

### Step 4: Download Windows ISO file

Go to this URL and download the Windows 10 ISO: https://www.microsoft.com/en-us/software-download/windows10ISO 

Make sure to get the 64-bit version.

### Step 5: Install Windows on VM

Back in VirtualBox, click “Settings,” then “Storage.”

![](./screenshots/virtualbox/12-settings-storage.png)

Click the small blue disk icon in the upper right, then select “Choose Disk File…,” select the Windows 10 ISO file you downloaded in Step 4, and then click OK.

Now, start the VM by clicking “Start.” If VirtualBox asks about controlling your computer using accessibility features, allow them. Make sure the Windows ISO file is selected (although it should be by default).

![](./screenshots/virtualbox/13-startup-choose-iso.png)

Use the appropriate language and keyboard settings and click Install.

> **Optional:** to make the Windows screen readable on HiDPI displays, click View > Virtual Screen 1 > Scale to 200%

![](./screenshots/virtualbox/14-vm-started.png)

You can safely ignore the product key alert for the entire class. It is not necessary to have a licensed version of Windows for COMP541.

![](./screenshots/virtualbox/15-activate-windows.png)

Select Windows 10 Education. Accept the Terms of Service. Select Custom Install (you are installing a fresh copy of Windows, not upgrading one). There will only be one drive available upon which to install Windows, select it (it will likely be called “Drive 0”). Now, wait for the install. It usually takes around a half an hour.

![](./screenshots/virtualbox/16-windows-10-education.png)

After that, follow standard install instructions. Set the region, keyboard layout, and log in to Microsoft.

> **Optional:** if you don’t want to log in to Microsoft, you can get around the nearly-mandatory login screen by disabling the internet connection temporarily. You can either just turn off wifi or unplug ethernet, or select Devices > Network and uncheck “Connect Network Adapter.” Then, click “Domain Join,” and when Windows cannot connect to the internet, it will revert to standard account creation procedure. Enter your name, password, and security questions. For privacy settings you may enter whatever you like, but know that none of the options are required for COMP541, so feel free to disable all of them.

### Step 6: Install VirtualBox Guest Additions

Click Devices > Insert Guest Additions CD image...

It should appear in your VM as though you had actually inserted a CD (often under “This PC”). Double click on “VBoxWindowsAdditions” and allow the app to make changes.

### Step 7: Install VirtualBox Extension Pack

Go to this URL: https://www.virtualbox.org/wiki/Downloads

Download and install the _Extension Pack_. It should be the same version as your copy of VirtualBox.

Make sure the VM is shut down, then go to _Settings > Ports > USB_, and select _2.0_ or _3.0_ for the version.

> **Note:** Some students will have issues with these USB drivers in Lab 3 and later. If you are having trouble, try switching from USB 2.0 to 3.0 or vice versa.

### Step 8: Download Vivado

Now, in the virtual machine, follow the **1. Windows** instructions above.
