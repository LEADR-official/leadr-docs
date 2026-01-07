# Games

## Create Game

=== "Python"

    ```python
    import requests
    headers = {
      'Content-Type': 'application/json',
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.post('/v1/games', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
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
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json',
      'leadr-api-key':'string',
      'authorization':'string',
      'leadr-client-nonce':'string'
    };

    fetch('/v1/games',
    {
      method: 'POST',
      body: inputBody,
      headers: headers
    })
    .then(function(res) {
        return res.json();
    }).then(function(body) {
        console.log(body);
    });

    ```
`POST /v1/games`

Create a new game.

Creates a new game associated with an existing account. Games can optionally
be configured with Steam integration and a default leaderboard.

For regular users, account_id must match their API key's account.
For superadmins, any account_id is accepted.

Args:
    request: Game creation details including account_id, name, and optional settings.
    service: Injected game service dependency.
    auth: Authentication context with user info.

Returns:
    GameResponse with the created game including auto-generated ID and timestamps.

Raises:
    403: User does not have access to the specified account.
    404: Account not found.

> Body parameter

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

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|account_id|query|any|false|none|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|
|body|body|[GameCreateRequest](./schemas.md#gamecreaterequest)|true|none|

> Example responses

> 201 Response

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

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Successful Response|[GameResponse](./schemas.md#gameresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## List Games

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/games', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript

    const headers = {
      'Accept':'application/json',
      'leadr-api-key':'string',
      'authorization':'string',
      'leadr-client-nonce':'string'
    };

    fetch('/v1/games',
    {
      method: 'GET',

      headers: headers
    })
    .then(function(res) {
        return res.json();
    }).then(function(body) {
        console.log(body);
    });

    ```
`GET /v1/games`

List all games for an account with pagination and optional filtering.

Returns paginated games for the specified account. Supports cursor-based
pagination with bidirectional navigation and custom sorting.

For regular users, account_id is automatically derived from their API key.
For superadmins, account_id is optional - if omitted, returns games from all accounts.

Filtering:
- Use ?slug={slug} to find a specific game by its globally unique slug

Pagination:
- Default: 20 items per page, sorted by created_at:desc,id:asc
- Custom sort: Use ?sort=name:asc,created_at:desc
- Valid sort fields: id, name, slug, created_at, updated_at
- Navigation: Use next_cursor/prev_cursor from response

Example:
    GET /v1/games?slug=my-game
    GET /v1/games?account_id=acc_123&limit=50&sort=name:asc

Args:
    auth: Authentication context with user info.
    service: Injected game service dependency.
    pagination: Pagination parameters (cursor, limit, sort).
    account_id: Optional account_id query parameter (superadmins can omit to see all).
    slug: Optional slug filter to find a specific game.

Returns:
    PaginatedResponse with games and pagination metadata.

Raises:
    400: Invalid cursor, sort field, or cursor state mismatch.
    403: User does not have access to the specified account.
    404: Game not found when filtering by slug.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|account_id|query|any|false|none|
|slug|query|any|false|Filter by game slug|
|cursor|query|any|false|Pagination cursor for navigating results|
|limit|query|integer|false|Number of items per page (1-100)|
|sort|query|any|false|Sort specification (e.g., 'value:desc,created_at:asc')|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|

> Example responses

> 200 Response

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

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[PaginatedResponse_GameResponse_](./schemas.md#paginatedresponse_gameresponse_)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Get Game

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/games/{game_id}', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript

    const headers = {
      'Accept':'application/json',
      'leadr-api-key':'string',
      'authorization':'string',
      'leadr-client-nonce':'string'
    };

    fetch('/v1/games/{game_id}',
    {
      method: 'GET',

      headers: headers
    })
    .then(function(res) {
        return res.json();
    }).then(function(body) {
        console.log(body);
    });

    ```
`GET /v1/games/{game_id}`

Get a game by ID.

Args:
    game_id: Unique identifier for the game.
    service: Injected game service dependency.
    auth: Authentication context with user info.

Returns:
    GameResponse with full game details.

Raises:
    403: User does not have access to this game's account.
    404: Game not found.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|game_id|path|string|true|none|
|account_id|query|any|false|none|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|

> Example responses

> 200 Response

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

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[GameResponse](./schemas.md#gameresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Update Game

=== "Python"

    ```python
    import requests
    headers = {
      'Content-Type': 'application/json',
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.patch('/v1/games/{game_id}', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
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
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json',
      'leadr-api-key':'string',
      'authorization':'string',
      'leadr-client-nonce':'string'
    };

    fetch('/v1/games/{game_id}',
    {
      method: 'PATCH',
      body: inputBody,
      headers: headers
    })
    .then(function(res) {
        return res.json();
    }).then(function(body) {
        console.log(body);
    });

    ```
`PATCH /v1/games/{game_id}`

Update a game.

Supports updating name, Steam App ID, default board ID, or soft-deleting the game.

Args:
    game_id: Unique identifier for the game.
    request: Game update details (all fields optional).
    service: Injected game service dependency.
    auth: Authentication context with user info.

Returns:
    GameResponse with the updated game details.

Raises:
    403: User does not have access to this game's account.
    404: Game not found.

> Body parameter

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

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|game_id|path|string|true|none|
|account_id|query|any|false|none|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|
|body|body|[GameUpdateRequest](./schemas.md#gameupdaterequest)|true|none|

> Example responses

> 200 Response

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

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[GameResponse](./schemas.md#gameresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication
