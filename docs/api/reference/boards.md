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

###### `leadr.boards.adapters.orm.BoardORM`

Bases: <code>[Base](./common.md#leadr.common.orm.Base)</code>

Board ORM model.

Represents a leaderboard/board that belongs to a game in the database.
Maps to the boards table with foreign keys to accounts and games, and a
unique constraint on short_code (globally unique for direct sharing).

**Attributes:**

- [**account**](./boards.md#leadr.boards.adapters.orm.BoardORM.account) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[AccountORM](./accounts.md#leadr.accounts.adapters.orm.AccountORM)\]</code>) –
- [**account_id**](#leadr.boards.adapters.orm.BoardORM.account_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**created_at**](#leadr.boards.adapters.orm.BoardORM.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**deleted_at**](#leadr.boards.adapters.orm.BoardORM.deleted_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[nullable_timestamp](#leadr.common.orm.nullable_timestamp)\]</code>) –
- [**ends_at**](#leadr.boards.adapters.orm.BoardORM.ends_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime) | None\]</code>) –
- [**game**](./boards.md#leadr.boards.adapters.orm.BoardORM.game) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[GameORM](./games.md#leadr.games.adapters.orm.GameORM)\]</code>) –
- [**game_id**](#leadr.boards.adapters.orm.BoardORM.game_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**icon**](./boards.md#leadr.boards.adapters.orm.BoardORM.icon) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**id**](./boards.md#leadr.boards.adapters.orm.BoardORM.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**is_active**](#leadr.boards.adapters.orm.BoardORM.is_active) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[bool](#bool)\]</code>) –
- [**keep_strategy**](#leadr.boards.adapters.orm.BoardORM.keep_strategy) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**name**](./boards.md#leadr.boards.adapters.orm.BoardORM.name) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**short_code**](#leadr.boards.adapters.orm.BoardORM.short_code) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**sort_direction**](#leadr.boards.adapters.orm.BoardORM.sort_direction) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**starts_at**](#leadr.boards.adapters.orm.BoardORM.starts_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime) | None\]</code>) –
- [**tags**](./boards.md#leadr.boards.adapters.orm.BoardORM.tags) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[list](#list)\[[str](#str)\]\]</code>) –
- [**template_id**](#leadr.boards.adapters.orm.BoardORM.template_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID) | None\]</code>) –
- [**template_name**](#leadr.boards.adapters.orm.BoardORM.template_name) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**unit**](./boards.md#leadr.boards.adapters.orm.BoardORM.unit) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
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

####### `leadr.boards.adapters.orm.BoardORM.deleted_at`

```python
deleted_at: Mapped[nullable_timestamp]
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
icon: Mapped[str] = mapped_column(String, nullable=False)
```

####### `leadr.boards.adapters.orm.BoardORM.id`

```python
id: Mapped[uuid_pk]
```

####### `leadr.boards.adapters.orm.BoardORM.is_active`

```python
is_active: Mapped[bool] = mapped_column(Boolean, nullable=False)
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
short_code: Mapped[str] = mapped_column(String, nullable=False, unique=True)
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

####### `leadr.boards.adapters.orm.BoardORM.template_id`

```python
template_id: Mapped[UUID | None] = mapped_column(nullable=True, default=None)
```

####### `leadr.boards.adapters.orm.BoardORM.template_name`

```python
template_name: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
```

####### `leadr.boards.adapters.orm.BoardORM.unit`

```python
unit: Mapped[str] = mapped_column(String, nullable=False)
```

####### `leadr.boards.adapters.orm.BoardORM.updated_at`

```python
updated_at: Mapped[timestamp] = mapped_column(onupdate=(func.now()))
```

#### `leadr.boards.api`

**Modules:**

- [**routes**](./boards.md#leadr.boards.api.routes) – Board API routes.
- [**schemas**](./boards.md#leadr.boards.api.schemas) – API request and response models for boards.

##### `leadr.boards.api.routes`

Board API routes.

**Functions:**

- [**create_board**](#leadr.boards.api.routes.create_board) – Create a new board.
- [**get_board**](#leadr.boards.api.routes.get_board) – Get a board by ID.
- [**get_board_by_short_code**](#leadr.boards.api.routes.get_board_by_short_code) – Get a board by its short code.
- [**list_boards**](#leadr.boards.api.routes.list_boards) – List all boards for an account.
- [**update_board**](#leadr.boards.api.routes.update_board) – Update a board.

**Attributes:**

- [**router**](./boards.md#leadr.boards.api.routes.router) –

###### `leadr.boards.api.routes.create_board`

```python
create_board(request, service)
```

Create a new board.

Creates a new leaderboard associated with an existing game and account.
The game must belong to the specified account.

**Parameters:**

- **request** (<code>[BoardCreateRequest](./boards.md#leadr.boards.api.schemas.BoardCreateRequest)</code>) – Board creation details including account_id, game_id, name, and settings.
- **service** (<code>[BoardServiceDep](./boards.md#leadr.boards.services.dependencies.BoardServiceDep)</code>) – Injected board service dependency.

**Returns:**

- <code>[BoardResponse](./boards.md#leadr.boards.api.schemas.BoardResponse)</code> – BoardResponse with the created board including auto-generated ID and timestamps.

**Raises:**

- <code>404</code> – Game or account not found.
- <code>400</code> – Game doesn't belong to the specified account.

###### `leadr.boards.api.routes.get_board`

```python
get_board(board_id, service)
```

Get a board by ID.

**Parameters:**

- **board_id** (<code>[UUID](#uuid.UUID)</code>) – Unique identifier for the board.
- **service** (<code>[BoardServiceDep](./boards.md#leadr.boards.services.dependencies.BoardServiceDep)</code>) – Injected board service dependency.

**Returns:**

- <code>[BoardResponse](./boards.md#leadr.boards.api.schemas.BoardResponse)</code> – BoardResponse with full board details.

**Raises:**

- <code>404</code> – Board not found.

###### `leadr.boards.api.routes.get_board_by_short_code`

```python
get_board_by_short_code(short_code, service)
```

Get a board by its short code.

**Parameters:**

- **short_code** (<code>[str](#str)</code>) – Globally unique short code for the board.
- **service** (<code>[BoardServiceDep](./boards.md#leadr.boards.services.dependencies.BoardServiceDep)</code>) – Injected board service dependency.

**Returns:**

- <code>[BoardResponse](./boards.md#leadr.boards.api.schemas.BoardResponse)</code> – BoardResponse with full board details.

**Raises:**

- <code>404</code> – Board not found.

###### `leadr.boards.api.routes.list_boards`

```python
list_boards(account_id, service)
```

List all boards for an account.

**Parameters:**

- **account_id** (<code>[UUID](#uuid.UUID)</code>) – Account ID to filter boards by.
- **service** (<code>[BoardServiceDep](./boards.md#leadr.boards.services.dependencies.BoardServiceDep)</code>) – Injected board service dependency.

**Returns:**

- <code>[list](#list)\[[BoardResponse](./boards.md#leadr.boards.api.schemas.BoardResponse)\]</code> – List of all active boards for the specified account.

###### `leadr.boards.api.routes.router`

```python
router = APIRouter()
```

###### `leadr.boards.api.routes.update_board`

```python
update_board(board_id, request, service)
```

Update a board.

Supports updating any board field or soft-deleting the board.

**Parameters:**

- **board_id** (<code>[UUID](#uuid.UUID)</code>) – Unique identifier for the board.
- **request** (<code>[BoardUpdateRequest](./boards.md#leadr.boards.api.schemas.BoardUpdateRequest)</code>) – Board update details (all fields optional).
- **service** (<code>[BoardServiceDep](./boards.md#leadr.boards.services.dependencies.BoardServiceDep)</code>) – Injected board service dependency.

**Returns:**

- <code>[BoardResponse](./boards.md#leadr.boards.api.schemas.BoardResponse)</code> – BoardResponse with the updated board details.

**Raises:**

- <code>404</code> – Board not found.

##### `leadr.boards.api.schemas`

API request and response models for boards.

**Classes:**

- [**BoardCreateRequest**](./boards.md#leadr.boards.api.schemas.BoardCreateRequest) – Request model for creating a board.
- [**BoardResponse**](./boards.md#leadr.boards.api.schemas.BoardResponse) – Response model for a board.
- [**BoardUpdateRequest**](./boards.md#leadr.boards.api.schemas.BoardUpdateRequest) – Request model for updating a board.

###### `leadr.boards.api.schemas.BoardCreateRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request model for creating a board.

**Attributes:**

- [**account_id**](#leadr.boards.api.schemas.BoardCreateRequest.account_id) (<code>[UUID](#uuid.UUID)</code>) –
- [**ends_at**](#leadr.boards.api.schemas.BoardCreateRequest.ends_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**game_id**](#leadr.boards.api.schemas.BoardCreateRequest.game_id) (<code>[UUID](#uuid.UUID)</code>) –
- [**icon**](./boards.md#leadr.boards.api.schemas.BoardCreateRequest.icon) (<code>[str](#str)</code>) –
- [**is_active**](#leadr.boards.api.schemas.BoardCreateRequest.is_active) (<code>[bool](#bool)</code>) –
- [**keep_strategy**](#leadr.boards.api.schemas.BoardCreateRequest.keep_strategy) (<code>[KeepStrategy](./boards.md#leadr.boards.domain.board.KeepStrategy)</code>) –
- [**name**](./boards.md#leadr.boards.api.schemas.BoardCreateRequest.name) (<code>[str](#str)</code>) –
- [**short_code**](#leadr.boards.api.schemas.BoardCreateRequest.short_code) (<code>[str](#str)</code>) –
- [**sort_direction**](#leadr.boards.api.schemas.BoardCreateRequest.sort_direction) (<code>[SortDirection](./boards.md#leadr.boards.domain.board.SortDirection)</code>) –
- [**starts_at**](#leadr.boards.api.schemas.BoardCreateRequest.starts_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**tags**](./boards.md#leadr.boards.api.schemas.BoardCreateRequest.tags) (<code>[list](#list)\[[str](#str)\] | None</code>) –
- [**template_id**](#leadr.boards.api.schemas.BoardCreateRequest.template_id) (<code>[UUID](#uuid.UUID) | None</code>) –
- [**template_name**](#leadr.boards.api.schemas.BoardCreateRequest.template_name) (<code>[str](#str) | None</code>) –
- [**unit**](./boards.md#leadr.boards.api.schemas.BoardCreateRequest.unit) (<code>[str](#str)</code>) –

####### `leadr.boards.api.schemas.BoardCreateRequest.account_id`

```python
account_id: UUID = Field(description='ID of the account this board belongs to')
```

####### `leadr.boards.api.schemas.BoardCreateRequest.ends_at`

```python
ends_at: datetime | None = Field(default=None, description='Optional end time for time-bounded boards (UTC)')
```

####### `leadr.boards.api.schemas.BoardCreateRequest.game_id`

```python
game_id: UUID = Field(description='ID of the game this board belongs to')
```

####### `leadr.boards.api.schemas.BoardCreateRequest.icon`

```python
icon: str = Field(description='Icon identifier for the board')
```

####### `leadr.boards.api.schemas.BoardCreateRequest.is_active`

```python
is_active: bool = Field(description='Whether the board is currently active')
```

####### `leadr.boards.api.schemas.BoardCreateRequest.keep_strategy`

```python
keep_strategy: KeepStrategy = Field(description='Strategy for keeping multiple scores from the same user')
```

####### `leadr.boards.api.schemas.BoardCreateRequest.name`

```python
name: str = Field(description='Name of the board')
```

####### `leadr.boards.api.schemas.BoardCreateRequest.short_code`

```python
short_code: str = Field(description='Globally unique short code for direct sharing')
```

####### `leadr.boards.api.schemas.BoardCreateRequest.sort_direction`

```python
sort_direction: SortDirection = Field(description='Direction to sort scores')
```

####### `leadr.boards.api.schemas.BoardCreateRequest.starts_at`

```python
starts_at: datetime | None = Field(default=None, description='Optional start time for time-bounded boards (UTC)')
```

####### `leadr.boards.api.schemas.BoardCreateRequest.tags`

```python
tags: list[str] | None = Field(default=None, description='Optional list of tags for categorization')
```

####### `leadr.boards.api.schemas.BoardCreateRequest.template_id`

```python
template_id: UUID | None = Field(default=None, description='Optional template ID this board was created from')
```

####### `leadr.boards.api.schemas.BoardCreateRequest.template_name`

```python
template_name: str | None = Field(default=None, description='Optional template name this board was created from')
```

####### `leadr.boards.api.schemas.BoardCreateRequest.unit`

```python
unit: str = Field(description="Unit of measurement for scores (e.g., 'seconds', 'points')")
```

###### `leadr.boards.api.schemas.BoardResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response model for a board.

**Functions:**

- [**from_domain**](#leadr.boards.api.schemas.BoardResponse.from_domain) – Convert domain entity to response model.

**Attributes:**

- [**account_id**](#leadr.boards.api.schemas.BoardResponse.account_id) (<code>[UUID](#uuid.UUID)</code>) –
- [**created_at**](#leadr.boards.api.schemas.BoardResponse.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**ends_at**](#leadr.boards.api.schemas.BoardResponse.ends_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**game_id**](#leadr.boards.api.schemas.BoardResponse.game_id) (<code>[UUID](#uuid.UUID)</code>) –
- [**icon**](./boards.md#leadr.boards.api.schemas.BoardResponse.icon) (<code>[str](#str)</code>) –
- [**id**](./boards.md#leadr.boards.api.schemas.BoardResponse.id) (<code>[UUID](#uuid.UUID)</code>) –
- [**is_active**](#leadr.boards.api.schemas.BoardResponse.is_active) (<code>[bool](#bool)</code>) –
- [**keep_strategy**](#leadr.boards.api.schemas.BoardResponse.keep_strategy) (<code>[KeepStrategy](./boards.md#leadr.boards.domain.board.KeepStrategy)</code>) –
- [**name**](./boards.md#leadr.boards.api.schemas.BoardResponse.name) (<code>[str](#str)</code>) –
- [**short_code**](#leadr.boards.api.schemas.BoardResponse.short_code) (<code>[str](#str)</code>) –
- [**sort_direction**](#leadr.boards.api.schemas.BoardResponse.sort_direction) (<code>[SortDirection](./boards.md#leadr.boards.domain.board.SortDirection)</code>) –
- [**starts_at**](#leadr.boards.api.schemas.BoardResponse.starts_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**tags**](./boards.md#leadr.boards.api.schemas.BoardResponse.tags) (<code>[list](#list)\[[str](#str)\]</code>) –
- [**template_id**](#leadr.boards.api.schemas.BoardResponse.template_id) (<code>[UUID](#uuid.UUID) | None</code>) –
- [**template_name**](#leadr.boards.api.schemas.BoardResponse.template_name) (<code>[str](#str) | None</code>) –
- [**unit**](./boards.md#leadr.boards.api.schemas.BoardResponse.unit) (<code>[str](#str)</code>) –
- [**updated_at**](#leadr.boards.api.schemas.BoardResponse.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.boards.api.schemas.BoardResponse.account_id`

```python
account_id: UUID = Field(description='ID of the account this board belongs to')
```

####### `leadr.boards.api.schemas.BoardResponse.created_at`

```python
created_at: datetime = Field(description='Timestamp when the board was created (UTC)')
```

####### `leadr.boards.api.schemas.BoardResponse.ends_at`

```python
ends_at: datetime | None = Field(default=None, description='End time for time-bounded boards (UTC)')
```

####### `leadr.boards.api.schemas.BoardResponse.from_domain`

```python
from_domain(board)
```

Convert domain entity to response model.

**Parameters:**

- **board** (<code>[Board](./boards.md#leadr.boards.domain.board.Board)</code>) – The domain Board entity to convert.

**Returns:**

- <code>[BoardResponse](./boards.md#leadr.boards.api.schemas.BoardResponse)</code> – BoardResponse with all fields populated from the domain entity.

####### `leadr.boards.api.schemas.BoardResponse.game_id`

```python
game_id: UUID = Field(description='ID of the game this board belongs to')
```

####### `leadr.boards.api.schemas.BoardResponse.icon`

```python
icon: str = Field(description='Icon identifier for the board')
```

####### `leadr.boards.api.schemas.BoardResponse.id`

```python
id: UUID = Field(description='Unique identifier for the board')
```

####### `leadr.boards.api.schemas.BoardResponse.is_active`

```python
is_active: bool = Field(description='Whether the board is currently active')
```

####### `leadr.boards.api.schemas.BoardResponse.keep_strategy`

```python
keep_strategy: KeepStrategy = Field(description='Strategy for keeping scores from same user')
```

####### `leadr.boards.api.schemas.BoardResponse.name`

```python
name: str = Field(description='Name of the board')
```

####### `leadr.boards.api.schemas.BoardResponse.short_code`

```python
short_code: str = Field(description='Globally unique short code for direct sharing')
```

####### `leadr.boards.api.schemas.BoardResponse.sort_direction`

```python
sort_direction: SortDirection = Field(description='Direction to sort scores')
```

####### `leadr.boards.api.schemas.BoardResponse.starts_at`

```python
starts_at: datetime | None = Field(default=None, description='Start time for time-bounded boards (UTC)')
```

####### `leadr.boards.api.schemas.BoardResponse.tags`

```python
tags: list[str] = Field(default_factory=list, description='List of tags for categorization')
```

####### `leadr.boards.api.schemas.BoardResponse.template_id`

```python
template_id: UUID | None = Field(default=None, description='Template ID this board was created from, or null')
```

####### `leadr.boards.api.schemas.BoardResponse.template_name`

```python
template_name: str | None = Field(default=None, description='Template name this board was created from, or null')
```

####### `leadr.boards.api.schemas.BoardResponse.unit`

```python
unit: str = Field(description='Unit of measurement for scores')
```

####### `leadr.boards.api.schemas.BoardResponse.updated_at`

```python
updated_at: datetime = Field(description='Timestamp of last update (UTC)')
```

###### `leadr.boards.api.schemas.BoardUpdateRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request model for updating a board.

**Attributes:**

- [**deleted**](./boards.md#leadr.boards.api.schemas.BoardUpdateRequest.deleted) (<code>[bool](#bool) | None</code>) –
- [**ends_at**](#leadr.boards.api.schemas.BoardUpdateRequest.ends_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**icon**](./boards.md#leadr.boards.api.schemas.BoardUpdateRequest.icon) (<code>[str](#str) | None</code>) –
- [**is_active**](#leadr.boards.api.schemas.BoardUpdateRequest.is_active) (<code>[bool](#bool) | None</code>) –
- [**keep_strategy**](#leadr.boards.api.schemas.BoardUpdateRequest.keep_strategy) (<code>[KeepStrategy](./boards.md#leadr.boards.domain.board.KeepStrategy) | None</code>) –
- [**name**](./boards.md#leadr.boards.api.schemas.BoardUpdateRequest.name) (<code>[str](#str) | None</code>) –
- [**short_code**](#leadr.boards.api.schemas.BoardUpdateRequest.short_code) (<code>[str](#str) | None</code>) –
- [**sort_direction**](#leadr.boards.api.schemas.BoardUpdateRequest.sort_direction) (<code>[SortDirection](./boards.md#leadr.boards.domain.board.SortDirection) | None</code>) –
- [**starts_at**](#leadr.boards.api.schemas.BoardUpdateRequest.starts_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**tags**](./boards.md#leadr.boards.api.schemas.BoardUpdateRequest.tags) (<code>[list](#list)\[[str](#str)\] | None</code>) –
- [**template_id**](#leadr.boards.api.schemas.BoardUpdateRequest.template_id) (<code>[UUID](#uuid.UUID) | None</code>) –
- [**template_name**](#leadr.boards.api.schemas.BoardUpdateRequest.template_name) (<code>[str](#str) | None</code>) –
- [**unit**](./boards.md#leadr.boards.api.schemas.BoardUpdateRequest.unit) (<code>[str](#str) | None</code>) –

####### `leadr.boards.api.schemas.BoardUpdateRequest.deleted`

```python
deleted: bool | None = Field(default=None, description='Set to true to soft delete the board')
```

####### `leadr.boards.api.schemas.BoardUpdateRequest.ends_at`

```python
ends_at: datetime | None = Field(default=None, description='Updated end time')
```

####### `leadr.boards.api.schemas.BoardUpdateRequest.icon`

```python
icon: str | None = Field(default=None, description='Updated icon identifier')
```

####### `leadr.boards.api.schemas.BoardUpdateRequest.is_active`

```python
is_active: bool | None = Field(default=None, description='Updated active status')
```

####### `leadr.boards.api.schemas.BoardUpdateRequest.keep_strategy`

```python
keep_strategy: KeepStrategy | None = Field(default=None, description='Updated keep strategy')
```

####### `leadr.boards.api.schemas.BoardUpdateRequest.name`

```python
name: str | None = Field(default=None, description='Updated board name')
```

####### `leadr.boards.api.schemas.BoardUpdateRequest.short_code`

```python
short_code: str | None = Field(default=None, description='Updated short code')
```

####### `leadr.boards.api.schemas.BoardUpdateRequest.sort_direction`

```python
sort_direction: SortDirection | None = Field(default=None, description='Updated sort direction')
```

####### `leadr.boards.api.schemas.BoardUpdateRequest.starts_at`

```python
starts_at: datetime | None = Field(default=None, description='Updated start time')
```

####### `leadr.boards.api.schemas.BoardUpdateRequest.tags`

```python
tags: list[str] | None = Field(default=None, description='Updated tags list')
```

####### `leadr.boards.api.schemas.BoardUpdateRequest.template_id`

```python
template_id: UUID | None = Field(default=None, description='Updated template ID')
```

####### `leadr.boards.api.schemas.BoardUpdateRequest.template_name`

```python
template_name: str | None = Field(default=None, description='Updated template name')
```

####### `leadr.boards.api.schemas.BoardUpdateRequest.unit`

```python
unit: str | None = Field(default=None, description='Updated unit of measurement')
```

#### `leadr.boards.domain`

**Modules:**

- [**board**](./boards.md#leadr.boards.domain.board) – Board domain model.

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

**Attributes:**

- [**account_id**](#leadr.boards.domain.board.Board.account_id) (<code>[UUID](#uuid.UUID)</code>) –
- [**created_at**](#leadr.boards.domain.board.Board.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**deleted_at**](#leadr.boards.domain.board.Board.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**ends_at**](#leadr.boards.domain.board.Board.ends_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**game_id**](#leadr.boards.domain.board.Board.game_id) (<code>[UUID](#uuid.UUID)</code>) –
- [**icon**](./boards.md#leadr.boards.domain.board.Board.icon) (<code>[str](#str)</code>) –
- [**id**](./boards.md#leadr.boards.domain.board.Board.id) (<code>[UUID](#uuid.UUID)</code>) –
- [**is_active**](#leadr.boards.domain.board.Board.is_active) (<code>[bool](#bool)</code>) –
- [**is_deleted**](#leadr.boards.domain.board.Board.is_deleted) (<code>[bool](#bool)</code>) – Check if entity is soft-deleted.
- [**keep_strategy**](#leadr.boards.domain.board.Board.keep_strategy) (<code>[KeepStrategy](./boards.md#leadr.boards.domain.board.KeepStrategy)</code>) –
- [**model_config**](#leadr.boards.domain.board.Board.model_config) –
- [**name**](./boards.md#leadr.boards.domain.board.Board.name) (<code>[str](#str)</code>) –
- [**short_code**](#leadr.boards.domain.board.Board.short_code) (<code>[str](#str)</code>) –
- [**sort_direction**](#leadr.boards.domain.board.Board.sort_direction) (<code>[SortDirection](./boards.md#leadr.boards.domain.board.SortDirection)</code>) –
- [**starts_at**](#leadr.boards.domain.board.Board.starts_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**tags**](./boards.md#leadr.boards.domain.board.Board.tags) (<code>[list](#list)\[[str](#str)\]</code>) –
- [**template_id**](#leadr.boards.domain.board.Board.template_id) (<code>[UUID](#uuid.UUID) | None</code>) –
- [**template_name**](#leadr.boards.domain.board.Board.template_name) (<code>[str](#str) | None</code>) –
- [**unit**](./boards.md#leadr.boards.domain.board.Board.unit) (<code>[str](#str)</code>) –
- [**updated_at**](#leadr.boards.domain.board.Board.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.boards.domain.board.Board.account_id`

```python
account_id: UUID = Field(frozen=True, description='ID of the account this board belongs to (immutable)')
```

####### `leadr.boards.domain.board.Board.created_at`

```python
created_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp when entity was created (UTC)')
```

####### `leadr.boards.domain.board.Board.deleted_at`

```python
deleted_at: datetime | None = Field(default=None, description='Timestamp when entity was soft-deleted (UTC), or null if active')
```

####### `leadr.boards.domain.board.Board.ends_at`

```python
ends_at: datetime | None = Field(default=None, description='Optional end time for time-bounded boards')
```

####### `leadr.boards.domain.board.Board.game_id`

```python
game_id: UUID = Field(frozen=True, description='ID of the game this board belongs to (immutable)')
```

####### `leadr.boards.domain.board.Board.icon`

```python
icon: str = Field(description='Icon identifier for the board')
```

####### `leadr.boards.domain.board.Board.id`

```python
id: UUID = Field(frozen=True, default_factory=uuid4, description='Unique identifier (auto-generated UUID)')
```

####### `leadr.boards.domain.board.Board.is_active`

```python
is_active: bool = Field(description='Whether the board is currently active')
```

####### `leadr.boards.domain.board.Board.is_deleted`

```python
is_deleted: bool
```

Check if entity is soft-deleted.

**Returns:**

- <code>[bool](#bool)</code> – True if the entity has a deleted_at timestamp, False otherwise.

####### `leadr.boards.domain.board.Board.keep_strategy`

```python
keep_strategy: KeepStrategy = Field(description='Strategy for keeping multiple scores from the same user')
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
sort_direction: SortDirection = Field(description='Direction to sort scores (ascending/descending)')
```

####### `leadr.boards.domain.board.Board.starts_at`

```python
starts_at: datetime | None = Field(default=None, description='Optional start time for time-bounded boards')
```

####### `leadr.boards.domain.board.Board.tags`

```python
tags: list[str] = Field(default_factory=list, description='List of tags for categorizing the board')
```

####### `leadr.boards.domain.board.Board.template_id`

```python
template_id: UUID | None = Field(default=None, description='Optional template ID this board was created from')
```

####### `leadr.boards.domain.board.Board.template_name`

```python
template_name: str | None = Field(default=None, description='Optional name of the template this board was created from')
```

####### `leadr.boards.domain.board.Board.unit`

```python
unit: str = Field(description="Unit of measurement for scores (e.g., 'seconds', 'points')")
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

###### `leadr.boards.domain.board.KeepStrategy`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Strategy for keeping scores from the same user.

**Attributes:**

- [**ALL**](./boards.md#leadr.boards.domain.board.KeepStrategy.ALL) –
- [**BEST_ONLY**](#leadr.boards.domain.board.KeepStrategy.BEST_ONLY) –
- [**LATEST_ONLY**](#leadr.boards.domain.board.KeepStrategy.LATEST_ONLY) –

####### `leadr.boards.domain.board.KeepStrategy.ALL`

```python
ALL = 'ALL'
```

####### `leadr.boards.domain.board.KeepStrategy.BEST_ONLY`

```python
BEST_ONLY = 'BEST_ONLY'
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

#### `leadr.boards.services`

**Modules:**

- [**board_service**](#leadr.boards.services.board_service) – Board service for managing board operations.
- [**dependencies**](./boards.md#leadr.boards.services.dependencies) – Board service dependency injection.
- [**repositories**](./boards.md#leadr.boards.services.repositories) – Board repository services.

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
- [**delete**](#leadr.boards.services.board_service.BoardService.delete) – Soft-delete an entity.
- [**get_board**](#leadr.boards.services.board_service.BoardService.get_board) – Get a board by its ID.
- [**get_board_by_short_code**](#leadr.boards.services.board_service.BoardService.get_board_by_short_code) – Get a board by its short_code.
- [**get_by_id**](#leadr.boards.services.board_service.BoardService.get_by_id) – Get an entity by its ID.
- [**get_by_id_or_raise**](#leadr.boards.services.board_service.BoardService.get_by_id_or_raise) – Get an entity by its ID or raise EntityNotFoundError.
- [**list_all**](#leadr.boards.services.board_service.BoardService.list_all) – List all non-deleted entities.
- [**list_boards_by_account**](#leadr.boards.services.board_service.BoardService.list_boards_by_account) – List all boards for an account.
- [**soft_delete**](#leadr.boards.services.board_service.BoardService.soft_delete) – Soft-delete an entity and return it before deletion.
- [**update_board**](#leadr.boards.services.board_service.BoardService.update_board) – Update board fields.

**Attributes:**

- [**repository**](#leadr.boards.services.board_service.BoardService.repository) –

####### `leadr.boards.services.board_service.BoardService.create_board`

```python
create_board(account_id, game_id, name, icon, short_code, unit, is_active, sort_direction, keep_strategy, template_id=None, template_name=None, starts_at=None, ends_at=None, tags=None)
```

Create a new board.

**Parameters:**

- **account_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the account that owns this board.
- **game_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the game this board belongs to.
- **name** (<code>[str](#str)</code>) – The board name.
- **icon** (<code>[str](#str)</code>) – Icon identifier for the board.
- **short_code** (<code>[str](#str)</code>) – Globally unique short code for direct sharing.
- **unit** (<code>[str](#str)</code>) – Unit of measurement for scores.
- **is_active** (<code>[bool](#bool)</code>) – Whether the board is currently active.
- **sort_direction** (<code>[SortDirection](./boards.md#leadr.boards.domain.board.SortDirection)</code>) – Direction to sort scores.
- **keep_strategy** (<code>[KeepStrategy](./boards.md#leadr.boards.domain.board.KeepStrategy)</code>) – Strategy for keeping multiple scores from same user.
- **template_id** (<code>[UUID](#uuid.UUID) | None</code>) – Optional template ID this board was created from.
- **template_name** (<code>[str](#str) | None</code>) – Optional template name.
- **starts_at** (<code>[datetime](#datetime.datetime) | None</code>) – Optional start time for time-bounded boards.
- **ends_at** (<code>[datetime](#datetime.datetime) | None</code>) – Optional end time for time-bounded boards.
- **tags** (<code>[list](#list)\[[str](#str)\] | None</code>) – Optional list of tags for categorization.

**Returns:**

- <code>[Board](./boards.md#leadr.boards.domain.board.Board)</code> – The created Board domain entity.

**Raises:**

- <code>[EntityNotFoundError](#EntityNotFoundError)</code> – If the game doesn't exist.
- <code>[ValueError](#ValueError)</code> – If the game doesn't belong to the specified account.

<details class="example" open markdown="1">
<summary>Example</summary>

> > > board = await service.create_board(
> > > ... account_id=account.id,
> > > ... game_id=game.id,
> > > ... name="Speed Run Board",
> > > ... icon="trophy",
> > > ... short_code="SR2025",
> > > ... unit="seconds",
> > > ... is_active=True,
> > > ... sort_direction=SortDirection.ASCENDING,
> > > ... keep_strategy=KeepStrategy.BEST_ONLY,
> > > ... )

</details>

####### `leadr.boards.services.board_service.BoardService.delete`

```python
delete(entity_id)
```

Soft-delete an entity.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the entity doesn't exist

####### `leadr.boards.services.board_service.BoardService.get_board`

```python
get_board(board_id)
```

Get a board by its ID.

**Parameters:**

- **board_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the board to retrieve.

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

- **entity_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the entity to retrieve

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.services.DomainEntityT) | None</code> – The domain entity if found, None otherwise

####### `leadr.boards.services.board_service.BoardService.get_by_id_or_raise`

```python
get_by_id_or_raise(entity_id)
```

Get an entity by its ID or raise EntityNotFoundError.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the entity to retrieve

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

####### `leadr.boards.services.board_service.BoardService.list_boards_by_account`

```python
list_boards_by_account(account_id)
```

List all boards for an account.

**Parameters:**

- **account_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the account to list boards for.

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

- **entity_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the entity to delete

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.services.DomainEntityT)</code> – The entity before it was deleted

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the entity doesn't exist

####### `leadr.boards.services.board_service.BoardService.update_board`

```python
update_board(board_id, name=None, icon=None, short_code=None, unit=None, is_active=None, sort_direction=None, keep_strategy=None, template_id=None, template_name=None, starts_at=None, ends_at=None, tags=None)
```

Update board fields.

**Parameters:**

- **board_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the board to update
- **name** (<code>[str](#str) | None</code>) – New board name, if provided
- **icon** (<code>[str](#str) | None</code>) – New icon, if provided
- **short_code** (<code>[str](#str) | None</code>) – New short_code, if provided
- **unit** (<code>[str](#str) | None</code>) – New unit, if provided
- **is_active** (<code>[bool](#bool) | None</code>) – New is_active status, if provided
- **sort_direction** (<code>[SortDirection](./boards.md#leadr.boards.domain.board.SortDirection) | None</code>) – New sort_direction, if provided
- **keep_strategy** (<code>[KeepStrategy](./boards.md#leadr.boards.domain.board.KeepStrategy) | None</code>) – New keep_strategy, if provided
- **template_id** (<code>[UUID](#uuid.UUID) | None</code>) – New template_id, if provided
- **template_name** (<code>[str](#str) | None</code>) – New template_name, if provided
- **starts_at** (<code>[datetime](#datetime.datetime) | None</code>) – New starts_at, if provided
- **ends_at** (<code>[datetime](#datetime.datetime) | None</code>) – New ends_at, if provided
- **tags** (<code>[list](#list)\[[str](#str)\] | None</code>) – New tags list, if provided

**Returns:**

- <code>[Board](./boards.md#leadr.boards.domain.board.Board)</code> – The updated Board domain entity

**Raises:**

- <code>[EntityNotFoundError](#EntityNotFoundError)</code> – If the board doesn't exist

##### `leadr.boards.services.dependencies`

Board service dependency injection.

**Functions:**

- [**get_board_service**](#leadr.boards.services.dependencies.get_board_service) – Get BoardService dependency.

**Attributes:**

- [**BoardServiceDep**](./boards.md#leadr.boards.services.dependencies.BoardServiceDep) –

###### `leadr.boards.services.dependencies.BoardServiceDep`

```python
BoardServiceDep = Annotated[BoardService, Depends(get_board_service)]
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

##### `leadr.boards.services.repositories`

Board repository services.

**Classes:**

- [**BoardRepository**](./boards.md#leadr.boards.services.repositories.BoardRepository) – Board repository for managing board persistence.

###### `leadr.boards.services.repositories.BoardRepository`

Bases: <code>[BaseRepository](./common.md#leadr.common.repositories.BaseRepository)\[[Board](./boards.md#leadr.boards.domain.board.Board), [BoardORM](./boards.md#leadr.boards.adapters.orm.BoardORM)\]</code>

Board repository for managing board persistence.

**Functions:**

- [**create**](./boards.md#leadr.boards.services.repositories.BoardRepository.create) – Create a new entity in the database.
- [**delete**](./boards.md#leadr.boards.services.repositories.BoardRepository.delete) – Soft delete an entity by setting its deleted_at timestamp.
- [**filter**](./boards.md#leadr.boards.services.repositories.BoardRepository.filter) – Filter boards by account and optional criteria.
- [**get_by_id**](#leadr.boards.services.repositories.BoardRepository.get_by_id) – Get an entity by its ID.
- [**get_by_short_code**](#leadr.boards.services.repositories.BoardRepository.get_by_short_code) – Get board by short_code.
- [**update**](./boards.md#leadr.boards.services.repositories.BoardRepository.update) – Update an existing entity in the database.

**Attributes:**

- [**session**](./boards.md#leadr.boards.services.repositories.BoardRepository.session) –

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

- **entity_id** (<code>[UUID4](#pydantic.UUID4)</code>) – ID of entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

####### `leadr.boards.services.repositories.BoardRepository.filter`

```python
filter(account_id, **kwargs)
```

Filter boards by account and optional criteria.

**Parameters:**

- **account_id** (<code>[UUID4](#pydantic.UUID4)</code>) – REQUIRED - Account ID to filter by (multi-tenant safety)
- \*\***kwargs** (<code>[Any](#typing.Any)</code>) – Additional filter parameters (reserved for future use)

**Returns:**

- <code>[list](#list)\[[Board](./boards.md#leadr.boards.domain.board.Board)\]</code> – List of boards for the account matching the filter criteria

####### `leadr.boards.services.repositories.BoardRepository.get_by_id`

```python
get_by_id(entity_id, include_deleted=False)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4)</code>) – Entity ID to retrieve
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
