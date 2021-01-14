# MX2
**Dual 6 Amp Motor Controller**  
A stackable add-on board for the Raspberry Pi computer. Use it with or without the [RedBoard+](https://github.com/RedRobotics/RedBoard) robotics controller for independent control of multiple DC brushed motors - up to 6 Amps each.   

![MX2 Image](https://github.com/RedRobotics/MX2/blob/images/MX2_text.png)

Use the MX2 with the RedBoard+ for easy control of mecanum wheeled robots.
[![](http://img.youtube.com/vi/_U4hyjQlxvI/0.jpg)](http://www.youtube.com/watch?v=_U4hyjQlxvI "Mecanum Wheel Test")  

# Usage  
The MX2 needs to be powered, you can use a different battery to the one powering your RedBoard+, just connect it to the battery input terminals. 
### Important!  

Check your wiring, there is no reverse polarity potection on the MX2!  


![MX2 Image](https://github.com/RedRobotics/MX2/blob/images/MX2_Wiring.png)  

You can use one battery to power the RedBoard+ and the MX2.  
You'll need to use a decent Lipo which can provide enough power for the whole system.  
Connect the matching battery terminals together + to + and - to -.  
Check your wiring, there is no reverse polarity potection on the MX2!  
![MX2 Image](https://github.com/RedRobotics/MX2/blob/images/MX2_Wiring_one_battery.png)

The MX2 already works with the latest version of the [RedBoard](https://github.com/RedRobotics/RedBoard) Library. If you are already using a RedBoard+, just stack the MX2 on top and use familiar RedBoard commands:

`redboard.M3(50)` - Motor 3 50% forwards

`redboard.M4(-75)` - Motor 4 75% backwards 

I've included a demo program - mecanum.py. This works like the original carsteer.py program, hook up your motors then hold or release the L1 button on your controller to toggle between 'turning' or 'strafing'.   

---  

You can stack up to four MX2 boards on top of each other.  
Each board must have a different I2C address, set the address by putting a blob of solder across the address selection pads as shown in the diagram.  

![MX2 Image](https://github.com/RedRobotics/MX2/blob/images/MX2_I2C.png)


---

Tom Oinn has forked the RedBoard library and added some very neat features.  
Head over to [ApproxEng](https://github.com/ApproxEng/RedBoard) and check out his RedBoard console, it's a great tool for setting up your motors and servos.  
![MX2 Image](https://github.com/RedRobotics/MX2/blob/images/RedBoard%2B%20Console.JPG)  

---


# MX2 Switchboard 

You can test the motors connected to the MX2 without any code!  
Just plug in the optional MX2 Switchboard and press the buttons (you'll still need to power the MX2). 
[![](http://img.youtube.com/vi/648YB2zGYNY/0.jpg)](http://www.youtube.com/watch?v=648YB2zGYNY "MX2 Switchboard")  


---
# Using the MX2 without the RedBoard+  
1 - 4 MX2 boards can be stacked on top of each other.   
You'll need to make sure each board has a different I2C address.  
You will need to solder in the optional 2x5 way pin header to the bottom MX2 board to connect it to the Raspberry Pi.  
The Raspberry Pi will have to be powered via it's USB port from a 5v powerbank, each MX2 board will have to be powered with a battery pack (as shown in the diagrams above).  


![MX2 Image](https://github.com/RedRobotics/MX2/blob/images/IMG_20200121_152340.jpg)
![MX2 Image](https://github.com/RedRobotics/MX2/blob/images/IMG_20200121_152405.jpg) 

I have created a simple python library to work just with the MX2 board (without all of the other RedBoard+ stuff).  

First make sure you have the I2C interface enabled:  
`sudo raspi-config`  

Go to Interface options, go down to I2C, then select YES. 

Make sure your system is up to date with:  
`sudo apt-get update && sudo apt-get upgrade -y`  

Then install pip:  
`sudo apt-get install python3-pip -y`  

Now install SMBus and I2CTools:  
`sudo apt-get install python3-smbus python3-dev i2c-tools -y`  

You can then install the library with:  
`pip3 install mx2`  

To test the MX2 board, open up a python shell:  
`python3`

Import the library:    
`import mx2`  

The library will now report how many MX2 boards are connected.  
You can now control the motors with the following commands:  

The first parameter is the number of the motor to be controlled.    
MX2 I2C address: 0x30 - motors 0 & 1  
MX2 I2C address: 0x31 - motors 2 & 3  
MX2 I2C address: 0x32 - motors 4 & 5  
MX2 I2C address: 0x33 - motors 6 & 7  

The second parameter is the speed, there are a few range options:  

For a speed range of 0-100 use:  
`mx2.M(0,50)` - motor 0, half speed forward  
`mx2.M(1,-100)` - motor 1, full speed backwards  

For an 8bit speed range, 0 - 255 use:  
`mx2.M_8bit(2,127)` - motor 2, half speed forward  
`mx2.M_8bit(3,-255)` - motor 3, full speed backwards  

for a speed range of 0 -1 use:  
`mx2.m(4,0.5)` - motor 4, half speed forward  
`mx2.m(5,-1)` - motor 5, full speed backwards  












