# `setthreadidentity`

!!! info "Not all locked functions can be called"

    Some functions like `#!luau debug.dumpheap()`, `#!luau debug.dumprefs()`, or other similar debug functions strictly require the calling thread to be `CommandBar` to be called.
    So just changing your thread's id to `4` (CommandBar Id) will mostly not work.

`#!luau setthreadidentity` sets the current [Luau thread](https://create.roblox.com/docs/reference/engine/libraries/coroutine#running) [identity and capabilities](https://github.com/Pseudoreality/Roblox-Identities/) matching that identity.

This is commonly used alongside functions like [`#!luau gethiddenproperty`](./gethiddenproperty.md) or [`#!luau getconnections`](../Signals/getconnections.md) which may require elevated access.
or maybe used to obtain engine features like specific propeties, methods, intances, that are locked behind specific capabilities that level 7 or 8 don't have such as [InternalTest](https://github.com/Pseudoreality/Roblox-Identities/blob/main/Capabilities/60%20-%20InternalTest.md).

```luau
function setthreadidentity(id: number): ()
```

## Parameters

| Parameter   | Description                                      |
| ----------- | ------------------------------------------------ |
| `#!luau id` | The [identity level](https://github.com/Pseudoreality/Roblox-Identities/tree/main/Identities) to set the current thread to. |

---

## Example

```luau title="Changing thread identity to obtain CoreGui" linenums="1"
local function GetCoreGui()
	if game:GetService("CoreGui") then
		return true, game:FindService("CoreGui")
	end
	return false, nil
end

setthreadidentity(2)
print(GetCoreGui()) -- false, nil

setthreadidentity(8)
print(GetCoreGui()) -- true, CoreGui
```

## Example 2

```luau title="Changing thread identity for features not available for 7 or 8" linenums="1"
local RunService = game.RunService
local function FrameNumber()
	local success, frame = pcall(function()
		return RunService.FrameNumber
	end)
	if success then
		return success, type(frame)
	end
	return false, frame
end

print(getthreadidentity()) -- 7 or 8
print(FrameNumber()) -- false, The current thread cannot read 'FrameNumber' (lacking capability InternalTest)

setthreadidentity(3)
print(FrameNumber()) -- true, number
```
