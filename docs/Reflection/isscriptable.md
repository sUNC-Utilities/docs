# `isscriptable`

`#!luau isscriptable` returns whether the given property of an [`Object`](https://create.roblox.com/docs/reference/engine/classes/Object) is scriptable (i.e. it does not have the `#!luau notscriptable` tag).

If it returns `#!luau true`, then the property is scriptable and can be indexed normally, and vice versa.

If it returns `#!luau nil`, then the property provided does not exist.

```luau
function isscriptable(object: Object, property: string): boolean | nil
```

## Parameters

| Parameter         | Description                                                                                                   |
| ----------------- | ------------------------------------------------------------------------------------------------------------- |
| `#!luau object`   | The [`Object`](https://create.roblox.com/docs/reference/engine/classes/Object) that owns the target property. |
| `#!luau property` | The name of the property to check.                                                                            |

---

## Example

```luau title="Checking the scriptability of a property" linenums="1"
local part = Instance.new("Part")

setscriptable(part, "Name", false)

print(isscriptable(part, "Name")) -- false
```
