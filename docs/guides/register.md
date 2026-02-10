# Register

To set up your game and create boards you'll first need a LEADR account. This guide assumes you're creating a LEADR account for the first time rather than [joining an account](./join.md) created by a colleague or teammate.

## Prerequisites

- [Download and install the LEADR app](./install.md)
- An email address to associate with your LEADR account and receive the verification email

!!! tip "Already have an invite?"

    If a teammate has already created a LEADR account and sent you an invite, you don't need to register a new account. See [Join a Team](./join.md) instead.

## Create Your Account

Creating a LEADR account takes about a minute. You'll verify your email, set up your profile, and name your team.

![Registering a LEADR account](../assets/images/register.gif)

### Step 1: Start Registration

Open the LEADR app and press `r` or select **Register** from the main menu.

When prompted, choose option **1** "Creating a new account".

### Step 2: Verify Your Email

Enter your email address. We'll send you a 6-digit verification code.

Check your inbox and enter the code when prompted.

If you don't receive the email, type `resend` to request a new code.

### Step 3: Set Your Display Name

Enter your display name. This is how you'll appear to teammates on your account.

This field is optional - if you leave it blank, we'll use the part of your email before the `@` symbol.

### Step 4: Name Your Team

Enter your team or studio name. This is the name of your LEADR account that teammates will see when they join.

This field is required (minimum 2 characters).

### Step 5: Optional Jam Code

If you're participating in a game jam or event with LEADR integration, you can enter the jam code here. Otherwise, leave it blank and press Enter to continue.

### Step 6: Done!

You'll see a success screen confirming your account has been created. Press Enter or Esc to return to the dashboard.

## Your API Key

Your API key is automatically generated and saved to your local config file:

- **MacOS / Linux:** `~/.leadr/config.toml`
- **Windows:** `%USERPROFILE%\.leadr\config.toml`

!!! warning "Keep your API key secret"

    Your API key grants admin access to your LEADR account. Never put it in your game code - game clients and SDKs use a separate API and a different authentication method.

    We'll never ask you for it, and you should never share it online or give it to anyone, even teammates.

    Keep it secret, keep it (your game) safe.

## What's Next

- **[Create a Game](./create-game.md)** - Set your game up in the LEADR app
- **[Invite teammates](./invites.md)** - Send invites so teammates can join your LEADR account

## Need Help?

If you get stuck at any point, the LEADR team and community is always happy to help on the [LEADR Discord](https://discord.gg/RMUukcAxSZ).

