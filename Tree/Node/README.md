# Node

## Overview

Nodes are the unit of the scene tree. They are interrelated objects that inherit one from another, creating a collection of parents and children, each with unique properties and behaviors. They might also inherit from a template, which are other imported ITF structures.

| Property | Type | JSON | Script |
|----------|------|------|--------|
| `children` | `Object` | Yes, not required | No |
| `modules` | `Object` | Yes, not required | No |
| `settings` | `Object` | Yes, not required | No |
| `template` | `String` | Yes, not required | No |

| Method | Returns |
|--------|---------|
| `addChild(Node child, String childName = "")` | `Undefined` |
| `addModule(Module module)` | `Undefined` |
| `addTemplate(Template template, String childName)` | `Node` |
| `callEvent(String eventName, Object eventData)` | `Undefined` |
| `exitTree()` | `Undefined` |
| `getChild(String childName)` | `Node` |
| `getChildCount()` | `Number` |
| `getChildren()` | `Node[]` |
| `getModule(String moduleName, Number moduleIndex = 0)` | `Module` |
| `getModuleCount(String moduleName)` | `Number` |
| `getModuleNames()` | `String[]` |
| `getModules(String moduleName)` | `Module[]` |
| `getName()` | `String` |
| `getParent()` | `Node` |
| `getPath()` | `String` |
| `getSibling(String siblingName)` | `Node` |
| `getSiblings()` | `Node[]` |
| `getRoot()` | `Node` |
| `hasChild(String childName)` | `Boolean` |
| `hasModule(String moduleName)` | `Boolean` |
| `hasSibling(String siblingName)` | `Boolean` |
| `registerEvent(String eventName, Function callback)` | `Undefined` |
| `removeChild(String childName)` | `Undefined` |
| `removeModule(String moduleName, Number moduleIndex = 0)` | `Undefined` |
| `setName(String newName)` | `Boolean` |
| `unregisterEvent(String eventName, Function callback)` | `Undefined` |

| Event | Data |
|-------|--------|
| `enterTree` | {} |
| `exitTree` | {} |
| `update` | {`Number` deltaTime }|

---

### Events

In order to keep the modules in sync with the application's pace, a set of events need to be triggered under various circumstances. Those events are given using a String, and will call functions called callbacks. Event callbacks expect one parameter called `eventData`, which contains all the information that the event provides to process whatever it needs.

Events can be triggered using `callEvent(String event, Object eventData)`, and they can be called from the node itself, or other modules.

### Sandbox

All templates are sandboxed by default, meaning that they can't access the global scope. Though, they higher templates can access the lower ones. This sandbox is managed by the API, preventing the node from obtaining anything above the template root. In order to allow access to higher templates, modules can be given a superior node reference, which will result in no error when trying to access it, or any of its functions. Always consider the security implications of this action, as it might lead to unexpected behavior.

API events will never break the sandbox, but they can be used to transfer data between templates, or to trigger actions in other templates. It's also possible to use global events, which will be triggered for all registered modules in the tree, regardless of the template they are in.

## Property descriptions

### `Object` children (JSON only)

A collection of named `Node` children.

> [!IMPORTANT]
> The name of children nodes cannot start with "@" or "$", and cannot contain ":", due to those characters being reserved to identify avatars, user-summoned assets, and modules in paths, respectively.

### `Object` modules (JSON only)

A collection of the `Module` objects that compose the behavior of the node. The keys of this object are the names of the modules to attach, while the value is an array of instances of that module.

#### Example

```json
{
    "MyModule": [
        {
            // Settings of the first instance of this module
        },
        {
            // Settings of the second instance of this module
        }
    ]
}
```

### `Object` settings (JSON only)

Settings of the `TemplateImporter` object, used to change import settings of it, and alter, override, or delete values.

### `String` template (JSON only)

URI to a `Template` resource that this node will inherit from. In case of this value being defined, children might no longer be added if they exist in the template, but rather replace the template nodes.

## Method descriptions

### addChild(`Node` child, `String` childName = "")

Adds another child to the node, with a specified name.

> [!NOTE]
> If this parameter is left empty, or it's invalid, the name that will be set instead is `"nodeN"`, where N is the number of children the node has before its instantiation.

### addModule(`Module` module)

Adds a new module to the node.

### `Node` addTemplate(`Template` template, `String` childName = "")

Adds a new child to the node, implementing a specific template resource.

### callEvent(`String` eventName, `Object` eventData)

Triggers an event, sending the free to setup information through the `eventData`. All registered callback functions will then be executed.

### `Node` getChild(`String` childName)

Attempts to retrieve a child node with the specified name. If there's none, it will return `Null`.

### `Number` getChildCount()

Returns the number of children that the node has.

### `Node[]` getChildren()

Gets an array containing all the children that the node has. If there are no children, it will return an empty array.

### `Module` getModule(`String` moduleName, `Number` moduleIndex = 0)

Gets a module based on its name. In case there are multiple modules of the same type, the index of it can be specified to retrieve the desired one. If the module is not found, it will return `Null`.

### `Number` getModuleCount(`String` moduleName = "")

Gets the number of implementation that the specified modules has in a node.

### `String[]` getModuleNames()

Returns an array with the name of all the modules that are implemented in the node. If there are no modules, it will return an empty array.

### `Module[]` getModules(`String` moduleName)

Returns an array with all the modules of one type. If there are no modules of that type, it will return an empty array.

### `String` getName()

Gets the name of the node in the hierarchy.

### `Node` getParent()

Returns the parent of the node. If the node is the root of the template, it will return `Null`.

### `String` getPath()

Gets the path relative to the template root. This path is unique for each node in the template.

### `Node` getSibling(`String` siblingName)

Returns a sibling of this node with the specified name. It will return `Null` if there sibling is missing, or if the node is the root of the template.

> [!WARNING]
> Looking up for the current node's name will return `Null`, as `this` is excluded when looking for siblings.

### `Node[]` getSiblings()

Returns the list of siblings that this node has. It will return an empty array if the node is the root of the template, or if it has no siblings.

> [!TIP]
> This method will return only the siblings, excluding `this`.

### `Node` getRoot()

Returns the root of the template that the node is located at. If the node is the root, it will return itself.

### `Boolean` hasChild(`String` childName)

Returns `true` if it can find a child with that name.

### `Boolean` hasModule(`String` moduleName)

Returns `true` if it can find a module with that name.

### `Boolean` hasSibling(`String` siblingName)

Tries to find a sibling with the specified name.

> [!WARNING]
> Looking up for the current node's name will return `false`, as `this` is excluded when looking for siblings.

### registerEvent(`String` eventName, `Function` callback)

Registers a new callback function for the desired event, which will be automatically called by this node, another node, or a module, when it's necessary.

> [!NOTE]
> Read [events](#events) for more information.

### removeChild(`String` childName)

Removes a child with the specified name.

### removeModule(`String` moduleName, `Number` moduleIndex = 0)

Removes a module with the specified name. In case there are multiple modules of the same type, the index of it can be specified to retrieve the desired one.

### `Boolean` setName(`String` newName)

Tries to set a new unique name to the node, returning `true` if it was successful.

### unregisterEvent(`String` eventName, `Function` callback)

Unregisters the specified callback function from the event.

## Event descriptions

### `enterTree` {}

This event is triggered when the node is added to the tree, and it's ready to start the application loop.

### `exitTree` {}

This event is triggered when the node is removed from the tree, and it's no longer part of the application loop.

### `update` {`Number` deltaTime }

This event is triggered every application tick, and it's used to update the node's logic. The `deltaTime` parameter is the time in seconds that has passed since the last frame.
