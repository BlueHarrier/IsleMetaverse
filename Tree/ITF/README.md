# ITF files

## Mandatory extensions

Many suggestions by other groups have already been made, and so, most of them are already supported 

## Project extensions

* ⚫ ISLE_animation_controller
* ⚫ ISLE_artifact
* ⚫ ISLE_avatar
* ⚫ ISLE_button
* 🔴 [ISLE_canvas](./Extensions/ISLE_canvas/)
* ⚫ ISLE_control_menu
* 🔴 [ISLE_light_shadows](./Extensions/ISLE_light_shadows/)
* 🔴 [ISLE_mirror](./Extensions/ISLE_mirror/)
* ⚫ ISLE_pickup
* ⚫ ISLE_portal
* ⚫ ISLE_script
* ⚫ ISLE_shader_material
* ⚫ ISLE_soft_body
* ⚫ ISLE_video_display
* ⚫ ISLE_world

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

### VRM Consortium

* [VRMC_materials_hdr_emissiveMultiplier](https://github.com/vrm-c/vrm-specification/tree/master/specification/VRMC_materials_hdr_emissiveMultiplier-1.0)
* [VRMC_materials_mtoon](https://github.com/vrm-c/vrm-specification/tree/master/specification/VRMC_materials_mtoon-1.0)

> Most VRM Consortium extensions do not match the glTF 2.0 design pattern, and so, they cannot be used in ITF.

## Scene usage

glTF 2.0 files can contain different scenes. ITF contemplates that feature and integrates it so one of these files can have multiple scenes, each scene being one different resource. The goal is to give content creators the ability to make libraries which hold different content and content types within. This can also help create variants of one asset types, allowing for better optimization as less resources can be stored at a time, practice that is very common to do for avatars.

## File extension

Any Isle Tree Format needs to be identified by a different extension, depending on what glTF 2.0 file format uses. The default format to use is `.glb` (binary), which will use the extension `.itf`, though, it's also possible to use the ASCII format, `.gltf`, in which case, the extension of the file will be `.jitf` (Json Isle Tree Format).
