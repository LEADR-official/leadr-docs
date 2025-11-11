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
- [**created_at**](#leadr.games.adapters.orm.GameORM.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**default_board_id**](#leadr.games.adapters.orm.GameORM.default_board_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID) | None\]</code>) –
- [**deleted_at**](#leadr.games.adapters.orm.GameORM.deleted_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[nullable_timestamp](#leadr.common.orm.nullable_timestamp)\]</code>) –
- [**id**](./games.md#leadr.games.adapters.orm.GameORM.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**name**](./games.md#leadr.games.adapters.orm.GameORM.name) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**steam_app_id**](#leadr.games.adapters.orm.GameORM.steam_app_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**updated_at**](#leadr.games.adapters.orm.GameORM.updated_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –

####### `leadr.games.adapters.orm.GameORM.account`

```python
account: Mapped[AccountORM] = relationship('AccountORM')
```

####### `leadr.games.adapters.orm.GameORM.account_id`

```python
account_id: Mapped[UUID] = mapped_column(ForeignKey('accounts.id', ondelete='CASCADE'), nullable=False, index=True)
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

####### `leadr.games.adapters.orm.GameORM.id`

```python
id: Mapped[uuid_pk]
```

####### `leadr.games.adapters.orm.GameORM.name`

```python
name: Mapped[str] = mapped_column(String, nullable=False)
```

####### `leadr.games.adapters.orm.GameORM.steam_app_id`

```python
steam_app_id: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
```

####### `leadr.games.adapters.orm.GameORM.updated_at`

```python
updated_at: Mapped[timestamp] = mapped_column(onupdate=(func.now()))
```

#### `leadr.games.api`

**Modules:**

- [**routes**](./games.md#leadr.games.api.routes) – Game API routes.
- [**schemas**](./games.md#leadr.games.api.schemas) – API request and response models for games.

##### `leadr.games.api.routes`

Game API routes.

**Functions:**

- [**create_game**](#leadr.games.api.routes.create_game) – Create a new game.
- [**get_game**](#leadr.games.api.routes.get_game) – Get a game by ID.
- [**list_games**](#leadr.games.api.routes.list_games) – List all games for an account.
- [**update_game**](#leadr.games.api.routes.update_game) – Update a game.

**Attributes:**

- [**router**](./games.md#leadr.games.api.routes.router) –

###### `leadr.games.api.routes.create_game`

```python
create_game(request, service)
```

Create a new game.

Creates a new game associated with an existing account. Games can optionally
be configured with Steam integration and a default leaderboard.

**Parameters:**

- **request** (<code>[GameCreateRequest](./games.md#leadr.games.api.schemas.GameCreateRequest)</code>) – Game creation details including account_id, name, and optional settings.
- **service** (<code>[GameServiceDep](./games.md#leadr.games.services.dependencies.GameServiceDep)</code>) – Injected game service dependency.

**Returns:**

- <code>[GameResponse](./games.md#leadr.games.api.schemas.GameResponse)</code> – GameResponse with the created game including auto-generated ID and timestamps.

**Raises:**

- <code>404</code> – Account not found.

###### `leadr.games.api.routes.get_game`

```python
get_game(game_id, service)
```

Get a game by ID.

**Parameters:**

- **game_id** (<code>[UUID](#uuid.UUID)</code>) – Unique identifier for the game.
- **service** (<code>[GameServiceDep](./games.md#leadr.games.services.dependencies.GameServiceDep)</code>) – Injected game service dependency.

**Returns:**

- <code>[GameResponse](./games.md#leadr.games.api.schemas.GameResponse)</code> – GameResponse with full game details.

**Raises:**

- <code>404</code> – Game not found.

###### `leadr.games.api.routes.list_games`

```python
list_games(account_id, service)
```

List all games for an account.

**Parameters:**

- **account_id** (<code>[UUID](#uuid.UUID)</code>) – Account ID to filter games by.
- **service** (<code>[GameServiceDep](./games.md#leadr.games.services.dependencies.GameServiceDep)</code>) – Injected game service dependency.

**Returns:**

- <code>[list](#list)\[[GameResponse](./games.md#leadr.games.api.schemas.GameResponse)\]</code> – List of all active games for the specified account.

###### `leadr.games.api.routes.router`

```python
router = APIRouter()
```

###### `leadr.games.api.routes.update_game`

```python
update_game(game_id, request, service)
```

Update a game.

Supports updating name, Steam App ID, default board ID, or soft-deleting the game.

**Parameters:**

- **game_id** (<code>[UUID](#uuid.UUID)</code>) – Unique identifier for the game.
- **request** (<code>[GameUpdateRequest](./games.md#leadr.games.api.schemas.GameUpdateRequest)</code>) – Game update details (all fields optional).
- **service** (<code>[GameServiceDep](./games.md#leadr.games.services.dependencies.GameServiceDep)</code>) – Injected game service dependency.

**Returns:**

- <code>[GameResponse](./games.md#leadr.games.api.schemas.GameResponse)</code> – GameResponse with the updated game details.

**Raises:**

- <code>404</code> – Game not found.

##### `leadr.games.api.schemas`

API request and response models for games.

**Classes:**

- [**GameCreateRequest**](./games.md#leadr.games.api.schemas.GameCreateRequest) – Request model for creating a game.
- [**GameResponse**](./games.md#leadr.games.api.schemas.GameResponse) – Response model for a game.
- [**GameUpdateRequest**](./games.md#leadr.games.api.schemas.GameUpdateRequest) – Request model for updating a game.

###### `leadr.games.api.schemas.GameCreateRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request model for creating a game.

**Attributes:**

- [**account_id**](#leadr.games.api.schemas.GameCreateRequest.account_id) (<code>[UUID](#uuid.UUID)</code>) –
- [**default_board_id**](#leadr.games.api.schemas.GameCreateRequest.default_board_id) (<code>[UUID](#uuid.UUID) | None</code>) –
- [**name**](./games.md#leadr.games.api.schemas.GameCreateRequest.name) (<code>[str](#str)</code>) –
- [**steam_app_id**](#leadr.games.api.schemas.GameCreateRequest.steam_app_id) (<code>[str](#str) | None</code>) –

####### `leadr.games.api.schemas.GameCreateRequest.account_id`

```python
account_id: UUID = Field(description='ID of the account this game belongs to')
```

####### `leadr.games.api.schemas.GameCreateRequest.default_board_id`

```python
default_board_id: UUID | None = Field(default=None, description='Optional ID of the default leaderboard for this game')
```

####### `leadr.games.api.schemas.GameCreateRequest.name`

```python
name: str = Field(description='Name of the game')
```

####### `leadr.games.api.schemas.GameCreateRequest.steam_app_id`

```python
steam_app_id: str | None = Field(default=None, description='Optional Steam App ID for Steam integration')
```

###### `leadr.games.api.schemas.GameResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response model for a game.

**Functions:**

- [**from_domain**](#leadr.games.api.schemas.GameResponse.from_domain) – Convert domain entity to response model.

**Attributes:**

- [**account_id**](#leadr.games.api.schemas.GameResponse.account_id) (<code>[UUID](#uuid.UUID)</code>) –
- [**created_at**](#leadr.games.api.schemas.GameResponse.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**default_board_id**](#leadr.games.api.schemas.GameResponse.default_board_id) (<code>[UUID](#uuid.UUID) | None</code>) –
- [**id**](./games.md#leadr.games.api.schemas.GameResponse.id) (<code>[UUID](#uuid.UUID)</code>) –
- [**name**](./games.md#leadr.games.api.schemas.GameResponse.name) (<code>[str](#str)</code>) –
- [**steam_app_id**](#leadr.games.api.schemas.GameResponse.steam_app_id) (<code>[str](#str) | None</code>) –
- [**updated_at**](#leadr.games.api.schemas.GameResponse.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.games.api.schemas.GameResponse.account_id`

```python
account_id: UUID = Field(description='ID of the account this game belongs to')
```

####### `leadr.games.api.schemas.GameResponse.created_at`

```python
created_at: datetime = Field(description='Timestamp when the game was created (UTC)')
```

####### `leadr.games.api.schemas.GameResponse.default_board_id`

```python
default_board_id: UUID | None = Field(default=None, description='ID of the default leaderboard, or null if not set')
```

####### `leadr.games.api.schemas.GameResponse.from_domain`

```python
from_domain(game)
```

Convert domain entity to response model.

**Parameters:**

- **game** (<code>[Game](./games.md#leadr.games.domain.game.Game)</code>) – The domain Game entity to convert.

**Returns:**

- <code>[GameResponse](./games.md#leadr.games.api.schemas.GameResponse)</code> – GameResponse with all fields populated from the domain entity.

####### `leadr.games.api.schemas.GameResponse.id`

```python
id: UUID = Field(description='Unique identifier for the game')
```

####### `leadr.games.api.schemas.GameResponse.name`

```python
name: str = Field(description='Name of the game')
```

####### `leadr.games.api.schemas.GameResponse.steam_app_id`

```python
steam_app_id: str | None = Field(default=None, description='Steam App ID if Steam integration is configured')
```

####### `leadr.games.api.schemas.GameResponse.updated_at`

```python
updated_at: datetime = Field(description='Timestamp of last update (UTC)')
```

###### `leadr.games.api.schemas.GameUpdateRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request model for updating a game.

**Attributes:**

- [**default_board_id**](#leadr.games.api.schemas.GameUpdateRequest.default_board_id) (<code>[UUID](#uuid.UUID) | None</code>) –
- [**deleted**](./games.md#leadr.games.api.schemas.GameUpdateRequest.deleted) (<code>[bool](#bool) | None</code>) –
- [**name**](./games.md#leadr.games.api.schemas.GameUpdateRequest.name) (<code>[str](#str) | None</code>) –
- [**steam_app_id**](#leadr.games.api.schemas.GameUpdateRequest.steam_app_id) (<code>[str](#str) | None</code>) –

####### `leadr.games.api.schemas.GameUpdateRequest.default_board_id`

```python
default_board_id: UUID | None = Field(default=None, description='Updated default leaderboard ID')
```

####### `leadr.games.api.schemas.GameUpdateRequest.deleted`

```python
deleted: bool | None = Field(default=None, description='Set to true to soft delete the game')
```

####### `leadr.games.api.schemas.GameUpdateRequest.name`

```python
name: str | None = Field(default=None, description='Updated game name')
```

####### `leadr.games.api.schemas.GameUpdateRequest.steam_app_id`

```python
steam_app_id: str | None = Field(default=None, description='Updated Steam App ID')
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

**Attributes:**

- [**account_id**](#leadr.games.domain.game.Game.account_id) (<code>[UUID](#uuid.UUID)</code>) –
- [**created_at**](#leadr.games.domain.game.Game.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**default_board_id**](#leadr.games.domain.game.Game.default_board_id) (<code>[UUID](#uuid.UUID) | None</code>) –
- [**deleted_at**](#leadr.games.domain.game.Game.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**id**](./games.md#leadr.games.domain.game.Game.id) (<code>[UUID](#uuid.UUID)</code>) –
- [**is_deleted**](#leadr.games.domain.game.Game.is_deleted) (<code>[bool](#bool)</code>) – Check if entity is soft-deleted.
- [**model_config**](#leadr.games.domain.game.Game.model_config) –
- [**name**](./games.md#leadr.games.domain.game.Game.name) (<code>[str](#str)</code>) –
- [**steam_app_id**](#leadr.games.domain.game.Game.steam_app_id) (<code>[str](#str) | None</code>) –
- [**updated_at**](#leadr.games.domain.game.Game.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.games.domain.game.Game.account_id`

```python
account_id: UUID = Field(frozen=True, description='ID of the account this game belongs to (immutable)')
```

####### `leadr.games.domain.game.Game.created_at`

```python
created_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp when entity was created (UTC)')
```

####### `leadr.games.domain.game.Game.default_board_id`

```python
default_board_id: UUID | None = Field(default=None, description='Optional default leaderboard ID for this game')
```

####### `leadr.games.domain.game.Game.deleted_at`

```python
deleted_at: datetime | None = Field(default=None, description='Timestamp when entity was soft-deleted (UTC), or null if active')
```

####### `leadr.games.domain.game.Game.id`

```python
id: UUID = Field(frozen=True, default_factory=uuid4, description='Unique identifier (auto-generated UUID)')
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
- [**list_all**](#leadr.games.services.game_service.GameService.list_all) – List all non-deleted entities.
- [**list_games**](#leadr.games.services.game_service.GameService.list_games) – List all games for an account.
- [**soft_delete**](#leadr.games.services.game_service.GameService.soft_delete) – Soft-delete an entity and return it before deletion.
- [**update_game**](#leadr.games.services.game_service.GameService.update_game) – Update game fields.

**Attributes:**

- [**repository**](#leadr.games.services.game_service.GameService.repository) –

####### `leadr.games.services.game_service.GameService.create_game`

```python
create_game(account_id, name, steam_app_id=None, default_board_id=None)
```

Create a new game.

**Parameters:**

- **account_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the account that owns this game.
- **name** (<code>[str](#str)</code>) – The game name.
- **steam_app_id** (<code>[str](#str) | None</code>) – Optional Steam application ID.
- **default_board_id** (<code>[UUID](#uuid.UUID) | None</code>) – Optional default leaderboard ID.

**Returns:**

- <code>[Game](./games.md#leadr.games.domain.game.Game)</code> – The created Game domain entity.

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

- **entity_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the entity doesn't exist

####### `leadr.games.services.game_service.GameService.get_by_id`

```python
get_by_id(entity_id)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the entity to retrieve

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.services.DomainEntityT) | None</code> – The domain entity if found, None otherwise

####### `leadr.games.services.game_service.GameService.get_by_id_or_raise`

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

####### `leadr.games.services.game_service.GameService.get_game`

```python
get_game(game_id)
```

Get a game by its ID.

**Parameters:**

- **game_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the game to retrieve.

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
list_games(account_id)
```

List all games for an account.

**Parameters:**

- **account_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the account to list games for.

**Returns:**

- <code>[list](#list)\[[Game](./games.md#leadr.games.domain.game.Game)\]</code> – List of Game domain entities for the account.

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

- **entity_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the entity to delete

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.services.DomainEntityT)</code> – The entity before it was deleted

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the entity doesn't exist

####### `leadr.games.services.game_service.GameService.update_game`

```python
update_game(game_id, name=None, steam_app_id=None, default_board_id=None)
```

Update game fields.

**Parameters:**

- **game_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the game to update
- **name** (<code>[str](#str) | None</code>) – New game name, if provided
- **steam_app_id** (<code>[str](#str) | None</code>) – New Steam app ID, if provided
- **default_board_id** (<code>[UUID](#uuid.UUID) | None</code>) – New default board ID, if provided

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
- [**update**](./games.md#leadr.games.services.repositories.GameRepository.update) – Update an existing entity in the database.

**Attributes:**

- [**session**](./games.md#leadr.games.services.repositories.GameRepository.session) –

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

- **entity_id** (<code>[UUID4](#pydantic.UUID4)</code>) – ID of entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

####### `leadr.games.services.repositories.GameRepository.filter`

```python
filter(account_id, **kwargs)
```

Filter games by account and optional criteria.

**Parameters:**

- **account_id** (<code>[UUID4](#pydantic.UUID4)</code>) – REQUIRED - Account ID to filter by (multi-tenant safety)
- \*\***kwargs** (<code>[Any](#typing.Any)</code>) – Additional filter parameters (reserved for future use)

**Returns:**

- <code>[list](#list)\[[Game](./games.md#leadr.games.domain.game.Game)\]</code> – List of games for the account matching the filter criteria

####### `leadr.games.services.repositories.GameRepository.get_by_id`

```python
get_by_id(entity_id, include_deleted=False)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4)</code>) – Entity ID to retrieve
- **include_deleted** (<code>[bool](#bool)</code>) – If True, include soft-deleted entities. Defaults to False.

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT) | None</code> – Domain entity if found, None otherwise

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
