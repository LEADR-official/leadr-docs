# User

User management

## Usage

```bash
leadr user <COMMAND>
```

## Commands

| Command | Description |
|---------|-------------|
| `create` | Create a new user |
| `list` | List users for an account |
| `get` | Get user by ID |
| `update` | Update a user |
| `delete` | Delete a user (soft delete) |

### user create

Create a new user

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--account-id` | Account ID (UUID) - optional if configured via `auth admin configure` | No |
| `--email` | User email | Yes |
| `--display-name` | Display name | Yes |

**Example:**

```bash
leadr user create --email user@example.com --display-name "John Doe"
```

### user list

List users for an account

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--account-id` | Account ID (UUID) - optional if configured via `auth admin configure` | No |

**Example:**

```bash
leadr user list
```

### user get

Get user by ID

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--user-id` | User ID (UUID) | Yes |

**Example:**

```bash
leadr user get --user-id <UUID>
```

### user update

Update a user

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--user-id` | User ID (UUID) | Yes |
| `--json` | JSON string with fields to update (e.g., `{"email": "new@example.com", "display_name": "New Name"}`) | Yes |

**Example:**

```bash
leadr user update --user-id <UUID> --json '{"display_name": "Jane Doe"}'
```

### user delete

Delete a user (soft delete)

**Options:**

| Option | Description | Required |
|--------|-------------|----------|
| `--user-id` | User ID (UUID) | Yes |

**Example:**

```bash
leadr user delete --user-id <UUID>
```

