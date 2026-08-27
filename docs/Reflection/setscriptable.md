# `setscriptable`

!!! warning "Detection risks"

    `#!luau setscriptable` can expose detection vectors. Games may check whether certain properties are unexpectedly accessible, which can lead to detections.

!!! info "Limited property support"

    Not all hidden properties can be obtained using this function.

`#!luau setscriptable` toggles the scriptability of a hidden or non-scriptable property on an [`Object`](https://create.roblox.com/docs/reference/engine/classes/Object). When a property is made scriptable, it can be accessed or assigned through standard indexing.

```luau
function setscriptable(object: Object, property_name: string, state: boolean): boolean | nil
```

## Parameters

| Parameter              | Description                                                                                                 |
| ---------------------- | ----------------------------------------------------------------------------------------------------------- |
| `#!luau object`        | The [Object](https://create.roblox.com/docs/reference/engine/classes/Object) that owns the target property. |
| `#!luau property_name` | The name of the property to make scriptable or un-scriptable.                                               |
| `#!luau state`         | Whether to enable (`#!luau true`) or disable (`#!luau false`) scriptability.                                |

---

## Example

```luau title="Temporarily enabling scriptability of a property" linenums="1"
setscriptable(workspace, "SignalBehavior", true)
print(workspace.SignalBehavior) -- Output:  Enum.SignalBehavior...

setscriptable(workspace, "SignalBehavior", false)
print(workspace.SignalBehavior) -- Throws an error
```
