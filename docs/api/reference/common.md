### `leadr.common`

**Modules:**

- [**api**](./common.md#leadr.common.api) – API utilities and exception handlers.
- [**background_tasks**](#leadr.common.background_tasks) – Background task scheduler using asyncio.
- [**database**](./common.md#leadr.common.database) – Database connection and session management.
- [**dependencies**](./common.md#leadr.common.dependencies) – Shared FastAPI dependencies for the application.
- [**domain**](./common.md#leadr.common.domain) –
- [**geoip**](./common.md#leadr.common.geoip) – GeoIP service for IP address geolocation using MaxMind databases.
- [**orm**](./common.md#leadr.common.orm) – Common ORM base classes and utilities.
- [**repositories**](./common.md#leadr.common.repositories) – Base repository abstraction for common CRUD operations.
- [**services**](./common.md#leadr.common.services) – Base service abstraction for common business logic patterns.
- [**utils**](./common.md#leadr.common.utils) – Common utility functions.

#### `leadr.common.api`

API utilities and exception handlers.

**Modules:**

- [**exceptions**](./common.md#leadr.common.api.exceptions) – Global exception handlers for API layer.
- [**hooks**](./common.md#leadr.common.api.hooks) – Request hooks for cloud/enterprise extensibility.
- [**pagination**](./common.md#leadr.common.api.pagination) – API pagination models and dependencies.

##### `leadr.common.api.exceptions`

Global exception handlers for API layer.

**Functions:**

- [**catchall_exception_handler**](#leadr.common.api.exceptions.catchall_exception_handler) – Convert all unhandled Exceptions to a 500 HTTP response with
- [**entity_not_found_handler**](#leadr.common.api.exceptions.entity_not_found_handler) – Convert EntityNotFoundError to 404 HTTP response.
- [**http_exception_handler**](#leadr.common.api.exceptions.http_exception_handler) – Convert all FastAPI HTTPExceptions to ensure our response envelope.
- [**validation_error_handler**](#leadr.common.api.exceptions.validation_error_handler) – Convert RequestValidationError to 422 HTTP response with our

**Attributes:**

- [**logger**](./common.md#leadr.common.api.exceptions.logger) –

###### `leadr.common.api.exceptions.catchall_exception_handler`

```python
catchall_exception_handler(request, exc)
```

Convert all unhandled Exceptions to a 500 HTTP response with
our response envelope.

**Parameters:**

- **request** (<code>[Request](#fastapi.Request)</code>) – The incoming request
- **exc** (<code>[Exception](#Exception)</code>) – The exception

**Returns:**

- <code>[JSONResponse](#fastapi.responses.JSONResponse)</code> – JSONResponse with 500 status and error detail

###### `leadr.common.api.exceptions.entity_not_found_handler`

```python
entity_not_found_handler(request, exc)
```

Convert EntityNotFoundError to 404 HTTP response.

**Parameters:**

- **request** (<code>[Request](#fastapi.Request)</code>) – The incoming request
- **exc** (<code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code>) – The domain exception

**Returns:**

- <code>[JSONResponse](#fastapi.responses.JSONResponse)</code> – JSONResponse with 404 status and error detail

###### `leadr.common.api.exceptions.http_exception_handler`

```python
http_exception_handler(request, exc)
```

Convert all FastAPI HTTPExceptions to ensure our response envelope.

**Parameters:**

- **request** (<code>[Request](#fastapi.Request)</code>) – The incoming request
- **exc** (<code>[HTTPException](#fastapi.HTTPException)</code>) – The exception

**Returns:**

- <code>[JSONResponse](#fastapi.responses.JSONResponse)</code> – JSONResponse with HTTP status code and error detail

###### `leadr.common.api.exceptions.logger`

```python
logger = logging.getLogger(__name__)
```

###### `leadr.common.api.exceptions.validation_error_handler`

```python
validation_error_handler(request, exc)
```

Convert RequestValidationError to 422 HTTP response with our
error response envelope.

**Parameters:**

- **request** (<code>[Request](#fastapi.Request)</code>) – The incoming request
- **exc** (<code>[RequestValidationError](#fastapi.exceptions.RequestValidationError)</code>) – The validation exception

**Returns:**

- <code>[JSONResponse](#fastapi.responses.JSONResponse)</code> – JSONResponse with 422 status and list of validation errors

##### `leadr.common.api.hooks`

Request hooks for cloud/enterprise extensibility.

These hooks are no-ops in OSS but can be overridden via FastAPI dependency_overrides.

**Classes:**

- [**Hook**](./common.md#leadr.common.api.hooks.Hook) – Generic hook type for resource lifecycle events.
- [**UpdateHook**](./common.md#leadr.common.api.hooks.UpdateHook) – Hook type for update operations that need the resource's account_id.

**Functions:**

- [**get_post_create_board_hook**](#leadr.common.api.hooks.get_post_create_board_hook) – Get the post-create board hook. Override in cloud.
- [**get_post_create_game_hook**](#leadr.common.api.hooks.get_post_create_game_hook) – Get the post-create game hook. Override in cloud.
- [**get_post_create_score_hook**](#leadr.common.api.hooks.get_post_create_score_hook) – Get the post-create score hook. Override in cloud.
- [**get_pre_create_board_hook**](#leadr.common.api.hooks.get_pre_create_board_hook) – Get the pre-create board hook. Override in cloud.
- [**get_pre_create_board_template_hook**](#leadr.common.api.hooks.get_pre_create_board_template_hook) – Get the pre-create board template hook. Override in cloud.
- [**get_pre_create_game_hook**](#leadr.common.api.hooks.get_pre_create_game_hook) – Get the pre-create game hook. Override in cloud.
- [**get_pre_create_score_hook**](#leadr.common.api.hooks.get_pre_create_score_hook) – Get the pre-create score hook. Override in cloud.
- [**get_pre_update_board_template_hook**](#leadr.common.api.hooks.get_pre_update_board_template_hook) – Get the pre-update board template hook. Override in cloud.
- [**get_rate_limit_hook**](#leadr.common.api.hooks.get_rate_limit_hook) – Get the rate limit hook. Override in cloud.
- [**noop_post_create_board**](#leadr.common.api.hooks.noop_post_create_board) – No-op post-create board hook.
- [**noop_post_create_game**](#leadr.common.api.hooks.noop_post_create_game) – No-op post-create game hook.
- [**noop_post_create_score**](#leadr.common.api.hooks.noop_post_create_score) – No-op post-create score hook.
- [**noop_pre_create_board**](#leadr.common.api.hooks.noop_pre_create_board) – No-op pre-create board hook.
- [**noop_pre_create_board_template**](#leadr.common.api.hooks.noop_pre_create_board_template) – No-op pre-create board template hook.
- [**noop_pre_create_game**](#leadr.common.api.hooks.noop_pre_create_game) – No-op pre-create game hook.
- [**noop_pre_create_score**](#leadr.common.api.hooks.noop_pre_create_score) – No-op pre-create score hook.
- [**noop_pre_update_board_template**](#leadr.common.api.hooks.noop_pre_update_board_template) – No-op pre-update board template hook.
- [**noop_rate_limit_check**](#leadr.common.api.hooks.noop_rate_limit_check) – No-op rate limit hook.
- [**require_rate_limit_check**](#leadr.common.api.hooks.require_rate_limit_check) – Rate limit dependency for router-level application.

**Attributes:**

- [**AuthT**](./common.md#leadr.common.api.hooks.AuthT) –
- [**PostCreateBoardHook**](./common.md#leadr.common.api.hooks.PostCreateBoardHook) (<code>[TypeAlias](#typing.TypeAlias)</code>) –
- [**PostCreateBoardHookDep**](./common.md#leadr.common.api.hooks.PostCreateBoardHookDep) –
- [**PostCreateGameHook**](./common.md#leadr.common.api.hooks.PostCreateGameHook) (<code>[TypeAlias](#typing.TypeAlias)</code>) –
- [**PostCreateGameHookDep**](./common.md#leadr.common.api.hooks.PostCreateGameHookDep) –
- [**PostCreateScoreHook**](./common.md#leadr.common.api.hooks.PostCreateScoreHook) (<code>[TypeAlias](#typing.TypeAlias)</code>) –
- [**PostCreateScoreHookDep**](./common.md#leadr.common.api.hooks.PostCreateScoreHookDep) –
- [**PreCreateBoardHook**](./common.md#leadr.common.api.hooks.PreCreateBoardHook) (<code>[TypeAlias](#typing.TypeAlias)</code>) –
- [**PreCreateBoardHookDep**](./common.md#leadr.common.api.hooks.PreCreateBoardHookDep) –
- [**PreCreateBoardTemplateHook**](./common.md#leadr.common.api.hooks.PreCreateBoardTemplateHook) (<code>[TypeAlias](#typing.TypeAlias)</code>) –
- [**PreCreateBoardTemplateHookDep**](./common.md#leadr.common.api.hooks.PreCreateBoardTemplateHookDep) –
- [**PreCreateGameHook**](./common.md#leadr.common.api.hooks.PreCreateGameHook) (<code>[TypeAlias](#typing.TypeAlias)</code>) –
- [**PreCreateGameHookDep**](./common.md#leadr.common.api.hooks.PreCreateGameHookDep) –
- [**PreCreateScoreHook**](./common.md#leadr.common.api.hooks.PreCreateScoreHook) (<code>[TypeAlias](#typing.TypeAlias)</code>) –
- [**PreCreateScoreHookDep**](./common.md#leadr.common.api.hooks.PreCreateScoreHookDep) –
- [**PreUpdateBoardTemplateHook**](./common.md#leadr.common.api.hooks.PreUpdateBoardTemplateHook) (<code>[TypeAlias](#typing.TypeAlias)</code>) –
- [**PreUpdateBoardTemplateHookDep**](./common.md#leadr.common.api.hooks.PreUpdateBoardTemplateHookDep) –
- [**RateLimitHook**](./common.md#leadr.common.api.hooks.RateLimitHook) –
- [**RequestT**](./common.md#leadr.common.api.hooks.RequestT) –

###### `leadr.common.api.hooks.AuthT`

```python
AuthT = TypeVar('AuthT', contravariant=True)
```

###### `leadr.common.api.hooks.Hook`

Bases: <code>[Protocol](#typing.Protocol)\[[RequestT](./common.md#leadr.common.api.hooks.RequestT), [AuthT](./common.md#leadr.common.api.hooks.AuthT)\]</code>

Generic hook type for resource lifecycle events.

All hooks follow the signature: (request, auth, background_tasks) -> None

- request: The Pydantic request schema for the operation
- auth: The authentication context (AdminAuthContext or ClientAuthContext)
- background_tasks: FastAPI BackgroundTasks for scheduling async work

###### `leadr.common.api.hooks.PostCreateBoardHook`

```python
PostCreateBoardHook: TypeAlias = Hook[BoardCreateRequest, AdminAuthContext]
```

###### `leadr.common.api.hooks.PostCreateBoardHookDep`

```python
PostCreateBoardHookDep = Annotated[PostCreateBoardHook, Depends(get_post_create_board_hook)]
```

###### `leadr.common.api.hooks.PostCreateGameHook`

```python
PostCreateGameHook: TypeAlias = Hook[GameCreateRequest, AdminAuthContext]
```

###### `leadr.common.api.hooks.PostCreateGameHookDep`

```python
PostCreateGameHookDep = Annotated[PostCreateGameHook, Depends(get_post_create_game_hook)]
```

###### `leadr.common.api.hooks.PostCreateScoreHook`

```python
PostCreateScoreHook: TypeAlias = Hook[ScoreClientCreateRequest, ClientAuthContext]
```

###### `leadr.common.api.hooks.PostCreateScoreHookDep`

```python
PostCreateScoreHookDep = Annotated[PostCreateScoreHook, Depends(get_post_create_score_hook)]
```

###### `leadr.common.api.hooks.PreCreateBoardHook`

```python
PreCreateBoardHook: TypeAlias = Hook[BoardCreateRequest, AdminAuthContext]
```

###### `leadr.common.api.hooks.PreCreateBoardHookDep`

```python
PreCreateBoardHookDep = Annotated[PreCreateBoardHook, Depends(get_pre_create_board_hook)]
```

###### `leadr.common.api.hooks.PreCreateBoardTemplateHook`

```python
PreCreateBoardTemplateHook: TypeAlias = Hook[BoardTemplateCreateRequest, AdminAuthContext]
```

###### `leadr.common.api.hooks.PreCreateBoardTemplateHookDep`

```python
PreCreateBoardTemplateHookDep = Annotated[PreCreateBoardTemplateHook, Depends(get_pre_create_board_template_hook)]
```

###### `leadr.common.api.hooks.PreCreateGameHook`

```python
PreCreateGameHook: TypeAlias = Hook[GameCreateRequest, AdminAuthContext]
```

###### `leadr.common.api.hooks.PreCreateGameHookDep`

```python
PreCreateGameHookDep = Annotated[PreCreateGameHook, Depends(get_pre_create_game_hook)]
```

###### `leadr.common.api.hooks.PreCreateScoreHook`

```python
PreCreateScoreHook: TypeAlias = Hook[ScoreClientCreateRequest, ClientAuthContext]
```

###### `leadr.common.api.hooks.PreCreateScoreHookDep`

```python
PreCreateScoreHookDep = Annotated[PreCreateScoreHook, Depends(get_pre_create_score_hook)]
```

###### `leadr.common.api.hooks.PreUpdateBoardTemplateHook`

```python
PreUpdateBoardTemplateHook: TypeAlias = UpdateHook[BoardTemplateUpdateRequest, AdminAuthContext]
```

###### `leadr.common.api.hooks.PreUpdateBoardTemplateHookDep`

```python
PreUpdateBoardTemplateHookDep = Annotated[PreUpdateBoardTemplateHook, Depends(get_pre_update_board_template_hook)]
```

###### `leadr.common.api.hooks.RateLimitHook`

```python
RateLimitHook = Callable[[Request], Awaitable[None]]
```

###### `leadr.common.api.hooks.RequestT`

```python
RequestT = TypeVar('RequestT', contravariant=True)
```

###### `leadr.common.api.hooks.UpdateHook`

Bases: <code>[Protocol](#typing.Protocol)\[[RequestT](./common.md#leadr.common.api.hooks.RequestT), [AuthT](./common.md#leadr.common.api.hooks.AuthT)\]</code>

Hook type for update operations that need the resource's account_id.

Update hooks receive account_id separately since it comes from the existing
resource, not the update request body.

###### `leadr.common.api.hooks.get_post_create_board_hook`

```python
get_post_create_board_hook()
```

Get the post-create board hook. Override in cloud.

###### `leadr.common.api.hooks.get_post_create_game_hook`

```python
get_post_create_game_hook()
```

Get the post-create game hook. Override in cloud.

###### `leadr.common.api.hooks.get_post_create_score_hook`

```python
get_post_create_score_hook()
```

Get the post-create score hook. Override in cloud.

###### `leadr.common.api.hooks.get_pre_create_board_hook`

```python
get_pre_create_board_hook()
```

Get the pre-create board hook. Override in cloud.

###### `leadr.common.api.hooks.get_pre_create_board_template_hook`

```python
get_pre_create_board_template_hook()
```

Get the pre-create board template hook. Override in cloud.

###### `leadr.common.api.hooks.get_pre_create_game_hook`

```python
get_pre_create_game_hook()
```

Get the pre-create game hook. Override in cloud.

###### `leadr.common.api.hooks.get_pre_create_score_hook`

```python
get_pre_create_score_hook()
```

Get the pre-create score hook. Override in cloud.

###### `leadr.common.api.hooks.get_pre_update_board_template_hook`

```python
get_pre_update_board_template_hook()
```

Get the pre-update board template hook. Override in cloud.

###### `leadr.common.api.hooks.get_rate_limit_hook`

```python
get_rate_limit_hook()
```

Get the rate limit hook. Override in cloud.

###### `leadr.common.api.hooks.noop_post_create_board`

```python
noop_post_create_board(request, auth, background_tasks)
```

No-op post-create board hook.

###### `leadr.common.api.hooks.noop_post_create_game`

```python
noop_post_create_game(request, auth, background_tasks)
```

No-op post-create game hook.

###### `leadr.common.api.hooks.noop_post_create_score`

```python
noop_post_create_score(request, auth, background_tasks)
```

No-op post-create score hook.

###### `leadr.common.api.hooks.noop_pre_create_board`

```python
noop_pre_create_board(request, auth, background_tasks)
```

No-op pre-create board hook.

###### `leadr.common.api.hooks.noop_pre_create_board_template`

```python
noop_pre_create_board_template(request, auth, background_tasks)
```

No-op pre-create board template hook.

###### `leadr.common.api.hooks.noop_pre_create_game`

```python
noop_pre_create_game(request, auth, background_tasks)
```

No-op pre-create game hook.

###### `leadr.common.api.hooks.noop_pre_create_score`

```python
noop_pre_create_score(request, auth, background_tasks)
```

No-op pre-create score hook.

###### `leadr.common.api.hooks.noop_pre_update_board_template`

```python
noop_pre_update_board_template(account_id, request, auth, background_tasks)
```

No-op pre-update board template hook.

###### `leadr.common.api.hooks.noop_rate_limit_check`

```python
noop_rate_limit_check(request)
```

No-op rate limit hook.

###### `leadr.common.api.hooks.require_rate_limit_check`

```python
require_rate_limit_check(request, hook)
```

Rate limit dependency for router-level application.

##### `leadr.common.api.pagination`

API pagination models and dependencies.

**Classes:**

- [**PaginatedResponse**](./common.md#leadr.common.api.pagination.PaginatedResponse) – Generic paginated response wrapper.
- [**PaginationMeta**](./common.md#leadr.common.api.pagination.PaginationMeta) – Pagination metadata in API responses.
- [**PaginationParams**](./common.md#leadr.common.api.pagination.PaginationParams) – FastAPI dependency for parsing pagination query parameters.

**Attributes:**

- [**DomainT**](./common.md#leadr.common.api.pagination.DomainT) –
- [**ResponseT**](./common.md#leadr.common.api.pagination.ResponseT) –
- [**T**](./common.md#leadr.common.api.pagination.T) –

###### `leadr.common.api.pagination.DomainT`

```python
DomainT = TypeVar('DomainT')
```

###### `leadr.common.api.pagination.PaginatedResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>, <code>[Generic](#typing.Generic)\[[T](./common.md#leadr.common.api.pagination.T)\]</code>

Generic paginated response wrapper.

Wraps a list of items with pagination metadata.

**Functions:**

- [**from_paginated_result**](#leadr.common.api.pagination.PaginatedResponse.from_paginated_result) – Create a PaginatedResponse from a PaginatedResult.

**Attributes:**

- [**data**](./common.md#leadr.common.api.pagination.PaginatedResponse.data) (<code>[list](#list)\[[T](./common.md#leadr.common.api.pagination.T)\]</code>) –
- [**model_config**](#leadr.common.api.pagination.PaginatedResponse.model_config) –
- [**pagination**](./common.md#leadr.common.api.pagination.PaginatedResponse.pagination) (<code>[PaginationMeta](./common.md#leadr.common.api.pagination.PaginationMeta)</code>) –

####### `leadr.common.api.pagination.PaginatedResponse.data`

```python
data: list[T] = Field(description='List of items in this page')
```

####### `leadr.common.api.pagination.PaginatedResponse.from_paginated_result`

```python
from_paginated_result(result, pagination, filters, response_model)
```

Create a PaginatedResponse from a PaginatedResult.

This factory method abstracts away cursor construction, converting a repository-layer
PaginatedResult into an API-layer PaginatedResponse with encoded cursors.

**Parameters:**

- **result** (<code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[DomainT](./common.md#leadr.common.api.pagination.DomainT)\]</code>) – The paginated result from the repository layer
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – The pagination parameters from the request
- **filters** (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\]</code>) – Dict of active filters to include in cursors (e.g., {"game_id": "123"})
- **response_model** (<code>[type](#type)\[[ResponseT](./common.md#leadr.common.api.pagination.ResponseT)\]</code>) – The response model class with a from_domain() method

**Returns:**

- <code>[PaginatedResponse](./common.md#leadr.common.api.pagination.PaginatedResponse)\[[ResponseT](./common.md#leadr.common.api.pagination.ResponseT)\]</code> – A fully constructed PaginatedResponse with encoded cursors and converted items

<details class="example" open markdown="1">
<summary>Example</summary>

> > > return PaginatedResponse.from_paginated_result(
> > > ... result=result,
> > > ... pagination=pagination,
> > > ... filters={"game_id": str(game_id)} if game_id else {},
> > > ... response_model=ScoreResponse,
> > > ... )

</details>

####### `leadr.common.api.pagination.PaginatedResponse.model_config`

```python
model_config = ConfigDict(json_schema_extra={'example': {'data': [{'id': 'scr_123', 'value': 1000}], 'pagination': {'next_cursor': 'eyJwdiI6WzEwMDAsMTIzXX0=', 'prev_cursor': None, 'has_next': True, 'has_prev': False, 'count': 20}}})
```

####### `leadr.common.api.pagination.PaginatedResponse.pagination`

```python
pagination: PaginationMeta = Field(description='Pagination metadata')
```

###### `leadr.common.api.pagination.PaginationMeta`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Pagination metadata in API responses.

**Attributes:**

- [**count**](./common.md#leadr.common.api.pagination.PaginationMeta.count) (<code>[int](#int)</code>) –
- [**has_next**](#leadr.common.api.pagination.PaginationMeta.has_next) (<code>[bool](#bool)</code>) –
- [**has_prev**](#leadr.common.api.pagination.PaginationMeta.has_prev) (<code>[bool](#bool)</code>) –
- [**next_cursor**](#leadr.common.api.pagination.PaginationMeta.next_cursor) (<code>[str](#str) | None</code>) –
- [**prev_cursor**](#leadr.common.api.pagination.PaginationMeta.prev_cursor) (<code>[str](#str) | None</code>) –

####### `leadr.common.api.pagination.PaginationMeta.count`

```python
count: int = Field(description='Number of items in this page')
```

####### `leadr.common.api.pagination.PaginationMeta.has_next`

```python
has_next: bool = Field(description='Whether there are more results after this page')
```

####### `leadr.common.api.pagination.PaginationMeta.has_prev`

```python
has_prev: bool = Field(description='Whether there are results before this page')
```

####### `leadr.common.api.pagination.PaginationMeta.next_cursor`

```python
next_cursor: str | None = Field(None, description='Cursor for the next page of results')
```

####### `leadr.common.api.pagination.PaginationMeta.prev_cursor`

```python
prev_cursor: str | None = Field(None, description='Cursor for the previous page of results')
```

###### `leadr.common.api.pagination.PaginationParams`

```python
PaginationParams(cursor=Query(None, description='Pagination cursor for navigating results'), limit=Query(20, ge=1, le=100, description='Number of items per page (1-100)'), sort=Query(None, description="Sort specification (e.g., 'value:desc,created_at:asc')"))
```

FastAPI dependency for parsing pagination query parameters.

Parses cursor, limit, and sort parameters from the query string.
Always appends 'id:asc' to sort specification for stable sorting.

**Functions:**

- [**decode_cursor**](#leadr.common.api.pagination.PaginationParams.decode_cursor) – Decode the cursor if present.
- [**has_cursor**](#leadr.common.api.pagination.PaginationParams.has_cursor) – Check if a cursor is present.

**Attributes:**

- [**cursor_str**](#leadr.common.api.pagination.PaginationParams.cursor_str) –
- [**limit**](./common.md#leadr.common.api.pagination.PaginationParams.limit) –
- [**sort_spec**](#leadr.common.api.pagination.PaginationParams.sort_spec) –

**Parameters:**

- **cursor** (<code>[str](#str) | None</code>) – Optional base64-encoded cursor string
- **limit** (<code>[int](#int)</code>) – Page size (1-100, default 20)
- **sort** (<code>[str](#str) | None</code>) – Comma-separated sort spec (e.g., "score:desc,created_at:asc")

####### `leadr.common.api.pagination.PaginationParams.cursor_str`

```python
cursor_str = cursor
```

####### `leadr.common.api.pagination.PaginationParams.decode_cursor`

```python
decode_cursor()
```

Decode the cursor if present.

**Returns:**

- <code>[Cursor](./common.md#leadr.common.domain.cursor.Cursor) | None</code> – Decoded Cursor object or None if no cursor

**Raises:**

- <code>[CursorValidationError](#CursorValidationError)</code> – If cursor is invalid

####### `leadr.common.api.pagination.PaginationParams.has_cursor`

```python
has_cursor()
```

Check if a cursor is present.

####### `leadr.common.api.pagination.PaginationParams.limit`

```python
limit = limit
```

####### `leadr.common.api.pagination.PaginationParams.sort_spec`

```python
sort_spec = self._parse_sort(sort)
```

###### `leadr.common.api.pagination.ResponseT`

```python
ResponseT = TypeVar('ResponseT', bound=BaseModel)
```

###### `leadr.common.api.pagination.T`

```python
T = TypeVar('T')
```

#### `leadr.common.background_tasks`

Background task scheduler using asyncio.

Provides a simple background task scheduler that runs periodic tasks
within the FastAPI application process.

**Classes:**

- [**BackgroundTaskScheduler**](#leadr.common.background_tasks.BackgroundTaskScheduler) – Manages periodic background tasks using asyncio.

**Functions:**

- [**get_scheduler**](#leadr.common.background_tasks.get_scheduler) – Get the global scheduler instance.

**Attributes:**

- [**logger**](#leadr.common.background_tasks.logger) –

##### `leadr.common.background_tasks.BackgroundTaskScheduler`

```python
BackgroundTaskScheduler()
```

Manages periodic background tasks using asyncio.

Tasks run in the same process as the FastAPI application,
making them easy to test and deploy without additional infrastructure.

<details class="example" open markdown="1">
<summary>Example</summary>

> > > scheduler = BackgroundTaskScheduler()
> > > async def my_task():
> > > ... print("Task running")
> > > scheduler.add_task("my-task", my_task, interval_seconds=60)
> > > await scheduler.start()

</details>

**Functions:**

- [**add_task**](#leadr.common.background_tasks.BackgroundTaskScheduler.add_task) – Register a periodic task.
- [**start**](#leadr.common.background_tasks.BackgroundTaskScheduler.start) – Start all registered tasks.
- [**stop**](#leadr.common.background_tasks.BackgroundTaskScheduler.stop) – Stop all running tasks gracefully.

**Attributes:**

- [**running**](#leadr.common.background_tasks.BackgroundTaskScheduler.running) –
- [**tasks**](#leadr.common.background_tasks.BackgroundTaskScheduler.tasks) (<code>[dict](#dict)\[[str](#str), [dict](#dict)\[[str](#str), [Any](#typing.Any)\]\]</code>) –

###### `leadr.common.background_tasks.BackgroundTaskScheduler.add_task`

```python
add_task(name, func, interval_seconds)
```

Register a periodic task.

**Parameters:**

- **name** (<code>[str](#str)</code>) – Unique identifier for the task.
- **func** (<code>[Callable](#collections.abc.Callable)\[[], [Awaitable](#collections.abc.Awaitable)[None]\]</code>) – Async function to call periodically.
- **interval_seconds** (<code>[int](#int)</code>) – How often to run the task (in seconds).

**Raises:**

- <code>[ValueError](#ValueError)</code> – If task with the same name already exists.

###### `leadr.common.background_tasks.BackgroundTaskScheduler.running`

```python
running = False
```

###### `leadr.common.background_tasks.BackgroundTaskScheduler.start`

```python
start()
```

Start all registered tasks.

This method starts all background task loops concurrently.
It returns immediately after starting the tasks.

###### `leadr.common.background_tasks.BackgroundTaskScheduler.stop`

```python
stop()
```

Stop all running tasks gracefully.

Waits for currently executing tasks to complete before stopping.

###### `leadr.common.background_tasks.BackgroundTaskScheduler.tasks`

```python
tasks: dict[str, dict[str, Any]] = {}
```

##### `leadr.common.background_tasks.get_scheduler`

```python
get_scheduler()
```

Get the global scheduler instance.

**Returns:**

- <code>[BackgroundTaskScheduler](#leadr.common.background_tasks.BackgroundTaskScheduler)</code> – The singleton BackgroundTaskScheduler instance.

##### `leadr.common.background_tasks.logger`

```python
logger = logging.getLogger(__name__)
```

#### `leadr.common.database`

Database connection and session management.

**Functions:**

- [**build_database_url**](#leadr.common.database.build_database_url) – Build async database URL from settings.
- [**build_direct_database_url**](#leadr.common.database.build_direct_database_url) – Build async database URL for direct connections (migrations).
- [**get_db**](#leadr.common.database.get_db) – FastAPI dependency for async database session.

**Attributes:**

- [**async_session_factory**](#leadr.common.database.async_session_factory) –
- [**engine**](./common.md#leadr.common.database.engine) –

##### `leadr.common.database.async_session_factory`

```python
async_session_factory = async_sessionmaker(engine, class_=AsyncSession, expire_on_commit=False)
```

##### `leadr.common.database.build_database_url`

```python
build_database_url()
```

Build async database URL from settings.

##### `leadr.common.database.build_direct_database_url`

```python
build_direct_database_url()
```

Build async database URL for direct connections (migrations).

Uses DB_HOST_DIRECT if set, otherwise falls back to DB_HOST.
For Neon, DB_HOST_DIRECT should be the non-pooler endpoint to avoid
connecting through PgBouncer during migrations.

##### `leadr.common.database.engine`

```python
engine = create_async_engine(build_database_url(), connect_args=(_get_connect_args()), poolclass=(_get_pool_class()), **(_get_pool_options()), echo=(settings.DB_ECHO))
```

##### `leadr.common.database.get_db`

```python
get_db()
```

FastAPI dependency for async database session.

The session is yielded to the caller, who is responsible for
committing transactions explicitly. The context manager automatically
handles cleanup and rollback on exceptions.

#### `leadr.common.dependencies`

Shared FastAPI dependencies for the application.

**Attributes:**

- [**DatabaseSession**](./common.md#leadr.common.dependencies.DatabaseSession) –

##### `leadr.common.dependencies.DatabaseSession`

```python
DatabaseSession = Annotated[AsyncSession, Depends(get_db)]
```

#### `leadr.common.domain`

**Modules:**

- [**cursor**](./common.md#leadr.common.domain.cursor) – Cursor-based pagination implementation.
- [**exceptions**](./common.md#leadr.common.domain.exceptions) – Domain-specific exceptions for LEADR.
- [**ids**](./common.md#leadr.common.domain.ids) – Prefixed ID types for entity identification.
- [**models**](./common.md#leadr.common.domain.models) – Common domain models and value objects.
- [**pagination**](./common.md#leadr.common.domain.pagination) – Pagination domain models.
- [**pagination_result**](#leadr.common.domain.pagination_result) – Pagination result from repository layer.

##### `leadr.common.domain.cursor`

Cursor-based pagination implementation.

**Classes:**

- [**Cursor**](./common.md#leadr.common.domain.cursor.Cursor) – Opaque cursor for pagination that encodes position, sort, filters, and direction.
- [**CursorValidationError**](./common.md#leadr.common.domain.cursor.CursorValidationError) – Raised when cursor validation fails.

**Attributes:**

- [**logger**](./common.md#leadr.common.domain.cursor.logger) –

###### `leadr.common.domain.cursor.Cursor`

```python
Cursor(position, sort_fields, filters, direction)
```

Opaque cursor for pagination that encodes position, sort, filters, and direction.

The cursor ensures that pagination state (sort order, filters) remains consistent
across page requests. If the client changes sort/filter parameters while using
a cursor, validation will fail.

**Functions:**

- [**decode**](./common.md#leadr.common.domain.cursor.Cursor.decode) – Decode cursor from base64 string.
- [**encode**](./common.md#leadr.common.domain.cursor.Cursor.encode) – Encode cursor to base64 string.
- [**validate_state**](#leadr.common.domain.cursor.Cursor.validate_state) – Validate that current query state matches cursor state.

**Attributes:**

- [**direction**](./common.md#leadr.common.domain.cursor.Cursor.direction) –
- [**filters**](./common.md#leadr.common.domain.cursor.Cursor.filters) –
- [**position**](./common.md#leadr.common.domain.cursor.Cursor.position) –
- [**sort_fields**](#leadr.common.domain.cursor.Cursor.sort_fields) –

**Parameters:**

- **position** (<code>[CursorPosition](./common.md#leadr.common.domain.pagination.CursorPosition)</code>) – The position in the result set (values + entity_id)
- **sort_fields** (<code>[list](#list)\[[SortField](./common.md#leadr.common.domain.pagination.SortField)\]</code>) – List of sort fields that were applied
- **filters** (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\]</code>) – Dictionary of filter parameters that were applied
- **direction** (<code>[PaginationDirection](./common.md#leadr.common.domain.pagination.PaginationDirection)</code>) – Direction of pagination (forward or backward)

####### `leadr.common.domain.cursor.Cursor.decode`

```python
decode(cursor_str)
```

Decode cursor from base64 string.

**Parameters:**

- **cursor_str** (<code>[str](#str)</code>) – Base64-encoded cursor string

**Returns:**

- <code>[Cursor](./common.md#leadr.common.domain.cursor.Cursor)</code> – Decoded Cursor object

**Raises:**

- <code>[CursorValidationError](./common.md#leadr.common.domain.cursor.CursorValidationError)</code> – If cursor is invalid or malformed

####### `leadr.common.domain.cursor.Cursor.direction`

```python
direction = direction
```

####### `leadr.common.domain.cursor.Cursor.encode`

```python
encode()
```

Encode cursor to base64 string.

**Returns:**

- <code>[str](#str)</code> – Base64-encoded JSON string representing the cursor state

####### `leadr.common.domain.cursor.Cursor.filters`

```python
filters = filters
```

####### `leadr.common.domain.cursor.Cursor.position`

```python
position = position
```

####### `leadr.common.domain.cursor.Cursor.sort_fields`

```python
sort_fields = sort_fields
```

####### `leadr.common.domain.cursor.Cursor.validate_state`

```python
validate_state(sort_fields, filters)
```

Validate that current query state matches cursor state.

**Parameters:**

- **sort_fields** (<code>[list](#list)\[[SortField](./common.md#leadr.common.domain.pagination.SortField)\]</code>) – Current sort fields
- **filters** (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\]</code>) – Current filter parameters

**Raises:**

- <code>[CursorValidationError](./common.md#leadr.common.domain.cursor.CursorValidationError)</code> – If state doesn't match

###### `leadr.common.domain.cursor.CursorValidationError`

Bases: <code>[ValueError](#ValueError)</code>

Raised when cursor validation fails.

###### `leadr.common.domain.cursor.logger`

```python
logger = logging.getLogger(__name__)
```

##### `leadr.common.domain.exceptions`

Domain-specific exceptions for LEADR.

**Classes:**

- [**DomainError**](./common.md#leadr.common.domain.exceptions.DomainError) – Base exception for all domain-level errors.
- [**EntityNotFoundError**](./common.md#leadr.common.domain.exceptions.EntityNotFoundError) – Raised when an entity cannot be found in the repository.
- [**InvalidEntityStateError**](./common.md#leadr.common.domain.exceptions.InvalidEntityStateError) – Raised when an entity is in an invalid state for the requested operation.
- [**ValidationError**](./common.md#leadr.common.domain.exceptions.ValidationError) – Raised when entity validation fails.

###### `leadr.common.domain.exceptions.DomainError`

```python
DomainError(message)
```

Bases: <code>[Exception](#Exception)</code>

Base exception for all domain-level errors.

All custom domain exceptions should inherit from this base class.
This allows catching all domain errors with a single except clause.

**Parameters:**

- **message** (<code>[str](#str)</code>) – Human-readable error message.

<details class="example" open markdown="1">
<summary>Example</summary>

> > > try:
> > > ... raise DomainError("Something went wrong")
> > > ... except DomainError as e:
> > > ... print(e.message)

</details>

**Attributes:**

- [**message**](./common.md#leadr.common.domain.exceptions.DomainError.message) –

####### `leadr.common.domain.exceptions.DomainError.message`

```python
message = message
```

###### `leadr.common.domain.exceptions.EntityNotFoundError`

```python
EntityNotFoundError(entity_type, entity_id)
```

Bases: <code>[DomainError](./common.md#leadr.common.domain.exceptions.DomainError)</code>

Raised when an entity cannot be found in the repository.

This exception is raised by repository queries when an entity with
the specified ID does not exist in the database.

**Parameters:**

- **entity_type** (<code>[str](#str)</code>) – Name of the entity type (e.g., "Account", "User").
- **entity_id** (<code>[str](#str)</code>) – The ID that was not found.

<details class="example" open markdown="1">
<summary>Example</summary>

> > > raise EntityNotFoundError("Account", "123e4567-e89b-12d3-a456-426614174000")
> > > EntityNotFoundError: Account not found: 123e4567-e89b-12d3-a456-426614174000

</details>

**Attributes:**

- [**entity_id**](#leadr.common.domain.exceptions.EntityNotFoundError.entity_id) –
- [**entity_type**](#leadr.common.domain.exceptions.EntityNotFoundError.entity_type) –
- [**message**](./common.md#leadr.common.domain.exceptions.EntityNotFoundError.message) –

####### `leadr.common.domain.exceptions.EntityNotFoundError.entity_id`

```python
entity_id = entity_id
```

####### `leadr.common.domain.exceptions.EntityNotFoundError.entity_type`

```python
entity_type = entity_type
```

####### `leadr.common.domain.exceptions.EntityNotFoundError.message`

```python
message = message
```

###### `leadr.common.domain.exceptions.InvalidEntityStateError`

```python
InvalidEntityStateError(entity_type, reason)
```

Bases: <code>[DomainError](./common.md#leadr.common.domain.exceptions.DomainError)</code>

Raised when an entity is in an invalid state for the requested operation.

Use this exception when business rules prevent an operation due to the
current state of an entity. For example, activating an already-active account,
or modifying a deleted entity.

**Parameters:**

- **entity_type** (<code>[str](#str)</code>) – Name of the entity type (e.g., "Account", "User").
- **reason** (<code>[str](#str)</code>) – Explanation of why the state is invalid.

<details class="example" open markdown="1">
<summary>Example</summary>

> > > raise InvalidEntityStateError("Account", "Cannot activate already active account")
> > > InvalidEntityStateError: Invalid Account state: Cannot activate already active account

</details>

**Attributes:**

- [**entity_type**](#leadr.common.domain.exceptions.InvalidEntityStateError.entity_type) –
- [**message**](./common.md#leadr.common.domain.exceptions.InvalidEntityStateError.message) –
- [**reason**](./common.md#leadr.common.domain.exceptions.InvalidEntityStateError.reason) –

####### `leadr.common.domain.exceptions.InvalidEntityStateError.entity_type`

```python
entity_type = entity_type
```

####### `leadr.common.domain.exceptions.InvalidEntityStateError.message`

```python
message = message
```

####### `leadr.common.domain.exceptions.InvalidEntityStateError.reason`

```python
reason = reason
```

###### `leadr.common.domain.exceptions.ValidationError`

```python
ValidationError(entity_type, field, reason)
```

Bases: <code>[DomainError](./common.md#leadr.common.domain.exceptions.DomainError)</code>

Raised when entity validation fails.

Use this exception when field-level validation fails, such as invalid
format, out-of-range values, or constraint violations.

**Parameters:**

- **entity_type** (<code>[str](#str)</code>) – Name of the entity type (e.g., "Account", "User").
- **field** (<code>[str](#str)</code>) – Name of the field that failed validation.
- **reason** (<code>[str](#str)</code>) – Explanation of why validation failed.

<details class="example" open markdown="1">
<summary>Example</summary>

> > > raise ValidationError("Account", "slug", "Must be lowercase alphanumeric")
> > > ValidationError: Account.slug: Must be lowercase alphanumeric

</details>

**Attributes:**

- [**entity_type**](#leadr.common.domain.exceptions.ValidationError.entity_type) –
- [**field**](./common.md#leadr.common.domain.exceptions.ValidationError.field) –
- [**message**](./common.md#leadr.common.domain.exceptions.ValidationError.message) –
- [**reason**](./common.md#leadr.common.domain.exceptions.ValidationError.reason) –

####### `leadr.common.domain.exceptions.ValidationError.entity_type`

```python
entity_type = entity_type
```

####### `leadr.common.domain.exceptions.ValidationError.field`

```python
field = field
```

####### `leadr.common.domain.exceptions.ValidationError.message`

```python
message = message
```

####### `leadr.common.domain.exceptions.ValidationError.reason`

```python
reason = reason
```

##### `leadr.common.domain.ids`

Prefixed ID types for entity identification.

**Classes:**

- [**APIKeyID**](./common.md#leadr.common.domain.ids.APIKeyID) – API key entity identifier.
- [**AccountID**](./common.md#leadr.common.domain.ids.AccountID) – Account entity identifier.
- [**BoardID**](./common.md#leadr.common.domain.ids.BoardID) – Board entity identifier.
- [**BoardTemplateID**](./common.md#leadr.common.domain.ids.BoardTemplateID) – Board template entity identifier.
- [**DeviceID**](./common.md#leadr.common.domain.ids.DeviceID) – Device entity identifier.
- [**DeviceSessionID**](./common.md#leadr.common.domain.ids.DeviceSessionID) – Device session entity identifier.
- [**EmailID**](./common.md#leadr.common.domain.ids.EmailID) – Email entity identifier.
- [**GameID**](./common.md#leadr.common.domain.ids.GameID) – Game entity identifier.
- [**JamCodeID**](./common.md#leadr.common.domain.ids.JamCodeID) – Jam Code entity identifier.
- [**JamCodeRedemptionID**](./common.md#leadr.common.domain.ids.JamCodeRedemptionID) – Jam Code Redemption entity identifier.
- [**NonceID**](./common.md#leadr.common.domain.ids.NonceID) – Nonce entity identifier.
- [**PrefixedID**](./common.md#leadr.common.domain.ids.PrefixedID) – Base class for entity IDs with type prefixes.
- [**ScoreFlagID**](./common.md#leadr.common.domain.ids.ScoreFlagID) – Score flag entity identifier.
- [**ScoreID**](./common.md#leadr.common.domain.ids.ScoreID) – Score entity identifier.
- [**ScoreSubmissionMetaID**](./common.md#leadr.common.domain.ids.ScoreSubmissionMetaID) – Score submission metadata entity identifier.
- [**UserID**](./common.md#leadr.common.domain.ids.UserID) – User entity identifier.

###### `leadr.common.domain.ids.APIKeyID`

Bases: <code>[PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>

API key entity identifier.

**Attributes:**

- [**prefix**](./common.md#leadr.common.domain.ids.APIKeyID.prefix) –
- [**uuid**](./common.md#leadr.common.domain.ids.APIKeyID.uuid) –

####### `leadr.common.domain.ids.APIKeyID.prefix`

```python
prefix = 'key'
```

####### `leadr.common.domain.ids.APIKeyID.uuid`

```python
uuid = uuid4()
```

###### `leadr.common.domain.ids.AccountID`

Bases: <code>[PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>

Account entity identifier.

**Attributes:**

- [**prefix**](./common.md#leadr.common.domain.ids.AccountID.prefix) –
- [**uuid**](./common.md#leadr.common.domain.ids.AccountID.uuid) –

####### `leadr.common.domain.ids.AccountID.prefix`

```python
prefix = 'acc'
```

####### `leadr.common.domain.ids.AccountID.uuid`

```python
uuid = uuid4()
```

###### `leadr.common.domain.ids.BoardID`

Bases: <code>[PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>

Board entity identifier.

**Attributes:**

- [**prefix**](./common.md#leadr.common.domain.ids.BoardID.prefix) –
- [**uuid**](./common.md#leadr.common.domain.ids.BoardID.uuid) –

####### `leadr.common.domain.ids.BoardID.prefix`

```python
prefix = 'brd'
```

####### `leadr.common.domain.ids.BoardID.uuid`

```python
uuid = uuid4()
```

###### `leadr.common.domain.ids.BoardTemplateID`

Bases: <code>[PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>

Board template entity identifier.

**Attributes:**

- [**prefix**](./common.md#leadr.common.domain.ids.BoardTemplateID.prefix) –
- [**uuid**](./common.md#leadr.common.domain.ids.BoardTemplateID.uuid) –

####### `leadr.common.domain.ids.BoardTemplateID.prefix`

```python
prefix = 'tpl'
```

####### `leadr.common.domain.ids.BoardTemplateID.uuid`

```python
uuid = uuid4()
```

###### `leadr.common.domain.ids.DeviceID`

Bases: <code>[PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>

Device entity identifier.

**Attributes:**

- [**prefix**](./common.md#leadr.common.domain.ids.DeviceID.prefix) –
- [**uuid**](./common.md#leadr.common.domain.ids.DeviceID.uuid) –

####### `leadr.common.domain.ids.DeviceID.prefix`

```python
prefix = 'dev'
```

####### `leadr.common.domain.ids.DeviceID.uuid`

```python
uuid = uuid4()
```

###### `leadr.common.domain.ids.DeviceSessionID`

Bases: <code>[PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>

Device session entity identifier.

**Attributes:**

- [**prefix**](./common.md#leadr.common.domain.ids.DeviceSessionID.prefix) –
- [**uuid**](./common.md#leadr.common.domain.ids.DeviceSessionID.uuid) –

####### `leadr.common.domain.ids.DeviceSessionID.prefix`

```python
prefix = 'ses'
```

####### `leadr.common.domain.ids.DeviceSessionID.uuid`

```python
uuid = uuid4()
```

###### `leadr.common.domain.ids.EmailID`

Bases: <code>[PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>

Email entity identifier.

**Attributes:**

- [**prefix**](./common.md#leadr.common.domain.ids.EmailID.prefix) –
- [**uuid**](./common.md#leadr.common.domain.ids.EmailID.uuid) –

####### `leadr.common.domain.ids.EmailID.prefix`

```python
prefix = 'eml'
```

####### `leadr.common.domain.ids.EmailID.uuid`

```python
uuid = uuid4()
```

###### `leadr.common.domain.ids.GameID`

Bases: <code>[PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>

Game entity identifier.

**Attributes:**

- [**prefix**](./common.md#leadr.common.domain.ids.GameID.prefix) –
- [**uuid**](./common.md#leadr.common.domain.ids.GameID.uuid) –

####### `leadr.common.domain.ids.GameID.prefix`

```python
prefix = 'gam'
```

####### `leadr.common.domain.ids.GameID.uuid`

```python
uuid = uuid4()
```

###### `leadr.common.domain.ids.JamCodeID`

Bases: <code>[PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>

Jam Code entity identifier.

**Attributes:**

- [**prefix**](./common.md#leadr.common.domain.ids.JamCodeID.prefix) –
- [**uuid**](./common.md#leadr.common.domain.ids.JamCodeID.uuid) –

####### `leadr.common.domain.ids.JamCodeID.prefix`

```python
prefix = 'jam'
```

####### `leadr.common.domain.ids.JamCodeID.uuid`

```python
uuid = uuid4()
```

###### `leadr.common.domain.ids.JamCodeRedemptionID`

Bases: <code>[PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>

Jam Code Redemption entity identifier.

**Attributes:**

- [**prefix**](./common.md#leadr.common.domain.ids.JamCodeRedemptionID.prefix) –
- [**uuid**](./common.md#leadr.common.domain.ids.JamCodeRedemptionID.uuid) –

####### `leadr.common.domain.ids.JamCodeRedemptionID.prefix`

```python
prefix = 'red'
```

####### `leadr.common.domain.ids.JamCodeRedemptionID.uuid`

```python
uuid = uuid4()
```

###### `leadr.common.domain.ids.NonceID`

Bases: <code>[PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>

Nonce entity identifier.

**Attributes:**

- [**prefix**](./common.md#leadr.common.domain.ids.NonceID.prefix) –
- [**uuid**](./common.md#leadr.common.domain.ids.NonceID.uuid) –

####### `leadr.common.domain.ids.NonceID.prefix`

```python
prefix = 'non'
```

####### `leadr.common.domain.ids.NonceID.uuid`

```python
uuid = uuid4()
```

###### `leadr.common.domain.ids.PrefixedID`

```python
PrefixedID(value=None)
```

Base class for entity IDs with type prefixes.

Provides Stripe-style prefixed UUIDs (e.g., "acc_123e4567-e89b-...") while
maintaining internal UUID representation for database efficiency.

<details class="usage" open markdown="1">
<summary>Usage</summary>

- AccountID() → generates new ID
- AccountID("acc_123...") → parses prefixed string
- AccountID(uuid_obj) → wraps existing UUID

</details>

**Attributes:**

- [**prefix**](./common.md#leadr.common.domain.ids.PrefixedID.prefix) (<code>[str](#str)</code>) –
- [**uuid**](./common.md#leadr.common.domain.ids.PrefixedID.uuid) –

**Parameters:**

- **value** (<code>[str](#str) | [UUID](#uuid.UUID) | [Self](#typing.Self) | None</code>) – Optional value to initialize from:
- None: Generate new UUID
- str: Parse "prefix_uuid" format
- UUID: Wrap existing UUID
- PrefixedID: Extract UUID from another PrefixedID

**Raises:**

- <code>[ValueError](#ValueError)</code> – If string format is invalid or prefix doesn't match

####### `leadr.common.domain.ids.PrefixedID.prefix`

```python
prefix: str = ''
```

####### `leadr.common.domain.ids.PrefixedID.uuid`

```python
uuid = uuid4()
```

###### `leadr.common.domain.ids.ScoreFlagID`

Bases: <code>[PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>

Score flag entity identifier.

**Attributes:**

- [**prefix**](./common.md#leadr.common.domain.ids.ScoreFlagID.prefix) –
- [**uuid**](./common.md#leadr.common.domain.ids.ScoreFlagID.uuid) –

####### `leadr.common.domain.ids.ScoreFlagID.prefix`

```python
prefix = 'flg'
```

####### `leadr.common.domain.ids.ScoreFlagID.uuid`

```python
uuid = uuid4()
```

###### `leadr.common.domain.ids.ScoreID`

Bases: <code>[PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>

Score entity identifier.

**Attributes:**

- [**prefix**](./common.md#leadr.common.domain.ids.ScoreID.prefix) –
- [**uuid**](./common.md#leadr.common.domain.ids.ScoreID.uuid) –

####### `leadr.common.domain.ids.ScoreID.prefix`

```python
prefix = 'scr'
```

####### `leadr.common.domain.ids.ScoreID.uuid`

```python
uuid = uuid4()
```

###### `leadr.common.domain.ids.ScoreSubmissionMetaID`

Bases: <code>[PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>

Score submission metadata entity identifier.

**Attributes:**

- [**prefix**](./common.md#leadr.common.domain.ids.ScoreSubmissionMetaID.prefix) –
- [**uuid**](./common.md#leadr.common.domain.ids.ScoreSubmissionMetaID.uuid) –

####### `leadr.common.domain.ids.ScoreSubmissionMetaID.prefix`

```python
prefix = 'sub'
```

####### `leadr.common.domain.ids.ScoreSubmissionMetaID.uuid`

```python
uuid = uuid4()
```

###### `leadr.common.domain.ids.UserID`

Bases: <code>[PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>

User entity identifier.

**Attributes:**

- [**prefix**](./common.md#leadr.common.domain.ids.UserID.prefix) –
- [**uuid**](./common.md#leadr.common.domain.ids.UserID.uuid) –

####### `leadr.common.domain.ids.UserID.prefix`

```python
prefix = 'usr'
```

####### `leadr.common.domain.ids.UserID.uuid`

```python
uuid = uuid4()
```

##### `leadr.common.domain.models`

Common domain models and value objects.

**Classes:**

- [**Entity**](./common.md#leadr.common.domain.models.Entity) – Base class for all domain entities with ID and timestamps.

###### `leadr.common.domain.models.Entity`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Base class for all domain entities with ID and timestamps.

Provides common functionality for domain entities including:

- Auto-generated UUID primary key (or typed prefixed ID in subclasses)
- Created/updated timestamps (UTC)
- Soft delete support with deleted_at timestamp
- Equality and hashing based on ID

All domain entities should extend this base class. The ID and timestamps
are automatically populated on entity creation and don't need to be
provided by consumers.

Subclasses can override the `id` field with a typed PrefixedID for better
type safety and API clarity.

**Functions:**

- [**restore**](./common.md#leadr.common.domain.models.Entity.restore) – Restore a soft-deleted entity.
- [**soft_delete**](#leadr.common.domain.models.Entity.soft_delete) – Mark entity as soft-deleted.

**Attributes:**

- [**created_at**](#leadr.common.domain.models.Entity.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**deleted_at**](#leadr.common.domain.models.Entity.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**id**](./common.md#leadr.common.domain.models.Entity.id) (<code>[Any](#typing.Any)</code>) –
- [**is_deleted**](#leadr.common.domain.models.Entity.is_deleted) (<code>[bool](#bool)</code>) – Check if entity is soft-deleted.
- [**model_config**](#leadr.common.domain.models.Entity.model_config) –
- [**updated_at**](#leadr.common.domain.models.Entity.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.common.domain.models.Entity.created_at`

```python
created_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp when entity was created (UTC)')
```

####### `leadr.common.domain.models.Entity.deleted_at`

```python
deleted_at: datetime | None = Field(default=None, description='Timestamp when entity was soft-deleted (UTC), or null if active')
```

####### `leadr.common.domain.models.Entity.id`

```python
id: Any = Field(frozen=True, default_factory=uuid4, description='Unique identifier (auto-generated UUID or typed ID)')
```

####### `leadr.common.domain.models.Entity.is_deleted`

```python
is_deleted: bool
```

Check if entity is soft-deleted.

**Returns:**

- <code>[bool](#bool)</code> – True if the entity has a deleted_at timestamp, False otherwise.

####### `leadr.common.domain.models.Entity.model_config`

```python
model_config = ConfigDict(validate_assignment=True)
```

####### `leadr.common.domain.models.Entity.restore`

```python
restore()
```

Restore a soft-deleted entity.

Clears the deleted_at timestamp, making the entity active again.

<details class="example" open markdown="1">
<summary>Example</summary>

> > > account.soft_delete()
> > > account.restore()
> > > assert account.is_deleted is False

</details>

####### `leadr.common.domain.models.Entity.soft_delete`

```python
soft_delete()
```

Mark entity as soft-deleted.

Sets the deleted_at timestamp to the current UTC time. Entities that are
already deleted are not affected (deleted_at remains at original deletion time).

<details class="example" open markdown="1">
<summary>Example</summary>

> > > account = Account(name="Test", slug="test")
> > > account.soft_delete()
> > > assert account.is_deleted is True

</details>

####### `leadr.common.domain.models.Entity.updated_at`

```python
updated_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp of last update (UTC)')
```

##### `leadr.common.domain.pagination`

Pagination domain models.

**Classes:**

- [**CursorPosition**](./common.md#leadr.common.domain.pagination.CursorPosition) – Position in a paginated result set.
- [**PaginationDirection**](./common.md#leadr.common.domain.pagination.PaginationDirection) – Direction of pagination.
- [**SortDirection**](./common.md#leadr.common.domain.pagination.SortDirection) – Sort direction for fields.
- [**SortField**](./common.md#leadr.common.domain.pagination.SortField) – Specification for sorting a field.

###### `leadr.common.domain.pagination.CursorPosition`

```python
CursorPosition(values, entity_id)
```

Position in a paginated result set.

**Attributes:**

- [**values**](./common.md#leadr.common.domain.pagination.CursorPosition.values) (<code>[tuple](#tuple)\[[Any](#typing.Any), ...\]</code>) – List of values for each sort field at this position
- [**entity_id**](#leadr.common.domain.pagination.CursorPosition.entity_id) (<code>[str](#str)</code>) – The ID of the entity at this position (for stable sorting)

####### `leadr.common.domain.pagination.CursorPosition.entity_id`

```python
entity_id: str
```

####### `leadr.common.domain.pagination.CursorPosition.values`

```python
values: tuple[Any, ...]
```

###### `leadr.common.domain.pagination.PaginationDirection`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Direction of pagination.

**Attributes:**

- [**BACKWARD**](./common.md#leadr.common.domain.pagination.PaginationDirection.BACKWARD) –
- [**FORWARD**](./common.md#leadr.common.domain.pagination.PaginationDirection.FORWARD) –

####### `leadr.common.domain.pagination.PaginationDirection.BACKWARD`

```python
BACKWARD = 'backward'
```

####### `leadr.common.domain.pagination.PaginationDirection.FORWARD`

```python
FORWARD = 'forward'
```

###### `leadr.common.domain.pagination.SortDirection`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Sort direction for fields.

**Attributes:**

- [**ASC**](./common.md#leadr.common.domain.pagination.SortDirection.ASC) –
- [**DESC**](./common.md#leadr.common.domain.pagination.SortDirection.DESC) –

####### `leadr.common.domain.pagination.SortDirection.ASC`

```python
ASC = 'asc'
```

####### `leadr.common.domain.pagination.SortDirection.DESC`

```python
DESC = 'desc'
```

###### `leadr.common.domain.pagination.SortField`

```python
SortField(name, direction)
```

Specification for sorting a field.

**Attributes:**

- [**name**](./common.md#leadr.common.domain.pagination.SortField.name) (<code>[str](#str)</code>) – Field name to sort by
- [**direction**](./common.md#leadr.common.domain.pagination.SortField.direction) (<code>[SortDirection](./common.md#leadr.common.domain.pagination.SortDirection)</code>) – ASC or DESC

####### `leadr.common.domain.pagination.SortField.direction`

```python
direction: SortDirection
```

####### `leadr.common.domain.pagination.SortField.name`

```python
name: str
```

##### `leadr.common.domain.pagination_result`

Pagination result from repository layer.

**Classes:**

- [**PaginatedResult**](#leadr.common.domain.pagination_result.PaginatedResult) – Result of a paginated query from the repository layer.

**Attributes:**

- [**T**](#leadr.common.domain.pagination_result.T) –

###### `leadr.common.domain.pagination_result.PaginatedResult`

```python
PaginatedResult(items, has_next, has_prev, next_position, prev_position)
```

Bases: <code>[Generic](#typing.Generic)\[[T](#leadr.common.domain.pagination_result.T)\]</code>

Result of a paginated query from the repository layer.

**Attributes:**

- [**items**](#leadr.common.domain.pagination_result.PaginatedResult.items) (<code>[list](#list)\[[T](#leadr.common.domain.pagination_result.T)\]</code>) – List of entities returned by the query
- [**has_next**](#leadr.common.domain.pagination_result.PaginatedResult.has_next) (<code>[bool](#bool)</code>) – Whether there are more results after these items
- [**has_prev**](#leadr.common.domain.pagination_result.PaginatedResult.has_prev) (<code>[bool](#bool)</code>) – Whether there are results before these items
- [**next_position**](#leadr.common.domain.pagination_result.PaginatedResult.next_position) (<code>[CursorPosition](./common.md#leadr.common.domain.pagination.CursorPosition) | None</code>) – Position for the next page cursor (if has_next)
- [**prev_position**](#leadr.common.domain.pagination_result.PaginatedResult.prev_position) (<code>[CursorPosition](./common.md#leadr.common.domain.pagination.CursorPosition) | None</code>) – Position for the previous page cursor (if has_prev)

####### `leadr.common.domain.pagination_result.PaginatedResult.count`

```python
count: int
```

Return the number of items in this page.

####### `leadr.common.domain.pagination_result.PaginatedResult.has_next`

```python
has_next: bool
```

####### `leadr.common.domain.pagination_result.PaginatedResult.has_prev`

```python
has_prev: bool
```

####### `leadr.common.domain.pagination_result.PaginatedResult.items`

```python
items: list[T]
```

####### `leadr.common.domain.pagination_result.PaginatedResult.next_position`

```python
next_position: CursorPosition | None
```

####### `leadr.common.domain.pagination_result.PaginatedResult.prev_position`

```python
prev_position: CursorPosition | None
```

###### `leadr.common.domain.pagination_result.T`

```python
T = TypeVar('T')
```

#### `leadr.common.geoip`

GeoIP service for IP address geolocation using MaxMind databases.

**Classes:**

- [**GeoIPService**](./common.md#leadr.common.geoip.GeoIPService) – Service for IP address geolocation using MaxMind GeoLite2 databases.
- [**GeoInfo**](./common.md#leadr.common.geoip.GeoInfo) – Geolocation information extracted from IP address.

**Attributes:**

- [**logger**](./common.md#leadr.common.geoip.logger) –

##### `leadr.common.geoip.GeoIPService`

```python
GeoIPService(account_id, license_key, city_db_url, country_db_url, database_path, refresh_days=7)
```

Service for IP address geolocation using MaxMind GeoLite2 databases.

This service downloads and manages MaxMind GeoLite2 databases for IP geolocation.
Databases are cached locally and refreshed periodically.

<details class="example" open markdown="1">
<summary>Example</summary>

> > > service = GeoIPService(
> > > ... account_id="12345",
> > > ... license_key="your_key",
> > > ... city_db_url="https://download.maxmind.com/...",
> > > ... country_db_url="https://download.maxmind.com/...",
> > > ... database_path=Path(".geoip"),
> > > ... refresh_days=7,
> > > ... )
> > > await service.initialize()
> > > geo_info = service.get_geo_info("8.8.8.8")
> > > print(geo_info.country)
> > > 'US'

</details>

**Functions:**

- [**close**](./common.md#leadr.common.geoip.GeoIPService.close) – Close database readers and release resources.
- [**get_geo_info**](#leadr.common.geoip.GeoIPService.get_geo_info) – Look up geolocation information for an IP address.
- [**initialize**](./common.md#leadr.common.geoip.GeoIPService.initialize) – Initialize the GeoIP service by downloading and loading databases.

**Attributes:**

- [**account_id**](#leadr.common.geoip.GeoIPService.account_id) –
- [**city_db_url**](#leadr.common.geoip.GeoIPService.city_db_url) –
- [**country_db_url**](#leadr.common.geoip.GeoIPService.country_db_url) –
- [**database_path**](#leadr.common.geoip.GeoIPService.database_path) –
- [**license_key**](#leadr.common.geoip.GeoIPService.license_key) –
- [**refresh_days**](#leadr.common.geoip.GeoIPService.refresh_days) –

**Parameters:**

- **account_id** (<code>[str](#str)</code>) – MaxMind account ID for basic auth
- **license_key** (<code>[str](#str)</code>) – MaxMind license key for basic auth
- **city_db_url** (<code>[str](#str)</code>) – URL to download GeoLite2 City database (tar.gz)
- **country_db_url** (<code>[str](#str)</code>) – URL to download GeoLite2 Country database (tar.gz)
- **database_path** (<code>[Path](#pathlib.Path)</code>) – Directory path to store database files
- **refresh_days** (<code>[int](#int)</code>) – Number of days before refreshing databases (default: 7)

###### `leadr.common.geoip.GeoIPService.account_id`

```python
account_id = account_id
```

###### `leadr.common.geoip.GeoIPService.city_db_url`

```python
city_db_url = city_db_url
```

###### `leadr.common.geoip.GeoIPService.close`

```python
close()
```

Close database readers and release resources.

###### `leadr.common.geoip.GeoIPService.country_db_url`

```python
country_db_url = country_db_url
```

###### `leadr.common.geoip.GeoIPService.database_path`

```python
database_path = database_path
```

###### `leadr.common.geoip.GeoIPService.get_geo_info`

```python
get_geo_info(ip_address)
```

Look up geolocation information for an IP address.

**Parameters:**

- **ip_address** (<code>[str](#str)</code>) – IP address to look up (e.g., '8.8.8.8')

**Returns:**

- <code>[GeoInfo](./common.md#leadr.common.geoip.GeoInfo) | None</code> – GeoInfo with timezone, country, and city, or None if lookup fails

###### `leadr.common.geoip.GeoIPService.initialize`

```python
initialize()
```

Initialize the GeoIP service by downloading and loading databases.

This method:

1. Creates the database directory if it doesn't exist
1. Downloads databases if they don't exist or are stale
1. Extracts tar.gz files to get .mmdb files
1. Opens database readers

Errors are logged but not raised - the service will work without databases
(get_geo_info will return None).

###### `leadr.common.geoip.GeoIPService.license_key`

```python
license_key = license_key
```

###### `leadr.common.geoip.GeoIPService.refresh_days`

```python
refresh_days = refresh_days
```

##### `leadr.common.geoip.GeoInfo`

```python
GeoInfo(timezone, country, city)
```

Geolocation information extracted from IP address.

**Attributes:**

- [**timezone**](./common.md#leadr.common.geoip.GeoInfo.timezone) (<code>[str](#str) | None</code>) – IANA timezone identifier (e.g., 'America/New_York')
- [**country**](./common.md#leadr.common.geoip.GeoInfo.country) (<code>[str](#str) | None</code>) – ISO country code (e.g., 'US')
- [**city**](./common.md#leadr.common.geoip.GeoInfo.city) (<code>[str](#str) | None</code>) – City name (e.g., 'New York')

###### `leadr.common.geoip.GeoInfo.city`

```python
city: str | None
```

###### `leadr.common.geoip.GeoInfo.country`

```python
country: str | None
```

###### `leadr.common.geoip.GeoInfo.timezone`

```python
timezone: str | None
```

##### `leadr.common.geoip.logger`

```python
logger = logging.getLogger(__name__)
```

#### `leadr.common.orm`

Common ORM base classes and utilities.

**Classes:**

- [**Base**](./common.md#leadr.common.orm.Base) – Base class for all database models with UUID primary key and timestamps.

**Attributes:**

- [**nullable_timestamp**](#leadr.common.orm.nullable_timestamp) –
- [**timestamp**](./common.md#leadr.common.orm.timestamp) –
- [**uuid_pk**](#leadr.common.orm.uuid_pk) –

##### `leadr.common.orm.Base`

Bases: <code>[DeclarativeBase](#sqlalchemy.orm.DeclarativeBase)</code>

Base class for all database models with UUID primary key and timestamps.

**Attributes:**

- [**created_at**](#leadr.common.orm.Base.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**deleted_at**](#leadr.common.orm.Base.deleted_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[nullable_timestamp](#leadr.common.orm.nullable_timestamp)\]</code>) –
- [**id**](./common.md#leadr.common.orm.Base.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**updated_at**](#leadr.common.orm.Base.updated_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –

###### `leadr.common.orm.Base.created_at`

```python
created_at: Mapped[timestamp]
```

###### `leadr.common.orm.Base.deleted_at`

```python
deleted_at: Mapped[nullable_timestamp]
```

###### `leadr.common.orm.Base.id`

```python
id: Mapped[uuid_pk]
```

###### `leadr.common.orm.Base.updated_at`

```python
updated_at: Mapped[timestamp] = mapped_column(onupdate=(func.now()))
```

##### `leadr.common.orm.nullable_timestamp`

```python
nullable_timestamp = Annotated[datetime | None, mapped_column(DateTime(timezone=True), nullable=True, default=None)]
```

##### `leadr.common.orm.timestamp`

```python
timestamp = Annotated[datetime, mapped_column(DateTime(timezone=True), nullable=False, server_default=(func.now()), default=(lambda: datetime.now(UTC)))]
```

##### `leadr.common.orm.uuid_pk`

```python
uuid_pk = Annotated[UUID, mapped_column(primary_key=True, default=uuid4, server_default=(func.gen_random_uuid()))]
```

#### `leadr.common.repositories`

Base repository abstraction for common CRUD operations.

**Classes:**

- [**BaseRepository**](./common.md#leadr.common.repositories.BaseRepository) – Abstract base repository providing common CRUD operations.

**Attributes:**

- [**DomainEntityT**](./common.md#leadr.common.repositories.DomainEntityT) –
- [**ORMModelT**](./common.md#leadr.common.repositories.ORMModelT) –

##### `leadr.common.repositories.BaseRepository`

```python
BaseRepository(session)
```

Bases: <code>[ABC](#abc.ABC)</code>, <code>[Generic](#typing.Generic)\[[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT), [ORMModelT](./common.md#leadr.common.repositories.ORMModelT)\]</code>

Abstract base repository providing common CRUD operations.

All repositories should extend this class and implement the abstract methods
for converting between domain entities and ORM models.

All delete operations are soft deletes by default, setting deleted_at timestamp.

**Functions:**

- [**create**](./common.md#leadr.common.repositories.BaseRepository.create) – Create a new entity in the database.
- [**delete**](./common.md#leadr.common.repositories.BaseRepository.delete) – Soft delete an entity by setting its deleted_at timestamp.
- [**filter**](./common.md#leadr.common.repositories.BaseRepository.filter) – Filter entities based on criteria with pagination.
- [**get_by_id**](#leadr.common.repositories.BaseRepository.get_by_id) – Get an entity by its ID.
- [**update**](./common.md#leadr.common.repositories.BaseRepository.update) – Update an existing entity in the database.

**Attributes:**

- [**session**](./common.md#leadr.common.repositories.BaseRepository.session) –

**Parameters:**

- **session** (<code>[AsyncSession](#sqlalchemy.ext.asyncio.AsyncSession)</code>) – SQLAlchemy async session

###### `leadr.common.repositories.BaseRepository.create`

```python
create(entity)
```

Create a new entity in the database.

**Parameters:**

- **entity** (<code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code>) – Domain entity to create

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code> – Created domain entity with refreshed data

###### `leadr.common.repositories.BaseRepository.delete`

```python
delete(entity_id)
```

Soft delete an entity by setting its deleted_at timestamp.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – ID of entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

###### `leadr.common.repositories.BaseRepository.filter`

```python
filter(account_id=None, *, pagination, **kwargs)
```

Filter entities based on criteria with pagination.

All filter operations return paginated results. The pagination parameter
is required to enforce consistent API behavior across the codebase.

For multi-tenant entities, implementations should make account_id required
(no default). For top-level entities like Account, account_id can remain
optional and unused.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – Optional account ID for filtering. Multi-tenant entities
  should override to make this required.
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Required pagination parameters (cursor, limit, sort).
- \*\***kwargs** (<code>[Any](#typing.Any)</code>) – Additional filter parameters specific to the entity type.

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)\]</code> – PaginatedResult containing matching entities and pagination metadata.

###### `leadr.common.repositories.BaseRepository.get_by_id`

```python
get_by_id(entity_id, include_deleted=False)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – Entity ID to retrieve
- **include_deleted** (<code>[bool](#bool)</code>) – If True, include soft-deleted entities. Defaults to False.

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT) | None</code> – Domain entity if found, None otherwise

###### `leadr.common.repositories.BaseRepository.session`

```python
session = session
```

###### `leadr.common.repositories.BaseRepository.update`

```python
update(entity)
```

Update an existing entity in the database.

**Parameters:**

- **entity** (<code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code>) – Domain entity with updated data

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code> – Updated domain entity with refreshed data

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

##### `leadr.common.repositories.DomainEntityT`

```python
DomainEntityT = TypeVar('DomainEntityT', bound=Entity)
```

##### `leadr.common.repositories.ORMModelT`

```python
ORMModelT = TypeVar('ORMModelT', bound=Base)
```

#### `leadr.common.services`

Base service abstraction for common business logic patterns.

**Classes:**

- [**BaseService**](./common.md#leadr.common.services.BaseService) – Abstract base service providing common business logic patterns.

**Attributes:**

- [**DomainEntityT**](./common.md#leadr.common.services.DomainEntityT) –
- [**RepositoryT**](./common.md#leadr.common.services.RepositoryT) –

##### `leadr.common.services.BaseService`

```python
BaseService(session)
```

Bases: <code>[ABC](#abc.ABC)</code>, <code>[Generic](#typing.Generic)\[[DomainEntityT](./common.md#leadr.common.services.DomainEntityT), [RepositoryT](./common.md#leadr.common.services.RepositoryT)\]</code>

Abstract base service providing common business logic patterns.

All services should extend this class to ensure consistent patterns for:

- Repository initialization
- Standard CRUD operations
- Error handling with domain exceptions

The service layer sits between API routes and repositories, providing:

- Business logic orchestration
- Domain validation
- Transaction boundaries
- Consistent error handling

**Functions:**

- [**delete**](./common.md#leadr.common.services.BaseService.delete) – Soft-delete an entity.
- [**get_by_id**](#leadr.common.services.BaseService.get_by_id) – Get an entity by its ID.
- [**get_by_id_or_raise**](#leadr.common.services.BaseService.get_by_id_or_raise) – Get an entity by its ID or raise EntityNotFoundError.
- [**list_all**](#leadr.common.services.BaseService.list_all) – List all non-deleted entities.
- [**soft_delete**](#leadr.common.services.BaseService.soft_delete) – Soft-delete an entity and return it before deletion.

**Attributes:**

- [**repository**](./common.md#leadr.common.services.BaseService.repository) –

**Parameters:**

- **session** (<code>[AsyncSession](#sqlalchemy.ext.asyncio.AsyncSession)</code>) – SQLAlchemy async session for database operations

###### `leadr.common.services.BaseService.delete`

```python
delete(entity_id)
```

Soft-delete an entity.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – The ID of the entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the entity doesn't exist

###### `leadr.common.services.BaseService.get_by_id`

```python
get_by_id(entity_id)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – The ID of the entity to retrieve

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.services.DomainEntityT) | None</code> – The domain entity if found, None otherwise

###### `leadr.common.services.BaseService.get_by_id_or_raise`

```python
get_by_id_or_raise(entity_id)
```

Get an entity by its ID or raise EntityNotFoundError.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – The ID of the entity to retrieve

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.services.DomainEntityT)</code> – The domain entity

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the entity is not found
  (converted to HTTP 404 by global handler)

###### `leadr.common.services.BaseService.list_all`

```python
list_all()
```

List all non-deleted entities.

**Returns:**

- <code>[list](#list)\[[DomainEntityT](./common.md#leadr.common.services.DomainEntityT)\]</code> – List of domain entities

###### `leadr.common.services.BaseService.repository`

```python
repository = self._create_repository(session)
```

###### `leadr.common.services.BaseService.soft_delete`

```python
soft_delete(entity_id)
```

Soft-delete an entity and return it before deletion.

Useful for endpoints that need to return the deleted entity in the response.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – The ID of the entity to delete

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.services.DomainEntityT)</code> – The entity before it was deleted

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the entity doesn't exist

##### `leadr.common.services.DomainEntityT`

```python
DomainEntityT = TypeVar('DomainEntityT', bound=Entity)
```

##### `leadr.common.services.RepositoryT`

```python
RepositoryT = TypeVar('RepositoryT', bound=BaseRepository)
```

#### `leadr.common.utils`

Common utility functions.

**Modules:**

- [**ip**](./common.md#leadr.common.utils.ip) – IP address extraction utilities.
- [**slug**](./common.md#leadr.common.utils.slug) – Slug generation utilities.

##### `leadr.common.utils.ip`

IP address extraction utilities.

**Functions:**

- [**extract_client_ip**](#leadr.common.utils.ip.extract_client_ip) – Extract client IP address from request headers.

###### `leadr.common.utils.ip.extract_client_ip`

```python
extract_client_ip(request)
```

Extract client IP address from request headers.

Checks headers in priority order:

1. X-Real-IP - common proxy header
1. X-Forwarded-For - standard proxy header (uses leftmost IP)
1. CF-Connecting-IP - Cloudflare header
1. request.client.host - fallback to direct connection

**Parameters:**

- **request** (<code>[Request](#fastapi.Request)</code>) – The incoming FastAPI/Starlette request

**Returns:**

- <code>[str](#str) | None</code> – IP address string, or None if unable to extract

##### `leadr.common.utils.slug`

Slug generation utilities.

Provides utilities for generating URL-friendly slugs from text,
with support for collision handling and uniqueness constraints.

**Functions:**

- [**generate_slug**](#leadr.common.utils.slug.generate_slug) – Generate a URL-friendly slug from text.
- [**generate_unique_slug_with_retry**](#leadr.common.utils.slug.generate_unique_slug_with_retry) – Generate a unique slug with collision handling.

**Attributes:**

- [**T**](./common.md#leadr.common.utils.slug.T) –

###### `leadr.common.utils.slug.T`

```python
T = TypeVar('T')
```

###### `leadr.common.utils.slug.generate_slug`

```python
generate_slug(text, max_length=50)
```

Generate a URL-friendly slug from text.

Converts text to lowercase, replaces spaces with hyphens, removes special
characters, and handles unicode by transliterating accented characters.

**Parameters:**

- **text** (<code>[str](#str)</code>) – The text to convert to a slug
- **max_length** (<code>[int](#int)</code>) – Maximum length of the generated slug (default: 50)

**Returns:**

- <code>[str](#str)</code> – A lowercase slug with alphanumeric characters, hyphens, and underscores

**Raises:**

- <code>[ValueError](#ValueError)</code> – If text is empty or contains no valid characters after processing

**Examples:**

```pycon
>>> generate_slug("Hello World")
"hello-world"
>>> generate_slug("Café Board")
"cafe-board"
>>> generate_slug("Speed-Run 2024")
"speed-run-2024"
```

###### `leadr.common.utils.slug.generate_unique_slug_with_retry`

```python
generate_unique_slug_with_retry(base_text, check_exists, max_retries=10, max_length=50)
```

Generate a unique slug with collision handling.

Attempts to generate a unique slug from the base text. If a collision is
detected (slug already exists), appends a numeric suffix and retries.

**Parameters:**

- **base_text** (<code>[str](#str)</code>) – The text to convert to a slug
- **check_exists** (<code>[Callable](#collections.abc.Callable)\[\[[str](#str)\], [Awaitable](#collections.abc.Awaitable)\[[bool](#bool)\]\]</code>) – Async function that returns True if slug already exists
- **max_retries** (<code>[int](#int)</code>) – Maximum number of collision retries (default: 10)
- **max_length** (<code>[int](#int)</code>) – Maximum length of the generated slug (default: 50)

**Returns:**

- <code>[str](#str)</code> – A unique slug that doesn't collide with existing slugs

**Raises:**

- <code>[ValueError](#ValueError)</code> – If unable to generate unique slug after max_retries
- <code>[ValueError](#ValueError)</code> – If base_text is invalid for slug generation

**Examples:**

```pycon
>>> async def check(slug: str) -> bool:
...     return slug in ["my-board", "my-board-2"]
>>> await generate_unique_slug_with_retry("My Board", check)
"my-board-3"
```
