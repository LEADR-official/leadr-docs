# Quick Start

Get your first leaderboard up and running in under 5 minutes. This guide walks you through each step, from installing the LEADR app to adding leaderboards to your game.

!!! tip "Need help along the way?"

    Each step below links to a detailed guide if you want to go deeper.

    If you get stuck at any point, the LEADR team and community is always happy to help on the [LEADR Discord](https://discord.gg/RMUukcAxSZ).

**The journey:**

1. [Install the LEADR App](#step-1-install-the-leadr-app)
2. [Register an account](#step-2-register-an-account)
3. [Create a game](#step-3-create-a-game)
4. [Create a board](#step-4-create-a-board)
5. [Add LEADR to your game](#step-5-add-leadr-to-your-game)

---

## Step 1: Install the LEADR App

The LEADR App is a terminal UI application that lets you manage your account, games, boards and more from your desktop.

=== "Windows"

    Download the latest version from [https://leadr.gg/download/windows](https://leadr.gg/download/windows) and double-click the `.exe` to install.

=== "macOS / Linux"

    ```bash
    curl -sSL https://leadr.gg/download/install.sh | bash
    ```

=== "Manual Install"

    Download binaries directly from the [Releases page](https://github.com/LEADR-official/leadr-releases/releases).

For troubleshooting and system requirements, see the [full install guide](guides/install.md).

## Step 2: Register an Account

Open the LEADR App and select **Register** from the main menu (or use the "r" keyboard shortcut).

First you'll input your email which we'll verify by sending you an email with a code.

Then input your display name and studio or team name.

![Registering a LEADR account](assets/images/register.gif)

Your API key is automatically generated and saved to your local configuration.

!!! warning "Keep your API key secret"

    Your API key grants admin access to your LEADR account. Never put it in your game code - game clients and SDKs use a separate API and a different authentication method.

    We'll never ask you for it, and you should never share it online or give it to anyone, even teammates.

    Keep it secret, keep it (your game) safe.

For more details, see the [registration guide](guides/register.md).

## Step 3: Create a Game

A game in LEADR groups all your boards, scores, and settings together. Create one for each game you ship.

In the LEADR App, navigate to **Games** ("g" keyboard shortcut), and then press "n" to add a new game.

You'll be prompted for a name and other optional information.

![Creating a game](assets/images/create-game.gif)

See the [create a game guide](guides/create-game.md) for advanced options.

## Step 4: Create a Board

Boards are the individual leaderboards your game can use. You can have as many boards as you like per game.

In the LEADR App, navigate to **Games > [your game] > Boards**, and then press "n" to add a new board.

Your board will need a name, a board type, sort direction (is higher or lower better?), and other configuration options.

![Creating a board](assets/images/create-board.gif)

!!! info "Boards can do a lot more"

     Fixed start & end dates, seasonal resets, counter boards, win-lose percentages, specific units, custom icons and more -- see the [Advanced Boards](guides/advanced-boards.md) and [Board Templates](./reference/board-templates.md) guides to explore what's possible.

For a full walkthrough, see the [create a board guide](guides/create-board.md).

## Step 5: Add LEADR to Your Game

Now your LEADR account is ready, you just need to connect your game.

Pick your engine or platform below to get started.

=== "Godot"

    Install the LEADR Godot SDK to submit scores and query boards using our native GDScript plugin asset. No raw HTTP needed.

    [Get started with the Godot SDK](sdks/godot/index.md){ .md-button }

=== "Unity"

    Import the LEADR Unity SDK to submit scores and query boards using our C# package. No raw HTTP needed.

    [Get started with the Unity SDK](sdks/unity/index.md){ .md-button }

=== "Other / REST API"

    Using a different engine, language, or custom setup? The REST API works from anything that speaks HTTP.

    [Client API Reference](api/client-api.md){ .md-button }

Looking for another engine? For a full list of available and planned SDKs, see the [SDKs overview](sdks/index.md).

## Next Steps

You've got a working leaderboard. Here's where to go from here:

- **[Invite Teammates](guides/invites.md)** - Add collaborators to your LEADR account
- **[Advanced Boards](guides/advanced-boards.md)** - Learn how to create boards for seasons, tournaments, win-lose percentages, play time, speedruns and more
- **[See All Features](features.md)** - Review scores, anti-cheat system, web views, and more
- **[Go-Live Checklist](guides/go-live-checklist.md)** - Everything to check before your game ships

!!! info "Join the community"

    Got questions, feedback, or just want to chat about game dev? Join the [LEADR Discord](https://discord.gg/RMUukcAxSZ). We'd love to hear what you're building.
