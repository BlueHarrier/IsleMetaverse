# Overview of the Isle Ecosystem

## Introduction

Isle is more than just a file structure, or a protocol, or a scripting API, it's an ecosystem, which means that it's the combination of all of those things, and the tight relationship between them. The Isle ecosystem is designed to be a powerful tool for managing and organizing the metaverse, and it's designed to be flexible and extensible, so that it can be adapted to a wide variety of use cases.

It's important for implementors and developers to understand the different parts of it, but also for users to understand what they can do, and some basic notions of how it works. This document is meant to be a high-level overview of the Isle ecosystem, and to provide a starting point for understanding how it works, and how to use it.

## Index

The Isle ecosystem is built around a few key concepts, which are used to organize and structure the data and the code that make up the ecosystem. These concepts are:

### For everyone

- [Avatars](./Avatars/): Are the way the user interfaces with the ecosystem. They're templates that get bound to the user on connect.
- [Worlds](./Worlds/): Are the top level of the hierarchy tree. They're the root of the tree, and they contain all the other nodes and templates, but they can also exist within other elements of the tree.
- [Artifacts](./Artifacts/): Are other templates that be summoned by users, and can serve multiple purposes, like entertainment, information, or even as a way to interact with the world.
- [Gateway](./Gateway/): The gateway is the application that connects the user to the ecosystem. Think about it like a web browser, but for the metaverse.
- [Isle](./Isle/): Isles are instances of the ecosystem, basically, servers where a tree is hosted. They can be public or private, and be hosted by anyone, anywhere. They can implement their own login system, or use a third-party one, and they can have their own rules and restrictions. They can also be linked to other isles, forming a network of isles. Back to the previous example, think about it like a website, but "multiplayer", for the metaverse.

### For developers

> [!NOTE]
> Not to mistake with implementors, developers are content creators that make things for the ecosystem, like worlds, avatars, or artifacts.

- [Templates](./Templates/): Templates are the building blocks of the ecosystem. They represent chunks of the hierarchy tree, and make sure each application running in one branch is isolated from each other. Templates are used to define the structure of the hierarchy, and to define the behavior of the applications that run in that tree.
- [Nodes](./Nodes/): They're the basic structure of the tree hierarchy. They represent basically anything in the world, and they can have behaviors attached to them.
- [Modules](./Modules/): Modules are the behaviors that can be attached to nodes. The API provides a big portion of them, but custom ones can be added by using the scripting API.
