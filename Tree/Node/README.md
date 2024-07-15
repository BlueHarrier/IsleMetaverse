# Node

## Overview

Nodes are the unit of the scene tree. They are interrelated objects that inherit one from another, creating a collection of parents and children, each with unique properties and behaviors. They might also inherit from a template, which are other imported ITF structures.

| Property | Type | Required |
|----------|------|----------|
| `children` | `Object` | No |
| `modules` | `Object` | No |
| `template` | `String` | No |
| `settings` | `Object` | No |

## Property descriptions

### `Object` children

A collection of named `Node` children.

> [!IMPORTANT]
> The name of children nodes cannot start with "@" or "$", and cannot contain ":", due to those characters being reserved to identify avatars, user-summoned assets, and modules in paths, respectively.

### `Object` modules

A collection of the `Module` objects that compose the behavior of the node. The keys of this object are the names of the modules to attach, while the value can be a `Module` object, or an array of them, if there's more than one of that module implemented.

#### Example

```json
{
    "MySingleModule": {
        // Module settings
    },
    "MyMultipleModule": [
        {
            // Settings of the first instance of this module
        },
        {
            // Settings of the second instance of this module
        }
    ]
}
```

### `String` template

URI to a `Template` resource that this node will inherit from. In case of this value being defined, children might no longer be added if they exist in the template, but rather replace the template nodes.

### `Object` settings

Settings of the `TemplateImporter` object, used to change import settings of it, and alter, override, or delete values.
