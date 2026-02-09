# Board Templates

## Board Template Naming

Board templates can automatically generate board names using placeholders and sequential series.

### Placeholders

Use placeholders in the `name_template` field to generate dynamic board names:

| Placeholder     | Output            | Example          |
| --------------- | ----------------- | ---------------- |
| `{year}`        | Four-digit year   | `2025`           |
| `{month}`       | Full month name   | `January`        |
| `{month_short}` | Abbreviated month | `Jan`            |
| `{week}`        | ISO week number   | `42`             |
| `{quarter}`     | Quarter of year   | `Q1`             |
| `{date}`        | ISO date format   | `2025-01-15`     |
| `{series}`      | Sequential number | `1`, `2`, `3`... |

### Sequential Series

The `series` field enables sequential numbering for boards created from the same template:

- **Calculated dynamically**: Series values are generated from existing board count + 1
- **Reuses numbers**: If boards are deleted, their numbers become available again

To use series:

1. Set an `reapeat_interval` value as you would for any Board Template
1. Set the `series` field to an identifier (e.g., `"weekly"`, `"season"`, `"pro_series"`)
1. Include `{series}` in your `name_template`

### Examples

**New board every month**

```json
{
  "name": "Monthly High Scores",
  "name_template": "{month} High Scores",
  "repeat_interval": "1 month",
  "series": "monthly"
}
```

>"January High Scores", "February High Scores"...

**New board every month, numbered using series sequence counter:**

```json
{
  "name": "Monthly Tournament",
  "name_template": "Monthly Tournament #{series} - {month_short}",
  "repeat_interval": "1 month",
  "series": "monthly"
}
```

>"Monthly Tournament #1 - Jan", "Monthly Tournament #2 - Feb"...

**New board every week, numbered using "week of the year":**

```json
{
  "name": "Weekly Challenge",
  "name_template": "Week {week} Challenge - {year}",
  "repeat_interval": "7 days",
  "series": null
}
```

>"Week 1 Challenge - 2025", ..., "Week 52 Challenge - 2025", "Week 1 Challenge - 2026", ...

**New board every quarter**

```json
{
  "name": "Seasonal Board",
  "name_template": "{year} {quarter} Season",
  "series": null
}
```

>"2026 Q1 Season", "2026 Q2 Season", ...
