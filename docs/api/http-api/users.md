# Users

## Create User

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

    r = requests.post('/v1/users', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
      "account_id": "string",
      "email": "user@example.com",
      "display_name": "string"
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json',
      'leadr-api-key':'string',
      'authorization':'string',
      'leadr-client-nonce':'string'
    };

    fetch('/v1/users',
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
`POST /v1/users`

Create a new user.

Creates a new user associated with an existing account.

For regular users, account_id must match their API key's account.
For superadmins, any account_id is accepted.

Args:
    request: User creation details including account_id, email, and display name.
    service: Injected user service dependency.
    auth: Authentication context with user info.

Returns:
    UserResponse with the created user including auto-generated ID and timestamps.

Raises:
    403: User does not have access to the specified account.
    404: Account not found.

> Body parameter

```json
{
  "account_id": "string",
  "email": "user@example.com",
  "display_name": "string"
}
```

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|account_id|query|any|false|none|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|
|body|body|[UserCreateRequest](./schemas.md#usercreaterequest)|true|none|

> Example responses

> 201 Response

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

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Successful Response|[UserResponse](./schemas.md#userresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## List Users

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/users', headers = headers)

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

    fetch('/v1/users',
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
`GET /v1/users`

List users for an account with pagination.

For regular users, account_id is automatically derived from their API key.
For superadmins, account_id is optional - if omitted, returns users from all accounts.

Pagination:
- Default: 20 items per page, sorted by created_at:desc,id:asc
- Custom sort: Use ?sort=email:asc,created_at:desc
- Valid sort fields: id, email, display_name, created_at, updated_at
- Navigation: Use next_cursor/prev_cursor from response

Example:
    GET /v1/users?account_id=acc_123&limit=50&sort=email:asc

Args:
    auth: Authentication context with user info.
    service: Injected user service dependency.
    pagination: Pagination parameters (cursor, limit, sort).
    account_id: Optional account_id query parameter (superadmins can omit to see all).

Returns:
    PaginatedResponse with users and pagination metadata.

Raises:
    400: Invalid cursor, sort field, or cursor state mismatch.
    403: User does not have access to the specified account.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
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
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[PaginatedResponse_UserResponse_](./schemas.md#paginatedresponse_userresponse_)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Get User

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/users/{user_id}', headers = headers)

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

    fetch('/v1/users/{user_id}',
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
`GET /v1/users/{user_id}`

Get a user by ID.

Args:
    user_id: Unique identifier for the user.
    service: Injected user service dependency.
    auth: Authentication context with user info.

Returns:
    UserResponse with full user details.

Raises:
    403: User does not have access to this user's account.
    404: User not found.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|user_id|path|string|true|none|
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
  "email": "string",
  "display_name": "string",
  "super_admin": true,
  "status": "invited",
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[UserResponse](./schemas.md#userresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Update User

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

    r = requests.patch('/v1/users/{user_id}', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
      "email": "user@example.com",
      "display_name": "string",
      "super_admin": true,
      "status": "invited",
      "deleted": true
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json',
      'leadr-api-key':'string',
      'authorization':'string',
      'leadr-client-nonce':'string'
    };

    fetch('/v1/users/{user_id}',
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
`PATCH /v1/users/{user_id}`

Update a user.

Supports updating email, display name, status, or soft-deleting the user.
Status changes (active/suspended) are handled through dedicated service methods.

Args:
    user_id: Unique identifier for the user.
    request: User update details (all fields optional).
    service: Injected user service dependency.
    auth: Authentication context with user info.

Returns:
    UserResponse with the updated user details.

Raises:
    403: User does not have access to this user's account.
    404: User not found.

> Body parameter

```json
{
  "email": "user@example.com",
  "display_name": "string",
  "super_admin": true,
  "status": "invited",
  "deleted": true
}
```

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|user_id|path|string|true|none|
|account_id|query|any|false|none|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|
|body|body|[UserUpdateRequest](./schemas.md#userupdaterequest)|true|none|

> Example responses

> 200 Response

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

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[UserResponse](./schemas.md#userresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication
