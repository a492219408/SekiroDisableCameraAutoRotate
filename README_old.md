# SekiroDisableCameraAutoRotate DLL

This is a standalone DLL that disables camera auto-rotate on movement in Sekiro: Shadows Die Twice.

## Features

- **Disable camera auto rotate on movement**: Prevents the camera from automatically adjusting when the player moves.

## Build Instructions

### Using CMake

```bash
cd SekiroDisableCameraAutoRotate
cmake -S . -B build -G Ninja -DCMAKE_BUILD_TYPE=Release
cmake --build build
```

## Notes

- The DLL is designed for **x64** only (Sekiro is a 64-bit game)
- The camera pitch XY adjustment is disabled by default as it can cause issues with controller input
- If you use a mouse, you can uncomment the pitch XY code in `dllmain.cpp` and rebuild

## Credits

Based on the camera adjustment code from [SekiroFpsUnlockAndMore](https://github.com/uberhalit/SekiroFpsUnlockAndMore) by uberhalit.
