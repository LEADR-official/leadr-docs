# Install

To create a LEADR account, set up your game, and configure your boards, you'll need to first download and install the lightweight LEADR desktop app for your operating system. 

We support the following install options:

- [Windows](#windows)
- [MacOS / Linux](#macos-linux)
- [Manual Install](#manual-install)

## Install

### Windows


Download the latest LEADR app version from [https://leadr.gg/download/windows](https://leadr.gg/download/windows).

Save the `.exe` file in your preferred location.

Double click the `.exe` and follow the instructions.

### MacOS / Linux

For MacOS and Linux there is an automated install script that downloads the latest LEADR app binary for your system and adds it to your PATH.

You can run the script like this:

```bash
curl -sSL https://leadr.gg/download/install.sh | bash
```

### Manual install

Download binaries from the [Releases page](https://github.com/LEADR-official/leadr-releases/releases).

To use the `leadr` command from your terminal, ensure that you save the binary executable file in a directory included in your local `PATH` variable (eg `~/.local/bin`). Alternatively, add the directory containing the binary to your PATH by adding the following line to your shell configuration file (`.bashrc`, `.zshrc`, etc.):

```bash
export PATH="$PATH:/path/to/leadr/directory"
```

Then restart your terminal or run `source ~/.bashrc` (or your shell's config file) to apply the changes.

## Verify

The LEADR app [releases page](https://github.com/LEADR-official/leadr-releases/releases) includes SHA256 checksum values for each version of the app in the `checksums.txt` file attached to each release.

Find the checksum value for your release version and operating system, and compare with the calculated checksum of your downloaded app binary.

To calculate the binary file's checksum, run the appropriate command from the directory containing your downloaded LEADR app file:

=== "Windows (PowerShell)"

    ```powershell
    Get-FileHash -Algorithm SHA256 leadr.exe
    ```

=== "MacOS"

    ```bash
    shasum -a 256 leadr
    ```

=== "Linux"

    ```bash
    sha256sum leadr
    ```

Compare the output with the corresponding value in the `checksums.txt` file. If they match, your download is verified.

## Updating

The LEADR app will notify you when a new version is available. You'll see an update notification on the dashboard when you launch the app.

To update, simply repeat the install process for your operating system. This will replace the old version and preserve your configuration.

## Troubleshooting

### I don't have permission to install new software on my computer

If you're using a device that's managed by your work, school, parents or other tyranical administrator and you don't have the access permissions required to download and install software or applications, unfortunately there's not much we can do to help. You will probably need to contact the relevant person or department and ask them to install LEADR for you. If they were already willing to install your game engine of choice then there's a chance they'll be on your side. It may help to send them supporting material such as:

- LEADR docs: https://docs.leadr.gg
- LEADR Open Source repository: https://github.com/LEADR-official/leadr-oss
- LEADR Releases repository: https://github.com/LEADR-official/leadr-releases
- LEADR website: https://www.leadr.gg
- Our email address: hello@leadr.gg (if they email us we'll try to reassure them we're legit)

### Run the app but nothing happens

Windows, Mac and other operating systems may flag the LEADR app as being from an unknown publisher and prevent it from running.

=== "Windows"

    Windows SmartScreen may block the app. Click "More info" then "Run anyway" to proceed.

=== "MacOS"

    macOS Gatekeeper may block the app. Go to **System Settings > Privacy & Security** and click "Open Anyway" next to the LEADR app warning. Alternatively, right-click the app and select "Open" to bypass the warning.

=== "Linux"

    Ensure the binary is executable:

    ```bash
    chmod +x leadr
    ```

### `leadr` command not found

The `install.sh` script for Mac and Linux attempts to add the LEADR app location to your local `PATH` variable to make the `leadr` command usable from your terminal. If you have moved the application binary executable file or manually installed the LEADR app you may need to add the directory containing the binary to the `PATH` variable yourself.

You can check the directories currently in your `PATH` by running:

```bash
echo $PATH
```

To add a directory to your PATH permanently, add the following line to your shell configuration file (`~/.bashrc` for Bash, `~/.zshrc` for Zsh):

```bash
export PATH="$PATH:$HOME/.local/bin"
```

Then restart your terminal or run `source ~/.bashrc` (or `~/.zshrc`) to apply the changes.

### Running the `leadr` command fails with an error

This sounds like a problem with your downloaded app binary.

Please try downloading and re-installing the latest version of LEADR app following the steps above for your operating system.

If the problem persists, share a screenshot of the error in the "#🐛-bug-reports" channel on [Discord](https://discord.gg/RMUukcAxSZ) and the LEADR team will help you out.

### LEADR app runs but displays error message

This may happen if there's a problem or ongoing maintenance on the LEADR Admin API. You can check the [LEADR status page](https://status.leadr.gg) for incidents or planned maintenance events. You may need to try again later.

!!! leadr "Don't panic"

    We deploy, update and monitor the LEADR Admin API (used by LEADR app) and Client API (used by SDKs and your game) separately to keep your leaderboards running as smoothly as possible. Even if the LEADR app reports an error from the Admin API, your leaderboards and game are unlikely to be impacted.

We try to fix all issues as quickly as we can once they are known to us and appreciate your patience. You can help us out by reporting problems in the "#🐛-bug-reports" channel on [Discord](https://discord.gg/RMUukcAxSZ).

### Where is the LEADR config file?

The default location for the LEADR app config file depends on your operating system:

- **Windows:** `%USERPROFILE%\.leadr\config.toml`
- **MacOS:** `$HOME/.leadr/config.toml`
- **Linux:** `$HOME/.leadr/config.toml`

You can see the location of your current LEADR app config file in the "Configure" screen of the LEADR app.

## Uninstall

To remove the LEADR app:

1. Delete the LEADR binary file (`.exe` on Windows, `leadr` on Mac/Linux)
2. Delete the config directory:
    - **Windows:** `%USERPROFILE%\.leadr\`
    - **MacOS / Linux:** `~/.leadr/`

!!! warning "Your API key is stored in the config"

    Deleting the config directory removes your stored API key. You should consider saving your API key somewhere safe in case you need to use your LEADR account again in future.

## What's Next

- **[Register](../guides/register.md)** - Create your LEADR account
- **[Join a team](../guides/join.md)** -  Join your teammates on an existing LEADR account

---

_Need Help? The LEADR team and community is always happy to help on the [LEADR Discord](https://discord.gg/RMUukcAxSZ)_
