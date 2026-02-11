# Godot SDK Reference

Complete API reference for the LEADR Godot SDK.

## LeadrClient

The main SDK interface, accessed via the `Leadr` autoload singleton.

The SDK automatically registers itself as an autoload when you enable the plugin. Access it globally from any script using `Leadr`:

```gdscript
# The singleton is available everywhere
var result := await Leadr.get_boards()
```

### Initialization Methods

| Method | Description | Returns |
|--------|-------------|---------|
| `initialize(settings: LeadrSettings)` | Initialize the SDK with a settings resource. Called automatically if `leadr_settings.tres` exists in `res://addons/leadr/` | `void` |
| `initialize_with_game_id(game_id: String, base_url: String = "", debug_logging: bool = false, test_mode: bool = false)` | Initialize the SDK programmatically without a settings resource | `void` |
| `is_initialized()` | Check if the SDK is ready to make API calls | `bool` |

### Board Methods

| Method | Description | Returns |
|--------|-------------|---------|
| `get_boards(limit: int = 20)` | Fetch all boards for your game. Returns a paginated list | `LeadrResult` with `LeadrPagedResult` containing `LeadrBoard` items |
| `get_board(board_slug: String)` | Fetch a single board by its URL-friendly slug | `LeadrResult` with `LeadrBoard` |

### Score Methods

| Method | Description | Returns |
|--------|-------------|---------|
| `get_scores(board_id: String, limit: int = 20, sort: String = "", around_score_id: String = "", around_score_value: float = 0.0)` | Fetch scores from a board. Use `around_score_id` to center results around a specific score, or `around_score_value` to center around a value | `LeadrResult` with `LeadrPagedResult` containing `LeadrScore` items |
| `get_score(score_id: String)` | Fetch a single score by its ID | `LeadrResult` with `LeadrScore` |
| `submit_score(board_id: String, value: int, player_name: String, value_display: String = "", metadata: Dictionary = {})` | Submit a new score. Returns the created score with its rank | `LeadrResult` with `LeadrScore` |

### Session Methods

| Method | Description | Returns |
|--------|-------------|---------|
| `start_session()` | Manually start an authentication session. Usually not needed - the SDK handles this automatically on first API call | `LeadrResult` with `LeadrSession` |
| `clear_session()` | Clear stored credentials and session. Use to "log out" or reset the device identity | `void` |
| `has_session()` | Check if the SDK has an active authenticated session | `bool` |

---

## LeadrSettings

Configuration resource for the SDK.

