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
* [`leadr board get-by-slug`↴](#leadr-board-get-by-slug)
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
* [`leadr invite`↴](#leadr-invite)

## `leadr`

LEADR CLI - Admin tool for LEADR API (v0.5.6)

CLI docs:  https://docs.leadr.gg/latest/cli/
Website:      https://www.leadr.gg
Discord:      https://discord.gg/RMUukcAxSZ

**Usage:** `leadr [OPTIONS] [COMMAND]`

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
* `invite` — Invite a user to the account (interactive)

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

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) [optional if configured]



## `leadr account update`

Update an account

**Usage:** `leadr account update [OPTIONS] --json <JSON>`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) [optional if configured]
* `--json <JSON>` — JSON string with fields to update [required]



## `leadr account delete`

Delete an account (soft delete)

**Usage:** `leadr account delete [OPTIONS]`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) [optional if configured]



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

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) [optional if configured]
* `--email <EMAIL>` — User email [required]
* `--display-name <DISPLAY_NAME>` — Display name [required]



## `leadr user list`

List users for an account

**Usage:** `leadr user list [OPTIONS]`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) [optional if configured]



## `leadr user get`

Get user by ID

**Usage:** `leadr user get --user-id <USER_ID>`

###### **Options:**

* `--user-id <USER_ID>` — User ID (UUID) [required]



## `leadr user update`

Update a user

**Usage:** `leadr user update --user-id <USER_ID> --json <JSON>`

###### **Options:**

* `--user-id <USER_ID>` — User ID (UUID) [required]
* `--json <JSON>` — JSON string with fields to update [required]



## `leadr user delete`

Delete a user (soft delete)

**Usage:** `leadr user delete --user-id <USER_ID>`

###### **Options:**

* `--user-id <USER_ID>` — User ID (UUID) [required]



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

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) [optional if configured]
* `--user-id <USER_ID>` — User ID (UUID), the user who owns this API key [required]
* `--name <NAME>` — API key name [required]



## `leadr api-key list`

List API keys for an account

**Usage:** `leadr api-key list [OPTIONS]`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) [optional if configured]



## `leadr api-key get`

Get API key by ID

**Usage:** `leadr api-key get --key-id <KEY_ID>`

###### **Options:**

* `--key-id <KEY_ID>` — API key ID (UUID) [required]



## `leadr api-key revoke`

Revoke an API key (soft delete)

**Usage:** `leadr api-key revoke --key-id <KEY_ID>`

###### **Options:**

* `--key-id <KEY_ID>` — API key ID (UUID) [required]



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

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) [optional if configured]
* `--name <NAME>` — Game name [required]
* `--description <DESCRIPTION>` — Game description [optional]
* `--page-url <PAGE_URL>` — URL to game's page, e.g. Steam store, itch.io [optional]
* `--steam-app-id <STEAM_APP_ID>` — Steam App ID [optional]
* `--anti-cheat-enabled <ANTI_CHEAT_ENABLED>` — Enable anti-cheat [optional, default: true]

  Possible values: `true`, `false`




## `leadr game list`

List games for an account

**Usage:** `leadr game list [OPTIONS]`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) [optional if configured]



## `leadr game get`

Get game by ID

**Usage:** `leadr game get --game-id <GAME_ID>`

###### **Options:**

* `--game-id <GAME_ID>` — Game ID (UUID) [required]



## `leadr game update`

Update a game

**Usage:** `leadr game update --game-id <GAME_ID> --json <JSON>`

###### **Options:**

* `--game-id <GAME_ID>` — Game ID (UUID) [required]
* `--json <JSON>` — JSON string with fields to update [required]



## `leadr game delete`

Delete a game (soft delete)

**Usage:** `leadr game delete --game-id <GAME_ID>`

###### **Options:**

* `--game-id <GAME_ID>` — Game ID (UUID) [required]



## `leadr board`

Board (leaderboard) management

**Usage:** `leadr board <COMMAND>`

###### **Subcommands:**

