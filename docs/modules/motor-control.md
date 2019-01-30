---
layout: default
---
# `motor-control`

## Asynchronous thruster control
Motor control is performed asynchronously. To allow for this to occur, a single file (thruster-control.c) contains 
the code to control a single thruster, with another file holding helpful #defines (thruster-control.h). The name of the
thruster to be controlled is passed to the compiled code via the command line (i.e., `./thruster-control T_FRONT_LEFT`).
This single module is called once for each thruster, and each instance looks at the respective part of the API to find what to do.

The subsystem control functions in an identical fashion.

## Motor master control
The `motor-master` spawns all thruster and subsystem processes. Once complete, it then calculates thruster values based off of user
input combined via a PID which reads from the sensor values.
