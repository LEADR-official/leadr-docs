# Boards

## Create Board

=== "Python"

    ```python
    import requests
    headers = {
      'Content-Type': 'application/json',
      'Accept': 'application/json',
      'leadr-api-key': 'string'
    }

    r = requests.post('/v1/boards', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
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
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json',
      'leadr-api-key':'string'
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

Args:
    request: Board creation details including account_id, game_id, name, and settings.
    service: Injected board service dependency.

Returns:
    BoardResponse with the created board including auto-generated ID and timestamps.

Raises:
    404: Game or account not found.
    400: Game doesn't belong to the specified account.

> Body parameter

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

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|leadr-api-key|header|any|false|none|
|body|body|[BoardCreateRequest](./schemas.md#boardcreaterequest)|true|none|

> Example responses

> 201 Response

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

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Successful Response|[BoardResponse](./schemas.md#boardresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## List Boards

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string'
    }

    r = requests.get('/v1/boards', params={
      'account_id': '497f6eca-6276-4993-bfeb-53cbbbba6f08'
    }, headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript

    const headers = {
      'Accept':'application/json',
      'leadr-api-key':'string'
    };

    fetch('/v1/boards?account_id=497f6eca-6276-4993-bfeb-53cbbbba6f08',
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

List all boards for an account.

Args:
    account_id: Account ID to filter boards by.
    service: Injected board service dependency.

Returns:
    List of all active boards for the specified account.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|account_id|query|string(uuid)|true|none|
|leadr-api-key|header|any|false|none|

> Example responses

> 200 Response

```json
[
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
]
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|Inline|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

### Response Schema

Status Code **200**

*Response List Boards V1 Boards Get*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|Response List Boards V1 Boards Get|[[BoardResponse](./schemas.md#boardresponse)]|false|none|[Response model for a board.]|
|» BoardResponse|[BoardResponse](./schemas.md#boardresponse)|false|none|Response model for a board.|
|»» id|string(uuid)|true|none|Unique identifier for the board|
|»» account_id|string(uuid)|true|none|ID of the account this board belongs to|
|»» game_id|string(uuid)|true|none|ID of the game this board belongs to|
|»» name|string|true|none|Name of the board|
|»» icon|string|true|none|Icon identifier for the board|
|»» short_code|string|true|none|Globally unique short code for direct sharing|
|»» unit|string|true|none|Unit of measurement for scores|
|»» is_active|boolean|true|none|Whether the board is currently active|
|»» sort_direction|[SortDirection](./schemas.md#sortdirection)|true|none|Sort direction for board scores.|
|»» keep_strategy|[KeepStrategy](./schemas.md#keepstrategy)|true|none|Strategy for keeping scores from the same user.|
|»» template_id|any|false|none|Template ID this board was created from, or null|

*anyOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|string(uuid)|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|null|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» template_name|any|false|none|Template name this board was created from, or null|

*anyOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|string|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|null|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» starts_at|any|false|none|Start time for time-bounded boards (UTC)|

*anyOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|string(date-time)|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|null|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» ends_at|any|false|none|End time for time-bounded boards (UTC)|

*anyOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|string(date-time)|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|null|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» tags|[string]|false|none|List of tags for categorization|
|»» created_at|string(date-time)|true|none|Timestamp when the board was created (UTC)|
|»» updated_at|string(date-time)|true|none|Timestamp of last update (UTC)|

#### Enumerated Values

|Property|Value|
|---|---|
|sort_direction|ASCENDING|
|sort_direction|DESCENDING|
|keep_strategy|BEST_ONLY|
|keep_strategy|LATEST_ONLY|
|keep_strategy|ALL|

!!! success
    This operation does not require authentication

## Get Board

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string'
    }

    r = requests.get('/v1/boards/{board_id}', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript

    const headers = {
      'Accept':'application/json',
      'leadr-api-key':'string'
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

Returns:
    BoardResponse with full board details.

Raises:
    404: Board not found.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|board_id|path|string(uuid)|true|none|
|leadr-api-key|header|any|false|none|

> Example responses

> 200 Response

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
      'leadr-api-key': 'string'
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
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json',
      'leadr-api-key':'string'
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

Returns:
    BoardResponse with the updated board details.

Raises:
    404: Board not found.

> Body parameter

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

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|board_id|path|string(uuid)|true|none|
|leadr-api-key|header|any|false|none|
|body|body|[BoardUpdateRequest](./schemas.md#boardupdaterequest)|true|none|

> Example responses

> 200 Response

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

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[BoardResponse](./schemas.md#boardresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Get Board By Short Code

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string'
    }

    r = requests.get('/v1/boards/by-code/{short_code}', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript

    const headers = {
      'Accept':'application/json',
      'leadr-api-key':'string'
    };

    fetch('/v1/boards/by-code/{short_code}',
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
`GET /v1/boards/by-code/{short_code}`

Get a board by its short code.

Args:
    short_code: Globally unique short code for the board.
    service: Injected board service dependency.

Returns:
    BoardResponse with full board details.

Raises:
    404: Board not found.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|short_code|path|string|true|none|
|leadr-api-key|header|any|false|none|

> Example responses

> 200 Response

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

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[BoardResponse](./schemas.md#boardresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication
