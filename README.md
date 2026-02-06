# DIY In-Car Infotainment setup using affordable COTS Hardware
When on a lengthy drive with young children, Its nice to have a setup to keep all your passengers indulge in the same content on their personal screens while immersing themselves in the audio through the car's speaker system. This provides them with a cinematic experience on the move. Leveraging commercial off-the-shelf (COTS) hardware and open-source software, here is an attempt to build such a system.

[![DIY In-Car-Infotainment](http://img.youtube.com/vi/KWB2NDv0Wd8/0.jpg)](http://www.youtube.com/watch?v=KWB2NDv0Wd8)

# Setup in the car
![Car Setup Diagram.](/images/setup-in-the-car.png "Car Setup Diagram.")

# Block Diagram
![Block Diagram.](/images/block-diagram.png "Block Diagram.")

# Detailed Wiring
![Detailed Wiring.](/images/detailed-wiring.png "Detailed Wiring.")

# Required Items
![Required Items.](/images/required-items.png "Required Items.")

# Bill-Of-Material
**Note: The list of items along with their respective models, prices, and online links provided in this table are from the the time when this was written. However, they are presented solely as a reference and may be subject to change in the future. It is advisable to conduct your own research and verify the current information before proceeding to build this setup.**
| Sr.No | Item                         | Quantity | Unit-Price(€) | Price(€) | Remarks                         | Link                              |
| ----- | ---------------------------- | -------- | ------------- | -------- | ------------------------------- | --------------------------------- |
| 1     | 12v-to-48v boostconverter    | 1        | 24            | 24       | 48V 3A 144W                     | [Link](https://amzn.eu/d/8j5iHBu) |
| 2     | TP-Link Gigabit PoE Switch   | 1        | 36            | 36       | Unmanaged PoE 65W               | [Link](https://amzn.eu/d/0vykrx9) |
| 3     | 5v PoE Splitter(MicroUSB)    | 1        | 10            | 10       | 5V/2.4A Micro USB Plug          | [Link](https://amzn.eu/d/7zvdOZI) |
| 4     | GL.iNet GL-MT300N-V2 router  | 1        | 30            | 30       | None                            | [Link](https://amzn.eu/d/1pgoR1M) |
| 5     | 12v Car Plug extension       | 1        | 7             | 7        | with DC 5.5mm connector         | [Link](https://amzn.eu/d/8JvOOct) |
| 6     | 3Key USB keyboard            | 1        | 25            | 25       | For sync trigger                | [Link](https://amzn.eu/d/1t1PTpO) |
| 7     | Aux Audio Jack Cable 3.5 mm  | 1        | 6             | 6        | Display-to-Car-Audio feeder     | [Link](https://amzn.eu/d/dHI4taW) |
| 8     | USB Flash drive              | 1        | 10            | 10       | Capacity as per your media size | [Link](https://amzn.eu/d/4NsNqtn) |
| 9     | Raspberry Pi-4               | 3        | 50            | 150      | Minimum 2GB Ram                 | [Link](https://amzn.eu/d/emsVxcN) |
| 10    | Raspberry Pi-4 Case          | 3        | 13            | 39       | Passive cooled aluminium case   | [Link](https://amzn.eu/d/6aMwm2k) |
| 11    | 180° USB-C adapter           | 3        | 8             | 24       | usb-c male to female            | [Link](https://amzn.eu/d/1mEUGQV) |
| 12    | 5v PoE Splitter(USB-C)       | 3        | 15            | 45       | With USB-C connector            | [Link](https://amzn.eu/d/01gzida) |
| 13    | 14" fullHD touch display     | 3        | 110           | 330      | Price may vary                  | [Link](https://amzn.eu/d/cfz5Ms5) |
| 14    | Flexible flat ethernet cable | 3        | 5             | 15       | 5m or longer                    | [Link](https://amzn.eu/d/hwBD5y5) |
| 15    | MicroHdmi-to-Hdmi cable      | 3        | 9             | 27       | 0.3m                            | [Link](https://amzn.eu/d/2qWMZNS) |
| 16    | Short USB to USB-C cable     | 3        | 5             | 15       | 0.3m                            | [Link](https://amzn.eu/d/akP5E0D) |
| 17    | 180° HDMI adapter            | 3        | 9             | 27       | Depends on your touch display   | [Link](https://amzn.eu/d/bOJszxq) |
| 18    | MicroSD Card                 | 3        | 10            | 30       | 16GB or higher                  | [Link](https://amzn.eu/d/e3RXCP2) |

As of writing this, total cost of building three screen infotainment setup is around **850€**

# Assembly of Display screen
Here is the picture showing the assembly of Raspberry-Pi, PoE-Splitter and touch-display(note: numbers marked on the parts are same as listed in the Bill-Of-Material).
![Display Assembly.](/images/touch-screen-assembly.jpg "Display Assembly.")

# Preparation of MicroSD Cards for Raspberry-Pi

There are two ways to prepare the SD cards:

## Option 1: Pre-built Image (Recommended)

The easiest way - download and flash the same image to all SD cards.

**Download**: [media-mux-v1.0.0 Pi4 Image](https://github.com/hackboxguy/media-mux/releases/download/v1.0.0/2024-10-22-raspios-bookworm-arm64-lite-media-mux-v1-0.img.xz) (~1.2GB)

1. Download the image file above
2. Flash to each SD card using [balenaEtcher](https://etcher.balena.io/) or [Rufus](https://rufus.ie/)
3. Insert SD cards into your Raspberry Pi 4's and boot

**That's it!** Each Pi automatically:
- Generates a unique hostname from its MAC address (e.g., `media-mux-a1b2c3`)
- Discovers other media-mux devices on the network
- Auto-negotiates master/slave roles (no manual configuration needed)

With this option, you can skip the ["Final setup of Raspberry Pi's"](#final-setup-of-raspberry-pis-option-2-only) section below - just boot and go!

---

## Option 2: Manual Installation (using Raspberry Pi Imager)

For custom setups or if you prefer to install on an existing Raspberry Pi OS.

As shown in this picture below, using Raspberry-Pi-Imager, prepare 3 micro-sd-cards by setting the correct hostname/user/pw(for pi user, feel free to choose your own password). Make sure to set hostname as **media-mux-0001/media-mux-0002/media-mux-0003** and keep the user as **pi**.

![SDCard Preparation.](/images/raspi-sdcard-preparation.png "SDCard Preparation.")

Then follow the "Final setup of Raspberry Pi's" section below to complete the installation.

---

# Preparation of GL-MT300N-V2 Pocket-Router
Overwrite OEM firmware of pocket router with [this](https://github.com/hackboxguy/lfs-downloads/raw/main/gl-mt300nv2-dlnasrv/gl-mt300nv2-dlnasrv.bin) image. Exact details of preparing pocket router as DLNA/DHCP server are available here in my [blog](https://albert-david.blogspot.com/2024/03/transforming-your-gl-mt300n-v2-pocket.html)(Make sure your media files are copied on a ntfs formatted flash drive).

# Final setup of Raspberry Pi's (Option 2 only)

**Note:** If you used the pre-built image (Option 1), skip this section - your Pi's are ready to use!

1. As shown in this picture below, connect your PC(or laptop) to the 5th ethernet port(Non-PoE) of the PoE switch and turn ON the +12Vdc to this setup. wait for about 1-2 minutes so that pocket-router and raspberry-pi's are done with booting(your laptop or pc will get the ip 192.168.20.x from the dhcp server of the pocket-router).

![Installation Setup.](/images/installation-setup.png "Installation Setup.")

2. From your PC(or laptop) ssh into the first Raspberry pi using putty.exe or ssh ```ssh pi@media-mux-0001```
3. As shown in this picture below, run the commands: ```git clone --recursive https://github.com/hackboxguy/media-mux.git``` and ```cd media-mux``` and ```sudo ./setup.sh -n 1``` and finally reboot using ```sudo reboot;exit```

![SW Installation.](/images/sw-installation.png "SW Installation.")

4. Repeat the steps 2 and 3 by using next hostname(**media-mux-0002/media-mux-0003**) and using ```sudo ./setup.sh -n 2``` and ```sudo ./setup.sh -n 3```
5. After reboot, all 3 Raspi-Touch-Screens will automatically boot to kodi media player where you can browse your media files from Pocket-Router's DLNA server and play the content.

# How to Trigger Sync

6. The Raspi that is attached with the **3-Key USB keyboard** becomes the sync trigger device. Press **KEY_1** to synchronize all screens to play the same media at the same position.
7. You are free to operate all 3 Raspi-Touch-Screens and play separate medias so that every passenger can enjoy their own content by attaching an audio-headset to their respective screens.

# Final Assembly
![Final Assembly 1.](/images/assembled-setup-1.jpg "Final Assembly 1.")

![Final Assembly 2.](/images/assembled-setup-2.jpg "Final Assembly 2.")

# Mounting in the car
Depending on your car's seat headrest, there are numerous options available, particularly those designed for tablet mounting. Seek out the one that best fits your car and the size of your touchscreen display. While inexpensive holder clips (option-3) may be simple to hold the touch-display but they dont have a secure grip as other options.
![Mount Options.](/images/display-mount-options.png "Mount Options.")

# Explanation of media-playback synchronization between the displays

The `media-mux-controller` daemon listens for keyboard input. Upon detection of **KEY_1**, the [media-mux-sync-kodi-players.sh](https://github.com/hackboxguy/media-mux/blob/master/media-mux-sync-kodi-players.sh) script is invoked. This script:

1. Reads the currently playing media and position from the master device
2. Discovers all media-mux devices on the network via Avahi/mDNS
3. Opens the same media file on all devices
4. Uses [kodisync](https://github.com/hackboxguy/kodisync) to pause all players at the exact same frame
5. Seeks all players to the master's position
6. Resumes playback simultaneously

**Sync accuracy:** The system achieves sub-200ms synchronization, typically with less than 10ms spread between devices. This is a significant improvement over the earlier version shown in the YouTube video, which required multiple sync attempts.

For more technical details, see the [media-mux README](https://github.com/hackboxguy/media-mux#how-synchronization-works).
