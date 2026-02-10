# Go-Live Checklist

Everything to verify before your game ships. Run through this checklist to make sure your LEADR integration is production-ready.

## Prerequisites

- [Download and install the LEADR app](./install.md)
- A LEADR account:
  - [Register](./register.md)
  - [Join a team](./join.md)
- [Create a game](./create-game.md)
- [Create a board](./create-board.md)
- [Get the SDK for your game engine](./get-sdk.md)
- [Use the SDK in your game](./use-sdk.md)

## Pre-Launch Checklist

### SDK Configuration

- **Correct Game ID** - Double check in the LEADR app and verify you're using the correct Game ID, including the `gam_` prefix
- **Production API URL** - Ensure `base_url` is set to `https://api.leadrcloud.com` (you probably haven't changed this)

### Board Configuration

- **Sort direction** - Verify each board sorts correctly (ascending for speedruns, descending for high scores)
- **Keep strategy** - Confirm the right behavior for duplicate scores (best, latest, or first) if applicable for your board
- **Active status** - Ensure boards are set to "Active" so they accept new scores
- **Published status** - Set boards to "Published" in order to generate board web pages

### Anti-Cheat

- **Anti-cheat enabled** - Verify anti-cheat is enabled on your game if you want to use it (recommended - it's on by default)
- **Review process ready** - Know how to [review flagged scores](./review-score-flags.md)
- **Reasonable score bounds** - Consider what scores are realistically achievable to help identify cheaters

### Testing

- **Submit test scores** - With `test_mode` still enabled, verify score submission works end-to-end
- **Scores are visible** - Use the LEADR app to check scores are recorded in the right board
- **Fetch leaderboards** - Test that your game correctly displays leaderboard data
- **Error handling** - Confirm your game handles network errors gracefully

### Before you release

- **Test mode disabled** - Set `test_mode` to `false` before building
- **Debug logging disabled** - Set `debug_logging` to `false` before building

### Web Views

- **Board page URLs** - Test your [board page URLs](./board-pages.md) work correctly

### Support

If you encounter any issues:

1. Check the [LEADR status page](https://status.leadr.gg)
2. Review your SDK configuration
3. Reach out on [Discord](https://discord.gg/RMUukcAxSZ) for help

!!! success "You're ready to launch!"

    If you've checked all the steps above, your LEADR integration is ready for production.

    Share your planned launch date with us on [Discord](https://discord.gg/RMUukcAxSZ) so we can give you a shout out.

    Good luck!

## What's Next

- **[Share your boards online](./board-pages.md)** - See &amp; share the live-updating web pages for your game's boards
- **[Review Scores](./review-score-flags.md)** - Review &amp; resolve scores flagged by the anti-cheat system

## Need Help?

If you get stuck at any point, the LEADR team and community is always happy to help on the [LEADR Discord](https://discord.gg/RMUukcAxSZ).
