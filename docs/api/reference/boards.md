### `leadr.boards`

**Modules:**

- [**adapters**](./boards.md#leadr.boards.adapters) –
- [**api**](./boards.md#leadr.boards.api) –
- [**domain**](./boards.md#leadr.boards.domain) –
- [**services**](./boards.md#leadr.boards.services) –

#### `leadr.boards.adapters`

**Modules:**

- [**orm**](./boards.md#leadr.boards.adapters.orm) – Board ORM model.

##### `leadr.boards.adapters.orm`

Board ORM model.

**Classes:**

- [**BoardORM**](./boards.md#leadr.boards.adapters.orm.BoardORM) – Board ORM model.
- [**BoardTemplateORM**](./boards.md#leadr.boards.adapters.orm.BoardTemplateORM) – BoardTemplate ORM model.

###### `leadr.boards.adapters.orm.BoardORM`

Bases: <code>[Base](./common.md#leadr.common.orm.Base)</code>

Board ORM model.

Represents a leaderboard/board that belongs to a game in the database.
Maps to the boards table with foreign keys to accounts and games, a
unique constraint on short_code (globally unique for direct sharing),
and a partial unique constraint on (account_id, game_id, slug) for
active boards only.

**Attributes:**

- [**account**](./boards.md#leadr.boards.adapters.orm.BoardORM.account) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[AccountORM](./accounts.md#leadr.accounts.adapters.orm.AccountORM)\]</code>) –
- [**account_id**](#leadr.boards.adapters.orm.BoardORM.account_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**created_at**](#leadr.boards.adapters.orm.BoardORM.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**created_from_template_id**](#leadr.boards.adapters.orm.BoardORM.created_from_template_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID) | None\]</code>) –
- [**deleted_at**](#leadr.boards.adapters.orm.BoardORM.deleted_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[nullable_timestamp](#leadr.common.orm.nullable_timestamp)\]</code>) –
- [**description**](./boards.md#leadr.boards.adapters.orm.BoardORM.description) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**ends_at**](#leadr.boards.adapters.orm.BoardORM.ends_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime) | None\]</code>) –
- [**game**](./boards.md#leadr.boards.adapters.orm.BoardORM.game) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[GameORM](./games.md#leadr.games.adapters.orm.GameORM)\]</code>) –
- [**game_id**](#leadr.boards.adapters.orm.BoardORM.game_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**icon**](./boards.md#leadr.boards.adapters.orm.BoardORM.icon) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**id**](./boards.md#leadr.boards.adapters.orm.BoardORM.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**is_active**](#leadr.boards.adapters.orm.BoardORM.is_active) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[bool](#bool)\]</code>) –
- [**is_published**](#leadr.boards.adapters.orm.BoardORM.is_published) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[bool](#bool)\]</code>) –
- [**keep_strategy**](#leadr.boards.adapters.orm.BoardORM.keep_strategy) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**name**](./boards.md#leadr.boards.adapters.orm.BoardORM.name) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**short_code**](#leadr.boards.adapters.orm.BoardORM.short_code) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**slug**](./boards.md#leadr.boards.adapters.orm.BoardORM.slug) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**sort_direction**](#leadr.boards.adapters.orm.BoardORM.sort_direction) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**starts_at**](#leadr.boards.adapters.orm.BoardORM.starts_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime) | None\]</code>) –
- [**tags**](./boards.md#leadr.boards.adapters.orm.BoardORM.tags) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[list](#list)\[[str](#str)\]\]</code>) –
- [**template_name**](#leadr.boards.adapters.orm.BoardORM.template_name) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**unit**](./boards.md#leadr.boards.adapters.orm.BoardORM.unit) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**updated_at**](#leadr.boards.adapters.orm.BoardORM.updated_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –

####### `leadr.boards.adapters.orm.BoardORM.account`

```python
account: Mapped[AccountORM] = relationship('AccountORM')
```

####### `leadr.boards.adapters.orm.BoardORM.account_id`

```python
account_id: Mapped[UUID] = mapped_column(ForeignKey('accounts.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.boards.adapters.orm.BoardORM.created_at`

```python
created_at: Mapped[timestamp]
```

####### `leadr.boards.adapters.orm.BoardORM.created_from_template_id`

```python
created_from_template_id: Mapped[UUID | None] = mapped_column(nullable=True, default=None)
```

####### `leadr.boards.adapters.orm.BoardORM.deleted_at`

```python
deleted_at: Mapped[nullable_timestamp]
```

####### `leadr.boards.adapters.orm.BoardORM.description`

```python
description: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
```

####### `leadr.boards.adapters.orm.BoardORM.ends_at`

```python
ends_at: Mapped[datetime | None] = mapped_column(DateTime(timezone=True), nullable=True, default=None)
```

####### `leadr.boards.adapters.orm.BoardORM.game`

```python
game: Mapped[GameORM] = relationship('GameORM')
```

####### `leadr.boards.adapters.orm.BoardORM.game_id`

```python
game_id: Mapped[UUID] = mapped_column(ForeignKey('games.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.boards.adapters.orm.BoardORM.icon`

```python
icon: Mapped[str | None] = mapped_column(String, nullable=True)
```

####### `leadr.boards.adapters.orm.BoardORM.id`

```python
id: Mapped[uuid_pk]
```

####### `leadr.boards.adapters.orm.BoardORM.is_active`

```python
is_active: Mapped[bool] = mapped_column(Boolean, nullable=False)
```

####### `leadr.boards.adapters.orm.BoardORM.is_published`

```python
is_published: Mapped[bool] = mapped_column(Boolean, nullable=False, default=True, server_default=(sa.text('true')))
```

####### `leadr.boards.adapters.orm.BoardORM.keep_strategy`

```python
keep_strategy: Mapped[str] = mapped_column(String, nullable=False)
```

####### `leadr.boards.adapters.orm.BoardORM.name`

```python
name: Mapped[str] = mapped_column(String, nullable=False)
```

####### `leadr.boards.adapters.orm.BoardORM.short_code`

```python
short_code: Mapped[str] = mapped_column(String, nullable=False, unique=True, index=True)
```

####### `leadr.boards.adapters.orm.BoardORM.slug`

```python
slug: Mapped[str] = mapped_column(String, nullable=False, index=True)
```

####### `leadr.boards.adapters.orm.BoardORM.sort_direction`

```python
sort_direction: Mapped[str] = mapped_column(String, nullable=False)
```

####### `leadr.boards.adapters.orm.BoardORM.starts_at`

```python
starts_at: Mapped[datetime | None] = mapped_column(DateTime(timezone=True), nullable=True, default=None)
```

####### `leadr.boards.adapters.orm.BoardORM.tags`

```python
tags: Mapped[list[str]] = mapped_column(ARRAY(String), nullable=False, default=list, server_default='{}')
```

####### `leadr.boards.adapters.orm.BoardORM.template_name`

```python
template_name: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
```

####### `leadr.boards.adapters.orm.BoardORM.unit`

```python
unit: Mapped[str | None] = mapped_column(String, nullable=True)
```

####### `leadr.boards.adapters.orm.BoardORM.updated_at`

```python
updated_at: Mapped[timestamp] = mapped_column(onupdate=(func.now()))
```

###### `leadr.boards.adapters.orm.BoardTemplateORM`

Bases: <code>[Base](./common.md#leadr.common.orm.Base)</code>

BoardTemplate ORM model.

Represents a template for automatically generating boards at regular intervals.
Maps to the board_templates table with foreign keys to accounts and games.
Uses JSONB column for config to support flexible procedural generation configuration.

**Functions:**

- [**from_domain**](#leadr.boards.adapters.orm.BoardTemplateORM.from_domain) – Convert domain entity to ORM model.
- [**to_domain**](#leadr.boards.adapters.orm.BoardTemplateORM.to_domain) – Convert ORM model to domain entity.

**Attributes:**

- [**account**](./boards.md#leadr.boards.adapters.orm.BoardTemplateORM.account) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[AccountORM](./accounts.md#leadr.accounts.adapters.orm.AccountORM)\]</code>) –
- [**account_id**](#leadr.boards.adapters.orm.BoardTemplateORM.account_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**config**](./boards.md#leadr.boards.adapters.orm.BoardTemplateORM.config) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[dict](#dict)\[[str](#str), [Any](#typing.Any)\]\]</code>) –
- [**created_at**](#leadr.boards.adapters.orm.BoardTemplateORM.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**deleted_at**](#leadr.boards.adapters.orm.BoardTemplateORM.deleted_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[nullable_timestamp](#leadr.common.orm.nullable_timestamp)\]</code>) –
- [**ends_at**](#leadr.boards.adapters.orm.BoardTemplateORM.ends_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime) | None\]</code>) –
- [**game**](./boards.md#leadr.boards.adapters.orm.BoardTemplateORM.game) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[GameORM](./games.md#leadr.games.adapters.orm.GameORM)\]</code>) –
- [**game_id**](#leadr.boards.adapters.orm.BoardTemplateORM.game_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**icon**](./boards.md#leadr.boards.adapters.orm.BoardTemplateORM.icon) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**id**](./boards.md#leadr.boards.adapters.orm.BoardTemplateORM.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**is_active**](#leadr.boards.adapters.orm.BoardTemplateORM.is_active) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[bool](#bool)\]</code>) –
- [**is_published**](#leadr.boards.adapters.orm.BoardTemplateORM.is_published) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[bool](#bool)\]</code>) –
- [**keep_strategy**](#leadr.boards.adapters.orm.BoardTemplateORM.keep_strategy) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**name**](./boards.md#leadr.boards.adapters.orm.BoardTemplateORM.name) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**name_template**](#leadr.boards.adapters.orm.BoardTemplateORM.name_template) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**next_run_at**](#leadr.boards.adapters.orm.BoardTemplateORM.next_run_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime)\]</code>) –
- [**repeat_interval**](#leadr.boards.adapters.orm.BoardTemplateORM.repeat_interval) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**series**](./boards.md#leadr.boards.adapters.orm.BoardTemplateORM.series) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**slug**](./boards.md#leadr.boards.adapters.orm.BoardTemplateORM.slug) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**sort_direction**](#leadr.boards.adapters.orm.BoardTemplateORM.sort_direction) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**starts_at**](#leadr.boards.adapters.orm.BoardTemplateORM.starts_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime) | None\]</code>) –
- [**tags**](./boards.md#leadr.boards.adapters.orm.BoardTemplateORM.tags) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[list](#list)\[[str](#str)\]\]</code>) –
- [**unit**](./boards.md#leadr.boards.adapters.orm.BoardTemplateORM.unit) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**updated_at**](#leadr.boards.adapters.orm.BoardTemplateORM.updated_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –

####### `leadr.boards.adapters.orm.BoardTemplateORM.account`

```python
account: Mapped[AccountORM] = relationship('AccountORM')
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.account_id`

```python
account_id: Mapped[UUID] = mapped_column(ForeignKey('accounts.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.config`

```python
config: Mapped[dict[str, Any]] = mapped_column(JSONB, nullable=False, default=dict, server_default='{}')
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.created_at`

```python
created_at: Mapped[timestamp]
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.deleted_at`

```python
deleted_at: Mapped[nullable_timestamp]
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.ends_at`

```python
ends_at: Mapped[datetime | None] = mapped_column(DateTime(timezone=True), nullable=True, default=None)
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.from_domain`

```python
from_domain(entity)
```

Convert domain entity to ORM model.

**Parameters:**

- **entity** (<code>[BoardTemplate](#leadr.boards.domain.board_template.BoardTemplate)</code>) – The BoardTemplate domain entity to convert.

**Returns:**

- <code>[BoardTemplateORM](./boards.md#leadr.boards.adapters.orm.BoardTemplateORM)</code> – BoardTemplateORM model with all fields populated from domain entity.

####### `leadr.boards.adapters.orm.BoardTemplateORM.game`

```python
game: Mapped[GameORM] = relationship('GameORM')
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.game_id`

```python
game_id: Mapped[UUID] = mapped_column(ForeignKey('games.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.icon`

```python
icon: Mapped[str | None] = mapped_column(String, nullable=True)
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.id`

```python
id: Mapped[uuid_pk]
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.is_active`

```python
is_active: Mapped[bool] = mapped_column(Boolean, nullable=False)
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.is_published`

```python
is_published: Mapped[bool] = mapped_column(Boolean, nullable=False, default=True, server_default=(sa.text('true')))
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.keep_strategy`

```python
keep_strategy: Mapped[str] = mapped_column(String, nullable=False)
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.name`

```python
name: Mapped[str] = mapped_column(String, nullable=False)
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.name_template`

```python
name_template: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.next_run_at`

```python
next_run_at: Mapped[datetime] = mapped_column(DateTime(timezone=True), nullable=False)
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.repeat_interval`

```python
repeat_interval: Mapped[str] = mapped_column(String, nullable=False)
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.series`

```python
series: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.slug`

```python
slug: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.sort_direction`

```python
sort_direction: Mapped[str] = mapped_column(String, nullable=False)
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.starts_at`

```python
starts_at: Mapped[datetime | None] = mapped_column(DateTime(timezone=True), nullable=True, default=None)
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.tags`

```python
tags: Mapped[list[str]] = mapped_column(ARRAY(String), nullable=False, default=list, server_default='{}')
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.to_domain`

```python
to_domain()
```

Convert ORM model to domain entity.

**Returns:**

- <code>[BoardTemplate](#leadr.boards.domain.board_template.BoardTemplate)</code> – BoardTemplate domain entity with all fields populated from ORM model.

####### `leadr.boards.adapters.orm.BoardTemplateORM.unit`

```python
unit: Mapped[str | None] = mapped_column(String, nullable=True)
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.updated_at`

```python
updated_at: Mapped[timestamp] = mapped_column(onupdate=(func.now()))
```

#### `leadr.boards.api`

**Modules:**

- [**board_routes**](#leadr.boards.api.board_routes) – Board API routes.
- [**board_schemas**](#leadr.boards.api.board_schemas) – API request and response models for boards.
- [**board_template_routes**](#leadr.boards.api.board_template_routes) – Board template API routes.
- [**board_template_schemas**](#leadr.boards.api.board_template_schemas) – API request and response models for board templates.

##### `leadr.boards.api.board_routes`

Board API routes.

**Functions:**

- [**create_board**](#leadr.boards.api.board_routes.create_board) – Create a new board.
- [**get_board**](#leadr.boards.api.board_routes.get_board) – Get a board by ID.
- [**handle_list_boards**](#leadr.boards.api.board_routes.handle_list_boards) – Shared handler for listing boards with filtering.
- [**list_boards_admin**](#leadr.boards.api.board_routes.list_boards_admin) – List boards (Admin API).
- [**list_boards_client**](#leadr.boards.api.board_routes.list_boards_client) – List boards (Client API).
- [**update_board**](#leadr.boards.api.board_routes.update_board) – Update a board.

**Attributes:**

- [**client_router**](#leadr.boards.api.board_routes.client_router) –
- [**logger**](#leadr.boards.api.board_routes.logger) –
- [**router**](#leadr.boards.api.board_routes.router) –

###### `leadr.boards.api.board_routes.client_router`

```python
client_router = APIRouter()
```

###### `leadr.boards.api.board_routes.create_board`

```python
create_board(request, service, auth, background_tasks, pre_create_hook, post_create_hook)
```

Create a new board.

Creates a new leaderboard associated with an existing game and account.
The game must belong to the specified account.

For regular users, account_id must match their API key's account.
For superadmins, any account_id is accepted.

**Parameters:**

- **request** (<code>[BoardCreateRequest](#leadr.boards.api.board_schemas.BoardCreateRequest)</code>) – Board creation details including account_id, game_id, name, and settings.
- **service** (<code>[BoardServiceDep](./boards.md#leadr.boards.services.dependencies.BoardServiceDep)</code>) – Injected board service dependency.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.
- **pre_create_hook** (<code>[PreCreateBoardHookDep](./common.md#leadr.common.api.hooks.PreCreateBoardHookDep)</code>) – Hook called before board creation (for quota checks).
- **post_create_hook** (<code>[PostCreateBoardHookDep](./common.md#leadr.common.api.hooks.PostCreateBoardHookDep)</code>) – Hook called after successful board creation.

**Returns:**

- <code>[BoardResponse](#leadr.boards.api.board_schemas.BoardResponse)</code> – BoardResponse with the created board including auto-generated ID and timestamps.

**Raises:**

- <code>403</code> – User does not have access to the specified account.
- <code>404</code> – Game or account not found.
- <code>400</code> – Game doesn't belong to the specified account.

###### `leadr.boards.api.board_routes.get_board`

```python
get_board(board_id, service, auth)
```

Get a board by ID.

**Parameters:**

- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – Unique identifier for the board.
- **service** (<code>[BoardServiceDep](./boards.md#leadr.boards.services.dependencies.BoardServiceDep)</code>) – Injected board service dependency.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.

**Returns:**

- <code>[BoardResponse](#leadr.boards.api.board_schemas.BoardResponse)</code> – BoardResponse with full board details.

**Raises:**

- <code>403</code> – User does not have access to this board's account.
- <code>404</code> – Board not found.

###### `leadr.boards.api.board_routes.handle_list_boards`

```python
handle_list_boards(auth, service, game_service, pagination, account_id, game_id, code, game_slug, slug, is_active, is_published, starts_before, starts_after, ends_before, ends_after)
```

Shared handler for listing boards with filtering.

**Parameters:**

- **auth** (<code>[AuthContext](./auth.md#leadr.auth.dependencies.AuthContext)</code>) – Authentication context with user info.
- **service** (<code>[BoardService](#leadr.boards.services.board_service.BoardService)</code>) – Board service instance.
- **game_service** (<code>[GameService](#leadr.games.services.game_service.GameService)</code>) – Game service instance for game_slug resolution.
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (cursor, limit, sort).
- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – Optional account ID to filter boards by.
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID) | None</code>) – Optional game ID to filter boards by.
- **code** (<code>[str](#str) | None</code>) – Optional short code to filter boards by.
- **game_slug** (<code>[str](#str) | None</code>) – Optional game slug to filter boards by game (resolves to game_id).
- **slug** (<code>[str](#str) | None</code>) – Optional board slug to filter by specific board (requires game_slug).
- **is_active** (<code>[bool](#bool) | None</code>) – Optional filter for active status.
- **is_published** (<code>[bool](#bool) | None</code>) – Optional filter for published status.
- **starts_before** (<code>[datetime](#datetime.datetime) | None</code>) – Optional filter for boards starting before this time.
- **starts_after** (<code>[datetime](#datetime.datetime) | None</code>) – Optional filter for boards starting after this time.
- **ends_before** (<code>[datetime](#datetime.datetime) | None</code>) – Optional filter for boards ending before this time.
- **ends_after** (<code>[datetime](#datetime.datetime) | None</code>) – Optional filter for boards ending after this time.

**Returns:**

- <code>[PaginatedResponse](./common.md#leadr.common.api.pagination.PaginatedResponse)\[[BoardResponse](#leadr.boards.api.board_schemas.BoardResponse)\]</code> – PaginatedResponse with boards and pagination metadata.

**Raises:**

- <code>400</code> – Invalid cursor, sort field, or cursor state mismatch.
- <code>404</code> – Game or board not found when using slug filters.

###### `leadr.boards.api.board_routes.list_boards_admin`

```python
list_boards_admin(auth, service, game_service, pagination, account_id=None, game_id=None, code=None, game_slug=None, slug=None, is_active=None, is_published=None, starts_before=None, starts_after=None, ends_before=None, ends_after=None)
```

List boards (Admin API).

For regular users:

- If account_id not provided, defaults to their API key's account
- If account_id provided and they are superadmin, can access any account
- If account_id provided and NOT superadmin, must match their account (validated in AuthContext)

Filtering:

- Use ?game_id={id} or ?game_slug={slug} to filter boards by game
- Use ?game_slug={game_slug}&slug={slug} to find a specific board within a game
- Use ?code={code} to filter boards by short code
- Use ?is_active=true/false to filter by active status
- Use ?is_published=true/false to filter by published status
- Use ?starts_before=<datetime>&starts_after=<datetime> for start date range
- Use ?ends_before=<datetime>&ends_after=<datetime> for end date range
- Note: board slug filter requires game_slug parameter

Pagination:

- Default: 20 items per page, sorted by created_at:desc,id:asc
- Custom sort: Use ?sort=name:asc,created_at:desc
- Valid sort fields: id, name, slug, short_code, created_at, updated_at
- Navigation: Use next_cursor/prev_cursor from response

<details class="example" open markdown="1">
<summary>Example</summary>

GET /v1/boards?account_id=acc_123&limit=50&sort=name:asc
GET /v1/boards?game_slug=my-game&is_active=true
GET /v1/boards?game_slug=my-game&slug=weekly-challenge
GET /v1/boards?starts_after=2025-01-01T00:00:00Z&ends_before=2025-12-31T23:59:59Z

</details>

**Parameters:**

- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Admin authentication context with user info.
- **service** (<code>[BoardServiceDep](./boards.md#leadr.boards.services.dependencies.BoardServiceDep)</code>) – Injected board service dependency.
- **game_service** (<code>[GameServiceDep](./games.md#leadr.games.services.dependencies.GameServiceDep)</code>) – Injected game service dependency.
- **pagination** (<code>[Annotated](#typing.Annotated)\[[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams), [Depends](#fastapi.Depends)()\]</code>) – Pagination parameters (cursor, limit, sort).
- **account_id** (<code>[Annotated](#typing.Annotated)\[[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None, [Query](#fastapi.Query)(description='Filter by account ID')\]</code>) – Optional account ID to filter boards by.
- **game_id** (<code>[Annotated](#typing.Annotated)\[[GameID](./common.md#leadr.common.domain.ids.GameID) | None, [Query](#fastapi.Query)(description='Filter by game ID')\]</code>) – Optional game ID to filter boards by.
- **code** (<code>[Annotated](#typing.Annotated)\[[str](#str) | None, [Query](#fastapi.Query)(description='Filter by short code')\]</code>) – Optional short code to filter boards by.
- **game_slug** (<code>[Annotated](#typing.Annotated)\[[str](#str) | None, [Query](#fastapi.Query)(description='Filter by game slug')\]</code>) – Optional game slug to filter boards by game (resolves to game_id).
- **slug** (<code>[Annotated](#typing.Annotated)\[[str](#str) | None, [Query](#fastapi.Query)(description='Filter by board slug (requires game_slug)')\]</code>) – Optional board slug to filter by specific board (requires game_slug).
- **is_active** (<code>[Annotated](#typing.Annotated)\[[bool](#bool) | None, [Query](#fastapi.Query)(description='Filter by active status')\]</code>) – Optional filter for active status.
- **is_published** (<code>[Annotated](#typing.Annotated)\[[bool](#bool) | None, [Query](#fastapi.Query)(description='Filter by published status')\]</code>) – Optional filter for published status.
- **starts_before** (<code>[Annotated](#typing.Annotated)\[[datetime](#datetime.datetime) | None, [Query](#fastapi.Query)(description='Filter boards starting before this time (ISO 8601)')\]</code>) – Optional filter for boards starting before this time.
- **starts_after** (<code>[Annotated](#typing.Annotated)\[[datetime](#datetime.datetime) | None, [Query](#fastapi.Query)(description='Filter boards starting after this time (ISO 8601)')\]</code>) – Optional filter for boards starting after this time.
- **ends_before** (<code>[Annotated](#typing.Annotated)\[[datetime](#datetime.datetime) | None, [Query](#fastapi.Query)(description='Filter boards ending before this time (ISO 8601)')\]</code>) – Optional filter for boards ending before this time.
- **ends_after** (<code>[Annotated](#typing.Annotated)\[[datetime](#datetime.datetime) | None, [Query](#fastapi.Query)(description='Filter boards ending after this time (ISO 8601)')\]</code>) – Optional filter for boards ending after this time.

**Returns:**

- <code>[PaginatedResponse](./common.md#leadr.common.api.pagination.PaginatedResponse)\[[BoardResponse](#leadr.boards.api.board_schemas.BoardResponse)\]</code> – PaginatedResponse with boards and pagination metadata.

**Raises:**

- <code>400</code> – Invalid cursor, sort field, cursor state mismatch, or slug without game_slug.
- <code>404</code> – Game or board not found when using slug filters.

###### `leadr.boards.api.board_routes.list_boards_client`

```python
list_boards_client(auth, service, game_service, pagination, game_id=None, code=None, game_slug=None, slug=None, is_published=None, starts_before=None, starts_after=None, ends_before=None, ends_after=None)
```

List boards (Client API).

Account ID is automatically derived from the authenticated device's account.
Clients can optionally filter by various criteria to find specific boards.

Filtering:

- Use ?game_id={id} or ?game_slug={slug} to filter boards by game
- Use ?game_slug={game_slug}&slug={slug} to find a specific board within a game
- Use ?code={code} to filter boards by short code
- Use ?is_published=true/false to filter by published status
- Use ?starts_before=<datetime>&starts_after=<datetime> for start date range
- Use ?ends_before=<datetime>&ends_after=<datetime> for end date range
- Note: board slug filter requires game_slug parameter

Pagination:

- Default: 20 items per page, sorted by created_at:desc,id:asc
- Custom sort: Use ?sort=name:asc,created_at:desc
- Valid sort fields: id, name, slug, short_code, created_at, updated_at
- Navigation: Use next_cursor/prev_cursor from response

<details class="example" open markdown="1">
<summary>Example</summary>

GET /v1/client/boards?code=WEEKLY-CHALLENGE&limit=50
GET /v1/client/boards?game_slug=my-game&is_published=true
GET /v1/client/boards?game_slug=my-game&slug=weekly-challenge
GET /v1/client/boards?starts_after=2025-01-01T00:00:00Z

</details>

**Parameters:**

- **auth** (<code>[ClientAuthContextDep](./auth.md#leadr.auth.dependencies.ClientAuthContextDep)</code>) – Client authentication context with device info.
- **service** (<code>[BoardServiceDep](./boards.md#leadr.boards.services.dependencies.BoardServiceDep)</code>) – Injected board service dependency.
- **game_service** (<code>[GameServiceDep](./games.md#leadr.games.services.dependencies.GameServiceDep)</code>) – Injected game service dependency.
- **pagination** (<code>[Annotated](#typing.Annotated)\[[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams), [Depends](#fastapi.Depends)()\]</code>) – Pagination parameters (cursor, limit, sort).
- **game_id** (<code>[Annotated](#typing.Annotated)\[[GameID](./common.md#leadr.common.domain.ids.GameID) | None, [Query](#fastapi.Query)(description='Filter by game ID')\]</code>) – Optional game ID to filter boards by.
- **code** (<code>[Annotated](#typing.Annotated)\[[str](#str) | None, [Query](#fastapi.Query)(description='Filter by short code')\]</code>) – Optional short code to filter boards by.
- **game_slug** (<code>[Annotated](#typing.Annotated)\[[str](#str) | None, [Query](#fastapi.Query)(description='Filter by game slug')\]</code>) – Optional game slug to filter boards by game (resolves to game_id).
- **slug** (<code>[Annotated](#typing.Annotated)\[[str](#str) | None, [Query](#fastapi.Query)(description='Filter by board slug (requires game_slug)')\]</code>) – Optional board slug to filter by specific board (requires game_slug).
- **is_published** (<code>[Annotated](#typing.Annotated)\[[bool](#bool) | None, [Query](#fastapi.Query)(description='Filter by published status')\]</code>) – Optional filter for published status.
- **starts_before** (<code>[Annotated](#typing.Annotated)\[[datetime](#datetime.datetime) | None, [Query](#fastapi.Query)(description='Filter boards starting before this time (ISO 8601)')\]</code>) – Optional filter for boards starting before this time.
- **starts_after** (<code>[Annotated](#typing.Annotated)\[[datetime](#datetime.datetime) | None, [Query](#fastapi.Query)(description='Filter boards starting after this time (ISO 8601)')\]</code>) – Optional filter for boards starting after this time.
- **ends_before** (<code>[Annotated](#typing.Annotated)\[[datetime](#datetime.datetime) | None, [Query](#fastapi.Query)(description='Filter boards ending before this time (ISO 8601)')\]</code>) – Optional filter for boards ending before this time.
- **ends_after** (<code>[Annotated](#typing.Annotated)\[[datetime](#datetime.datetime) | None, [Query](#fastapi.Query)(description='Filter boards ending after this time (ISO 8601)')\]</code>) – Optional filter for boards ending after this time.

**Returns:**

- <code>[PaginatedResponse](./common.md#leadr.common.api.pagination.PaginatedResponse)\[[BoardResponse](#leadr.boards.api.board_schemas.BoardResponse)\]</code> – PaginatedResponse with boards and pagination metadata.

**Raises:**

- <code>400</code> – Invalid cursor, sort field, cursor state mismatch, or slug without game_slug.
- <code>404</code> – Game or board not found when using slug filters.

###### `leadr.boards.api.board_routes.logger`

```python
logger = logging.getLogger(__name__)
```

###### `leadr.boards.api.board_routes.router`

```python
router = APIRouter()
```

###### `leadr.boards.api.board_routes.update_board`

```python
update_board(board_id, request, service, auth)
```

Update a board.

Supports updating any board field or soft-deleting the board.

**Parameters:**

- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – Unique identifier for the board.
- **request** (<code>[BoardUpdateRequest](#leadr.boards.api.board_schemas.BoardUpdateRequest)</code>) – Board update details (all fields optional).
- **service** (<code>[BoardServiceDep](./boards.md#leadr.boards.services.dependencies.BoardServiceDep)</code>) – Injected board service dependency.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.

**Returns:**

- <code>[BoardResponse](#leadr.boards.api.board_schemas.BoardResponse)</code> – BoardResponse with the updated board details.

**Raises:**

- <code>403</code> – User does not have access to this board's account.
- <code>404</code> – Board not found.

##### `leadr.boards.api.board_schemas`

API request and response models for boards.

**Classes:**

- [**BoardCreateRequest**](#leadr.boards.api.board_schemas.BoardCreateRequest) – Request model for creating a board.
- [**BoardResponse**](#leadr.boards.api.board_schemas.BoardResponse) – Response model for a board.
- [**BoardUpdateRequest**](#leadr.boards.api.board_schemas.BoardUpdateRequest) – Request model for updating a board.

###### `leadr.boards.api.board_schemas.BoardCreateRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request model for creating a board.

**Attributes:**

- [**account_id**](#leadr.boards.api.board_schemas.BoardCreateRequest.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**created_from_template_id**](#leadr.boards.api.board_schemas.BoardCreateRequest.created_from_template_id) (<code>[BoardTemplateID](./common.md#leadr.common.domain.ids.BoardTemplateID) | None</code>) –
- [**description**](#leadr.boards.api.board_schemas.BoardCreateRequest.description) (<code>[str](#str) | None</code>) –
- [**ends_at**](#leadr.boards.api.board_schemas.BoardCreateRequest.ends_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**game_id**](#leadr.boards.api.board_schemas.BoardCreateRequest.game_id) (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) –
- [**icon**](#leadr.boards.api.board_schemas.BoardCreateRequest.icon) (<code>[str](#str) | None</code>) –
- [**is_active**](#leadr.boards.api.board_schemas.BoardCreateRequest.is_active) (<code>[bool](#bool)</code>) –
- [**is_published**](#leadr.boards.api.board_schemas.BoardCreateRequest.is_published) (<code>[bool](#bool)</code>) –
- [**keep_strategy**](#leadr.boards.api.board_schemas.BoardCreateRequest.keep_strategy) (<code>[KeepStrategy](./boards.md#leadr.boards.domain.board.KeepStrategy)</code>) –
- [**name**](#leadr.boards.api.board_schemas.BoardCreateRequest.name) (<code>[str](#str)</code>) –
- [**short_code**](#leadr.boards.api.board_schemas.BoardCreateRequest.short_code) (<code>[str](#str) | None</code>) –
- [**slug**](#leadr.boards.api.board_schemas.BoardCreateRequest.slug) (<code>[str](#str) | None</code>) –
- [**sort_direction**](#leadr.boards.api.board_schemas.BoardCreateRequest.sort_direction) (<code>[SortDirection](./boards.md#leadr.boards.domain.board.SortDirection)</code>) –
- [**starts_at**](#leadr.boards.api.board_schemas.BoardCreateRequest.starts_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**tags**](#leadr.boards.api.board_schemas.BoardCreateRequest.tags) (<code>[list](#list)\[[str](#str)\] | None</code>) –
- [**template_name**](#leadr.boards.api.board_schemas.BoardCreateRequest.template_name) (<code>[str](#str) | None</code>) –
- [**unit**](#leadr.boards.api.board_schemas.BoardCreateRequest.unit) (<code>[str](#str) | None</code>) –

####### `leadr.boards.api.board_schemas.BoardCreateRequest.account_id`

```python
account_id: AccountID = Field(description='ID of the account this board belongs to')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.created_from_template_id`

```python
created_from_template_id: BoardTemplateID | None = Field(default=None, description='Optional template ID this board was created from')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.description`

```python
description: str | None = Field(default=None, description='Optional short description of the board')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.ends_at`

```python
ends_at: datetime | None = Field(default=None, description='Optional end time for time-bounded boards (UTC)')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.game_id`

```python
game_id: GameID = Field(description='ID of the game this board belongs to')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.icon`

```python
icon: str | None = Field(default='fa-crown', description="Icon identifier for the board. Defaults to 'fa-crown'")
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.is_active`

```python
is_active: bool = Field(default=True, description='Whether the board is currently active')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.is_published`

```python
is_published: bool = Field(default=True, description='Whether the board is published and visible on public web views')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.keep_strategy`

```python
keep_strategy: KeepStrategy = Field(default=(KeepStrategy.ALL), description='Strategy for keeping multiple scores from the same user')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.name`

```python
name: str = Field(description='Name of the board')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.short_code`

```python
short_code: str | None = Field(default=None, description='Globally unique short code for direct sharing. Auto-generated if not provided')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.slug`

```python
slug: str | None = Field(default=None, description='Optional URL-friendly slug. If not provided, will be auto-generated from name')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.sort_direction`

```python
sort_direction: SortDirection = Field(default=(SortDirection.DESCENDING), description='Direction to sort scores')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.starts_at`

```python
starts_at: datetime | None = Field(default=None, description='Optional start time for time-bounded boards (UTC)')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.tags`

```python
tags: list[str] | None = Field(default=None, description='Optional list of tags for categorization')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.template_name`

```python
template_name: str | None = Field(default=None, description='Optional template name this board was created from')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.unit`

```python
unit: str | None = Field(default=None, description="Unit of measurement for scores (e.g., 'seconds', 'points'). Optional")
```

###### `leadr.boards.api.board_schemas.BoardResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response model for a board.

**Functions:**

- [**from_domain**](#leadr.boards.api.board_schemas.BoardResponse.from_domain) – Convert domain entity to response model.

**Attributes:**

- [**account_id**](#leadr.boards.api.board_schemas.BoardResponse.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**created_at**](#leadr.boards.api.board_schemas.BoardResponse.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**created_from_template_id**](#leadr.boards.api.board_schemas.BoardResponse.created_from_template_id) (<code>[BoardTemplateID](./common.md#leadr.common.domain.ids.BoardTemplateID) | None</code>) –
- [**description**](#leadr.boards.api.board_schemas.BoardResponse.description) (<code>[str](#str) | None</code>) –
- [**ends_at**](#leadr.boards.api.board_schemas.BoardResponse.ends_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**game_id**](#leadr.boards.api.board_schemas.BoardResponse.game_id) (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) –
- [**icon**](#leadr.boards.api.board_schemas.BoardResponse.icon) (<code>[str](#str) | None</code>) –
- [**id**](#leadr.boards.api.board_schemas.BoardResponse.id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) –
- [**is_active**](#leadr.boards.api.board_schemas.BoardResponse.is_active) (<code>[bool](#bool)</code>) –
- [**is_published**](#leadr.boards.api.board_schemas.BoardResponse.is_published) (<code>[bool](#bool)</code>) –
- [**keep_strategy**](#leadr.boards.api.board_schemas.BoardResponse.keep_strategy) (<code>[KeepStrategy](./boards.md#leadr.boards.domain.board.KeepStrategy)</code>) –
- [**name**](#leadr.boards.api.board_schemas.BoardResponse.name) (<code>[str](#str)</code>) –
- [**short_code**](#leadr.boards.api.board_schemas.BoardResponse.short_code) (<code>[str](#str)</code>) –
- [**slug**](#leadr.boards.api.board_schemas.BoardResponse.slug) (<code>[str](#str)</code>) –
- [**sort_direction**](#leadr.boards.api.board_schemas.BoardResponse.sort_direction) (<code>[SortDirection](./boards.md#leadr.boards.domain.board.SortDirection)</code>) –
- [**starts_at**](#leadr.boards.api.board_schemas.BoardResponse.starts_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**tags**](#leadr.boards.api.board_schemas.BoardResponse.tags) (<code>[list](#list)\[[str](#str)\]</code>) –
- [**template_name**](#leadr.boards.api.board_schemas.BoardResponse.template_name) (<code>[str](#str) | None</code>) –
- [**unit**](#leadr.boards.api.board_schemas.BoardResponse.unit) (<code>[str](#str) | None</code>) –
- [**updated_at**](#leadr.boards.api.board_schemas.BoardResponse.updated_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**url_short**](#leadr.boards.api.board_schemas.BoardResponse.url_short) (<code>[str](#str) | None</code>) – Short URL for direct board access via short_code.

####### `leadr.boards.api.board_schemas.BoardResponse.account_id`

```python
account_id: AccountID = Field(description='ID of the account this board belongs to')
```

####### `leadr.boards.api.board_schemas.BoardResponse.created_at`

```python
created_at: datetime = Field(description='Timestamp when the board was created (UTC)')
```

####### `leadr.boards.api.board_schemas.BoardResponse.created_from_template_id`

```python
created_from_template_id: BoardTemplateID | None = Field(default=None, description='Template ID this board was created from, or null')
```

####### `leadr.boards.api.board_schemas.BoardResponse.description`

```python
description: str | None = Field(default=None, description='Short description of the board')
```

####### `leadr.boards.api.board_schemas.BoardResponse.ends_at`

```python
ends_at: datetime | None = Field(default=None, description='End time for time-bounded boards (UTC)')
```

####### `leadr.boards.api.board_schemas.BoardResponse.from_domain`

```python
from_domain(board)
```

Convert domain entity to response model.

**Parameters:**

- **board** (<code>[Board](./boards.md#leadr.boards.domain.board.Board)</code>) – The domain Board entity to convert.

**Returns:**

- <code>[BoardResponse](#leadr.boards.api.board_schemas.BoardResponse)</code> – BoardResponse with all fields populated from the domain entity.

####### `leadr.boards.api.board_schemas.BoardResponse.game_id`

```python
game_id: GameID = Field(description='ID of the game this board belongs to')
```

####### `leadr.boards.api.board_schemas.BoardResponse.icon`

```python
icon: str | None = Field(description='Icon identifier for the board, or null')
```

####### `leadr.boards.api.board_schemas.BoardResponse.id`

```python
id: BoardID = Field(description='Unique identifier for the board')
```

####### `leadr.boards.api.board_schemas.BoardResponse.is_active`

```python
is_active: bool = Field(description='Whether the board is currently active')
```

####### `leadr.boards.api.board_schemas.BoardResponse.is_published`

```python
is_published: bool = Field(description='Whether the board is published and visible on public web views')
```

####### `leadr.boards.api.board_schemas.BoardResponse.keep_strategy`

```python
keep_strategy: KeepStrategy = Field(description='Strategy for keeping scores from same user')
```

####### `leadr.boards.api.board_schemas.BoardResponse.name`

```python
name: str = Field(description='Name of the board')
```

####### `leadr.boards.api.board_schemas.BoardResponse.short_code`

```python
short_code: str = Field(description='Globally unique short code for direct sharing')
```

####### `leadr.boards.api.board_schemas.BoardResponse.slug`

```python
slug: str = Field(description='URL-friendly slug for the board (auto-generated, read-only)')
```

####### `leadr.boards.api.board_schemas.BoardResponse.sort_direction`

```python
sort_direction: SortDirection = Field(description='Direction to sort scores')
```

####### `leadr.boards.api.board_schemas.BoardResponse.starts_at`

```python
starts_at: datetime | None = Field(default=None, description='Start time for time-bounded boards (UTC)')
```

####### `leadr.boards.api.board_schemas.BoardResponse.tags`

```python
tags: list[str] = Field(default_factory=list, description='List of tags for categorization')
```

####### `leadr.boards.api.board_schemas.BoardResponse.template_name`

```python
template_name: str | None = Field(default=None, description='Template name this board was created from, or null')
```

####### `leadr.boards.api.board_schemas.BoardResponse.unit`

```python
unit: str | None = Field(description='Unit of measurement for scores, or null')
```

####### `leadr.boards.api.board_schemas.BoardResponse.updated_at`

```python
updated_at: datetime = Field(description='Timestamp of last update (UTC)')
```

####### `leadr.boards.api.board_schemas.BoardResponse.url_short`

```python
url_short: str | None
```

Short URL for direct board access via short_code.

Returns the URL if BOARDS_UI_DOMAIN is configured and the board is published,
otherwise None.

###### `leadr.boards.api.board_schemas.BoardUpdateRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request model for updating a board.

**Attributes:**

- [**created_from_template_id**](#leadr.boards.api.board_schemas.BoardUpdateRequest.created_from_template_id) (<code>[BoardTemplateID](./common.md#leadr.common.domain.ids.BoardTemplateID) | None</code>) –
- [**deleted**](#leadr.boards.api.board_schemas.BoardUpdateRequest.deleted) (<code>[bool](#bool) | None</code>) –
- [**description**](#leadr.boards.api.board_schemas.BoardUpdateRequest.description) (<code>[str](#str) | None</code>) –
- [**ends_at**](#leadr.boards.api.board_schemas.BoardUpdateRequest.ends_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**icon**](#leadr.boards.api.board_schemas.BoardUpdateRequest.icon) (<code>[str](#str) | None</code>) –
- [**is_active**](#leadr.boards.api.board_schemas.BoardUpdateRequest.is_active) (<code>[bool](#bool) | None</code>) –
- [**is_published**](#leadr.boards.api.board_schemas.BoardUpdateRequest.is_published) (<code>[bool](#bool) | None</code>) –
- [**keep_strategy**](#leadr.boards.api.board_schemas.BoardUpdateRequest.keep_strategy) (<code>[KeepStrategy](./boards.md#leadr.boards.domain.board.KeepStrategy) | None</code>) –
- [**name**](#leadr.boards.api.board_schemas.BoardUpdateRequest.name) (<code>[str](#str) | None</code>) –
- [**short_code**](#leadr.boards.api.board_schemas.BoardUpdateRequest.short_code) (<code>[str](#str) | None</code>) –
- [**sort_direction**](#leadr.boards.api.board_schemas.BoardUpdateRequest.sort_direction) (<code>[SortDirection](./boards.md#leadr.boards.domain.board.SortDirection) | None</code>) –
- [**starts_at**](#leadr.boards.api.board_schemas.BoardUpdateRequest.starts_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**tags**](#leadr.boards.api.board_schemas.BoardUpdateRequest.tags) (<code>[list](#list)\[[str](#str)\] | None</code>) –
- [**template_name**](#leadr.boards.api.board_schemas.BoardUpdateRequest.template_name) (<code>[str](#str) | None</code>) –
- [**unit**](#leadr.boards.api.board_schemas.BoardUpdateRequest.unit) (<code>[str](#str) | None</code>) –

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.created_from_template_id`

```python
created_from_template_id: BoardTemplateID | None = Field(default=None, description='Updated template ID')
```

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.deleted`

```python
deleted: bool | None = Field(default=None, description='Set to true to soft delete the board')
```

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.description`

```python
description: str | None = Field(default=None, description='Updated board description')
```

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.ends_at`

```python
ends_at: datetime | None = Field(default=None, description='Updated end time')
```

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.icon`

```python
icon: str | None = Field(default=None, description='Updated icon identifier')
```

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.is_active`

```python
is_active: bool | None = Field(default=None, description='Updated active status')
```

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.is_published`

```python
is_published: bool | None = Field(default=None, description='Updated published status')
```

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.keep_strategy`

```python
keep_strategy: KeepStrategy | None = Field(default=None, description='Updated keep strategy')
```

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.name`

```python
name: str | None = Field(default=None, description='Updated board name')
```

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.short_code`

```python
short_code: str | None = Field(default=None, description='Updated short code')
```

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.sort_direction`

```python
sort_direction: SortDirection | None = Field(default=None, description='Updated sort direction')
```

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.starts_at`

```python
starts_at: datetime | None = Field(default=None, description='Updated start time')
```

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.tags`

```python
tags: list[str] | None = Field(default=None, description='Updated tags list')
```

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.template_name`

```python
template_name: str | None = Field(default=None, description='Updated template name')
```

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.unit`

```python
unit: str | None = Field(default=None, description='Updated unit of measurement')
```

##### `leadr.boards.api.board_template_routes`

Board template API routes.

**Functions:**

- [**create_board_template**](#leadr.boards.api.board_template_routes.create_board_template) – Create a new board template.
- [**get_board_template**](#leadr.boards.api.board_template_routes.get_board_template) – Get a board template by ID.
- [**list_board_templates**](#leadr.boards.api.board_template_routes.list_board_templates) – List board templates for an account with pagination, optionally filtered by game.
- [**update_board_template**](#leadr.boards.api.board_template_routes.update_board_template) – Update a board template.

**Attributes:**

- [**router**](#leadr.boards.api.board_template_routes.router) –

###### `leadr.boards.api.board_template_routes.create_board_template`

```python
create_board_template(request, service, auth)
```

Create a new board template.

Creates a template for automatically generating boards at regular intervals.
The game must belong to the specified account.

For regular users, account_id must match their API key's account.
For superadmins, any account_id is accepted.

**Parameters:**

- **request** (<code>[BoardTemplateCreateRequest](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest)</code>) – Template creation details including repeat_interval and configuration.
- **service** (<code>[BoardTemplateServiceDep](./boards.md#leadr.boards.services.dependencies.BoardTemplateServiceDep)</code>) – Injected board template service dependency.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.

**Returns:**

- <code>[BoardTemplateResponse](#leadr.boards.api.board_template_schemas.BoardTemplateResponse)</code> – BoardTemplateResponse with the created template including auto-generated ID.

**Raises:**

- <code>403</code> – User does not have access to the specified account.
- <code>404</code> – Game or account not found.
- <code>400</code> – Game doesn't belong to the specified account.

###### `leadr.boards.api.board_template_routes.get_board_template`

```python
get_board_template(template_id, service, auth)
```

Get a board template by ID.

**Parameters:**

- **template_id** (<code>[BoardTemplateID](./common.md#leadr.common.domain.ids.BoardTemplateID)</code>) – Unique identifier for the template.
- **service** (<code>[BoardTemplateServiceDep](./boards.md#leadr.boards.services.dependencies.BoardTemplateServiceDep)</code>) – Injected board template service dependency.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.

**Returns:**

- <code>[BoardTemplateResponse](#leadr.boards.api.board_template_schemas.BoardTemplateResponse)</code> – BoardTemplateResponse with full template details.

**Raises:**

- <code>403</code> – User does not have access to this template's account.
- <code>404</code> – Template not found.

###### `leadr.boards.api.board_template_routes.list_board_templates`

```python
list_board_templates(auth, service, pagination, account_id=None, game_id=None)
```

List board templates for an account with pagination, optionally filtered by game.

For regular users, account_id is automatically derived from their API key.
For superadmins, account_id is optional - if omitted, returns templates from all accounts.

Pagination:

- Default: 20 items per page, sorted by created_at:desc,id:asc
- Custom sort: Use ?sort=name:asc,created_at:desc
- Valid sort fields: id, name, created_at, updated_at
- Navigation: Use next_cursor/prev_cursor from response

<details class="example" open markdown="1">
<summary>Example</summary>

GET /v1/board-templates?account_id=acc_123&game_id=gam_456&limit=50&sort=name:asc

</details>

**Parameters:**

- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.
- **service** (<code>[BoardTemplateServiceDep](./boards.md#leadr.boards.services.dependencies.BoardTemplateServiceDep)</code>) – Injected board template service dependency.
- **pagination** (<code>[Annotated](#typing.Annotated)\[[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams), [Depends](#fastapi.Depends)()\]</code>) – Pagination parameters (cursor, limit, sort).
- **account_id** (<code>[Annotated](#typing.Annotated)\[[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None, [Query](#fastapi.Query)(description='Account ID filter')\]</code>) – Optional account_id query parameter (superadmins can omit to see all).
- **game_id** (<code>[Annotated](#typing.Annotated)\[[GameID](./common.md#leadr.common.domain.ids.GameID) | None, [Query](#fastapi.Query)(description='Filter by game ID')\]</code>) – Optional game ID to filter templates by.

**Returns:**

- <code>[PaginatedResponse](./common.md#leadr.common.api.pagination.PaginatedResponse)\[[BoardTemplateResponse](#leadr.boards.api.board_template_schemas.BoardTemplateResponse)\]</code> – PaginatedResponse with board templates and pagination metadata.

**Raises:**

- <code>400</code> – Invalid cursor, sort field, or cursor state mismatch.
- <code>403</code> – User does not have access to the specified account.

###### `leadr.boards.api.board_template_routes.router`

```python
router = APIRouter()
```

###### `leadr.boards.api.board_template_routes.update_board_template`

```python
update_board_template(template_id, request, service, auth)
```

Update a board template.

Supports updating any template field or soft-deleting the template.

**Parameters:**

- **template_id** (<code>[BoardTemplateID](./common.md#leadr.common.domain.ids.BoardTemplateID)</code>) – Unique identifier for the template.
- **request** (<code>[BoardTemplateUpdateRequest](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest)</code>) – Template update details (all fields optional).
- **service** (<code>[BoardTemplateServiceDep](./boards.md#leadr.boards.services.dependencies.BoardTemplateServiceDep)</code>) – Injected board template service dependency.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.

**Returns:**

- <code>[BoardTemplateResponse](#leadr.boards.api.board_template_schemas.BoardTemplateResponse)</code> – BoardTemplateResponse with the updated template details.

**Raises:**

- <code>403</code> – User does not have access to this template's account.
- <code>404</code> – Template not found.

##### `leadr.boards.api.board_template_schemas`

API request and response models for board templates.

**Classes:**

- [**BoardTemplateCreateRequest**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest) – Request model for creating a board template.
- [**BoardTemplateResponse**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse) – Response model for a board template.
- [**BoardTemplateUpdateRequest**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest) – Request model for updating a board template.

###### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request model for creating a board template.

**Attributes:**

- [**account_id**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**config**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.config) (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\] | None</code>) –
- [**ends_at**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.ends_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**game_id**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.game_id) (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) –
- [**icon**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.icon) (<code>[str](#str) | None</code>) –
- [**is_active**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.is_active) (<code>[bool](#bool)</code>) –
- [**is_published**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.is_published) (<code>[bool](#bool)</code>) –
- [**keep_strategy**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.keep_strategy) (<code>[KeepStrategy](./boards.md#leadr.boards.domain.board.KeepStrategy)</code>) –
- [**name**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.name) (<code>[str](#str)</code>) –
- [**name_template**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.name_template) (<code>[str](#str) | None</code>) –
- [**next_run_at**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.next_run_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**repeat_interval**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.repeat_interval) (<code>[str](#str)</code>) –
- [**series**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.series) (<code>[str](#str) | None</code>) –
- [**slug**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.slug) (<code>[str](#str) | None</code>) –
- [**sort_direction**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.sort_direction) (<code>[SortDirection](./boards.md#leadr.boards.domain.board.SortDirection)</code>) –
- [**starts_at**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.starts_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**tags**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.tags) (<code>[list](#list)\[[str](#str)\] | None</code>) –
- [**unit**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.unit) (<code>[str](#str) | None</code>) –

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.account_id`

```python
account_id: AccountID = Field(description='ID of the account this template belongs to')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.config`

```python
config: dict[str, Any] | None = Field(default=None, description='Reserved for future procedural generation (bounds, variables, randomization rules)')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.ends_at`

```python
ends_at: datetime | None = Field(default=None, description='Optional end time for time-bounded boards')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.game_id`

```python
game_id: GameID = Field(description='ID of the game this template belongs to')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.icon`

```python
icon: str | None = Field(default='fa-crown', description='Icon identifier for boards created from this template')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.is_active`

```python
is_active: bool = Field(description='Whether the template is currently active')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.is_published`

```python
is_published: bool = Field(default=True, description='Whether boards created from this template should be published')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.keep_strategy`

```python
keep_strategy: KeepStrategy = Field(default=(KeepStrategy.ALL), description='Strategy for keeping multiple scores from the same user')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.name`

```python
name: str = Field(description='Name of the template')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.name_template`

```python
name_template: str | None = Field(default=None, description='Optional template string for generating board names')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.next_run_at`

```python
next_run_at: datetime = Field(description='Next scheduled time to create a board from this template (UTC)')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.repeat_interval`

```python
repeat_interval: str = Field(description="PostgreSQL interval syntax for repeat frequency (e.g., '7 days', '1 month')")
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.series`

```python
series: str | None = Field(default=None, description='Optional series identifier for sequential board naming')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.slug`

```python
slug: str | None = Field(default=None, description='URL-friendly slug for boards created from this template')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.sort_direction`

```python
sort_direction: SortDirection = Field(default=(SortDirection.DESCENDING), description='Direction to sort scores (ascending/descending)')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.starts_at`

```python
starts_at: datetime | None = Field(default=None, description='Optional start time for time-bounded boards')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.tags`

```python
tags: list[str] | None = Field(default=None, description='List of tags for categorizing boards created from this template')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.unit`

```python
unit: str | None = Field(default=None, description="Unit of measurement for scores (e.g., 'seconds', 'points')")
```

###### `leadr.boards.api.board_template_schemas.BoardTemplateResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response model for a board template.

**Functions:**

- [**from_domain**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.from_domain) – Convert domain entity to response model.

**Attributes:**

- [**account_id**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**config**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.config) (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\]</code>) –
- [**created_at**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**ends_at**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.ends_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**game_id**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.game_id) (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) –
- [**icon**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.icon) (<code>[str](#str) | None</code>) –
- [**id**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.id) (<code>[BoardTemplateID](./common.md#leadr.common.domain.ids.BoardTemplateID)</code>) –
- [**is_active**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.is_active) (<code>[bool](#bool)</code>) –
- [**is_published**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.is_published) (<code>[bool](#bool)</code>) –
- [**keep_strategy**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.keep_strategy) (<code>[KeepStrategy](./boards.md#leadr.boards.domain.board.KeepStrategy)</code>) –
- [**name**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.name) (<code>[str](#str)</code>) –
- [**name_template**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.name_template) (<code>[str](#str) | None</code>) –
- [**next_run_at**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.next_run_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**repeat_interval**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.repeat_interval) (<code>[str](#str)</code>) –
- [**series**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.series) (<code>[str](#str) | None</code>) –
- [**slug**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.slug) (<code>[str](#str) | None</code>) –
- [**sort_direction**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.sort_direction) (<code>[SortDirection](./boards.md#leadr.boards.domain.board.SortDirection)</code>) –
- [**starts_at**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.starts_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**tags**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.tags) (<code>[list](#list)\[[str](#str)\]</code>) –
- [**unit**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.unit) (<code>[str](#str) | None</code>) –
- [**updated_at**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.account_id`

```python
account_id: AccountID = Field(description='ID of the account this template belongs to')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.config`

```python
config: dict[str, Any] = Field(default_factory=dict, description='Reserved for future procedural generation (bounds, variables, randomization rules)')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.created_at`

```python
created_at: datetime = Field(description='Timestamp when the template was created (UTC)')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.ends_at`

```python
ends_at: datetime | None = Field(description='Optional end time for time-bounded boards')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.from_domain`

```python
from_domain(template)
```

Convert domain entity to response model.

**Parameters:**

- **template** (<code>[BoardTemplate](#leadr.boards.domain.board_template.BoardTemplate)</code>) – The domain BoardTemplate entity to convert.

**Returns:**

- <code>[BoardTemplateResponse](#leadr.boards.api.board_template_schemas.BoardTemplateResponse)</code> – BoardTemplateResponse with all fields populated from the domain entity.

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.game_id`

```python
game_id: GameID = Field(description='ID of the game this template belongs to')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.icon`

```python
icon: str | None = Field(description='Icon identifier for boards created from this template')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.id`

```python
id: BoardTemplateID = Field(description='Unique identifier for the template')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.is_active`

```python
is_active: bool = Field(description='Whether the template is currently active')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.is_published`

```python
is_published: bool = Field(description='Whether boards created from this template should be published')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.keep_strategy`

```python
keep_strategy: KeepStrategy = Field(description='Strategy for keeping multiple scores from the same user')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.name`

```python
name: str = Field(description='Name of the template')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.name_template`

```python
name_template: str | None = Field(default=None, description='Template string for generating board names, or null')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.next_run_at`

```python
next_run_at: datetime = Field(description='Next scheduled run time (UTC)')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.repeat_interval`

```python
repeat_interval: str = Field(description='Repeat frequency in PostgreSQL interval syntax')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.series`

```python
series: str | None = Field(default=None, description='Series identifier for sequential board naming, or null')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.slug`

```python
slug: str | None = Field(description='URL-friendly slug for boards created from this template, or null')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.sort_direction`

```python
sort_direction: SortDirection = Field(description='Direction to sort scores (ascending/descending)')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.starts_at`

```python
starts_at: datetime | None = Field(description='Optional start time for time-bounded boards')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.tags`

```python
tags: list[str] = Field(description='List of tags for categorizing boards created from this template')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.unit`

```python
unit: str | None = Field(description="Unit of measurement for scores (e.g., 'seconds', 'points')")
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.updated_at`

```python
updated_at: datetime = Field(description='Timestamp of last update (UTC)')
```

###### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request model for updating a board template.

**Attributes:**

- [**config**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.config) (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\] | None</code>) –
- [**deleted**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.deleted) (<code>[bool](#bool) | None</code>) –
- [**ends_at**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.ends_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**icon**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.icon) (<code>[str](#str) | None</code>) –
- [**is_active**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.is_active) (<code>[bool](#bool) | None</code>) –
- [**is_published**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.is_published) (<code>[bool](#bool) | None</code>) –
- [**keep_strategy**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.keep_strategy) (<code>[KeepStrategy](./boards.md#leadr.boards.domain.board.KeepStrategy) | None</code>) –
- [**name**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.name) (<code>[str](#str) | None</code>) –
- [**name_template**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.name_template) (<code>[str](#str) | None</code>) –
- [**next_run_at**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.next_run_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**repeat_interval**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.repeat_interval) (<code>[str](#str) | None</code>) –
- [**series**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.series) (<code>[str](#str) | None</code>) –
- [**slug**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.slug) (<code>[str](#str) | None</code>) –
- [**sort_direction**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.sort_direction) (<code>[SortDirection](./boards.md#leadr.boards.domain.board.SortDirection) | None</code>) –
- [**starts_at**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.starts_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**tags**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.tags) (<code>[list](#list)\[[str](#str)\] | None</code>) –
- [**unit**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.unit) (<code>[str](#str) | None</code>) –

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.config`

```python
config: dict[str, Any] | None = Field(default=None, description='Updated config (reserved for procedural generation)')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.deleted`

```python
deleted: bool | None = Field(default=None, description='Set to true to soft delete the template')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.ends_at`

```python
ends_at: datetime | None = Field(default=None, description='Updated end time')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.icon`

```python
icon: str | None = Field(default=None, description='Updated icon identifier')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.is_active`

```python
is_active: bool | None = Field(default=None, description='Updated active status')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.is_published`

```python
is_published: bool | None = Field(default=None, description='Updated published status')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.keep_strategy`

```python
keep_strategy: KeepStrategy | None = Field(default=None, description='Updated keep strategy')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.name`

```python
name: str | None = Field(default=None, description='Updated template name')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.name_template`

```python
name_template: str | None = Field(default=None, description='Updated name template')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.next_run_at`

```python
next_run_at: datetime | None = Field(default=None, description='Updated next run time')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.repeat_interval`

```python
repeat_interval: str | None = Field(default=None, description='Updated repeat interval')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.series`

```python
series: str | None = Field(default=None, description='Updated series identifier')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.slug`

```python
slug: str | None = Field(default=None, description='Updated slug')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.sort_direction`

```python
sort_direction: SortDirection | None = Field(default=None, description='Updated sort direction')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.starts_at`

```python
starts_at: datetime | None = Field(default=None, description='Updated start time')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.tags`

```python
tags: list[str] | None = Field(default=None, description='Updated tags list')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.unit`

```python
unit: str | None = Field(default=None, description='Updated unit of measurement')
```

#### `leadr.boards.domain`

**Modules:**

- [**board**](./boards.md#leadr.boards.domain.board) – Board domain model.
- [**board_template**](#leadr.boards.domain.board_template) – BoardTemplate domain model.
- [**interval_parser**](#leadr.boards.domain.interval_parser) – Utilities for parsing PostgreSQL interval syntax.

##### `leadr.boards.domain.board`

Board domain model.

**Classes:**

- [**Board**](./boards.md#leadr.boards.domain.board.Board) – Board domain entity.
- [**KeepStrategy**](./boards.md#leadr.boards.domain.board.KeepStrategy) – Strategy for keeping scores from the same user.
- [**SortDirection**](./boards.md#leadr.boards.domain.board.SortDirection) – Sort direction for board scores.

###### `leadr.boards.domain.board.Board`

Bases: <code>[Entity](./common.md#leadr.common.domain.models.Entity)</code>

Board domain entity.

Represents a leaderboard/board that belongs to a game. Boards define how
scores are tracked, sorted, and displayed. Each board has a globally unique
short_code for direct sharing and can be time-bounded with start/end dates.

Each board belongs to exactly one game and inherits the game's account for
multi-tenancy. Boards can be created from templates and can have custom
tags for categorization.

**Functions:**

- [**restore**](./boards.md#leadr.boards.domain.board.Board.restore) – Restore a soft-deleted entity.
- [**soft_delete**](#leadr.boards.domain.board.Board.soft_delete) – Mark entity as soft-deleted.
- [**validate_name**](#leadr.boards.domain.board.Board.validate_name) – Validate board name is not empty.
- [**validate_short_code**](#leadr.boards.domain.board.Board.validate_short_code) – Validate short_code is not empty.
- [**validate_slug**](#leadr.boards.domain.board.Board.validate_slug) – Validate slug format (lowercase alphanumeric with hyphens).

**Attributes:**

- [**account_id**](#leadr.boards.domain.board.Board.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**created_at**](#leadr.boards.domain.board.Board.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**created_from_template_id**](#leadr.boards.domain.board.Board.created_from_template_id) (<code>[BoardTemplateID](./common.md#leadr.common.domain.ids.BoardTemplateID) | None</code>) –
- [**deleted_at**](#leadr.boards.domain.board.Board.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**description**](./boards.md#leadr.boards.domain.board.Board.description) (<code>[str](#str) | None</code>) –
- [**ends_at**](#leadr.boards.domain.board.Board.ends_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**game_id**](#leadr.boards.domain.board.Board.game_id) (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) –
- [**icon**](./boards.md#leadr.boards.domain.board.Board.icon) (<code>[str](#str) | None</code>) –
- [**id**](./boards.md#leadr.boards.domain.board.Board.id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) –
- [**is_active**](#leadr.boards.domain.board.Board.is_active) (<code>[bool](#bool)</code>) –
- [**is_deleted**](#leadr.boards.domain.board.Board.is_deleted) (<code>[bool](#bool)</code>) – Check if entity is soft-deleted.
- [**is_published**](#leadr.boards.domain.board.Board.is_published) (<code>[bool](#bool)</code>) –
- [**keep_strategy**](#leadr.boards.domain.board.Board.keep_strategy) (<code>[KeepStrategy](./boards.md#leadr.boards.domain.board.KeepStrategy)</code>) –
- [**model_config**](#leadr.boards.domain.board.Board.model_config) –
- [**name**](./boards.md#leadr.boards.domain.board.Board.name) (<code>[str](#str)</code>) –
- [**short_code**](#leadr.boards.domain.board.Board.short_code) (<code>[str](#str)</code>) –
- [**slug**](./boards.md#leadr.boards.domain.board.Board.slug) (<code>[str](#str)</code>) –
- [**sort_direction**](#leadr.boards.domain.board.Board.sort_direction) (<code>[SortDirection](./boards.md#leadr.boards.domain.board.SortDirection)</code>) –
- [**starts_at**](#leadr.boards.domain.board.Board.starts_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**tags**](./boards.md#leadr.boards.domain.board.Board.tags) (<code>[list](#list)\[[str](#str)\]</code>) –
- [**template_name**](#leadr.boards.domain.board.Board.template_name) (<code>[str](#str) | None</code>) –
- [**unit**](./boards.md#leadr.boards.domain.board.Board.unit) (<code>[str](#str) | None</code>) –
- [**updated_at**](#leadr.boards.domain.board.Board.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.boards.domain.board.Board.account_id`

```python
account_id: AccountID = Field(frozen=True, description='ID of the account this board belongs to (immutable)')
```

####### `leadr.boards.domain.board.Board.created_at`

```python
created_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp when entity was created (UTC)')
```

####### `leadr.boards.domain.board.Board.created_from_template_id`

```python
created_from_template_id: BoardTemplateID | None = Field(default=None, description='Optional template ID this board was created from')
```

####### `leadr.boards.domain.board.Board.deleted_at`

```python
deleted_at: datetime | None = Field(default=None, description='Timestamp when entity was soft-deleted (UTC), or null if active')
```

####### `leadr.boards.domain.board.Board.description`

```python
description: str | None = Field(default=None, description='Short description of the board')
```

####### `leadr.boards.domain.board.Board.ends_at`

```python
ends_at: datetime | None = Field(default=None, description='Optional end time for time-bounded boards')
```

####### `leadr.boards.domain.board.Board.game_id`

```python
game_id: GameID = Field(frozen=True, description='ID of the game this board belongs to (immutable)')
```

####### `leadr.boards.domain.board.Board.icon`

```python
icon: str | None = Field(description='Icon identifier for the board', default='fa-crown')
```

####### `leadr.boards.domain.board.Board.id`

```python
id: BoardID = Field(frozen=True, default_factory=BoardID, description='Unique board identifier')
```

####### `leadr.boards.domain.board.Board.is_active`

```python
is_active: bool = Field(description='Whether the board is currently active', default=True)
```

####### `leadr.boards.domain.board.Board.is_deleted`

```python
is_deleted: bool
```

Check if entity is soft-deleted.

**Returns:**

- <code>[bool](#bool)</code> – True if the entity has a deleted_at timestamp, False otherwise.

####### `leadr.boards.domain.board.Board.is_published`

```python
is_published: bool = Field(description='Whether the board is published and visible on public web views', default=True)
```

####### `leadr.boards.domain.board.Board.keep_strategy`

```python
keep_strategy: KeepStrategy = Field(description='Strategy for keeping multiple scores from the same user', default=(KeepStrategy.ALL))
```

####### `leadr.boards.domain.board.Board.model_config`

```python
model_config = ConfigDict(validate_assignment=True)
```

####### `leadr.boards.domain.board.Board.name`

```python
name: str = Field(description='Name of the board')
```

####### `leadr.boards.domain.board.Board.restore`

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

####### `leadr.boards.domain.board.Board.short_code`

```python
short_code: str = Field(description='Globally unique short code for direct board sharing')
```

####### `leadr.boards.domain.board.Board.slug`

```python
slug: str = Field(description='URL-friendly slug for the board (unique per game when active)')
```

####### `leadr.boards.domain.board.Board.soft_delete`

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

####### `leadr.boards.domain.board.Board.sort_direction`

```python
sort_direction: SortDirection = Field(description='Direction to sort scores (ascending/descending)', default=(SortDirection.DESCENDING))
```

####### `leadr.boards.domain.board.Board.starts_at`

```python
starts_at: datetime | None = Field(default=None, description='Optional start time for time-bounded boards')
```

####### `leadr.boards.domain.board.Board.tags`

```python
tags: list[str] = Field(default_factory=list, description='List of tags for categorizing the board')
```

####### `leadr.boards.domain.board.Board.template_name`

```python
template_name: str | None = Field(default=None, description='Optional name of the template this board was created from')
```

####### `leadr.boards.domain.board.Board.unit`

```python
unit: str | None = Field(description="Unit of measurement for scores (e.g., 'seconds', 'points')", default=None)
```

####### `leadr.boards.domain.board.Board.updated_at`

```python
updated_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp of last update (UTC)')
```

####### `leadr.boards.domain.board.Board.validate_name`

```python
validate_name(value)
```

Validate board name is not empty.

**Parameters:**

- **value** (<code>[str](#str)</code>) – The board name to validate.

**Returns:**

- <code>[str](#str)</code> – The validated and trimmed board name.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If board name is empty or whitespace only.

####### `leadr.boards.domain.board.Board.validate_short_code`

```python
validate_short_code(value)
```

Validate short_code is not empty.

**Parameters:**

- **value** (<code>[str](#str)</code>) – The short_code to validate.

**Returns:**

- <code>[str](#str)</code> – The validated and trimmed short_code.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If short_code is empty or whitespace only.

####### `leadr.boards.domain.board.Board.validate_slug`

```python
validate_slug(value)
```

Validate slug format (lowercase alphanumeric with hyphens).

**Parameters:**

- **value** (<code>[str](#str)</code>) – The slug to validate.

**Returns:**

- <code>[str](#str)</code> – The validated slug.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If slug is invalid.

###### `leadr.boards.domain.board.KeepStrategy`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Strategy for keeping scores from the same user.

**Attributes:**

- [**ALL**](./boards.md#leadr.boards.domain.board.KeepStrategy.ALL) –
- [**BEST_ONLY**](#leadr.boards.domain.board.KeepStrategy.BEST_ONLY) –
- [**FIRST_ONLY**](#leadr.boards.domain.board.KeepStrategy.FIRST_ONLY) –
- [**LATEST_ONLY**](#leadr.boards.domain.board.KeepStrategy.LATEST_ONLY) –

####### `leadr.boards.domain.board.KeepStrategy.ALL`

```python
ALL = 'ALL'
```

####### `leadr.boards.domain.board.KeepStrategy.BEST_ONLY`

```python
BEST_ONLY = 'BEST_ONLY'
```

####### `leadr.boards.domain.board.KeepStrategy.FIRST_ONLY`

```python
FIRST_ONLY = 'FIRST_ONLY'
```

####### `leadr.boards.domain.board.KeepStrategy.LATEST_ONLY`

```python
LATEST_ONLY = 'LATEST_ONLY'
```

###### `leadr.boards.domain.board.SortDirection`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Sort direction for board scores.

**Attributes:**

- [**ASCENDING**](./boards.md#leadr.boards.domain.board.SortDirection.ASCENDING) –
- [**DESCENDING**](./boards.md#leadr.boards.domain.board.SortDirection.DESCENDING) –

####### `leadr.boards.domain.board.SortDirection.ASCENDING`

```python
ASCENDING = 'ASCENDING'
```

####### `leadr.boards.domain.board.SortDirection.DESCENDING`

```python
DESCENDING = 'DESCENDING'
```

##### `leadr.boards.domain.board_template`

BoardTemplate domain model.

**Classes:**

- [**BoardTemplate**](#leadr.boards.domain.board_template.BoardTemplate) – BoardTemplate domain entity.

###### `leadr.boards.domain.board_template.BoardTemplate`

Bases: <code>[Entity](./common.md#leadr.common.domain.models.Entity)</code>

BoardTemplate domain entity.

Represents a template for automatically generating boards at regular intervals.
Templates belong to a game and define the configuration for boards that will be
created by the pg_cron scheduler.

Each template specifies a repeat interval (PostgreSQL interval syntax), configuration
for boards to be created, and can optionally use template variables in the name
generation. Templates can be activated/deactivated and track the next scheduled run.

**Functions:**

- [**generate_name**](#leadr.boards.domain.board_template.BoardTemplate.generate_name) – Generate a board name using the name template.
- [**restore**](#leadr.boards.domain.board_template.BoardTemplate.restore) – Restore a soft-deleted entity.
- [**soft_delete**](#leadr.boards.domain.board_template.BoardTemplate.soft_delete) – Mark entity as soft-deleted.
- [**validate_name**](#leadr.boards.domain.board_template.BoardTemplate.validate_name) – Validate template name is not empty.
- [**validate_repeat_interval**](#leadr.boards.domain.board_template.BoardTemplate.validate_repeat_interval) – Validate repeat_interval uses PostgreSQL interval syntax.
- [**validate_slug**](#leadr.boards.domain.board_template.BoardTemplate.validate_slug) – Validate slug format (lowercase alphanumeric with hyphens).

**Attributes:**

- [**account_id**](#leadr.boards.domain.board_template.BoardTemplate.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**config**](#leadr.boards.domain.board_template.BoardTemplate.config) (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\]</code>) –
- [**created_at**](#leadr.boards.domain.board_template.BoardTemplate.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**deleted_at**](#leadr.boards.domain.board_template.BoardTemplate.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**ends_at**](#leadr.boards.domain.board_template.BoardTemplate.ends_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**game_id**](#leadr.boards.domain.board_template.BoardTemplate.game_id) (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) –
- [**icon**](#leadr.boards.domain.board_template.BoardTemplate.icon) (<code>[str](#str) | None</code>) –
- [**id**](#leadr.boards.domain.board_template.BoardTemplate.id) (<code>[BoardTemplateID](./common.md#leadr.common.domain.ids.BoardTemplateID)</code>) –
- [**is_active**](#leadr.boards.domain.board_template.BoardTemplate.is_active) (<code>[bool](#bool)</code>) –
- [**is_deleted**](#leadr.boards.domain.board_template.BoardTemplate.is_deleted) (<code>[bool](#bool)</code>) – Check if entity is soft-deleted.
- [**is_published**](#leadr.boards.domain.board_template.BoardTemplate.is_published) (<code>[bool](#bool)</code>) –
- [**keep_strategy**](#leadr.boards.domain.board_template.BoardTemplate.keep_strategy) (<code>[KeepStrategy](./boards.md#leadr.boards.domain.board.KeepStrategy)</code>) –
- [**model_config**](#leadr.boards.domain.board_template.BoardTemplate.model_config) –
- [**name**](#leadr.boards.domain.board_template.BoardTemplate.name) (<code>[str](#str)</code>) –
- [**name_template**](#leadr.boards.domain.board_template.BoardTemplate.name_template) (<code>[str](#str) | None</code>) –
- [**next_run_at**](#leadr.boards.domain.board_template.BoardTemplate.next_run_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**repeat_interval**](#leadr.boards.domain.board_template.BoardTemplate.repeat_interval) (<code>[str](#str)</code>) –
- [**series**](#leadr.boards.domain.board_template.BoardTemplate.series) (<code>[str](#str) | None</code>) –
- [**slug**](#leadr.boards.domain.board_template.BoardTemplate.slug) (<code>[str](#str) | None</code>) –
- [**sort_direction**](#leadr.boards.domain.board_template.BoardTemplate.sort_direction) (<code>[SortDirection](./boards.md#leadr.boards.domain.board.SortDirection)</code>) –
- [**starts_at**](#leadr.boards.domain.board_template.BoardTemplate.starts_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**tags**](#leadr.boards.domain.board_template.BoardTemplate.tags) (<code>[list](#list)\[[str](#str)\]</code>) –
- [**unit**](#leadr.boards.domain.board_template.BoardTemplate.unit) (<code>[str](#str) | None</code>) –
- [**updated_at**](#leadr.boards.domain.board_template.BoardTemplate.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.boards.domain.board_template.BoardTemplate.account_id`

```python
account_id: AccountID = Field(frozen=True, description='ID of the account this template belongs to (immutable)')
```

####### `leadr.boards.domain.board_template.BoardTemplate.config`

```python
config: dict[str, Any] = Field(default_factory=dict, description='Reserved for future procedural generation (bounds, variables, randomization rules)')
```

####### `leadr.boards.domain.board_template.BoardTemplate.created_at`

```python
created_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp when entity was created (UTC)')
```

####### `leadr.boards.domain.board_template.BoardTemplate.deleted_at`

```python
deleted_at: datetime | None = Field(default=None, description='Timestamp when entity was soft-deleted (UTC), or null if active')
```

####### `leadr.boards.domain.board_template.BoardTemplate.ends_at`

```python
ends_at: datetime | None = Field(default=None, description='Optional end time for time-bounded boards')
```

####### `leadr.boards.domain.board_template.BoardTemplate.game_id`

```python
game_id: GameID = Field(frozen=True, description='ID of the game this template belongs to (immutable)')
```

####### `leadr.boards.domain.board_template.BoardTemplate.generate_name`

```python
generate_name(timestamp, series_value)
```

Generate a board name using the name template.

If name_template is None, returns the template's name.
Otherwise, substitutes placeholders with values derived from the timestamp and series.

Supported placeholders:

- {year}: 4-digit year (e.g., 2025)
- {month}: Full month name (e.g., July)
- {month_short}: Abbreviated month (e.g., Jul)
- {week}: ISO week number (e.g., 29)
- {quarter}: Quarter (e.g., Q1, Q2, Q3, Q4)
- {date}: ISO date (e.g., 2025-07-15)
- {series}: Sequential series value

**Parameters:**

- **timestamp** (<code>[datetime](#datetime.datetime)</code>) – The datetime to use for generating time-based placeholders.
- **series_value** (<code>[int](#int) | None</code>) – Optional series value for {series} placeholder.

**Returns:**

- <code>[str](#str)</code> – The generated board name.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If the name_template contains invalid placeholders or if
  {series} is used but series_value is None.

####### `leadr.boards.domain.board_template.BoardTemplate.icon`

```python
icon: str | None = Field(description='Icon identifier for boards created from this template', default='fa-crown')
```

####### `leadr.boards.domain.board_template.BoardTemplate.id`

```python
id: BoardTemplateID = Field(frozen=True, default_factory=BoardTemplateID, description='Unique board template identifier')
```

####### `leadr.boards.domain.board_template.BoardTemplate.is_active`

```python
is_active: bool = Field(description='Whether the template is currently active')
```

####### `leadr.boards.domain.board_template.BoardTemplate.is_deleted`

```python
is_deleted: bool
```

Check if entity is soft-deleted.

**Returns:**

- <code>[bool](#bool)</code> – True if the entity has a deleted_at timestamp, False otherwise.

####### `leadr.boards.domain.board_template.BoardTemplate.is_published`

```python
is_published: bool = Field(description='Whether boards created from this template should be published', default=True)
```

####### `leadr.boards.domain.board_template.BoardTemplate.keep_strategy`

```python
keep_strategy: KeepStrategy = Field(description='Strategy for keeping multiple scores from the same user', default=(KeepStrategy.ALL))
```

####### `leadr.boards.domain.board_template.BoardTemplate.model_config`

```python
model_config = ConfigDict(validate_assignment=True)
```

####### `leadr.boards.domain.board_template.BoardTemplate.name`

```python
name: str = Field(description='Name of the template')
```

####### `leadr.boards.domain.board_template.BoardTemplate.name_template`

```python
name_template: str | None = Field(default=None, description='Optional template string for generating board names')
```

####### `leadr.boards.domain.board_template.BoardTemplate.next_run_at`

```python
next_run_at: datetime = Field(description='Next scheduled time to create a board from this template')
```

####### `leadr.boards.domain.board_template.BoardTemplate.repeat_interval`

```python
repeat_interval: str = Field(description="PostgreSQL interval syntax for repeat frequency (e.g., '7 days', '1 month')")
```

####### `leadr.boards.domain.board_template.BoardTemplate.restore`

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

####### `leadr.boards.domain.board_template.BoardTemplate.series`

```python
series: str | None = Field(default=None, description="Optional series identifier for sequential board naming (e.g., 'weekly', 'seasonal')")
```

####### `leadr.boards.domain.board_template.BoardTemplate.slug`

```python
slug: str | None = Field(default=None, description='URL-friendly slug for boards created from this template')
```

####### `leadr.boards.domain.board_template.BoardTemplate.soft_delete`

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

####### `leadr.boards.domain.board_template.BoardTemplate.sort_direction`

```python
sort_direction: SortDirection = Field(description='Direction to sort scores (ascending/descending)', default=(SortDirection.DESCENDING))
```

####### `leadr.boards.domain.board_template.BoardTemplate.starts_at`

```python
starts_at: datetime | None = Field(default=None, description='Optional start time for time-bounded boards')
```

####### `leadr.boards.domain.board_template.BoardTemplate.tags`

```python
tags: list[str] = Field(default_factory=list, description='List of tags for categorizing boards created from this template')
```

####### `leadr.boards.domain.board_template.BoardTemplate.unit`

```python
unit: str | None = Field(description="Unit of measurement for scores (e.g., 'seconds', 'points')", default=None)
```

####### `leadr.boards.domain.board_template.BoardTemplate.updated_at`

```python
updated_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp of last update (UTC)')
```

####### `leadr.boards.domain.board_template.BoardTemplate.validate_name`

```python
validate_name(value)
```

Validate template name is not empty.

**Parameters:**

- **value** (<code>[str](#str)</code>) – The template name to validate.

**Returns:**

- <code>[str](#str)</code> – The validated and trimmed template name.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If template name is empty or whitespace only.

####### `leadr.boards.domain.board_template.BoardTemplate.validate_repeat_interval`

```python
validate_repeat_interval(value)
```

Validate repeat_interval uses PostgreSQL interval syntax.

**Parameters:**

- **value** (<code>[str](#str)</code>) – The interval string to validate.

**Returns:**

- <code>[str](#str)</code> – The validated interval string.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If interval syntax is invalid.

####### `leadr.boards.domain.board_template.BoardTemplate.validate_slug`

```python
validate_slug(value)
```

Validate slug format (lowercase alphanumeric with hyphens).

**Parameters:**

- **value** (<code>[str](#str) | None</code>) – The slug to validate, or None.

**Returns:**

- <code>[str](#str) | None</code> – The validated slug, or None if not provided.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If slug is invalid.

##### `leadr.boards.domain.interval_parser`

Utilities for parsing PostgreSQL interval syntax.

**Functions:**

- [**parse_interval_to_timedelta**](#leadr.boards.domain.interval_parser.parse_interval_to_timedelta) – Parse PostgreSQL interval syntax to Python timedelta.

###### `leadr.boards.domain.interval_parser.parse_interval_to_timedelta`

```python
parse_interval_to_timedelta(interval_string)
```

Parse PostgreSQL interval syntax to Python timedelta.

Supports formats like:

- "7 days"
- "1 week"
- "2 hours"
- "30 minutes"

**Parameters:**

- **interval_string** (<code>[str](#str)</code>) – PostgreSQL interval syntax string.

**Returns:**

- <code>[timedelta](#datetime.timedelta)</code> – Equivalent Python timedelta.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If interval format is invalid or unsupported.

<details class="example" open markdown="1">
<summary>Example</summary>

> > > parse_interval_to_timedelta("7 days")
> > > timedelta(days=7)
> > > parse_interval_to_timedelta("1 week")
> > > timedelta(weeks=1)

</details>

#### `leadr.boards.services`

**Modules:**

- [**board_service**](#leadr.boards.services.board_service) – Board service for managing board operations.
- [**board_tasks**](#leadr.boards.services.board_tasks) – Background tasks for board processing.
- [**board_template_service**](#leadr.boards.services.board_template_service) – BoardTemplate service for managing board template operations.
- [**dependencies**](./boards.md#leadr.boards.services.dependencies) – Board service dependency injection.
- [**repositories**](./boards.md#leadr.boards.services.repositories) – Board repository services.
- [**short_code_generator**](#leadr.boards.services.short_code_generator) – Utility for generating unique short codes for boards.

##### `leadr.boards.services.board_service`

Board service for managing board operations.

**Classes:**

- [**BoardService**](#leadr.boards.services.board_service.BoardService) – Service for managing board lifecycle and operations.

###### `leadr.boards.services.board_service.BoardService`

Bases: <code>[BaseService](./common.md#leadr.common.services.BaseService)\[[Board](./boards.md#leadr.boards.domain.board.Board), [BoardRepository](./boards.md#leadr.boards.services.repositories.BoardRepository)\]</code>

Service for managing board lifecycle and operations.

This service orchestrates board creation, updates, and retrieval
by coordinating between the domain models and repository layer.
Ensures business rules like game validation are enforced.

**Functions:**

- [**create_board**](#leadr.boards.services.board_service.BoardService.create_board) – Create a new board.
- [**create_board_from_template**](#leadr.boards.services.board_service.BoardService.create_board_from_template) – Create a new board from a board template.
- [**delete**](#leadr.boards.services.board_service.BoardService.delete) – Soft-delete an entity.
- [**get_board**](#leadr.boards.services.board_service.BoardService.get_board) – Get a board by its ID.
- [**get_board_by_short_code**](#leadr.boards.services.board_service.BoardService.get_board_by_short_code) – Get a board by its short_code.
- [**get_by_id**](#leadr.boards.services.board_service.BoardService.get_by_id) – Get an entity by its ID.
- [**get_by_id_or_raise**](#leadr.boards.services.board_service.BoardService.get_by_id_or_raise) – Get an entity by its ID or raise EntityNotFoundError.
- [**list_all**](#leadr.boards.services.board_service.BoardService.list_all) – List all non-deleted entities.
- [**list_boards**](#leadr.boards.services.board_service.BoardService.list_boards) – List boards with optional filtering and pagination.
- [**list_boards_by_account**](#leadr.boards.services.board_service.BoardService.list_boards_by_account) – List all boards for an account.
- [**soft_delete**](#leadr.boards.services.board_service.BoardService.soft_delete) – Soft-delete an entity and return it before deletion.
- [**update_board**](#leadr.boards.services.board_service.BoardService.update_board) – Update board fields.

**Attributes:**

- [**repository**](#leadr.boards.services.board_service.BoardService.repository) –

####### `leadr.boards.services.board_service.BoardService.create_board`

```python
create_board(account_id, game_id, name, icon='fa-crown', unit=None, is_active=True, is_published=True, sort_direction=SortDirection.DESCENDING, keep_strategy=KeepStrategy.ALL, slug=None, short_code=None, created_from_template_id=None, template_name=None, starts_at=None, ends_at=None, tags=None, description=None)
```

Create a new board.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – The ID of the account that owns this board.
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) – The ID of the game this board belongs to.
- **name** (<code>[str](#str)</code>) – The board name.
- **icon** (<code>[str](#str) | None</code>) – Icon identifier for the board. Defaults to "fa-crown".
- **unit** (<code>[str](#str) | None</code>) – Unit of measurement for scores. Defaults to None.
- **is_active** (<code>[bool](#bool)</code>) – Whether the board is currently active. Defaults to True.
- **is_published** (<code>[bool](#bool)</code>) – Whether the board is published and visible on public web views.
  Defaults to True.
- **sort_direction** (<code>[SortDirection](./boards.md#leadr.boards.domain.board.SortDirection)</code>) – Direction to sort scores. Defaults to DESCENDING.
- **keep_strategy** (<code>[KeepStrategy](./boards.md#leadr.boards.domain.board.KeepStrategy)</code>) – Strategy for keeping multiple scores from same user. Defaults to ALL.
- **slug** (<code>[str](#str) | None</code>) – Optional URL-friendly slug. If not provided, auto-generated from name.
- **short_code** (<code>[str](#str) | None</code>) – Globally unique short code for direct sharing.
- **created_from_template_id** (<code>[BoardTemplateID](./common.md#leadr.common.domain.ids.BoardTemplateID) | None</code>) – Optional template ID this board was created from.
- **template_name** (<code>[str](#str) | None</code>) – Optional template name.
- **starts_at** (<code>[datetime](#datetime.datetime) | None</code>) – Optional start time for time-bounded boards.
- **ends_at** (<code>[datetime](#datetime.datetime) | None</code>) – Optional end time for time-bounded boards.
- **tags** (<code>[list](#list)\[[str](#str)\] | None</code>) – Optional list of tags for categorization.
- **description** (<code>[str](#str) | None</code>) – Optional short description of the board.

**Returns:**

- <code>[Board](./boards.md#leadr.boards.domain.board.Board)</code> – The created Board domain entity.

**Raises:**

- <code>[EntityNotFoundError](#EntityNotFoundError)</code> – If the game doesn't exist.
- <code>[ValueError](#ValueError)</code> – If the game doesn't belong to the specified account or slug is invalid.

<details class="example" open markdown="1">
<summary>Example</summary>

> > > board = await service.create_board(
> > > ... account_id=account.id,
> > > ... game_id=game.id,
> > > ... name="Speed Run Board",
> > > ... icon="trophy",
> > > ... unit="seconds",
> > > ... is_active=True,
> > > ... sort_direction=SortDirection.ASCENDING,
> > > ... keep_strategy=KeepStrategy.BEST_ONLY,
> > > ... )

</details>

####### `leadr.boards.services.board_service.BoardService.create_board_from_template`

```python
create_board_from_template(template)
```

Create a new board from a board template.

Extracts configuration from the template and calculates time boundaries
based on the template's repeat_interval. Automatically generates a unique
short code for the board. If the template has a series field, generates
a sequential series value and uses it in the board name.

**Parameters:**

- **template** (<code>[BoardTemplate](#leadr.boards.domain.board_template.BoardTemplate)</code>) – The BoardTemplate to create a board from.

**Returns:**

- <code>[Board](./boards.md#leadr.boards.domain.board.Board)</code> – The created Board domain entity.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If interval parsing fails, game doesn't belong to account,
  or name generation fails.

<details class="example" open markdown="1">
<summary>Example</summary>

> > > board = await service.create_board_from_template(template)

</details>

####### `leadr.boards.services.board_service.BoardService.delete`

```python
delete(entity_id)
```

Soft-delete an entity.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – The ID of the entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the entity doesn't exist

####### `leadr.boards.services.board_service.BoardService.get_board`

```python
get_board(board_id)
```

Get a board by its ID.

**Parameters:**

- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – The ID of the board to retrieve.

**Returns:**

- <code>[Board](./boards.md#leadr.boards.domain.board.Board) | None</code> – The Board domain entity if found, None otherwise.

####### `leadr.boards.services.board_service.BoardService.get_board_by_short_code`

```python
get_board_by_short_code(short_code)
```

Get a board by its short_code.

**Parameters:**

- **short_code** (<code>[str](#str)</code>) – The short_code to search for.

**Returns:**

- <code>[Board](./boards.md#leadr.boards.domain.board.Board) | None</code> – The Board domain entity if found, None otherwise.

####### `leadr.boards.services.board_service.BoardService.get_by_id`

```python
get_by_id(entity_id)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – The ID of the entity to retrieve

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.services.DomainEntityT) | None</code> – The domain entity if found, None otherwise

####### `leadr.boards.services.board_service.BoardService.get_by_id_or_raise`

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

####### `leadr.boards.services.board_service.BoardService.list_all`

```python
list_all()
```

List all non-deleted entities.

**Returns:**

- <code>[list](#list)\[[DomainEntityT](./common.md#leadr.common.services.DomainEntityT)\]</code> – List of domain entities

####### `leadr.boards.services.board_service.BoardService.list_boards`

```python
list_boards(account_id=None, game_id=None, code=None, slug=None, is_active=None, is_published=None, starts_before=None, starts_after=None, ends_before=None, ends_after=None, *, pagination)
```

List boards with optional filtering and pagination.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – Optional account ID to filter by
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID) | None</code>) – Optional game ID to filter by
- **code** (<code>[str](#str) | None</code>) – Optional short code to filter by
- **slug** (<code>[str](#str) | None</code>) – Optional slug to filter by
- **is_active** (<code>[bool](#bool) | None</code>) – Optional filter for active status
- **is_published** (<code>[bool](#bool) | None</code>) – Optional filter for published status
- **starts_before** (<code>[datetime](#datetime.datetime) | None</code>) – Optional filter for boards starting before this time
- **starts_after** (<code>[datetime](#datetime.datetime) | None</code>) – Optional filter for boards starting after this time
- **ends_before** (<code>[datetime](#datetime.datetime) | None</code>) – Optional filter for boards ending before this time
- **ends_after** (<code>[datetime](#datetime.datetime) | None</code>) – Optional filter for boards ending after this time
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (required)

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[Board](./boards.md#leadr.boards.domain.board.Board)\]</code> – PaginatedResult containing Board entities matching the filter criteria.

####### `leadr.boards.services.board_service.BoardService.list_boards_by_account`

```python
list_boards_by_account(account_id)
```

List all boards for an account.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – The ID of the account to list boards for.

**Returns:**

- <code>[list](#list)\[[Board](./boards.md#leadr.boards.domain.board.Board)\]</code> – List of Board domain entities for the account.

####### `leadr.boards.services.board_service.BoardService.repository`

```python
repository = self._create_repository(session)
```

####### `leadr.boards.services.board_service.BoardService.soft_delete`

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

####### `leadr.boards.services.board_service.BoardService.update_board`

```python
update_board(board_id, name=None, icon=None, short_code=None, unit=None, is_active=None, is_published=None, sort_direction=None, keep_strategy=None, created_from_template_id=None, template_name=None, starts_at=None, ends_at=None, tags=None, description=None)
```

Update board fields.

**Parameters:**

- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – The ID of the board to update
- **name** (<code>[str](#str) | None</code>) – New board name, if provided
- **icon** (<code>[str](#str) | None</code>) – New icon, if provided
- **short_code** (<code>[str](#str) | None</code>) – New short_code, if provided
- **unit** (<code>[str](#str) | None</code>) – New unit, if provided
- **is_active** (<code>[bool](#bool) | None</code>) – New is_active status, if provided
- **is_published** (<code>[bool](#bool) | None</code>) – New is_published status, if provided
- **sort_direction** (<code>[SortDirection](./boards.md#leadr.boards.domain.board.SortDirection) | None</code>) – New sort_direction, if provided
- **keep_strategy** (<code>[KeepStrategy](./boards.md#leadr.boards.domain.board.KeepStrategy) | None</code>) – New keep_strategy, if provided
- **created_from_template_id** (<code>[BoardTemplateID](./common.md#leadr.common.domain.ids.BoardTemplateID) | None</code>) – New created_from_template_id, if provided
- **template_name** (<code>[str](#str) | None</code>) – New template_name, if provided
- **starts_at** (<code>[datetime](#datetime.datetime) | None</code>) – New starts_at, if provided
- **ends_at** (<code>[datetime](#datetime.datetime) | None</code>) – New ends_at, if provided
- **tags** (<code>[list](#list)\[[str](#str)\] | None</code>) – New tags list, if provided
- **description** (<code>[str](#str) | None</code>) – New description, if provided

**Returns:**

- <code>[Board](./boards.md#leadr.boards.domain.board.Board)</code> – The updated Board domain entity

**Raises:**

- <code>[EntityNotFoundError](#EntityNotFoundError)</code> – If the board doesn't exist

##### `leadr.boards.services.board_tasks`

Background tasks for board processing.

Contains tasks for:

- Processing due board templates and creating boards
- Expiring boards past their end date

**Functions:**

- [**expire_boards**](#leadr.boards.services.board_tasks.expire_boards) – Expire boards that have passed their end date.
- [**process_due_templates**](#leadr.boards.services.board_tasks.process_due_templates) – Process all due board templates and create boards.

**Attributes:**

- [**logger**](#leadr.boards.services.board_tasks.logger) –

###### `leadr.boards.services.board_tasks.expire_boards`

```python
expire_boards()
```

Expire boards that have passed their end date.

Queries for active boards where ends_at \<= now() and sets is_active=False.

This task is designed to be called periodically (e.g., every minute).

###### `leadr.boards.services.board_tasks.logger`

```python
logger = logging.getLogger(__name__)
```

###### `leadr.boards.services.board_tasks.process_due_templates`

```python
process_due_templates()
```

Process all due board templates and create boards.

Queries for active templates where next_run_at \<= now(), creates boards
from each template, and updates the template's next_run_at.

This task is designed to be called periodically (e.g., every minute).

##### `leadr.boards.services.board_template_service`

BoardTemplate service for managing board template operations.

**Classes:**

- [**BoardTemplateService**](#leadr.boards.services.board_template_service.BoardTemplateService) – Service for managing board template lifecycle and operations.

###### `leadr.boards.services.board_template_service.BoardTemplateService`

Bases: <code>[BaseService](./common.md#leadr.common.services.BaseService)\[[BoardTemplate](#leadr.boards.domain.board_template.BoardTemplate), [BoardTemplateRepository](./boards.md#leadr.boards.services.repositories.BoardTemplateRepository)\]</code>

Service for managing board template lifecycle and operations.

This service orchestrates board template creation, updates, and retrieval
by coordinating between the domain models and repository layer.
Ensures business rules like game validation are enforced.

**Functions:**

- [**advance_template_schedule**](#leadr.boards.services.board_template_service.BoardTemplateService.advance_template_schedule) – Advance a template's next_run_at by its repeat_interval.
- [**create_board_template**](#leadr.boards.services.board_template_service.BoardTemplateService.create_board_template) – Create a new board template.
- [**delete**](#leadr.boards.services.board_template_service.BoardTemplateService.delete) – Soft-delete an entity.
- [**get_board_template**](#leadr.boards.services.board_template_service.BoardTemplateService.get_board_template) – Get a board template by its ID.
- [**get_by_id**](#leadr.boards.services.board_template_service.BoardTemplateService.get_by_id) – Get an entity by its ID.
- [**get_by_id_or_raise**](#leadr.boards.services.board_template_service.BoardTemplateService.get_by_id_or_raise) – Get an entity by its ID or raise EntityNotFoundError.
- [**list_all**](#leadr.boards.services.board_template_service.BoardTemplateService.list_all) – List all non-deleted entities.
- [**list_board_templates_by_account**](#leadr.boards.services.board_template_service.BoardTemplateService.list_board_templates_by_account) – List all board templates for an account with pagination.
- [**list_board_templates_by_game**](#leadr.boards.services.board_template_service.BoardTemplateService.list_board_templates_by_game) – List all board templates for a specific game with pagination.
- [**soft_delete**](#leadr.boards.services.board_template_service.BoardTemplateService.soft_delete) – Soft-delete an entity and return it before deletion.
- [**update_board_template**](#leadr.boards.services.board_template_service.BoardTemplateService.update_board_template) – Update board template fields.

**Attributes:**

- [**repository**](#leadr.boards.services.board_template_service.BoardTemplateService.repository) –

####### `leadr.boards.services.board_template_service.BoardTemplateService.advance_template_schedule`

```python
advance_template_schedule(template_id)
```

Advance a template's next_run_at by its repeat_interval.

This is typically called after successfully creating a board from the template.

**Parameters:**

- **template_id** (<code>[BoardTemplateID](./common.md#leadr.common.domain.ids.BoardTemplateID)</code>) – The ID of the template to advance.

**Returns:**

- <code>[BoardTemplate](#leadr.boards.domain.board_template.BoardTemplate)</code> – The updated BoardTemplate with advanced next_run_at.

**Raises:**

- <code>[EntityNotFoundError](#EntityNotFoundError)</code> – If the template doesn't exist.
- <code>[ValueError](#ValueError)</code> – If the repeat_interval cannot be parsed.

<details class="example" open markdown="1">
<summary>Example</summary>

> > > template = await service.advance_template_schedule(template.id)
> > >
> > > # template.next_run_at is now advanced by repeat_interval

</details>

####### `leadr.boards.services.board_template_service.BoardTemplateService.create_board_template`

```python
create_board_template(account_id, game_id, name, slug, repeat_interval, next_run_at, is_active, is_published=True, name_template=None, series=None, icon='fa-crown', unit=None, sort_direction=SortDirection.DESCENDING, keep_strategy=KeepStrategy.ALL, starts_at=None, ends_at=None, tags=None, config=None)
```

Create a new board template.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – The ID of the account that owns this template.
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) – The ID of the game this template belongs to.
- **name** (<code>[str](#str)</code>) – The template name.
- **repeat_interval** (<code>[str](#str)</code>) – PostgreSQL interval syntax for repeat frequency.
- **next_run_at** (<code>[datetime](#datetime.datetime)</code>) – Next scheduled time to create a board.
- **is_active** (<code>[bool](#bool)</code>) – Whether the template is currently active.
- **name_template** (<code>[str](#str) | None</code>) – Optional template string for generating board names.
- **series** (<code>[str](#str) | None</code>) – Optional series identifier for sequential board naming.
- **config** (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\] | None</code>) – Optional configuration object for boards created from this template.
- **config_template** – Optional template configuration for random generation.

**Returns:**

- <code>[BoardTemplate](#leadr.boards.domain.board_template.BoardTemplate)</code> – The created BoardTemplate domain entity.

**Raises:**

- <code>[EntityNotFoundError](#EntityNotFoundError)</code> – If the game doesn't exist.
- <code>[ValueError](#ValueError)</code> – If the game doesn't belong to the specified account or
  if name_template contains invalid placeholders.

<details class="example" open markdown="1">
<summary>Example</summary>

> > > template = await service.create_board_template(
> > > ... account_id=account.id,
> > > ... game_id=game.id,
> > > ... name="Weekly Speed Run Template",
> > > ... name_template="Week {series} - {year}",
> > > ... series="weekly",
> > > ... repeat_interval="7 days",
> > > ... next_run_at=datetime.now(UTC) + timedelta(days=7),
> > > ... is_active=True,
> > > ... )

</details>

####### `leadr.boards.services.board_template_service.BoardTemplateService.delete`

```python
delete(entity_id)
```

Soft-delete an entity.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – The ID of the entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the entity doesn't exist

####### `leadr.boards.services.board_template_service.BoardTemplateService.get_board_template`

```python
get_board_template(template_id)
```

Get a board template by its ID.

**Parameters:**

- **template_id** (<code>[BoardTemplateID](./common.md#leadr.common.domain.ids.BoardTemplateID)</code>) – The ID of the template to retrieve.

**Returns:**

- <code>[BoardTemplate](#leadr.boards.domain.board_template.BoardTemplate) | None</code> – The BoardTemplate domain entity if found, None otherwise.

####### `leadr.boards.services.board_template_service.BoardTemplateService.get_by_id`

```python
get_by_id(entity_id)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – The ID of the entity to retrieve

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.services.DomainEntityT) | None</code> – The domain entity if found, None otherwise

####### `leadr.boards.services.board_template_service.BoardTemplateService.get_by_id_or_raise`

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

####### `leadr.boards.services.board_template_service.BoardTemplateService.list_all`

```python
list_all()
```

List all non-deleted entities.

**Returns:**

- <code>[list](#list)\[[DomainEntityT](./common.md#leadr.common.services.DomainEntityT)\]</code> – List of domain entities

####### `leadr.boards.services.board_template_service.BoardTemplateService.list_board_templates_by_account`

```python
list_board_templates_by_account(account_id, *, pagination)
```

List all board templates for an account with pagination.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – The ID of the account to list templates for. If None, returns all
  templates (superadmin use case).
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (required).

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[BoardTemplate](#leadr.boards.domain.board_template.BoardTemplate)\]</code> – PaginatedResult containing BoardTemplate entities matching the filter criteria.

####### `leadr.boards.services.board_template_service.BoardTemplateService.list_board_templates_by_game`

```python
list_board_templates_by_game(account_id, game_id, *, pagination)
```

List all board templates for a specific game with pagination.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – The ID of the account. If None, returns templates from all accounts
  (superadmin use case).
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) – The ID of the game to list templates for.
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (required).

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[BoardTemplate](#leadr.boards.domain.board_template.BoardTemplate)\]</code> – PaginatedResult containing BoardTemplate entities matching the filter criteria.

####### `leadr.boards.services.board_template_service.BoardTemplateService.repository`

```python
repository = self._create_repository(session)
```

####### `leadr.boards.services.board_template_service.BoardTemplateService.soft_delete`

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

####### `leadr.boards.services.board_template_service.BoardTemplateService.update_board_template`

```python
update_board_template(template_id, name=None, slug=None, name_template=None, series=None, icon=None, unit=None, sort_direction=None, keep_strategy=None, starts_at=None, ends_at=None, tags=None, repeat_interval=None, config=None, next_run_at=None, is_active=None, is_published=None)
```

Update board template fields.

**Parameters:**

- **template_id** (<code>[BoardTemplateID](./common.md#leadr.common.domain.ids.BoardTemplateID)</code>) – The ID of the template to update.
- **name** (<code>[str](#str) | None</code>) – New template name, if provided.
- **name_template** (<code>[str](#str) | None</code>) – New name template, if provided.
- **series** (<code>[str](#str) | None</code>) – New series identifier, if provided.
- **repeat_interval** (<code>[str](#str) | None</code>) – New repeat interval, if provided.
- **config** (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\] | None</code>) – New config, if provided.
- **config_template** – New config template, if provided.
- **next_run_at** (<code>[datetime](#datetime.datetime) | None</code>) – New next_run_at, if provided.
- **is_active** (<code>[bool](#bool) | None</code>) – New is_active status, if provided.

**Returns:**

- <code>[BoardTemplate](#leadr.boards.domain.board_template.BoardTemplate)</code> – The updated BoardTemplate domain entity.

**Raises:**

- <code>[EntityNotFoundError](#EntityNotFoundError)</code> – If the template doesn't exist.
- <code>[ValueError](#ValueError)</code> – If name_template contains invalid placeholders.

##### `leadr.boards.services.dependencies`

Board service dependency injection.

**Functions:**

- [**get_board_service**](#leadr.boards.services.dependencies.get_board_service) – Get BoardService dependency.
- [**get_board_template_service**](#leadr.boards.services.dependencies.get_board_template_service) – Get BoardTemplateService dependency.

**Attributes:**

- [**BoardServiceDep**](./boards.md#leadr.boards.services.dependencies.BoardServiceDep) –
- [**BoardTemplateServiceDep**](./boards.md#leadr.boards.services.dependencies.BoardTemplateServiceDep) –

###### `leadr.boards.services.dependencies.BoardServiceDep`

```python
BoardServiceDep = Annotated[BoardService, Depends(get_board_service)]
```

###### `leadr.boards.services.dependencies.BoardTemplateServiceDep`

```python
BoardTemplateServiceDep = Annotated[BoardTemplateService, Depends(get_board_template_service)]
```

###### `leadr.boards.services.dependencies.get_board_service`

```python
get_board_service(db)
```

Get BoardService dependency.

**Parameters:**

- **db** (<code>[DatabaseSession](./common.md#leadr.common.dependencies.DatabaseSession)</code>) – Database session from dependency injection

**Returns:**

- <code>[BoardService](#leadr.boards.services.board_service.BoardService)</code> – BoardService instance for handling board operations

###### `leadr.boards.services.dependencies.get_board_template_service`

```python
get_board_template_service(db)
```

Get BoardTemplateService dependency.

**Parameters:**

- **db** (<code>[DatabaseSession](./common.md#leadr.common.dependencies.DatabaseSession)</code>) – Database session from dependency injection

**Returns:**

- <code>[BoardTemplateService](#leadr.boards.services.board_template_service.BoardTemplateService)</code> – BoardTemplateService instance for handling board template operations

##### `leadr.boards.services.repositories`

Board repository services.

**Classes:**

- [**BoardRepository**](./boards.md#leadr.boards.services.repositories.BoardRepository) – Board repository for managing board persistence.
- [**BoardTemplateRepository**](./boards.md#leadr.boards.services.repositories.BoardTemplateRepository) – BoardTemplate repository for managing board template persistence.

###### `leadr.boards.services.repositories.BoardRepository`

Bases: <code>[BaseRepository](./common.md#leadr.common.repositories.BaseRepository)\[[Board](./boards.md#leadr.boards.domain.board.Board), [BoardORM](./boards.md#leadr.boards.adapters.orm.BoardORM)\]</code>

Board repository for managing board persistence.

**Functions:**

- [**count_boards_by_template**](#leadr.boards.services.repositories.BoardRepository.count_boards_by_template) – Count boards created from a specific template.
- [**create**](./boards.md#leadr.boards.services.repositories.BoardRepository.create) – Create a new entity in the database.
- [**delete**](./boards.md#leadr.boards.services.repositories.BoardRepository.delete) – Soft delete an entity by setting its deleted_at timestamp.
- [**filter**](./boards.md#leadr.boards.services.repositories.BoardRepository.filter) – Filter boards with optional criteria and pagination.
- [**get_by_id**](#leadr.boards.services.repositories.BoardRepository.get_by_id) – Get an entity by its ID.
- [**get_by_short_code**](#leadr.boards.services.repositories.BoardRepository.get_by_short_code) – Get board by short_code.
- [**update**](./boards.md#leadr.boards.services.repositories.BoardRepository.update) – Update an existing entity in the database.

**Attributes:**

- [**SORTABLE_FIELDS**](#leadr.boards.services.repositories.BoardRepository.SORTABLE_FIELDS) –
- [**session**](./boards.md#leadr.boards.services.repositories.BoardRepository.session) –

####### `leadr.boards.services.repositories.BoardRepository.SORTABLE_FIELDS`

```python
SORTABLE_FIELDS = {'id', 'name', 'slug', 'short_code', 'created_at', 'updated_at'}
```

####### `leadr.boards.services.repositories.BoardRepository.count_boards_by_template`

```python
count_boards_by_template(template_id)
```

Count boards created from a specific template.

**Parameters:**

- **template_id** (<code>[BoardTemplateID](./common.md#leadr.common.domain.ids.BoardTemplateID)</code>) – The template ID to count boards for

**Returns:**

- <code>[int](#int)</code> – Number of boards created from this template

####### `leadr.boards.services.repositories.BoardRepository.create`

```python
create(entity)
```

Create a new entity in the database.

**Parameters:**

- **entity** (<code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code>) – Domain entity to create

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code> – Created domain entity with refreshed data

####### `leadr.boards.services.repositories.BoardRepository.delete`

```python
delete(entity_id)
```

Soft delete an entity by setting its deleted_at timestamp.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – ID of entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

####### `leadr.boards.services.repositories.BoardRepository.filter`

```python
filter(account_id=None, game_id=None, code=None, slug=None, is_active=None, is_published=None, starts_before=None, starts_after=None, ends_before=None, ends_after=None, *, pagination, **kwargs)
```

Filter boards with optional criteria and pagination.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – Optional account ID to filter by
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID) | None</code>) – Optional game ID to filter by
- **code** (<code>[str](#str) | None</code>) – Optional short code to filter by
- **slug** (<code>[str](#str) | None</code>) – Optional slug to filter by
- **is_active** (<code>[bool](#bool) | None</code>) – Optional filter for active status
- **is_published** (<code>[bool](#bool) | None</code>) – Optional filter for published status
- **starts_before** (<code>[datetime](#datetime.datetime) | None</code>) – Optional filter for boards starting before this time
- **starts_after** (<code>[datetime](#datetime.datetime) | None</code>) – Optional filter for boards starting after this time
- **ends_before** (<code>[datetime](#datetime.datetime) | None</code>) – Optional filter for boards ending before this time
- **ends_after** (<code>[datetime](#datetime.datetime) | None</code>) – Optional filter for boards ending after this time
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (required)

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[Board](./boards.md#leadr.boards.domain.board.Board)\]</code> – PaginatedResult containing boards matching the filter criteria

**Raises:**

- <code>[ValueError](#ValueError)</code> – If sort field is not in SORTABLE_FIELDS
- <code>[CursorValidationError](#CursorValidationError)</code> – If cursor is invalid or state doesn't match

####### `leadr.boards.services.repositories.BoardRepository.get_by_id`

```python
get_by_id(entity_id, include_deleted=False)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – Entity ID to retrieve
- **include_deleted** (<code>[bool](#bool)</code>) – If True, include soft-deleted entities. Defaults to False.

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT) | None</code> – Domain entity if found, None otherwise

####### `leadr.boards.services.repositories.BoardRepository.get_by_short_code`

```python
get_by_short_code(short_code)
```

Get board by short_code.

**Parameters:**

- **short_code** (<code>[str](#str)</code>) – The short_code to search for

**Returns:**

- <code>[Board](./boards.md#leadr.boards.domain.board.Board) | None</code> – Board entity if found, None otherwise

####### `leadr.boards.services.repositories.BoardRepository.session`

```python
session = session
```

####### `leadr.boards.services.repositories.BoardRepository.update`

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

###### `leadr.boards.services.repositories.BoardTemplateRepository`

Bases: <code>[BaseRepository](./common.md#leadr.common.repositories.BaseRepository)\[[BoardTemplate](#leadr.boards.domain.board_template.BoardTemplate), [BoardTemplateORM](./boards.md#leadr.boards.adapters.orm.BoardTemplateORM)\]</code>

BoardTemplate repository for managing board template persistence.

**Functions:**

- [**create**](./boards.md#leadr.boards.services.repositories.BoardTemplateRepository.create) – Create a new entity in the database.
- [**delete**](./boards.md#leadr.boards.services.repositories.BoardTemplateRepository.delete) – Soft delete an entity by setting its deleted_at timestamp.
- [**filter**](./boards.md#leadr.boards.services.repositories.BoardTemplateRepository.filter) – Filter board templates by account and optional game with pagination.
- [**get_by_id**](#leadr.boards.services.repositories.BoardTemplateRepository.get_by_id) – Get an entity by its ID.
- [**update**](./boards.md#leadr.boards.services.repositories.BoardTemplateRepository.update) – Update an existing entity in the database.

**Attributes:**

- [**SORTABLE_FIELDS**](#leadr.boards.services.repositories.BoardTemplateRepository.SORTABLE_FIELDS) –
- [**session**](./boards.md#leadr.boards.services.repositories.BoardTemplateRepository.session) –

####### `leadr.boards.services.repositories.BoardTemplateRepository.SORTABLE_FIELDS`

```python
SORTABLE_FIELDS = {'id', 'name', 'created_at', 'updated_at'}
```

####### `leadr.boards.services.repositories.BoardTemplateRepository.create`

```python
create(entity)
```

Create a new entity in the database.

**Parameters:**

- **entity** (<code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code>) – Domain entity to create

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code> – Created domain entity with refreshed data

####### `leadr.boards.services.repositories.BoardTemplateRepository.delete`

```python
delete(entity_id)
```

Soft delete an entity by setting its deleted_at timestamp.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – ID of entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

####### `leadr.boards.services.repositories.BoardTemplateRepository.filter`

```python
filter(account_id=None, game_id=None, *, pagination, **kwargs)
```

Filter board templates by account and optional game with pagination.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – Optional account ID to filter by. If None, returns all templates
  (superadmin use case). Regular users should always pass account_id.
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID) | None</code>) – OPTIONAL - Game ID to filter by
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (required)
- \*\***kwargs** (<code>[Any](#typing.Any)</code>) – Additional filter parameters (reserved for future use)

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[BoardTemplate](#leadr.boards.domain.board_template.BoardTemplate)\]</code> – PaginatedResult containing board templates matching the filter criteria

**Raises:**

- <code>[ValueError](#ValueError)</code> – If sort field is not in SORTABLE_FIELDS
- <code>[CursorValidationError](#CursorValidationError)</code> – If cursor is invalid or state doesn't match

####### `leadr.boards.services.repositories.BoardTemplateRepository.get_by_id`

```python
get_by_id(entity_id, include_deleted=False)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – Entity ID to retrieve
- **include_deleted** (<code>[bool](#bool)</code>) – If True, include soft-deleted entities. Defaults to False.

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT) | None</code> – Domain entity if found, None otherwise

####### `leadr.boards.services.repositories.BoardTemplateRepository.session`

```python
session = session
```

####### `leadr.boards.services.repositories.BoardTemplateRepository.update`

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

##### `leadr.boards.services.short_code_generator`

Utility for generating unique short codes for boards.

Short codes are used for direct board sharing (e.g., example.com/board/ABC123XY).
They must be globally unique across all boards.

**Functions:**

- [**generate_short_code**](#leadr.boards.services.short_code_generator.generate_short_code) – Generate a random 8-character alphanumeric short code.
- [**generate_unique_short_code**](#leadr.boards.services.short_code_generator.generate_unique_short_code) – Generate a globally unique short code with collision retry logic.

**Attributes:**

- [**CHARSET**](#leadr.boards.services.short_code_generator.CHARSET) –
- [**CODE_LENGTH**](#leadr.boards.services.short_code_generator.CODE_LENGTH) –

###### `leadr.boards.services.short_code_generator.CHARSET`

```python
CHARSET = '23456789ABCDEFGHJKMNPQRSTUVWXYZ'
```

###### `leadr.boards.services.short_code_generator.CODE_LENGTH`

```python
CODE_LENGTH = 5
```

###### `leadr.boards.services.short_code_generator.generate_short_code`

```python
generate_short_code()
```

Generate a random 8-character alphanumeric short code.

Uses cryptographically strong random number generator for security.
Excludes ambiguous characters (0/O, 1/I/l) for better readability.

**Returns:**

- <code>[str](#str)</code> – 5-character uppercase alphanumeric code (e.g., 'A7B3X').

<details class="example" open markdown="1">
<summary>Example</summary>

> > > code = generate_short_code()
> > > len(code)
> > > 5
> > > code.isupper()
> > > True

</details>

###### `leadr.boards.services.short_code_generator.generate_unique_short_code`

```python
generate_unique_short_code(session, max_retries=10)
```

Generate a globally unique short code with collision retry logic.

Generates random codes and checks database for uniqueness. If a collision
is detected, retries up to max_retries times before raising an error.

**Parameters:**

- **session** (<code>[AsyncSession](#sqlalchemy.ext.asyncio.AsyncSession)</code>) – Database session for uniqueness checking.
- **max_retries** (<code>[int](#int)</code>) – Maximum number of generation attempts (default 10).

**Returns:**

- <code>[str](#str)</code> – Unique 5-character short code guaranteed not to exist in database.

**Raises:**

- <code>[RuntimeError](#RuntimeError)</code> – If unable to generate unique code within max_retries attempts.

<details class="example" open markdown="1">
<summary>Example</summary>

> > > code = await generate_unique_short_code(session)
> > >
> > > # Code is guaranteed to be unique in database

</details>
