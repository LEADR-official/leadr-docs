### `leadr.games`

**Modules:**

- [**adapters**](./games.md#leadr.games.adapters) –
- [**api**](./games.md#leadr.games.api) –
- [**domain**](./games.md#leadr.games.domain) –
- [**services**](./games.md#leadr.games.services) –

#### `leadr.games.adapters`

**Modules:**

- [**orm**](./games.md#leadr.games.adapters.orm) – Game ORM model.

##### `leadr.games.adapters.orm`

Game ORM model.

**Classes:**

- [**GameORM**](./games.md#leadr.games.adapters.orm.GameORM) – Game ORM model.

###### `leadr.games.adapters.orm.GameORM`

Bases: <code>[Base](./common.md#leadr.common.orm.Base)</code>

Game ORM model.

Represents a game that belongs to an account in the database.
Maps to the games table with foreign key to accounts and unique
constraint on (account_id, name) to prevent duplicate game names
within the same account.

**Attributes:**

- [**account**](./games.md#leadr.games.adapters.orm.GameORM.account) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[AccountORM](./accounts.md#leadr.accounts.adapters.orm.AccountORM)\]</code>) –
- [**account_id**](#leadr.games.adapters.orm.GameORM.account_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**anti_cheat_enabled**](#leadr.games.adapters.orm.GameORM.anti_cheat_enabled) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[bool](#bool)\]</code>) –
- [**created_at**](#leadr.games.adapters.orm.GameORM.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**default_board_id**](#leadr.games.adapters.orm.GameORM.default_board_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID) | None\]</code>) –
- [**deleted_at**](#leadr.games.adapters.orm.GameORM.deleted_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[nullable_timestamp](#leadr.common.orm.nullable_timestamp)\]</code>) –
- [**description**](./games.md#leadr.games.adapters.orm.GameORM.description) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**id**](./games.md#leadr.games.adapters.orm.GameORM.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**name**](./games.md#leadr.games.adapters.orm.GameORM.name) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**page_url**](#leadr.games.adapters.orm.GameORM.page_url) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**slug**](./games.md#leadr.games.adapters.orm.GameORM.slug) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**steam_app_id**](#leadr.games.adapters.orm.GameORM.steam_app_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**tags**](./games.md#leadr.games.adapters.orm.GameORM.tags) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[list](#list)\[[str](#str)\]\]</code>) –
- [**updated_at**](#leadr.games.adapters.orm.GameORM.updated_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –

####### `leadr.games.adapters.orm.GameORM.account`

```python
account: Mapped[AccountORM] = relationship('AccountORM')
```

####### `leadr.games.adapters.orm.GameORM.account_id`

```python
account_id: Mapped[UUID] = mapped_column(ForeignKey('accounts.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.games.adapters.orm.GameORM.anti_cheat_enabled`

```python
anti_cheat_enabled: Mapped[bool] = mapped_column(nullable=False, default=True)
```

####### `leadr.games.adapters.orm.GameORM.created_at`

```python
created_at: Mapped[timestamp]
```

####### `leadr.games.adapters.orm.GameORM.default_board_id`

```python
default_board_id: Mapped[UUID | None] = mapped_column(nullable=True, default=None)
```

####### `leadr.games.adapters.orm.GameORM.deleted_at`

```python
deleted_at: Mapped[nullable_timestamp]
```

####### `leadr.games.adapters.orm.GameORM.description`

```python
description: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
```

####### `leadr.games.adapters.orm.GameORM.id`

```python
id: Mapped[uuid_pk]
```

####### `leadr.games.adapters.orm.GameORM.name`

```python
name: Mapped[str] = mapped_column(String, nullable=False)
```

####### `leadr.games.adapters.orm.GameORM.page_url`

```python
page_url: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
```

####### `leadr.games.adapters.orm.GameORM.slug`

```python
slug: Mapped[str] = mapped_column(String, nullable=False, unique=True, index=True)
```

####### `leadr.games.adapters.orm.GameORM.steam_app_id`

```python
steam_app_id: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
```

####### `leadr.games.adapters.orm.GameORM.tags`

```python
tags: Mapped[list[str]] = mapped_column(ARRAY(String), nullable=False, default=list, server_default='{}')
```

####### `leadr.games.adapters.orm.GameORM.updated_at`

```python
updated_at: Mapped[timestamp] = mapped_column(onupdate=(func.now()))
```

#### `leadr.games.api`

**Modules:**

- [**game_routes**](#leadr.games.api.game_routes) – Game API routes.
- [**game_schemas**](#leadr.games.api.game_schemas) – API request and response models for games.

##### `leadr.games.api.game_routes`

Game API routes.

**Functions:**

- [**create_game**](#leadr.games.api.game_routes.create_game) – Create a new game.
- [**get_game**](#leadr.games.api.game_routes.get_game) – Get a game by ID.
- [**list_games**](#leadr.games.api.game_routes.list_games) – List all games for an account with pagination and optional filtering.
- [**update_game**](#leadr.games.api.game_routes.update_game) – Update a game.

**Attributes:**

- [**router**](#leadr.games.api.game_routes.router) –

###### `leadr.games.api.game_routes.create_game`

```python
create_game(request, service, auth)
```

Create a new game.

Creates a new game associated with an existing account. Games can optionally
be configured with Steam integration and a default leaderboard.

For regular users, account_id must match their API key's account.
For superadmins, any account_id is accepted.

**Parameters:**

- **request** (<code>[GameCreateRequest](#leadr.games.api.game_schemas.GameCreateRequest)</code>) – Game creation details including account_id, name, and optional settings.
- **service** (<code>[GameServiceDep](./games.md#leadr.games.services.dependencies.GameServiceDep)</code>) – Injected game service dependency.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.

**Returns:**

- <code>[GameResponse](#leadr.games.api.game_schemas.GameResponse)</code> – GameResponse with the created game including auto-generated ID and timestamps.

**Raises:**

- <code>403</code> – User does not have access to the specified account.
- <code>404</code> – Account not found.

###### `leadr.games.api.game_routes.get_game`

```python
get_game(game_id, service, auth)
```

Get a game by ID.

**Parameters:**

- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) – Unique identifier for the game.
- **service** (<code>[GameServiceDep](./games.md#leadr.games.services.dependencies.GameServiceDep)</code>) – Injected game service dependency.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.

**Returns:**

- <code>[GameResponse](#leadr.games.api.game_schemas.GameResponse)</code> – GameResponse with full game details.

**Raises:**

- <code>403</code> – User does not have access to this game's account.
- <code>404</code> – Game not found.

###### `leadr.games.api.game_routes.list_games`

```python
list_games(auth, service, pagination, account_id=None, slug=None)
```

List all games for an account with pagination and optional filtering.

Returns paginated games for the specified account. Supports cursor-based
pagination with bidirectional navigation and custom sorting.

For regular users, account_id is automatically derived from their API key.
For superadmins, account_id is optional - if omitted, returns games from all accounts.

Filtering:

- Use ?slug={slug} to find a specific game by its globally unique slug

Pagination:

- Default: 20 items per page, sorted by created_at:desc,id:asc
- Custom sort: Use ?sort=name:asc,created_at:desc
- Valid sort fields: id, name, slug, created_at, updated_at
- Navigation: Use next_cursor/prev_cursor from response

<details class="example" open markdown="1">
<summary>Example</summary>

GET /v1/games?slug=my-game
GET /v1/games?account_id=acc_123&limit=50&sort=name:asc

</details>

**Parameters:**

- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.
- **service** (<code>[GameServiceDep](./games.md#leadr.games.services.dependencies.GameServiceDep)</code>) – Injected game service dependency.
- **pagination** (<code>[Annotated](#typing.Annotated)\[[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams), [Depends](#fastapi.Depends)()\]</code>) – Pagination parameters (cursor, limit, sort).
- **account_id** (<code>[Annotated](#typing.Annotated)\[[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None, [Query](#fastapi.Query)(description='Account ID filter')\]</code>) – Optional account_id query parameter (superadmins can omit to see all).
- **slug** (<code>[Annotated](#typing.Annotated)\[[str](#str) | None, [Query](#fastapi.Query)(description='Filter by game slug')\]</code>) – Optional slug filter to find a specific game.

**Returns:**

- <code>[PaginatedResponse](./common.md#leadr.common.api.pagination.PaginatedResponse)\[[GameResponse](#leadr.games.api.game_schemas.GameResponse)\]</code> – PaginatedResponse with games and pagination metadata.

**Raises:**

- <code>400</code> – Invalid cursor, sort field, or cursor state mismatch.
- <code>403</code> – User does not have access to the specified account.
- <code>404</code> – Game not found when filtering by slug.

###### `leadr.games.api.game_routes.router`

```python
router = APIRouter()
```

###### `leadr.games.api.game_routes.update_game`

```python
update_game(game_id, request, service, auth)
```

Update a game.

Supports updating name, Steam App ID, default board ID, or soft-deleting the game.

**Parameters:**

- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) – Unique identifier for the game.
- **request** (<code>[GameUpdateRequest](#leadr.games.api.game_schemas.GameUpdateRequest)</code>) – Game update details (all fields optional).
- **service** (<code>[GameServiceDep](./games.md#leadr.games.services.dependencies.GameServiceDep)</code>) – Injected game service dependency.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.

**Returns:**

- <code>[GameResponse](#leadr.games.api.game_schemas.GameResponse)</code> – GameResponse with the updated game details.

**Raises:**

- <code>403</code> – User does not have access to this game's account.
- <code>404</code> – Game not found.

##### `leadr.games.api.game_schemas`

API request and response models for games.

**Classes:**

- [**GameCreateRequest**](#leadr.games.api.game_schemas.GameCreateRequest) – Request model for creating a game.
- [**GameResponse**](#leadr.games.api.game_schemas.GameResponse) – Response model for a game.
- [**GameUpdateRequest**](#leadr.games.api.game_schemas.GameUpdateRequest) – Request model for updating a game.

###### `leadr.games.api.game_schemas.GameCreateRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request model for creating a game.

**Attributes:**

- [**account_id**](#leadr.games.api.game_schemas.GameCreateRequest.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**anti_cheat_enabled**](#leadr.games.api.game_schemas.GameCreateRequest.anti_cheat_enabled) (<code>[bool](#bool)</code>) –
- [**default_board_id**](#leadr.games.api.game_schemas.GameCreateRequest.default_board_id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None</code>) –
- [**description**](#leadr.games.api.game_schemas.GameCreateRequest.description) (<code>[str](#str) | None</code>) –
- [**name**](#leadr.games.api.game_schemas.GameCreateRequest.name) (<code>[str](#str)</code>) –
- [**page_url**](#leadr.games.api.game_schemas.GameCreateRequest.page_url) (<code>[str](#str) | None</code>) –
- [**slug**](#leadr.games.api.game_schemas.GameCreateRequest.slug) (<code>[str](#str) | None</code>) –
- [**steam_app_id**](#leadr.games.api.game_schemas.GameCreateRequest.steam_app_id) (<code>[str](#str) | None</code>) –
- [**tags**](#leadr.games.api.game_schemas.GameCreateRequest.tags) (<code>[list](#list)\[[str](#str)\] | None</code>) –

####### `leadr.games.api.game_schemas.GameCreateRequest.account_id`

```python
account_id: AccountID = Field(description='ID of the account this game belongs to')
```

####### `leadr.games.api.game_schemas.GameCreateRequest.anti_cheat_enabled`

```python
anti_cheat_enabled: bool = Field(default=True, description='Whether anti-cheat is enabled for this game (defaults to True)')
```

####### `leadr.games.api.game_schemas.GameCreateRequest.default_board_id`

```python
default_board_id: BoardID | None = Field(default=None, description='Optional ID of the default leaderboard for this game')
```

####### `leadr.games.api.game_schemas.GameCreateRequest.description`

```python
description: str | None = Field(default=None, description='Optional game description')
```

####### `leadr.games.api.game_schemas.GameCreateRequest.name`

```python
name: str = Field(description='Name of the game')
```

####### `leadr.games.api.game_schemas.GameCreateRequest.page_url`

```python
page_url: str | None = Field(default=None, description="Optional URL to the game's page")
```

####### `leadr.games.api.game_schemas.GameCreateRequest.slug`

```python
slug: str | None = Field(default=None, description='Optional URL-friendly slug (globally unique). If not provided, will be auto-generated from name')
```

####### `leadr.games.api.game_schemas.GameCreateRequest.steam_app_id`

```python
steam_app_id: str | None = Field(default=None, description='Optional Steam App ID for Steam integration')
```

####### `leadr.games.api.game_schemas.GameCreateRequest.tags`

```python
tags: list[str] | None = Field(default=None, description='Optional list of tags for categorization')
```

###### `leadr.games.api.game_schemas.GameResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response model for a game.

**Functions:**

- [**from_domain**](#leadr.games.api.game_schemas.GameResponse.from_domain) – Convert domain entity to response model.

**Attributes:**

- [**account_id**](#leadr.games.api.game_schemas.GameResponse.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**anti_cheat_enabled**](#leadr.games.api.game_schemas.GameResponse.anti_cheat_enabled) (<code>[bool](#bool)</code>) –
- [**created_at**](#leadr.games.api.game_schemas.GameResponse.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**default_board_id**](#leadr.games.api.game_schemas.GameResponse.default_board_id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None</code>) –
- [**description**](#leadr.games.api.game_schemas.GameResponse.description) (<code>[str](#str) | None</code>) –
- [**id**](#leadr.games.api.game_schemas.GameResponse.id) (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) –
- [**name**](#leadr.games.api.game_schemas.GameResponse.name) (<code>[str](#str)</code>) –
- [**page_url**](#leadr.games.api.game_schemas.GameResponse.page_url) (<code>[str](#str) | None</code>) –
- [**slug**](#leadr.games.api.game_schemas.GameResponse.slug) (<code>[str](#str)</code>) –
- [**steam_app_id**](#leadr.games.api.game_schemas.GameResponse.steam_app_id) (<code>[str](#str) | None</code>) –
- [**tags**](#leadr.games.api.game_schemas.GameResponse.tags) (<code>[list](#list)\[[str](#str)\]</code>) –
- [**updated_at**](#leadr.games.api.game_schemas.GameResponse.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.games.api.game_schemas.GameResponse.account_id`

```python
account_id: AccountID = Field(description='ID of the account this game belongs to')
```

####### `leadr.games.api.game_schemas.GameResponse.anti_cheat_enabled`

```python
anti_cheat_enabled: bool = Field(description='Whether anti-cheat is enabled for this game')
```

####### `leadr.games.api.game_schemas.GameResponse.created_at`

```python
created_at: datetime = Field(description='Timestamp when the game was created (UTC)')
```

####### `leadr.games.api.game_schemas.GameResponse.default_board_id`

```python
default_board_id: BoardID | None = Field(default=None, description='ID of the default leaderboard, or null if not set')
```

####### `leadr.games.api.game_schemas.GameResponse.description`

```python
description: str | None = Field(default=None, description='Game description')
```

####### `leadr.games.api.game_schemas.GameResponse.from_domain`

```python
from_domain(game)
```

Convert domain entity to response model.

**Parameters:**

- **game** (<code>[Game](./games.md#leadr.games.domain.game.Game)</code>) – The domain Game entity to convert.

**Returns:**

- <code>[GameResponse](#leadr.games.api.game_schemas.GameResponse)</code> – GameResponse with all fields populated from the domain entity.

####### `leadr.games.api.game_schemas.GameResponse.id`

```python
id: GameID = Field(description='Unique identifier for the game')
```

####### `leadr.games.api.game_schemas.GameResponse.name`

```python
name: str = Field(description='Name of the game')
```

####### `leadr.games.api.game_schemas.GameResponse.page_url`

```python
page_url: str | None = Field(default=None, description="URL to the game's page")
```

####### `leadr.games.api.game_schemas.GameResponse.slug`

```python
slug: str = Field(description='URL-friendly slug for the game (globally unique, immutable)')
```

####### `leadr.games.api.game_schemas.GameResponse.steam_app_id`

```python
steam_app_id: str | None = Field(default=None, description='Steam App ID if Steam integration is configured')
```

####### `leadr.games.api.game_schemas.GameResponse.tags`

```python
tags: list[str] = Field(default_factory=list, description='List of tags for categorization')
```

####### `leadr.games.api.game_schemas.GameResponse.updated_at`

```python
updated_at: datetime = Field(description='Timestamp of last update (UTC)')
```

###### `leadr.games.api.game_schemas.GameUpdateRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request model for updating a game.

**Attributes:**

- [**anti_cheat_enabled**](#leadr.games.api.game_schemas.GameUpdateRequest.anti_cheat_enabled) (<code>[bool](#bool) | None</code>) –
- [**default_board_id**](#leadr.games.api.game_schemas.GameUpdateRequest.default_board_id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None</code>) –
- [**deleted**](#leadr.games.api.game_schemas.GameUpdateRequest.deleted) (<code>[bool](#bool) | None</code>) –
- [**description**](#leadr.games.api.game_schemas.GameUpdateRequest.description) (<code>[str](#str) | None</code>) –
- [**name**](#leadr.games.api.game_schemas.GameUpdateRequest.name) (<code>[str](#str) | None</code>) –
- [**page_url**](#leadr.games.api.game_schemas.GameUpdateRequest.page_url) (<code>[str](#str) | None</code>) –
- [**steam_app_id**](#leadr.games.api.game_schemas.GameUpdateRequest.steam_app_id) (<code>[str](#str) | None</code>) –
- [**tags**](#leadr.games.api.game_schemas.GameUpdateRequest.tags) (<code>[list](#list)\[[str](#str)\] | None</code>) –

####### `leadr.games.api.game_schemas.GameUpdateRequest.anti_cheat_enabled`

```python
anti_cheat_enabled: bool | None = Field(default=None, description='Whether anti-cheat is enabled for this game')
```

####### `leadr.games.api.game_schemas.GameUpdateRequest.default_board_id`

```python
default_board_id: BoardID | None = Field(default=None, description='Updated default leaderboard ID')
```

####### `leadr.games.api.game_schemas.GameUpdateRequest.deleted`

```python
deleted: bool | None = Field(default=None, description='Set to true to soft delete the game')
```

####### `leadr.games.api.game_schemas.GameUpdateRequest.description`

```python
description: str | None = Field(default=None, description='Updated game description')
```

####### `leadr.games.api.game_schemas.GameUpdateRequest.name`

```python
name: str | None = Field(default=None, description='Updated game name')
```

####### `leadr.games.api.game_schemas.GameUpdateRequest.page_url`

```python
page_url: str | None = Field(default=None, description='Updated page URL')
```

####### `leadr.games.api.game_schemas.GameUpdateRequest.steam_app_id`

```python
steam_app_id: str | None = Field(default=None, description='Updated Steam App ID')
```

####### `leadr.games.api.game_schemas.GameUpdateRequest.tags`

```python
tags: list[str] | None = Field(default=None, description='Updated tags list')
```

#### `leadr.games.domain`

**Modules:**

- [**game**](./games.md#leadr.games.domain.game) – Game domain model.

##### `leadr.games.domain.game`

Game domain model.

**Classes:**

- [**Game**](./games.md#leadr.games.domain.game.Game) – Game domain entity.

###### `leadr.games.domain.game.Game`

Bases: <code>[Entity](./common.md#leadr.common.domain.models.Entity)</code>

Game domain entity.

Represents a game that belongs to an account. Games can have optional
Steam integration via steam_app_id and can reference a default leaderboard.

Each game belongs to exactly one account and cannot be transferred. Games
can be configured with Steam integration for syncing achievements or other
Steam platform features.

**Functions:**

- [**restore**](./games.md#leadr.games.domain.game.Game.restore) – Restore a soft-deleted entity.
- [**soft_delete**](#leadr.games.domain.game.Game.soft_delete) – Mark entity as soft-deleted.
- [**validate_name**](#leadr.games.domain.game.Game.validate_name) – Validate game name is not empty.
- [**validate_slug**](#leadr.games.domain.game.Game.validate_slug) – Validate slug format (lowercase alphanumeric with hyphens).

**Attributes:**

- [**account_id**](#leadr.games.domain.game.Game.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**anti_cheat_enabled**](#leadr.games.domain.game.Game.anti_cheat_enabled) (<code>[bool](#bool)</code>) –
- [**created_at**](#leadr.games.domain.game.Game.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**default_board_id**](#leadr.games.domain.game.Game.default_board_id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None</code>) –
- [**deleted_at**](#leadr.games.domain.game.Game.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**description**](./games.md#leadr.games.domain.game.Game.description) (<code>[str](#str) | None</code>) –
- [**id**](./games.md#leadr.games.domain.game.Game.id) (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) –
- [**is_deleted**](#leadr.games.domain.game.Game.is_deleted) (<code>[bool](#bool)</code>) – Check if entity is soft-deleted.
- [**model_config**](#leadr.games.domain.game.Game.model_config) –
- [**name**](./games.md#leadr.games.domain.game.Game.name) (<code>[str](#str)</code>) –
- [**page_url**](#leadr.games.domain.game.Game.page_url) (<code>[str](#str) | None</code>) –
- [**slug**](./games.md#leadr.games.domain.game.Game.slug) (<code>[str](#str)</code>) –
- [**steam_app_id**](#leadr.games.domain.game.Game.steam_app_id) (<code>[str](#str) | None</code>) –
- [**tags**](./games.md#leadr.games.domain.game.Game.tags) (<code>[list](#list)\[[str](#str)\]</code>) –
- [**updated_at**](#leadr.games.domain.game.Game.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.games.domain.game.Game.account_id`

```python
account_id: AccountID = Field(frozen=True, description='ID of the account this game belongs to (immutable)')
```

####### `leadr.games.domain.game.Game.anti_cheat_enabled`

```python
anti_cheat_enabled: bool = Field(default=True, description='Whether anti-cheat is enabled for this game (defaults to enabled)')
```

####### `leadr.games.domain.game.Game.created_at`

```python
created_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp when entity was created (UTC)')
```

####### `leadr.games.domain.game.Game.default_board_id`

```python
default_board_id: BoardID | None = Field(default=None, description='Optional default leaderboard ID for this game')
```

####### `leadr.games.domain.game.Game.deleted_at`

```python
deleted_at: datetime | None = Field(default=None, description='Timestamp when entity was soft-deleted (UTC), or null if active')
```

####### `leadr.games.domain.game.Game.description`

```python
description: str | None = Field(default=None, description='Short description of the game')
```

####### `leadr.games.domain.game.Game.id`

```python
id: GameID = Field(frozen=True, default_factory=GameID, description='Unique game identifier')
```

####### `leadr.games.domain.game.Game.is_deleted`

```python
is_deleted: bool
```

Check if entity is soft-deleted.

**Returns:**

- <code>[bool](#bool)</code> – True if the entity has a deleted_at timestamp, False otherwise.

####### `leadr.games.domain.game.Game.model_config`

```python
model_config = ConfigDict(validate_assignment=True)
```

####### `leadr.games.domain.game.Game.name`

```python
name: str = Field(description='Name of the game')
```

####### `leadr.games.domain.game.Game.page_url`

```python
page_url: str | None = Field(default=None, description="URL to the game's page or website")
```

####### `leadr.games.domain.game.Game.restore`

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

####### `leadr.games.domain.game.Game.slug`

```python
slug: str = Field(description='URL-friendly slug for the game (globally unique)')
```

####### `leadr.games.domain.game.Game.soft_delete`

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

####### `leadr.games.domain.game.Game.steam_app_id`

```python
steam_app_id: str | None = Field(default=None, description='Optional Steam App ID for platform integration')
```

####### `leadr.games.domain.game.Game.tags`

```python
tags: list[str] = Field(default_factory=list, description='List of tags for categorizing the game')
```

####### `leadr.games.domain.game.Game.updated_at`

```python
updated_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp of last update (UTC)')
```

####### `leadr.games.domain.game.Game.validate_name`

```python
validate_name(value)
```

Validate game name is not empty.

**Parameters:**

- **value** (<code>[str](#str)</code>) – The game name to validate.

**Returns:**

- <code>[str](#str)</code> – The validated and trimmed game name.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If game name is empty or whitespace only.

####### `leadr.games.domain.game.Game.validate_slug`

```python
validate_slug(value)
```

Validate slug format (lowercase alphanumeric with hyphens).

**Parameters:**

- **value** (<code>[str](#str)</code>) – The slug to validate.

**Returns:**

- <code>[str](#str)</code> – The validated slug.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If slug format is invalid.

#### `leadr.games.services`

**Modules:**

- [**dependencies**](./games.md#leadr.games.services.dependencies) – Game service dependencies for FastAPI dependency injection.
- [**game_service**](#leadr.games.services.game_service) – Game service for managing game operations.
- [**repositories**](./games.md#leadr.games.services.repositories) – Game repository services.

##### `leadr.games.services.dependencies`

Game service dependencies for FastAPI dependency injection.

**Functions:**

- [**get_game_service**](#leadr.games.services.dependencies.get_game_service) – Get GameService dependency.

**Attributes:**

- [**GameServiceDep**](./games.md#leadr.games.services.dependencies.GameServiceDep) –

###### `leadr.games.services.dependencies.GameServiceDep`

```python
GameServiceDep = Annotated[GameService, Depends(get_game_service)]
```

###### `leadr.games.services.dependencies.get_game_service`

```python
get_game_service(db)
```

Get GameService dependency.

##### `leadr.games.services.game_service`

Game service for managing game operations.

**Classes:**

- [**GameService**](#leadr.games.services.game_service.GameService) – Service for managing game lifecycle and operations.

###### `leadr.games.services.game_service.GameService`

Bases: <code>[BaseService](./common.md#leadr.common.services.BaseService)\[[Game](./games.md#leadr.games.domain.game.Game), [GameRepository](./games.md#leadr.games.services.repositories.GameRepository)\]</code>

Service for managing game lifecycle and operations.

This service orchestrates game creation, updates, and retrieval
by coordinating between the domain models and repository layer.

**Functions:**

- [**create_game**](#leadr.games.services.game_service.GameService.create_game) – Create a new game.
- [**delete**](#leadr.games.services.game_service.GameService.delete) – Soft-delete an entity.
- [**get_by_id**](#leadr.games.services.game_service.GameService.get_by_id) – Get an entity by its ID.
- [**get_by_id_or_raise**](#leadr.games.services.game_service.GameService.get_by_id_or_raise) – Get an entity by its ID or raise EntityNotFoundError.
- [**get_game**](#leadr.games.services.game_service.GameService.get_game) – Get a game by its ID.
- [**get_game_by_slug**](#leadr.games.services.game_service.GameService.get_game_by_slug) – Get a game by its slug (globally unique).
- [**list_all**](#leadr.games.services.game_service.GameService.list_all) – List all non-deleted entities.
- [**list_games**](#leadr.games.services.game_service.GameService.list_games) – List all games for an account with optional pagination.
- [**soft_delete**](#leadr.games.services.game_service.GameService.soft_delete) – Soft-delete an entity and return it before deletion.
- [**update_game**](#leadr.games.services.game_service.GameService.update_game) – Update game fields.

**Attributes:**

- [**repository**](#leadr.games.services.game_service.GameService.repository) –

####### `leadr.games.services.game_service.GameService.create_game`

```python
create_game(account_id, name, slug=None, steam_app_id=None, default_board_id=None, anti_cheat_enabled=True, description=None, tags=None, page_url=None)
```

Create a new game.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – The ID of the account that owns this game.
- **name** (<code>[str](#str)</code>) – The game name.
- **slug** (<code>[str](#str) | None</code>) – Optional URL-friendly slug. If not provided, auto-generated from name.
- **steam_app_id** (<code>[str](#str) | None</code>) – Optional Steam application ID.
- **default_board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None</code>) – Optional default leaderboard ID.
- **anti_cheat_enabled** (<code>[bool](#bool)</code>) – Whether anti-cheat is enabled (defaults to True).
- **description** (<code>[str](#str) | None</code>) – Optional short description of the game.
- **tags** (<code>[list](#list)\[[str](#str)\] | None</code>) – Optional list of tags for categorizing the game.
- **page_url** (<code>[str](#str) | None</code>) – Optional URL to the game's page or website.

**Returns:**

- <code>[Game](./games.md#leadr.games.domain.game.Game)</code> – The created Game domain entity.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If slug is invalid or already exists globally.

<details class="example" open markdown="1">
<summary>Example</summary>

> > > game = await service.create_game(
> > > ... account_id=account.id,
> > > ... name="Super Awesome Game",
> > > ... steam_app_id="123456",
> > > ... )

</details>

####### `leadr.games.services.game_service.GameService.delete`

```python
delete(entity_id)
```

Soft-delete an entity.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – The ID of the entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the entity doesn't exist

####### `leadr.games.services.game_service.GameService.get_by_id`

```python
get_by_id(entity_id)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – The ID of the entity to retrieve

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.services.DomainEntityT) | None</code> – The domain entity if found, None otherwise

####### `leadr.games.services.game_service.GameService.get_by_id_or_raise`

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

####### `leadr.games.services.game_service.GameService.get_game`

```python
get_game(game_id)
```

Get a game by its ID.

**Parameters:**

- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) – The ID of the game to retrieve.

**Returns:**

- <code>[Game](./games.md#leadr.games.domain.game.Game) | None</code> – The Game domain entity if found, None otherwise.

####### `leadr.games.services.game_service.GameService.get_game_by_slug`

```python
get_game_by_slug(slug)
```

Get a game by its slug (globally unique).

**Parameters:**

- **slug** (<code>[str](#str)</code>) – The game slug to search for.

**Returns:**

- <code>[Game](./games.md#leadr.games.domain.game.Game) | None</code> – The Game domain entity if found, None otherwise.

####### `leadr.games.services.game_service.GameService.list_all`

```python
list_all()
```

List all non-deleted entities.

**Returns:**

- <code>[list](#list)\[[DomainEntityT](./common.md#leadr.common.services.DomainEntityT)\]</code> – List of domain entities

####### `leadr.games.services.game_service.GameService.list_games`

```python
list_games(account_id, pagination=None)
```

List all games for an account with optional pagination.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – The ID of the account to list games for. If None, returns all
  games (superadmin use case).
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams) | None</code>) – Optional pagination parameters.

**Returns:**

- <code>[list](#list)\[[Game](./games.md#leadr.games.domain.game.Game)\] | [PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[Game](./games.md#leadr.games.domain.game.Game)\]</code> – List of Game entities if no pagination, PaginatedResult if pagination provided.

####### `leadr.games.services.game_service.GameService.repository`

```python
repository = self._create_repository(session)
```

####### `leadr.games.services.game_service.GameService.soft_delete`

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

####### `leadr.games.services.game_service.GameService.update_game`

```python
update_game(game_id, name=None, steam_app_id=None, default_board_id=None, anti_cheat_enabled=None, description=None, tags=None, page_url=None)
```

Update game fields.

**Parameters:**

- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) – The ID of the game to update
- **name** (<code>[str](#str) | None</code>) – New game name, if provided
- **steam_app_id** (<code>[str](#str) | None</code>) – New Steam app ID, if provided
- **default_board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None</code>) – New default board ID, if provided
- **anti_cheat_enabled** (<code>[bool](#bool) | None</code>) – Whether anti-cheat is enabled, if provided
- **description** (<code>[str](#str) | None</code>) – New game description, if provided
- **tags** (<code>[list](#list)\[[str](#str)\] | None</code>) – New list of tags, if provided
- **page_url** (<code>[str](#str) | None</code>) – New page URL, if provided

**Returns:**

- <code>[Game](./games.md#leadr.games.domain.game.Game)</code> – The updated Game domain entity

**Raises:**

- <code>[EntityNotFoundError](#EntityNotFoundError)</code> – If the game doesn't exist

##### `leadr.games.services.repositories`

Game repository services.

**Classes:**

- [**GameRepository**](./games.md#leadr.games.services.repositories.GameRepository) – Game repository for managing game persistence.

###### `leadr.games.services.repositories.GameRepository`

Bases: <code>[BaseRepository](./common.md#leadr.common.repositories.BaseRepository)\[[Game](./games.md#leadr.games.domain.game.Game), [GameORM](./games.md#leadr.games.adapters.orm.GameORM)\]</code>

Game repository for managing game persistence.

**Functions:**

- [**create**](./games.md#leadr.games.services.repositories.GameRepository.create) – Create a new entity in the database.
- [**delete**](./games.md#leadr.games.services.repositories.GameRepository.delete) – Soft delete an entity by setting its deleted_at timestamp.
- [**filter**](./games.md#leadr.games.services.repositories.GameRepository.filter) – Filter games by account and optional criteria.
- [**get_by_id**](#leadr.games.services.repositories.GameRepository.get_by_id) – Get an entity by its ID.
- [**get_by_slug**](#leadr.games.services.repositories.GameRepository.get_by_slug) – Get game by slug (globally unique lookup).
- [**update**](./games.md#leadr.games.services.repositories.GameRepository.update) – Update an existing entity in the database.

**Attributes:**

- [**SORTABLE_FIELDS**](#leadr.games.services.repositories.GameRepository.SORTABLE_FIELDS) –
- [**session**](./games.md#leadr.games.services.repositories.GameRepository.session) –

####### `leadr.games.services.repositories.GameRepository.SORTABLE_FIELDS`

```python
SORTABLE_FIELDS = {'id', 'name', 'slug', 'created_at', 'updated_at'}
```

####### `leadr.games.services.repositories.GameRepository.create`

```python
create(entity)
```

Create a new entity in the database.

**Parameters:**

- **entity** (<code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code>) – Domain entity to create

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code> – Created domain entity with refreshed data

####### `leadr.games.services.repositories.GameRepository.delete`

```python
delete(entity_id)
```

Soft delete an entity by setting its deleted_at timestamp.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – ID of entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

####### `leadr.games.services.repositories.GameRepository.filter`

```python
filter(account_id=None, pagination=None, **kwargs)
```

Filter games by account and optional criteria.

**Parameters:**

- **account_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID) | None</code>) – Optional account ID to filter by. If None, returns all games
  (superadmin use case). Regular users should always pass account_id.
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams) | None</code>) – Optional pagination parameters
- \*\***kwargs** (<code>[Any](#typing.Any)</code>) – Additional filter parameters (reserved for future use)

**Returns:**

- <code>[list](#list)\[[Game](./games.md#leadr.games.domain.game.Game)\] | [PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[Game](./games.md#leadr.games.domain.game.Game)\]</code> – List of games if no pagination, PaginatedResult if pagination provided

**Raises:**

- <code>[ValueError](#ValueError)</code> – If sort field is not in SORTABLE_FIELDS
- <code>[CursorValidationError](#CursorValidationError)</code> – If cursor is invalid or state doesn't match

####### `leadr.games.services.repositories.GameRepository.get_by_id`

```python
get_by_id(entity_id, include_deleted=False)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – Entity ID to retrieve
- **include_deleted** (<code>[bool](#bool)</code>) – If True, include soft-deleted entities. Defaults to False.

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT) | None</code> – Domain entity if found, None otherwise

####### `leadr.games.services.repositories.GameRepository.get_by_slug`

```python
get_by_slug(slug)
```

Get game by slug (globally unique lookup).

**Parameters:**

- **slug** (<code>[str](#str)</code>) – The game slug to search for.

**Returns:**

- <code>[Game](./games.md#leadr.games.domain.game.Game) | None</code> – Game domain entity if found, None otherwise.

####### `leadr.games.services.repositories.GameRepository.session`

```python
session = session
```

####### `leadr.games.services.repositories.GameRepository.update`

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
