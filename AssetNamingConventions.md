Everything is typed in English.

Most assets are prefixed with an acronym representing the asset type, followed by an underscore.

`[AssetTypePrefix]_[AssetName]_[Descriptor]_[OptionalVariantLetterOrNumber]`

* `AssetTypePrefix`identifies the type of Asset, refer to the table below for details.
* `AssetName` is the Asset's name.
* `Descriptor` provides additional context for the Asset, to help identify how it is used. For example, whether a texture is a normal map or an opacity map.
* `OptionalVariantLetterOrNumber` is optionally used to differentiate between multiple versions or variations of an asset.

------
### Asset Prefixes

This list is not exhaustive, as new features can require new Asset types. If you are using an Asset type not listed, use the existing list as a guideline for your naming convention for that Asset.

Examples based on the contents in the table below:

* `M_Collectable`
* `T_Collectable_Normal`

------
### Base Asset Name
All assets should have a _Base Asset Name_. A Base Asset Name represents a logical grouping of related assets. Any asset that is part of this logical group
should follow the standard of  `Prefix_BaseAssetName_Variant_Suffix`.

Keeping the pattern `Prefix_BaseAssetName_Variant_Suffix` in mind and using common sense is generally enough to ensure good asset names. Here are some detailed rules regarding each element.

