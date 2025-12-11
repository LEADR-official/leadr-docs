# Device

Device management

## Usage

```bash
leadr device <COMMAND>
```

## Commands

| Command | Description |
|---------|-------------|
| `list` | List devices for an account |
| `get` | Get device by ID |
| `update` | Update device status |
| `delete` | Delete a device (soft delete) |

### device list

List devices for an account

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--account-id` | Account ID (UUID) - optional if configured via `auth admin configure` | No |
| `--game-id` | Optional Game ID to filter by (UUID) | No |
| `--status` | Optional status filter (active, banned, suspended) | No |

**Example:**

```bash
leadr device list
leadr device list --status banned
```

### device get

Get device by ID

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--device-id` | Device ID (UUID) | Yes |

**Example:**

```bash
leadr device get --device-id <UUID>
```

### device update

Update device status

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--device-id` | Device ID (UUID) | Yes |
| `--status` | New status (active, banned, suspended) | No |

**Example:**

```bash
leadr device update --device-id <UUID> --status banned
```

### device delete

Delete a device (soft delete)

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--device-id` | Device ID (UUID) | Yes |

**Example:**

```bash
leadr device delete --device-id <UUID>
```

