# Command Reference

This section documents all available commands in the LEADR CLI.

## Global Options

All commands support the following global options:

| Option          | Description                   |
| --------------- | ----------------------------- |
| `--host <HOST>` | Override the default API host |
| `--help`        | Show help information         |
| `--version`     | Show version information      |

## Top-Level Commands

| Command                   | Description                              |
| ------------------------- | ---------------------------------------- |
| [`register`](register.md) | Create a new LEADR account (interactive) |
| [`me`](me.md)             | Show current account and user info       |

## Command Groups

### Authentication

| Command                                                | Description             |
| ------------------------------------------------------ | ----------------------- |
| [`auth admin configure`](auth.md#auth-admin-configure) | Configure admin API key |
| [`auth admin status`](auth.md#auth-admin-status)       | Show API key status     |
| [`auth admin clear`](auth.md#auth-admin-clear)         | Clear saved API key     |

### Resource Management

| Group                               | Description            | Commands                                       |
| ----------------------------------- | ---------------------- | ---------------------------------------------- |
| [account](account.md)               | Account management     | get, update, delete                            |
| [user](user.md)                     | User management        | create, list, get, update, delete              |
| [api-key](api_key.md)               | API key management     | create, list, get, revoke                      |
| [game](game.md)                     | Game management        | create, list, get, update, delete              |
| [board](board.md)                   | Leaderboard management | create, list, get, get-by-code, update, delete |
| [board-template](board_template.md) | Recurring leaderboards | create, list, get, update, delete              |
| [score](score.md)                   | Score management       | create, list, get, update, delete              |

### Device & Anti-Cheat

| Group                               | Description       | Commands                  |
| ----------------------------------- | ----------------- | ------------------------- |
| [device](device.md)                 | Device management | list, get, update, delete |
| [device-session](device_session.md) | Device sessions   | list, get, update, delete |
| [score-flag](score_flag.md)         | Anti-cheat flags  | list, get, review, delete |

### Analytics

| Group                                             | Description          | Commands  |
| ------------------------------------------------- | -------------------- | --------- |
| [score-submission-meta](score_submission_meta.md) | Submission analytics | list, get |

## Full Reference

For a complete single-page reference of all commands, see [reference.md](reference.md).

## Getting Help

Get help for any command:

```bash
# General help
leadr --help

# Help for a command group
leadr game --help

# Help for a specific command
leadr game create --help
```
