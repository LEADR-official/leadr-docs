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
| `--account-id` | Account ID (UUID) - optional if configured via `auth admin configure` | No |
| `--game-id` | Game ID (UUID) | Yes |
| `--name` | Template name | Yes |
| `--slug` | URL-friendly slug for boards created from this template | No |
| `--repeat-interval` | Repeat interval (`PostgreSQL` interval syntax, e.g., "7 days", "1 month") | Yes |
| `--next-run-at` | Next run time (ISO 8601 datetime, e.g., "2025-01-01T00:00:00Z") | Yes |
| `--is-active` | Template is active (default: true) | No |
| `--is-published` | Whether boards created from this template should be published (default: true) | No |
| `--name-template` | Optional name template for generated boards | No |
| `--series` | Optional series identifier for sequential board naming | No |
| `--icon` | Icon identifier for boards (e.g., "fa-crown") | No |
| `--unit` | Unit of measurement for scores (e.g., "seconds", "points") | No |
| `--sort-direction` | Sort direction for scores (default: desc) | No |
| `--keep-strategy` | Strategy for keeping multiple scores from the same user (default: all) | No |
| `--starts-at` | Optional start time for time-bounded boards (ISO 8601 datetime) | No |
| `--ends-at` | Optional end time for time-bounded boards (ISO 8601 datetime) | No |

**Example:**

```bash
leadr board-template create --game-id <UUID> --name "Weekly Challenge" --repeat-interval "7 days" --next-run-at "2025-01-01T00:00:00Z"
```

### board-template list

List board templates for an account

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--account-id` | Account ID (UUID) - optional if configured via `auth admin configure` | No |
| `--game-id` | Optional Game ID to filter templates by (UUID) | No |

**Example:**

```bash
leadr board-template list
```

### board-template get

Get board template by ID

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--template-id` | Template ID (UUID) | Yes |

**Example:**

```bash
leadr board-template get --template-id <UUID>
```

### board-template update

Update a board template

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--template-id` | Template ID (UUID) | Yes |
| `--json` | JSON string with fields to update | Yes |

**Example:**

```bash
leadr board-template update --template-id <UUID> --json '{"is_active": false}'
```

### board-template delete

Delete a board template (soft delete)

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--template-id` | Template ID (UUID) | Yes |

**Example:**

```bash
leadr board-template delete --template-id <UUID>
```

