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

Finally, the `.iep` file structure goes as follow:

```
|- Project.iep
  |- TREE.isl (Optional ecosystem tree)
  |- PACK.isi
  |- Folder1
    |- resource1
    |- resource2
    |- ...
  |- Folder2
    |- resource1
    |- resource2
    |- ...
```

### Generated resources

Some resources may be generated algorithmically by the API, like procedural textures or noise, in which case, the URI can be left empty, and only the importer will be specified. It's also possible to specify a virtual path in the `.isi` file, which will be used to generate the resource, and the importer will be used to interpret it.

This generated resource can be accessed in `repo://nonexistent/path`:

```json
{
    "GenResImporterClass@nonexistent/path": {
        // Importer settings
    }
}
```

## Coconuts (WIP)

Coconuts (as usually found in tropical isles) are they codename selected for the WebAssembly implementation of the ecosystem. As it's thought so far, the interaction is going to be interlaced between files and templates, and so, the API is more strict than web is. This is because a established environment is needed to run semi-native applications. For this, it's been chosen a Linux environment, with some extra services that allow for all the calls to be made. The API is going to be designed for Rust, as it's more modern and safe than C and C++, as well as easier to maintain in the future, though, virtually any language can be used to interact with the API, as long as it can be compiled to WebAssembly. The files that are going to be using are, of course `.wasm` files, but in order to differentiate libraries from executables, these last ones use the extension `.nut`. Coconuts (nuts for short) are not only a way to run the ecosystem, just like JavaScript and TypeScript, but also faster, more secure, and with additional access to lower level APIs, like Vulkan and OpenGL, which are going to be used to render the ecosystem (implementations can translate calls to DirectX if they need to, but Vulkan is highly encouraged). This allows for custom ecosystem engines to be made, replacing the default runner, and also opens the door to create native operating systems designed specifically for the ecosystem, but can also run other applications.

In order to run a nut, `.isl` file includes a field called `application`, which is a link directly to the `.nut` file.

> [!TIP]
> In order to run a nut directly from a `.iep` file, the `.nut` executable would be called `APP.nut`, so `TREE.isl` will not be needed, as the nut can generate a tree on its own.
> If both are included, the tree will be created in the environment, and the nut will be executed.

## Safety concerns

The Isle Ecosystem is designed with safety in mind, of course, and so, a hierarchy is established within the templates. Each Isle Ecosystem template is isolated from the others in ascending order, so lower template nodes cannot access higher ones. This is done to prevent malicious code run from different clients in the same isle to access each other's data, or simply bothering the users in the session. Though, each element can be access in descending order, so the root template can access everything, but children templates, such as avatars, summonable items, or other elements that the system might require, have limited access to other templates. Though, this doesn't prevent objects from interacting with each other, like using triggers, or sending messages, but as this are broadcast messages, they don't allow templates to access each other's data, just sending and receiving expected data.

Worlds can also control how much freedom children templates have, and can even restrict them from sending messages, or even moving, if the world owner decides so. This is done to prevent malicious code from running in the ecosystem, and to keep the users safe.

## Avatars

Based on previous implementations of the metaverse, such as Resonite and VRChat, avatars are the interface between the user and the ecosystem. They are the representation of the user in the isle, and they can be anything that you can imagine. Avatars can be humanoid creatures, animals, or even objects, and can be controlled by the user. Though, the way they interact is a thing of two. While the avatar sets the appearance, toys, and gadgets that they want, the movement of the user through the world is define by this entity, as malicious avatars could easily mess with the other user's experience. Hence, worlds can set up movement rules, as well as size (scale) restrictions, tag restrictions, and even the ability to interact with other avatars. This is done to prevent griefing, and to keep the ecosystem safe.

### Avatars in the tree

Tree objects always have a name, but that can create a small problem: name conflicts. In order to prevent these conflicts, there is a reserved prefix specific to avatars, which is `@`. This prefix is used to identify avatars in the tree, and so, they can be easily found and managed.

### Shifting avatars

An avatar shift is the process of changing the avatar. If the established avatar is valid, while it downloads, the user can still move and interact normally, but if the avatar is invalid, the runner will request the server to give them a default avatar, and the user will be stuck in the void until the avatar is downloaded. If this change is smooth, the user won't even notice their short stay in the void.

### Unbound avatars

