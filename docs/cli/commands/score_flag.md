# Score Flag

Score flag management (anti-cheat)

## Usage

```bash
leadr score-flag <COMMAND>
```

## Commands

| Command | Description |
|---------|-------------|
| `list` | List score flags for an account |
| `get` | Get score flag by ID |
| `review` | Review/update a score flag |
| `delete` | Delete a score flag (soft delete) |

### score-flag list

List score flags for an account

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--account-id` | Account ID (UUID) - optional if configured via `auth admin configure` | No |
| `--board-id` | Optional Board ID to filter by (UUID) | No |
| `--game-id` | Optional Game ID to filter by (UUID) | No |
| `--status` | Optional status filter (`PENDING`, `CONFIRMED_CHEAT`, `FALSE_POSITIVE`, `DISMISSED`) | No |
| `--flag-type` | Optional flag type filter (`VELOCITY`, `DUPLICATE`, `RATE_LIMIT`) | No |

**Example:**

```bash
leadr score-flag list
leadr score-flag list --status PENDING --flag-type VELOCITY
```

### score-flag get

Get score flag by ID

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--flag-id` | Flag ID (UUID) | Yes |

**Example:**

```bash
leadr score-flag get --flag-id <UUID>
```

### score-flag review

Review/update a score flag

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--flag-id` | Flag ID (UUID) | Yes |
| `--status` | New status (`PENDING`, `CONFIRMED_CHEAT`, `FALSE_POSITIVE`, `DISMISSED`) | No |
| `--reviewer-decision` | Reviewer decision/notes | No |

**Example:**

```bash
leadr score-flag review --flag-id <UUID> --status CONFIRMED_CHEAT
leadr score-flag review --flag-id <UUID> --status FALSE_POSITIVE --reviewer-decision "Legitimate speedrun"
```

### score-flag delete

Delete a score flag (soft delete)

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--flag-id` | Flag ID (UUID) | Yes |

**Example:**

```bash
leadr score-flag delete --flag-id <UUID>
```

