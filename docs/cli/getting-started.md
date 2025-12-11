# Getting Started

This guide walks you through installing the LEADR CLI and setting up your first game and leaderboard.

## Installation

### Quick Install (macOS/Linux)

```bash
curl -sSL https://raw.githubusercontent.com/LEADR-official/leadr-cli-releases/main/install.sh | bash
```

### Manual Download

Download binaries from the [Releases page](https://github.com/LEADR-official/leadr-cli-releases/releases).

### Verify Installation

After installation, verify the CLI is working:

```bash
leadr --version
```

## Create Your Account

Register a new LEADR account using the interactive registration command:

```bash
leadr register
```

This will prompt you for:

- **Email address** - Your account email
- **Display name** - Your name as shown in the dashboard
- **Account name** - Your organization or studio name
- **Account slug** - A URL-friendly identifier (e.g., `my-studio`)

After registration, an API key will be generated and automatically saved to your local configuration.

## Verify Your Setup

Check that your API key is configured correctly:

```bash
leadr auth admin status
```

View your account information:

```bash
leadr me
```

## Create Your First Game

Create a game to start adding leaderboards:

```bash
leadr game create --name "My Awesome Game"
```

The command outputs the game details including its UUID. Save this ID for the next steps.

List your games to see all registered games:

```bash
leadr game list
```

## Create Your First Leaderboard

Create a leaderboard for your game:

```bash
leadr board create \
  --game-id <game-uuid> \
  --name "High Scores" \
  --short-code highscores \
  --sort-direction desc
```

**Options explained:**

- `--game-id` - The UUID of your game
- `--name` - Display name for the leaderboard
- `--short-code` - A unique identifier used in your game's API calls
- `--sort-direction` - `desc` for highest-first (default), `asc` for lowest-first

### Additional Leaderboard Options

```bash
leadr board create \
  --game-id <game-uuid> \
  --name "Speedrun Times" \
  --short-code speedrun \
  --sort-direction asc \
  --unit "seconds" \
  --keep-strategy best
```

- `--unit` - Label for the score value (e.g., "points", "seconds", "kills")
- `--keep-strategy` - How to handle multiple submissions from the same player:
  - `all` - Keep all scores (default)
  - `best` - Keep only the best score
  - `first` - Keep only the first score
  - `last` - Keep only the latest score

## Submit a Test Score

Submit a score to your leaderboard:

```bash
leadr score create \
  --board-id <board-uuid> \
  --player-name "TestPlayer" \
  --value 1000
```

With a formatted display value:

```bash
leadr score create \
  --board-id <board-uuid> \
  --player-name "SpeedRunner" \
  --value 125.5 \
  --value-display "2:05.500"
```

## View Leaderboard Scores

List scores on a leaderboard:

```bash
leadr score list --board-id <board-uuid>
```

With pagination:

```bash
leadr score list --board-id <board-uuid> --limit 50
```

Fetch all pages:

```bash
leadr score list --board-id <board-uuid> --all
```

## Next Steps

- [Authentication Guide](authentication.md) - Learn about API keys and authentication
- [Command Reference](commands/reference.md) - Explore all available commands
- [Board Templates](commands/board_template.md) - Set up recurring leaderboards (daily, weekly, etc.)
- [Anti-Cheat Flags](commands/score_flag.md) - Manage flagged suspicious scores
