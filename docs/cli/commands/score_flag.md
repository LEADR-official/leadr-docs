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
| `--account-id` | Account ID (UUID) [optional if configured] | No |
| `--board-id` | Board ID to filter by (UUID) [optional] | No |
| `--game-id` | Game ID to filter by (UUID) [optional] | No |
| `--status` | Status: PENDING/CONFIRMED_CHEAT/FALSE_POSITIVE/DISMISSED [optional] | No |
| `--flag-type` | Flag type: VELOCITY/DUPLICATE/RATE_LIMIT [optional] | No |

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
| `--flag-id` | Flag ID (UUID) [required] | Yes |

**Example:**

```bash
leadr score-flag get --flag-id <UUID>
```

### score-flag review

Review/update a score flag

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--flag-id` | Flag ID (UUID) [required] | Yes |
| `--status` | New status: PENDING/CONFIRMED_CHEAT/FALSE_POSITIVE/DISMISSED [optional] | No |
| `--reviewer-decision` | Reviewer decision/notes [optional] | No |

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
| `--flag-id` | Flag ID (UUID) [required] | Yes |

**Example:**

```bash
leadr score-flag delete --flag-id <UUID>
```

