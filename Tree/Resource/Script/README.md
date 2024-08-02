# Script : IResource

## Overview

JavaScript script is the only officially supported scripted language for this specification, due to its flexibility, popularity, performance, and obfuscability. This class is used by the `ResourceManager` singleton to load additional modules, resources, importers, or general-purpose classes in the environment. Every script is loaded in a separate context, but they're all executed in the global scope. This means that scripts can interact with each other, but they can't access each other's variables or functions, unless they're explicitly imported.

> [!TIP]
> JavaScript objects are dynamic, so even if you didn't import a class, you can still access its properties and functions, as long as this script can get its reference, though, in order to ensure consistency, you can use compatible alternatives like TypeScript, which will ensure the type safety of the code. Don't forget to compile to JavaScript before packing your project.

| Property | Type |
|----------|------|
| `content` | `String` |

| Method | Returns |
|--------|---------|
| `getClasses()` | `String[]` |
| `getConstants()` | `String[]` |
| `getFunctions()` | `String[]` |
| `getVariables()` | `String[]` |

## Property descriptions

### `String` content

The content of the script, which will be executed by the `ResourceManager` singleton. This content must be written in valid JavaScript in order for the interpreter to compile it. The script can be as long as needed, but it's recommended to keep it as short as possible, as it will be loaded in memory.

## Method descriptions

### `String[]` getClasses()

Returns an array of class names that are defined in the script. This method will return an empty array if no classes are defined.

### `String[]` getConstants()

Returns an array of constant names that are defined in the script. This method will return an empty array if no constants are defined.

### `String[]` getFunctions()

Returns an array of function names that are defined in the script. This method will return an empty array if no functions are defined.

### `String[]` getVariables()

Returns an array of variable names that are defined in the script. This method will return an empty array if no variables are defined.
