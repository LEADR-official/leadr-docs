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
| `get-by-slug` | Get board by slug |
| `update` | Update a board |
| `delete` | Delete a board (soft delete) |

### board create

Create a new board

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--account-id` | Account ID (UUID) [optional if configured] | No |
| `--game-id` | Game ID (UUID) [required] | Yes |
| `--name` | Board name [required] | Yes |
| `--description` | Board description [optional] | No |
| `--icon` | Icon - emoji or URL [optional] | No |
| `--short-code` | Short code [optional, auto-generated if omitted] | No |
| `--unit` | Unit, e.g. "points", "seconds" [optional] | No |
| `--sort-direction` | Sort direction: asc or desc [optional, default: desc] | No |
| `--keep-strategy` | Keep strategy: best, first, last, or all [optional, default: best] | No |
| `--is-active` | Board is active [default: true] | No |
| `--is-published` | Board is published/visible to clients [default: true] | No |
| `--starts-at` | Start time for time-bounded boards, ISO 8601 [optional] | No |
| `--ends-at` | End time for time-bounded boards, ISO 8601 [optional] | No |

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
| `--account-id` | Account ID (UUID) [optional if configured] | No |
| `--game-id` | Game ID to filter boards by (UUID) [optional] | No |

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
| `--board-id` | Board ID (e.g. `brd_xxx`) [required] | Yes |
| `--account-id` | Account ID for superadmin cross-account access [optional] | No |

**Example:**

```bash
leadr board get --board-id <UUID>
```

### board get-by-code

Get board by short code

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--account-id` | Account ID (UUID) [optional if configured] | No |
| `--short-code` | Short code [required] | Yes |

**Example:**

```bash
leadr board get-by-code --short-code highscores
```

### board get-by-slug

Get board by slug

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--account-id` | Account ID (UUID) [optional if configured] | No |
| `--game-id` | Game ID (UUID) [required] | Yes |
| `--slug` | Board slug [required] | Yes |


### board update

Update a board

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--board-id` | Board ID (UUID) [required] | Yes |
| `--json` | JSON string with fields to update [required] | Yes |

**Example:**

```bash
leadr board update --board-id <UUID> --json '{"name": "New Name"}'
```

### board delete

Delete a board (soft delete)

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--board-id` | Board ID (UUID) [required] | Yes |

**Example:**

```bash
leadr board delete --board-id <UUID>
```

