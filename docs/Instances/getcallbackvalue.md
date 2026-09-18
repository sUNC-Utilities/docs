# `getcallbackvalue`

`#!luau getcallbackvalue` retrieves the **assigned callback property** on an [`#!luau Object`](https://create.roblox.com/docs/reference/engine/classes/Object), such as [`#!luau OnInvoke`](https://create.roblox.com/docs/reference/engine/classes/BindableFunction#OnInvoke).

Normally, these properties are **write-only**, meaning you can assign a function to them but cannot read them back. This function bypasses that limitation and exposes the function directly.

```luau
function getcallbackvalue(object: Object, property: string): any | nil
```

## Parameters

| Parameter         | Description                                                                                                            |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------- |
| `#!luau object`   | The [`#!luau Object`](https://create.roblox.com/docs/reference/engine/classes/Object) that owns the callback property. |
| `#!luau property` | The name of the callback property to retrieve.                                                                         |

---

## Example

```luau title="Retrieving a valid callback function, an unset property, and a missing property" linenums="1"
local dummy_bindable = Instance.new("BindableFunction")
local dummy_remote_function = Instance.new("RemoteFunction")

dummy_bindable.OnInvoke = function()
    print("Hello from callback!")
end

local retrieved = getcallbackvalue(dummy_bindable, "OnInvoke")
retrieved() -- Output: Hello from callback!

print(getcallbackvalue(dummy_remote_function, "OnClientInvoke")) -- Output: nil
```
