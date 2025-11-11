# Games

## Create Game

=== "Python"

    ```python
    import requests
    headers = {
      'Content-Type': 'application/json',
      'Accept': 'application/json',
      'leadr-api-key': 'string'
    }

    r = requests.post('/v1/games', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
      "account_id": "449e7a5c-69d3-4b8a-aaaf-5c9b713ebc65",
      "name": "string",
      "steam_app_id": "string",
      "default_board_id": "d242572a-54cf-433e-9831-a8453b36773b"
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json',
      'leadr-api-key':'string'
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

Args:
    request: Game creation details including account_id, name, and optional settings.
    service: Injected game service dependency.

Returns:
    GameResponse with the created game including auto-generated ID and timestamps.

Raises:
    404: Account not found.

> Body parameter

```json
{
  "account_id": "449e7a5c-69d3-4b8a-aaaf-5c9b713ebc65",
  "name": "string",
  "steam_app_id": "string",
  "default_board_id": "d242572a-54cf-433e-9831-a8453b36773b"
}
```

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|leadr-api-key|header|any|false|none|
|body|body|[GameCreateRequest](./schemas.md#gamecreaterequest)|true|none|

> Example responses

> 201 Response

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
      'leadr-api-key': 'string'
    }

    r = requests.get('/v1/games', params={
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

    fetch('/v1/games?account_id=497f6eca-6276-4993-bfeb-53cbbbba6f08',
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

List all games for an account.

Args:
    account_id: Account ID to filter games by.
    service: Injected game service dependency.

Returns:
    List of all active games for the specified account.

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
    "name": "string",
    "steam_app_id": "string",
    "default_board_id": "d242572a-54cf-433e-9831-a8453b36773b",
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

*Response List Games V1 Games Get*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|Response List Games V1 Games Get|[[GameResponse](./schemas.md#gameresponse)]|false|none|[Response model for a game.]|
|» GameResponse|[GameResponse](./schemas.md#gameresponse)|false|none|Response model for a game.|
|»» id|string(uuid)|true|none|Unique identifier for the game|
|»» account_id|string(uuid)|true|none|ID of the account this game belongs to|
|»» name|string|true|none|Name of the game|
|»» steam_app_id|any|false|none|Steam App ID if Steam integration is configured|

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
|»» default_board_id|any|false|none|ID of the default leaderboard, or null if not set|

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
|»» created_at|string(date-time)|true|none|Timestamp when the game was created (UTC)|
|»» updated_at|string(date-time)|true|none|Timestamp of last update (UTC)|

!!! success
    This operation does not require authentication

## Get Game

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string'
    }

    r = requests.get('/v1/games/{game_id}', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript

    const headers = {
      'Accept':'application/json',
      'leadr-api-key':'string'
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

Returns:
    GameResponse with full game details.

Raises:
    404: Game not found.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|game_id|path|string(uuid)|true|none|
|leadr-api-key|header|any|false|none|

> Example responses

> 200 Response

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
      'leadr-api-key': 'string'
    }

    r = requests.patch('/v1/games/{game_id}', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
      "name": "string",
      "steam_app_id": "string",
      "default_board_id": "d242572a-54cf-433e-9831-a8453b36773b",
      "deleted": true
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json',
      'leadr-api-key':'string'
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

Returns:
    GameResponse with the updated game details.

Raises:
    404: Game not found.

> Body parameter

```json
{
  "name": "string",
  "steam_app_id": "string",
  "default_board_id": "d242572a-54cf-433e-9831-a8453b36773b",
  "deleted": true
}
```

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|game_id|path|string(uuid)|true|none|
|leadr-api-key|header|any|false|none|
|body|body|[GameUpdateRequest](./schemas.md#gameupdaterequest)|true|none|

> Example responses

> 200 Response

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

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[GameResponse](./schemas.md#gameresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication
