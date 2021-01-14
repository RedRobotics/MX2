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




