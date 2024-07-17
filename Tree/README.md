# Isle Tree Format

## Introduction

Over the years, video game development workflows have evolved towards a tree structure pattern. This tree, usually called hierarchy as well, allows for objects, often called nodes, to be made out of other nodes recursively to create complex scenes. This dependent nodes, called children, can inherit characteristics fom their parents as well, like transformation and style. In order to define the purpose of each node, game engines have two different approaches: inheritance and module integration. The first approach is simpler to understand and implement, as each node has one specific and specialized behavior, but the second approach allows for one node to have multiple behaviors.

To achieve this, the Isle Ecosystem uses a mixture of both approaches, having a single node as a root, but each node being able to have multiple modules attached to it. This allows for a more flexible and extensible system, where each node can have many behaviors, and can be easily extended by the community developers.

## Isle files

The Isle Ecosystem collects a total of 6 different new file extensions. This might sound intimidating at first, but some of them serve the same purpose, and others are just different versions of the same file. The extensions are:

1. `.isl`: Isle file, containing the whole ecosystem tree structure. This will be a JSON file, containing metadata, the data structure, and the repository to obtain the required `.iep` and `.iez` files from.
2. `.isi`: Isle Ecosystem Index file, with a special JSON structure that allows for resources to be indexed and imported properly in the system. Keep in mind that it's possible to import virtually any format, as custom importers can be created in JavaScript and TypeScript.
3. `.iep`: Isle Ecosystem Package, containing the assets required to run `.isl` files. These are `.tar` files, which can have an `PACK.isi` file indexing all the resources and how to import them. If it's not included, they can also be imported from the inside of the tree. Check [resources](Resource/README.md) for more information. They can also have a `TREE.isl`, making this file a standalone ecosystem.
4. `.iez`: Isle Ecosystem Zip, which is the same as the `.iep` file, but in a `.zip` format.

## URIs and repositories

In order to load assets in the ecosystem, URIs are essential. Though, the system might encounter issues loading the files when it doesn't know how to interpret them. For this purpose, the Isle Ecosystem uses special URIs, which combine the class needed to import the file into a valid resource, and the path to the actual file. This allows for the system to load the file properly, and to know how to interpret it. The URIs are structured as follows: `NameOfTheImporterClass@path/to/the/file`. The path can also include a protocol, such as `http://` or `https://`, to load the file from the internet.

Repositories are an even easier way of importing the resources. They are included in the `.isl` file, and allow anything running in that scope to access resources by calling the protocol `repo://`. This is useful for loading assets from the ecosystem, as they can be downloaded all at once, and then loaded from the repository, and not from the internet, which is a lot faster. Repositories are also an object, so they can have names assigned to them, and so, multiple repositories can be used at once, making it easy to create dependency packages and libraries. In order to differentiate between the repositories, the name must be specified in the URI: `repo://NameOfTheRepository:path/to/the/file`. If the repository is not specified, the default one will be used, which will be declare with the name `.` in the repository object. So far, you may have noticed that the importer class hasn't been mentioned yet with the repository protocol, and this is because repositories have a way of defining the importer class as well: the `.isi` file. Repositories always point towards a `.isi` file, or a `.iep` / `.iez` file, which contains the pack index, and the importer class for each resource, predefining settings for the resources importers.

### Example

This is an example of the repository section in a `.isl`:

```json
{
    "repository": {
        ".": "https://example.com/default/repo.iep",
        "anotherSource": "https://example.com/another/repo.isi"
    }
}
```

And an example of a `PACK.isi` file inside a `.iep` file:

```json
{
    "ImporterClass@path/to/resource": {
        // Importer settings
    },
    "AnotherImporterClass@another/path/to/resource": {
        // Importer settings
    }
}
```

As we were saying, it can also happen that a repository points towards a raw `.isi` file, which doesn't really have local paths, but instead, it uses absolute URIs:

```json
{
    "ImporterClass@https://example.com/path/to/resource": {
        // Importer settings
    },
    "AnotherImporterClass@https://example.com/another/path/to/resource": {
        // Importer settings
    }
}
```

Resources can use their `import` parameter to point towards a local resource, which will be imported automatically.

```json
{
    "import": "repo://RepositoryName:path/to/resource"
}
```

Resources can also point towards a non-imported resource, for which, they can use the `settings` parameter in order to define the importer class and settings:

```json
{
    "import": "ImporterClass@https://example.com/path/to/resource",
    "settings": {
        // Importer settings
    }
}
```

They can also use these settings to override the default repository settings, and even the importer class:

```json
{
    "import": "AnotherImporterClass@repo://RepositoryName:path/to/resource",
    "settings": {
        // Importer settings
    }
}
```

## Definitions

- Scene: Reference to the origin of the tree. Scenes don't have behavior, and can represent only one of the three elements that compose the ecosystem, may it be a World, Avatar, or Artifact.
- Node: Scene object that is available in the scene tree, which contains a unique name in the order where they belong, is made out of components, and can have child nodes.
- Module: Free to define data block, with a name (key) that establishes the class to attach the behavior from.
