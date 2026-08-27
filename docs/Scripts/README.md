# Scripts

The **Scripts** library provides advanced functions for inspecting and interacting with script objects. It allows you to analyse bytecode, retrieve closures and environments, and simulate the loading or running of scripts.

---

## What can you do?

With the Scripts library, you can:

- **Read compiled bytecode** from scripts using [`#!luau getscriptbytecode`](./getscriptbytecode.md)
- **Get the bytecode hash** of a script using [`#!luau getscripthash`](./getscripthash.md)
- **Create a new closure based off of the script's bytecode** using [`#!luau getscriptclosure`](./getscriptclosure.md)
- **Access script environments** with [`#!luau getsenv`](./getsenv.md)
- **Enumerate script objects** using [`#!luau getscripts`](./getscripts.md) and [`#!luau getrunningscripts`](./getrunningscripts.md)
- **List loaded modules** via [`#!luau getloadedmodules`](./getloadedmodules.md)
- **Determine the current script** executing via [`#!luau getcallingscript`](./getcallingscript.md)
- **Resolve the script associated with a thread** using [`#!luau getscriptfromthread`](./getscriptfromthread.md)
