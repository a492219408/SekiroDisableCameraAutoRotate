# SekiroDisableCameraAutoRotate

[中文文档](README_zh.md)

A DLL mod for **Sekiro: Shadows Die Twice** that disables the automatic camera rotation when the player moves.

> **⚠️ Important**: This mod is designed for **mouse input**. If you use a controller, you may experience issues such as lack of smooth acceleration (the camera reaches max speed immediately when the stick is tilted) and a dead zone in stick input.

## Description

In Sekiro, the camera automatically adjusts its angle when the player character moves, which can be disorienting for some players. This mod disables that behavior, giving you full manual control over the camera.

### Features

- Disables automatic camera pitch adjustment
- Disables automatic camera yaw adjustment on Z-axis movement
- Disables automatic camera pitch adjustment on XY-axis movement
- Disables automatic camera yaw adjustment on XY-axis movement

## Usage

This mod is designed to be loaded via [ModEngine3 (me3)](https://github.com/garyttierney/me3). You can also use [me3-manager](https://github.com/2Pz/me3-manager), a GUI frontend that uses me3 as its backend.

### ModEngine3 Configuration Example

Create a `.me3` configuration file with the following content:

```toml
profileVersion = "v1"

[[supports]]
game = "sekiro"

[[natives]]
enabled = true
path = "SekiroDisableCameraAutoRotate.dll"  # Supports relative path (relative to the .me3 file) or absolute path
```

Place the `SekiroDisableCameraAutoRotate.dll` in the same directory as your `.me3` file, or adjust the path accordingly.

For detailed configuration instructions, please refer to the [ModEngine3 Documentation](https://me3.help/en/latest/).

## Building

### Requirements

- CMake 3.20 or higher
- One of the following toolchains:
  - **Visual Studio 2022** (MSVC v143 or later)
  - **MinGW-w64** with Ninja

### Build Instructions

#### Option 1: Visual Studio 2022

```powershell
cmake -S . -B build -G "Visual Studio 17 2022" -A x64
cmake --build build --config Release
```

The output DLL will be located at `build/Release/SekiroDisableCameraAutoRotate.dll`.

#### Option 2: MinGW + Ninja

```powershell
cmake -S . -B build -G Ninja -DCMAKE_BUILD_TYPE=Release
cmake --build build
```

The output DLL will be located at `build/SekiroDisableCameraAutoRotate.dll`.

> **Note**: This project only supports **64-bit (x64)** builds, as Sekiro is a 64-bit game.

## Credits

This project is based on the camera adjustment code from [SekiroFpsUnlockAndMore](https://github.com/uberhalit/SekiroFpsUnlockAndMore) by **uberhalit**. Special thanks for providing the game data patterns needed for the modifications.

## License

See [LICENSE](LICENSE) for details.
