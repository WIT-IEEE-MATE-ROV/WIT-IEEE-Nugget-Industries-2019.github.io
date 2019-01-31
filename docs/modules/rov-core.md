---
layout: default
---

# `rov-core`
The Rov Core is the only piece of code called by the user (or system daemon). It then spawns all other processes. Once all other
processes are spawned, it will then look at the heartbeat nodes and use the procid nodes on the API to ensure that each module
is behaving properly. In the event that it is not behaving properly, rov-core will first stop the process if necessary, and
then re-spawn it. By keeping the system modular, if a process should fail, rov-core can respawn it with minimal interruption.

For this reason, rov-core is kept as minimal as possible-- all functionality that can exist elsewhere, should. This lowers the
likelihood of a catastrophic error happening in the rov-core. 

When rov-core recieves the shutdown signal, it closes all named pipes, closes all child processes, and then closes itself.
