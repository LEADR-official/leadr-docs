# Public

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
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[HealthResponse](./schemas.md#healthresponse)|

!!! success
    This operation does not require authentication

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