* `create` — Create a new board
* `list` — List boards for an account
* `get` — Get board by ID
* `get-by-code` — Get board by short code
* `get-by-slug` — Get board by slug
* `update` — Update a board
* `delete` — Delete a board (soft delete)



## `leadr board create`

Create a new board

**Usage:** `leadr board create [OPTIONS] --game-id <GAME_ID> --name <NAME>`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) [optional if configured]
* `--game-id <GAME_ID>` — Game ID (UUID) [required]
* `--name <NAME>` — Board name [required]
* `--description <DESCRIPTION>` — Board description [optional]
* `--icon <ICON>` — Icon - emoji or URL [optional]
* `--short-code <SHORT_CODE>` — Short code [optional, auto-generated if omitted]
* `--unit <UNIT>` — Unit, e.g. "points", "seconds" [optional]
* `--sort-direction <SORT_DIRECTION>` — Sort direction: asc or desc [optional, default: desc]
* `--keep-strategy <KEEP_STRATEGY>` — Keep strategy: best, first, last, or all [optional, default: best]
* `--is-active <IS_ACTIVE>` — Board is active [default: true]

  Default value: `true`

  Possible values: `true`, `false`

* `--is-published <IS_PUBLISHED>` — Board is published/visible to clients [default: true]

  Default value: `true`

  Possible values: `true`, `false`

* `--starts-at <STARTS_AT>` — Start time for time-bounded boards, ISO 8601 [optional]
* `--ends-at <ENDS_AT>` — End time for time-bounded boards, ISO 8601 [optional]



## `leadr board list`

List boards for an account

**Usage:** `leadr board list [OPTIONS]`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) [optional if configured]
* `--game-id <GAME_ID>` — Game ID to filter boards by (UUID) [optional]



## `leadr board get`

Get board by ID

**Usage:** `leadr board get [OPTIONS] --board-id <BOARD_ID>`

###### **Options:**

* `--board-id <BOARD_ID>` — Board ID (e.g. `brd_xxx`) [required]
* `--account-id <ACCOUNT_ID>` — Account ID for superadmin cross-account access [optional]



## `leadr board get-by-code`

Get board by short code

**Usage:** `leadr board get-by-code [OPTIONS] --short-code <SHORT_CODE>`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) [optional if configured]
* `--short-code <SHORT_CODE>` — Short code [required]



## `leadr board get-by-slug`

Get board by slug

**Usage:** `leadr board get-by-slug [OPTIONS] --game-id <GAME_ID> --slug <SLUG>`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) [optional if configured]
* `--game-id <GAME_ID>` — Game ID (UUID) [required]
* `--slug <SLUG>` — Board slug [required]



## `leadr board update`

Update a board

**Usage:** `leadr board update --board-id <BOARD_ID> --json <JSON>`

###### **Options:**

* `--board-id <BOARD_ID>` — Board ID (UUID) [required]
* `--json <JSON>` — JSON string with fields to update [required]



## `leadr board delete`

Delete a board (soft delete)

**Usage:** `leadr board delete --board-id <BOARD_ID>`

###### **Options:**

* `--board-id <BOARD_ID>` — Board ID (UUID) [required]



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

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) [optional if configured]
* `--game-id <GAME_ID>` — Game ID (UUID) [required]
* `--name <NAME>` — Template name [required]
* `--slug <SLUG>` — URL-friendly slug for boards created from this template [optional]
* `--repeat-interval <REPEAT_INTERVAL>` — Repeat interval, `PostgreSQL` syntax e.g. "7 days", "1 month" [required]
* `--next-run-at <NEXT_RUN_AT>` — Next run time, ISO 8601 datetime [required]
* `--is-active <IS_ACTIVE>` — Template is active [default: true]

  Default value: `true`

  Possible values: `true`, `false`

* `--is-published <IS_PUBLISHED>` — Boards created from this template should be published [default: true]

  Default value: `true`

  Possible values: `true`, `false`

