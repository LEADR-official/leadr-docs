### `leadr.common`

**Modules:**

- [**api**](./common.md#leadr.common.api) – API utilities and exception handlers.
- [**database**](./common.md#leadr.common.database) – Database connection and session management.
- [**dependencies**](./common.md#leadr.common.dependencies) – Shared FastAPI dependencies for the application.
- [**domain**](./common.md#leadr.common.domain) –
- [**orm**](./common.md#leadr.common.orm) – Common ORM base classes and utilities.
- [**repositories**](./common.md#leadr.common.repositories) – Base repository abstraction for common CRUD operations.
- [**services**](./common.md#leadr.common.services) – Base service abstraction for common business logic patterns.

#### `leadr.common.api`

API utilities and exception handlers.

**Modules:**

- [**exceptions**](./common.md#leadr.common.api.exceptions) – Global exception handlers for API layer.

##### `leadr.common.api.exceptions`

Global exception handlers for API layer.

**Functions:**

- [**entity_not_found_handler**](#leadr.common.api.exceptions.entity_not_found_handler) – Convert EntityNotFoundError to 404 HTTP response.

###### `leadr.common.api.exceptions.entity_not_found_handler`

```python
entity_not_found_handler(request, exc)
```

Convert EntityNotFoundError to 404 HTTP response.

**Parameters:**

- **request** (<code>[Request](#fastapi.Request)</code>) – The incoming request
- **exc** (<code>[Exception](#Exception)</code>) – The domain exception

**Returns:**

- <code>[JSONResponse](#fastapi.responses.JSONResponse)</code> – JSONResponse with 404 status and error detail

#### `leadr.common.database`

Database connection and session management.

**Functions:**

- [**build_database_url**](#leadr.common.database.build_database_url) – Build async database URL from settings.
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

##### `leadr.common.database.engine`

```python
engine = create_async_engine(build_database_url(), pool_size=(settings.DB_POOL_SIZE), max_overflow=(settings.DB_POOL_MAX_OVERFLOW), pool_recycle=(settings.DB_POOL_RECYCLE), pool_pre_ping=True, echo=(settings.DB_ECHO))
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

- [**exceptions**](./common.md#leadr.common.domain.exceptions) – Domain-specific exceptions for LEADR.
- [**models**](./common.md#leadr.common.domain.models) – Common domain models and value objects.

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

##### `leadr.common.domain.models`

Common domain models and value objects.

**Classes:**

- [**Entity**](./common.md#leadr.common.domain.models.Entity) – Base class for all domain entities with ID and timestamps.

###### `leadr.common.domain.models.Entity`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Base class for all domain entities with ID and timestamps.

Provides common functionality for domain entities including:

- Auto-generated UUID primary key
- Created/updated timestamps (UTC)
- Soft delete support with deleted_at timestamp
- Equality and hashing based on ID

All domain entities should extend this base class. The ID and timestamps
are automatically populated on entity creation and don't need to be
provided by consumers.

**Functions:**

- [**restore**](./common.md#leadr.common.domain.models.Entity.restore) – Restore a soft-deleted entity.
- [**soft_delete**](#leadr.common.domain.models.Entity.soft_delete) – Mark entity as soft-deleted.

**Attributes:**

- [**created_at**](#leadr.common.domain.models.Entity.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**deleted_at**](#leadr.common.domain.models.Entity.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**id**](./common.md#leadr.common.domain.models.Entity.id) (<code>[UUID](#uuid.UUID)</code>) –
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
id: UUID = Field(frozen=True, default_factory=uuid4, description='Unique identifier (auto-generated UUID)')
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
- [**filter**](./common.md#leadr.common.repositories.BaseRepository.filter) – Filter entities based on criteria.
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

- **entity_id** (<code>[UUID4](#pydantic.UUID4)</code>) – ID of entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

###### `leadr.common.repositories.BaseRepository.filter`

```python
filter(account_id, **kwargs)
```

Filter entities based on criteria.

For multi-tenant entities, implementations MUST override this to make
account_id required (no default). For top-level entities like Account,
account_id can remain optional and unused.

**Parameters:**

- **account_id** (<code>[UUID4](#pydantic.UUID4)</code>) – Optional account ID for filtering. Multi-tenant entities
  MUST override to make this required (account_id: UUID).
- \*\***kwargs** (<code>[Any](#typing.Any)</code>) – Additional filter parameters specific to the entity type.

**Returns:**

- <code>[list](#list)\[[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)\]</code> – List of domain entities matching the filter criteria

Example (multi-tenant - account_id required):
async def filter(
self,
account_id: UUID, # Required, no default
status: str | None = None,
\*\*kwargs
) -> list\[User\]:
\# Implementation with account_id required

Example (top-level tenant - account_id optional/unused):
async def filter(
self,
account_id: UUID | None = None, # Optional, unused
status: str | None = None,
\*\*kwargs
) -> list\[Account\]:
\# Implementation where account_id is not used

###### `leadr.common.repositories.BaseRepository.get_by_id`

```python
get_by_id(entity_id, include_deleted=False)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4)</code>) – Entity ID to retrieve
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

- **entity_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the entity doesn't exist

###### `leadr.common.services.BaseService.get_by_id`

```python
get_by_id(entity_id)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the entity to retrieve

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.services.DomainEntityT) | None</code> – The domain entity if found, None otherwise

###### `leadr.common.services.BaseService.get_by_id_or_raise`

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

- **entity_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the entity to delete

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
