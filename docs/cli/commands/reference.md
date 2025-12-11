# Command-Line Help for `leadr`

This document contains the help content for the `leadr` command-line program.

**Command Overview:**

* [`leadr`↴](#leadr)
* [`leadr register`↴](#leadr-register)
* [`leadr me`↴](#leadr-me)
* [`leadr auth`↴](#leadr-auth)
* [`leadr auth admin`↴](#leadr-auth-admin)
* [`leadr auth admin configure`↴](#leadr-auth-admin-configure)
* [`leadr auth admin status`↴](#leadr-auth-admin-status)
* [`leadr auth admin clear`↴](#leadr-auth-admin-clear)
* [`leadr account`↴](#leadr-account)
* [`leadr account get`↴](#leadr-account-get)
* [`leadr account update`↴](#leadr-account-update)
* [`leadr account delete`↴](#leadr-account-delete)
* [`leadr user`↴](#leadr-user)
* [`leadr user create`↴](#leadr-user-create)
* [`leadr user list`↴](#leadr-user-list)
* [`leadr user get`↴](#leadr-user-get)
* [`leadr user update`↴](#leadr-user-update)
* [`leadr user delete`↴](#leadr-user-delete)
* [`leadr api-key`↴](#leadr-api-key)
* [`leadr api-key create`↴](#leadr-api-key-create)
* [`leadr api-key list`↴](#leadr-api-key-list)
* [`leadr api-key get`↴](#leadr-api-key-get)
* [`leadr api-key revoke`↴](#leadr-api-key-revoke)
* [`leadr game`↴](#leadr-game)
* [`leadr game create`↴](#leadr-game-create)
* [`leadr game list`↴](#leadr-game-list)
* [`leadr game get`↴](#leadr-game-get)
* [`leadr game update`↴](#leadr-game-update)
* [`leadr game delete`↴](#leadr-game-delete)
* [`leadr board`↴](#leadr-board)
* [`leadr board create`↴](#leadr-board-create)
* [`leadr board list`↴](#leadr-board-list)
* [`leadr board get`↴](#leadr-board-get)
* [`leadr board get-by-code`↴](#leadr-board-get-by-code)
* [`leadr board update`↴](#leadr-board-update)
* [`leadr board delete`↴](#leadr-board-delete)
* [`leadr board-template`↴](#leadr-board-template)
* [`leadr board-template create`↴](#leadr-board-template-create)
* [`leadr board-template list`↴](#leadr-board-template-list)
* [`leadr board-template get`↴](#leadr-board-template-get)
* [`leadr board-template update`↴](#leadr-board-template-update)
* [`leadr board-template delete`↴](#leadr-board-template-delete)
* [`leadr score`↴](#leadr-score)
* [`leadr score create`↴](#leadr-score-create)
* [`leadr score list`↴](#leadr-score-list)
* [`leadr score get`↴](#leadr-score-get)
* [`leadr score update`↴](#leadr-score-update)
* [`leadr score delete`↴](#leadr-score-delete)
* [`leadr device`↴](#leadr-device)
* [`leadr device list`↴](#leadr-device-list)
* [`leadr device get`↴](#leadr-device-get)
* [`leadr device update`↴](#leadr-device-update)
* [`leadr device delete`↴](#leadr-device-delete)
* [`leadr device-session`↴](#leadr-device-session)
* [`leadr device-session list`↴](#leadr-device-session-list)
* [`leadr device-session get`↴](#leadr-device-session-get)
* [`leadr device-session update`↴](#leadr-device-session-update)
* [`leadr device-session delete`↴](#leadr-device-session-delete)
* [`leadr score-flag`↴](#leadr-score-flag)
* [`leadr score-flag list`↴](#leadr-score-flag-list)
* [`leadr score-flag get`↴](#leadr-score-flag-get)
* [`leadr score-flag review`↴](#leadr-score-flag-review)
* [`leadr score-flag delete`↴](#leadr-score-flag-delete)
* [`leadr score-submission-meta`↴](#leadr-score-submission-meta)
* [`leadr score-submission-meta list`↴](#leadr-score-submission-meta-list)
* [`leadr score-submission-meta get`↴](#leadr-score-submission-meta-get)

## `leadr`

LEADR CLI - Admin and testing tool for LEADR API

**Usage:** `leadr [OPTIONS] <COMMAND>`

###### **Subcommands:**

* `register` — Register a new LEADR account (interactive)
* `me` — Show current account and user info
* `auth` — Authentication commands
* `account` — Account management
* `user` — User management
* `api-key` — API key management
* `game` — Game management
* `board` — Board (leaderboard) management
* `board-template` — Board template management
* `score` — Score management
* `device` — Device management
* `device-session` — Device session management
* `score-flag` — Score flag management (anti-cheat)
* `score-submission-meta` — Score submission metadata (analytics)

###### **Options:**

* `--host <HOST>` — API host override. Overrides default URLs for all commands. Defaults to `admin-api.leadrcloud.com` (public) or `0.0.0.0:8001`/`0.0.0.0:8000` (internal)



## `leadr register`

Register a new LEADR account (interactive)

**Usage:** `leadr register`



## `leadr me`

Show current account and user info

**Usage:** `leadr me [OPTIONS]`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (required for superadmins)



## `leadr auth`

Authentication commands

**Usage:** `leadr auth <COMMAND>`

###### **Subcommands:**

* `admin` — Admin authentication



## `leadr auth admin`

Admin authentication

**Usage:** `leadr auth admin <COMMAND>`

###### **Subcommands:**

* `configure` — Configure admin API key (interactive prompt)
* `status` — Show API key configuration status
* `clear` — Clear saved API key



## `leadr auth admin configure`

Configure admin API key (interactive prompt)

**Usage:** `leadr auth admin configure`



## `leadr auth admin status`

Show API key configuration status

**Usage:** `leadr auth admin status`



## `leadr auth admin clear`

Clear saved API key

**Usage:** `leadr auth admin clear`



## `leadr account`

Account management

**Usage:** `leadr account <COMMAND>`

###### **Subcommands:**

* `get` — Get account by ID
* `update` — Update an account
* `delete` — Delete an account (soft delete)



## `leadr account get`

Get account by ID

**Usage:** `leadr account get [OPTIONS]`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) - optional if configured via `auth admin configure`



## `leadr account update`

Update an account

**Usage:** `leadr account update [OPTIONS] --json <JSON>`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) - optional if configured via `auth admin configure`
* `--json <JSON>` — JSON string with fields to update (e.g., `{"name": "New Name", "status": "suspended"}`)



## `leadr account delete`

Delete an account (soft delete)

**Usage:** `leadr account delete [OPTIONS]`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) - optional if configured via `auth admin configure`



## `leadr user`

User management

**Usage:** `leadr user <COMMAND>`

###### **Subcommands:**

* `create` — Create a new user
* `list` — List users for an account
* `get` — Get user by ID
* `update` — Update a user
* `delete` — Delete a user (soft delete)



## `leadr user create`

Create a new user

**Usage:** `leadr user create [OPTIONS] --email <EMAIL> --display-name <DISPLAY_NAME>`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) - optional if configured via `auth admin configure`
* `--email <EMAIL>` — User email
* `--display-name <DISPLAY_NAME>` — Display name



## `leadr user list`

List users for an account

**Usage:** `leadr user list [OPTIONS]`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) - optional if configured via `auth admin configure`



## `leadr user get`

Get user by ID

**Usage:** `leadr user get --user-id <USER_ID>`

###### **Options:**

* `--user-id <USER_ID>` — User ID (UUID)



## `leadr user update`

Update a user

**Usage:** `leadr user update --user-id <USER_ID> --json <JSON>`

###### **Options:**

* `--user-id <USER_ID>` — User ID (UUID)
* `--json <JSON>` — JSON string with fields to update (e.g., `{"email": "new@example.com", "display_name": "New Name"}`)



## `leadr user delete`

Delete a user (soft delete)

**Usage:** `leadr user delete --user-id <USER_ID>`

###### **Options:**

* `--user-id <USER_ID>` — User ID (UUID)



## `leadr api-key`

API key management

**Usage:** `leadr api-key <COMMAND>`

###### **Subcommands:**

* `create` — Create a new API key
* `list` — List API keys for an account
* `get` — Get API key by ID
* `revoke` — Revoke an API key (soft delete)



## `leadr api-key create`

Create a new API key

**Usage:** `leadr api-key create [OPTIONS] --user-id <USER_ID> --name <NAME>`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) - optional if configured via `auth admin configure`
* `--user-id <USER_ID>` — User ID (UUID) - the user who owns this API key
* `--name <NAME>` — API key name



## `leadr api-key list`

List API keys for an account

**Usage:** `leadr api-key list [OPTIONS]`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) - optional if configured via `auth admin configure`



## `leadr api-key get`

Get API key by ID

**Usage:** `leadr api-key get --key-id <KEY_ID>`

###### **Options:**

* `--key-id <KEY_ID>` — API key ID (UUID)



## `leadr api-key revoke`

Revoke an API key (soft delete)

**Usage:** `leadr api-key revoke --key-id <KEY_ID>`

###### **Options:**

* `--key-id <KEY_ID>` — API key ID (UUID)



## `leadr game`

Game management

**Usage:** `leadr game <COMMAND>`

###### **Subcommands:**

* `create` — Create a new game
* `list` — List games for an account
* `get` — Get game by ID
* `update` — Update a game
* `delete` — Delete a game (soft delete)



## `leadr game create`

Create a new game

**Usage:** `leadr game create [OPTIONS] --name <NAME>`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) - optional if configured via `auth admin configure`
* `--name <NAME>` — Game name
* `--steam-app-id <STEAM_APP_ID>` — Steam App ID (optional)
* `--anti-cheat-enabled <ANTI_CHEAT_ENABLED>` — Enable anti-cheat (default: true)

  Possible values: `true`, `false`




## `leadr game list`

List games for an account

**Usage:** `leadr game list [OPTIONS]`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) - optional if configured via `auth admin configure`



## `leadr game get`

Get game by ID

**Usage:** `leadr game get --game-id <GAME_ID>`

###### **Options:**

* `--game-id <GAME_ID>` — Game ID (UUID)



## `leadr game update`

Update a game

**Usage:** `leadr game update --game-id <GAME_ID> --json <JSON>`

###### **Options:**

* `--game-id <GAME_ID>` — Game ID (UUID)
* `--json <JSON>` — JSON string with fields to update



## `leadr game delete`

Delete a game (soft delete)

**Usage:** `leadr game delete --game-id <GAME_ID>`

###### **Options:**

* `--game-id <GAME_ID>` — Game ID (UUID)



## `leadr board`

Board (leaderboard) management

**Usage:** `leadr board <COMMAND>`

###### **Subcommands:**

* `create` — Create a new board
* `list` — List boards for an account
* `get` — Get board by ID
* `get-by-code` — Get board by short code
* `update` — Update a board
* `delete` — Delete a board (soft delete)



## `leadr board create`

Create a new board

**Usage:** `leadr board create [OPTIONS] --game-id <GAME_ID> --name <NAME>`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) - optional if configured via `auth admin configure`
* `--game-id <GAME_ID>` — Game ID (UUID)
* `--name <NAME>` — Board name
* `--icon <ICON>` — Icon (emoji or URL)
* `--short-code <SHORT_CODE>` — Short code (globally unique identifier)
* `--unit <UNIT>` — Unit (e.g., "points", "seconds", "kills")
* `--sort-direction <SORT_DIRECTION>` — Sort direction (asc or desc)
* `--keep-strategy <KEEP_STRATEGY>` — Keep strategy (best, first, last, or all)
* `--is-active` — Board is active (default: true)

  Default value: `true`



## `leadr board list`

List boards for an account

**Usage:** `leadr board list [OPTIONS]`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) - optional when using client authentication
* `--game-id <GAME_ID>` — Optional Game ID to filter boards by (UUID)



## `leadr board get`

Get board by ID

**Usage:** `leadr board get [OPTIONS] --board-id <BOARD_ID>`

###### **Options:**

* `--board-id <BOARD_ID>` — Board ID (e.g., `brd_xxx`)
* `--account-id <ACCOUNT_ID>` — Account ID (for superadmin cross-account access)



## `leadr board get-by-code`

Get board by short code

**Usage:** `leadr board get-by-code [OPTIONS] --short-code <SHORT_CODE>`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) - optional if configured via `auth admin configure`
* `--short-code <SHORT_CODE>` — Short code



## `leadr board update`

Update a board

**Usage:** `leadr board update --board-id <BOARD_ID> --json <JSON>`

###### **Options:**

* `--board-id <BOARD_ID>` — Board ID (UUID)
* `--json <JSON>` — JSON string with fields to update



## `leadr board delete`

Delete a board (soft delete)

**Usage:** `leadr board delete --board-id <BOARD_ID>`

###### **Options:**

* `--board-id <BOARD_ID>` — Board ID (UUID)



## `leadr board-template`

Board template management

**Usage:** `leadr board-template <COMMAND>`

###### **Subcommands:**

* `create` — Create a new board template
* `list` — List board templates for an account
* `get` — Get board template by ID
* `update` — Update a board template
* `delete` — Delete a board template (soft delete)



## `leadr board-template create`

Create a new board template

**Usage:** `leadr board-template create [OPTIONS] --game-id <GAME_ID> --name <NAME> --repeat-interval <REPEAT_INTERVAL> --next-run-at <NEXT_RUN_AT>`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) - optional if configured via `auth admin configure`
* `--game-id <GAME_ID>` — Game ID (UUID)
* `--name <NAME>` — Template name
* `--slug <SLUG>` — URL-friendly slug for boards created from this template
* `--repeat-interval <REPEAT_INTERVAL>` — Repeat interval (`PostgreSQL` interval syntax, e.g., "7 days", "1 month")
* `--next-run-at <NEXT_RUN_AT>` — Next run time (ISO 8601 datetime, e.g., "2025-01-01T00:00:00Z")
* `--is-active` — Template is active (default: true)

  Default value: `true`
* `--is-published` — Whether boards created from this template should be published (default: true)

  Default value: `true`
* `--name-template <NAME_TEMPLATE>` — Optional name template for generated boards
* `--series <SERIES>` — Optional series identifier for sequential board naming
* `--icon <ICON>` — Icon identifier for boards (e.g., "fa-crown")
* `--unit <UNIT>` — Unit of measurement for scores (e.g., "seconds", "points")
* `--sort-direction <SORT_DIRECTION>` — Sort direction for scores (default: desc)

  Default value: `desc`

  Possible values:
  - `asc`:
    Ascending order (lowest score first)
  - `desc`:
    Descending order (highest score first)

* `--keep-strategy <KEEP_STRATEGY>` — Strategy for keeping multiple scores from the same user (default: all)

  Default value: `all`

  Possible values:
  - `all`:
    Keep all scores
  - `best`:
    Keep only the best score
  - `first`:
    Keep only the first score
  - `last`:
    Keep only the latest score

* `--starts-at <STARTS_AT>` — Optional start time for time-bounded boards (ISO 8601 datetime)
* `--ends-at <ENDS_AT>` — Optional end time for time-bounded boards (ISO 8601 datetime)



## `leadr board-template list`

List board templates for an account

**Usage:** `leadr board-template list [OPTIONS]`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) - optional if configured via `auth admin configure`
* `--game-id <GAME_ID>` — Optional Game ID to filter templates by (UUID)



## `leadr board-template get`

Get board template by ID

**Usage:** `leadr board-template get --template-id <TEMPLATE_ID>`

###### **Options:**

* `--template-id <TEMPLATE_ID>` — Template ID (UUID)



## `leadr board-template update`

Update a board template

**Usage:** `leadr board-template update --template-id <TEMPLATE_ID> --json <JSON>`

###### **Options:**

* `--template-id <TEMPLATE_ID>` — Template ID (UUID)
* `--json <JSON>` — JSON string with fields to update



## `leadr board-template delete`

Delete a board template (soft delete)

**Usage:** `leadr board-template delete --template-id <TEMPLATE_ID>`

###### **Options:**

* `--template-id <TEMPLATE_ID>` — Template ID (UUID)



## `leadr score`

Score management

**Usage:** `leadr score <COMMAND>`

###### **Subcommands:**

* `create` — Create a new score
* `list` — List scores for an account
* `get` — Get score by ID
* `update` — Update a score
* `delete` — Delete a score (soft delete)



## `leadr score create`

Create a new score

**Usage:** `leadr score create [OPTIONS] --board-id <BOARD_ID> --player-name <PLAYER_NAME> --value <VALUE>`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) - optional when using client authentication
* `--game-id <GAME_ID>` — Game ID (UUID) - optional when using client authentication
* `--board-id <BOARD_ID>` — Board ID (UUID)
* `--device-id <DEVICE_ID>` — Device ID (UUID) - optional when using client authentication
* `--player-name <PLAYER_NAME>` — Player name
* `--value <VALUE>` — Score value (number)
* `--value-display <VALUE_DISPLAY>` — Optional display string (e.g., "1:23.45", "1,234 points")
* `--filter-timezone <FILTER_TIMEZONE>` — Optional timezone filter
* `--filter-country <FILTER_COUNTRY>` — Optional country filter
* `--filter-city <FILTER_CITY>` — Optional city filter



## `leadr score list`

List scores for an account

**Usage:** `leadr score list [OPTIONS]`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) - optional when using client authentication
* `--board-id <BOARD_ID>` — Optional Board ID to filter by (UUID)
* `--game-id <GAME_ID>` — Optional Game ID to filter by (UUID)
* `--device-id <DEVICE_ID>` — Optional Device ID to filter by (UUID)
* `--cursor <CURSOR>` — Pagination cursor (from previous response)
* `--limit <LIMIT>` — Number of items per page (1-100, default: 20)
* `--sort <SORT>` — Sort order (e.g., "value:desc", "`created_at:asc`")
* `--all` — Fetch all pages automatically



## `leadr score get`

Get score by ID

**Usage:** `leadr score get --score-id <SCORE_ID>`

###### **Options:**

* `--score-id <SCORE_ID>` — Score ID (UUID)



## `leadr score update`

Update a score

**Usage:** `leadr score update --score-id <SCORE_ID> --json <JSON>`

###### **Options:**

* `--score-id <SCORE_ID>` — Score ID (UUID)
* `--json <JSON>` — JSON string with fields to update



## `leadr score delete`

Delete a score (soft delete)

**Usage:** `leadr score delete --score-id <SCORE_ID>`

###### **Options:**

* `--score-id <SCORE_ID>` — Score ID (UUID)



## `leadr device`

Device management

**Usage:** `leadr device <COMMAND>`

###### **Subcommands:**

* `list` — List devices for an account
* `get` — Get device by ID
* `update` — Update device status
* `delete` — Delete a device (soft delete)



## `leadr device list`

List devices for an account

**Usage:** `leadr device list [OPTIONS]`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) - optional if configured via `auth admin configure`
* `--game-id <GAME_ID>` — Optional Game ID to filter by (UUID)
* `--status <STATUS>` — Optional status filter (active, banned, suspended)



## `leadr device get`

Get device by ID

**Usage:** `leadr device get --device-id <DEVICE_ID>`

###### **Options:**

* `--device-id <DEVICE_ID>` — Device ID (UUID)



## `leadr device update`

Update device status

**Usage:** `leadr device update [OPTIONS] --device-id <DEVICE_ID>`

###### **Options:**

* `--device-id <DEVICE_ID>` — Device ID (UUID)
* `--status <STATUS>` — New status (active, banned, suspended)



## `leadr device delete`

Delete a device (soft delete)

**Usage:** `leadr device delete --device-id <DEVICE_ID>`

###### **Options:**

* `--device-id <DEVICE_ID>` — Device ID (UUID)



## `leadr device-session`

Device session management

**Usage:** `leadr device-session <COMMAND>`

###### **Subcommands:**

* `list` — List device sessions for an account
* `get` — Get device session by ID
* `update` — Update device session status
* `delete` — Delete a device session (soft delete)



## `leadr device-session list`

List device sessions for an account

**Usage:** `leadr device-session list [OPTIONS]`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) - optional if configured via `auth admin configure`
* `--device-id <DEVICE_ID>` — Optional Device ID to filter by (UUID)
* `--game-id <GAME_ID>` — Optional Game ID to filter by (UUID)
* `--status <STATUS>` — Optional status filter



## `leadr device-session get`

Get device session by ID

**Usage:** `leadr device-session get --session-id <SESSION_ID>`

###### **Options:**

* `--session-id <SESSION_ID>` — Session ID (UUID)



## `leadr device-session update`

Update device session status

**Usage:** `leadr device-session update [OPTIONS] --session-id <SESSION_ID>`

###### **Options:**

* `--session-id <SESSION_ID>` — Session ID (UUID)
* `--status <STATUS>` — New status



## `leadr device-session delete`

Delete a device session (soft delete)

**Usage:** `leadr device-session delete --session-id <SESSION_ID>`

###### **Options:**

* `--session-id <SESSION_ID>` — Session ID (UUID)



## `leadr score-flag`

Score flag management (anti-cheat)

**Usage:** `leadr score-flag <COMMAND>`

###### **Subcommands:**

* `list` — List score flags for an account
* `get` — Get score flag by ID
* `review` — Review/update a score flag
* `delete` — Delete a score flag (soft delete)



## `leadr score-flag list`

List score flags for an account

**Usage:** `leadr score-flag list [OPTIONS]`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) - optional if configured via `auth admin configure`
* `--board-id <BOARD_ID>` — Optional Board ID to filter by (UUID)
* `--game-id <GAME_ID>` — Optional Game ID to filter by (UUID)
* `--status <STATUS>` — Optional status filter (`PENDING`, `CONFIRMED_CHEAT`, `FALSE_POSITIVE`, `DISMISSED`)
* `--flag-type <FLAG_TYPE>` — Optional flag type filter (`VELOCITY`, `DUPLICATE`, `RATE_LIMIT`)



## `leadr score-flag get`

Get score flag by ID

**Usage:** `leadr score-flag get --flag-id <FLAG_ID>`

###### **Options:**

* `--flag-id <FLAG_ID>` — Flag ID (UUID)



## `leadr score-flag review`

Review/update a score flag

**Usage:** `leadr score-flag review [OPTIONS] --flag-id <FLAG_ID>`

###### **Options:**

* `--flag-id <FLAG_ID>` — Flag ID (UUID)
* `--status <STATUS>` — New status (`PENDING`, `CONFIRMED_CHEAT`, `FALSE_POSITIVE`, `DISMISSED`)
* `--reviewer-decision <REVIEWER_DECISION>` — Reviewer decision/notes



## `leadr score-flag delete`

Delete a score flag (soft delete)

**Usage:** `leadr score-flag delete --flag-id <FLAG_ID>`

###### **Options:**

* `--flag-id <FLAG_ID>` — Flag ID (UUID)



## `leadr score-submission-meta`

Score submission metadata (analytics)

**Usage:** `leadr score-submission-meta <COMMAND>`

###### **Subcommands:**

* `list` — List score submission metadata for an account
* `get` — Get score submission metadata by ID



## `leadr score-submission-meta list`

List score submission metadata for an account

**Usage:** `leadr score-submission-meta list [OPTIONS]`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) - optional if configured via `auth admin configure`
* `--board-id <BOARD_ID>` — Optional Board ID to filter by (UUID)
* `--device-id <DEVICE_ID>` — Optional Device ID to filter by (UUID)
* `--game-id <GAME_ID>` — Optional Game ID to filter by (UUID)



## `leadr score-submission-meta get`

Get score submission metadata by ID

**Usage:** `leadr score-submission-meta get --meta-id <META_ID>`

###### **Options:**

* `--meta-id <META_ID>` — Metadata ID (UUID)



<hr/>

<small><i>
    This document was generated automatically by
    <a href="https://crates.io/crates/clap-markdown"><code>clap-markdown</code></a>.
</i></small>
