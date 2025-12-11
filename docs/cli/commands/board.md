# Board

Board (leaderboard) management

## Usage

```bash
leadr board <COMMAND>
```

## Commands

| Command | Description |
|---------|-------------|
| `create` | Create a new board |
| `list` | List boards for an account |
| `get` | Get board by ID |
| `get-by-code` | Get board by short code |
| `update` | Update a board |
| `delete` | Delete a board (soft delete) |

### board create

Create a new board

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--account-id` | Account ID (UUID) - optional if configured via `auth admin configure` | No |
| `--game-id` | Game ID (UUID) | Yes |
| `--name` | Board name | Yes |
| `--icon` | Icon (emoji or URL) | No |
| `--short-code` | Short code (globally unique identifier) | No |
| `--unit` | Unit (e.g., "points", "seconds", "kills") | No |
| `--sort-direction` | Sort direction (asc or desc) | No |
| `--keep-strategy` | Keep strategy (best, first, last, or all) | No |
| `--is-active` | Board is active (default: true) | No |

**Example:**

```bash
leadr board create --game-id <UUID> --name "High Scores"
leadr board create --game-id <UUID> --name "Weekly" --short-code weekly --sort-direction desc
```

### board list

List boards for an account

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--account-id` | Account ID (UUID) - optional when using client authentication | No |
| `--game-id` | Optional Game ID to filter boards by (UUID) | No |

**Example:**

```bash
leadr board list
leadr board list --game-id <UUID>
```

### board get

Get board by ID

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--board-id` | Board ID (e.g., `brd_xxx`) | Yes |
| `--account-id` | Account ID (for superadmin cross-account access) | No |

**Example:**

```bash
leadr board get --board-id <UUID>
```

### board get-by-code

Get board by short code

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--account-id` | Account ID (UUID) - optional if configured via `auth admin configure` | No |
| `--short-code` | Short code | Yes |

**Example:**

```bash
leadr board get-by-code --short-code highscores
```

### board update

Update a board

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--board-id` | Board ID (UUID) | Yes |
| `--json` | JSON string with fields to update | Yes |

**Example:**

```bash
leadr board update --board-id <UUID> --json '{"name": "New Name"}'
```

### board delete

Delete a board (soft delete)

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--board-id` | Board ID (UUID) | Yes |

**Example:**

```bash
leadr board delete --board-id <UUID>
```

