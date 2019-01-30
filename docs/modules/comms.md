# `comms`
The comms module handles both inter-process and inter-device communication.

## Inter-process communication
Interprocess communication is handled by the API. The API is represented by a file
structure in the `api` folder, and every file is then opened as a named pipe. This provides
high-speed interprocess communication. To manage this process, a series of functions and structs provides
functionality to read and write to the API.

To learn more abou the API and how to interact with it, click [here](../../api/api).

## Inter-device communcation
Because the API is structed as a file system, it's pretty trivial to publish it to the network.
This provides the useful functionality of being able to see everything the ROV is doing on the network,
and allows other devices to interact with it. However, by the nature of the API other devices cannot
write to the API.

This has yet to be completed or documented.
