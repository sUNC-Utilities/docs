# `cloneref`

!!! info "Creates a safe reference to protected instances"

    `#!luau cloneref` returns a reference to an [`#!luau Instance`](https://create.roblox.com/docs/reference/engine/classes/Instance). This can help avoid weak table styled detections. 

!!! info "note on `#!luau cloneref` common use."

    This **was** commonly used to safely interact with specific services such as [`#!luau game.CoreGui`](https://create.roblox.com/docs/reference/engine/classes/CoreGui) but since Roblox made it so developers can't even reference/obtain said services (e.g.. `#!luau game.CoreGui` - `#!luau game:GetService("CoreGui")` all now return nil now)
    There's now no point of using this function on **internal services** that require a specific [thread-id/capability](https://github.com/Pseudoreality/Roblox-Identities/) for developers to access. note that this doesn't mean the function is useless it's still useful for protected instances or non-internal services that still get targeted such as [`#!luau UserInputService`](https://create.roblox.com/docs/reference/engine/classes/UserInputService).

`#!luau cloneref` returns a **reference clone** of an [`#!luau Instance`](https://create.roblox.com/docs/reference/engine/classes/Instance). The returned object behaves identically to the original but is not strictly equal (`==`) to it.

```luau
function cloneref<T>(object: T & Instance): T
```

## Parameters

| Parameter       | Description                                                                                                               |
| --------------- | ------------------------------------------------------------------------------------------------------------------------- |
| `#!luau object` | The [`#!luau Instance`](https://create.roblox.com/docs/reference/engine/classes/Instance) to clone a safe reference from. |

---

## Example

```luau title="Cloning a safe reference to LocalPlayer" linenums="1"
local players = game:GetService("Players")

local original = players.LocalPlayer
local clone = cloneref(original)

print(original == clone) -- Output: false
print(clone.Name)        -- Output: Player's name (same as original)
```
