# Api Key

API key management

## Usage

```bash
leadr api-key <COMMAND>
```

## Commands

| Command | Description |
|---------|-------------|
| `create` | Create a new API key |
| `list` | List API keys for an account |
| `get` | Get API key by ID |
| `revoke` | Revoke an API key (soft delete) |

### api-key create

Create a new API key

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--account-id` | Account ID (UUID) [optional if configured] | No |
| `--user-id` | User ID (UUID), the user who owns this API key [required] | Yes |
| `--name` | API key name [required] | Yes |

**Example:**

```bash
leadr api-key create --user-id <UUID> --name "Production Key"
```

### api-key list

List API keys for an account

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--account-id` | Account ID (UUID) [optional if configured] | No |

**Example:**

```bash
leadr api-key list
```

### api-key get

Get API key by ID

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--key-id` | API key ID (UUID) [required] | Yes |

**Example:**

```bash
leadr api-key get --key-id <UUID>
```

### api-key revoke

Revoke an API key (soft delete)

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--key-id` | API key ID (UUID) [required] | Yes |

**Example:**

```bash
leadr api-key revoke --key-id <UUID>
```

