# Project Silicon


# **This is in no way, shape or form affiliated with Microsoft or Mojang studios!!**
A native Apple Silicon Minecraft client written from scratch in Swift and Metal.

Not a mod. Not a port. A voxel engine built specifically for Apple Silicon hardware that speaks the Minecraft Java Edition multiplayer protocol.

## Status

🚧 **Early development.** Auth pipeline complete, asset pipeline in progress.

## How It Works

Silicon Launcher does not contain any Minecraft code or assets. When you launch it for the first time, it authenticates with your Microsoft account, verifies your Minecraft: Java Edition license, then downloads your legally-owned assets directly from Mojang's own CDN, the same way the official launcher does. Those assets are then compiled into native Metal GPU formats and serialized in a form locked to your hardware, **they cannot be extracted or redistributed.** If you don't own Minecraft: Java Edition, the launcher won't start.

The voxel engine, renderer, protocol implementation, and all game logic are written from scratch in Swift and Metal with no Minecraft code involved.

## Goals

- Native arm64 binary — no Rosetta, no JVM, no abstraction layers
- Metal 3 renderer with Indirect Command Buffers and MetalFX upscaling
- Full Minecraft Java Edition multiplayer protocol support (1.21.x, newer versions may or may not come)
- Zero-copy chunk geometry via shared MTLHeap
- ProMotion display support

## Requirements

- Apple Silicon Mac (M1 or later)
- macOS 14 (Sonoma) or later
- Minecraft: Java Edition license (assets are not included or redistributed!!)

## Architecture

```
Game Logic (Swift)       ECS, world state, physics
Chunk System (Swift)     Generation, meshing, streaming  
Protocol Layer (Swift)   MC Java protocol 1.21.x
Metal Renderer           ICB, mesh shaders, MetalFX
Apple Silicon HW         UMA, P+E cores, Media Engine
```

## Building

Open `MCClient.xcodeproj` in Xcode 15 or later and build the `MCClient` target. Requires your own Azure app registration with Mojang API approval.

## Legal

**This project does not include, redistribute, or reverse-engineer any Minecraft assets or code. Users must own a valid Minecraft: Java Edition license. Minecraft is a trademark of Mojang Studios. And I repeat, this is in no way, shape or form affiliated with Microsoft or Mojang studios!**
