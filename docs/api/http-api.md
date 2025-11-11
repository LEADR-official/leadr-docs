---
title: LEADR - Admin & Client API v0.1.0
---

# LEADR - Admin & Client API v0.1.0

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

LEADR is the cross-platform leaderboard backend for indie game devs

# Health

## Health Check

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json'
    }

    r = requests.get('/v1/health', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript

    const headers = {
      'Accept':'application/json'
    };

    fetch('/v1/health',
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
`GET /v1/health`

Health check endpoint.

Verifies that the API is running and can connect to the database.
Returns degraded status if database connectivity fails.

Args:
    db: Database session dependency.

Returns:
    HealthResponse with API and database status.

> Example responses

> 200 Response

```json
{
  "status": "string",
  "database": "string"
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[HealthResponse](#schemahealthresponse)|

!!! success
    This operation does not require authentication

# Root

## Root

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json'
    }

    r = requests.get('/v1/', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript

    const headers = {
      'Accept':'application/json'
    };

    fetch('/v1/',
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
`GET /v1/`

Root endpoint.

Returns basic API information including version and documentation URL.

Returns:
    Dict containing API metadata.

> Example responses

> 200 Response

```json
null
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|Inline|

### Response Schema

!!! success
    This operation does not require authentication

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
|body|body|[AccountCreateRequest](#schemaaccountcreaterequest)|true|none|

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
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Successful Response|[AccountResponse](#schemaaccountresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](#schemahttpvalidationerror)|

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
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](#schemahttpvalidationerror)|

### Response Schema

Status Code **200**

*Response List Accounts V1 Accounts Get*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|Response List Accounts V1 Accounts Get|[[AccountResponse](#schemaaccountresponse)]|false|none|[Response model for an account.]|
|» AccountResponse|[AccountResponse](#schemaaccountresponse)|false|none|Response model for an account.|
|»» id|string(uuid)|true|none|Unique identifier for the account|
|»» name|string|true|none|Account name|
|»» slug|string|true|none|URL-friendly identifier|
|»» status|[AccountStatus](#schemaaccountstatus)|true|none|Account status enumeration.|
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
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[AccountResponse](#schemaaccountresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](#schemahttpvalidationerror)|

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
|body|body|[AccountUpdateRequest](#schemaaccountupdaterequest)|true|none|

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
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[AccountResponse](#schemaaccountresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](#schemahttpvalidationerror)|

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
|body|body|[UserCreateRequest](#schemausercreaterequest)|true|none|

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
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Successful Response|[UserResponse](#schemauserresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](#schemahttpvalidationerror)|

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
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](#schemahttpvalidationerror)|

### Response Schema

Status Code **200**

*Response List Users V1 Users Get*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|Response List Users V1 Users Get|[[UserResponse](#schemauserresponse)]|false|none|[Response model for a user.]|
|» UserResponse|[UserResponse](#schemauserresponse)|false|none|Response model for a user.|
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
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[UserResponse](#schemauserresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](#schemahttpvalidationerror)|

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
|body|body|[UserUpdateRequest](#schemauserupdaterequest)|true|none|

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
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[UserResponse](#schemauserresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](#schemahttpvalidationerror)|

!!! success
    This operation does not require authentication

# API Keys

## Create Api Key

=== "Python"

    ```python
    import requests
    headers = {
      'Content-Type': 'application/json',
      'Accept': 'application/json',
      'leadr-api-key': 'string'
    }

    r = requests.post('/v1/api-keys', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
      "account_id": "449e7a5c-69d3-4b8a-aaaf-5c9b713ebc65",
      "name": "string",
      "expires_at": "2019-08-24T14:15:22Z"
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json',
      'leadr-api-key':'string'
    };

    fetch('/v1/api-keys',
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
`POST /v1/api-keys`

Create a new API key for an account.

The plain API key is returned only once in this response.
Store it securely as it cannot be retrieved later.

Returns:
    CreateAPIKeyResponse with the plain key included.

Raises:
    404: Account not found.

> Body parameter

```json
{
  "account_id": "449e7a5c-69d3-4b8a-aaaf-5c9b713ebc65",
  "name": "string",
  "expires_at": "2019-08-24T14:15:22Z"
}
```

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|leadr-api-key|header|any|false|none|
|body|body|[CreateAPIKeyRequest](#schemacreateapikeyrequest)|true|none|

> Example responses

> 201 Response

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

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Successful Response|[CreateAPIKeyResponse](#schemacreateapikeyresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](#schemahttpvalidationerror)|

!!! success
    This operation does not require authentication

## List Api Keys

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string'
    }

    r = requests.get('/v1/api-keys', params={
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

    fetch('/v1/api-keys?account_id=string',
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
`GET /v1/api-keys`

List API keys for an account with optional filters.

TODO: Replace account_id query param with account_id from auth token.

Args:
    account_id: Account ID to filter results (REQUIRED for multi-tenant safety).
    status: Optional status to filter results (active or revoked).

Returns:
    List of API keys matching the filters.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|account_id|query|string(uuid4)|true|Account ID to filter by|
|status|query|any|false|Filter by status|
|leadr-api-key|header|any|false|none|

> Example responses

> 200 Response

```json
[
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
]
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|Inline|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](#schemahttpvalidationerror)|

### Response Schema

Status Code **200**

*Response List Api Keys V1 Api Keys Get*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|Response List Api Keys V1 Api Keys Get|[[APIKeyResponse](#schemaapikeyresponse)]|false|none|[Response schema for API key details.<br><br>Excludes sensitive information like key_hash.<br>The full key is never returned after creation.]|
|» APIKeyResponse|[APIKeyResponse](#schemaapikeyresponse)|false|none|Response schema for API key details.<br><br>Excludes sensitive information like key_hash.<br>The full key is never returned after creation.|
|»» id|string(uuid)|true|none|Unique identifier for the API key|
|»» account_id|string(uuid)|true|none|ID of the account this key belongs to|
|»» name|string|true|none|Human-readable name for the API key|
|»» prefix|string|true|none|Key prefix for identification (first 8 characters)|
|»» status|[APIKeyStatus](#schemaapikeystatus)|true|none|API Key status enumeration.|
|»» last_used_at|any|false|none|Timestamp of last successful authentication (UTC)|

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
|»» expires_at|any|false|none|Expiration timestamp (UTC), or null if never expires|

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
|»» created_at|string(date-time)|true|none|Timestamp when the key was created (UTC)|
|»» updated_at|string(date-time)|true|none|Timestamp of last update (UTC)|

#### Enumerated Values

|Property|Value|
|---|---|
|status|active|
|status|revoked|

!!! success
    This operation does not require authentication

## Get Api Key

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string'
    }

    r = requests.get('/v1/api-keys/{key_id}', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript

    const headers = {
      'Accept':'application/json',
      'leadr-api-key':'string'
    };

    fetch('/v1/api-keys/{key_id}',
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
`GET /v1/api-keys/{key_id}`

Get a single API key by ID.

Args:
    key_id: The UUID of the API key to retrieve.

Returns:
    APIKeyResponse with key details (excludes the plain key).

Raises:
    404: API key not found.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|key_id|path|string(uuid4)|true|none|
|leadr-api-key|header|any|false|none|

> Example responses

> 200 Response

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

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[APIKeyResponse](#schemaapikeyresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](#schemahttpvalidationerror)|

!!! success
    This operation does not require authentication

## Update Api Key

=== "Python"

    ```python
    import requests
    headers = {
      'Content-Type': 'application/json',
      'Accept': 'application/json',
      'leadr-api-key': 'string'
    }

    r = requests.patch('/v1/api-keys/{key_id}', headers = headers)

    print(r.json())

    ```

=== "JavaScript"

    ```javascript
    const inputBody = '{
      "status": "active",
      "deleted": true
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json',
      'leadr-api-key':'string'
    };

    fetch('/v1/api-keys/{key_id}',
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
`PATCH /v1/api-keys/{key_id}`

Update an API key.

Currently supports:
- Updating status (e.g., to revoke a key)
- Soft delete via deleted flag

Args:
    key_id: The UUID of the API key to update.
    request: Update request with optional status and deleted fields.

Returns:
    APIKeyResponse with updated key details.

Raises:
    404: API key not found.

> Body parameter

```json
{
  "status": "active",
  "deleted": true
}
```

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|key_id|path|string(uuid4)|true|none|
|leadr-api-key|header|any|false|none|
|body|body|[UpdateAPIKeyRequest](#schemaupdateapikeyrequest)|true|none|

> Example responses

> 200 Response

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

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[APIKeyResponse](#schemaapikeyresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](#schemahttpvalidationerror)|

!!! success
    This operation does not require authentication

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
|body|body|[GameCreateRequest](#schemagamecreaterequest)|true|none|

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
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Successful Response|[GameResponse](#schemagameresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](#schemahttpvalidationerror)|

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
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](#schemahttpvalidationerror)|

### Response Schema

Status Code **200**

*Response List Games V1 Games Get*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|Response List Games V1 Games Get|[[GameResponse](#schemagameresponse)]|false|none|[Response model for a game.]|
|» GameResponse|[GameResponse](#schemagameresponse)|false|none|Response model for a game.|
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
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[GameResponse](#schemagameresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](#schemahttpvalidationerror)|

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
|body|body|[GameUpdateRequest](#schemagameupdaterequest)|true|none|

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
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[GameResponse](#schemagameresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](#schemahttpvalidationerror)|

!!! success
    This operation does not require authentication

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
|status|[APIKeyStatus](#schemaapikeystatus)|true|none|Current status (active, revoked, expired)|
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
|status|[AccountStatus](#schemaaccountstatus)|true|none|Current account status|
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
|» *anonymous*|[AccountStatus](#schemaaccountstatus)|false|none|Account status enumeration.|

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
|status|[APIKeyStatus](#schemaapikeystatus)|true|none|Current status of the API key|
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
|detail|[[ValidationError](#schemavalidationerror)]|false|none|none|

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
|» *anonymous*|[APIKeyStatus](#schemaapikeystatus)|false|none|API Key status enumeration.|

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
