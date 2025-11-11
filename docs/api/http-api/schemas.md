# Schemas

## APIKeyResponse

```json
{
  "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",
  "account_id": "449e7a5c-69d3-4b8a-aaaf-5c9b713ebc65",
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
|id|string(uuid)|true|none|Unique identifier for the API key|
|account_id|string(uuid)|true|none|ID of the account this key belongs to|
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
|slug|string|true|none|URL-friendly identifier for the account (lowercase, alphanumeric, hyphens)|

## AccountResponse

```json
{
  "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",
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
|id|string(uuid)|true|none|Unique identifier for the account|
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
  "account_id": "449e7a5c-69d3-4b8a-aaaf-5c9b713ebc65",
  "game_id": "129babd7-0a5a-4108-81e4-77c8f2b49aed",
  "name": "string",
  "icon": "string",
  "short_code": "string",
  "unit": "string",
  "is_active": true,
  "sort_direction": "ASCENDING",
  "keep_strategy": "BEST_ONLY",
  "template_id": "c6d67e98-83ea-49f0-8812-e4abae2b68bc",
  "template_name": "string",
  "starts_at": "2019-08-24T14:15:22Z",
  "ends_at": "2019-08-24T14:15:22Z",
  "tags": [
    "string"
  ]
}

```

BoardCreateRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|account_id|string(uuid)|true|none|ID of the account this board belongs to|
|game_id|string(uuid)|true|none|ID of the game this board belongs to|
|name|string|true|none|Name of the board|
|icon|string|true|none|Icon identifier for the board|
|short_code|string|true|none|Globally unique short code for direct sharing|
|unit|string|true|none|Unit of measurement for scores (e.g., 'seconds', 'points')|
|is_active|boolean|true|none|Whether the board is currently active|
|sort_direction|[SortDirection](./schemas.md#sortdirection)|true|none|Direction to sort scores|
|keep_strategy|[KeepStrategy](./schemas.md#keepstrategy)|true|none|Strategy for keeping multiple scores from the same user|
|template_id|any|false|none|Optional template ID this board was created from|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string(uuid)|false|none|none|

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

## BoardResponse

```json
{
  "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",
  "account_id": "449e7a5c-69d3-4b8a-aaaf-5c9b713ebc65",
  "game_id": "129babd7-0a5a-4108-81e4-77c8f2b49aed",
  "name": "string",
  "icon": "string",
  "short_code": "string",
  "unit": "string",
  "is_active": true,
  "sort_direction": "ASCENDING",
  "keep_strategy": "BEST_ONLY",
  "template_id": "c6d67e98-83ea-49f0-8812-e4abae2b68bc",
  "template_name": "string",
  "starts_at": "2019-08-24T14:15:22Z",
  "ends_at": "2019-08-24T14:15:22Z",
  "tags": [
    "string"
  ],
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}

