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

List score submission metadata for an account with optional filters.

Returns all non-deleted submission metadata for the specified account, with optional
filtering by board or device.

For regular users, account_id is automatically derived from their API key.
For superadmins, account_id is optional - if omitted, returns metadata from all accounts.

Args:
    auth: Authentication context with user info.
    service: Injected submission metadata service dependency.
    account_id: Optional account_id query parameter (superadmins can omit to see all).
    board_id: Optional board ID to filter by.
    device_id: Optional device ID to filter by.

Returns:
    List of ScoreSubmissionMetaResponse objects matching the filter criteria.

Raises:
    403: User does not have access to the specified account.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|account_id|query|any|false|none|
|board_id|query|any|false|none|
|device_id|query|any|false|none|
|leadr-api-key|header|any|false|none|
|authorization|header|any|false|none|
|leadr-client-nonce|header|any|false|none|

> Example responses

> 200 Response

```json
[
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
]
```

### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|Inline|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](./schemas.md#httpvalidationerror)|

### Response Schema

Status Code **200**

*Response List Submission Meta V1 Score Submission Metadata Get*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|Response List Submission Meta V1 Score Submission Metadata Get|[[ScoreSubmissionMetaResponse](./schemas.md#scoresubmissionmetaresponse)]|false|none|[Response model for score submission metadata.]|
|» ScoreSubmissionMetaResponse|[ScoreSubmissionMetaResponse](./schemas.md#scoresubmissionmetaresponse)|false|none|Response model for score submission metadata.|
|»» id|string|true|none|none|
|»» score_id|string|true|none|none|
|»» device_id|string|true|none|none|
|»» board_id|string|true|none|none|
|»» submission_count|integer|true|none|none|
|»» last_submission_at|string(date-time)|true|none|none|
|»» last_score_value|any|true|none|none|

*anyOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|number|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|null|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» created_at|string(date-time)|true|none|none|
|»» updated_at|string(date-time)|true|none|none|

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