* `--name-template <NAME_TEMPLATE>` — Name template for generated boards [optional]
* `--series <SERIES>` — Series identifier for sequential board naming [optional]
* `--icon <ICON>` — Icon identifier for boards, e.g. "fa-crown" [optional]
* `--unit <UNIT>` — Unit of measurement, e.g. "seconds", "points" [optional]
* `--sort-direction <SORT_DIRECTION>` — Sort direction for scores [default: desc]

  Default value: `desc`

  Possible values:
  - `asc`:
    Ascending order (lowest score first)
  - `desc`:
    Descending order (highest score first)

* `--keep-strategy <KEEP_STRATEGY>` — Strategy for keeping multiple scores from same user [default: all]

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

* `--starts-at <STARTS_AT>` — Start time for time-bounded boards, ISO 8601 [optional]
* `--ends-at <ENDS_AT>` — End time for time-bounded boards, ISO 8601 [optional]



## `leadr board-template list`

List board templates for an account

**Usage:** `leadr board-template list [OPTIONS]`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) [optional if configured]
* `--game-id <GAME_ID>` — Game ID to filter templates by (UUID) [optional]



## `leadr board-template get`

Get board template by ID

**Usage:** `leadr board-template get --template-id <TEMPLATE_ID>`

###### **Options:**

* `--template-id <TEMPLATE_ID>` — Template ID (UUID) [required]



## `leadr board-template update`

Update a board template

**Usage:** `leadr board-template update --template-id <TEMPLATE_ID> --json <JSON>`

###### **Options:**

* `--template-id <TEMPLATE_ID>` — Template ID (UUID) [required]
* `--json <JSON>` — JSON string with fields to update [required]



## `leadr board-template delete`

Delete a board template (soft delete)

**Usage:** `leadr board-template delete --template-id <TEMPLATE_ID>`

###### **Options:**

* `--template-id <TEMPLATE_ID>` — Template ID (UUID) [required]



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

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) [optional with client auth]
* `--game-id <GAME_ID>` — Game ID (UUID) [optional with client auth]
* `--board-id <BOARD_ID>` — Board ID (UUID) [required]
* `--device-id <DEVICE_ID>` — Device ID (UUID) [optional with client auth]
* `--player-name <PLAYER_NAME>` — Player name [required]
* `--value <VALUE>` — Score value (number) [required]
* `--value-display <VALUE_DISPLAY>` — Display string, e.g. "1:23.45", "1,234 points" [optional]
* `--filter-timezone <FILTER_TIMEZONE>` — Timezone filter [optional]
* `--filter-country <FILTER_COUNTRY>` — Country filter [optional]
* `--filter-city <FILTER_CITY>` — City filter [optional]



## `leadr score list`

List scores for an account

**Usage:** `leadr score list [OPTIONS]`

###### **Options:**

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) [optional with client auth]
* `--board-id <BOARD_ID>` — Board ID to filter by (UUID) [optional]
* `--game-id <GAME_ID>` — Game ID to filter by (UUID) [optional]
* `--device-id <DEVICE_ID>` — Device ID to filter by (UUID) [optional]
* `--cursor <CURSOR>` — Pagination cursor from previous response [optional]
* `--limit <LIMIT>` — Items per page, 1-100 [optional, default: 20]
* `--sort <SORT>` — Sort order, e.g. "value:desc", "`created_at:asc`" [optional]
* `--all` — Fetch all pages automatically



## `leadr score get`

Get score by ID

**Usage:** `leadr score get --score-id <SCORE_ID>`

###### **Options:**

* `--score-id <SCORE_ID>` — Score ID (UUID) [required]



## `leadr score update`

Update a score

**Usage:** `leadr score update --score-id <SCORE_ID> --json <JSON>`

###### **Options:**

* `--score-id <SCORE_ID>` — Score ID (UUID) [required]
* `--json <JSON>` — JSON string with fields to update [required]



## `leadr score delete`

Delete a score (soft delete)

**Usage:** `leadr score delete --score-id <SCORE_ID>`

###### **Options:**

* `--score-id <SCORE_ID>` — Score ID (UUID) [required]



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

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) [optional if configured]
* `--game-id <GAME_ID>` — Game ID to filter by (UUID) [optional]
* `--status <STATUS>` — Status filter: active, banned, suspended [optional]



