# Game

Game management

## Usage

```bash
leadr game <COMMAND>
```

## Commands

| Command | Description |
|---------|-------------|
| `create` | Create a new game |
| `list` | List games for an account |
| `get` | Get game by ID |
| `update` | Update a game |
| `delete` | Delete a game (soft delete) |

### game create

Create a new game

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--account-id` | Account ID (UUID) - optional if configured via `auth admin configure` | No |
| `--name` | Game name | Yes |
| `--steam-app-id` | Steam App ID (optional) | No |
| `--anti-cheat-enabled` | Enable anti-cheat (default: true) | No |

**Example:**

```bash
leadr game create --name "My Game"
leadr game create --name "My Game" --steam-app-id 123456 --anti-cheat-enabled true
```

### game list

List games for an account

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--account-id` | Account ID (UUID) - optional if configured via `auth admin configure` | No |

**Example:**

```bash
leadr game list
```

### game get

Get game by ID

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--game-id` | Game ID (UUID) | Yes |

**Example:**

```bash
leadr game get --game-id <UUID>
```

### game update

Update a game

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--game-id` | Game ID (UUID) | Yes |
| `--json` | JSON string with fields to update | Yes |

**Example:**

```bash
leadr game update --game-id <UUID> --json '{"name": "New Game Name"}'
```

### game delete

Delete a game (soft delete)

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--game-id` | Game ID (UUID) | Yes |

**Example:**

```bash
leadr game delete --game-id <UUID>
```

