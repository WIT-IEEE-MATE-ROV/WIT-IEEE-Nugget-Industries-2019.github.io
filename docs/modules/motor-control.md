---
layout: default
---
# `motor-control`

## Asynchronous thruster control
Motor control is performed asynchronously. To allow for this to occur, a single file (thruster-control.c) contains 
the code to control a single thruster, with another file holding helpful #defines (thruster-control.h). The name of the
thruster to be controlled is passed to the compiled code via the command line (i.e., `./thruster-control T_FRONT_LEFT`).
This single module is called once for each thruster, and each instance looks at the respective part of the API to find what to do.
Having this setup protects against thruster failure, if one stops working we can reset it and the other 7 are able to continue working without a problem.

The subsystem control functions in an identical fashion.

## Motor master control
The `motor-master` spawns all thruster and subsystem processes. Once complete, it then calculates thruster values based off of user
input combined via a PID which reads from the sensor values.

## Code
To Implement this asynchonous thursuter control, a struct was created called Whichami to help keep track which thuruster we are controlling. This struct contronts the name(i.e. T_FRONT_LEFT) along with the goal value(the data_send) and the file descriptor that will keep track of the num,ber assocaited with each thurster. This file descriptor will be used to make sure that we are calling the right thurster when using the wiringPiI2C funcitons.

### WiringPiI2C library
First before having the thruster move we must connect to it and it setup using the wiringPiI2C libarary. The first time connecting the thursters we will need to use wiringPiI2CDetect() to find each thruster unique identifier which we will put in their respective Whichami struct. From there once we know the uniquie identifier, fd, we can then use to it in wiringPiI2cSetup() which makes sure that the Pi connects to the thruster, if it does not work it will return an error. Once setup is comeplete then using the API we can send data to the thruster and control it. We will be using the wiringPiI2CWrite() to set the the PWM of the thruster.
