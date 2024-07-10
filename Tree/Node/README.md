# Node

## Overview

Nodes are the unit of the scene tree. They are interrelated objects that inherit one from another, creating a collection of parents and children, each with unique properties and behaviors. They might also inherit from a template, which are other imported ITF structures.

| Property | Type | Required |
|----------|------|----------|
| `children` | `[String]: Node` | No |
| `modules` | `[String]: Module \| Module[]` | No |
| `template` | `String \| Template` | No |

## Property descriptions

### `[String]: Node` children

A collection of named `Node` children.

> [!IMPORTANT]
> The name of children nodes cannot start with "@" or "$", due to those characters being reserved to identify avatars and user-summoned assets, respectively.

### `[String]: Module | Module[]` modules

A collection of the `Module` objects that compose the behavior of the node. The keys of this `Object` are the names of the modules to attach, while the value can be a `Module` or an array of them, if there's more than one module implemented.

#### Example

```json
{
    "MySingleModule": {
        // Module settings
    },
    "MyMultipleModule": [
        {
            // Settings of the first module of this type
        },
        {
            // Settings of the second module of this type
        }
    ]
}
```

### `String | Template` template

`Template` resource that this node inherits from. In case of this value being defined, children might no longer be added if they exist in the template, but rather modify the template nodes.

> [!WARNING]
> This part is still in development, as for now this specification can only override pre-existing values and add new ones, but not delete any.
