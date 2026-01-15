# SekiroDisableCameraAutoRotate

一个用于 **《只狼：影逝二度》(Sekiro: Shadows Die Twice)** 的 DLL Mod，用于禁用玩家移动时的相机自动旋转功能。

> **⚠️ 重要提示**：本 Mod 专为**鼠标操作**设计。如果使用手柄，可能会出现以下问题：摇杆操作没有平滑加速效果（摇杆轻拨即达到最大转动速度），以及存在一段死区。

## 描述

在《只狼》中，当玩家角色移动时，相机会自动调整角度，这对部分玩家来说可能会造成不适。本 Mod 禁用了该行为，让你可以完全手动控制相机。

### 功能

- 禁用相机俯仰角自动调整
- 禁用 Z 轴移动时的相机偏航角自动调整
- 禁用 XY 轴移动时的相机俯仰角自动调整
- 禁用 XY 轴移动时的相机偏航角自动调整

## 使用方法

本 Mod 通过 [ModEngine3 (me3)](https://github.com/garyttierney/me3) 加载。你也可以使用 [me3-manager](https://github.com/2Pz/me3-manager)，这是一个使用 me3 作为后端的图形界面工具。

### ModEngine3 配置示例

创建一个 `.me3` 配置文件，内容如下：

```toml
profileVersion = "v1"

[[supports]]
game = "sekiro"

[[natives]]
enabled = true
path = "SekiroDisableCameraAutoRotate.dll"  # 支持相对路径（相对于 .me3 文件所在目录）和绝对路径
```

将 `SekiroDisableCameraAutoRotate.dll` 放置在与 `.me3` 文件相同的目录下，或根据需要调整路径。

详细的配置说明请参阅 [ModEngine3 文档](https://me3.help/en/latest/)。

## 构建

### 环境要求

- CMake 3.20 或更高版本
- 以下工具链之一：
  - **Visual Studio 2022**（MSVC v143 或更高版本）
  - **MinGW-w64** 配合 Ninja

### 构建步骤

#### 方式一：Visual Studio 2022

```powershell
cmake -S . -B build -G "Visual Studio 17 2022" -A x64
cmake --build build --config Release
```

输出的 DLL 文件位于 `build/Release/SekiroDisableCameraAutoRotate.dll`。

#### 方式二：MinGW + Ninja

```powershell
cmake -S . -B build -G Ninja -DCMAKE_BUILD_TYPE=Release
cmake --build build
```

输出的 DLL 文件位于 `build/SekiroDisableCameraAutoRotate.dll`。

> **注意**：本项目仅支持 **64 位 (x64)** 构建，因为《只狼》是一款 64 位游戏。

## 致谢

本项目参考了 [SekiroFpsUnlockAndMore](https://github.com/uberhalit/SekiroFpsUnlockAndMore) 中的相机调整代码，作者为 **uberhalit**。特别感谢提供了修改所需的游戏数据模式。

## 许可证

详见 [LICENSE](LICENSE) 文件。