```

BoardResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string(uuid)|true|none|Unique identifier for the board|
|account_id|string(uuid)|true|none|ID of the account this board belongs to|
|game_id|string(uuid)|true|none|ID of the game this board belongs to|
|name|string|true|none|Name of the board|
|icon|string|true|none|Icon identifier for the board|
|short_code|string|true|none|Globally unique short code for direct sharing|
|unit|string|true|none|Unit of measurement for scores|
|is_active|boolean|true|none|Whether the board is currently active|
|sort_direction|[SortDirection](./schemas.md#sortdirection)|true|none|Direction to sort scores|
|keep_strategy|[KeepStrategy](./schemas.md#keepstrategy)|true|none|Strategy for keeping scores from same user|
|template_id|any|false|none|Template ID this board was created from, or null|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string(uuid)|false|none|none|

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
|created_at|string(date-time)|true|none|Timestamp when the board was created (UTC)|
|updated_at|string(date-time)|true|none|Timestamp of last update (UTC)|

## BoardUpdateRequest

```json
{
  "name": "string",
  "icon": "string",
  "short_code": "string",
  "unit": "string",
  "is_active": true,
  "sort_direction": "ASCENDING",
  "keep_strategy": "BEST_ONLY",
  "template_id": "c6d67e98-83ea-49f0-8812-e4abae2b68bc",
  "template_name": "string",
  "starts_at": "2019-08-24T14:15:22Z",
  "ends_at": "2019-08-24T14:15:22Z",
  "tags": [
    "string"
  ],
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
|template_id|any|false|none|Updated template ID|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string(uuid)|false|none|none|

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
|deleted|any|false|none|Set to true to soft delete the board|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|boolean|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

## CreateAPIKeyRequest

```json
{
  "account_id": "449e7a5c-69d3-4b8a-aaaf-5c9b713ebc65",
  "name": "string",
  "expires_at": "2019-08-24T14:15:22Z"
}

```

CreateAPIKeyRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|account_id|string(uuid)|true|none|ID of the account this API key belongs to|
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
  "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",
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
|id|string(uuid)|true|none|Unique identifier for the API key|
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

## GameCreateRequest

```json
{
  "account_id": "449e7a5c-69d3-4b8a-aaaf-5c9b713ebc65",
  "name": "string",
  "steam_app_id": "string",
  "default_board_id": "d242572a-54cf-433e-9831-a8453b36773b"
}

```

GameCreateRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|account_id|string(uuid)|true|none|ID of the account this game belongs to|
|name|string|true|none|Name of the game|
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
|» *anonymous*|string(uuid)|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

## GameResponse

```json
{
  "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",
  "account_id": "449e7a5c-69d3-4b8a-aaaf-5c9b713ebc65",
  "name": "string",
  "steam_app_id": "string",
  "default_board_id": "d242572a-54cf-433e-9831-a8453b36773b",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}

```

GameResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string(uuid)|true|none|Unique identifier for the game|
|account_id|string(uuid)|true|none|ID of the account this game belongs to|
|name|string|true|none|Name of the game|
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
|» *anonymous*|string(uuid)|false|none|none|

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
  "default_board_id": "d242572a-54cf-433e-9831-a8453b36773b",
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
|» *anonymous*|string(uuid)|false|none|none|

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
  "status": "string",
  "database": "string"
}

```

HealthResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|status|string|true|none|Overall API health status (healthy, degraded, or unhealthy)|
|database|string|true|none|Database connection status|

## KeepStrategy

```json
"BEST_ONLY"

```

KeepStrategy

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|KeepStrategy|string|false|none|Strategy for keeping scores from the same user.|

#### Enumerated Values

|Property|Value|
|---|---|
|KeepStrategy|BEST_ONLY|
|KeepStrategy|LATEST_ONLY|
|KeepStrategy|ALL|

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

## UserCreateRequest

```json
{
  "account_id": "449e7a5c-69d3-4b8a-aaaf-5c9b713ebc65",
  "email": "user@example.com",
  "display_name": "string"
}

```

UserCreateRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|account_id|string(uuid)|true|none|ID of the account this user belongs to|
|email|string(email)|true|none|User's email address (must be valid email format)|
|display_name|string|true|none|User's display name (2-100 characters)|

## UserResponse

```json
{
  "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",
  "account_id": "449e7a5c-69d3-4b8a-aaaf-5c9b713ebc65",
  "email": "string",
  "display_name": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}

```

UserResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string(uuid)|true|none|Unique identifier for the user|
|account_id|string(uuid)|true|none|ID of the account this user belongs to|
|email|string|true|none|User's email address|
|display_name|string|true|none|User's display name|
|created_at|string(date-time)|true|none|Timestamp when the user was created (UTC)|
|updated_at|string(date-time)|true|none|Timestamp of last update (UTC)|

## UserUpdateRequest

```json
{
  "email": "user@example.com",
  "display_name": "string",
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
