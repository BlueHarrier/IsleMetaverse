# Repository

## Introduction

Repositories are all the sources required by the tree, from which all the resources can be obtained.

## Overview

ITF Resources are organized in repositories, each one pointing towards a zip or tar file, or a raw path. These repositories must be indexed properly, which can be done in two ways: in-file manifest, or a `manifest.itr` file inside the repository. If there's no manifest, the resources will deem impossible to import, and will result in a non critical error.

Some resources can be procedural, which means, they will not exist as files within the repository, but instead be generated at runtime. Though, they must have a reference inside the repository.

### Example

Repositories can be directed using only an `uri`, in which case, there's a promise that the file or path specified will have a `manifest.itr`.

> [!WARNING]
> If the `manifest.itr` file is not located inside the repository, the repository will refuse to be load and discarded.

```json
{
    "myTarRepository": {
        "uri": "https://domain.mine/myResources.tar"
    }
}
```

If the repository that wishes to be downloaded doesn't have a manifest file, the in-file manifest can be used. It follows the same structure that a `manifest.itr` file would.

> [!WARNING]
> If any of the files is not listed in the repository, that resource will be inaccessible.

```json
{
    "myPathRepository": {
        "uri": "resourcesPath",
        "manifest": {
            "path/to/image.png": {
                "type": "image/png",
                "resource": {
                    // png import settings
                }
            },
            "path/to/scene.glb": {
                "type": "scene/glTF",
                "resource": {
                    // glTF import settings
                }
            }
        }
    }
}
```

> [!NOTE]
> If a manifest file exists inside the repository, but a `manifest` property was incorporated, conflicting import configurations specified in the repository definition will override the ones in the manifest file.

Procedural resources don't require an `uri`, but still require a path in a repository.

```json
{
    "myProceduralRepository": {
        "manifest": {
            "path/to/procedural/resource": {
                "type": "generated/GradientTexture",
                "resource": {
                    // Gradient texture generation settings
                }
            }
        }
    }
}
```

### Structure

| Property | Type | Description | Required |
|----------|------|-------------|----------|
| `uri` | `String` | Path to the desired resource, which can be obtained from a local directory, or HTTP, and be a simple path, or point to a zip or tar file. | Yes, except if all the resources included are generated |
| `manifest` | `Object` | Manifest expressed in line, with the resources that are available to the asset from this repository. | No, but the location specified by the `uri` must have a manifest file |

### Manifest

In order to safely import resources from the internet into the Isle browser running the ecosystem, there must be a way to specify what resources are required, and how to load them. The manifest serves this purpose, by allowing the content creator to define what they need, from where within a repository, and what is it.

Hence, the manifest doesn't have fixed properties, but keys, which are local paths to each resource, which are then expanded into what they are and how to import them.

In order to create libraries or collections of resources, manifests can be introduced within a repository as `manifest.itr`, which will follow this structure.

### Internal URIs and restrictions

In order to access registered resources, it's necessary to use the `repo` protocol, so a resource of the `myRepository` repository, located in `path/of/resource`, would be accessed like this: `repo://myRepository/path/of/resource`. Some files exists with the intent of storing multiple resources, such as glTF, and so, those resources can be requested by following the internal structure of the file, so, to access a glTF mesh, it could be done like so: `repo://myRepository/path/to/gltf.glb/meshes/0`, which would return a usable imported `Mesh` resource that can be used. Like this, it's also posible to access other ITF files, including their repositories, but this can only be done in descending flow, so it's not possible for an ITF file to access its parent, if it has one.
