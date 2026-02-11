# Godot SDK

The LEADR Godot SDK is a native GDScript plugin that lets you integrate LEADR leaderboards directly into your Godot Engine game. Install the plugin, configure your Game ID, and submit scores with a few lines of GDScript.

[View on GitHub](https://github.com/LEADR-official/leadr-sdk-godot){:target="_blank", .md-button }

## Prerequisites

- [Download and install the LEADR app](../../guides/install.md)
- A LEADR account:
    - [Register](../../guides/register.md)
    - [Join a team](../../guides/join.md)
- [Create a game](../../guides/create-game.md)
- [Create a board](../../guides/create-board.md)
- Godot Engine 4.x installed

## Installation

1. Go to the [LEADR Godot SDK releases page](https://github.com/LEADR-official/leadr-sdk-godot/releases){:target="_blank"}
2. Download the latest `.zip` file and extract it to a temporary location
3. Copy the `leadr` folder from the extracted `addons` directory into your Godot project's `addons` directory
4. Open your Godot project
5. Go to **Project > Project Settings > Plugins**
6. Find "LEADR" in the list and ensure "Enabled" is set to "☑️ On"

![The "Installed Plugins" dialog in the Godot editor](../../assets/images/godot_enable_plugin.png 'The "Installed Plugins" dialog in the Godot editor')

## Configuration

### Creating the Settings Resource

1. In the **FileSystem** dock, right-click on `res://addons/leadr/`
2. Select "+ Create New" and then "Resource..." to open the "Create New Resource" dialog
3. In the dialog, search for "LeadrSettings"
4. Select **LeadrSettings** and click **Create**
5. Save the file as `leadr_settings.tres`

![The Create New Resource menu](../../assets/images/godot_create_settings_1.png 'The Create New Resource menu')
![The Create New Resource dialog](../../assets/images/godot_create_settings_2.png 'The Create New Resource dialog')

### Settings Properties

| Setting | Required | Default | Description |
|---------|----------|---------|-------------|
| `game_id` | Yes | — | Your game's UUID from the LEADR app (e.g., `gam_a1b2c3d4-...`) |
| `base_url` | No | `https://api.leadrcloud.com` | API endpoint. Change only for self-hosted LEADR instances |
| `debug_logging` | No | `false` | Log all API requests and responses to the console |
| `test_mode` | No | `false` | Mark all score submissions as test data |

![LeadrSettings in the Inspector panel](../../assets/images/godot_configure_settings.png 'LeadrSettings in the Inspector panel')

### Test Mode

During development, enable test mode to keep your development scores separate from real player data.

To enable test mode, select your `leadr_settings.tres` resource and check the **Test Mode** box:

When test mode is enabled:

- All submitted scores are marked with `is_test = true`
- Test scores appear on a separate "Mode: Test" view for that board in the LEADR app
- Test scores don't affect your live leaderboards

!!! warning "Disable before shipping"
    Remember to disable test mode before exporting your game for release. Test scores won't appear on your public leaderboards.

### Debug Logging

Enable debug logging to see detailed API request/response information in the Godot output panel.

To enable, select your `leadr_settings.tres` resource and check the **Debug Logging** box.

Example output:

```
[LEADR] -> POST https://api.leadrcloud.com/v1/client/scores
[LEADR]    Headers: {Authorization: Bearer [REDACTED], Content-Type: application/json}
[LEADR]    Body: {"board_id": "brd_...", "value": 5000, "player_name": "Alex"}
[LEADR] <- 201 (145ms)
[LEADR]    Body: {"id": "scr_...", "rank": 42, ...}
```

Sensitive data like access tokens and device fingerprints are automatically redacted in logs.

!!! warning "Disable before shipping"
    Debug logging can expose sensitive information and impact performance. Disable it before exporting your game for release.

## Enabling the Autoload

The plugin automatically registers `Leadr` as an autoload singleton when you enable the plugin. You can access it from any script:

```gdscript
# Check if the SDK is ready
if Leadr.is_initialized():
    print("LEADR is ready!")
```

If the autoload isn't appearing, verify the autoload is correctly configured in **Project Settings** > **Globals**:

![The Autoload tab in the Project Settings dialog](../../assets/images/godot_autoload.png 'The Autoload tab in the Project Settings dialog')

Also check:

1. The plugin is enabled in **Project > Project Settings > Plugins**
2. Your `leadr_settings.tres` file exists in `res://addons/leadr/`
3. The `game_id` field is set in your settings resource

## Your First API Call

### Verifying Setup

Create a simple test script to verify everything is connected:

```gdscript
extends Node

func _ready() -> void:
    # Check the SDK initialized correctly
    if not Leadr.is_initialized():
        push_error("LEADR SDK not initialized - check your settings")
        return

    # Fetch your game's boards to verify the connection
    var result := await Leadr.get_boards()
    if result.is_success:
        print("Connected to LEADR! Found %d boards:" % result.data.items.size())
        for board in result.data.items:
            print("  - %s (%s)" % [board.name, board.slug])
    else:
        push_error("Failed to connect: %s" % result.error.message)
```

Run your scene. If you see your boards listed in the output, you're ready to submit scores.

### Submitting a Score

Here's how to submit a score when a player finishes a level:

```gdscript
func _on_level_complete(final_score: int, player_name: String) -> void:
    var board_id := "brd_your-board-id-here"

    var result := await Leadr.submit_score(board_id, final_score, player_name)

    if result.is_success:
        var score: LeadrScore = result.data
        print("Score submitted! You ranked #%d" % score.rank)
    else:
        push_error("Failed to submit score: %s" % result.error.message)
```

For scores that need custom display formatting (e.g. speedrun times), use the `value_display` parameter when submitting the score:

```gdscript
# Submit a speedrun time (stored as milliseconds, displayed as mm:ss.mmm)
func _on_run_complete(elapsed_ms: int, player_name: String) -> void:
    var display := format_time(elapsed_ms)  # e.g., "1:23.456"

    var result := await Leadr.submit_score(
        board_id,
        elapsed_ms,
        player_name,
        display  # Shows "1:23.456" on the leaderboard instead of "83456"
    )
```

You can also attach custom metadata to track additional context:

```gdscript
# Include metadata about the run
var metadata := {
    "level": "forest_temple",
    "difficulty": "hard",
    "character": "knight"
}

var result := await Leadr.submit_score(
    board_id,
    final_score,
    player_name,
    "",  # No custom display
    metadata
)
```

## Working with Leaderboards

### Fetching Boards

Retrieve all boards for your game to display a board selection menu:

```gdscript
func load_board_list() -> void:
    var result := await Leadr.get_boards(50)  # Get up to 50 boards

    if result.is_success:
        for board in result.data.items:
            print("%s - %s" % [board.name, board.slug])
```

Or fetch a specific board by its slug to get its ID and configuration:

```gdscript
func get_weekly_board() -> LeadrBoard:
    var result := await Leadr.get_board("weekly-high-scores")

    if result.is_success:
        return result.data
    return null
```

### Fetching Scores

**Get the top scores** to display a leaderboard:

```gdscript
func show_top_scores(board_id: String) -> void:
    var result := await Leadr.get_scores(board_id, 10)

    if result.is_success:
        for score in result.data.items:
            print("#%d %s - %s" % [score.rank, score.player_name, score.value_display])
```

**Show where a player would rank** before or while a score is submitted. This is useful for immediately showing "You placed be #47!" on a game over screen:

```gdscript
func show_potential_rank(board_id: String, player_score: int) -> void:
    # Fetch scores around the player's value
    var result := await Leadr.get_scores(board_id, 5, "", "", float(player_score))

    if result.is_success:
        print("Scores around your result:")
        for score in result.data.items:
            print("#%d %s - %d" % [score.rank, score.player_name, score.value])
```

**Show context around a submitted score** so players can see other scores around theirs:

```gdscript
func show_score_context(board_id: String, submitted_score: LeadrScore) -> void:
    # Fetch scores around the player's submitted score
    var result := await Leadr.get_scores(board_id, 5, "", submitted_score.id, 0.0)

    if result.is_success:
        for score in result.data.items:
            var marker := " <-- YOU" if score.id == submitted_score.id else ""
            print("#%d %s - %d%s" % [score.rank, score.player_name, score.value, marker])
```

### Pagination

For leaderboards with many entries, use the `next_page()` & `prev_page()` pagination helper functions to load scores in chunks:

```gdscript
var current_page: LeadrPagedResult

func load_first_page(board_id: String) -> void:
    var result := await Leadr.get_scores(board_id, 20)
    if result.is_success:
        current_page = result.data
        display_scores(current_page.items)
        update_nav_buttons()

func _on_next_pressed() -> void:
    if current_page and current_page.has_next:
        var result := await current_page.next_page()
        if result.is_success:
            current_page = result.data
            display_scores(current_page.items)
            update_nav_buttons()

func _on_prev_pressed() -> void:
    if current_page and current_page.has_prev:
        var result := await current_page.prev_page()
        if result.is_success:
            current_page = result.data
            display_scores(current_page.items)
            update_nav_buttons()

func update_nav_buttons() -> void:
    $PrevButton.disabled = not current_page.has_prev
    $NextButton.disabled = not current_page.has_next
```

## Error Handling

All SDK methods return a `LeadrResult` object instead of throwing exceptions. Always check `is_success` before accessing the data:

```gdscript
var result := await Leadr.submit_score(board_id, score, name)

if result.is_success:
    # Safe to access result.data
    var score: LeadrScore = result.data
    show_success_screen(score.rank)
else:
    # Access error details via result.error
    var error: LeadrError = result.error
    match error.status_code:
        0:
            show_error("No internet connection")
        429:
            show_error("Too many requests - please wait")
        _:
            show_error("Error: %s" % error.message)
```

### Common Error Codes

| Status | Code | Meaning |
|--------|------|---------|
| 0 | `network_error` | No internet connection or request timed out |
| 400 | `bad_request` | Invalid parameters (check board_id format, player_name length) |
| 401 | `unauthorized` | Authentication failed (SDK usually retries automatically) |
| 404 | `not_found` | Board or score doesn't exist (check IDs) |
| 429 | `rate_limited` | Too many requests - implement retry with backoff |

## Using UI Components

The SDK includes pre-built UI components for common leaderboard interactions. Use them to prototype quickly or as a starting point for custom UI.

See [UI components reference](./reference#ui-components) for more information.

!!! info "When to use built-in components"
    The built-in components are great for quick integration and testing. For production games with custom art styles, you'll likely want to build your own UI that calls the SDK API directly.

## Troubleshooting

### Common Issues

| Issue | Solution |
|-------|----------|
| "Game ID not found" | Verify your `game_id` in settings matches the ID shown in the LEADR app. The format should be `gam_xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx` |
| "Network error" | Check your internet connection. Check the "Base URL" value in `leadr_settings.tres` is `https://api.leadrcloud.com`. If using a firewall, ensure `api.leadrcloud.com` is allowed |
| Scores not appearing | Check if test mode is enabled - test scores appear on a separate board. Also verify you're using the correct board `id` and/or `slug` |
| Plugin not loading | Ensure the addon is in `res://addons/leadr/` and enabled in Project Settings > Plugins |
| "Autoload not found" | Restart Godot after enabling the plugin. The `Leadr` autoload should appear in Project Settings > Autoload |

### FAQ

**How do I reset the device identity?**

Delete the credentials file at `user://leadr_credentials.cfg`. The SDK will create a new device identity on the next request.

**Can I use custom player IDs instead of device fingerprinting?**

Not yet. Custom identity providers (Steam, Epic, custom auth) are on [the roadmap](./../../roadmap.md). For now, the SDK uses device fingerprinting to identify returning players.

**How do I handle offline play?**

Built-in offline support is coming soon but isn't included in the SDK yet. For games that need it, queue scores locally (e.g., in a JSON file) and submit them when connectivity is restored.

**What Godot versions are supported?**

The SDK requires Godot 4.x. It's tested with Godot 4.2 and later.

## Next Steps

- **[Godot SDK Reference](reference.md)** - Complete documentation for all classes and methods
- **[GitHub Repository](https://github.com/LEADR-official/leadr-sdk-godot){:target="_blank"}** - Source code, issues, and releases
- **[Advanced Boards Guide](../../guides/advanced-boards.md)** - Get the most out of LEADR's board functionality with counters, ratio boards, seasons and more

---

_Need Help? The LEADR team and community is always happy to help on the [LEADR Discord](https://discord.gg/RMUukcAxSZ)_
