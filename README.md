# Installation Guide for Raspberry Pi In QEMU on Kali/Debian Linux

# Please note that the following guide is a general outline and may require adjustments based on your specific setup.

## Install QEMU:
$ sudo apt update 
$ sudo apt install qemu-system-arm qemu-kvm libvirt-clients libvirt-daemon-system bridge-utils virtinst libvirt-daemon virt-manager

## Download Raspberry Pi Buster Lite Image:
Download the "2022-09-22-raspios-buster-armhf-lite.img.xz" file from the official Raspberry Pi website or a trusted source.

## Download kernel and device tree blob:
Download the "kernel-qemu-4.19.50-buster" and "versatile-pb-buster.dtb" files from a reliable source or the website mentioned in the guide.

## Set up the Virtual Machine (VM) in Virtual Machine Manager (Virt-Manager):
Open Virt-Manager with the following command:
$ sudo virt-manager
Click on "Create a new virtual machine."

Choose "Import existing disk image" and click "Forward."

Under "Architecture Options," select:

Architecture: armv6l
Machine Type: versatilepb
Click "Forward."

Under "Provide the existing storage path," click "Browse" and select the downloaded Raspberry Pi OS image file.

Choose "Generic or unknown" as the operating system and click "Forward."

Input "Memory" as 256 and "CPUs" as 1. Click "Forward."

Optionally, you can rename the VM if desired.

Enable "Customize configuration before install" and select "Virtual network 'default': NAT" as the network selection. Click "Finish."

Configuration screen:

Go to the "CPUs" tab and select "Model: arm1176." Click "Apply."
Go to the "Boot Options" tab, expand "Direct kernel boot," and enable "Enable direct kernel boot."
Input or browse the "Kernel path" to the downloaded "kernel-qemu-4.19.50-buster" file.
Input or browse the "DTB path" to the downloaded "versatile-pb-buster.dtb" file.
Input "Kernel args" as "root=/dev/vda2 panic=1."
Click "Apply."
Go to the "IDE Disk 1" tab and select "Disk Bus: VirtIO." Click "Apply."
Go to the "NIC" tab and select "Device Model: virtio." Click "Apply."
Click "Add Hardware" and go to the "Channel" tab.
Input "Name" as "org.qemu.guest_agent.0" and select "Device Type: UNIX socket (unix)." Click "Finish."
Optionally, you can add additional hardware such as a random number generator (RNG) by clicking "Add Hardware" and following the respective configuration.
Click "Begin Installation" to start the VM and begin the installation process.

## Inside the VM:

Log in using the default credentials:
Login: pi
Password: raspberry
Run the following command to configure the OS using the Raspberry Pi configuration tool:
$ sudo raspi-config
Use this tool to set the hostname, password, enable SSH, configure language, keyboard layout, etc.
Install the QEMU guest agent and enable host control by running:

$ sudo apt install qemu-guest-agent

## All done:
At this point, you should have successfully installed Raspberry Pi in QEMU on your Kali/Debian Linux system. Adjustments may be needed based on your specific requirements.

# OUTPUT SCREENSHOTS

## QEMU INSTALLATION PROCESS
![image](https://github.com/FaezSQ/OS_LAB10/assets/123714138/4946d811-9397-45f4-a035-943b36ee6b89)

## Raspberry PI LITE INSTALLATION PROCESS
![image](https://github.com/FaezSQ/OS_LAB10/assets/123714138/dc570092-45d9-45e2-828c-cf144aea325e)

## CLI SCREEN
![image](https://github.com/FaezSQ/OS_LAB10/assets/123714138/c5d06a81-5555-4805-baae-0ea4b2cce849)