An avatar that is not being used by any user, but is summoned in the world, can be called "unbound". These avatars can be picked up and clone by users, and even being used as NPCs, or even another special and unique way to interact with world, just saying 👀. This is useful to share avatars with other users by summoning them into the world, without shifting your own.

### Unbound users

In the other hand, if a user doesn't have an avatar, what happens? Avatars are the interface with the ecosystem, so a user simply cannot exist without an avatar. In that case, the runner must request the server to give them an avatar. This avatar can be a default one, or even a random one, but it must be an avatar. In the meantime, the user can chill out in the void, or something.

## Artifacts

Artifacts are templates that can be spawned by users, and may be interactable. There's really no class that controls the artifacts, as they're just simple pieces of ecosystem, so effectively, worlds and avatars can be artifacts as well. The user owner of said artifact is kept, so they can always remove them if they want, doesn't matter where is it in the tree. As avatars are templates, and so, isolated, they can always communicate with messages and triggers.

### Artifacts in tree

Similar to avatars, artifacts have a reserved prefix, which is `%`. This prefix is used to identify artifacts in the tree, and so, they can be easily found and managed. This is also useful to identify artifacts, as they are a special type of object, and should be treated as such.

## Worlds

Worlds are the continent of the ecosystem. They give the environment in which objects can interact with, including the rules, the physics, and the behavior of the objects. Worlds can be anything, from a simple room, to a whole universe, and can be controlled by the user that created them. Worlds can also be shared, and even be used as templates for other worlds, or even avatars. Worlds can also be used to create pocket worlds, which are worlds inside other worlds, and can be used to create very complex applications.

### Spawn points

Spawn points are not required in a world, avatars would spawn at (0, 0, 0) coordinates, but they can be placed, and then managed by the world as it needs to. Also, by default avatars will spawn as children of the world node, but it can also be changed to spawn on any other node, as long as it's a child of the world node. This also includes spawning inside other pocket worlds within the main one.

### Griefing prevention

To prevent other users to force people into pocket worlds, the only means of traveling between them is either a script doing the job, which requires a higher hierarchy, or a portal, which can only be access by the user's interaction, knowing that they are going to be teleported to another world.

### Pocket worlds

Pocket worlds, or more commonly named "dimensions", is a way in which the ecosystem can run multiple worlds at once, in the same environment. This is done by adding the `World` module to another node inside the already existing tree. Avatars will only be able to see and interact with elements that are in the same world as them, and travel between them using portals (class `Portal`). Portals can be instantiated by the scripting API, exist already in the tree, or even be created by the ISLE server. This allows for more complex applications to be made, like games, or even social networks, where users can interact with each other in different worlds, but still be in the same environment.

> [!TIP]
> In order to instantiate a portal back to a superior world, as they might be running in another template, the one world higher in the hierarchy can communicate with the world and add the portal to the world's spawn point.

> [!CAUTION]
> It's important to note that users should be allowed to respawn back into the default world, as they might get stuck in a world that doesn't allow them to go back to a superior world. The protocol will include a special instruction to request a respawn back to the default world, that will occur if allowed by the server.
> In the case of the client being run locally, the user can always do this, without the need of any server's permission.

Worlds can be instantiated inside everything (as long as the working hierarchy allows it), creating very interesting concepts, such as avatars holding pocket worlds, or artifacts that can be used to create new worlds. This allows for a very flexible system, where the user can create virtually anything they want, and the ecosystem will adapt to it.

### Between-worlds interaction

Worlds running in the same hierarchy can communicate between each other, and so, many cool stuff can be made with this, such as using cameras to render another world, as I'm writing this, I'm thinking about a small artifact, a snow globe, that, when interacted with (portal) can put users inside of it, allowing them to see the world outside, and the users outside, to see the world inside. This is a very cool concept, and can be used to create very interesting applications, and can even be implemented in an avatar, so it can be a pocket dimension in a character's collar, or even a pocket watch!

### Null world

What happens if there's no world attached anywhere on top of the avatar? I already see people panicking, but don't worry. All modules in Isle have default parameters, and worlds do too, so, in case of no world being available above the avatar, the default world parameters will be taken to display at least something.

## Definitions

- Scene: Reference to the origin of the tree. Scenes don't have behavior, and can represent only one of the three elements that compose the ecosystem, may it be a World, Avatar, or Artifact.
- Node: Scene object that is available in the scene tree, which contains a unique name in the order where they belong, is made out of components, and can have child nodes.
- Module: Free to define data block, with a name (key) that establishes the class to attach the behavior from.
