---
layout: default
---
# `line-follower`
The line follower module handles the line following challenge. It takes over control of the ROV to have
it move based off of the input from the vision processing camera. 

## API usage
This module reads from the API to find out when it should be running. When it should be running, it then starts to publish
what it believes to be the correct direction to move. It is triggered to start running by the `berunning` node of the API, which
the motor-control module also watches to find out if it should be taking direction from the line follower.

TODO: update this documentation as this portion of the code is written.

## How it works
See the [algorithm description](../algorithms/line-following).
