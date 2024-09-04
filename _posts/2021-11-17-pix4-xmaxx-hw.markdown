---
layout:     post
title:      "Pixhawk 4 rover hardware"
subtitle:   "Hardware setup for Xmaxx with Pixhawk 4 and Xavier"
date:       2021-11-21 15:00:00
author:     "gary ding"
header-img: "img/in-post/post-eleme-pwa/eleme-at-io.jpg"
header-mask: 0.3
catalog:    true
tags:
    - Robot
    - Self-driving 
---


> Steps to build PIXHAWK 4 rover based on a Traxxas X-Maxx RC truck with a Jetson Xavier as a Companion computer<br><br>
> 

## Goals
To create a reference platform for the following:
- Multi-camera verification
- Data driven verification 
- Real world ML-Ops
- A source for training data   

## Parts List 

- Traxxas X-Maxx RC Monster Truck
- SparkFun FTDI Basic Breakout - 3.3V cable
- Traxxas 6700 Battery and 12A EZ Plus charger (6700)  
- Nvidia Jetson Xavier development board
- 25000 PC portable battery with 19V output 
- Delkin Devices Fat Gecko mini suction camera mount for 4 camera kit
- 55 mm spacers/ standoffs
- 60 mm spacers/ standoffs
- 35 mm spacers/ standoffs
- Acrylic Plexiglass Sheet 1/4" x 12" x 24" 
- M3 screws x 10 mm
- M3 screws x 20 mm
- PIXHAWK 4 kit
- X8R receiver 
- Taranis QX7
- e-CAM20_CUXVR - Four Synchronized 4K Cameras
- Taranis X7 and X8R


### 1. Modifying the Truck
The Traxxas X-Maxx is an affordable platform to carry heavy equipment, suitable for containing the other elements of the rover.   
![](/img/in-post/xmaxx.jpg)

Two layers of Plexiglass are installed to hold the PIXHAWK 4, Xavier computer, and camera setup.

The X-Maxx's onboard ESC is kept but the actual control wire is rerouted from the original 2.4G receiver box to pins 1 and 3 on the PIXHAWK 4 power board IO port.


### 2. Building the bottom layer

Standoffs are used to hold the PVC board to existing holes on the X-Maxx chassis. However, two holes in the front need to be newly created and threaded.

![](/img/in-post/xmaxx-body-drill.jpg)



### 3. Building the top layer

The second platform is created to hold the camera setup and also to protect the PIXHAWK 4 and computer. The image below depicts the finished assembly.

![](/img/in-post/xmaxx-body.jpg)

### 4. Wiring the motors

This is the standard wire diagram for accessories to be connected to the PIXHAWK 4.  

![](/img/in-post/pixhawk4.jpg)

A standard wiring diagram for this rover is as follows.

![](/img/in-post/pix4-wire.png)

Since the X-Maxx requires a high voltage that is provided by  two batteries, the wires needs to be redesigned to accomodate the PM07 power board.

![](/img/in-post/xmaxx-wire.png)

The PM07 board to connect ESC actual wiring is like this. The connector is trx female connector.

![](/img/in-post/xmaxx-pm07.jpg)

The wiring that connects the PM07 board to the battery is as follows. The connector shown in the image is a trx male connector.

![](/img/in-post/xmaxx-battery.jpg)


The X-Maxx setup after completion:

![](/img/in-post/xmaxx-complete.jpg)

### 5. Wiring the Xavier 

The battery used for the Xavier is a Krionia 25000mAH battery which can output a voltage of 19V.
A power cable connects the electrical output of the battery directly to the Xavier.

### 6. Wiring the ECS and steering cables

The X-Maxx's ESC and steering cables can be found inside the carrier box. 

![](/img/in-post/xmaxx-esc-cable.jpg)

The cable on the left is the ESC and the cable on the right is the steering cable. These two cables are rerouted from the receiver to GPIO pins 1 and 3 on the PM07. 

### 7. Connecting the Xavier to the PIXHAWK 4 

In order connect the  Xavier with the PIXHAWK4, a UART is needed. A telem2 is typically used for this purpose.  Therefore, an additional cable is used.

On the Xavier, the ports are as follows:

Jetson Xavier GPIO Pin 6 (GND) → Cable GND (Black Wire)
Jetson Xavier GPIO Pin 8 (UART1_TX) → Cable RXD (White Wire)
Jetson Xavier GPIO Pin 10 (UART1-RX) → Cable TXD (Green Wire)

![](/img/in-post/xmaxx-uart.jpg)


