# Advanced Boards

LEADR boards can handle recurring competitions, time-limited tournaments, and complex scoring systems. This guide covers the advanced features beyond basic leaderboards.

## Prerequisites

- [Download and install the LEADR app](./install.md)
- A LEADR account:
  - [Register](./register.md)
  - [Join a team](./join.md)
- [Create a game](./create-game.md)

## Seasonal & Recurring Boards

Use board templates to automatically create recurring leaderboards - perfect for weekly challenges, monthly tournaments, or seasons.

### How Board Templates Work

1. Create a board template with a repeat interval (e.g., "1 month")
2. LEADR automatically creates new boards at each interval
3. Previous boards are archived but remain viewable. This means the scores from past tournaments or seasons are preserved

See the [Board Templates reference](../reference/board-templates.md) for more examples and configuration options.

## Time-Limited Boards

Create one-off tournaments or limited-time events by setting start and end dates on a board.

When creating or editing a board:

- **Starts At**: When the board becomes active and accepts scores
- **Ends At**: When the board closes for new submissions

Players can still view scores after the board ends, but no new submissions are accepted.

**Use cases:**

- Launch week competitions
- Streaming events and tournaments
- Limited-time game modes
- Game jam leaderboards

## Per Player Boards

Per player boards are associated with a players identity and can be used to only accept a single score per player. The score that is kept depends on the configured `keep_strategy` for the board:

- **Best** - Uses the board `sort_direction` to only keep a single best score submitted by each player. Worse scores are discarded 
- **First** - Only stores the first ever score submitted for each player. Any subsequent scores are discarded
- **Latest** - Always stores new scores submitted for a player, but discards any existing scores


## Counter Boards

Counter boards track cumulative totals that increment over time, rather than individual high scores. Counters are great for tracking lifetime stats, or for using in ratio boards.

**Examples:**

- Total wins
- Games played
- Enemies defeated
- Distance traveled (lifetime)
- Play time (minutes)

When submitting to a Counter board, each submission is a `delta` that adds to the player's total rather than replacing their score.

## Ratio Boards

Ratio boards calculate a percentage or ratio between two Counter boards.

**Setup:**

1. Create two Counter boards (e.g., "Wins" and "Games Played")
2. Create a Ratio board
3. Set the numerator board (e.g., "Wins")
4. Set the denominator board (e.g., "Games Played")

LEADR automatically calculates and displays the ratio (e.g., 75% win rate).

**Use cases:**

- Win/loss percentages
- Accuracy rates
- Completion percentages
- Kill/death ratios

The "Display" setting for ratio boards determines whether the output values are handled as percentages (e.g. 50%) or simple ratios (e.g. 0.5).

## Custom Units

Set a custom unit label to display scores in context:

| Unit | Example Display |
|------|-----------------|
| `points` | 1,500 points |
| `seconds` | 45.23 seconds |
| `meters` | 1,234 meters |

You can also use the `value_display` field when submitting scores via the SDK to provide custom formatted values (e.g., "1:23.45" for a time).

## Reference

- See the [Boards reference](../reference/boards.md) for complete configuration options.
- See the [Board Templates reference](../reference/board-templates.md) for template naming and repeat intervals.

## What's Next

- **[Get your SDK](./get-sdk.md)** - Get and configure the LEADR SDK for your game engine

---

_Need Help? The LEADR team and community is always happy to help on the [LEADR Discord](https://discord.gg/RMUukcAxSZ)_
