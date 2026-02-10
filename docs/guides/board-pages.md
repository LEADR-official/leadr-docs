# Board Pages

Every LEADR board automatically gets a live-updating web page. Share leaderboards with players, embed them on your website, or display them during streams.

## Prerequisites

- [Download and install the LEADR app](./install.md)
- A LEADR account:
  - [Register](./register.md)
  - [Join a team](./join.md)
- [Create a game](./create-game.md)
- [Create a board](./create-board.md)
- [Get the SDK for your game engine](./get-sdk.md)
- [Use the SDK in your game](./use-sdk.md)

## Game Page URLs

Every game has a unique URL listing any published boards with the following structure:

```
https://leadr.gg/games/{game-slug}
```

### Finding Your Game URL

In the LEADR App:

1. Press `g` to open **Games**
2. Select your game
3. The game URL is listed as "URL"
4. Press `4` to copy the game URL

## Board Page URLs

Every published board has a unique URL based on the game URL:

```
https://leadr.gg/games/{game-slug}/boards/{board-slug}
```

**Example:** If your game slug is `space-blaster` and your board slug is `high-scores`, the URL would be:

```
https://leadr.gg/games/space-blaster/boards/high-scores
```

## Short URLs

Each board also has a shorter URL using the board `short_code` for easy sharing. The short URL format is:

```
https://leadr.gg/b/{short-code}
```

Short codes are 6 characters and shown in the board details view.

## Finding Your Board URL

In the LEADR App

1. Press `g` to open **Games**
2. Select your game
3. Press `b` to  open **Boards**
4. Select a board to view its details
5. The board short URL is displayed in the board info
6. Press `5` to copy the board short URL

## Publishing Boards

Boards must be **published** to be visible on the web. By default, new boards are published.

To check or change a board's published status:

1. Navigate to the board in the LEADR app
2. Edit the board (`e`)
3. Toggle the **Published** setting
4. Save your changes

!!! info "Unpublished boards"

    Unpublished boards return a 404 error when accessed via their URL. Use this to hide boards during development or to retire old boards.

## Use Cases

### Share on Social Media

Post your board URL on Twitter, Discord, or other platforms so players can check rankings:

> Check out the current high scores for Space Blaster! https://boards.leadr.gg/space-blaster/high-scores

### Embed on Your Game's Website

Add an embedded leaderboard to your game's website or itch.io page to show off competition.

### Display During Streams

Open the board page in a browser and capture it in OBS or your streaming software to show live rankings during gameplay streams.

### Tournament Results

Share the board URL with tournament participants so they can track standings in real time.

## What's Next

- **[Review Scores](./review-score-flags.md)** - Review &amp; resolve scores flagged by the anti-cheat system
- **[Go live checklist](./go-live-checklist.md)** - Make sure your game is ready to ship

---

_Need Help? The LEADR team and community is always happy to help on the [LEADR Discord](https://discord.gg/RMUukcAxSZ)_
