# Unity SDK Reference

Complete API reference for the LEADR Unity SDK.

## LeadrClient

The main SDK interface, accessed via the `LeadrClient.Instance` singleton.

The SDK creates a persistent GameObject marked with `DontDestroyOnLoad` that survives scene transitions. Access it from anywhere using the static `Instance` property:

```csharp
// The singleton is available everywhere after initialization
var result = await LeadrClient.Instance.GetBoardsAsync();
```

### Initialization Methods

| Method | Description | Returns |
|--------|-------------|---------|
| `Initialize(LeadrSettings settings)` | Initialize the SDK with a settings asset. Call once at game startup | `void` |
| `Initialize(string gameId, string baseUrl = null)` | Initialize the SDK programmatically without a settings asset | `void` |

### Board Methods

| Method | Description | Returns |
|--------|-------------|---------|
| `GetBoardsAsync(int limit = 20)` | Fetch all boards for your game. Returns a paginated list | `Task<LeadrResult<PagedResult<Board>>>` |
| `GetBoardAsync(string boardSlug)` | Fetch a single board by its URL-friendly slug | `Task<LeadrResult<Board>>` |

### Score Methods

| Method | Description | Returns |
|--------|-------------|---------|
| `GetScoresAsync(string boardId, int limit = 20, string sort = null, string aroundScoreId = null, long? aroundScoreValue = null)` | Fetch scores from a board. Use `aroundScoreId` to center results around a specific score, or `aroundScoreValue` to center around a value | `Task<LeadrResult<PagedResult<Score>>>` |
| `GetMyScoresAsync(string boardId, int limit = 20, string sort = null)` | Fetch the current player's scores from a board. Returns multiple scores on RunRuns boards, or a single score on boards with a keep strategy | `Task<LeadrResult<PagedResult<Score>>>` |
| `GetScoreAsync(string scoreId)` | Fetch a single score by its ID | `Task<LeadrResult<Score>>` |
| `SubmitScoreAsync(string boardId, long score, string playerName, string valueDisplay = null, Dictionary<string, object> metadata = null)` | Submit a new score. Returns the created score with its rank | `Task<LeadrResult<Score>>` |

### Session Methods

| Method | Description | Returns |
|--------|-------------|---------|
| `StartSessionAsync()` | Manually start an authentication session. Usually not needed - the SDK handles this automatically on first API call | `Task<LeadrResult<Session>>` |

---

## LeadrSettings

ScriptableObject for SDK configuration. Create via **Create > LEADR > Settings** in the Project panel.

Store the settings asset anywhere in your Assets folder (e.g., `Assets/Settings/LeadrSettings.asset`). Reference it in your initialization script via a serialized field.

### Properties

| Property | Type | Required | Default | Description |
|----------|------|----------|---------|-------------|
| `GameId` | `string` | Yes | `""` | Your game's UUID from the LEADR app (format: `gam_xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`) |
| `BaseUrl` | `string` | No | `https://api.leadrcloud.com` | API endpoint URL. Only change for self-hosted LEADR instances |
| `DebugLogging` | `bool` | No | `false` | Log all API requests and responses to the Unity Console. Sensitive data is automatically redacted |
| `TestMode` | `bool` | No | `false` | Mark all score submissions as test data. Test scores are stored separately from production data |

---

## Models

### Board

Represents a leaderboard configuration.

| Property | Type | Description |
|----------|------|-------------|
| `Id` | `string` | Unique board identifier (format: `brd_xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`) |
| `Slug` | `string` | URL-friendly identifier used for fetching the board (e.g., "weekly-high-scores") |
| `Name` | `string` | Human-readable display name (e.g., "Weekly High Scores") |
| `SortDirection` | `SortDirection` | How scores are ranked: `Ascending` (lowest first) or `Descending` (highest first) |
| `KeepStrategy` | `KeepStrategy` | Which score to keep per player: `First`, `Best`, `Latest`, or `NA` |
| `Type` | `BoardType` | Board type: `RunIdentity`, `RunRuns`, `Counter`, or `Ratio` |
| `Tags` | `List<string>` | Custom tags for filtering and organization |
| `StartsAt` | `DateTime?` | Season start timestamp or null if no season |
| `EndsAt` | `DateTime?` | Season end timestamp or null if no season |
| `RatioConfig` | `RatioConfig` | Configuration for Ratio-type boards (numerator/denominator labels) |

