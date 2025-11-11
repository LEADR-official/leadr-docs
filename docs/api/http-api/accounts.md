# Accounts

## Create Account

=== "Python"

    ```python
    import requests
    headers = {
      'Content-Type': 'application/json',
      'Accept': 'application/json',
      'leadr-api-key': 'string'
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
      'leadr-api-key':'string'
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

Args:
    request: Account creation details including name and slug.
    service: Injected account service dependency.

Returns:
    AccountResponse with the created account including auto-generated ID and timestamps.

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
|leadr-api-key|header|any|false|none|
|body|body|[AccountCreateRequest](./schemas.md#accountcreaterequest)|true|none|

> Example responses

> 201 Response

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
      'leadr-api-key': 'string'
    }

    r = requests.get('/v1/accounts', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript

    const headers = {
      'Accept':'application/json',
      'leadr-api-key':'string'
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

List all accounts.

Args:
    service: Injected account service dependency.

Returns:
    List of all active accounts.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|leadr-api-key|header|any|false|none|

> Example responses

> 200 Response

```json
[
  {
    "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",
    "name": "string",
    "slug": "string",
    "status": "active",
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

*Response List Accounts V1 Accounts Get*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|Response List Accounts V1 Accounts Get|[[AccountResponse](./schemas.md#accountresponse)]|false|none|[Response model for an account.]|
|» AccountResponse|[AccountResponse](./schemas.md#accountresponse)|false|none|Response model for an account.|
|»» id|string(uuid)|true|none|Unique identifier for the account|
|»» name|string|true|none|Account name|
|»» slug|string|true|none|URL-friendly identifier|
|»» status|[AccountStatus](./schemas.md#accountstatus)|true|none|Account status enumeration.|
|»» created_at|string(date-time)|true|none|Timestamp when the account was created (UTC)|
|»» updated_at|string(date-time)|true|none|Timestamp of last update (UTC)|

#### Enumerated Values

|Property|Value|
|---|---|
|status|active|
|status|suspended|

!!! success
    This operation does not require authentication

## Get Account

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string'
    }

    r = requests.get('/v1/accounts/{account_id}', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript

    const headers = {
      'Accept':'application/json',
      'leadr-api-key':'string'
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

Returns:
    AccountResponse with full account details.

Raises:
    404: Account not found.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|account_id|path|string(uuid4)|true|none|
|leadr-api-key|header|any|false|none|

> Example responses

> 200 Response

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
      'leadr-api-key': 'string'
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
      "deleted": true
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json',
      'leadr-api-key':'string'
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

Returns:
    AccountResponse with the updated account details.

Raises:
    404: Account not found.

> Body parameter

```json
{
  "name": "string",
  "slug": "string",
  "status": "active",
  "deleted": true
}
```

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|account_id|path|string(uuid4)|true|none|
|leadr-api-key|header|any|false|none|
|body|body|[AccountUpdateRequest](./schemas.md#accountupdaterequest)|true|none|

> Example responses

> 200 Response

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

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[AccountResponse](./schemas.md#accountresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Create User

=== "Python"

    ```python
    import requests
    headers = {
      'Content-Type': 'application/json',
      'Accept': 'application/json',
      'leadr-api-key': 'string'
    }

    r = requests.post('/v1/users', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
      "account_id": "449e7a5c-69d3-4b8a-aaaf-5c9b713ebc65",
      "email": "user@example.com",
      "display_name": "string"
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json',
      'leadr-api-key':'string'
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

Args:
    request: User creation details including account_id, email, and display name.
    service: Injected user service dependency.

Returns:
    UserResponse with the created user including auto-generated ID and timestamps.

Raises:
    404: Account not found.

> Body parameter

```json
{
  "account_id": "449e7a5c-69d3-4b8a-aaaf-5c9b713ebc65",
  "email": "user@example.com",
  "display_name": "string"
}
```

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|leadr-api-key|header|any|false|none|
|body|body|[UserCreateRequest](./schemas.md#usercreaterequest)|true|none|

> Example responses

> 201 Response

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
      'leadr-api-key': 'string'
    }

    r = requests.get('/v1/users', params={
      'account_id': 'string'
    }, headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript

    const headers = {
      'Accept':'application/json',
      'leadr-api-key':'string'
    };

    fetch('/v1/users?account_id=string',
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

List users for an account.

TODO: Replace account_id query param with account_id from auth token.

Args:
    service: Injected user service dependency.
    account_id: Account ID to filter results (REQUIRED for multi-tenant safety).

Returns:
    List of users for the account.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|account_id|query|string(uuid4)|true|Account ID to filter by|
|leadr-api-key|header|any|false|none|

> Example responses

> 200 Response

```json
[
  {
    "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",
    "account_id": "449e7a5c-69d3-4b8a-aaaf-5c9b713ebc65",
    "email": "string",
    "display_name": "string",
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

*Response List Users V1 Users Get*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|Response List Users V1 Users Get|[[UserResponse](./schemas.md#userresponse)]|false|none|[Response model for a user.]|
|» UserResponse|[UserResponse](./schemas.md#userresponse)|false|none|Response model for a user.|
|»» id|string(uuid)|true|none|Unique identifier for the user|
|»» account_id|string(uuid)|true|none|ID of the account this user belongs to|
|»» email|string|true|none|User's email address|
|»» display_name|string|true|none|User's display name|
|»» created_at|string(date-time)|true|none|Timestamp when the user was created (UTC)|
|»» updated_at|string(date-time)|true|none|Timestamp of last update (UTC)|

!!! success
    This operation does not require authentication

## Get User

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string'
    }

    r = requests.get('/v1/users/{user_id}', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript

    const headers = {
      'Accept':'application/json',
      'leadr-api-key':'string'
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

Returns:
    UserResponse with full user details.

Raises:
    404: User not found.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|user_id|path|string(uuid4)|true|none|
|leadr-api-key|header|any|false|none|

> Example responses

> 200 Response

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
      'leadr-api-key': 'string'
    }

    r = requests.patch('/v1/users/{user_id}', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
      "email": "user@example.com",
      "display_name": "string",
      "deleted": true
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json',
      'leadr-api-key':'string'
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

Supports updating email, display name, or soft-deleting the user.

Args:
    user_id: Unique identifier for the user.
    request: User update details (all fields optional).
    service: Injected user service dependency.

Returns:
    UserResponse with the updated user details.

Raises:
    404: User not found.

> Body parameter

```json
{
  "email": "user@example.com",
  "display_name": "string",
  "deleted": true
}
```

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|user_id|path|string(uuid4)|true|none|
|leadr-api-key|header|any|false|none|
|body|body|[UserUpdateRequest](./schemas.md#userupdaterequest)|true|none|

> Example responses

> 200 Response

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

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[UserResponse](./schemas.md#userresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication
