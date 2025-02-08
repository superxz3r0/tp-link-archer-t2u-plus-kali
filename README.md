# Installation Guide for TP-Link Archer T2U Plus AC600 Driver on Kali Linux

## Step 1: Update System Packages
Before installing the driver, ensure your system is up to date.
```bash
sudo apt-get update && sudo apt-get upgrade -y
```

## Step 2: Check Kernel Version and Install Required Modules
To find your current kernel version, run:
```bash
uname -r
```

Based on the kernel version and system architecture, download the appropriate headers and modules from [Kali's official repository](https://kali.download/kali/pool/main/l/linux/).

For example, if your kernel version is `6.6.15`, use the following commands:
```bash
wget https://kali.download/kali/pool/main/l/linux/linux-headers-6.6.15-common_6.6.15-2kali1_all.deb
wget https://kali.download/kali/pool/main/l/linux/linux-kbuild-6.6.15_6.6.15-2kali1+b1_amd64.deb
wget https://kali.download/kali/pool/main/l/linux/linux-headers-6.6.15-amd64_6.6.15-2kali1+b1_amd64.deb
```

Now, install the downloaded packages:
```bash
sudo dpkg -i linux-headers-6.6.15-common_6.6.15-2kali1_all.deb
sudo dpkg -i linux-kbuild-6.6.15_6.6.15-2kali1+b1_amd64.deb
sudo dpkg -i linux-headers-6.6.15-amd64_6.6.15-2kali1+b1_amd64.deb
```

## Step 3: Download and Install the TP-Link T2U Driver
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
If the module is listed, your TP-Link T2U adapter is now properly installed and ready to use!

To further verify, use the following command:
```bash
iwconfig
```
This should display the wireless interfaces, confirming that your adapter is recognized.
If the module is listed, your TP-Link T2U adapter is now properly installed and ready to use!

### Enjoy your TP-Link T2U adapter on Kali Linux! 🚀

