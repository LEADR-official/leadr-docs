# Device Session

Device session management

## Usage

```bash
leadr device-session <COMMAND>
```

## Commands

| Command | Description |
|---------|-------------|
| `list` | List device sessions for an account |
| `get` | Get device session by ID |
| `update` | Update device session status |
| `delete` | Delete a device session (soft delete) |

### device-session list

List device sessions for an account

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--account-id` | Account ID (UUID) - optional if configured via `auth admin configure` | No |
| `--device-id` | Optional Device ID to filter by (UUID) | No |
| `--game-id` | Optional Game ID to filter by (UUID) | No |
| `--status` | Optional status filter | No |

**Example:**

```bash
leadr device-session list
```

### device-session get

Get device session by ID

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--session-id` | Session ID (UUID) | Yes |

**Example:**

```bash
leadr device-session get --session-id <UUID>
```

### device-session update

Update device session status

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--session-id` | Session ID (UUID) | Yes |
| `--status` | New status | No |

**Example:**

```bash
leadr device-session update --session-id <UUID> --status terminated
```

### device-session delete

Delete a device session (soft delete)

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--session-id` | Session ID (UUID) | Yes |

**Example:**

```bash
leadr device-session delete --session-id <UUID>
```