### Score

Represents a submitted score entry.

| Property | Type | Description |
|----------|------|-------------|
| `Id` | `string` | Unique score identifier (format: `scr_xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`) |
| `PlayerName` | `string` | Display name of the player who submitted the score |
| `Value` | `long` | Numeric score value used for ranking |
| `ValueDisplay` | `string` | Formatted display string (e.g., "1:23.456" for a time). Falls back to `Value.ToString()` if empty |
| `Metadata` | `Dictionary<string, object>` | Custom key-value data attached to the score (max 1KB) |
| `Rank` | `int` | Position on the leaderboard (1 = first place) |
| `IsPlaceholder` | `bool` | True if this is a synthetic score inserted for context (e.g., "You would rank here") |
| `IsTest` | `bool` | True if the score was submitted with test mode enabled |
| `CreatedAt` | `DateTime` | Submission timestamp |

### Session

Represents the current authentication session. Most games won't need to interact with this directly.

| Property | Type | Description |
|----------|------|-------------|
| `IdentityId` | `string` | Unique identifier for this device/player |
| `GameId` | `string` | The game this session is authenticated for |
| `AccountId` | `string` | The LEADR account that owns the game |
| `Kind` | `IdentityKind` | Identity type: `Device` (current), `Steam` (planned), or `Custom` (planned) |
| `Platform` | `string` | Detected platform (e.g., "Windows", "Android", "iOS") |

---

## Enums

### BoardType

| Value | Description |
|-------|-------------|
| `RunIdentity` | Standard leaderboard. One score per player, keeps the best/first/latest based on KeepStrategy |
| `RunRuns` | Multiple entries per player allowed. Good for speedrun attempts where players want to track all runs |
| `Counter` | Incrementing value that accumulates over time (e.g., total kills, lifetime earnings) |
| `Ratio` | Win/loss ratio or percentage (e.g., 75% win rate, 3.5 K/D ratio) |

### SortDirection

| Value | Description |
|-------|-------------|
| `Ascending` | Lowest value ranks first. Use for speedruns, golf scores, or "fewer is better" metrics |
| `Descending` | Highest value ranks first. Use for points, high scores, or "more is better" metrics |

### KeepStrategy

| Value | Description |
|-------|-------------|
| `First` | Keep the player's first submission. Good for "first to reach X" achievements |
| `Best` | Keep the player's best score. The most common choice for high score boards |
| `Latest` | Keep the player's most recent submission. Good for daily/weekly challenges |
| `NA` | Not applicable. Used with RunRuns boards where all submissions are kept |

### IdentityKind

| Value | Description |
|-------|-------------|
| `Device` | Device fingerprint identity. The current default for all games |
| `Steam` | Steam user identity. Planned for future release |
| `Custom` | Custom identity provider. Planned for future release |

---

## Result Types

### LeadrResult\<T\>

Generic wrapper for all API responses. Use `IsSuccess` to check the outcome before accessing data.

| Property | Type | Description |
|----------|------|-------------|
| `IsSuccess` | `bool` | True if the operation completed successfully |
| `Data` | `T` | The result data. Only valid when `IsSuccess` is true |
| `Error` | `LeadrError` | Error details. Only valid when `IsSuccess` is false |

```csharp
var result = await LeadrClient.Instance.GetBoardAsync("weekly");

if (result.IsSuccess)
{
    Board board = result.Data;
    Debug.Log($"Board: {board.Name}");
}
else
{
    Debug.LogError($"Error {result.Error.StatusCode}: {result.Error.Message}");
}
```

