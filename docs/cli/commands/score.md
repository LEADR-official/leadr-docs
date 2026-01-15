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
| `--account-id` | Account ID (UUID) [optional with client auth] | No |
| `--game-id` | Game ID (UUID) [optional with client auth] | No |
| `--board-id` | Board ID (UUID) [required] | Yes |
| `--device-id` | Device ID (UUID) [optional with client auth] | No |
| `--player-name` | Player name [required] | Yes |
| `--value` | Score value (number) [required] | Yes |
| `--value-display` | Display string, e.g. "1:23.45", "1,234 points" [optional] | No |
| `--filter-timezone` | Timezone filter [optional] | No |
| `--filter-country` | Country filter [optional] | No |
| `--filter-city` | City filter [optional] | No |

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
| `--account-id` | Account ID (UUID) [optional with client auth] | No |
| `--board-id` | Board ID to filter by (UUID) [optional] | No |
| `--game-id` | Game ID to filter by (UUID) [optional] | No |
| `--device-id` | Device ID to filter by (UUID) [optional] | No |
| `--cursor` | Pagination cursor from previous response [optional] | No |
| `--limit` | Items per page, 1-100 [optional, default: 20] | No |
| `--sort` | Sort order, e.g. "value:desc", "`created_at:asc`" [optional] | No |
| `--all` | Fetch all pages automatically | No |
| `--is-test` | Filter by test mode: true (test only), false (production only), all (both). API defaults to false (production only) when omitted | No |

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
| `--score-id` | Score ID (UUID) [required] | Yes |

**Example:**

```bash
leadr score get --score-id <UUID>
```

### score update

Update a score

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--score-id` | Score ID (UUID) [required] | Yes |
| `--json` | JSON string with fields to update [required] | Yes |

**Example:**

```bash
leadr score update --score-id <UUID> --json '{"value": 2000}'
```

### score delete

Delete a score (soft delete)

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--score-id` | Score ID (UUID) [required] | Yes |

**Example:**

```bash
leadr score delete --score-id <UUID>
```

