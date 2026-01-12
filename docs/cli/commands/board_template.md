# Board Template

Board template management

## Usage

```bash
leadr board-template <COMMAND>
```

## Commands

| Command | Description |
|---------|-------------|
| `create` | Create a new board template |
| `list` | List board templates for an account |
| `get` | Get board template by ID |
| `update` | Update a board template |
| `delete` | Delete a board template (soft delete) |

### board-template create

Create a new board template

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--account-id` | Account ID (UUID) [optional if configured] | No |
| `--game-id` | Game ID (UUID) [required] | Yes |
| `--name` | Template name [required] | Yes |
| `--slug` | URL-friendly slug for boards created from this template [optional] | No |
| `--repeat-interval` | Repeat interval, `PostgreSQL` syntax e.g. "7 days", "1 month" [required] | Yes |
| `--next-run-at` | Next run time, ISO 8601 datetime [required] | Yes |
| `--is-active` | Template is active [default: true] | No |
| `--is-published` | Boards created from this template should be published [default: true] | No |
| `--name-template` | Name template for generated boards [optional] | No |
| `--series` | Series identifier for sequential board naming [optional] | No |
| `--icon` | Icon identifier for boards, e.g. "fa-crown" [optional] | No |
| `--unit` | Unit of measurement, e.g. "seconds", "points" [optional] | No |
| `--sort-direction` | Sort direction for scores [default: desc] | No |
| `--keep-strategy` | Strategy for keeping multiple scores from same user [default: all] | No |
| `--starts-at` | Start time for time-bounded boards, ISO 8601 [optional] | No |
| `--ends-at` | End time for time-bounded boards, ISO 8601 [optional] | No |

**Example:**

```bash
leadr board-template create --game-id <UUID> --name "Weekly Challenge" --repeat-interval "7 days" --next-run-at "2025-01-01T00:00:00Z"
```

### board-template list

List board templates for an account

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--account-id` | Account ID (UUID) [optional if configured] | No |
| `--game-id` | Game ID to filter templates by (UUID) [optional] | No |

**Example:**

```bash
leadr board-template list
```

### board-template get

Get board template by ID

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--template-id` | Template ID (UUID) [required] | Yes |

**Example:**

```bash
leadr board-template get --template-id <UUID>
```

### board-template update

Update a board template

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--template-id` | Template ID (UUID) [required] | Yes |
| `--json` | JSON string with fields to update [required] | Yes |

**Example:**

```bash
leadr board-template update --template-id <UUID> --json '{"is_active": false}'
```

### board-template delete

Delete a board template (soft delete)

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--template-id` | Template ID (UUID) [required] | Yes |

**Example:**

```bash
leadr board-template delete --template-id <UUID>
```

