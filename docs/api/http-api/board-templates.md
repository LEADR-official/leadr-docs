# Board Templates

## Create Board Template

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

    r = requests.post('/v1/board-templates', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
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
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json',
      'leadr-api-key':'string',
      'authorization':'string',
      'leadr-client-nonce':'string'
    };

    fetch('/v1/board-templates',
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
`POST /v1/board-templates`

Create a new board template.

Creates a template for automatically generating boards at regular intervals.
The game must belong to the specified account.

For regular users, account_id must match their API key's account.
For superadmins, any account_id is accepted.

Args:
    request: Template creation details including repeat_interval and configuration.
    service: Injected board template service dependency.
    auth: Authentication context with user info.

Returns:
    BoardTemplateResponse with the created template including auto-generated ID.

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

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|account_id|query|any|false|none|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|
|body|body|[BoardTemplateCreateRequest](./schemas.md#boardtemplatecreaterequest)|true|none|

> Example responses

> 201 Response

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

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Successful Response|[BoardTemplateResponse](./schemas.md#boardtemplateresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## List Board Templates

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/board-templates', headers = headers)

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

    fetch('/v1/board-templates',
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
`GET /v1/board-templates`

List board templates for an account with pagination, optionally filtered by game.

For regular users, account_id is automatically derived from their API key.
For superadmins, account_id is optional - if omitted, returns templates from all accounts.

Pagination:
- Default: 20 items per page, sorted by created_at:desc,id:asc
- Custom sort: Use ?sort=name:asc,created_at:desc
- Valid sort fields: id, name, created_at, updated_at
- Navigation: Use next_cursor/prev_cursor from response

Example:
    GET /v1/board-templates?account_id=acc_123&game_id=gam_456&limit=50&sort=name:asc

Args:
    auth: Authentication context with user info.
    service: Injected board template service dependency.
    pagination: Pagination parameters (cursor, limit, sort).
    account_id: Optional account_id query parameter (superadmins can omit to see all).
    game_id: Optional game ID to filter templates by.

Returns:
    PaginatedResponse with board templates and pagination metadata.

Raises:
    400: Invalid cursor, sort field, or cursor state mismatch.
    403: User does not have access to the specified account.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|account_id|query|any|false|none|
|game_id|query|any|false|Filter by game ID|
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
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[PaginatedResponse_BoardTemplateResponse_](./schemas.md#paginatedresponse_boardtemplateresponse_)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Get Board Template

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/board-templates/{template_id}', headers = headers)

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

    fetch('/v1/board-templates/{template_id}',
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
`GET /v1/board-templates/{template_id}`

Get a board template by ID.

Args:
    template_id: Unique identifier for the template.
    service: Injected board template service dependency.
    auth: Authentication context with user info.

Returns:
    BoardTemplateResponse with full template details.

Raises:
    403: User does not have access to this template's account.
    404: Template not found.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|template_id|path|string|true|none|
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

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[BoardTemplateResponse](./schemas.md#boardtemplateresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Update Board Template

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

    r = requests.patch('/v1/board-templates/{template_id}', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
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
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json',
      'leadr-api-key':'string',
      'authorization':'string',
      'leadr-client-nonce':'string'
    };

    fetch('/v1/board-templates/{template_id}',
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
`PATCH /v1/board-templates/{template_id}`

Update a board template.

Supports updating any template field or soft-deleting the template.

Args:
    template_id: Unique identifier for the template.
    request: Template update details (all fields optional).
    service: Injected board template service dependency.
    auth: Authentication context with user info.

Returns:
    BoardTemplateResponse with the updated template details.

Raises:
    403: User does not have access to this template's account.
    404: Template not found.

> Body parameter

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

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|template_id|path|string|true|none|
|account_id|query|any|false|none|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|
|body|body|[BoardTemplateUpdateRequest](./schemas.md#boardtemplateupdaterequest)|true|none|

> Example responses

> 200 Response

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

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[BoardTemplateResponse](./schemas.md#boardtemplateresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication
