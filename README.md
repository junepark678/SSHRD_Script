## EliteBypass: A iCloud/FMI bypass for checkm8 devices
[Join our Discord](https://discord.gg/jTwEYsyMaX) for more info/support

# THIS ONLY WORKS ON A11 AND BELOW. IF YOU ARE USING AN IPHONE THAT MEANS XR/XS AND ABOVE WILL *NOT* WORK
# THIS ONLY WORKS ON *NIX BASED SYSTEMS


# Linux notes

On Linux, usbmuxd will have to be restarted. On most distros, it's as simple as these 2 commands in another terminal:
```
sudo systemctl stop usbmuxd
sudo usbmuxd -p -f
```

# For those who want an iCloud bypass:
### Disclamer: This will wipe everything from the device, I, and the Elite team will not be held responsable for misuse or not reading disclaimers.
By using Elite Bypass, you automatically agree to the previous statement.

1. Clone and cd into this repository: `git clone https://github.com/verygenericname/SSHRD_Script --recursive && cd SSHRD_Script`
    - If you have cloned this before, run `cd SSHRD_Script && git pull` to pull new changes
2. Run `./sshrd.sh <iOS version for ramdisk>`, **without** the `<>`.
    - The iOS version doesn't have to be the version you're currently on, but it should be close enough, and SEP has to be compatible
    - If you're on Linux, you will not be able to make a ramdisk for 16.1+, please use something lower instead, like 16.0
        - This is due to ramdisks switching to APFS over HFS+, and another dmg library would have to be used
3. Place your device into DFU mode
    - A11 users, go to recovery first, then DFU.
4. Run `./sshrd.sh boot` to boot the ramdisk
5. Run `./sshrd.sh nvram` to connect to clear the nvram. When you do this, you will be resetting all of find my iphone data stored in the nvram
6. Run `./sshrd.sh reset` to reset the borked device. When you clear the nvram, the device WILL BE BORKED

# Prerequsites

1. A computer running macOS/linux
2. A checkm8 device (A7-A11) NOTE: iPhone 6 and below cannot have filesystems mounted for unknown reasons.

# Usage

1. Clone and cd into this repository: `git clone https://github.com/verygenericname/SSHRD_Script --recursive && cd SSHRD_Script`
    - If you have cloned this before, run `cd SSHRD_Script && git pull` to pull new changes
2. Run `./sshrd.sh <iOS version for ramdisk>`, **without** the `<>`.
    - The iOS version doesn't have to be the version you're currently on, but it should be close enough, and SEP has to be compatible
    - If you're on Linux, you will not be able to make a ramdisk for 16.1+, please use something lower instead, like 16.0
        - This is due to ramdisks switching to APFS over HFS+, and another dmg library would have to be used
3. Place your device into DFU mode
    - A11 users, go to recovery first, then DFU.
4. Run `./sshrd.sh boot` to boot the ramdisk
5. Run `./sshrd.sh ssh` to connect to SSH on your device
6. Finally, to mount the filesystems, run `mount_filesystems`  
    - /var is mounted to /mnt2 in the ssh session.
    - /private/preboot is mounted to /mnt6.
    - DO NOT RUN THIS IF THE DEVICE IS ON A REALLY OLD VERSION!!!!!!!
7. Have fun!


# Other commands

- Reboot your device: `./sshrd.sh reboot`
- Erase all data from your device: `./sshrd.sh reset`
- Dump onboard SHSH blobs: `./sshrd.sh dump-blobs`
- Delete old SSH ramdisk: `./sshrd.sh clean`

# Credits

- [Nathan](https://github.com/verygenericname) for original code
- [tihmstar](https://github.com/tihmstar) for pzb/original iBoot64Patcher/img4tool
- [xerub](https://github.com/xerub) for img4lib and restored_external in the ramdisk
- [Cryptic](https://github.com/Cryptiiiic) for iBoot64Patcher fork
- [opa334](https://github.com/opa334) for TrollStore
- [Nebula](https://github.com/itsnebulalol) for a bunch of QOL fixes to this script
- [OpenAI](https://chat.openai.com/chat) for converting [kerneldiff](https://github.com/mcg29/kerneldiff) into [C](https://github.com/verygenericname/kerneldiff_C)
