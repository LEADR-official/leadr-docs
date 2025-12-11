# Score

Score management

## Usage

```bash
leadr score <COMMAND>
```

## Commands

| Command | Description |
|---------|-------------|
| `create` | Create a new score |
| `list` | List scores for an account |
| `get` | Get score by ID |
| `update` | Update a score |
| `delete` | Delete a score (soft delete) |

### score create

Create a new score

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--account-id` | Account ID (UUID) - optional when using client authentication | No |
| `--game-id` | Game ID (UUID) - optional when using client authentication | No |
| `--board-id` | Board ID (UUID) | Yes |
| `--device-id` | Device ID (UUID) - optional when using client authentication | No |
| `--player-name` | Player name | Yes |
| `--value` | Score value (number) | Yes |
| `--value-display` | Optional display string (e.g., "1:23.45", "1,234 points") | No |
| `--filter-timezone` | Optional timezone filter | No |
| `--filter-country` | Optional country filter | No |
| `--filter-city` | Optional city filter | No |

**Example:**

```bash
leadr score create --board-id <UUID> --player-name "Player1" --value 1000
leadr score create --board-id <UUID> --player-name "Player1" --value 1000 --value-display "1,000 pts"
```

### score list

List scores for an account

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--account-id` | Account ID (UUID) - optional when using client authentication | No |
| `--board-id` | Optional Board ID to filter by (UUID) | No |
| `--game-id` | Optional Game ID to filter by (UUID) | No |
| `--device-id` | Optional Device ID to filter by (UUID) | No |
| `--cursor` | Pagination cursor (from previous response) | No |
| `--limit` | Number of items per page (1-100, default: 20) | No |
| `--sort` | Sort order (e.g., "value:desc", "`created_at:asc`") | No |
| `--all` | Fetch all pages automatically | No |

**Example:**

```bash
leadr score list
leadr score list --board-id <UUID> --limit 50
```

### score get

Get score by ID

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--score-id` | Score ID (UUID) | Yes |

**Example:**

```bash
leadr score get --score-id <UUID>
```

### score update

Update a score

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--score-id` | Score ID (UUID) | Yes |
| `--json` | JSON string with fields to update | Yes |

**Example:**

```bash
leadr score update --score-id <UUID> --json '{"value": 2000}'
```

### score delete

Delete a score (soft delete)

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--score-id` | Score ID (UUID) | Yes |

**Example:**

```bash
leadr score delete --score-id <UUID>
```

