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
  "timezone": "string",
  "country": "string",
  "city": "string",
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
|timezone|any|true|none|Timezone from registration GeoIP|

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
|country|any|true|none|Country code from registration GeoIP|

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
|city|any|true|none|City name from registration GeoIP|

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
  "deleted": true,
  "timezone": "string",
  "country": "string",
  "city": "string"
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

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|timezone|any|false|none|Timezone (IANA format)|

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
|country|any|false|none|Country code (ISO 2-letter)|

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
|city|any|false|none|City name|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

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
  "board_type": "RUN_IDENTITY",
  "keep_strategy": "FIRST",
  "created_from_template_id": "string",
  "template_name": "string",
  "starts_at": "2019-08-24T14:15:22Z",
  "ends_at": "2019-08-24T14:15:22Z",
  "tags": [
    "string"
  ],
  "description": "string",
  "ratio_config": {
    "numerator_board_id": "string",
    "denominator_board_id": "string",
    "zero_denominator_policy": "NULL",
    "min_denominator": 0,
    "min_numerator": 0,
    "scale": 1000000,
    "display": "RAW",
    "decimals": 2,
    "tie_breaker": "NUMERATOR_DESC_DENOMINATOR_ASC"
  }
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
|board_type|[BoardType](./schemas.md#boardtype)|false|none|Type of board determining score behavior|
|keep_strategy|any|false|none|Strategy for keeping scores (RUN_IDENTITY boards only). Defaults to BEST for RUN_IDENTITY, ignored for other board types.|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[KeepStrategy](./schemas.md#keepstrategy)|false|none|Strategy for keeping scores from the same user (RUN_IDENTITY boards only).|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
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

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|ratio_config|any|false|none|Ratio config (required when board_type is RATIO)|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[BoardRatioConfigRequest](./schemas.md#boardratioconfigrequest)|false|none|Request model for ratio config when creating/updating a RATIO board.|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

## BoardRatioConfigRequest

```json
{
  "numerator_board_id": "string",
  "denominator_board_id": "string",
  "zero_denominator_policy": "NULL",
  "min_denominator": 0,
  "min_numerator": 0,
  "scale": 1000000,
  "display": "RAW",
  "decimals": 2,
  "tie_breaker": "NUMERATOR_DESC_DENOMINATOR_ASC"
}

```

BoardRatioConfigRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|numerator_board_id|string|true|none|ID of the numerator board|
|denominator_board_id|string|true|none|ID of the denominator board|
|zero_denominator_policy|[ZeroDenominatorPolicy](./schemas.md#zerodenominatorpolicy)|false|none|How to handle zero denominators|
|min_denominator|number|false|none|Minimum denominator value for ranking eligibility|
|min_numerator|number|false|none|Minimum numerator value for ranking eligibility|
|scale|integer|false|none|Scaling factor for ratio storage precision|
|display|[RatioDisplay](./schemas.md#ratiodisplay)|false|none|Display format for ratio values|
|decimals|integer|false|none|Number of decimal places for display|
|tie_breaker|[TieBreaker](./schemas.md#tiebreaker)|false|none|Strategy for breaking ties|

## BoardRatioConfigResponse

```json
{
  "id": "string",
  "numerator_board_id": "string",
  "denominator_board_id": "string",
  "zero_denominator_policy": "NULL",
  "min_denominator": 0,
  "min_numerator": 0,
  "scale": 0,
  "display": "RAW",
  "decimals": 0,
  "tie_breaker": "NUMERATOR_DESC_DENOMINATOR_ASC",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}

```

BoardRatioConfigResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|Unique identifier for the ratio config|
|numerator_board_id|string|true|none|ID of the numerator board|
|denominator_board_id|string|true|none|ID of the denominator board|
|zero_denominator_policy|[ZeroDenominatorPolicy](./schemas.md#zerodenominatorpolicy)|true|none|How zero denominators are handled|
|min_denominator|number|true|none|Minimum denominator for ranking eligibility|
|min_numerator|number|true|none|Minimum numerator for ranking eligibility|
|scale|integer|true|none|Scaling factor for ratio storage|
|display|[RatioDisplay](./schemas.md#ratiodisplay)|true|none|Display format for ratio values|
|decimals|integer|true|none|Number of decimal places for display|
|tie_breaker|[TieBreaker](./schemas.md#tiebreaker)|true|none|Strategy for breaking ties|
|created_at|string(date-time)|true|none|Timestamp when the config was created (UTC)|
|updated_at|string(date-time)|true|none|Timestamp of last update (UTC)|

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
  "board_type": "RUN_IDENTITY",
  "keep_strategy": "FIRST",
  "created_from_template_id": "string",
  "template_name": "string",
  "starts_at": "2019-08-24T14:15:22Z",
  "ends_at": "2019-08-24T14:15:22Z",
  "tags": [
    "string"
  ],
  "description": "string",
  "ratio_config": {
    "id": "string",
    "numerator_board_id": "string",
    "denominator_board_id": "string",
    "zero_denominator_policy": "NULL",
    "min_denominator": 0,
    "min_numerator": 0,
    "scale": 0,
    "display": "RAW",
    "decimals": 0,
    "tie_breaker": "NUMERATOR_DESC_DENOMINATOR_ASC",
    "created_at": "2019-08-24T14:15:22Z",
    "updated_at": "2019-08-24T14:15:22Z"
  },
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z",
  "url_short": "string"
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
|board_type|[BoardType](./schemas.md#boardtype)|true|none|Type of board determining score behavior|
|keep_strategy|[KeepStrategy](./schemas.md#keepstrategy)|true|none|Strategy for keeping scores (RUN_IDENTITY only)|
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
|ratio_config|any|false|none|Ratio config (present only for RATIO boards)|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[BoardRatioConfigResponse](./schemas.md#boardratioconfigresponse)|false|none|Response model for ratio config.|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|created_at|string(date-time)|true|none|Timestamp when the board was created (UTC)|
|updated_at|string(date-time)|true|none|Timestamp of last update (UTC)|
|url_short|any|true|read-only|Short URL for direct board access via short_code.<br><br>Returns the URL if BOARDS_UI_DOMAIN is configured and the board is published,<br>otherwise None.|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

## BoardStateResponse

```json
{
  "id": "string",
  "board_id": "string",
  "identity_id": "string",
  "primary_value": 0,
  "aux": {},
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}

```

BoardStateResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|Unique identifier for the board state|
|board_id|string|true|none|ID of the board this state belongs to|
|identity_id|string|true|none|ID of the identity this state is for|
|primary_value|any|false|none|Rankable value (null if not rankable)|

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
|aux|any|false|none|Board-type-specific auxiliary data|

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
|created_at|string(date-time)|true|none|Timestamp when the state was created (UTC)|
|updated_at|string(date-time)|true|none|Timestamp when the state was last updated (UTC)|

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
  "keep_strategy": "FIRST",
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
  "keep_strategy": "FIRST",
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
  "keep_strategy": "FIRST",
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
|» *anonymous*|[KeepStrategy](./schemas.md#keepstrategy)|false|none|Strategy for keeping scores from the same user (RUN_IDENTITY boards only).|

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

## BoardType

```json
"RUN_IDENTITY"

```

BoardType

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|BoardType|string|false|none|Type of board determining score behavior.|

#### Enumerated Values

|Property|Value|
|---|---|
|BoardType|RUN_IDENTITY|
|BoardType|RUN_RUNS|
|BoardType|COUNTER|
|BoardType|RATIO|

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
  "board_type": "RUN_IDENTITY",
  "keep_strategy": "FIRST",
  "created_from_template_id": "string",
  "template_name": "string",
  "starts_at": "2019-08-24T14:15:22Z",
  "ends_at": "2019-08-24T14:15:22Z",
  "tags": [
    "string"
  ],
  "description": "string",
  "deleted": true,
  "ratio_config": {
    "numerator_board_id": "string",
    "denominator_board_id": "string",
    "zero_denominator_policy": "NULL",
    "min_denominator": 0,
    "min_numerator": 0,
    "scale": 1000000,
    "display": "RAW",
    "decimals": 2,
    "tie_breaker": "NUMERATOR_DESC_DENOMINATOR_ASC"
  }
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
|board_type|any|false|none|Updated board type|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[BoardType](./schemas.md#boardtype)|false|none|Type of board determining score behavior.|

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
|» *anonymous*|[KeepStrategy](./schemas.md#keepstrategy)|false|none|Strategy for keeping scores from the same user (RUN_IDENTITY boards only).|

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

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|ratio_config|any|false|none|Updated ratio config (for RATIO boards only)|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[BoardRatioConfigRequest](./schemas.md#boardratioconfigrequest)|false|none|Request model for ratio config when creating/updating a RATIO board.|

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
|account_name|any|false|none|Name for the new account (required for registration, ignored for invite)|

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
  "account_name": "string",
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
|account_name|string|true|none|Name of the account|
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

## FlagConfidence

```json
"low"

```

FlagConfidence

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|FlagConfidence|string|false|none|Confidence level for anti-cheat detection.<br><br>Determines the action taken when a flag is raised:<br>- HIGH: Auto-reject submission<br>- MEDIUM: Flag for manual review, accept submission<br>- LOW: Log for analysis, accept submission|

#### Enumerated Values

|Property|Value|
|---|---|
|FlagConfidence|low|
|FlagConfidence|medium|
|FlagConfidence|high|

## FlagType

```json
"rate_limit"

```

FlagType

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|FlagType|string|false|none|Type of anti-cheat flag detected.<br><br>Each flag type represents a different detection tactic used to identify<br>potentially suspicious score submissions.|

#### Enumerated Values

|Property|Value|
|---|---|
|FlagType|rate_limit|
|FlagType|duplicate|
|FlagType|velocity|
|FlagType|outlier|
|FlagType|impossible_value|
|FlagType|pattern|
|FlagType|progression|
|FlagType|cluster|
|FlagType|manual|

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
  "updated_at": "2019-08-24T14:15:22Z",
  "url": "string"
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
|url|any|true|read-only|Public URL to view this game's leaderboards.<br><br>Returns the URL if BOARDS_UI_DOMAIN is configured, otherwise None.|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

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

## IdentityKind

```json
"DEVICE"

```

IdentityKind

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|IdentityKind|string|false|none|Identity provider type enumeration.|

#### Enumerated Values

|Property|Value|
|---|---|
|IdentityKind|DEVICE|
|IdentityKind|STEAM|
|IdentityKind|CUSTOM|

## IdentityResponse

```json
{
  "id": "string",
  "account_id": "string",
  "game_id": "string",
  "kind": "string",
  "external_key": "string",
  "display_name": "string",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}

```

IdentityResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|Unique identifier for the identity|
|account_id|string|true|none|ID of the account this identity belongs to|
|game_id|string|true|none|ID of the game this identity belongs to|
|kind|string|true|none|Identity kind: DEVICE, STEAM, or CUSTOM|
|external_key|string|true|none|External identifier (device ID, Steam ID, etc.)|
|display_name|any|false|none|Player display name|

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
|created_at|string(date-time)|true|none|Timestamp when identity was created (UTC)|
|updated_at|string(date-time)|true|none|Timestamp of last update (UTC)|

## IdentitySessionResponse

```json
{
  "id": "string",
  "identity_id": "string",
  "expires_at": "2019-08-24T14:15:22Z",
  "refresh_expires_at": "2019-08-24T14:15:22Z",
  "revoked_at": "2019-08-24T14:15:22Z",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}

```

IdentitySessionResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|Unique identifier for the session|
|identity_id|string|true|none|ID of the identity this session belongs to|
|expires_at|string(date-time)|true|none|Access token expiration time (UTC)|
|refresh_expires_at|string(date-time)|true|none|Refresh token expiration time (UTC)|
|revoked_at|any|false|none|Time when session was revoked|

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
|created_at|string(date-time)|true|none|Timestamp when session was created (UTC)|
|updated_at|string(date-time)|true|none|Timestamp of last update (UTC)|

## IdentityUpdateRequest

```json
{
  "display_name": "string",
  "deleted": true
}

```

IdentityUpdateRequest

### Properties

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
|deleted|any|false|none|Set to true to soft-delete the identity|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|boolean|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

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

## InviteUserRequest

```json
{
  "email": "user@example.com",
  "display_name": "string"
}

```

InviteUserRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|email|string(email)|true|none|Email address to invite|
|display_name|any|false|none|Optional display name (defaults to email prefix if not provided)|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

## InviteUserResponse

```json
{
  "user_id": "string",
  "email": "string",
  "status": "string",
  "message": "string"
}

```

InviteUserResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|user_id|string|true|none|ID of the invited user|
|email|string|true|none|Email address of the invited user|
|status|string|true|none|User status (INVITED)|
|message|string|true|none|Success message|

## IsTestFilter

```json
"true"

```

IsTestFilter

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|IsTestFilter|string|false|none|Filter options for is_test query parameter in admin score listing.|

#### Enumerated Values

|Property|Value|
|---|---|
|IsTestFilter|true|
|IsTestFilter|false|
|IsTestFilter|all|

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
"FIRST"

```

KeepStrategy

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|KeepStrategy|string|false|none|Strategy for keeping scores from the same user (RUN_IDENTITY boards only).|

#### Enumerated Values

|Property|Value|
|---|---|
|KeepStrategy|FIRST|
|KeepStrategy|BEST|
|KeepStrategy|LATEST|
|KeepStrategy|NA|

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

## PaginatedResponse_BoardStateResponse_

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

PaginatedResponse[BoardStateResponse]

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|[[BoardStateResponse](./schemas.md#boardstateresponse)]|true|none|List of items in this page|
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

## PaginatedResponse_IdentityResponse_

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

PaginatedResponse[IdentityResponse]

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|[[IdentityResponse](./schemas.md#identityresponse)]|true|none|List of items in this page|
|pagination|[PaginationMeta](./schemas.md#paginationmeta)|true|none|Pagination metadata|

## PaginatedResponse_IdentitySessionResponse_

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

PaginatedResponse[IdentitySessionResponse]

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|[[IdentitySessionResponse](./schemas.md#identitysessionresponse)]|true|none|List of items in this page|
|pagination|[PaginationMeta](./schemas.md#paginationmeta)|true|none|Pagination metadata|

## PaginatedResponse_JamCodeResponse_

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

PaginatedResponse[JamCodeResponse]

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|[[JamCodeResponse](./schemas.md#jamcoderesponse)]|true|none|List of items in this page|
|pagination|[PaginationMeta](./schemas.md#paginationmeta)|true|none|Pagination metadata|

## PaginatedResponse_RunEntryResponse_

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

PaginatedResponse[RunEntryResponse]

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|[[RunEntryResponse](./schemas.md#runentryresponse)]|true|none|List of items in this page|
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

## PaginatedResponse_ScoreEventResponse_

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

PaginatedResponse[ScoreEventResponse]

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|[[ScoreEventResponse](./schemas.md#scoreeventresponse)]|true|none|List of items in this page|
|pagination|[PaginationMeta](./schemas.md#paginationmeta)|true|none|Pagination metadata|

## PaginatedResponse_ScoreFlagResponse_

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

PaginatedResponse[ScoreFlagResponse]

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|[[ScoreFlagResponse](./schemas.md#scoreflagresponse)]|true|none|List of items in this page|
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

## PaginatedResponse_ScoreSubmissionMetaResponse_

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

PaginatedResponse[ScoreSubmissionMetaResponse]

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|[[ScoreSubmissionMetaResponse](./schemas.md#scoresubmissionmetaresponse)]|true|none|List of items in this page|
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

## RatioDisplay

```json
"RAW"

```

RatioDisplay

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|RatioDisplay|string|false|none|Display format for ratio values.<br><br>- RAW: Display the ratio value as-is (e.g., 0.75)<br>- PERCENT: Display as percentage (e.g., 75%)|

#### Enumerated Values

|Property|Value|
|---|---|
|RatioDisplay|RAW|
|RatioDisplay|PERCENT|

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

## RunEntryResponse

```json
{
  "id": "string",
  "board_id": "string",
  "identity_id": "string",
  "score_event_id": "string",
  "primary_value": 0,
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}

```

RunEntryResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|Unique identifier for the run entry|
|board_id|string|true|none|ID of the board this entry belongs to|
|identity_id|string|true|none|ID of the identity that submitted this entry|
|score_event_id|string|true|none|ID of the score event that created this entry|
|primary_value|number|true|none|Rankable value for this submission|
|created_at|string(date-time)|true|none|Timestamp when the entry was created (UTC)|
|updated_at|string(date-time)|true|none|Timestamp when the entry was last updated (UTC)|

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
  "identity_id": "string",
  "player_name": "string",
  "value": 0,
  "value_display": "string",
  "metadata": {},
  "rank": 0,
  "is_placeholder": false,
  "is_test": false,
  "status": "provisional",
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
|identity_id|string|true|none|ID of the identity that submitted this score|
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
|rank|any|false|none|Leaderboard position (1 = first). Null if not querying by board_id.|

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
|is_placeholder|boolean|false|none|True if this is a synthetic placeholder score (from around_score_value query)|
|is_test|boolean|false|none|True if this score was submitted in test mode|
|status|[ScoreStatus](./schemas.md#scorestatus)|true|none|Score lifecycle status (active, under_review, rejected)|
|created_at|string(date-time)|true|none|Timestamp when the score was created (UTC)|
|updated_at|string(date-time)|true|none|Timestamp of last update (UTC)|

## ScoreEventCreateRequest

```json
{
  "board_id": "string",
  "identity_id": "string",
  "value": 0,
  "player_name": "string",
  "is_test": false,
  "timezone": "string",
  "country": "string",
  "city": "string"
}

```

ScoreEventCreateRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|board_id|string|true|none|Board to submit to|
|identity_id|string|true|none|Identity submitting the score|
|value|number|true|none|Score value (or delta for COUNTER boards)|
|player_name|any|false|none|Optional display name|

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
|is_test|boolean|false|none|Whether this is a test event|
|timezone|any|false|none|Optional timezone|

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
|country|any|false|none|Optional country code|

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
|city|any|false|none|Optional city name|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

## ScoreEventResponse

```json
{
  "id": "string",
  "account_id": "string",
  "game_id": "string",
  "board_id": "string",
  "identity_id": "string",
  "event_payload": {},
  "is_test": true,
  "timezone": "string",
  "country": "string",
  "city": "string",
  "created_at": "2019-08-24T14:15:22Z"
}

```

ScoreEventResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|Unique identifier for the score event|
|account_id|string|true|none|ID of the account this event belongs to|
|game_id|string|true|none|ID of the game this event belongs to|
|board_id|string|true|none|ID of the board this event was submitted to|
|identity_id|string|true|none|ID of the identity that submitted this score|
|event_payload|object|true|none|Board-type-specific payload (value for RUN boards, delta for COUNTER)|
|is_test|boolean|true|none|True if this was a test submission|
|timezone|any|false|none|Timezone from GeoIP lookup|

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
|country|any|false|none|Country code from GeoIP lookup|

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
|city|any|false|none|City name from GeoIP lookup|

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
|created_at|string(date-time)|true|none|Timestamp when the event was created (UTC)|

## ScoreFlagCreateRequest

```json
{
  "score_event_id": "string",
  "flag_type": "rate_limit",
  "confidence": "low",
  "metadata": {}
}

```

ScoreFlagCreateRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|score_event_id|string|true|none|ID of the score event to flag|
|flag_type|[FlagType](./schemas.md#flagtype)|false|none|Type of flag (manual, duplicate, velocity, rate_limit, outlier, etc.)|
|confidence|[FlagConfidence](./schemas.md#flagconfidence)|false|none|Confidence level (low, medium, high)|
|metadata|any|false|none|Optional metadata/notes about the flag|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|object|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|null|false|none|none|

## ScoreFlagResponse

```json
{
  "id": "string",
  "score_event_id": "string",
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
|score_event_id|string|true|none|ID of the score event that was flagged|
|flag_type|string|true|none|Type of flag (e.g., velocity, duplicate, rate_limit)|
|confidence|string|true|none|Confidence level of the flag (low, medium, high)|
|metadata|object|true|none|Additional metadata about the flag|
|status|string|true|none|Status: pending, confirmed_cheat, false_positive, or dismissed|
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

## ScoreFlagStatus

```json
"pending"

```

ScoreFlagStatus

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|ScoreFlagStatus|string|false|none|Status of a score flag review.<br><br>Indicates whether a flag has been reviewed and what decision was made.|

#### Enumerated Values

|Property|Value|
|---|---|
|ScoreFlagStatus|pending|
|ScoreFlagStatus|confirmed_cheat|
|ScoreFlagStatus|false_positive|
|ScoreFlagStatus|dismissed|

## ScoreFlagUpdateRequest

```json
{
  "status": "pending",
  "reviewer_decision": "string",
  "deleted": true
}

```

ScoreFlagUpdateRequest

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|status|any|false|none|Updated status: pending, confirmed_cheat, false_positive, or dismissed|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[ScoreFlagStatus](./schemas.md#scoreflagstatus)|false|none|Status of a score flag review.<br><br>Indicates whether a flag has been reviewed and what decision was made.|

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
  "identity_id": "string",
  "player_name": "string",
  "value": 0,
  "value_display": "string",
  "timezone": "string",
  "country": "string",
  "city": "string",
  "metadata": {},
  "rank": 0,
  "is_placeholder": false,
  "is_test": false,
  "status": "provisional",
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
|identity_id|string|true|none|ID of the identity that submitted this score|
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
|rank|any|false|none|Leaderboard position (1 = first). Null if not querying by board_id.|

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
|is_placeholder|boolean|false|none|True if this is a synthetic placeholder score (from around_score_value query)|
|is_test|boolean|false|none|True if this score was submitted in test mode|
|status|[ScoreStatus](./schemas.md#scorestatus)|true|none|Score lifecycle status (active, under_review, rejected)|
|created_at|string(date-time)|true|none|Timestamp when the score was created (UTC)|
|updated_at|string(date-time)|true|none|Timestamp of last update (UTC)|

## ScoreStatus

```json
"provisional"

```

ScoreStatus

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|ScoreStatus|string|false|none|Lifecycle status of a score in the anti-cheat workflow.<br><br>Tracks the score from submission through review, determining visibility<br>on leaderboards.|

#### Enumerated Values

|Property|Value|
|---|---|
|ScoreStatus|provisional|
|ScoreStatus|active|
|ScoreStatus|under_review|
|ScoreStatus|rejected|

## ScoreSubmissionMetaResponse

```json
{
  "id": "string",
  "score_event_id": "string",
  "identity_id": "string",
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
|score_event_id|string|true|none|none|
|identity_id|string|true|none|none|
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
  "metadata": {},
  "test_mode": false
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

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|test_mode|boolean|false|none|If true, session is in test mode and scores will be marked as test|

## StartSessionResponse

```json
{
  "identity_id": "string",
  "game_id": "string",
  "account_id": "string",
  "kind": "DEVICE",
  "display_name": "string",
  "access_token": "string",
  "refresh_token": "string",
  "expires_in": 0,
  "test_mode": true
}

```

StartSessionResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|identity_id|string|true|none|Unique identifier for the player identity|
|game_id|string|true|none|ID of the game|
|account_id|string|true|none|ID of the account that owns the game|
|kind|[IdentityKind](./schemas.md#identitykind)|true|none|Identity type (DEVICE, STEAM, CUSTOM)|
|display_name|any|false|none|Player display name|

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
|access_token|string|true|none|JWT access token for authenticating API requests|
|refresh_token|string|true|none|JWT refresh token for obtaining new access tokens|
|expires_in|integer|true|none|Access token expiration time in seconds|
|test_mode|boolean|true|none|Whether session is in test mode|

## TieBreaker

```json
"NUMERATOR_DESC_DENOMINATOR_ASC"

```

TieBreaker

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|TieBreaker|string|false|none|Tie-breaking strategy for equal ratios.<br><br>NUMERATOR_DESC_DENOMINATOR_ASC: Higher numerator wins, then lower denominator.<br>This favors players who achieved more (higher numerator) with less attempts<br>(lower denominator).|

#### Enumerated Values

|Property|Value|
|---|---|
|TieBreaker|NUMERATOR_DESC_DENOMINATOR_ASC|

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
  "status": "invited",
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
|status|[UserStatus](./schemas.md#userstatus)|true|none|User's current status (INVITED, ACTIVE, SUSPENDED)|
|created_at|string(date-time)|true|none|Timestamp when the user was created (UTC)|
|updated_at|string(date-time)|true|none|Timestamp of last update (UTC)|

## UserStatus

```json
"invited"

```

UserStatus

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|UserStatus|string|false|none|User status enum.<br><br>Represents the lifecycle state of a user.|

#### Enumerated Values

|Property|Value|
|---|---|
|UserStatus|invited|
|UserStatus|active|
|UserStatus|suspended|

## UserUpdateRequest

```json
{
  "email": "user@example.com",
  "display_name": "string",
  "super_admin": true,
  "status": "invited",
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
|status|any|false|none|User status (INVITED, ACTIVE, SUSPENDED)|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|[UserStatus](./schemas.md#userstatus)|false|none|User status enum.<br><br>Represents the lifecycle state of a user.|

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
  "expires_in": 0,
  "type": "string"
}

```

VerifyCodeResponse

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|verification_token|string|true|none|Temporary token for completing registration|
|expires_in|integer|true|none|Seconds until the token expires|
|type|string|true|none|Type of verification: REGISTRATION for new accounts, INVITE for invited users|

## ZeroDenominatorPolicy

```json
"NULL"

```

ZeroDenominatorPolicy

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|ZeroDenominatorPolicy|string|false|none|Policy for handling zero denominators in ratio calculations.<br><br>Determines what value to use when the denominator is zero:<br>- NULL: Return null/not rankable<br>- ZERO: Return zero<br>- INFINITY: Return infinity (highest rank)|

#### Enumerated Values

|Property|Value|
|---|---|
|ZeroDenominatorPolicy|NULL|
|ZeroDenominatorPolicy|ZERO|
|ZeroDenominatorPolicy|INFINITY|
