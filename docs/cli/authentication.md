# Authentication

The LEADR CLI uses API keys to authenticate requests to the LEADR API. This guide explains how authentication works and how to manage your credentials.

## How It Works

When you run `leadr register` or `leadr auth admin configure`, the CLI stores your API key in a local configuration file. All subsequent commands use this stored key to authenticate with the LEADR API.

**Configuration location:** `~/.leadr/config.toml`

The configuration file is created with restrictive permissions (readable only by you) to protect your credentials.

## Configuring Your API Key

### During Registration

When you create a new account with `leadr register`, an API key is automatically generated and saved:

```bash
leadr register
```

### Manual Configuration

If you already have an API key (e.g., from the LEADR dashboard), configure it manually:

```bash
leadr auth admin configure
```

This command prompts you to enter your API key securely (input is hidden).

### Check Configuration Status

Verify your API key is configured:

```bash
leadr auth admin status
```

This shows whether an API key is saved and its prefix (for identification).

### Clear Saved Credentials

Remove your saved API key:

```bash
leadr auth admin clear
```

## API Key Format

LEADR API keys have the format `ldr_<random-string>`.

Example: `ldr_abc123def456...`

**Important:** API keys are shown only once when created. Store them securely.

## Account Context

Many commands require knowing which account to operate on. The CLI determines this in one of two ways:

### 1. Automatic (Recommended)

When you authenticate with a non-superadmin API key, the CLI automatically uses your account for all operations. You don't need to specify `--account-id`.

```bash
# These work without --account-id for regular users
leadr game list
leadr board list
leadr user list
```

### 2. Explicit Account ID

Superadmin users can operate on any account by specifying `--account-id`:

```bash
leadr game list --account-id <account-uuid>
leadr user create --account-id <account-uuid> --email user@example.com --display-name "User"
```

## Creating Additional API Keys

Create additional API keys for team members or services:

```bash
# First, create a user
leadr user create --email teammate@example.com --display-name "Teammate"

# Then create an API key for that user
leadr api-key create --user-id <user-uuid> --name "Teammate's Key"
```

**Note:** The API key value is displayed only once. Make sure to copy and save it.

## Managing API Keys

List all API keys for your account:

```bash
leadr api-key list
```

Get details about a specific key:

```bash
leadr api-key get --key-id <key-uuid>
```

Revoke a compromised or unused key:

```bash
leadr api-key revoke --key-id <key-uuid>
```

## Security Best Practices

1. **Never commit API keys** to version control
1. **Use separate keys** for development and production
1. **Revoke unused keys** promptly
1. **Rotate keys periodically** for sensitive applications
1. **Use environment variables** in CI/CD pipelines instead of storing keys in config files

## Troubleshooting

### "No API key configured"

Run `leadr auth admin configure` to set up your API key.

### "Invalid API key"

Your API key may have been revoked or is incorrect. Check the key and reconfigure if needed.

### "Permission denied"

You may be trying to access resources outside your account. Contact support if you believe this is an error.

## Command Reference

| Command                      | Description                  |
| ---------------------------- | ---------------------------- |
| `leadr auth admin configure` | Set up API key (interactive) |
| `leadr auth admin status`    | Check API key status         |
| `leadr auth admin clear`     | Remove saved API key         |
| `leadr api-key create`       | Create a new API key         |
| `leadr api-key list`         | List all API keys            |
| `leadr api-key get`          | Get API key details          |
| `leadr api-key revoke`       | Revoke an API key            |

See [API Key Commands](commands/api_key.md) for detailed documentation.
