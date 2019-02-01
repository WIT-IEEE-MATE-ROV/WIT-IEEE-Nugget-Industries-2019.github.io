---
layout: default
---

# API Overview
We need to be able to communicate between the various processes that make up the ROV software: some processes need to share things like sensor data with others, while other processes need to be able to read that data. To handle all of this, we have an API (Application Program Interface). This API provides one nice, neat location for processes to go and get/post integers, doubles, and strings. 

For more detail on how this all works, see the ['How It Works'](#How-It-Works) section.

## Pieces of the API
The content of the API is made up of files and folders in the `api`folder of the `comms` module. Below is the file tree, which has been modified to include information about the purpose of each file/folder.
```
├── motor                    For all the motors on board the ROV.
│   ├── subsystem            For all of the subsystems.
│   │   ├── dumper           For the dumper subsystem.
│   │   │   ├── actual       The actual value being maintained by the motor.
│   │   │   ├── goal         The goal value of the motor.
│   │   │   ├── heartbeat    A heartbeat for process that owns this motor.
│   │   │   ├── procid       The process ID of the process that owns this motor.
│   │   │   └── state        The state of the process that owns this motor.
│   │   ├── manipulator      The manipulator on the ROV.
│   │   │   ├── actual       The actual value being maintained by the motor.
│   │   │   ├── goal         The goal value of the motor.
│   │   │   ├── heartbeat    A heartbeat for process that owns this motor.
│   │   │   ├── procid       The process ID of the process that owns this motor.
│   │   │   └── state        The state of the process that owns this motor.
│   │   └── probe            The motor that controls the probe.
│   │       ├── actual       The actual value being maintained by the motor.
│   │       ├── goal         The goal value of the motor.
│   │       ├── heartbeat    A heartbeat for process that owns this motor.
│   │       ├── procid       The process ID of the process that owns this motor.
│   │       └── state        The state of the process that owns this motor.
│   └── thruster             All of the thrusters on the ROV.
│       ├── b                The back thruster.
│       │   ├── actual       The actual value being maintained by the motor.
│       │   ├── goal         The goal value of the motor.
│       │   ├── heartbeat    A heartbeat for process that owns this motor.
│       │   ├── procid       The process ID of the process that owns this motor.
│       │   └── state        The state of the process that owns this motor.
│       ├── bl               The back left thruster.
│       │   ├── actual       The actual value being maintained by the motor.
│       │   ├── goal         The goal value of the motor.
│       │   ├── heartbeat    A heartbeat for process that owns this motor.
│       │   ├── procid       The process ID of the process that owns this motor.
│       │   └── state        The state of the process that owns this motor.
│       ├── br               The back right thruster.
│       │   ├── actual       The actual value being maintained by the motor.
│       │   ├── goal         The goal value of the motor.
│       │   ├── heartbeat    A heartbeat for process that owns this motor.
│       │   ├── procid       The process ID of the process that owns this motor.
│       │   └── state        The state of the process that owns this motor.
│       ├── f                The front thruster.
│       │   ├── actual       The actual value being maintained by the motor.
│       │   ├── goal         The goal value of the motor.
│       │   ├── heartbeat    A heartbeat for process that owns this motor.
│       │   ├── procid       The process ID of the process that owns this motor.
│       │   └── state        The state of the process that owns this motor.
│       ├── fl               The front left thruster.
│       │   ├── actual       The actual value being maintained by the motor.
│       │   ├── goal         The goal value of the motor.
│       │   ├── heartbeat    A heartbeat for process that owns this motor.
│       │   ├── procid       The process ID of the process that owns this motor.
│       │   └── state        The state of the process that owns this motor.
│       ├── fr               The front right thruster.
│       │   ├── actual       The actual value being maintained by the motor.
│       │   ├── goal         The goal value of the motor.
│       │   ├── heartbeat    A heartbeat for process that owns this motor.
│       │   ├── procid       The process ID of the process that owns this motor.
│       │   └── state        The state of the process that owns this motor.
│       ├── l                The left thruster.
│       │   ├── actual       The actual value being maintained by the motor.
│       │   ├── goal         The goal value of the motor.
│       │   ├── heartbeat    A heartbeat for process that owns this motor.
│       │   ├── procid       The process ID of the process that owns this motor.
│       │   └── state        The state of the process that owns this motor.
│       └── r                The right thruster.
│           ├── actual       The actual value being maintained by the motor.
│           ├── goal         The goal value of the motor.
│           ├── heartbeat    A heartbeat for process that owns this motor.
│           ├── procid       The process ID of the process that owns this motor.
│           └── state        The state of the process that owns this motor.
├── sensor                   The sensor data.
│   ├── accelerometer        For the accelerometer unit.
│   │   ├── heartbeat        A heartbeat signal for the process that owns this sensor.
│   │   ├── procid           The process ID of the process that owns this sensor.
│   │   ├── x                The x component of the accelerometer, corrected for placement of the sensor (x is ROV x)
│   │   ├── y                The y component of the accelerometer, corrected for placement of the sensor (y is ROV y)
│   │   └── z                The z component of the accelerometer, corrected for placement of the sensor (z is ROV z)
│   ├── bar10                For the bar10 sensor, which provides depth and temperature.
│   │   ├── depth            The depth value produced by the bar10 sensor.
│   │   ├── heartbeat        A heartbeat signal for the process that owns this sensor.
│   │   ├── procid           The process ID of the process that owns this sensor.
│   │   └── temperature      The temperature measure by this sensor.
│   ├── distance             For the distance sensor mounted on the line-following camera.
│   │   ├── heartbeat        A heartbeat signal for the process that owns this sensor.
│   │   ├── procid           The process ID of the process that owns this sensor.
│   │   └── value            The value produced by this sensor.
│   ├── gyroscope            The gyroscope sensor.
│   │   ├── heartbeat        A heartbeat signal for the process that owns this sensor.
│   │   ├── pitch            The pitch value, corrected for placement of the sensor (pitch is rov pitch)
│   │   ├── procid           The process ID of the process that owns this sensor.
│   │   ├── roll             The roll value, corrected for placement of the sensor (roll is rov pitch)
│   │   └── yaw              The yaw value, corrected for placement of the sensor (yaw is rov pitch)
│   └── probe                For the sensors on the probe
│       ├── heartbeat        A heartbeat signal for the process that owns this sensor.
│       ├── ph               The pH value as measure by the probe.
│       └── procid           The process ID of the process that owns this sensor.
└── vision-processing        For the vision processing tasks.
    └── line-follower        For the line-follower.
        ├── berunning        Should the line-follower be running?
        ├── direction        What direction the line-follower says we should move
        ├── heartbeat        A heartbeat signal for the process that owns this sensor
        ├── line-length      The length of the blue line
        ├── line-location-x  The location of the blue line (x component)
        ├── line-location-y  The location of the blue line (y component)
        └── procid           The process ID of the process that handles this
```
The API is sorted by type (motor or sensor?) and then made more specific (thruster or subsystem?), and potentially made more specific again (dumper, manipulator, or probe?). At the end of the tree is a file, which contains information that the respective processes write to, allowing other processes to read from.

There are two files that are univeral for each process: `heartbeat`  and `procid`. `procid` is the Process ID (`PID`) of the process that publishes everything in the folder. Upon starting, it sets `heartbeat` to 0 and publishes its PID here. No less than once a second, the process will increment `heartbeat`. In the even that `heartbeat` is not being incremented, the process is not running and the process can be automatically restarted. When the heartbeat reaches 2 billion, it is reset to 0 to prevent integer overflow. This is not aniticipated to occur in normal ROV usage (2 billion seconds is over 23,000 days).

## Listening to the API and getting data
In the `comms.h` library, a function called `get_listener` exists. This function returns a `LISTENER` struct. The `LISTENER` struct is declared [here](https://github.com/WIT-IEEE-Nugget-Industries-2019/comms/blob/10ce6510c7d54dedf46384a592f6c14ecedee4ae/nugget-api.h#L16), but the contents aren't important (unless you want to know how it works, in which case check out How It Works). 

Pass to the function the path to the file relative to the `api` folder, and a value from the TYPE enum (`_int`, `_double`, `_string`). This will then allow you to use the listener to get the approprate value. For example, to get the pH provided by the probe sensor:

```C
LISTENER my_listener = get_listener("sensor/probe/ph", _double);
double ph_value = get_double(my_listener);
```

Note that it is possible to pass this listener to the `get_int()` or `get_string()` functions despite being a listener for doubles. However, these functions will return an error on runtime unless a listener with the appropriate `TYPE` is passed. Creating a listener of the correct type is the responsibilty of the user, as at the time of writing this is not checked.


## Publishing to the API
In the `comms.h` library, several post functions exist: `pos_int`, `post_double`, and `post_string`. This function returns true or false to indicate a success/fail on publishing. After creating a `PUBLISHER`, the publisher can be passed to the appropriate function with the desired content. For example, to publish that the state of the front left thruster is "running":

```C
PUBLISHER my_publisher = get_publisher("motor/thruster/fl/state", _string);
post_string(my_publisher, "running");
```

## Adding content to the API
The current state of the API should accomodate all inter-process needs. In the event that it does not, however, adding more content to the API is trivial.

When starting the API, the contents of the entire api folder are made available as part of the API. As a result, to add content to the API simply add an empty file within the API folder. To keep things clean, be sure to tuck things into descriptive folders in the same way the existing API does it.

## How It Works
It may seem that this API is simply reading/writing to files, but in reality this is not the case. The API works off of [named pipes](https://en.wikipedia.org/wiki/Named_pipe) by using the [mkfifo()](https://linux.die.net/man/3/mkfifo) call. This is significantly faster than reading and writing to a file, and is moderately faster than reading and writing to network sockets. To keep things fast, the pipe is opened when the listener/publisher is opened, and kept open until the process is shut down. 

As a bonus, this can be easily published to the network allowing for other devices to access them.

:)
