# Template : IResource

## Overview

Templates are isolated tree structures, which can be instantiated in real time in any part of the tree. They're also used to create store any complex instantiable asset, such as avatars, worlds, and artifacts.

| Property | Type |
|----------|------|
| `children` | `Node` |
| `modules` | `Module` |

| Method | Returns |
|--------|---------|
| `instantiate()` | `Node` |
| `pack()` | `Undefined` |

## Property descriptions

### `Object` children

A collection of named `Node` children, which will be instantiated when the template is instantiated.

### `Object` modules

A collection of the `Module` objects that compose the behavior of the template. The keys of this object are the names of the modules to attach, while the value is an array of instances of that module.

## Method descriptions

### `Node` instantiate()

Instantiates the template, returning the root node of the tree.

### `Undefined` pack()

Populates `children` and `modules` with the current state of the tree, so it can be saved to a file.
