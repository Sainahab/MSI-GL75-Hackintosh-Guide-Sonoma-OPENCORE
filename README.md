# MSI GL75 Hackintosh Guide Sonoma OPENCORE (Please Read the FULL guide before starting)
 MSI GL75 Sonoma Hackintosh Guide OpenCore ( Bigsur monterey ventura too )

(Please Read the FULL guide before starting)

## Specifics

- CPU : Intel® Core™ i7-10750H Processor (12M Cache, up to 5 GHz)
- Graphics1 : Intel® UHD Graphics 630
- Graphics2 : Nvidia RTX2060
- Memory : Samsung LPDDR4 32GB 2666MHZ (16GB * 2 Dual Channel)
- Display : 17.3 Inch 1920 X 1080 120Hz
- Sound : Realtek ALC233
- Samsung NVMe SSD 1024GB
- WiFi/Bluethooth : Intel AX201
- Battery : 53WHr


## BIOS Version / OpenCore Bootloader Version / macOS Version Supported

- BIOS : Latest
- OpenCore Bootloader : v0.9.7
- macOS : Big Sur 11.7.10, Monterey 12.7, Ventura 13.6, Sonoma 14.1.1


## BIOS Setup

- Advanced

   - Sata mode = AHCI (Only necessary if you're not using an external SSD to install macOS. Warning: if switched from RAID to AHCI, your Windows install and all data will be lost)
   - VT-d = Disabled

- Boot

   - Fastboot = disabled
   - Boot mode = UEFI with CSM Security
   - Secure boot = disabled

## Hackintosh Status:

# What's Working: ✅✅✅

 - imessage / facetime / handoff / sidecar
 - WIFI/BT
 - GPU1 Intel with acceleration
 - SteelSeries Keyboard RGB working in MacOS
 - Trackpad + Gestures
 - Sound and mic
 - Usb type A
 - camera
 - Usb type C

# What's NOT Working: 🚫🚫🚫

 - GPU2 Nvidia RTX2060 (Obviously)
 - HDMI output (Again Nvidia)
 - I managed to get HDMI output to work with a USB-A DisplayLink hub !
 - MiniDP (Nvidiaaaaaaaaa)
 - Card Reader (Don't care enough to fix)


## Step by step how to :

# 1st Step is to boot Big sur (Please Read the FULL guide before starting)

 - YOU Must install Big sur first before upgrading to sonoma 
 - Follow dortania guide to make bootable usbstick for BIG SUR 11.7 macos (not montery/not ventura)  : https://dortania.github.io/OpenCore-Install-Guide/installer-guide/
 - 
# 2nd Step copy Big Sur EFI to usb

 - copy Efi folder (inside 1 - EFI BIG sur) to usb stick root.
 - now your usb root should have 2 folders {com.apple.recovery.boot & EFI}

<img src="https://dortania.github.io/OpenCore-Install-Guide/assets/img/com-efi-done.a6fb730e.png" alt="">

# 3nd Step config.plist config
 - download ProperTree and GenSMBIOS.

            -   https://github.com/corpnewt/ProperTree
            -   https://github.com/corpnewt/GenSMBIOS
            
 - Next, let's open ProperTree and edit our config.plist:

    * ProperTree.command
      ** For macOS
    * ProperTree.bat
      ** For Windows

    Once ProperTree is running, open your config.plist by pressing Cmd/Ctrl + O and selecting the config.plist file on your USB.

 - For setting up the SMBIOS info, we'll use GenSMBIOS application.

    
    <img src="https://dortania.github.io/OpenCore-Install-Guide/assets/img/smbios.35dd8ead.png" alt="">

    Run GenSMBIOS, pick option 1 for downloading MacSerial and Option 3 for selecting out SMBIOS. 
    This will give us an output similar to the following:

        #######################################################
        #               MacBookPro16,1 SMBIOS Info                  #
        #######################################################

        Type:         MacBookPro16,1
        Serial:       C02KCYZLDNCW
        Board Serial: C02309301QXF2FRJC
        SmUUID:       A154B586-874B-4E57-A1FF-9D6E503E4580


        The Type part gets copied to Generic -> SystemProductName.

        The Serial part gets copied to Generic -> SystemSerialNumber.

        The Board Serial part gets copied to Generic -> MLB.

        The SmUUID part gets copied to Generic -> SystemUUID.

        We set Generic -> ROM to either an Apple ROM (dumped from a real Mac), your NIC MAC address, or any random MAC address (could be just 6 random bytes, for this guide we'll use 11223300 0000. After install follow the Fixing iServices ( https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html ) on how to find your real MAC Address)

        Reminder that you need an invalid serial! When inputting your serial number in Apple's Check Coverage Page , you should get a message such as "Unable to check coverage for this serial number."

        Automatic: YES

        Generates PlatformInfo based on Generic section instead of DataHub, NVRAM, and SMBIOS sections
        #Generic

# 4nd Step Booting the OpenCore USB

     - boot usb stick and finish instalation.

# 5nd Step : OpenCore Post-Install

     - follow this guide to Booting without USB and Fixing iServices
     
     https://dortania.github.io/OpenCore-Post-Install/#how-to-follow-this-guide

# 5nd Step update to Sonoma
    
     - Normally update from software update in settings but before rebooting make sure to replace EFI folder with corresponded EFI , (don't forget to replace SMBIOS Info in the new EFI files) .
