# Review Score Flags

LEADR's anti-cheat system automatically flags suspicious score submissions. Review and resolve flagged scores to keep your leaderboards fair.

## Prerequisites

- [Download and install the LEADR app](./install.md)
- A LEADR account:
  - [Register](./register.md)
  - [Join a team](./join.md)
- [Create a game](./create-game.md)
- [Create a board](./create-board.md)
- [Get the SDK for your game engine](./get-sdk.md)
- [Use the SDK in your game](./use-sdk.md)
- [Get your game ready to ship](./go-live-checklist.md)

## Viewing Flagged Scores

### Navigate to Score Flags

From the LEADR app dashboard:

1. Go to **Account**
2. Select **Score Flags**

You'll see a list of flagged scores with the following columns:

| Column | Description |
|--------|-------------|
| **Score Event** | Truncated ID of the flagged score |
| **Flag Type** | What triggered the flag |
| **Confidence** | How confident the system is this is a cheat |
| **Status** | Current review status |
| **Created** | When the flag was created |

### Filter by Status

Press `s` to cycle through status filters:

| Status | Color | Description |
|--------|-------|-------------|
| **Pending** | Yellow | Awaiting review |
| **Confirmed Cheat** | Red | Verified as cheating |
| **False Positive** | Green | Verified as legitimate |
| **Dismissed** | Gray | Reviewed but no action taken |
| **All** | - | Show all flags |

### Keyboard Controls

| Key | Action |
|-----|--------|
| `↑`/`↓` or `j`/`k` | Select a flag |
| `Enter` | View flag details |
| `f` | Review/resolve the selected flag |
| `s` | Cycle through status filters |
| `r` | Reload the list |
| `Esc` | Go back |

## Reviewing a Flag

1. Select a flagged score from the list
2. Press `f` to open the review dialog
3. Choose a resolution:

### Resolution Options

**Confirmed Cheat**

Mark the score as verified cheating. The score may be removed from the leaderboard depending on your configuration.

Use this when:

- The score is obviously impossible
- The player is a known cheater
- You have evidence of cheating

**False Positive**

Mark the score as legitimate. The flag is cleared and the score remains on the leaderboard.

Use this when:

- The score is high but achievable
- You know the player is legitimate
- The detection was overly aggressive

**Dismissed**

Acknowledge the flag without taking action. The score remains on the leaderboard.

Use this when:

- You're unsure if it's cheating
- You want to monitor the player before deciding
- The flag is borderline

## Anti-Cheat Tips

### Set Realistic Expectations

Think about what scores are realistically achievable in your game. If your game has a natural maximum score, extremely high scores are easier to identify as cheats.

### Monitor New Players

Pay attention to flags from players with very few scores. A new player immediately topping the leaderboard can be suspicious.

### Review Regularly

Check your flagged scores regularly, especially after launch. Early cheaters can discourage legitimate players from competing.

### Community Reports

If players report suspected cheaters on Discord or social media, cross-reference with your flagged scores to investigate.

See the [Anti-Cheat reference](../reference/anti-cheat.md) for more details on how the anti-cheat system works.

## What's Next

- **[Share your boards online](./board-pages.md)** - See &amp; share the live-updating web pages for your game's boards
- **[Advanced Boards](./advanced-boards.md)** - Learn how to create boards for seasons, tournaments, win-lose percentages, play time, speedruns and more

---

_Need Help? The LEADR team and community is always happy to help on the [LEADR Discord](https://discord.gg/RMUukcAxSZ)_
