# Quick Start

Get a LEADR account and create your first leaderboard in under 5 minutes. By the end of this guide, you'll have a working leaderboard ready for your game.

## Download the CLI

Install the LEADR command-line tool:

```bash
curl -sSL https://raw.githubusercontent.com/LEADR-official/leadr-cli-releases/main/install.sh | bash
```

For manual installation, download binaries from the [Releases page](https://github.com/LEADR-official/leadr-cli-releases/releases).

Verify the installation:

```bash
leadr --version
```

## Create an Account

Register for a free LEADR account:

```bash
leadr register
```

This interactive command prompts you for your email, display name, and studio or team name. Your API key is automatically saved to your local configuration.

!!! warning "Keep Your API Key Secret"

    Your API key is for your personally to access LEADR admin features for your account.

    NEVER put any API key directly in your code - use the CLI, environment variables, or other secure methods.

    We'll never ask you for it, and you shouldn't give it to strangers on the internet.

    Keep it secret. Keep it (your game) safe.


See [CLI Getting Started](cli/getting-started.md) for more details on account setup and verification.

## Create a Leaderboard

First, create a game:

```bash
leadr game create --name "My Game"
```

Note the game UUID from the output, then create a leaderboard:

```bash
leadr board create --game-id <game-uuid> --name "High Scores" --slug highscores
```

You can reference this leaderboard in your game's code using the returned UUID or `short_code`.

See [CLI Getting Started](cli/getting-started.md) for more leaderboard options like sort direction, score units, and score keep strategies.

## Add LEADR to Your Game

Native SDKs for **Godot**, **Unity**, and more game engines are in development. These will provide APIs that feel natural in your development environment.

Check the [SDKs page](sdks/index.md) for the latest availability, or [join the waitlist](https://docs.google.com/forms/d/e/1FAIpQLSeXN6UtTCgyoO7n07ANeQ0XBsgkz1rB9i7ZBGjXgSN_Er7Ebg/viewform?usp=sharing&ouid=101801924018683932467) for early access.

Need to integrate now? The [HTTP API](api/client-api.md) is available for direct integration from any platform.

## Next Steps

- **[CLI Getting Started](cli/getting-started.md)** - Detailed CLI walkthrough with all options
- **[Features](features.md)** - Explore what LEADR can do
- **[SDKs](sdks/index.md)** - Game engine integrations
- **[Discord](https://discord.gg/RMUukcAxSZ)** - Get help from the community