### LeadrError

Error information when an operation fails.

| Property | Type | Description |
|----------|------|-------------|
| `StatusCode` | `int` | HTTP status code. 0 indicates a network error (no response received) |
| `Code` | `string` | Machine-readable error code (e.g., "not_found", "rate_limited") |
| `Message` | `string` | Human-readable error message suitable for logging or display |

### PagedResult\<T\>

Pagination wrapper for list operations (boards, scores).

| Property | Type | Description |
|----------|------|-------------|
| `Items` | `List<T>` | Items on the current page (Board or Score objects) |
| `Count` | `int` | Number of items on this page |
| `HasNext` | `bool` | True if there are more pages after this one |
| `HasPrev` | `bool` | True if there are pages before this one |

| Method | Description | Returns |
|--------|-------------|---------|
| `NextPageAsync()` | Fetch the next page of results | `Task<LeadrResult<PagedResult<T>>>` |
| `PrevPageAsync()` | Fetch the previous page of results | `Task<LeadrResult<PagedResult<T>>>` |

```csharp
var result = await LeadrClient.Instance.GetScoresAsync(boardId, limit: 10);

if (result.IsSuccess)
{
    var page = result.Data;

    foreach (var score in page.Items)
    {
        Debug.Log($"#{score.Rank} {score.PlayerName}");
    }

    if (page.HasNext)
    {
        var next = await page.NextPageAsync();
        // Process next page...
    }
}
```

---

## UI Components

The SDK includes pre-built UI Toolkit (UIElements) components for common leaderboard interactions. Use them to prototype quickly or as a starting point for custom UI.

### LeadrBoardView

Pre-built leaderboard display component with pagination support.

Add the component to your UI Document hierarchy. Configure it via code or the UI Builder inspector. The component handles loading states, error display, and pagination automatically.

#### Properties

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `Board` | `string` | `""` | Board slug to display (e.g., "weekly-high-scores"). Required |
| `ScoresPerPage` | `int` | `10` | Number of scores to show per page |
| `AutoLoad` | `bool` | `true` | Automatically fetch scores when the component is enabled |
| `ShowPagination` | `bool` | `true` | Show Previous/Next navigation buttons |
| `Title` | `string` | `""` | Custom title text. If empty, uses the board's name |
| `SortOverride` | `string` | `""` | Override the board's default sort direction |
| `State` | `BoardViewState` | `Idle` | Current component state (read-only): Idle, Loading, Loaded, Empty, Error |

#### Methods

| Method | Description | Returns |
|--------|-------------|---------|
| `LoadAsync()` | Fetch scores from the server. Called automatically if `AutoLoad` is true | `Task` |
| `LoadNextPageAsync()` | Fetch the next page of scores | `Task` |
| `LoadPrevPageAsync()` | Fetch the previous page of scores | `Task` |
| `RefreshAsync()` | Reload the current page of scores | `Task` |
| `HighlightScore(string scoreId)` | Visually highlight a specific score (e.g., the player's submission) | `void` |
| `ClearHighlights()` | Remove all score highlights | `void` |

#### Events

| Event | Type | Description |
|-------|------|-------------|
| `ScoreSelected` | `Action<Score>` | Fired when the player clicks/taps a score row |
| `StateChanged` | `Action<BoardViewState>` | Fired when the component state changes |
| `ErrorOccurred` | `Action<LeadrError>` | Fired when an API error occurs |
| `PageLoaded` | `Action<PagedResult<Score>>` | Fired when a page of scores is successfully loaded |

**Responding to events:**

```csharp
public class LeaderboardController : MonoBehaviour
{
    [SerializeField] private LeadrBoardView boardView;

    void OnEnable()
    {
        boardView.ScoreSelected += OnScoreSelected;
        boardView.ErrorOccurred += OnError;
    }

    void OnDisable()
    {
        boardView.ScoreSelected -= OnScoreSelected;
        boardView.ErrorOccurred -= OnError;
    }

    private void OnScoreSelected(Score score)
    {
        Debug.Log($"Player selected: {score.PlayerName}");
    }

    private void OnError(LeadrError error)
    {
        ShowErrorDialog(error.Message);
    }
}
```

### LeadrScoreEntry

Individual score row component. Used internally by LeadrBoardView, but can be used standalone for custom layouts.

#### Properties

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `Score` | `Score` | `null` | Score data to display |
| `ShowRank` | `bool` | `true` | Show the rank number (e.g., "#1") |
| `IsSelected` | `bool` | `false` | Visual selection state |
| `IsHighlighted` | `bool` | `false` | Visual highlight state (e.g., for the current player's score) |

### LeadrScoreSubmitter

Pre-built score submission form with player name input and validation.

Add the component to your game over screen's UI Document. Set the score programmatically using `SetScore()`, and the form handles name input and submission.

#### Properties

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `Board` | `string` | `""` | Board slug to submit to. Required |
| `MinNameLength` | `int` | `1` | Minimum allowed player name length |
| `MaxNameLength` | `int` | `20` | Maximum allowed player name length |
| `ShowScoreInput` | `bool` | `false` | Show a text field for manual score entry. Usually false - set score via `SetScore()` |
| `ClearOnSuccess` | `bool` | `true` | Reset the form after successful submission |
| `PlayerName` | `string` | `""` | Current value of the player name input field |
| `ScoreValue` | `long` | `0` | Current score value to be submitted |
| `ValueDisplay` | `string` | `""` | Formatted display string for the score |
| `Metadata` | `Dictionary<string, object>` | `null` | Custom metadata to attach to the score |
| `IsValid` | `bool` | `false` | Whether the form passes validation (read-only) |
| `State` | `SubmitterState` | `Idle` | Current component state (read-only): Idle, Submitting, Success, Error |

#### Methods

| Method | Description | Returns |
|--------|-------------|---------|
| `SubmitAsync()` | Submit the score to the server | `Task` |
| `ClearForm()` | Reset all fields to their default values | `void` |
| `ResetState()` | Reset the state to Idle (e.g., after displaying an error) | `void` |
| `SetScore(long value, string displayValue = null)` | Set the score value to submit. Call when the player finishes the level | `void` |

#### Events

| Event | Type | Description |
|-------|------|-------------|
| `ScoreSubmitted` | `Action<Score>` | Fired when the score is successfully submitted. Contains the rank |
| `SubmissionFailed` | `Action<LeadrError>` | Fired when submission fails |
| `StateChanged` | `Action<SubmitterState>` | Fired when the form state changes |
| `ValidationChanged` | `Action<bool>` | Fired when form validity changes (e.g., name meets length requirements) |

**Setting the score programmatically** (the typical workflow):

```csharp
public class GameOverController : MonoBehaviour
{
    [SerializeField] private LeadrScoreSubmitter submitter;

    void OnEnable()
    {
        submitter.ScoreSubmitted += OnScoreSubmitted;
        submitter.SubmissionFailed += OnSubmissionFailed;
    }

    void OnDisable()
    {
        submitter.ScoreSubmitted -= OnScoreSubmitted;
        submitter.SubmissionFailed -= OnSubmissionFailed;
    }

    // Call this when the player finishes the level
    public void ShowGameOver(long finalScore)
    {
        submitter.SetScore(finalScore, FormatScore(finalScore));
        gameOverPanel.SetActive(true);
    }

    private void OnScoreSubmitted(Score score)
    {
        Debug.Log($"Submitted! Rank: #{score.Rank}");
        ShowLeaderboardWithHighlight(score.Id);
    }

    private void OnSubmissionFailed(LeadrError error)
    {
        ShowErrorDialog($"Could not submit score: {error.Message}");
    }
}
```

---

_Need Help? The LEADR team and community is always happy to help on the [LEADR Discord](https://discord.gg/RMUukcAxSZ)_