## `leadr device get`

Get device by ID

**Usage:** `leadr device get --device-id <DEVICE_ID>`

###### **Options:**

* `--device-id <DEVICE_ID>` — Device ID (UUID) [required]



## `leadr device update`

Update device status

**Usage:** `leadr device update [OPTIONS] --device-id <DEVICE_ID>`

###### **Options:**

* `--device-id <DEVICE_ID>` — Device ID (UUID) [required]
* `--status <STATUS>` — New status: active, banned, suspended [optional]



## `leadr device delete`

Delete a device (soft delete)

**Usage:** `leadr device delete --device-id <DEVICE_ID>`

###### **Options:**

* `--device-id <DEVICE_ID>` — Device ID (UUID) [required]



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

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) [optional if configured]
* `--device-id <DEVICE_ID>` — Device ID to filter by (UUID) [optional]
* `--game-id <GAME_ID>` — Game ID to filter by (UUID) [optional]
* `--status <STATUS>` — Status filter [optional]



## `leadr device-session get`

Get device session by ID

**Usage:** `leadr device-session get --session-id <SESSION_ID>`

###### **Options:**

* `--session-id <SESSION_ID>` — Session ID (UUID) [required]



## `leadr device-session update`

Update device session status

**Usage:** `leadr device-session update [OPTIONS] --session-id <SESSION_ID>`

###### **Options:**

* `--session-id <SESSION_ID>` — Session ID (UUID) [required]
* `--status <STATUS>` — New status [optional]



## `leadr device-session delete`

Delete a device session (soft delete)

**Usage:** `leadr device-session delete --session-id <SESSION_ID>`

###### **Options:**

* `--session-id <SESSION_ID>` — Session ID (UUID) [required]



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

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) [optional if configured]
* `--board-id <BOARD_ID>` — Board ID to filter by (UUID) [optional]
* `--game-id <GAME_ID>` — Game ID to filter by (UUID) [optional]
* `--status <STATUS>` — Status: PENDING/CONFIRMED_CHEAT/FALSE_POSITIVE/DISMISSED [optional]
* `--flag-type <FLAG_TYPE>` — Flag type: VELOCITY/DUPLICATE/RATE_LIMIT [optional]



## `leadr score-flag get`

Get score flag by ID

**Usage:** `leadr score-flag get --flag-id <FLAG_ID>`

###### **Options:**

* `--flag-id <FLAG_ID>` — Flag ID (UUID) [required]



## `leadr score-flag review`

Review/update a score flag

**Usage:** `leadr score-flag review [OPTIONS] --flag-id <FLAG_ID>`

###### **Options:**

* `--flag-id <FLAG_ID>` — Flag ID (UUID) [required]
* `--status <STATUS>` — New status: PENDING/CONFIRMED_CHEAT/FALSE_POSITIVE/DISMISSED [optional]
* `--reviewer-decision <REVIEWER_DECISION>` — Reviewer decision/notes [optional]



## `leadr score-flag delete`

Delete a score flag (soft delete)

**Usage:** `leadr score-flag delete --flag-id <FLAG_ID>`

###### **Options:**

* `--flag-id <FLAG_ID>` — Flag ID (UUID) [required]



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

* `--account-id <ACCOUNT_ID>` — Account ID (UUID) [optional if configured]
* `--board-id <BOARD_ID>` — Board ID to filter by (UUID) [optional]
* `--device-id <DEVICE_ID>` — Device ID to filter by (UUID) [optional]
* `--game-id <GAME_ID>` — Game ID to filter by (UUID) [optional]



## `leadr score-submission-meta get`

Get score submission metadata by ID

**Usage:** `leadr score-submission-meta get --meta-id <META_ID>`

###### **Options:**

* `--meta-id <META_ID>` — Metadata ID (UUID) [required]



## `leadr invite`

Invite a user to the account (interactive)

**Usage:** `leadr invite`



<hr/>

<small><i>
    This document was generated automatically by
    <a href="https://crates.io/crates/clap-markdown"><code>clap-markdown</code></a>.
</i></small>