Create as a `.tres` file in your project. See [Creating the Settings Resource](../#creating-the-settings-resource) for instructions.

### Properties

| Property | Type | Required | Default | Description |
|----------|------|----------|---------|-------------|
| `game_id` | `String` | Yes | `""` | Your game's UUID from the LEADR app (format: `gam_xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`) |
| `base_url` | `String` | No | `https://api.leadrcloud.com` | API endpoint URL. Only change for self-hosted LEADR instances |
| `debug_logging` | `bool` | No | `false` | Log all API requests and responses to the console. Sensitive data is automatically redacted |
| `test_mode` | `bool` | No | `false` | Mark all score submissions as test data. Test scores are stored separately from production data |

---

## Models

### LeadrBoard

Represents a leaderboard configuration.

| Property | Type | Description |
|----------|------|-------------|
| `id` | `String` | Unique board identifier (format: `brd_xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`) |
| `slug` | `String` | URL-friendly identifier used for fetching the board (e.g., "weekly-high-scores") |
| `name` | `String` | Human-readable display name (e.g., "Weekly High Scores") |
| `sort_direction` | `String` | How scores are ranked: `"ascending"` (lowest first) or `"descending"` (highest first) |
| `keep_strategy` | `String` | Which score to keep per player: `"first"`, `"best"`, `"latest"`, or `"na"` |
| `board_type` | `String` | Board type: `"RUN_IDENTITY"`, `"RUN_RUNS"`, `"COUNTER"`, or `"RATIO"` |
| `tags` | `Array[String]` | Custom tags for filtering and organization |
| `starts_at` | `String` | Season start timestamp (ISO 8601) or empty string if no season |
| `ends_at` | `String` | Season end timestamp (ISO 8601) or empty string if no season |
| `ratio_config` | `Dictionary` | Configuration for RATIO-type boards (numerator/denominator labels) |

### LeadrScore

Represents a submitted score entry.

| Property | Type | Description |
|----------|------|-------------|
| `id` | `String` | Unique score identifier (format: `scr_xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`) |
| `player_name` | `String` | Display name of the player who submitted the score |
| `value` | `int` | Numeric score value used for ranking |
| `value_display` | `String` | Formatted display string (e.g., "1:23.456" for a time). Falls back to `value` if empty |
| `metadata` | `Dictionary` | Custom key-value data attached to the score (max 1KB) |
| `rank` | `int` | Position on the leaderboard (1 = first place) |
| `is_placeholder` | `bool` | True if this is a synthetic score inserted for context (e.g., "You would rank here") |
| `is_test` | `bool` | True if the score was submitted with test mode enabled |
| `created_at` | `String` | Submission timestamp in ISO 8601 format |

#### Helper Methods

| Method | Description | Returns |
|--------|-------------|---------|
| `get_relative_time()` | Get a human-readable relative time (e.g., "2 hours ago", "yesterday") | `String` |

### LeadrSession

Represents the current authentication session. Most games won't need to interact with this directly.

| Property | Type | Description |
|----------|------|-------------|
| `identity_id` | `String` | Unique identifier for this device/player |
| `game_id` | `String` | The game this session is authenticated for |
| `account_id` | `String` | The LEADR account that owns the game |
| `kind` | `String` | Identity type: `"DEVICE"` (current), `"STEAM"` (planned), or `"CUSTOM"` (planned) |
| `display_name` | `String` | Optional display name associated with the identity |
| `test_mode` | `bool` | Whether this session is in test mode |

---

## Enums

### BoardType

| Value | Description |
|-------|-------------|
| `RUN_IDENTITY` | Standard leaderboard. One score per player, keeps the best/first/latest based on keep_strategy |
| `RUN_RUNS` | Multiple entries per player allowed. Good for speedrun attempts where players want to track all runs |
| `COUNTER` | Incrementing value that accumulates over time (e.g., total kills, lifetime earnings) |
| `RATIO` | Win/loss ratio or percentage (e.g., 75% win rate, 3.5 K/D ratio) |

### SortDirection

| Value | Description |
|-------|-------------|
| `ascending` | Lowest value ranks first. Use for speedruns, golf scores, or "fewer is better" metrics |
| `descending` | Highest value ranks first. Use for points, high scores, or "more is better" metrics |

### KeepStrategy

| Value | Description |
|-------|-------------|
| `first` | Keep the player's first submission. Good for "first to reach X" achievements |
| `best` | Keep the player's best score. The most common choice for high score boards |
| `latest` | Keep the player's most recent submission. Good for daily/weekly challenges |
| `na` | Not applicable. Used with RUN_RUNS boards where all submissions are kept |

---

## Result Types

### LeadrResult

Wrapper for all API responses. Use `is_success` to check the outcome before accessing data.

| Property | Type | Description |
|----------|------|-------------|
| `is_success` | `bool` | True if the operation completed successfully |
| `data` | `Variant` | The result data. Type depends on the operation (LeadrBoard, LeadrScore, LeadrPagedResult, etc.) |
| `error` | `LeadrError` | Error details when `is_success` is false |

```gdscript
var result := await Leadr.get_board("weekly")

if result.is_success:
    var board: LeadrBoard = result.data
    print("Board: %s" % board.name)
else:
    print("Error %d: %s" % [result.error.status_code, result.error.message])
```

### LeadrError

Error information when an operation fails.

| Property | Type | Description |
|----------|------|-------------|
| `status_code` | `int` | HTTP status code. 0 indicates a network error (no response received) |
| `code` | `String` | Machine-readable error code (e.g., "not_found", "rate_limited") |
| `message` | `String` | Human-readable error message suitable for logging or display |

### LeadrPagedResult

Pagination wrapper for list operations (boards, scores).

| Property | Type | Description |
|----------|------|-------------|
| `items` | `Array` | Items on the current page (LeadrBoard or LeadrScore objects) |
| `count` | `int` | Number of items on this page |
| `has_next` | `bool` | True if there are more pages after this one |
| `has_prev` | `bool` | True if there are pages before this one |

| Method | Description | Returns |
|--------|-------------|---------|
| `next_page()` | Fetch the next page of results | `LeadrResult` with `LeadrPagedResult` |
| `prev_page()` | Fetch the previous page of results | `LeadrResult` with `LeadrPagedResult` |

```gdscript
var result := await Leadr.get_scores(board_id, 10)

if result.is_success:
    var page: LeadrPagedResult = result.data

    for score in page.items:
        print("#%d %s" % [score.rank, score.player_name])

    if page.has_next:
        var next := await page.next_page()
        # Process next page...
```

---

## UI Components

### LeadrBoardView

The SDK includes pre-built UI components with pagination support for common leaderboard interactions. Use them to prototype quickly or as a starting point for custom UI.

Add the `LeadrBoardView` scene to your UI tree and configure it via the Inspector or code. The component handles loading states, error display, and pagination automatically.

#### Exported Properties

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `board` | `String` | `""` | Board slug to display (e.g., "weekly-high-scores"). Required |
| `scores_per_page` | `int` | `10` | Number of scores to show per page |
| `auto_load` | `bool` | `true` | Automatically fetch scores when the node enters the tree |
| `show_pagination` | `bool` | `true` | Show Previous/Next navigation buttons |
| `title` | `String` | `""` | Custom title text. If empty, uses the board's name |

#### Methods

| Method | Description | Returns |
|--------|-------------|---------|
| `load_scores()` | Fetch scores from the server. Called automatically if `auto_load` is true | `void` |
| `refresh()` | Reload the current page of scores | `void` |
| `clear()` | Remove all displayed scores and reset to empty state | `void` |
| `highlight_score(score_id: String)` | Visually highlight a specific score (e.g., the player's submission) | `void` |

#### Signals

| Signal | Parameters | Description |
|--------|------------|-------------|
| `score_selected` | `score: LeadrScore` | Emitted when the player clicks/taps a score row |
| `state_changed` | `state: String` | Emitted when the component state changes (idle, loading, loaded, error) |
| `error_occurred` | `error: LeadrError` | Emitted when an API error occurs |
| `page_loaded` | `page: LeadrPagedResult` | Emitted when a page of scores is successfully loaded |

### LeadrScoreEntry

Individual score row component. Used internally by LeadrBoardView, but can be used standalone for custom layouts.

#### Exported Properties

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `show_rank` | `bool` | `true` | Show the rank number (e.g., "#1") |
| `show_date` | `bool` | `false` | Show when the score was submitted |
| `is_selected` | `bool` | `false` | Visual selection state |
| `is_highlighted` | `bool` | `false` | Visual highlight state (e.g., for the current player's score) |

### LeadrScoreSubmitter

Pre-built score submission form with player name input and validation.

Add the `LeadrScoreSubmitter` scene to your game over screen. Set the score programmatically, and the form handles name input and submission.

#### Exported Properties

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `board` | `String` | `""` | Board slug to submit to. Required |
| `min_name_length` | `int` | `1` | Minimum allowed player name length |
| `max_name_length` | `int` | `20` | Maximum allowed player name length |
| `show_score_input` | `bool` | `false` | Show a text field for manual score entry. Usually false - set score via code |
| `clear_on_success` | `bool` | `true` | Reset the form after successful submission |

#### Methods

| Method | Description | Returns |
|--------|-------------|---------|
| `set_score(value: int, display: String = "")` | Set the score value to submit. Call this when the player finishes the level | `void` |
| `set_player_name(name: String)` | Pre-fill the player name field | `void` |
| `get_player_name()` | Get the currently entered player name | `String` |
| `clear_form()` | Reset all fields to their default values | `void` |
| `submit()` | Trigger score submission. Usually called by the form's submit button | `void` |

#### Signals

| Signal | Parameters | Description |
|--------|------------|-------------|
| `score_submitted` | `score: LeadrScore` | Emitted when the score is successfully submitted. Contains the rank |
| `submission_failed` | `error: LeadrError` | Emitted when submission fails |
| `state_changed` | `state: String` | Emitted when the form state changes (idle, submitting, success, error) |
| `validation_changed` | `is_valid: bool` | Emitted when form validity changes (e.g., name meets length requirements) |

---

_Need Help? The LEADR team and community is always happy to help on the [LEADR Discord](https://discord.gg/RMUukcAxSZ)_
