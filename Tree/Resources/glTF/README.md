# glTF files

## Introduction

Due to the growing demand on the media, [glTF](https://github.com/KhronosGroup/glTF) was created to provide a standardized tree-like format, in a very generalized manner, and in an excellently simple way to implement. It can either contain a Json structure only (`.glTF`), or have a binary buffer as well to store more complex information too (`.glb`). This format has also become so popular due to its extensibility, as extensions can be easily implemented without breaking the original philosophy. Formats for VR have already been implemented in the past, like the [OMI group extensions](https://github.com/omigroup/gltf-extensions/tree/main), or the [VRM format](https://github.com/vrm-c/UniVRM).

Though glTF was at first considered as a valid option to be the ITF format, their philosophy only provide a workflow valid for static scenes. In the metaverse, though, scenes are very dynamic, and will alter, create, and delete nodes, and for that reason, it's better to use glTF as resources instead.

## Credits

Thank you to all members in the [Khronos group](https://www.khronos.org/) for maintaining the glTF project, alongside other tens of open source projects for us, indie developers and communities, to use. We would not be able to do this without you.

## Deprecated

> [!WARNING]
> Information beyond this point is being kept to act as a reference for future additions to the documentation, and it's deprecated. All classes need to be altered will be done through scene overrides inside the ITF file.

## Status

* Deprecated, purple 🟣: The extension is unsupported, no longer maintained, and will soon be removed completely from the ecosystem.

## Project extensions

* 🟣 ISLE_animation_controller
* 🟣 [ISLE_canvas](./Extensions/ISLE_canvas/)
* 🟣 ISLE_control_menu
* 🟣 [ISLE_light_shadows](./Extensions/ISLE_light_shadows/)
* 🟣 [ISLE_mirror](./Extensions/ISLE_mirror/)
* 🟣 ISLE_portal
* 🟣 ISLE_script
* 🟣 ISLE_shader_material
* 🟣 ISLE_soft_body
* 🟣 ISLE_video_display

## Third-party extensions

### Khronos Group

* [KHR_animation_pointer](https://github.com/KhronosGroup/glTF/tree/main/extensions/2.0/Khronos/KHR_animation_pointer)
* [KHR_draco_mesh_compression](https://github.com/KhronosGroup/glTF/tree/main/extensions/2.0/Khronos/KHR_draco_mesh_compression)
* [KHR_lights_punctual](https://github.com/KhronosGroup/glTF/tree/main/extensions/2.0/Khronos/KHR_lights_punctual)
* [KHR_materials_anisotropy](https://github.com/KhronosGroup/glTF/tree/main/extensions/2.0/Khronos/KHR_materials_anisotropy)
* [KHR_materials_clearcoat](https://github.com/KhronosGroup/glTF/tree/main/extensions/2.0/Khronos/KHR_materials_clearcoat)
* [KHR_materials_dispersion](https://github.com/KhronosGroup/glTF/tree/main/extensions/2.0/Khronos/KHR_materials_dispersion)
* [KHR_materials_emissive_strength](https://github.com/KhronosGroup/glTF/tree/main/extensions/2.0/Khronos/KHR_materials_emissive_strength)
* [KHR_materials_ior](https://github.com/KhronosGroup/glTF/tree/main/extensions/2.0/Khronos/KHR_materials_ior)
* [KHR_materials_iridescence](https://github.com/KhronosGroup/glTF/tree/main/extensions/2.0/Khronos/KHR_materials_iridescence)
* [KHR_materials_sheen](https://github.com/KhronosGroup/glTF/tree/main/extensions/2.0/Khronos/KHR_materials_sheen)
* [KHR_materials_specular](https://github.com/KhronosGroup/glTF/tree/main/extensions/2.0/Khronos/KHR_materials_specular)
* [KHR_materials_transmission](https://github.com/KhronosGroup/glTF/tree/main/extensions/2.0/Khronos/KHR_materials_transmission)
* [KHR_materials_unlit](https://github.com/KhronosGroup/glTF/tree/main/extensions/2.0/Khronos/KHR_materials_unlit)
* [KHR_materials_variants](https://github.com/KhronosGroup/glTF/tree/main/extensions/2.0/Khronos/KHR_materials_variants)
* [KHR_materials_volume](https://github.com/KhronosGroup/glTF/tree/main/extensions/2.0/Khronos/KHR_materials_volume)
* [KHR_mesh_quantization](https://github.com/KhronosGroup/glTF/tree/main/extensions/2.0/Khronos/KHR_mesh_quantization)
* [KHR_texture_basisu](https://github.com/KhronosGroup/glTF/tree/main/extensions/2.0/Khronos/KHR_texture_basisu)
* [KHR_texture_transform](https://github.com/KhronosGroup/glTF/tree/main/extensions/2.0/Khronos/KHR_texture_transform)
* [KHR_xmp_json_ld](https://github.com/KhronosGroup/glTF/tree/main/extensions/2.0/Khronos/KHR_xmp_json_ld)

### Open Metaverse Interoperability Group (OMI)

* [KHR_audio_emitter](https://github.com/omigroup/gltf-extensions/tree/main/extensions/2.0/KHR_audio_emitter) (will be officially supported by the Khronos group soon)
* [OMI_link](https://github.com/omigroup/gltf-extensions/tree/main/extensions/2.0/OMI_link)
* [OMI_physics_body](https://github.com/omigroup/gltf-extensions/tree/main/extensions/2.0/OMI_physics_body)
* [OMI_physics_joint](https://github.com/omigroup/gltf-extensions/tree/main/extensions/2.0/OMI_physics_joint)
* [OMI_physics_shape](https://github.com/omigroup/gltf-extensions/tree/main/extensions/2.0/OMI_physics_shape)
* [OMI_seat](https://github.com/omigroup/gltf-extensions/tree/main/extensions/2.0/OMI_seat)
* [OMI_spawn_point](https://github.com/omigroup/gltf-extensions/tree/main/extensions/2.0/OMI_spawn_point)


