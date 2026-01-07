# Score Submission Metadata

## List Submission Meta

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/score-submission-metadata', headers = headers)

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

    fetch('/v1/score-submission-metadata',
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
`GET /v1/score-submission-metadata`

List score submission metadata for an account with optional filters and pagination.

Returns paginated submission metadata for the specified account, with optional
filtering by board or device. Supports cursor-based pagination with bidirectional
navigation and custom sorting.

For regular users, account_id is automatically derived from their API key.
For superadmins, account_id is optional - if omitted, returns metadata from all accounts.

Args:
    auth: Authentication context with user info.
    service: Injected submission metadata service dependency.
    pagination: Pagination parameters (cursor, limit, sort).
    account_id: Optional account_id query parameter (superadmins can omit to see all).
    board_id: Optional board ID to filter by.
    device_id: Optional device ID to filter by.

Returns:
    PaginatedResponse containing ScoreSubmissionMetaResponse objects matching the filter.

Raises:
    400: Invalid cursor or sort field.
    403: User does not have access to the specified account.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|account_id|query|any|false|none|
|board_id|query|any|false|none|
|device_id|query|any|false|none|
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
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[PaginatedResponse_ScoreSubmissionMetaResponse_](./schemas.md#paginatedresponse_scoresubmissionmetaresponse_)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication

## Get Submission Meta

=== "Python"

    ```python
    import requests
    headers = {
      'Accept': 'application/json',
      'leadr-api-key': 'string',
      'authorization': 'string',
      'leadr-client-nonce': 'string'
    }

    r = requests.get('/v1/score-submission-metadata/{meta_id}', headers = headers)

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

    fetch('/v1/score-submission-metadata/{meta_id}',
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
`GET /v1/score-submission-metadata/{meta_id}`

Get score submission metadata by ID.

Args:
    meta_id: Submission metadata identifier to retrieve.
    service: Injected submission metadata service dependency.
    auth: Authentication context with user info.

Returns:
    ScoreSubmissionMetaResponse with the submission metadata details.

Raises:
    403: User does not have access to this metadata's account.
    404: Submission metadata not found or soft-deleted.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|meta_id|path|string|true|none|
|account_id|query|any|false|none|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|

> Example responses

> 200 Response

```json
{
  "id": "string",
  "score_id": "string",
  "device_id": "string",
  "board_id": "string",
  "submission_count": 0,
  "last_submission_at": "2019-08-24T14:15:22Z",
  "last_score_value": 0,
  "created_at": "2019-08-24T14:15:22Z",
  "updated_at": "2019-08-24T14:15:22Z"
}
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[ScoreSubmissionMetaResponse](./schemas.md#scoresubmissionmetaresponse)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

!!! success
    This operation does not require authentication
