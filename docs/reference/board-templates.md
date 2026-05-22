# Board Templates

Board templates let you automatically create recurring leaderboards on a schedule. Perfect for weekly challenges, monthly tournaments, or seasonal competitions.

When a template is active, LEADR automatically creates new boards at each interval. Previous boards are archived but remain viewable, preserving historical rankings.

## Template ID

Each template has a unique identifier in the format `tpl_<uuid>`, for example: `tpl_a1b2c3d4-e5f6-7890-abcd-ef1234567890`.

## Fields

| Field | Required | Example | Default | Description |
|-------|----------|---------|---------|-------------|
| **Name** | Yes | `Monthly Challenge Boards` | - | Template name (used as fallback for board names) |
| **Series** | No | `monthly-challenge` | None | Identifier for sequential numbering (e.g., "weekly", "season") |
| **Slug** | No | `monthly-challenge` | None | URL-friendly identifier for boards created from this template |
| **Name Template** | No | `{month_short} Challenge` | None | Template string with placeholders for dynamic board names |
| **Repeat Interval** | Yes | `1 week` | - | How often to create boards (see format below) |
| **Next Run** | Yes | `2026-06-15 19:00` | - | Next scheduled date and time (in UTC) to create a board from this template |
| **Board Type** | No | - | Per Player | Type of boards to create |
| **Sort Direction** | No | - | Descending | Sort direction for boards |
| **Keep Strategy** | No | - | Best | Keep strategy for Per Player boards |
| **Icon** | No | `fa-trophy` | fa-crown | FontAwesome icon for boards |
| **Unit** | No | `points` | None | Score unit label |
| **Starts At** | No | `2026-01-01T00:00:00Z` | None | Start time for created boards |
| **Ends At** | No | `2026-01-07T23:59:59Z` | None | End time for created boards |
| **Tags** | No | `monthly, challenge` | None | Tags for created boards |
| **Active** | Yes | - | - | Whether the template is currently active |
| **Published** | No | - | Yes | Whether created boards should be published |

## Repeat Interval Format

The repeat interval uses PostgreSQL-style interval syntax. Valid formats:

| Interval | Example |
|----------|---------|
| Hours | `1 hour`, `12 hours` |
| Days | `1 day`, `5 days`, `13 days` |
| Weeks | `1 week`, `2 weeks` |
| Months | `1 month`, `3 months` |
| Years | `1 year` |

!!! leadr "LEADR Cloud"

    The LEADR Cloud service enables the weekly and monthly repeat interval to all accounts - including the free tier. An account with a paid plan is required to create board templates with daily, hourly or custom repeat intervals.

    Self-hosted deployments manage the allowed repeat intervals independently.

**Common intervals:**

- Daily: `1 day`
- Weekly: `7 days` or `1 week`
- Weekends: `7 days` or `1 week`, plus the date of the first weekend in `Next Run`
- Bi-weekly: `14 days` or `2 weeks`
- Monthly: `1 month`
- First day of each month: `1 month`, plus the 1st date of the next month in `Next Run`
- Quarterly: `3 months`

## Name Template Placeholders

Use placeholders in the **Name Template** field to generate dynamic board names:

| Placeholder | Output | Example |
|-------------|--------|---------|
| `{year}` | Four-digit year | `2026` |
| `{month}` | Full month name | `January` |
| `{month_short}` | Abbreviated month | `Jan` |
| `{week}` | ISO week number | `42` |
| `{quarter}` | Quarter of year | `Q1` |
| `{date}` | ISO date format | `2026-01-15` |
| `{series}` | Sequential number | `1`, `2`, `3`... |

## Sequential Series

The **Series** field enables sequential numbering for boards created from the same template:

- **Calculated dynamically**: Series values are generated from existing board count + 1
- **Reuses numbers**: If boards are deleted, their numbers become available again

To use series:

1. Set a **Repeat Interval** value
2. Set the **Series** field to an identifier (e.g., `"weekly"`, `"season"`, `"pro_series"`)
3. Include `{series}` in your **Name Template**

## Examples

### Monthly High Scores

Creates a new board at the start of each month:

```json
{
  "name": "Monthly High Scores",
  "name_template": "{month} High Scores",
  "repeat_interval": "1 month"
}
```

**Generated boards:** "January High Scores", "February High Scores", ...

### Numbered Monthly Tournament

Creates numbered monthly tournaments:

```json
{
  "name": "Monthly Tournament",
  "name_template": "Monthly Tournament #{series} - {month_short}",
  "repeat_interval": "1 month",
  "series": "monthly"
}
```

**Generated boards:** "Monthly Tournament #1 - Jan", "Monthly Tournament #2 - Feb", ...

### Weekly Challenge

Creates weekly challenges numbered by ISO week:

```json
{
  "name": "Weekly Challenge",
  "name_template": "Week {week} Challenge - {year}",
  "repeat_interval": "7 days"
}
```

**Generated boards:** "Week 1 Challenge - 2026", ..., "Week 52 Challenge - 2026", "Week 1 Challenge - 2027", ...

### Quarterly Seasons

Creates seasonal boards each quarter:

```json
{
  "name": "Seasonal Board",
  "name_template": "{year} {quarter} Season",
  "repeat_interval": "3 months"
}
```

**Generated boards:** "2026 Q1 Season", "2026 Q2 Season", "2026 Q3 Season", "2026 Q4 Season", ...

## Pause a Template

To pause or disable a template and stop it from generating new boards:

1. Open the LEADR app and navigate to **Games**
2. Select your game and press `t` to open **Templates**
3. Select the template you want to pause
4. Press `e` to edit the template
5. Set **Active** to `No`
6. Save the template

The template will stop creating new boards until you set **Active** back to `Yes`. Existing boards created by the template are not affected.

See the [Advanced Boards guide](../guides/advanced-boards.md) for more information on using board templates.

---

_Need Help? The LEADR team and community is always happy to help on the [LEADR Discord](https://discord.gg/RMUukcAxSZ)_
