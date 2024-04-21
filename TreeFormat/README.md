# Isle Tree Format

## Introduction

Over the years, video game development workflows have evolved towards a tree structure pattern. This tree, usually called hierarchy as well, allows for objects, often called nodes, to be made out of other nodes recursively to create complex scenes. This dependent nodes, called children, can inherit characteristics fom their parents as well, like transformation and style. Due to the growing demand on the media, [glTF](https://github.com/KhronosGroup/glTF) was created to provide a standardized tree-like format, in a very generalized manner, and in an excellently simple way to implement. It can either contain a Json structure only (`.glTF`), or have a binary buffer as well to store more complex information too (`.glb`). This format has also become so popular due to its extensibility, as extensions can be easily implemented without breaking the original philosophy. Formats for VR have already been implemented in the past, like the [OMI group extensions](https://github.com/omigroup/gltf-extensions/tree/main), or the [VRM format](https://github.com/vrm-c/UniVRM).

## Features

The Isle Tree Format (ITF) is a [glTF 2.0](https://github.com/KhronosGroup/glTF/tree/main/specification/2.0) extension set which adds common video game features to the scene tree.

### Common

* Static collision
* Rigid body physics
* Soft body physics
* Bone chain physics
* Joints and constraints
* Triggers
* Buttons
* Pickups
* Seats
* Audio emitters
* Global audio emitters
* Shader materials
* Video players
* Mirrors
* Canvases
* State machines
* Scripting

### Worlds

* Skyboxes
* Post-processing
* Physics environment
* Baked lighting
* Isle rules

### Avatars

* Humanoid rigging
* IK tracker links
* Facial tracking and expression
* Eye position
* Voice position
* Control menu

### UI

> TODO: Design UI elements and styling.

## Compatibility

As it was mentioned earlier, other organizations have already implemented suggestions with similar purposes than ours, hence, most of them are compatible with the Tree Format. Besides all the [ratified Khronos extensions](https://github.com/KhronosGroup/glTF/tree/main/extensions#ratified-khronos-extensions-for-gltf-20), ITF compatible extensions are:

> TODO: Check out potentially compatible extensions, for now, see the [glTF 2.0 extension registry](https://github.com/KhronosGroup/glTF/tree/main/extensions) to have a reference.

## Credits

Thank you to all members in the [Khronos group](https://www.khronos.org/) for maintaining the glTF project, alongside other tens of open source projects for us, indie developers and communities, to use. We would not be able to do this without you.
