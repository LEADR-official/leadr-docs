# Use the LEADR SDK

This guide covers the common patterns for integrating LEADR into your game code. The SDK handles authentication automatically - you just need to configure it and call the API.

## Prerequisites

- [Download and install the LEADR app](./install.md)
- A LEADR account:
  - [Register](./register.md)
  - [Join a team](./join.md)
- [Create a game](./create-game.md)
- [Create a board](./create-board.md)
- [Get the SDK for your game engine](./get-sdk.md)

## Find Your Game ID

You'll need your Game ID to configure the SDK. To find it:

1. Open the LEADR app
2. Press `g` to go to **Games**
3. Select your game
4. Press `y` to copy the Game ID to your clipboard

The Game ID is a UUID that looks like: `gam_a1b2c3d4-e5f6-7890-abcd-ef1234567890`

Keep this handy, you'll need it in a minute.

## Configuration

Before using the SDK in your game code or scenes, you'll need to configure it.

Open your game engine and follow the steps:

=== "Godot"

    The LEADR Godot SDK provides a `LeadrSettings` resource type to manage your configuration:

    1. In the FileSystem dock, right-click and select "+ Create New" and then "Resource..." to open the "Create New Resource" window
    2. Search for "LeadrSettings" to find the resource type
    3. Select "LeadrSettings" from the results and click "Create"
    4. Make sure "Path:" is set to `res://addons/leadr`
    5. Name the file `leadr_settings.tres` and click "Save"

    [Full Godot SDK documentation](../sdks/godot/index.md){ .md-button }

=== "Unity"

    The LEADR Unity SDK provides "LeadrSettings.cs" Mono Script accessible from the create asset menu to manage your configuration:

    1. In the Project panel, right click and select "Create > LEADR > Settings"
    2. You can leave the default name of `LeadrSettings.asset`

    [Full Unity SDK documentation](../sdks/unity/index.md){ .md-button }

### Required Settings

| Setting | Description |
|---------|-------------|
| `game_id` | Your game's UUID from the LEADR app |

### Optional Settings

| Setting | Default | Description |
|---------|---------|-------------|
| `test_mode` | `false` | Store scores created during development and testing separately from live game data |
| `debug_logging` | `false` | Enable verbose logging for development |
| `base_url` | `https://api.leadrcloud.com` | API endpoint (change for self-hosted) |

## Common Operations

All LEADR SDKs provide a standard pattern for interacting with the LEADR API and your boards based off a `Leadr`/`LeadrClient` singleton variable. Exact function names and arguments will vary depending on your SDK. Below is a pseudocode  quick reference:

| Function | Behaviour |
|----------|-----------|
| `await Initialize(settings)` | Before making any API calls, initialize the LEADR client. Handles all authentication and session tokens |
| `await GetBoards(limit: n)` | Fetch the list of `n` boards for your game. Useful if you want to display available boards in your game |
| `await GetBoard(slug: slug)` | Fetch the fetch the details for the board with slug `slug`. Use to retrieve the ID or config for a specific board |
| `await GetScores(board_id: brd_..., limit: n)` | Fetch the top scores for the board with ID `brd_...`. The simplest way to list scores |
| `await GetScores(board_id: brd_..., around_value: x)` | Fetch the scores around value `x` for the board with ID `brd_...`. Useful for showing where a player would rank before their score is even submitted |
| `await GetScores(board_id: brd_..., around_score: scr_...)` | Fetch the scores around score `scr_...` for the board with ID `brd_...`. Useful for showing where a player would rank after their score is submitted |
| `await GetScore(score_id: scr_...)` | Fetch fetch a single score with ID `scr_...` |
| `await SubmitScore(board_id: brd_..., value: x, player_name: name)` | Submit a new score to the board with ID `brd_...` |

## Error Handling

All SDK methods return a `Result` object instead of throwing exceptions:

```
result = await LeadrClient.GetBoard("invalid-slug")

if result.is_success:
    // Use result.data
    board = result.data
else:
    // Handle error
    print("Error:", result.error.message)
    print("Status:", result.error.status_code)
```

Common error codes:

| Status | Meaning |
|--------|---------|
| 400 | Bad request (invalid parameters) |
| 401 | Unauthorized (handled automatically by retry) |
| 404 | Board or score not found |
| 429 | Rate limited (implement backoff in your code) |

## Pagination

The SDKs handle LEADR's cursor-based pagination for you and expose convenient helper functions. Use these to list large numbers of scores, to add "Next" and "Previous" page buttons to leaderboards, or to implement an infinite scroll effect:

```
result = await LeadrClient.GetScores(board_id, limit: 20)

// Get next page
if result.data.has_next:
    next_result = await result.data.NextPage()

// Get previous page
if result.data.has_prev:
    prev_result = await result.data.PrevPage()
```

## Test Mode

Enable test mode in your LEADR SDK config during development so that score submissions are stored separately and don't pollute your live game boards.

!!! warning "Disable before shipping"

    Remember to disable test mode before building/compiling/exporting your game when preparing a release.

## Debug Logging

Enable debug logging during development to see API requests and responses:

!!! warning "Disable before shipping"

    Remember to disable debug logging before building/compiling/exporting your game when preparing a release. It can expose sensitive information and impact performance.

For detailed examples and engine-specific code, see your SDK's documentation:

- [Godot SDK](../sdks/godot/index.md)
- [Unity SDK](../sdks/unity/index.md)
- [REST API](../api/client-api.md)

## What's Next

- **[Advanced Boards](./advanced-boards.md)** - Learn how to create boards for seasons, tournaments, win-lose percentages, play time, speedruns and more
- **[Go live checklist](./go-live-checklist.md)** - Make sure your game is ready to ship

## Need Help?

If you get stuck at any point, the LEADR team and community is always happy to help on the [LEADR Discord](https://discord.gg/RMUukcAxSZ).
