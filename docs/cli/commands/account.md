# Account

Account management

## Usage

```bash
leadr account <COMMAND>
```

## Commands

| Command | Description |
|---------|-------------|
| `get` | Get account by ID |
| `update` | Update an account |
| `delete` | Delete an account (soft delete) |

### account get

Get account by ID

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--account-id` | Account ID (UUID) [optional if configured] | No |

**Example:**

```bash
leadr account get
leadr account get --account-id <UUID>
```

### account update

Update an account

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--account-id` | Account ID (UUID) [optional if configured] | No |
| `--json` | JSON string with fields to update [required] | Yes |

**Example:**

```bash
leadr account update --account-id <UUID> --json '{"name": "New Name"}'
```

### account delete

Delete an account (soft delete)

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--account-id` | Account ID (UUID) [optional if configured] | No |

**Example:**

```bash
leadr account delete --account-id <UUID>
```

