---
layout: default
---

# Sensors
## Specs
## Hardware Selection
The sensors in the robot:
1. Accelerometer/Gyroscope: LSM303 by Adafruit
2. Temperature: MAX6581 chip by Maxim Ingetrated
3. Barometer: Blue Robotics Bar02
4. Distance(for vision processing): 
# Code Development
The WiringPi library was used to send data readings through the Raspberry Pi's on-board I2C interface. 

## Accelerometer/Gyroscope
There are two sensors inside the triple-axis accelerometer/magnetometer compass module. The accelerometer tells you which direction is down towrds the earth (by measuring gravity) and the magnetometer senses where the strongest magnetic force is coming from, used to detect magnetic north.

### setup()
Sets the I2C interface connection up and enables the accelerometer and magnetometer.

### read_accel()
Reads the accelerometer split between least significant bits and most significant bits. Combines the bits and and prints the results.

### read_mag()
Reads the magnetometer split between least significant bits and most significant bits. Combines the bits and prints the results.

### set_mag_gain()
Sets the magnetometer gain.

## Temperature(MAX6581)
This is used to monitor the temperature inside the ROV


## Barometer
This sensor can measure up to 10 meter depth with water depth resolution of 0.16mm adn can measure altitude in air using air pressure with a resolution of 13cm.

### ms5837_init()
The sensor is intialized and data is verified with a cyclic redundancy check (crc).

### ms5837_read()
Read the sensor and updates the pressure and temperature.

### calculate()
Used to convert uncompensated temperature and pressure 

### setFluidDensity()
Sets the density of the working fluid in kg/m^3. Choose between seawater or freshwater.

### pressure()
Pressure is returned in mbar * conversion.

### temperature()
Temperature is returned in chosen conversion.

### depth()
Depth is returned in meters, calculated using the set density.

### altitude()
Altitude is returned in meters.

## Distance(for vision processing)

