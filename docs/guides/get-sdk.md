# Get the SDK

Connect your game to LEADR using an SDK or the REST API. SDKs handle authentication, sessions, and token management automatically so you can focus on your game.

## Prerequisites

- [Download and install the LEADR app](./install.md)
- A LEADR account:
  - [Register](./register.md)
  - [Join a team](./join.md)
- [Create a game](./create-game.md)
- [Create a board](./create-board.md)

## Choose Your Platform

=== "Godot"

    The LEADR Godot SDK provides a native GDScript plugin for Godot 4.x.

    **Install from the GitHub repository:**

    1. Open the latest release of the LEADR Godot SDK on GitHub: [https://github.com/LEADR-official/leadr-sdk-godot/releases](https://github.com/LEADR-official/leadr-sdk-godot/releases)
    2. Download the `.zip` containing the SDK code and unzip to a temporary location (or clone the repo if you prefer)
    3. Copy the entire `leadr` directory from the unzipped `addons` directory into the `addons` directory of your Godot project
    4. Open your Godot project

    [Full Godot SDK documentation](../sdks/godot/index.md){ .md-button }

=== "Unity"

    The LEADR Unity SDK provides a C# package for Unity 2021.3+.

    **Install from GitHub via Package Manager:**

    1. Open **Window > Package Manager**
    2. Click **+** > **Add package from git URL**
    3. Enter: `https://github.com/LEADR-Official/leadr-sdk-unity.git?path=Packages/com.leadr.sd`

    [Full Unity SDK documentation](../sdks/unity/index.md){ .md-button }

=== "Other / REST API"

    Using a different engine, language, or custom setup? The REST API works from anything that speaks HTTP.

    [Client API Reference](../api/client-api.md){ .md-button }

For the full list of available and planned SDKs, see the [SDKs overview](../sdks/index.md).

## SDK vs REST API

| Feature | SDK | REST API |
|---------|-----|----------|
| Authentication | Automatic | Manual |
| Session management | Automatic | Manual |
| Token refresh | Automatic | Manual |
| Nonce handling | Automatic | Manual |
| Platform-specific | Yes | No |

**Use an SDK** if one exists for your engine. It handles all the authentication complexity automatically.

**Use the REST API** if you're using an unsupported engine, building a custom integration, or need full control over the HTTP layer.

## What's Next

- **[Use LEADR in your game](./use-sdk.md)** - Integrate the LEADR SDK into your game code and scenes

## Need Help?

If you get stuck at any point, the LEADR team and community is always happy to help on the [LEADR Discord](https://discord.gg/RMUukcAxSZ).
