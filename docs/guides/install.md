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

See the [Quick Start](../quick-start.md) guide for next steps.

### MacOS / Linux

For MacOS and Linux there is an automated install script that...

You can run the script like this:

```bash
curl -sSL https://leadr.gg/download/install.sh | bash
```

See the [Quick Start](../quick-start.md) guide for next steps.

### Manual install

Download binaries from the [Releases page](https://github.com/LEADR-official/leadr-releases/releases).

To use the `leadr` command from your terminal, ensure that you save the binary executable file in a directory included in your local `PATH` variable (eg `~/.local/bin`). Alternatively add the directory containing the binary to your path...

See the [Quick Start](../quick-start.md) guide for next steps.

## Verify

The LEADR app [releases page](https://github.com/LEADR-official/leadr-releases/releases) includes SHA256 checksum values for each version of the app.

{screenshot}

Find the checksum value for your release version and operating system, and compare with the calculated checksum of your downloaded app binary.

- **Windows:** ...
- **MacOS:** ...
- **Linux:** ...

## Updating

The LEADR app will notify you when a new version of the app is available, as shown below:

{screenshot}

To update the app, simply repeat the install process for your operating system. This will replace the old version, and preserve your config.

## Troubleshooting

### I don't have permission to install new software on my computer

If you're using a device that's managed by your work, school, parents or other tyranical administrator and you don't have the access permissions required to download and install software or applications, unfortunately there's not much we can do to help. You will probably need to contact the relevant person or department and ask them to install LEADR for you. If they were already willing to install your game engine of choice then there's a chance they'll be on your side. It may help to send them supporting material such as:

- LEADR docs: https://docs.leadr.gg
- LEADR Open Source repository: https://github.com/LEADR-official/leadr-oss
- LEADR Releases repository: https://github.com/LEADR-official/leadr-releases
- LEADR website: https://www.leadr.gg
- Our email address: hello@leadr.gg (if they email us we'll try to reassure them we're legit)

### Run the app but nothing happens

Windows, Mac and other operating systems may say the LEADR app is from an unknown publisher and prevent the application from running when you try...

{Actions per operating system...}

### `leadr` command not found

The `install.sh` script for Mac and Linux attempts to add the LEADR app location to your local `PATH` variable to make the `leadr` command usable from your terminal. If you have moved the application binary executable file or manually installed the LEADR app you may need to add the directory containing the binary to the `PATH` variable yourself.

You can check the directories currently in your `PATH` by running:

```bash
echo $PATH
```

...

### Running the `leadr` command fails with an error

This sounds like a problem with your downloaded app binary.

Please try downloading and re-installing the latest version of LEADR app following the steps above for your operating system.

If the problem persists, share a screenshot of the error in the "#🐛-bug-reports" channel on Discord and the LEADR team will help you out.

### LEADR app runs but displays error message

This may happen if there's a problem or ongoing maintenance on the LEADR Admin API. You can check the [LEADR status page](https://status.leadr.gg) for incidents or planned maintenance events. You may need to try again later.

!!! info "Don't panic"

    We deploy, update and monitor the LEADR Admin API (used by LEADR app) and Client API (used by SDKs and your game) separately to keep your leaderboards running as smoothly as possible. Even if the LEADR app reports an error from the Admin API, your leaderboards and game are unlikely to be impacted.

We try to fix all issues as quickly as we can once they are known to us and appreciate your patience. You can help us out by reporting problems in the "#🐛-bug-reports" channel on Discord.

### Where is the LEADR config file?

The default location for the LEADR app config file depends on your operating system:

- **Windows:** ...
- **MacOS:** `$HOME/.leadr/config.toml`
- **Linux:** `$HOME/.leadr/config.toml`

You can see the location of your current LEADR app config file in the "Configure" screen of the LEADR app.

## Uninstall

To remove the LEADR app you simply need to delete the `.exe` or binary file and the config file...

## What's Next

- **[Register](../guides/register.md)** - Create your LEADR account
- **[Join a team](../guides/join.md)** -  Join your teammates on an existing LEADR account

## Need Help?

If you get stuck at any point, the LEADR team and community is always happy to help on the [LEADR Discord](https://discord.gg/RMUukcAxSZ).
