# Importer\<T: Resource> (interface)

## Overview

Importing resources can be a bit tricky sometimes. There are a lot of formats possible, each with its own uniqueness and complexity, therefore, there must be a system to import each type of resource, and, if the project requires, implement new ways of importing resources.

| Method | Returns | Required |
|--------|---------|----------|
| `export(settings: Object, file: File)` | `Number` | No |
| `import(settings: Object, file: File)` | `T` | Yes |
| `validate(settings: Object, file: File)` | `Number` | No |

## Method descriptions

### `Number` export(settings: `Object`, file: `File`)

Tries to export the resource into the specified file, and write its settings for export. If not implemented, it will return `0` (OK).

> [!NOTE]
> This function is more commonly used for editors.

### `T` import(settings: `Object`, file: `File`)

Imports the file in the system, returning the corresponding type of the `Resource`.

> [!IMPORTANT]
> This function will only execute after `validate`, so it's assumed that the resource exists and it's valid.

### `Number` validate(settings: `Object`, file: `File`)

Validates the file and the settings, and returns an error code if it fails. If not implemented, it will return `0` (OK). If an error is returned, the resource will be considered invalid, and so, discarded.
