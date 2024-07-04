# Isle Tree Format

## Introduction

Over the years, video game development workflows have evolved towards a tree structure pattern. This tree, usually called hierarchy as well, allows for objects, often called nodes, to be made out of other nodes recursively to create complex scenes. This dependent nodes, called children, can inherit characteristics fom their parents as well, like transformation and style. In order to define the purpose of each node, game engines have two different approaches: inheritance and component integration. The first approach is simpler to understand and implement, as each node has one specific and specialized behavior, but the second approach allows for one node to have multiple behaviors.

As each individual system has their own structure, there's no standard way of representing a scene tree. Formats like [glTF 2.0](https://github.com/KhronosGroup/glTF/tree/main/specification/2.0) try this, but during our first ITF implementation attempt, we found a lot of difficulties involving the static form of the tree, which makes it hard to make dynamic with ease. Instead, ITF departs from the same concept, but makes it dynamic, and takes immediate consideration on the scripting API to create a node - component system.

To achieve this, ITF files use a Json structure to represent the type of asset, the resources required by this file, and the metadata. Another file type also exists, the ITL (Isle Tree Library), which contains only a collection of resources.

## Definitions

- Scene: Reference to the origin of the tree. Scenes don't have behavior, and can represent only one of the three elements that compose the ecosystem, may it be a World, Avatar, or Artifact.
- Node: Scene object that is available in the scene tree, which contains a unique name in the order where they belong, is made out of components, and can have child nodes.
- Module: Free to define data block, with a name (key) that establishes the class to attach the behavior.
