# Accounts

## Create Account

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

    r = requests.post('/v1/accounts', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
      "name": "string",
      "slug": "string"
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json',
      'leadr-api-key':'string',
      'authorization':'string',
      'leadr-client-nonce':'string'
    };

    fetch('/v1/accounts',
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
`POST /v1/accounts`

Create a new account.

Only superadmins can create accounts.

Args:
    request: Account creation details including name and slug.
    service: Injected account service dependency.
    auth: Authentication context with user info.

Returns:
    AccountResponse with the created account including auto-generated ID and timestamps.

Raises:
    403: User does not have permission to create accounts.

> Body parameter

```json
{
  "name": "string",
  "slug": "string"
}
```

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|account_id|query|any|false|none|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|
|body|body|[AccountCreateRequest](./schemas.md#accountcreaterequest)|true|none|

> Example responses

> 201 Response

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

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Successful Response|[AccountResponse](./schemas.md#accountresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## List Accounts

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/accounts', headers = headers)

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

    fetch('/v1/accounts',
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
`GET /v1/accounts`

List accounts with pagination and optional filtering.

Superadmins see all accounts (paginated). Regular users see only their own account.

Filtering:
- Use ?slug={slug} to find a specific account by its slug

Pagination:
- Default: 20 items per page, sorted by created_at:desc,id:asc
- Custom sort: Use ?sort=name:asc,created_at:desc
- Valid sort fields: id, name, slug, created_at, updated_at
- Navigation: Use next_cursor/prev_cursor from response

Example:
    GET /v1/accounts?slug=acme-corp
    GET /v1/accounts?limit=50&sort=name:asc

Args:
    service: Injected account service dependency.
    auth: Authentication context with user info.
    pagination: Pagination parameters (cursor, limit, sort).
    slug: Optional slug filter to find a specific account.

Returns:
    PaginatedResponse with accounts and pagination metadata.

Raises:
    400: Invalid cursor, sort field, or cursor state mismatch.
    404: Account not found when filtering by slug.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|slug|query|any|false|Filter by account slug|
|account_id|query|any|false|none|
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
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[PaginatedResponse_AccountResponse_](./schemas.md#paginatedresponse_accountresponse_)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Get Account

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/accounts/{account_id}', headers = headers)

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

    fetch('/v1/accounts/{account_id}',
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
`GET /v1/accounts/{account_id}`

Get an account by ID.

Args:
    account_id: Unique identifier for the account.
    service: Injected account service dependency.
    auth: Authentication context with user info.

Returns:
    AccountResponse with full account details.

Raises:
    403: User does not have access to this account.
    404: Account not found.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|account_id|path|string|true|none|
|account_id|query|any|false|none|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|

> Example responses

> 200 Response

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

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[AccountResponse](./schemas.md#accountresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Update Account

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

    r = requests.patch('/v1/accounts/{account_id}', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
      "name": "string",
      "slug": "string",
      "status": "active",
      "deleted": true,
      "timezone": "string",
      "country": "string",
      "city": "string"
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json',
      'leadr-api-key':'string',
      'authorization':'string',
      'leadr-client-nonce':'string'
    };

    fetch('/v1/accounts/{account_id}',
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
`PATCH /v1/accounts/{account_id}`

Update an account.

Supports updating name, slug, status, or soft-deleting the account.
Status changes (active/suspended) are handled through dedicated service methods.

Args:
    account_id: Unique identifier for the account.
    request: Account update details (all fields optional).
    service: Injected account service dependency.
    auth: Authentication context with user info.

Returns:
    AccountResponse with the updated account details.

Raises:
    403: User does not have access to this account.
    404: Account not found.

> Body parameter

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

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|account_id|path|string|true|none|
|account_id|query|any|false|none|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|
|body|body|[AccountUpdateRequest](./schemas.md#accountupdaterequest)|true|none|

> Example responses

> 200 Response

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

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[AccountResponse](./schemas.md#accountresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication
