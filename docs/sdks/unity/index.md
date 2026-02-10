# Unity SDK

The LEADR Unity SDK is a native C# package that lets you integrate LEADR leaderboards directly into your Unity game. Import the package, configure your Game ID, and submit scores with a few lines of C#.

[View on GitHub](https://github.com/LEADR-official/leadr-sdk-unity){:target="_blank", .md-button }

## Prerequisites

- [Download and install the LEADR app](../../guides/install.md)
- A LEADR account:
    - [Register](../../guides/register.md)
    - [Join a team](../../guides/join.md)
- [Create a game](../../guides/create-game.md)
- [Create a board](../../guides/create-board.md)
- Unity 2020.3 or later installed

## Installation

1. In Unity, open **Window > Package Manager**
2. Click the **+** button in the top-left corner
3. Select **Add package from git URL...**
4. Enter: `https://github.com/LEADR-Official/leadr-sdk-unity.git?path=Packages/com.leadr.sdk`
5. Click **Add** and wait for the import to complete

![assets/images/placeholder.png](../../assets/images/placeholder.png)

## Configuration

### Creating the Settings Asset

1. In the **Project** panel, right-click in your desired folder (e.g., `Assets/Settings/`)
2. Select **Create > LEADR > Settings**
3. Name the asset `LeadrSettings` (or any name you prefer)
4. Select the asset to configure it in the Inspector

![assets/images/placeholder.png](../../assets/images/placeholder.png)

### Settings Properties

| Setting | Required | Default | Description |
|---------|----------|---------|-------------|
| `GameId` | Yes | — | Your game's UUID from the LEADR app (e.g., `gam_a1b2c3d4-...`) |
| `BaseUrl` | No | `https://api.leadrcloud.com` | API endpoint. Change only for self-hosted LEADR instances |
| `DebugLogging` | No | `false` | Log all API requests and responses to the Console |
| `TestMode` | No | `false` | Mark all score submissions as test data |

### Initializing the Client

The SDK uses a singleton pattern. Initialize it once, typically in your game's startup script:

```csharp
using Leadr;
using UnityEngine;

public class GameManager : MonoBehaviour
{
    [SerializeField] private LeadrSettings settings;

    void Awake()
    {
        LeadrClient.Instance.Initialize(settings);
    }
}
```

The `LeadrClient.Instance` automatically creates a persistent GameObject that survives scene loads.

## Your First API Call

### Verifying Setup

Create a simple test script to verify everything is connected:

```csharp
using Leadr;
using UnityEngine;

public class LeadrTest : MonoBehaviour
{
    [SerializeField] private LeadrSettings settings;

    async void Start()
    {
        LeadrClient.Instance.Initialize(settings);

        // Fetch your game's boards to verify the connection
        var result = await LeadrClient.Instance.GetBoardsAsync();

        if (result.IsSuccess)
        {
            Debug.Log($"Connected to LEADR! Found {result.Data.Items.Count} boards:");
            foreach (var board in result.Data.Items)
            {
                Debug.Log($"  - {board.Name} ({board.Slug})");
            }
        }
        else
        {
            Debug.LogError($"Failed to connect: {result.Error.Message}");
        }
    }
}
```

Enter Play mode. If you see your boards listed in the Console, you're ready to submit scores.

### Submitting a Score

Here's how to submit a score when a player finishes a level:

```csharp
public async void OnLevelComplete(long finalScore, string playerName)
{
    var boardId = "brd_your-board-id-here";

    var result = await LeadrClient.Instance.SubmitScoreAsync(
        boardId,
        finalScore,
        playerName
    );

    if (result.IsSuccess)
    {
        Debug.Log($"Score submitted! You ranked #{result.Data.Rank}");
    }
    else
    {
        Debug.LogError($"Failed to submit score: {result.Error.Message}");
    }
}
```

For speedrun times or other scores that need custom formatting, use the `valueDisplay` parameter:

```csharp
// Submit a speedrun time (stored as milliseconds, displayed as mm:ss.mmm)
public async void OnRunComplete(long elapsedMs, string playerName)
{
    var display = FormatTime(elapsedMs);  // e.g., "1:23.456"

    var result = await LeadrClient.Instance.SubmitScoreAsync(
        boardId,
        elapsedMs,
        playerName,
        display  // Shows "1:23.456" on the leaderboard instead of "83456"
    );
}
```

You can also attach custom metadata to track additional context:

```csharp
// Include metadata about the run
var metadata = new Dictionary<string, object>
{
    { "level", "forest_temple" },
    { "difficulty", "hard" },
    { "character", "knight" }
};

var result = await LeadrClient.Instance.SubmitScoreAsync(
    boardId,
    finalScore,
    playerName,
    null,  // No custom display
    metadata
);
```

## Working with Leaderboards

### Fetching Boards

Retrieve all boards for your game to display a board selection menu:

```csharp
public async void LoadBoardList()
{
    var result = await LeadrClient.Instance.GetBoardsAsync(limit: 50);

    if (result.IsSuccess)
    {
        foreach (var board in result.Data.Items)
        {
            Debug.Log($"{board.Name} - {board.Slug}");
        }
    }
}
```

Or fetch a specific board by its slug to get its ID and configuration:

```csharp
public async Task<Board> GetWeeklyBoard()
{
    var result = await LeadrClient.Instance.GetBoardAsync("weekly-high-scores");

    if (result.IsSuccess)
    {
        return result.Data;
    }
    return null;
}
```

### Fetching Scores

**Get the top scores** to display a leaderboard:

```csharp
public async void ShowTopScores(string boardId)
{
    var result = await LeadrClient.Instance.GetScoresAsync(boardId, limit: 10);

    if (result.IsSuccess)
    {
        foreach (var score in result.Data.Items)
        {
            Debug.Log($"#{score.Rank} {score.PlayerName} - {score.ValueDisplay}");
        }
    }
}
```

**Show where a player would rank** before they submit. This is useful for showing "You would be #47!" on a game over screen:

```csharp
public async void ShowPotentialRank(string boardId, long playerScore)
{
    // Fetch scores around the player's value
    var result = await LeadrClient.Instance.GetScoresAsync(
        boardId,
        limit: 5,
        aroundScoreValue: playerScore
    );

    if (result.IsSuccess)
    {
        Debug.Log("Scores around your result:");
        foreach (var score in result.Data.Items)
        {
            Debug.Log($"#{score.Rank} {score.PlayerName} - {score.Value}");
        }
    }
}
```

**Show context around a submitted score** so players can see who they beat:

```csharp
public async void ShowScoreContext(string boardId, Score submittedScore)
{
    // Fetch scores around the player's submitted score
    var result = await LeadrClient.Instance.GetScoresAsync(
        boardId,
        limit: 5,
        aroundScoreId: submittedScore.Id
    );

    if (result.IsSuccess)
    {
        foreach (var score in result.Data.Items)
        {
            var marker = score.Id == submittedScore.Id ? " <-- YOU" : "";
            Debug.Log($"#{score.Rank} {score.PlayerName} - {score.Value}{marker}");
        }
    }
}
```

### Pagination

For leaderboards with many entries, use pagination to load scores in chunks:

```csharp
private PagedResult<Score> currentPage;

public async void LoadFirstPage(string boardId)
{
    var result = await LeadrClient.Instance.GetScoresAsync(boardId, limit: 20);

    if (result.IsSuccess)
    {
        currentPage = result.Data;
        DisplayScores(currentPage.Items);
        UpdateNavButtons();
    }
}

public async void OnNextPressed()
{
    if (currentPage != null && currentPage.HasNext)
    {
        var result = await currentPage.NextPageAsync();

        if (result.IsSuccess)
        {
            currentPage = result.Data;
            DisplayScores(currentPage.Items);
            UpdateNavButtons();
        }
    }
}

public async void OnPrevPressed()
{
    if (currentPage != null && currentPage.HasPrev)
    {
        var result = await currentPage.PrevPageAsync();

        if (result.IsSuccess)
        {
            currentPage = result.Data;
            DisplayScores(currentPage.Items);
            UpdateNavButtons();
        }
    }
}

private void UpdateNavButtons()
{
    prevButton.interactable = currentPage.HasPrev;
    nextButton.interactable = currentPage.HasNext;
}
```

## Using UI Components

The SDK includes pre-built UI Toolkit (UIElements) components for common leaderboard interactions. Use them to prototype quickly or as a starting point for custom UI.

!!! info "UI Toolkit vs uGUI"
    The built-in components use Unity's UI Toolkit system. If your game uses the legacy uGUI (Canvas-based) system, you can still use the SDK API directly to build your own UI, or check the samples for a Canvas-based example.

### LeadrBoardView

A complete leaderboard display with pagination. Add it to your UI Document.

![assets/images/placeholder.png](../../assets/images/placeholder.png)

**Key properties:**

| Property | Description |
|----------|-------------|
| `Board` | The board slug to display (e.g., "weekly-high-scores") |
| `ScoresPerPage` | Number of scores per page (default: 10) |
| `AutoLoad` | Automatically load scores when enabled |
| `ShowPagination` | Show Previous/Next navigation buttons |

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

### LeadrScoreSubmitter

A form for players to enter their name and submit a score. Typically shown on a game over screen.

![assets/images/placeholder.png](../../assets/images/placeholder.png)

**Key properties:**

| Property | Description |
|----------|-------------|
| `Board` | The board slug to submit to |
| `MinNameLength` | Minimum player name length (default: 1) |
| `MaxNameLength` | Maximum player name length (default: 20) |
| `ClearOnSuccess` | Reset the form after successful submission |

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

## Error Handling

All SDK methods return a `LeadrResult<T>` object instead of throwing exceptions. Always check `IsSuccess` before accessing the data:

```csharp
var result = await LeadrClient.Instance.SubmitScoreAsync(boardId, score, name);

if (result.IsSuccess)
{
    // Safe to access result.Data
    Score score = result.Data;
    ShowSuccessScreen(score.Rank);
}
else
{
    // Access error details via result.Error
    LeadrError error = result.Error;

    switch (error.StatusCode)
    {
        case 0:
            ShowError("No internet connection");
            break;
        case 429:
            ShowError("Too many requests - please wait");
            break;
        default:
            ShowError($"Error: {error.Message}");
            break;
    }
}
```

### Common Error Codes

| Status | Code | Meaning |
|--------|------|---------|
| 0 | `network_error` | No internet connection or request timed out |
| 400 | `bad_request` | Invalid parameters (check boardId format, playerName length) |
| 401 | `unauthorized` | Authentication failed (SDK usually retries automatically) |
| 404 | `not_found` | Board or score doesn't exist (check IDs) |
| 429 | `rate_limited` | Too many requests - implement retry with backoff |

## Test Mode

During development, enable test mode to keep your development scores separate from real player data.

To enable test mode, select your LeadrSettings asset and check the **Test Mode** box in the Inspector:

![assets/images/placeholder.png](../../assets/images/placeholder.png)

When test mode is enabled:

- All submitted scores are marked with `IsTest = true`
- Test scores appear on a separate "Test" leaderboard in the LEADR app
- Test scores don't affect your live leaderboards

!!! warning "Disable before shipping"
    Remember to disable test mode before building your game for release. Test scores won't appear on your public leaderboards.

## Debug Logging

Enable debug logging to see detailed API request/response information in the Unity Console.

To enable, select your LeadrSettings asset and check the **Debug Logging** box in the Inspector.

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
    Debug logging can expose sensitive information and impact performance. Disable it before building your game for release.

## Troubleshooting

### Common Issues

| Issue | Solution |
|-------|----------|
| "Game ID not found" | Verify your `GameId` in the settings asset matches the ID shown in the LEADR app. The format should be `gam_xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx` |
| "Network error" | Check your internet connection. If using a firewall, ensure `api.leadrcloud.com` is allowed |
| Scores not appearing | Check if test mode is enabled - test scores appear on a separate board. Also verify you're using the correct `boardId` |
| Package not importing | Verify the git URL is correct and your Unity version is 2020.3 or later. Check the Console for import errors |
| NullReferenceException on LeadrClient.Instance | Make sure you call `Initialize()` with a valid settings asset before making API calls |

### FAQ

**How do I reset the device identity?**

Call `PlayerPrefs.DeleteAll()` or delete the LEADR-specific keys from PlayerPrefs. The SDK will create a new device identity on the next request.

**Can I use custom player IDs instead of device fingerprinting?**

Not yet. Custom identity providers (Steam, Epic, custom auth) are on the roadmap. For now, the SDK uses device fingerprinting to identify returning players.

**How do I handle offline play?**

Built-in offline support is coming soon but isn't included in the SDK yet. For games that need it, queue scores locally (e.g., using PlayerPrefs or a local file) and submit them when connectivity is restored.

**Which platforms are supported?**

The SDK supports all major Unity platforms: Windows, Mac, Linux, Android, iOS, WebGL, and consoles. Platform detection is automatic.

**Does the SDK support IL2CPP?**

Yes, the SDK is fully compatible with IL2CPP builds.

## Next Steps

- **[Unity SDK Reference](reference.md)** - Complete documentation for all classes and methods
- **[GitHub Repository](https://github.com/LEADR-official/leadr-sdk-unity){:target="_blank"}** - Source code, issues, and releases
- **[Advanced Boards Guide](../../guides/advanced-boards.md)** - Get the most out of LEADR's board functionality with counters, ratio boards, seasons and more

---

_Need Help? The LEADR team and community is always happy to help on the [LEADR Discord](https://discord.gg/RMUukcAxSZ)_
