# Warning this page is still Work-in-progress

# DIY In-Car Infotainment setup using affordable COTS Hardware
When on a lengthy drive with young children, Its nice to have a setup to keep all your passengers indulge in the same content on their personal screens while immersing themselves in the audio through the car's speaker system. This provides them with a cinematic experience on the move. Leveraging commercial off-the-shelf (COTS) hardware and open-source software, here is an attempt to build such a system.

[![DIY In-Car-Infotainment](http://img.youtube.com/vi/1vdC4lBXq0s/0.jpg)](http://www.youtube.com/watch?v=1vdC4lBXq0s)

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
