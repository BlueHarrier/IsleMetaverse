# Module (interface)

## Overview

Modules exist to implement behaviors to the nodes. There are plenty of different API implementations that give high performance behaviors, like physics calculations and mesh rendering, but it allows for JS and TS class implementations as well.

Modules are handled through the use of events that are periodically called by the node or other modules. In order to register and unregister them, the methods `enterNode()` and `exitNode()` are used.

| Property | Type |
|----------|------|
| `node` | `Node` |

| Method | Returns | Required |
|--------|---------|----------|
| `enterNode()` | `Null` | No, but pointless not to implement |
| `exitNode()` | `Null` | No |

## Property descriptions

### `Node` node

The node that the module belongs to. It will be remain `Null` until it's the module is added to any node, and it will reset on every update. Its value will remain valid right before `enterNode()` is called to after `exitNode()` is executed.

## Method descriptions

### enterNode()

This method will automatically run when a module is added to the node. It's designed to register all the events assigned with the node so the logic of the module starts running.

### exitNode()

This method is designed to clear anything else that has been defined in `enterNode()` besides the callbacks, as they will clear automatically.