`Prefix` and `Suffix` are to be determined by the asset type through the following [Asset Name Modifier](#asset-name-modifiers) tables.

`BaseAssetName` should be determined by short and easily recognizable name related to the context of this group of assets. For example, if you had a character named Calvin, all of Calvin's assets would have the `BaseAssetName` of `Calvin`.

For unique and specific variations of assets, `Variant` is either a short and easily recognizable name that represents logical grouping of assets that are a subset of an asset's base name. For example, if Calvin had multiple skins these skins should still use `Calvin` as the `BaseAssetName` but include a recognizable `Variant`. An 'Evil' skin would be referred to as `Calvin_Evil` and a 'Retro' skin would be referred to as `Calvin_Retro`.

For unique but generic variations of assets, `Variant` is a two digit number starting at `01`. For example, if you have an environment artist generating nondescript rocks, they would be named `Rock_01`, `Rock_02`, `Rock_03`, etc. Except for rare exceptions, you should never require a three-digit variant number. If you have more than 100 assets, you should consider organizing them with different base names or using multiple variant names.

Depending on how your asset variants are made, you can chain variant names together. For example, if you are creating flooring assets for an Arch Viz project you should use the base name `Flooring` with chained variants such as `Flooring_Marble_01`, `Flooring_Maple_01`, `Flooring_Tile_Squares_01`.

#### Examples

##### Character

| Asset Type               | Asset Name   |
| ------------------------ | ------------ |
| Skeletal Mesh            | SK_Calvin       |
| Material                 | M_Calvin        |
| Texture (Diffuse/Albedo) | T_Calvin_D      |
| Texture (Normal)         | T_Calvin_N      |
| Texture (Evil_Diffuse)   | T_Calvin_Evil_D |

##### Prop

| Asset Type               | Asset Name   |
| ------------------------ | ------------ |
| Static Mesh (01)         | SM_Rock_01   |
| Static Mesh (02)         | SM_Rock_02   |
| Static Mesh (03)         | SM_Rock_03   |
| Material                 | M_Rock       |
| Material Instance (Snow) | MI_Rock_Snow |

------
### Asset Name Modifiers

When naming an asset use these tables to determine the prefix and suffix to use with an asset's [Base Asset Name](#base-asset-name).

- [Most Common Prefixes and Suffixes](#most-common-prefixes-and-suffixes)
  - [FBX](#3d-models-fbx-files)
  - [3ds](#3d-models-3ds-max-files)
- [Animations](#animations)
- [Artificial Intelligence](#artificial-intelligence)
- [Prefabs](#prefabs)
- [materials](#materials)
- [Textures](#textures)
  - [Texture Packing](#texture-packing)
- [Miscellaneous](#miscellaneous)
- [Physics](#physics)
- [Audio](#audio)
- [User Interface](#user-interface)
- [Effects](#effects)

#### Most Common Prefixes and Suffixes

| Asset Type              | Prefix     | Suffix     | Notes                                                                                     |
| ----------------------- | ---------- | ---------- |-------------------------------------------------------------------------------------------|
| Level / Scene           |  *          |            | Should be in a folder called Scenes. e.g. `Scenes/ArtTest.unity` |
| Level (Persistent)      |            | _P         |                                                                                           |
| Level (Audio)           |            | _Audio     |                                                                                           |
| Level (Lighting)        |            | _Lighting  |                                                                                           |
| Level (Geometry)        |            | _Geo       |                                                                                           |
| Level (Gameplay)        |            | _Gameplay  |                                                                                           |
| Prefab                  |        |            |                                                                                           |
| Material                | M_         |            |                                                                                           |
| Static Mesh             | SM_       |            |                                                                                           |
| Skeletal Mesh           | SK_       |            |                                                                                           |
| Texture                 | T_         | _?         | See [Textures](#textures)                                                             |
| Particle System         | PS_       |            |                                                                                           |

#### 3D Models FBX Files

PascalCase

| Asset Type    | Prefix | Suffix | Notes |
| ------------- | ------ | ------ | ----- |
| Characters    | CH_    |        |       |
| Vehicles      | VH_    |        |       |
| Weapons       | WP_    |        |       |
| Static Mesh   | SM_    |        |       |
| Skeletal Mesh | SK_    |        |       |
| Skeleton      | SKEL_  |        |       |
| Rig           | RIG_   |        |       |

#### 3D Models 3ds Max Files

All meshes in 3ds Max are lowercase to differentiate them from their FBX exports.

| Asset Type    | Prefix | Suffix      | Notes                                   |
| ------------- | ------ | ----------- | --------------------------------------- |
| Mesh          |        | _mesh_lod0* | Only use LOD suffix if model uses LOD's |
| Mesh Collider |        | _collider   |                                         |

#### Animations
| Asset Type           | Prefix | Suffix | Notes |
| -------------------- | ------ | ------ | ----- |
| Animation Clip       | A_     |        |       |
| Animation Controller | AC_    |        |       |
| Avatar Mask          | AM_    |        |       |
| Morph Target         | MT_    |        |       |

#### Artificial Intelligence

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| AI Controller           | AIC_     |            |                                  |
| Behavior Tree           | BT_      |            |                                  |
| Blackboard              | BB_       |            |                                  |
| Decorator               | BTDecorator_ |          |                                  |
| Service                 | BTService_ |            |                                  |
| Task                    | BTTask_  |            |                                  |
| Environment Query       | EQS_     |            |                                  |
| EnvQueryContext         | EQS_     | Context    |                                  |

#### Prefabs

| Asset Type              | Prefix     | Suffix     | Notes |
| ----------------------- | ---------- | ---------- |-------|
| Prefab         |        |            |       |
| Prefab Instance         | I       |            |       |
| Scriptable Object       |     |        |       |

#### Materials
| Asset Type        | Prefix | Suffix | Notes |
| ----------------- | ------ | ------ | ----- |
| Material          | M_     |        |       |
| Material Instance | MI_    |        |       |
| Physical Material | PM_    |        |       |

#### Textures
| Asset Type              | Prefix     | Suffix     | Notes                          |
| ----------------------- | ---------- | ---------- |--------------------------------|
| Texture                 | T_         |            |                                |
| Texture (Diffuse/Albedo/Base Color)| T_ | _D      |                                |
| Texture (Normal)        | T_         | _N         |                                |
| Texture (Metallic)        | T_         | _MT         |                                |
| Texture (Height)        | T_         | _H         |                                |
| Texture (Roughness)     | T_         | _R         |                                |
| Texture (Alpha/Opacity) | T_         | _A         |                                |
| Texture (Ambient Occlusion) | T_     | _AO      |                                |
| Texture (Bump)          | T_         | _B         |                                |
| Texture (Emissive)      | T_         | _E         |                                |
| Texture (Mask)          | T_         | _M         |                                |
| Texture (Specular)      | T_         | _S         |                                |
| Texture (Packed)        | T_         | _*         | See notes below about packing  |
| Texture Cube            | TC_       |            |                                |
| Media Texture           | MT_       |            |                                |
| Render Target           | RT_       |            |                                |
| Cube Render Target      | RTC_     |            |                                |
| Texture Light Profile   | TLP_     |            |                                |

##### Texture Packing
It is common practice to pack multiple layers of texture data into one texture. An example of this is packing Emissive, Roughness, Ambient Occlusion together as the Red, Green, and Blue channels of a texture respectively. To determine the suffix, simply stack the given suffix letters from above together, e.g. `_ERO`.

> It is generally acceptable to include an Alpha/Opacity layer in your Diffuse/Albedo's alpha channel and as this is common practice, adding `A` to the `_D` suffix is optional.

Packing 4 channels of data into a texture (RGBA) is not recommended except for an Alpha/Opacity mask in the Diffuse/Albedo's alpha channel as a texture with an alpha channel incurs more overhead than one without.

#### Miscellaneous

| Asset Type                      | Prefix | Suffix | Notes |
| ------------------------------- | ------ | ------ | ----- |
| Universal Render Pipeline Asset | URP_   |        |       |
| Post Process Volume Profile     | PP_    |        |       |
| User Interface                  | UI_    |        |       |

#### Physics

| Asset Type        | Prefix | Suffix | Notes |
| ----------------- | ------ | ------ | ----- |
| Physical Material | PM_    |        |       |

#### Audio

| Asset Type     | Prefix | Suffix | Notes                                                        |
| -------------- | ------ | ------ | ------------------------------------------------------------ |
| Audio Clip     | A_     |        |                                                              |
| Audio Mixer    | MIX_   |        |                                                              |
| Dialogue Voice | DV_    |        |                                                              |
| Audio Class    |        |        | No prefix or suffix. Should be put in a folder called AudioClasses |

#### User Interface
| Asset Type       | Prefix | Suffix | Notes |
| ---------------- | ------ |--------| ----- |
| Font             | Font_  |        |       |
| Texture (Sprite) | T_     |        |       |

#### Effects
| Asset Type      | Prefix | Suffix | Notes |
| --------------- | ------ | ------ | ----- |
| Particle System | PS_    |        |       |
