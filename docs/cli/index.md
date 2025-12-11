# LEADR CLI

Command-line tool for managing your LEADR account and leaderboards.

> **Need help?** Give us a shout on Discord: [discord.gg/RMUukcAxSZ](https://discord.gg/RMUukcAxSZ)

## What is LEADR?

LEADR is the cross-platform leaderboard backend for game developers. The LEADR CLI provides a command-line interface to manage your account, games, leaderboards, and scores.

## Quick Links

- [Getting Started](getting-started.md) - Installation and first steps
- [Authentication](authentication.md) - How to configure your API key
- [Command Reference](commands/reference.md) - Full command documentation

## Quick Start

```bash
curl -sSL https://raw.githubusercontent.com/LEADR-official/leadr-cli-releases/main/install.sh | bash
leadr register
```

See [Getting Started](getting-started.md) for more details.

## Features

- **Account Management** - Create and manage your LEADR account
- **Game Management** - Register and configure your games
- **Leaderboard Management** - Create and customize leaderboards
- **Score Management** - Submit and query scores
- **Anti-Cheat** - Review flagged scores and manage devices

## Common Commands

| Command                      | Description                      |
| ---------------------------- | -------------------------------- |
| `leadr register`             | Create a new LEADR account       |
| `leadr auth admin configure` | Configure your API key           |
| `leadr game create`          | Create a new game                |
| `leadr game list`            | List your games                  |
| `leadr board create`         | Create a leaderboard             |
| `leadr board list`           | List boards for a game           |
| `leadr score list`           | List scores on a leaderboard     |
| `leadr --help`               | Show all available commands      |
| `leadr <command> --help`     | Show help for a specific command |

## Command Groups

| Group                                                      | Description                           |
| ---------------------------------------------------------- | ------------------------------------- |
| [auth](commands/auth.md)                                   | Authentication and API key management |
| [account](commands/account.md)                             | Account management                    |
| [user](commands/user.md)                                   | User management                       |
| [api-key](commands/api_key.md)                             | API key management                    |
| [game](commands/game.md)                                   | Game management                       |
| [board](commands/board.md)                                 | Leaderboard management                |
| [board-template](commands/board_template.md)               | Recurring leaderboard templates       |
| [score](commands/score.md)                                 | Score management                      |
| [device](commands/device.md)                               | Device management                     |
| [device-session](commands/device_session.md)               | Device session management             |
| [score-flag](commands/score_flag.md)                       | Anti-cheat score flags                |
| [score-submission-meta](commands/score_submission_meta.md) | Score submission analytics            |

## Documentation

For full documentation, visit [docs.leadr.gg](https://docs.leadr.gg)
