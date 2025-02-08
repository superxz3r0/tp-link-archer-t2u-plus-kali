# Installation Guide for TP-Link Archer T2U Plus AC600 Driver on Kali Linux

## Step 1: Update System Packages
Before installing the driver, ensure your system is up to date.
```bash
sudo apt-get update && sudo apt-get upgrade -y
```

## Step 2: Check Kernel Version and Find Required Modules
To find your current kernel version, run:
```bash
uname -r
```

Based on the kernel version and system architecture, find and download the appropriate headers and modules from [Kali's official repository](https://kali.download/kali/pool/main/l/linux/).

### Steps to find the required modules:
1. Open the repository link in your browser.
2. Search for files that match your kernel version (e.g., `linux-headers-*` and `linux-kbuild-*`).
3. Copy the direct links of the required files and save them in a text file (e.g., `modules.txt`).

### Example:
If your kernel version is `6.6.15`, your `modules.txt` file might look like this:
```
https://kali.download/kali/pool/main/l/linux/linux-headers-6.6.15-common_6.6.15-2kali1_all.deb
https://kali.download/kali/pool/main/l/linux/linux-kbuild-6.6.15_6.6.15-2kali1+b1_amd64.deb
https://kali.download/kali/pool/main/l/linux/linux-headers-6.6.15-amd64_6.6.15-2kali1+b1_amd64.deb
```

Download the modules using:
```bash
wget -i modules.txt
```

Now, install the downloaded packages:
```bash
sudo dpkg -i *.deb
```

## Step 3: Download and Install the TP-Link Archer T2U Plus AC600 Driver
Clone the driver repository from GitHub:
```bash
git clone https://github.com/morrownr/8821au-20210708
cd 8821au-20210708
```

Install necessary dependencies:
```bash
sudo apt install bc dkms -y
```

Run the installation script:
```bash
sudo ./install-driver.sh
```

During installation, you will be prompted to edit the driver options file. Make any necessary changes based on your requirements.

Once the installation is complete, you will be prompted to reboot. Type `y` and press Enter to restart your system and apply the changes.

```bash
Do you want to apply the new options by rebooting now? (recommended) [Y/n]
```

## Verification
After rebooting, check if the driver is loaded correctly:
```bash
lsmod | grep 8821au
```
If the module is listed, your TP-Link Archer T2U Plus AC600 adapter is now properly installed and ready to use!

To further verify, use the following command:
```bash
iwconfig
```
This should display the wireless interfaces, confirming that your adapter is recognized.

### Enjoy your TP-Link Archer T2U Plus AC600 adapter on Kali Linux! 🚀
