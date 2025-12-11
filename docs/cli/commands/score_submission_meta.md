# Score Submission Meta

Score submission metadata (analytics)

## Usage

```bash
leadr score-submission-meta <COMMAND>
```

## Commands

| Command | Description |
|---------|-------------|
| `list` | List score submission metadata for an account |
| `get` | Get score submission metadata by ID |

### score-submission-meta list

List score submission metadata for an account

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--account-id` | Account ID (UUID) - optional if configured via `auth admin configure` | No |
| `--board-id` | Optional Board ID to filter by (UUID) | No |
| `--device-id` | Optional Device ID to filter by (UUID) | No |
| `--game-id` | Optional Game ID to filter by (UUID) | No |

**Example:**

```bash
leadr score-submission-meta list
```

### score-submission-meta get

Get score submission metadata by ID

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--meta-id` | Metadata ID (UUID) | Yes |

**Example:**

```bash
leadr score-submission-meta get --meta-id <UUID>
```

