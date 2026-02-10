# SDKs

LEADR's SDKs help you quickly and easily get leaderboards in your game using tools and code you're familiar with. They're the best way to integrate all the features of LEADR. Whether you're working in C# for Unity or GDScript for Godot, we've got you covered, with more SDKs for other engines and languages on the way.

!!! info "What's an SDK?"

    Software Development Kits (SDKs) are native libraries for your game engine or programming language that make integrating LEADR straightforward. Instead of making raw HTTP requests, SDKs provide friendly functions that feel natural in your development environment.

    If you're using plugins, libraries or code assets that someone else made inside your game engine, you already know how to use a LEADR SDK.

## Getting Started

- **[Quick Start Guide](../quick-start.md)** - Integration walkthrough

## Supported Game Engines

### Godot

Native GDScript plugin for Godot Engine. Install the plugin, configure your game ID, and submit scores with a few lines of GDScript.

[Get Started with Godot](godot/index.md){ .md-button .md-button--primary }
[View Source](https://github.com/LEADR-official/leadr-sdk-godot){ .md-button }

### Unity

Native C# package for Unity Engine. Import the package, configure your game ID, and submit scores with a few lines of C#.

[Get Started with Unity](unity/index.md){ .md-button .md-button--primary }
[View Source](https://github.com/LEADR-official/leadr-sdk-unity/){ .md-button }

### C# (.NET)

Standalone .NET library for custom C# projects. Coming soon.

### REST API

Using a different engine, language, or custom setup? The REST API works from anything that speaks HTTP. Authenticate your game client, submit scores, and query leaderboards directly.

[API Quick Reference](../api/client-api.md){ .md-button .md-button--primary }
[Authentication Guide](../api/client-auth.md){ .md-button }

## Planned SDKs

We're building native SDKs for the most popular game engines and platforms. SDKs are being developed in priority order based on indie game developer usage:

- **Unreal Engine** - C++ SDK for Unreal Engine
- **GameMaker** - GML SDK for GameMaker
- **Lua/Defold/LOVE2D** - For games written in Lua or Lua-based game engines like Defold or LOVE2D
- **JavaScript/TypeScript** - For web games and Node.js backends
- **Python** - For game servers and tools
- **C++** - Standalone C++ library for custom engines

Want to see an SDK for your platform? Let us know on [Discord](https://discord.gg/RMUukcAxSZ) or [Reddit](https://www.reddit.com/r/LEADR/).

## Advanced

- **[Client Authentication](../api/client-auth.md)** - A deep dive on how LEADR's secure client authentication works
