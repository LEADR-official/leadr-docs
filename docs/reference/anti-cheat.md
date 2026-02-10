# Anti-Cheat System

LEADR's anti-cheat system automatically detects and flags suspicious score submissions. When enabled on a game, every score submission is analyzed before being accepted.

## Overview

The anti-cheat system works in three stages:

1. **Detection**: Each score submission is checked against multiple detection rules
2. **Action**: Based on the check results, the score is accepted, flagged, or rejected
3. **Review**: Flagged scores appear in the LEADR app for manual review

Anti-cheat is **enabled by default** for new games. You can toggle it in the game settings.

## Detection Types

LEADR checks for the following suspicious behaviors:

| Flag Type | Description | Default Action |
|-----------|-------------|----------------|
| **Rate Limit** | Player exceeds submission rate limit for the hour | Reject |
| **Duplicate** | Exact same score value submitted within detection window | Flag |
| **Velocity** | Submissions less than 2 seconds apart | Flag |

## Confidence Levels

Each detection has a confidence level that determines the action taken:

| Confidence | Action | Description |
|------------|--------|-------------|
| **Low** | Accept | Score is logged but accepted without flagging |
| **Medium** | Flag | Score is accepted but flagged for manual review |
| **High** | Reject | Score submission is rejected immediately |

## Flag Status

Flagged scores have one of these statuses:

| Status | Description |
|--------|-------------|
| **Pending** | Flag has not been reviewed yet, score is visible in board & rankings |
| **Confirmed Cheat** | Admin confirmed the score is cheating, and score is removed from board & rankings |
| **False Positive** | Admin confirmed the score is legitimate, and score remains in board & rankings |
| **Dismissed** | Admin reviewed but made no determination, and score remains in board & rankings |

## Rate Limits

Rate limits are per-player, per-board, within a sliding 1-hour window. The exact limits depend on the player's trust tier and can be configured.

When a player exceeds the rate limit, their submission is **rejected** (not flagged). This prevents spam attacks from flooding your leaderboards.

## Reviewing Flags

Flagged scores appear in the LEADR app under **Games** > your game > **Flags**. From there you can:

1. View flag details (type, confidence, score data)
2. Mark as **Confirmed Cheat** to remove the score
3. Mark as **False Positive** to clear the flag
4. **Dismiss** to acknowledge without action

See [Review Score Flags](../guides/review-score-flags.md) for a step-by-step guide.

## Best Practices

### Set Realistic Expectations

Think about what scores are realistically achievable in your game. This helps you identify obvious cheats and train LEADR's detection over time.

### Review Regularly

Check flagged scores regularly, especially after launch. Early cheaters can discourage legitimate players from competing.

### Monitor New Players

Pay attention to flags from players with very few scores. A new player immediately topping the leaderboard can be suspicious.

### Use Test Mode During Development

Enable **test mode** in your SDK config during development so test submissions don't affect your anti-cheat baseline.

## Improvements

The LEADR anti-cheat system is something we are excited to keep improving and for this your feedback is very helpful. We have lots of planned improvements that will make the anti-cheat system even better but your input helps us to prioritise and have new ideas.

If there's something you don't like, something more you need, something that doesn't work as expected, or you just have an idea you'd like to share, please message us on [Discord](https://discord.gg/RMUukcAxSZ){:target="_blank"} or [drop us an email](mailto:hello@leadr.gg).
