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

# Preparation of MicroSD Cards for Raspberry-Pi
As shown in this picture below, using Raspberry-Pi-Imager, prepare 3 micro-sd-cards by setting the correct hostname/user/pw(for pi user, feel free to choose your own password). Make sure to set hostname as **media-mux-0001/media-mux-0002/media-mux-0003** and keep the user as **pi**.

![SDCard Preparation.](/images/raspi-sdcard-preparation.png "SDCard Preparation.")

# Preparation of GL-MT300N-V2 Pocket-Router
Overwrite OEM firmware of pocket router with [this](https://github.com/hackboxguy/lfs-downloads/raw/main/gl-mt300nv2-dlnasrv/gl-mt300nv2-dlnasrv.bin) image. Exact details of preparing pocket router as DLNA/DHCP server are available here in my [blog](https://albert-david.blogspot.com/2024/03/transforming-your-gl-mt300n-v2-pocket.html)(Make sure your media files are copied on a ntfs formatted flash drive).

# Final setup of Raspberry Pi's
1. As shown in this picture below, connect your PC(or laptop) to the 5th ethernet port(Non-PoE) of the PoE switch and turn ON the +12Vdc to this setup. wait for about 1-2 minutes so that pocket-router and raspberry-pi's are done with booting(your laptop or pc will get the ip 192.168.20.x from the dhcp server of the pocket-router).

![Installation Setup.](/images/installation-setup.png "Installation Setup.")

2. From your PC(or laptop) ssh into the first Raspberry pi using putty.exe or ssh ```ssh pi@media-mux-0001```
3. As shown in this picture below, run the commands: ```git clone https://github.com/hackboxguy/media-mux.git``` and ```cd media-mux``` and ```sudo ./setup.sh -n 1``` and finally reboot using ```sudo reboot;exit```

![SW Installation.](/images/sw-installation.png "SW Installation.")

4. Repeat the steps 2 and 3 by using next hostname(**media-mux-0002/media-mux-0003**) and using ```sudo ./setup.sh -n 2``` and ```sudo ./setup.sh -n 3```
5. After reboot, all 3 Raspi-Touch-Screens will automatically boot to kodi media player where you can browse your media files from Pocket-Router's DLNA server and play the content.
6. The Raspi that is attached with **3Keyboard-usb-accessory** will become a master device and by pressing the KEY_1 will play the same media of the master(by seeking the exact time of media) on to remaining two displays in a synchronized fashion.
7. You are free to operate all 3 Raspi-Touch-Screens and play separate medias so that every passanger can enjoy their own content by attaching an audio-headset to their respective screens.

# Final Assembly
![Final Assembly 1.](/images/assembled-setup-1.jpg "Final Assembly 1.")

![Final Assembly 2.](/images/assembled-setup-2.jpg "Final Assembly 2.")
