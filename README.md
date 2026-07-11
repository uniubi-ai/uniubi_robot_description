# Uniubi Robot Description

Language: English | [中文](README.zh-CN.md)

This repository contains open robot description assets for Uniubi robots, including URDF, MuJoCo XML, USD, and mesh files.

## Robots

The current robot model is `cyvet`.

```text
robots/
└── cyvet/
    ├── meshes/
    ├── urdf/
    ├── usd/
    └── xml/
```

## Directory Layout

Each robot model should use a lowercase directory name under `robots/`.

```text
robots/<robot_model>/
├── meshes/    # Mesh assets, such as STL files
├── urdf/      # URDF robot descriptions
├── usd/       # USD robot descriptions
└── xml/       # MuJoCo XML and scene files
```

Naming should stay lowercase for robot directories and primary robot description files.

## Cyvet Assets

The `cyvet` model currently provides:

- `robots/cyvet/urdf/cyvet.urdf`
- `robots/cyvet/xml/cyvet.xml`
- `robots/cyvet/xml/scene_terrain.xml`
- `robots/cyvet/usd/cyvet.usd`
- `robots/cyvet/meshes/*.stl`

The URDF mesh paths are relative to the URDF file:

```xml
filename="../meshes/base_link.stl"
```

The MuJoCo XML mesh paths are relative to the XML file:

```xml
<mesh name="BASE_LINK.STL" file="../meshes/base_link.stl" />
```

The terrain scene includes the robot XML:

```xml
<include file="cyvet.xml"/>
```

The terrain scene also uses local heightfield images stored in `robots/cyvet/xml/`:

- `height_field.png`
- `unitree_hfield.png`

## USD

`robots/cyvet/usd/cyvet.usd` is a flattened single-file USD asset. Its default prim is:

```text
/cyvet
```

This file has no external USD sublayer dependency. Some tools may still report an unresolved `OmniPBR.mdl` material dependency, which comes from the original Omniverse material setup.

## Conventions

- Use lowercase robot model directory names.
- Use lowercase primary asset file names, such as `cyvet.urdf`, `cyvet.xml`, and `cyvet.usd`.
- Keep mesh files in `meshes/`.
- Prefer relative paths from the description file to its referenced assets.
- Keep simulator-specific scene files under `xml/` when they are MuJoCo XML files.

## License

Original UniUbi description files and documentation in this repository are licensed under the Apache License 2.0. Robot model assets, meshes, textures, simulator assets, and third-party assets may be subject to separate terms. See [LICENSE](LICENSE), [NOTICE](NOTICE), and [ASSET_NOTICES.md](ASSET_NOTICES.md).
