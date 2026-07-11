# Uniubi Robot Description

语言：[English](README.md) | 中文

这个仓库用于存放 Uniubi 机器人的开源描述资产，包括 URDF、MuJoCo XML、USD 和 mesh 文件。

## 机器人型号

当前机器人型号是 `cyvet`。

```text
robots/
└── cyvet/
    ├── meshes/
    ├── urdf/
    ├── usd/
    └── xml/
```

## 目录结构

每个机器人型号都放在 `robots/` 下，型号目录统一使用小写名称。

```text
robots/<robot_model>/
├── meshes/    # Mesh 资产，例如 STL 文件
├── urdf/      # URDF 机器人描述文件
├── usd/       # USD 机器人描述文件
└── xml/       # MuJoCo XML 和场景文件
```

机器人目录名和主要描述文件名都保持小写。

## Cyvet 资产

`cyvet` 目前包含以下资产：

- `robots/cyvet/urdf/cyvet.urdf`
- `robots/cyvet/xml/cyvet.xml`
- `robots/cyvet/xml/scene_terrain.xml`
- `robots/cyvet/usd/cyvet.usd`
- `robots/cyvet/meshes/*.stl`

URDF 中的 mesh 路径相对于 URDF 文件：

```xml
filename="../meshes/base_link.stl"
```

MuJoCo XML 中的 mesh 路径相对于 XML 文件：

```xml
<mesh name="BASE_LINK.STL" file="../meshes/base_link.stl" />
```

地形场景文件会包含机器人 XML：

```xml
<include file="cyvet.xml"/>
```

地形场景还依赖两个 heightfield 图片，图片放在 `robots/cyvet/xml/` 下：

- `height_field.png`
- `unitree_hfield.png`

## USD

`robots/cyvet/usd/cyvet.usd` 是已经 flatten 的单文件 USD 资产。它的 default prim 是：

```text
/cyvet
```

这个文件没有外部 USD sublayer 依赖。部分工具可能仍会提示 `OmniPBR.mdl` 材质依赖未解析，这是原始 Omniverse 材质设置带来的引用。

## 约定

- 机器人型号目录使用小写名称。
- 主要资产文件名使用小写，例如 `cyvet.urdf`、`cyvet.xml`、`cyvet.usd`。
- mesh 文件统一放在 `meshes/` 目录。
- 资产引用优先使用相对于描述文件的相对路径。
- MuJoCo XML 的机器人文件和场景文件都放在 `xml/` 目录。

## 许可证

本仓库中的 UniUbi 原创描述文件和文档使用 Apache License 2.0。机器人模型资产、mesh、贴图、仿真资产和第三方资产可能适用单独条款。详见 [LICENSE](LICENSE)、[NOTICE](NOTICE) 和 [ASSET_NOTICES.md](ASSET_NOTICES.md)。
