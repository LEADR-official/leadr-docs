# Schemas

## APIKeyResponse

```json
{
  "id": "string",
  "account_id": "string",
  "user_id": "string",
  "name": "string",
  "prefix": "string",
  "status": "active",
  "last_used_at": "2019-08-24T14:15:22Z",
  "expires_at": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}

```

APIKeyResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|Unique identifier for the API key|
|account_id|string|true|none|ID of the account this key belongs to|
|user_id|string|true|none|ID of the user who owns this API key|
|name|string|true|none|Human-readable name for the API key|
|prefix|string|true|none|Key prefix for identification (first 8 characters)|
|status|[APIKeyStatus](./schemas.md#apikeystatus)|true|none|Current status (active, revoked, expired)|
|last_used_at|any|false|none|Timestamp of last successful authentication (UTC)|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string(date-time)|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|expires_at|any|false|none|Expiration timestamp (UTC), or null if never expires|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string(date-time)|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|created_at|string(date-time)|true|none|Timestamp when the key was created (UTC)|
|updated_at|string(date-time)|true|none|Timestamp of last update (UTC)|

## APIKeyStatus

```json
"active"

```

APIKeyStatus

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|APIKeyStatus|string|false|none|API Key status enumeration.|

#### Enumerated Values

|Property|Value|
|---|---|
|APIKeyStatus|active|
|APIKeyStatus|revoked|

## AccountCreateRequest

```json
{
  "name": "string",
  "slug": "string"
}

```

AccountCreateRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|string|true|none|Account name (2-100 characters)|
|slug|any|false|none|Optional URL-friendly slug (globally unique). If not provided, will be auto-generated from name|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

## AccountResponse

```json
{
  "id": "string",
  "name": "string",
  "slug": "string",
  "status": "active",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}

```

AccountResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|Unique identifier for the account|
|name|string|true|none|Account name|
|slug|string|true|none|URL-friendly identifier|
|status|[AccountStatus](./schemas.md#accountstatus)|true|none|Current account status|
|created_at|string(date-time)|true|none|Timestamp when the account was created (UTC)|
|updated_at|string(date-time)|true|none|Timestamp of last update (UTC)|

## AccountStatus

```json
"active"

```

AccountStatus

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|AccountStatus|string|false|none|Account status enumeration.|

#### Enumerated Values

|Property|Value|
|---|---|
|AccountStatus|active|
|AccountStatus|suspended|

## AccountUpdateRequest

```json
{
  "name": "string",
  "slug": "string",
  "status": "active",
  "deleted": true
}

```

AccountUpdateRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|any|false|none|Updated account name|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|slug|any|false|none|Updated URL-friendly identifier|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|status|any|false|none|Account status (active, suspended, deleted)|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[AccountStatus](./schemas.md#accountstatus)|false|none|Account status enumeration.|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|deleted|any|false|none|Set to true to soft delete the account|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|boolean|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

## BoardCreateRequest

```json
{
  "account_id": "string",
  "game_id": "string",
  "name": "string",
  "slug": "string",
  "icon": "fa-crown",
  "short_code": "string",
  "unit": "string",
  "is_active": true,
  "is_published": true,
  "sort_direction": "ASCENDING",
  "keep_strategy": "FIRST_ONLY",
  "created_from_template_id": "string",
  "template_name": "string",
  "starts_at": "2019-08-24T14:15:22Z",
  "ends_at": "2019-08-24T14:15:22Z",
  "tags": [
    "string"
  ],
  "description": "string"
}

```

BoardCreateRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|account_id|string|true|none|ID of the account this board belongs to|
|game_id|string|true|none|ID of the game this board belongs to|
|name|string|true|none|Name of the board|
|slug|any|false|none|Optional URL-friendly slug. If not provided, will be auto-generated from name|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|icon|any|false|none|Icon identifier for the board. Defaults to 'fa-crown'|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|short_code|any|false|none|Globally unique short code for direct sharing. Auto-generated if not provided|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|unit|any|false|none|Unit of measurement for scores (e.g., 'seconds', 'points'). Optional|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|is_active|boolean|false|none|Whether the board is currently active|
|is_published|boolean|false|none|Whether the board is published and visible on public web views|
|sort_direction|[SortDirection](./schemas.md#sortdirection)|false|none|Direction to sort scores|
|keep_strategy|[KeepStrategy](./schemas.md#keepstrategy)|false|none|Strategy for keeping multiple scores from the same user|
|created_from_template_id|any|false|none|Optional template ID this board was created from|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|template_name|any|false|none|Optional template name this board was created from|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|starts_at|any|false|none|Optional start time for time-bounded boards (UTC)|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string(date-time)|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|ends_at|any|false|none|Optional end time for time-bounded boards (UTC)|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string(date-time)|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|tags|any|false|none|Optional list of tags for categorization|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[string]|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|description|any|false|none|Optional short description of the board|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

## BoardResponse

```json
{
  "id": "string",
  "account_id": "string",
  "game_id": "string",
  "name": "string",
  "slug": "string",
  "icon": "string",
  "short_code": "string",
  "unit": "string",
  "is_active": true,
  "is_published": true,
  "sort_direction": "ASCENDING",
  "keep_strategy": "FIRST_ONLY",
  "created_from_template_id": "string",
  "template_name": "string",
  "starts_at": "2019-08-24T14:15:22Z",
  "ends_at": "2019-08-24T14:15:22Z",
  "tags": [
    "string"
  ],
  "description": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}

```

BoardResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|Unique identifier for the board|
|account_id|string|true|none|ID of the account this board belongs to|
|game_id|string|true|none|ID of the game this board belongs to|
|name|string|true|none|Name of the board|
|slug|string|true|none|URL-friendly slug for the board (auto-generated, read-only)|
|icon|any|true|none|Icon identifier for the board, or null|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|short_code|string|true|none|Globally unique short code for direct sharing|
|unit|any|true|none|Unit of measurement for scores, or null|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|is_active|boolean|true|none|Whether the board is currently active|
|is_published|boolean|true|none|Whether the board is published and visible on public web views|
|sort_direction|[SortDirection](./schemas.md#sortdirection)|true|none|Direction to sort scores|
|keep_strategy|[KeepStrategy](./schemas.md#keepstrategy)|true|none|Strategy for keeping scores from same user|
|created_from_template_id|any|false|none|Template ID this board was created from, or null|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|template_name|any|false|none|Template name this board was created from, or null|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|starts_at|any|false|none|Start time for time-bounded boards (UTC)|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string(date-time)|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|ends_at|any|false|none|End time for time-bounded boards (UTC)|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string(date-time)|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|tags|[string]|false|none|List of tags for categorization|
|description|any|false|none|Short description of the board|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|created_at|string(date-time)|true|none|Timestamp when the board was created (UTC)|
|updated_at|string(date-time)|true|none|Timestamp of last update (UTC)|

## BoardTemplateCreateRequest

```json
{
  "account_id": "string",
  "game_id": "string",
  "name": "string",
  "slug": "string",
  "repeat_interval": "string",
  "next_run_at": "2019-08-24T14:15:22Z",
  "is_active": true,
  "is_published": true,
  "name_template": "string",
  "series": "string",
  "icon": "fa-crown",
  "unit": "string",
  "sort_direction": "ASCENDING",
  "keep_strategy": "FIRST_ONLY",
  "starts_at": "2019-08-24T14:15:22Z",
  "ends_at": "2019-08-24T14:15:22Z",
  "tags": [
    "string"
  ],
  "config": {}
}

```

BoardTemplateCreateRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|account_id|string|true|none|ID of the account this template belongs to|
|game_id|string|true|none|ID of the game this template belongs to|
|name|string|true|none|Name of the template|
|slug|any|false|none|URL-friendly slug for boards created from this template|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|repeat_interval|string|true|none|PostgreSQL interval syntax for repeat frequency (e.g., '7 days', '1 month')|
|next_run_at|string(date-time)|true|none|Next scheduled time to create a board from this template (UTC)|
|is_active|boolean|true|none|Whether the template is currently active|
|is_published|boolean|false|none|Whether boards created from this template should be published|
|name_template|any|false|none|Optional template string for generating board names|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|series|any|false|none|Optional series identifier for sequential board naming|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|icon|any|false|none|Icon identifier for boards created from this template|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|unit|any|false|none|Unit of measurement for scores (e.g., 'seconds', 'points')|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|sort_direction|[SortDirection](./schemas.md#sortdirection)|false|none|Direction to sort scores (ascending/descending)|
|keep_strategy|[KeepStrategy](./schemas.md#keepstrategy)|false|none|Strategy for keeping multiple scores from the same user|
|starts_at|any|false|none|Optional start time for time-bounded boards|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string(date-time)|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|ends_at|any|false|none|Optional end time for time-bounded boards|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string(date-time)|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|tags|any|false|none|List of tags for categorizing boards created from this template|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[string]|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|config|any|false|none|Reserved for future procedural generation (bounds, variables, randomization rules)|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

## BoardTemplateResponse

```json
{
  "id": "string",
  "account_id": "string",
  "game_id": "string",
  "name": "string",
  "slug": "string",
  "name_template": "string",
  "series": "string",
  "icon": "string",
  "unit": "string",
  "sort_direction": "ASCENDING",
  "keep_strategy": "FIRST_ONLY",
  "starts_at": "2019-08-24T14:15:22Z",
  "ends_at": "2019-08-24T14:15:22Z",
  "tags": [
    "string"
  ],
  "repeat_interval": "string",
  "config": {},
  "next_run_at": "2019-08-24T14:15:22Z",
  "is_active": true,
  "is_published": true,
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}

```

BoardTemplateResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|Unique identifier for the template|
|account_id|string|true|none|ID of the account this template belongs to|
|game_id|string|true|none|ID of the game this template belongs to|
|name|string|true|none|Name of the template|
|slug|any|true|none|URL-friendly slug for boards created from this template, or null|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name_template|any|false|none|Template string for generating board names, or null|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|series|any|false|none|Series identifier for sequential board naming, or null|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|icon|any|true|none|Icon identifier for boards created from this template|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|unit|any|true|none|Unit of measurement for scores (e.g., 'seconds', 'points')|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|sort_direction|[SortDirection](./schemas.md#sortdirection)|true|none|Direction to sort scores (ascending/descending)|
|keep_strategy|[KeepStrategy](./schemas.md#keepstrategy)|true|none|Strategy for keeping multiple scores from the same user|
|starts_at|any|true|none|Optional start time for time-bounded boards|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string(date-time)|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|ends_at|any|true|none|Optional end time for time-bounded boards|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string(date-time)|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|tags|[string]|true|none|List of tags for categorizing boards created from this template|
|repeat_interval|string|true|none|Repeat frequency in PostgreSQL interval syntax|
|config|object|false|none|Reserved for future procedural generation (bounds, variables, randomization rules)|
|next_run_at|string(date-time)|true|none|Next scheduled run time (UTC)|
|is_active|boolean|true|none|Whether the template is currently active|
|is_published|boolean|true|none|Whether boards created from this template should be published|
|created_at|string(date-time)|true|none|Timestamp when the template was created (UTC)|
|updated_at|string(date-time)|true|none|Timestamp of last update (UTC)|

## BoardTemplateUpdateRequest

```json
{
  "name": "string",
  "slug": "string",
  "name_template": "string",
  "series": "string",
  "icon": "string",
  "unit": "string",
  "sort_direction": "ASCENDING",
  "keep_strategy": "FIRST_ONLY",
  "starts_at": "2019-08-24T14:15:22Z",
  "ends_at": "2019-08-24T14:15:22Z",
  "tags": [
    "string"
  ],
  "repeat_interval": "string",
  "config": {},
  "next_run_at": "2019-08-24T14:15:22Z",
  "is_active": true,
  "is_published": true,
  "deleted": true
}

```

BoardTemplateUpdateRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|any|false|none|Updated template name|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|slug|any|false|none|Updated slug|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name_template|any|false|none|Updated name template|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|series|any|false|none|Updated series identifier|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|icon|any|false|none|Updated icon identifier|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|unit|any|false|none|Updated unit of measurement|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|sort_direction|any|false|none|Updated sort direction|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[SortDirection](./schemas.md#sortdirection)|false|none|Sort direction for board scores.|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|keep_strategy|any|false|none|Updated keep strategy|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[KeepStrategy](./schemas.md#keepstrategy)|false|none|Strategy for keeping scores from the same user.|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|starts_at|any|false|none|Updated start time|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string(date-time)|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|ends_at|any|false|none|Updated end time|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string(date-time)|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|tags|any|false|none|Updated tags list|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[string]|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|repeat_interval|any|false|none|Updated repeat interval|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|config|any|false|none|Updated config (reserved for procedural generation)|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|next_run_at|any|false|none|Updated next run time|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string(date-time)|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|is_active|any|false|none|Updated active status|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|boolean|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|is_published|any|false|none|Updated published status|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|boolean|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|deleted|any|false|none|Set to true to soft delete the template|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|boolean|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

## BoardUpdateRequest

```json
{
  "name": "string",
  "icon": "string",
  "short_code": "string",
  "unit": "string",
  "is_active": true,
  "is_published": true,
  "sort_direction": "ASCENDING",
  "keep_strategy": "FIRST_ONLY",
  "created_from_template_id": "string",
  "template_name": "string",
  "starts_at": "2019-08-24T14:15:22Z",
  "ends_at": "2019-08-24T14:15:22Z",
  "tags": [
    "string"
  ],
  "description": "string",
  "deleted": true
}

```

BoardUpdateRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|any|false|none|Updated board name|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|icon|any|false|none|Updated icon identifier|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|short_code|any|false|none|Updated short code|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|unit|any|false|none|Updated unit of measurement|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|is_active|any|false|none|Updated active status|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|boolean|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|is_published|any|false|none|Updated published status|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|boolean|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|sort_direction|any|false|none|Updated sort direction|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[SortDirection](./schemas.md#sortdirection)|false|none|Sort direction for board scores.|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|keep_strategy|any|false|none|Updated keep strategy|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[KeepStrategy](./schemas.md#keepstrategy)|false|none|Strategy for keeping scores from the same user.|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|created_from_template_id|any|false|none|Updated template ID|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|template_name|any|false|none|Updated template name|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|starts_at|any|false|none|Updated start time|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string(date-time)|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|ends_at|any|false|none|Updated end time|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string(date-time)|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|tags|any|false|none|Updated tags list|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[string]|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|description|any|false|none|Updated board description|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|deleted|any|false|none|Set to true to soft delete the board|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|boolean|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

## CompleteRegistrationRequest

```json
{
  "verification_token": "string",
  "account_name": "string",
  "account_slug": "string",
  "jam_code": "string",
  "display_name": "string"
}

```

CompleteRegistrationRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|verification_token|string|true|none|Token from code verification step|
|account_name|string|true|none|Name for the new account|
|account_slug|any|false|none|Optional URL slug (auto-generated if not provided)|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|jam_code|any|false|none|Optional jam/promo code|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|display_name|any|false|none|Optional display name for user (auto-generated from email if not provided)|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

## CompleteRegistrationResponse

```json
{
  "account_id": "string",
  "account_slug": "string",
  "api_key": "string",
  "display_name": "string"
}

```

CompleteRegistrationResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|account_id|string|true|none|ID of the created account|
|account_slug|string|true|none|URL slug of the account|
|api_key|string|true|none|API key for authentication|
|display_name|string|true|none|Display name of the created user|

## CreateAPIKeyRequest

```json
{
  "account_id": "string",
  "user_id": "string",
  "name": "string",
  "expires_at": "2019-08-24T14:15:22Z"
}

```

CreateAPIKeyRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|account_id|string|true|none|ID of the account this API key belongs to|
|user_id|string|true|none|ID of the user who owns this API key|
|name|string|true|none|Human-readable name for the API key (e.g., 'Production Server')|
|expires_at|any|false|none|Optional expiration timestamp (UTC). Key never expires if omitted|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string(date-time)|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

## CreateAPIKeyResponse

```json
{
  "id": "string",
  "name": "string",
  "key": "string",
  "prefix": "string",
  "status": "active",
  "expires_at": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z"
}

```

CreateAPIKeyResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|Unique identifier for the API key|
|name|string|true|none|Human-readable name for the API key|
|key|string|true|none|Plain text API key. ONLY returned at creation - save this securely!|
|prefix|string|true|none|Key prefix for identification (first 8 characters)|
|status|[APIKeyStatus](./schemas.md#apikeystatus)|true|none|Current status of the API key|
|expires_at|any|false|none|Expiration timestamp (UTC), or null if never expires|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string(date-time)|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|created_at|string(date-time)|true|none|Timestamp when the key was created (UTC)|

## CreateJamCodeRequest

```json
{
  "code": "string",
  "description": "string",
  "features": {},
  "max_uses": 0,
  "expires_at": "2019-08-24T14:15:22Z"
}

```

CreateJamCodeRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|code|string|true|none|Alphanumeric code (3-50 characters)|
|description|string|true|none|Human-readable description|
|features|object|false|none|Features/config for this code|
|max_uses|any|false|none|Maximum redemptions (null = unlimited)|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|integer|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|expires_at|any|false|none|Expiration date (null = never)|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string(date-time)|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

## DeviceResponse

```json
{
  "id": "string",
  "game_id": "string",
  "client_fingerprint": "string",
  "account_id": "string",
  "platform": "string",
  "status": "string",
  "first_seen_at": "2019-08-24T14:15:22Z",
  "last_seen_at": "2019-08-24T14:15:22Z",
  "metadata": {},
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}

```

DeviceResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|Unique identifier for the device|
|game_id|string|true|none|ID of the game this device belongs to|
|client_fingerprint|string|true|none|Client-generated SHA256 device fingerprint (64 hex characters)|
|account_id|string|true|none|ID of the account this device belongs to|
|platform|any|false|none|Platform (iOS, Android, etc.), or null|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|status|string|true|none|Device status: active, banned, or suspended|
|first_seen_at|string(date-time)|true|none|Timestamp when device was first seen (UTC)|
|last_seen_at|string(date-time)|true|none|Timestamp when device was last seen (UTC)|
|metadata|object|true|none|Additional device metadata|
|created_at|string(date-time)|true|none|Timestamp when device record was created (UTC)|
|updated_at|string(date-time)|true|none|Timestamp of last update (UTC)|

## DeviceSessionResponse

```json
{
  "id": "string",
  "device_id": "string",
  "expires_at": "2019-08-24T14:15:22Z",
  "refresh_expires_at": "2019-08-24T14:15:22Z",
  "ip_address": "string",
  "user_agent": "string",
  "revoked_at": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}

```

DeviceSessionResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|none|
|device_id|string|true|none|none|
|expires_at|string(date-time)|true|none|none|
|refresh_expires_at|string(date-time)|true|none|none|
|ip_address|any|true|none|none|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|user_agent|any|true|none|none|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|revoked_at|any|true|none|none|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string(date-time)|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|created_at|string(date-time)|true|none|none|
|updated_at|string(date-time)|true|none|none|

## DeviceSessionUpdateRequest

```json
{
  "revoked": true
}

```

DeviceSessionUpdateRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|revoked|any|false|none|none|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|boolean|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

## DeviceStatus

```json
"active"

```

DeviceStatus

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|DeviceStatus|string|false|none|Device status enumeration.|

#### Enumerated Values

|Property|Value|
|---|---|
|DeviceStatus|active|
|DeviceStatus|banned|
|DeviceStatus|suspended|

## DeviceUpdateRequest

```json
{
  "status": "string"
}

```

DeviceUpdateRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|status|any|false|none|Updated status: active, banned, or suspended|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

## GameCreateRequest

```json
{
  "account_id": "string",
  "name": "string",
  "slug": "string",
  "steam_app_id": "string",
  "default_board_id": "string",
  "anti_cheat_enabled": true,
  "description": "string",
  "tags": [
    "string"
  ],
  "page_url": "string"
}

```

GameCreateRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|account_id|string|true|none|ID of the account this game belongs to|
|name|string|true|none|Name of the game|
|slug|any|false|none|Optional URL-friendly slug (globally unique). If not provided, will be auto-generated from name|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|steam_app_id|any|false|none|Optional Steam App ID for Steam integration|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|default_board_id|any|false|none|Optional ID of the default leaderboard for this game|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|anti_cheat_enabled|boolean|false|none|Whether anti-cheat is enabled for this game (defaults to True)|
|description|any|false|none|Optional game description|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|tags|any|false|none|Optional list of tags for categorization|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[string]|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|page_url|any|false|none|Optional URL to the game's page|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

## GameResponse

```json
{
  "id": "string",
  "account_id": "string",
  "name": "string",
  "slug": "string",
  "steam_app_id": "string",
  "default_board_id": "string",
  "anti_cheat_enabled": true,
  "description": "string",
  "tags": [
    "string"
  ],
  "page_url": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}

```

GameResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|Unique identifier for the game|
|account_id|string|true|none|ID of the account this game belongs to|
|name|string|true|none|Name of the game|
|slug|string|true|none|URL-friendly slug for the game (globally unique, immutable)|
|steam_app_id|any|false|none|Steam App ID if Steam integration is configured|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|default_board_id|any|false|none|ID of the default leaderboard, or null if not set|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|anti_cheat_enabled|boolean|true|none|Whether anti-cheat is enabled for this game|
|description|any|false|none|Game description|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|tags|[string]|false|none|List of tags for categorization|
|page_url|any|false|none|URL to the game's page|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|created_at|string(date-time)|true|none|Timestamp when the game was created (UTC)|
|updated_at|string(date-time)|true|none|Timestamp of last update (UTC)|

## GameUpdateRequest

```json
{
  "name": "string",
  "steam_app_id": "string",
  "default_board_id": "string",
  "anti_cheat_enabled": true,
  "description": "string",
  "tags": [
    "string"
  ],
  "page_url": "string",
  "deleted": true
}

```

GameUpdateRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|any|false|none|Updated game name|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|steam_app_id|any|false|none|Updated Steam App ID|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|default_board_id|any|false|none|Updated default leaderboard ID|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|anti_cheat_enabled|any|false|none|Whether anti-cheat is enabled for this game|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|boolean|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|description|any|false|none|Updated game description|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|tags|any|false|none|Updated tags list|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[string]|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|page_url|any|false|none|Updated page URL|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|deleted|any|false|none|Set to true to soft delete the game|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|boolean|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

## HTTPValidationError

```json
{
  "detail": [
    {
      "loc": [
        "string"
      ],
      "msg": "string",
      "type": "string"
    }
  ]
}

```

HTTPValidationError

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|detail|[[ValidationError](./schemas.md#validationerror)]|false|none|none|

## HealthResponse

```json
{
  "service": "string",
  "status": "string",
  "database": "string"
}

```

HealthResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|service|string|true|none|The name of the service|
|status|string|true|none|Overall API health status (healthy, degraded, or unhealthy)|
|database|string|true|none|Database connection status|

## InitiateRegistrationRequest

```json
{
  "email": "user@example.com"
}

```

InitiateRegistrationRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|email|string(email)|true|none|Email address to send verification code to|

## InitiateRegistrationResponse

```json
{
  "message": "string",
  "code_expires_in": 0
}

```

InitiateRegistrationResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|message|string|true|none|Success message|
|code_expires_in|integer|true|none|Seconds until the code expires|

## JamCodeResponse

```json
{
  "id": "string",
  "code": "string",
  "description": "string",
  "features": {},
  "max_uses": 0,
  "current_uses": 0,
  "active": true,
  "expires_at": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}

```

JamCodeResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|none|
|code|string|true|none|none|
|description|string|true|none|none|
|features|object|true|none|none|
|max_uses|any|true|none|none|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|integer|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|current_uses|integer|true|none|none|
|active|boolean|true|none|none|
|expires_at|any|true|none|none|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string(date-time)|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|created_at|string(date-time)|true|none|none|
|updated_at|string(date-time)|true|none|none|

## KeepStrategy

```json
"FIRST_ONLY"

```

KeepStrategy

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|KeepStrategy|string|false|none|Strategy for keeping scores from the same user.|

#### Enumerated Values

|Property|Value|
|---|---|
|KeepStrategy|FIRST_ONLY|
|KeepStrategy|BEST_ONLY|
|KeepStrategy|LATEST_ONLY|
|KeepStrategy|ALL|

## NonceResponse

```json
{
  "nonce_value": "string",
  "expires_at": "2019-08-24T14:15:22Z"
}

```

NonceResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|nonce_value|string|true|none|Unique nonce value (UUID)|
|expires_at|string(date-time)|true|none|Nonce expiration timestamp (UTC)|

## PaginatedResponse_APIKeyResponse_

```json
{
  "data": [
    {
      "id": "scr_123",
      "value": 1000
    }
  ],
  "pagination": {
    "count": 20,
    "has_next": true,
    "has_prev": false,
    "next_cursor": "eyJwdiI6WzEwMDAsMTIzXX0="
  }
}

```

PaginatedResponse[APIKeyResponse]

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|[[APIKeyResponse](./schemas.md#apikeyresponse)]|true|none|List of items in this page|
|pagination|[PaginationMeta](./schemas.md#paginationmeta)|true|none|Pagination metadata|

## PaginatedResponse_AccountResponse_

```json
{
  "data": [
    {
      "id": "scr_123",
      "value": 1000
    }
  ],
  "pagination": {
    "count": 20,
    "has_next": true,
    "has_prev": false,
    "next_cursor": "eyJwdiI6WzEwMDAsMTIzXX0="
  }
}

```

PaginatedResponse[AccountResponse]

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|[[AccountResponse](./schemas.md#accountresponse)]|true|none|List of items in this page|
|pagination|[PaginationMeta](./schemas.md#paginationmeta)|true|none|Pagination metadata|

## PaginatedResponse_BoardResponse_

```json
{
  "data": [
    {
      "id": "scr_123",
      "value": 1000
    }
  ],
  "pagination": {
    "count": 20,
    "has_next": true,
    "has_prev": false,
    "next_cursor": "eyJwdiI6WzEwMDAsMTIzXX0="
  }
}

```

PaginatedResponse[BoardResponse]

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|[[BoardResponse](./schemas.md#boardresponse)]|true|none|List of items in this page|
|pagination|[PaginationMeta](./schemas.md#paginationmeta)|true|none|Pagination metadata|

## PaginatedResponse_BoardTemplateResponse_

```json
{
  "data": [
    {
      "id": "scr_123",
      "value": 1000
    }
  ],
  "pagination": {
    "count": 20,
    "has_next": true,
    "has_prev": false,
    "next_cursor": "eyJwdiI6WzEwMDAsMTIzXX0="
  }
}

```

PaginatedResponse[BoardTemplateResponse]

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|[[BoardTemplateResponse](./schemas.md#boardtemplateresponse)]|true|none|List of items in this page|
|pagination|[PaginationMeta](./schemas.md#paginationmeta)|true|none|Pagination metadata|

## PaginatedResponse_DeviceResponse_

```json
{
  "data": [
    {
      "id": "scr_123",
      "value": 1000
    }
  ],
  "pagination": {
    "count": 20,
    "has_next": true,
    "has_prev": false,
    "next_cursor": "eyJwdiI6WzEwMDAsMTIzXX0="
  }
}

```

PaginatedResponse[DeviceResponse]

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|[[DeviceResponse](./schemas.md#deviceresponse)]|true|none|List of items in this page|
|pagination|[PaginationMeta](./schemas.md#paginationmeta)|true|none|Pagination metadata|

## PaginatedResponse_DeviceSessionResponse_

```json
{
  "data": [
    {
      "id": "scr_123",
      "value": 1000
    }
  ],
  "pagination": {
    "count": 20,
    "has_next": true,
    "has_prev": false,
    "next_cursor": "eyJwdiI6WzEwMDAsMTIzXX0="
  }
}

```

PaginatedResponse[DeviceSessionResponse]

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|[[DeviceSessionResponse](./schemas.md#devicesessionresponse)]|true|none|List of items in this page|
|pagination|[PaginationMeta](./schemas.md#paginationmeta)|true|none|Pagination metadata|

## PaginatedResponse_GameResponse_

```json
{
  "data": [
    {
      "id": "scr_123",
      "value": 1000
    }
  ],
  "pagination": {
    "count": 20,
    "has_next": true,
    "has_prev": false,
    "next_cursor": "eyJwdiI6WzEwMDAsMTIzXX0="
  }
}

```

PaginatedResponse[GameResponse]

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|[[GameResponse](./schemas.md#gameresponse)]|true|none|List of items in this page|
|pagination|[PaginationMeta](./schemas.md#paginationmeta)|true|none|Pagination metadata|

## PaginatedResponse_ScoreClientResponse_

```json
{
  "data": [
    {
      "id": "scr_123",
      "value": 1000
    }
  ],
  "pagination": {
    "count": 20,
    "has_next": true,
    "has_prev": false,
    "next_cursor": "eyJwdiI6WzEwMDAsMTIzXX0="
  }
}

```

PaginatedResponse[ScoreClientResponse]

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|[[ScoreClientResponse](./schemas.md#scoreclientresponse)]|true|none|List of items in this page|
|pagination|[PaginationMeta](./schemas.md#paginationmeta)|true|none|Pagination metadata|

## PaginatedResponse_ScoreResponse_

```json
{
  "data": [
    {
      "id": "scr_123",
      "value": 1000
    }
  ],
  "pagination": {
    "count": 20,
    "has_next": true,
    "has_prev": false,
    "next_cursor": "eyJwdiI6WzEwMDAsMTIzXX0="
  }
}

```

PaginatedResponse[ScoreResponse]

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|[[ScoreResponse](./schemas.md#scoreresponse)]|true|none|List of items in this page|
|pagination|[PaginationMeta](./schemas.md#paginationmeta)|true|none|Pagination metadata|

## PaginatedResponse_UserResponse_

```json
{
  "data": [
    {
      "id": "scr_123",
      "value": 1000
    }
  ],
  "pagination": {
    "count": 20,
    "has_next": true,
    "has_prev": false,
    "next_cursor": "eyJwdiI6WzEwMDAsMTIzXX0="
  }
}

```

PaginatedResponse[UserResponse]

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|[[UserResponse](./schemas.md#userresponse)]|true|none|List of items in this page|
|pagination|[PaginationMeta](./schemas.md#paginationmeta)|true|none|Pagination metadata|

## PaginationMeta

```json
{
  "next_cursor": "string",
  "prev_cursor": "string",
  "has_next": true,
  "has_prev": true,
  "count": 0
}

```

PaginationMeta

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|next_cursor|any|false|none|Cursor for the next page of results|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|prev_cursor|any|false|none|Cursor for the previous page of results|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|has_next|boolean|true|none|Whether there are more results after this page|
|has_prev|boolean|true|none|Whether there are results before this page|
|count|integer|true|none|Number of items in this page|

## RefreshTokenRequest

```json
{
  "refresh_token": "string"
}

```

RefreshTokenRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|refresh_token|string|true|none|JWT refresh token obtained from start_session|

## RefreshTokenResponse

```json
{
  "access_token": "string",
  "refresh_token": "string",
  "expires_in": 0
}

```

RefreshTokenResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|access_token|string|true|none|New JWT access token|
|refresh_token|string|true|none|New JWT refresh token (old token is invalidated)|
|expires_in|integer|true|none|Access token expiration time in seconds|

## ScoreClientCreateRequest

```json
{
  "board_id": "string",
  "player_name": "string",
  "value": 0,
  "value_display": "string",
  "metadata": {}
}

```

ScoreClientCreateRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|board_id|string|true|none|ID of the board this score belongs to|
|player_name|string|true|none|Display name of the player|
|value|number|true|none|Numeric value of the score for sorting/comparison|
|value_display|any|false|none|Optional formatted display string (e.g., '1:23.45', '1,234 points')|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|metadata|any|false|none|Optional JSON metadata for game-specific data (max 1KB)|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|any|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

## ScoreClientResponse

```json
{
  "id": "string",
  "account_id": "string",
  "game_id": "string",
  "board_id": "string",
  "player_name": "string",
  "value": 0,
  "value_display": "string",
  "metadata": {},
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}

```

ScoreClientResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|Unique identifier for the score|
|account_id|string|true|none|ID of the account this score belongs to|
|game_id|string|true|none|ID of the game this score belongs to|
|board_id|string|true|none|ID of the board this score belongs to|
|player_name|string|true|none|Display name of the player|
|value|number|true|none|Numeric value of the score|
|value_display|any|false|none|Formatted display string, or null|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|metadata|any|false|none|Game-specific metadata, or null|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|any|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|created_at|string(date-time)|true|none|Timestamp when the score was created (UTC)|
|updated_at|string(date-time)|true|none|Timestamp of last update (UTC)|

## ScoreCreateRequest

```json
{
  "board_id": "string",
  "player_name": "string",
  "value": 0,
  "value_display": "string",
  "metadata": {},
  "account_id": "string",
  "game_id": "string",
  "device_id": "string",
  "timezone": "string",
  "country": "string",
  "city": "string"
}

```

ScoreCreateRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|board_id|string|true|none|ID of the board this score belongs to|
|player_name|string|true|none|Display name of the player|
|value|number|true|none|Numeric value of the score for sorting/comparison|
|value_display|any|false|none|Optional formatted display string (e.g., '1:23.45', '1,234 points')|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|metadata|any|false|none|Optional JSON metadata for game-specific data (max 1KB)|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|any|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|account_id|any|false|none|ID of the account (only for superadmins, regular admins use their auth account)|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|game_id|string|true|none|ID of the game this score belongs to (required for admin API)|
|device_id|string|true|none|ID of the device that submitted this score (required for admin API)|
|timezone|any|false|none|Optional override of GeoIP metadata|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|country|any|false|none|Optional override of GeoIP metadata|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|city|any|false|none|Optional override of GeoIP metadata|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

## ScoreFlagResponse

```json
{
  "id": "string",
  "score_id": "string",
  "flag_type": "string",
  "confidence": "string",
  "metadata": {},
  "status": "string",
  "reviewed_at": "2019-08-24T14:15:22Z",
  "reviewer_id": "string",
  "reviewer_decision": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}

```

ScoreFlagResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|Unique identifier for the score flag|
|score_id|string|true|none|ID of the score that was flagged|
|flag_type|string|true|none|Type of flag (e.g., VELOCITY, DUPLICATE, RATE_LIMIT)|
|confidence|string|true|none|Confidence level of the flag (LOW, MEDIUM, HIGH)|
|metadata|object|true|none|Additional metadata about the flag|
|status|string|true|none|Status: PENDING, CONFIRMED_CHEAT, FALSE_POSITIVE, or DISMISSED|
|reviewed_at|any|false|none|Timestamp when flag was reviewed, or null|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string(date-time)|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|reviewer_id|any|false|none|ID of the user who reviewed this flag, or null|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|reviewer_decision|any|false|none|Admin's decision/notes, or null|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|created_at|string(date-time)|true|none|Timestamp when the flag was created (UTC)|
|updated_at|string(date-time)|true|none|Timestamp of last update (UTC)|

## ScoreFlagUpdateRequest

```json
{
  "status": "string",
  "reviewer_decision": "string",
  "deleted": true
}

```

ScoreFlagUpdateRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|status|any|false|none|Updated status: PENDING, CONFIRMED_CHEAT, FALSE_POSITIVE, or DISMISSED|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|reviewer_decision|any|false|none|Admin's decision/notes about the flag|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|deleted|any|false|none|Set to true to soft delete the flag|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|boolean|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

## ScoreResponse

```json
{
  "id": "string",
  "account_id": "string",
  "game_id": "string",
  "board_id": "string",
  "device_id": "string",
  "player_name": "string",
  "value": 0,
  "value_display": "string",
  "timezone": "string",
  "country": "string",
  "city": "string",
  "metadata": {},
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}

```

ScoreResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|Unique identifier for the score|
|account_id|string|true|none|ID of the account this score belongs to|
|game_id|string|true|none|ID of the game this score belongs to|
|board_id|string|true|none|ID of the board this score belongs to|
|device_id|string|true|none|ID of the device that submitted this score|
|player_name|string|true|none|Display name of the player|
|value|number|true|none|Numeric value of the score|
|value_display|any|false|none|Formatted display string, or null|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|timezone|any|false|none|Timezone for categorization, or null|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|country|any|false|none|Country for categorization, or null|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|city|any|false|none|City for categorization, or null|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|metadata|any|false|none|Game-specific metadata, or null|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|any|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|created_at|string(date-time)|true|none|Timestamp when the score was created (UTC)|
|updated_at|string(date-time)|true|none|Timestamp of last update (UTC)|

## ScoreSubmissionMetaResponse

```json
{
  "id": "string",
  "score_id": "string",
  "device_id": "string",
  "board_id": "string",
  "submission_count": 0,
  "last_submission_at": "2019-08-24T14:15:22Z",
  "last_score_value": 0,
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}

```

ScoreSubmissionMetaResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|none|
|score_id|string|true|none|none|
|device_id|string|true|none|none|
|board_id|string|true|none|none|
|submission_count|integer|true|none|none|
|last_submission_at|string(date-time)|true|none|none|
|last_score_value|any|true|none|none|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|number|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|created_at|string(date-time)|true|none|none|
|updated_at|string(date-time)|true|none|none|

## ScoreUpdateRequest

```json
{
  "player_name": "string",
  "value": 0,
  "value_display": "string",
  "timezone": "string",
  "country": "string",
  "city": "string",
  "metadata": {},
  "deleted": true
}

```

ScoreUpdateRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|player_name|any|false|none|Updated player name|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|value|any|false|none|Updated score value|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|number|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|value_display|any|false|none|Updated display string|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|timezone|any|false|none|Updated timezone|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|country|any|false|none|Updated country|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|city|any|false|none|Updated city|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|metadata|any|false|none|Updated metadata|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|any|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|deleted|any|false|none|Set to true to soft delete the score|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|boolean|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

## SortDirection

```json
"ASCENDING"

```

SortDirection

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|SortDirection|string|false|none|Sort direction for board scores.|

#### Enumerated Values

|Property|Value|
|---|---|
|SortDirection|ASCENDING|
|SortDirection|DESCENDING|

## StartSessionRequest

```json
{
  "game_id": "string",
  "client_fingerprint": "string",
  "platform": "string",
  "metadata": {}
}

```

StartSessionRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|game_id|string|true|none|ID of the game this device belongs to|
|client_fingerprint|string|true|none|Client-generated SHA256 device fingerprint (64 hex characters)|
|platform|any|false|none|Device platform (e.g., 'ios', 'android', 'pc', 'console')|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|metadata|any|false|none|Optional device metadata (e.g., OS version, device model)|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

## StartSessionResponse

```json
{
  "id": "string",
  "game_id": "string",
  "client_fingerprint": "string",
  "account_id": "string",
  "platform": "string",
  "status": "active",
  "metadata": {},
  "access_token": "string",
  "refresh_token": "string",
  "expires_in": 0,
  "first_seen_at": "2019-08-24T14:15:22Z",
  "last_seen_at": "2019-08-24T14:15:22Z"
}

```

StartSessionResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|Unique identifier for the device|
|game_id|string|true|none|ID of the game|
|client_fingerprint|string|true|none|Client-generated SHA256 device fingerprint (64 hex characters)|
|account_id|string|true|none|ID of the account that owns the game|
|platform|any|false|none|Device platform|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|status|[DeviceStatus](./schemas.md#devicestatus)|true|none|Device status (active, suspended, banned)|
|metadata|object|false|none|Device metadata|
|access_token|string|true|none|JWT access token for authenticating API requests|
|refresh_token|string|true|none|JWT refresh token for obtaining new access tokens|
|expires_in|integer|true|none|Access token expiration time in seconds|
|first_seen_at|string(date-time)|true|none|Timestamp when device was first seen (UTC)|
|last_seen_at|string(date-time)|true|none|Timestamp when device was last seen (UTC)|

## UpdateAPIKeyRequest

```json
{
  "status": "active",
  "deleted": true
}

```

UpdateAPIKeyRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|status|any|false|none|Updated status (use 'revoked' to disable key)|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[APIKeyStatus](./schemas.md#apikeystatus)|false|none|API Key status enumeration.|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|deleted|any|false|none|Set to true to soft delete the key|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|boolean|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

## UpdateJamCodeRequest

```json
{
  "description": "string",
  "features": {},
  "max_uses": 0,
  "active": true,
  "expires_at": "2019-08-24T14:15:22Z"
}

```

UpdateJamCodeRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|description|any|false|none|New description|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|features|any|false|none|New features/config|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|max_uses|any|false|none|New max uses|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|integer|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|active|any|false|none|New active status|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|boolean|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|expires_at|any|false|none|New expiration date|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string(date-time)|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

## UserCreateRequest

```json
{
  "account_id": "string",
  "email": "user@example.com",
  "display_name": "string"
}

```

UserCreateRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|account_id|string|true|none|ID of the account this user belongs to|
|email|string(email)|true|none|User's email address (must be valid email format)|
|display_name|string|true|none|User's display name (2-100 characters)|

## UserResponse

```json
{
  "id": "string",
  "account_id": "string",
  "email": "string",
  "display_name": "string",
  "super_admin": true,
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}

```

UserResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|Unique identifier for the user|
|account_id|string|true|none|ID of the account this user belongs to|
|email|string|true|none|User's email address|
|display_name|string|true|none|User's display name|
|super_admin|boolean|true|none|Whether this user has superadmin privileges|
|created_at|string(date-time)|true|none|Timestamp when the user was created (UTC)|
|updated_at|string(date-time)|true|none|Timestamp of last update (UTC)|

## UserUpdateRequest

```json
{
  "email": "user@example.com",
  "display_name": "string",
  "super_admin": true,
  "deleted": true
}

```

UserUpdateRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|email|any|false|none|Updated email address|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string(email)|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|display_name|any|false|none|Updated display name|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|super_admin|any|false|none|Set superadmin privileges (true/false)|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|boolean|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|deleted|any|false|none|Set to true to soft delete the user|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|boolean|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

## ValidationError

```json
{
  "loc": [
    "string"
  ],
  "msg": "string",
  "type": "string"
}

```

ValidationError

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|loc|[anyOf]|true|none|none|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|integer|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|msg|string|true|none|none|
|type|string|true|none|none|

## VerifyCodeRequest

```json
{
  "email": "user@example.com",
  "code": "string"
}

```

VerifyCodeRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|email|string(email)|true|none|Email address|
|code|string|true|none|6-character verification code|

## VerifyCodeResponse

```json
{
  "verification_token": "string",
  "expires_in": 0
}

```

VerifyCodeResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|verification_token|string|true|none|Temporary token for completing registration|
|expires_in|integer|true|none|Seconds until the token expires|
