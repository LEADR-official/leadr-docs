# Boards

## Create Board

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

    r = requests.post('/v1/boards', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
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
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json',
      'leadr-api-key':'string',
      'authorization':'string',
      'leadr-client-nonce':'string'
    };

    fetch('/v1/boards',
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
`POST /v1/boards`

Create a new board.

Creates a new leaderboard associated with an existing game and account.
The game must belong to the specified account.

For regular users, account_id must match their API key's account.
For superadmins, any account_id is accepted.

Args:
    request: Board creation details including account_id, game_id, name, and settings.
    service: Injected board service dependency.
    auth: Authentication context with user info.

Returns:
    BoardResponse with the created board including auto-generated ID and timestamps.

Raises:
    403: User does not have access to the specified account.
    404: Game or account not found.
    400: Game doesn't belong to the specified account.

> Body parameter

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

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|account_id|query|any|false|none|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|
|body|body|[BoardCreateRequest](./schemas.md#boardcreaterequest)|true|none|

> Example responses

> 201 Response

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

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Successful Response|[BoardResponse](./schemas.md#boardresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## List Boards Admin

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/boards', headers = headers)

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

    fetch('/v1/boards',
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
`GET /v1/boards`

List boards (Admin API).

For regular users:
- If account_id not provided, defaults to their API key's account
- If account_id provided and they are superadmin, can access any account
- If account_id provided and NOT superadmin, must match their account (validated in AuthContext)

Filtering:
- Use ?game_id={id} or ?game_slug={slug} to filter boards by game
- Use ?game_slug={game_slug}&slug={slug} to find a specific board within a game
- Use ?code={code} to filter boards by short code
- Use ?is_active=true/false to filter by active status
- Use ?is_published=true/false to filter by published status
- Use ?starts_before=<datetime>&starts_after=<datetime> for start date range
- Use ?ends_before=<datetime>&ends_after=<datetime> for end date range
- Note: board slug filter requires game_slug parameter

Pagination:
- Default: 20 items per page, sorted by created_at:desc,id:asc
- Custom sort: Use ?sort=name:asc,created_at:desc
- Valid sort fields: id, name, slug, short_code, created_at, updated_at
- Navigation: Use next_cursor/prev_cursor from response

Example:
    GET /v1/boards?account_id=acc_123&limit=50&sort=name:asc
    GET /v1/boards?game_slug=my-game&is_active=true
    GET /v1/boards?game_slug=my-game&slug=weekly-challenge
    GET /v1/boards?starts_after=2025-01-01T00:00:00Z&ends_before=2025-12-31T23:59:59Z

Args:
    auth: Admin authentication context with user info.
    service: Injected board service dependency.
    game_service: Injected game service dependency.
    pagination: Pagination parameters (cursor, limit, sort).
    account_id: Optional account ID to filter boards by.
    game_id: Optional game ID to filter boards by.
    code: Optional short code to filter boards by.
    game_slug: Optional game slug to filter boards by game (resolves to game_id).
    slug: Optional board slug to filter by specific board (requires game_slug).
    is_active: Optional filter for active status.
    is_published: Optional filter for published status.
    starts_before: Optional filter for boards starting before this time.
    starts_after: Optional filter for boards starting after this time.
    ends_before: Optional filter for boards ending before this time.
    ends_after: Optional filter for boards ending after this time.

Returns:
    PaginatedResponse with boards and pagination metadata.

Raises:
    400: Invalid cursor, sort field, cursor state mismatch, or slug without game_slug.
    404: Game or board not found when using slug filters.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|account_id|query|any|false|none|
|game_id|query|any|false|Filter by game ID|
|code|query|any|false|Filter by short code|
|game_slug|query|any|false|Filter by game slug|
|slug|query|any|false|Filter by board slug (requires game_slug)|
|is_active|query|any|false|Filter by active status|
|is_published|query|any|false|Filter by published status|
|starts_before|query|any|false|Filter boards starting before this time (ISO 8601)|
|starts_after|query|any|false|Filter boards starting after this time (ISO 8601)|
|ends_before|query|any|false|Filter boards ending before this time (ISO 8601)|
|ends_after|query|any|false|Filter boards ending after this time (ISO 8601)|
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
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[PaginatedResponse_BoardResponse_](./schemas.md#paginatedresponse_boardresponse_)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Get Board

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/boards/{board_id}', headers = headers)

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

    fetch('/v1/boards/{board_id}',
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
`GET /v1/boards/{board_id}`

Get a board by ID.

Args:
    board_id: Unique identifier for the board.
    service: Injected board service dependency.
    auth: Authentication context with user info.

Returns:
    BoardResponse with full board details.

Raises:
    403: User does not have access to this board's account.
    404: Board not found.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|board_id|path|string|true|none|
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

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[BoardResponse](./schemas.md#boardresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Update Board

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

    r = requests.patch('/v1/boards/{board_id}', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
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
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json',
      'leadr-api-key':'string',
      'authorization':'string',
      'leadr-client-nonce':'string'
    };

    fetch('/v1/boards/{board_id}',
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
`PATCH /v1/boards/{board_id}`

Update a board.

Supports updating any board field or soft-deleting the board.

Args:
    board_id: Unique identifier for the board.
    request: Board update details (all fields optional).
    service: Injected board service dependency.
    auth: Authentication context with user info.

Returns:
    BoardResponse with the updated board details.

Raises:
    403: User does not have access to this board's account.
    404: Board not found.

> Body parameter

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

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|board_id|path|string|true|none|
|account_id|query|any|false|none|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|
|body|body|[BoardUpdateRequest](./schemas.md#boardupdaterequest)|true|none|

> Example responses

> 200 Response

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

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[BoardResponse](./schemas.md#boardresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication
