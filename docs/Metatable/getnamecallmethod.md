# `getnamecallmethod`

!!! info "This function returns the active `#!luau __namecall` method, whether or not that metamethod is hooked. It returns `#!luau nil` when no namecall method is available."

`#!luau getnamecallmethod` returns the name of the method that invoked the [`#!luau __namecall`](https://devforum.roblox.com/t/how-do-i-get-namecall-method/2848439/5) metamethod.

It retrieves the method being called (e.g. `#!luau InvokeServer`) from the current `#!luau __namecall` invocation. This works both in a normal `#!luau __namecall` metamethod and in a [`#!luau hookmetamethod`](../Closures/hookmetamethod.md) hook targeting `#!luau __namecall`.

When no namecall method is available, this function will safely return `#!luau nil`.

```luau
function getnamecallmethod(): string?
```

## Parameters

| Parameter | Description                        |
| --------- | ---------------------------------- |
| *(none)*  | This function takes no parameters. |

---

## Example

```luau title="Disallowing the usage of game:service()" linenums="1"
local refs = {}

refs.__namecall = hookmetamethod(game, "__namecall", function(...)
    local self = ...
    local method = getnamecallmethod()

    if self == game and method == "service" then
        error("Using game:service() is not allowed.")
    end

    return refs.__namecall(...)
end)
```
