# Repository

## Overview

Though some elements of the scene can be created in real time, other more complex resources may be needed from different sources. For ease of encapsulation, as using URLs all the time would be very slow, ITF files possess a repository, filled with all the file dependencies that the project might require, as well as providing an alias for easy access to those files in the project.

The corresponding URI to access these sources will use the protocol `repo://`, followed by the name of the repository, and the path to the desired resource, like so: `repo://MyRepository:path/to/resource`. The API will do the connection with the pre-downloaded asset and will return the imported resource.

> [!NOTE]
> Check the [Importer class documentation](./Importer/) for more information.

## Properties

Each property of the repository corresponds to the alias that the source receives to be accessed locally using `repo://` within the project, and defines with a string the URI of the actual source.

### Project source

Most projects may have a project source. This is the one that is used by default, and so, the name of the repository can be omitted in the URI. This project source will be named `.`, and will allow resources to be accessed directly in this way: `repo://path/to/resource`.

### Example

```json
{
    ".": "uri/to/my/project/location",
    "Dependency": "https://domain.mine/dependency/location"
}
```

In the previous example, all files in the project source (`.`) can be accessed from `repo://`, and the ones in the `Dependency` repo will be accessed using `repo://Dependency:`.

> [!TIP]
> Sometimes, depending on the server implementation, the project source may be pointing to the same path where the file was loaded from: `".": "."`.

## Sources

A source is essentially the location where all the importable files are located. This source can be a raw path, in which case, the resource indexing process might be a bit slow, or rather a path to a compressed file, which can be a zip, tar, or tgz, though, the same logic will be applied to all of them.

Sources must have an `index.json` file in the project root, which will be the guideline on how to import all files within a repository. Any file not listed in here will be ignored, and the lack of index will result in the repository being completely empty, as well as a warning.

The `index.json` file will have the following structure:

```json
{
    "path/to/image.png": {
        "class": "PNGImporter",
        "settings": {
            // PNG import settings
        }
    },
    "path/to/scene.glb": {
        "class": "GLTFImporter"
        // No settings where defined, and so, the default settings will be used
    }
}
```

| Property | Type | Required |
|----------|------|----------|
| `class` | `String` | Yes |
| `settings` | `Object` | No |

> [!IMPORTANT]
> If there's any error during the import process, the reference to the resource will be invalidated, and so, the resource will not be accessible.

> [!TIP]
> Clients shouldn't load all resources while the index process is happening, but as the nodes and application requires them, as some custom importers might not even be available yet.

### Property descriptions

#### `String` class

Name of the importer class that should be used whenever the asset needs to be loaded.

#### `Object` settings

Object that contains the settings required to import the resource. It can be overloaded with additional data that some specific client API implementations might use.
