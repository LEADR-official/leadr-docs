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
| `--account-id` | Account ID (UUID) [optional if configured] | No |
| `--board-id` | Board ID to filter by (UUID) [optional] | No |
| `--device-id` | Device ID to filter by (UUID) [optional] | No |
| `--game-id` | Game ID to filter by (UUID) [optional] | No |

**Example:**

```bash
leadr score-submission-meta list
```

### score-submission-meta get

Get score submission metadata by ID

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--meta-id` | Metadata ID (UUID) [required] | Yes |

**Example:**

```bash
leadr score-submission-meta get --meta-id <UUID>
```

