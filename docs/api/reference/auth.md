### `leadr.auth`

**Modules:**

- [**adapters**](./auth.md#leadr.auth.adapters) –
- [**api**](./auth.md#leadr.auth.api) –
- [**dependencies**](./auth.md#leadr.auth.dependencies) – Authentication dependencies for FastAPI.
- [**domain**](./auth.md#leadr.auth.domain) –
- [**services**](./auth.md#leadr.auth.services) –

#### `leadr.auth.adapters`

**Modules:**

- [**orm**](./auth.md#leadr.auth.adapters.orm) – API Key ORM models.

##### `leadr.auth.adapters.orm`

API Key ORM models.

**Classes:**

- [**APIKeyORM**](./auth.md#leadr.auth.adapters.orm.APIKeyORM) – API Key ORM model.
- [**APIKeyStatusEnum**](./auth.md#leadr.auth.adapters.orm.APIKeyStatusEnum) – API Key status enum for database.

###### `leadr.auth.adapters.orm.APIKeyORM`

Bases: <code>[Base](./common.md#leadr.common.orm.Base)</code>

API Key ORM model.

Represents an API key for account authentication in the database.
Maps to the api_keys table with foreign key to accounts.

**Attributes:**

- [**account_id**](#leadr.auth.adapters.orm.APIKeyORM.account_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**created_at**](#leadr.auth.adapters.orm.APIKeyORM.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**deleted_at**](#leadr.auth.adapters.orm.APIKeyORM.deleted_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[nullable_timestamp](#leadr.common.orm.nullable_timestamp)\]</code>) –
- [**expires_at**](#leadr.auth.adapters.orm.APIKeyORM.expires_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime) | None\]</code>) –
- [**id**](./auth.md#leadr.auth.adapters.orm.APIKeyORM.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**key_hash**](#leadr.auth.adapters.orm.APIKeyORM.key_hash) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**key_prefix**](#leadr.auth.adapters.orm.APIKeyORM.key_prefix) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**last_used_at**](#leadr.auth.adapters.orm.APIKeyORM.last_used_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime) | None\]</code>) –
- [**name**](./auth.md#leadr.auth.adapters.orm.APIKeyORM.name) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**status**](./auth.md#leadr.auth.adapters.orm.APIKeyORM.status) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[APIKeyStatusEnum](./auth.md#leadr.auth.adapters.orm.APIKeyStatusEnum)\]</code>) –
- [**updated_at**](#leadr.auth.adapters.orm.APIKeyORM.updated_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –

####### `leadr.auth.adapters.orm.APIKeyORM.account_id`

```python
account_id: Mapped[UUID] = mapped_column(ForeignKey('accounts.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.auth.adapters.orm.APIKeyORM.created_at`

```python
created_at: Mapped[timestamp]
```

####### `leadr.auth.adapters.orm.APIKeyORM.deleted_at`

```python
deleted_at: Mapped[nullable_timestamp]
```

####### `leadr.auth.adapters.orm.APIKeyORM.expires_at`

```python
expires_at: Mapped[datetime | None] = mapped_column(DateTime(timezone=True), nullable=True)
```

####### `leadr.auth.adapters.orm.APIKeyORM.id`

```python
id: Mapped[uuid_pk]
```

####### `leadr.auth.adapters.orm.APIKeyORM.key_hash`

```python
key_hash: Mapped[str] = mapped_column(String, nullable=False)
```

####### `leadr.auth.adapters.orm.APIKeyORM.key_prefix`

```python
key_prefix: Mapped[str] = mapped_column(String, nullable=False, unique=True, index=True)
```

####### `leadr.auth.adapters.orm.APIKeyORM.last_used_at`

```python
last_used_at: Mapped[datetime | None] = mapped_column(DateTime(timezone=True), nullable=True)
```

####### `leadr.auth.adapters.orm.APIKeyORM.name`

```python
name: Mapped[str] = mapped_column(String, nullable=False)
```

####### `leadr.auth.adapters.orm.APIKeyORM.status`

```python
status: Mapped[APIKeyStatusEnum] = mapped_column(Enum(APIKeyStatusEnum, name='api_key_status', native_enum=True, values_callable=(lambda x: [(e.value) for e in x])), nullable=False, default=(APIKeyStatusEnum.ACTIVE), server_default='active')
```

####### `leadr.auth.adapters.orm.APIKeyORM.updated_at`

```python
updated_at: Mapped[timestamp] = mapped_column(onupdate=(func.now()))
```

###### `leadr.auth.adapters.orm.APIKeyStatusEnum`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

API Key status enum for database.

**Attributes:**

- [**ACTIVE**](./auth.md#leadr.auth.adapters.orm.APIKeyStatusEnum.ACTIVE) –
- [**REVOKED**](./auth.md#leadr.auth.adapters.orm.APIKeyStatusEnum.REVOKED) –

####### `leadr.auth.adapters.orm.APIKeyStatusEnum.ACTIVE`

```python
ACTIVE = 'active'
```

####### `leadr.auth.adapters.orm.APIKeyStatusEnum.REVOKED`

```python
REVOKED = 'revoked'
```

#### `leadr.auth.api`

**Modules:**

- [**routes**](./auth.md#leadr.auth.api.routes) – API routes for authentication and API key management.
- [**schemas**](./auth.md#leadr.auth.api.schemas) – API schemas for API Key endpoints.

##### `leadr.auth.api.routes`

API routes for authentication and API key management.

**Functions:**

- [**create_api_key**](#leadr.auth.api.routes.create_api_key) – Create a new API key for an account.
- [**get_api_key**](#leadr.auth.api.routes.get_api_key) – Get a single API key by ID.
- [**list_api_keys**](#leadr.auth.api.routes.list_api_keys) – List API keys for an account with optional filters.
- [**update_api_key**](#leadr.auth.api.routes.update_api_key) – Update an API key.

**Attributes:**

- [**router**](./auth.md#leadr.auth.api.routes.router) –

###### `leadr.auth.api.routes.create_api_key`

```python
create_api_key(request, service)
```

Create a new API key for an account.

The plain API key is returned only once in this response.
Store it securely as it cannot be retrieved later.

**Returns:**

- <code>[CreateAPIKeyResponse](./auth.md#leadr.auth.api.schemas.CreateAPIKeyResponse)</code> – CreateAPIKeyResponse with the plain key included.

**Raises:**

- <code>404</code> – Account not found.

###### `leadr.auth.api.routes.get_api_key`

```python
get_api_key(key_id, service)
```

Get a single API key by ID.

**Parameters:**

- **key_id** (<code>[UUID4](#pydantic.UUID4)</code>) – The UUID of the API key to retrieve.

**Returns:**

- <code>[APIKeyResponse](./auth.md#leadr.auth.api.schemas.APIKeyResponse)</code> – APIKeyResponse with key details (excludes the plain key).

**Raises:**

- <code>404</code> – API key not found.

###### `leadr.auth.api.routes.list_api_keys`

```python
list_api_keys(service, account_id, status=None)
```

List API keys for an account with optional filters.

TODO: Replace account_id query param with account_id from auth token.

**Parameters:**

- **account_id** (<code>[Annotated](#typing.Annotated)\[[UUID4](#pydantic.UUID4), [Query](#fastapi.Query)(description='Account ID to filter by')\]</code>) – Account ID to filter results (REQUIRED for multi-tenant safety).
- **status** (<code>[Annotated](#typing.Annotated)\[[APIKeyStatus](#leadr.auth.domain.api_key.APIKeyStatus) | None, [Query](#fastapi.Query)(description='Filter by status')\]</code>) – Optional status to filter results (active or revoked).

**Returns:**

- <code>[list](#list)\[[APIKeyResponse](./auth.md#leadr.auth.api.schemas.APIKeyResponse)\]</code> – List of API keys matching the filters.

###### `leadr.auth.api.routes.router`

```python
router = APIRouter()
```

###### `leadr.auth.api.routes.update_api_key`

```python
update_api_key(key_id, request, service)
```

Update an API key.

Currently supports:

- Updating status (e.g., to revoke a key)
- Soft delete via deleted flag

**Parameters:**

- **key_id** (<code>[UUID4](#pydantic.UUID4)</code>) – The UUID of the API key to update.
- **request** (<code>[UpdateAPIKeyRequest](./auth.md#leadr.auth.api.schemas.UpdateAPIKeyRequest)</code>) – Update request with optional status and deleted fields.

**Returns:**

- <code>[APIKeyResponse](./auth.md#leadr.auth.api.schemas.APIKeyResponse)</code> – APIKeyResponse with updated key details.

**Raises:**

- <code>404</code> – API key not found.

##### `leadr.auth.api.schemas`

API schemas for API Key endpoints.

**Classes:**

- [**APIKeyResponse**](./auth.md#leadr.auth.api.schemas.APIKeyResponse) – Response schema for API key details.
- [**CreateAPIKeyRequest**](./auth.md#leadr.auth.api.schemas.CreateAPIKeyRequest) – Request schema for creating an API key.
- [**CreateAPIKeyResponse**](./auth.md#leadr.auth.api.schemas.CreateAPIKeyResponse) – Response schema for creating an API key.
- [**UpdateAPIKeyRequest**](./auth.md#leadr.auth.api.schemas.UpdateAPIKeyRequest) – Request schema for updating an API key.

###### `leadr.auth.api.schemas.APIKeyResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response schema for API key details.

Excludes sensitive information like key_hash.
The full key is never returned after creation.

**Functions:**

- [**from_domain**](#leadr.auth.api.schemas.APIKeyResponse.from_domain) – Convert domain entity to response model.

**Attributes:**

- [**account_id**](#leadr.auth.api.schemas.APIKeyResponse.account_id) (<code>[UUID](#uuid.UUID)</code>) –
- [**created_at**](#leadr.auth.api.schemas.APIKeyResponse.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**expires_at**](#leadr.auth.api.schemas.APIKeyResponse.expires_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**id**](./auth.md#leadr.auth.api.schemas.APIKeyResponse.id) (<code>[UUID](#uuid.UUID)</code>) –
- [**last_used_at**](#leadr.auth.api.schemas.APIKeyResponse.last_used_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**model_config**](#leadr.auth.api.schemas.APIKeyResponse.model_config) –
- [**name**](./auth.md#leadr.auth.api.schemas.APIKeyResponse.name) (<code>[str](#str)</code>) –
- [**prefix**](./auth.md#leadr.auth.api.schemas.APIKeyResponse.prefix) (<code>[str](#str)</code>) –
- [**status**](./auth.md#leadr.auth.api.schemas.APIKeyResponse.status) (<code>[APIKeyStatus](#leadr.auth.domain.api_key.APIKeyStatus)</code>) –
- [**updated_at**](#leadr.auth.api.schemas.APIKeyResponse.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.auth.api.schemas.APIKeyResponse.account_id`

```python
account_id: UUID = Field(description='ID of the account this key belongs to')
```

####### `leadr.auth.api.schemas.APIKeyResponse.created_at`

```python
created_at: datetime = Field(description='Timestamp when the key was created (UTC)')
```

####### `leadr.auth.api.schemas.APIKeyResponse.expires_at`

```python
expires_at: datetime | None = Field(default=None, description='Expiration timestamp (UTC), or null if never expires')
```

####### `leadr.auth.api.schemas.APIKeyResponse.from_domain`

```python
from_domain(api_key)
```

Convert domain entity to response model.

**Parameters:**

- **api_key** (<code>[APIKey](#leadr.auth.domain.api_key.APIKey)</code>) – The domain APIKey entity

**Returns:**

- <code>[APIKeyResponse](./auth.md#leadr.auth.api.schemas.APIKeyResponse)</code> – APIKeyResponse with all fields populated

####### `leadr.auth.api.schemas.APIKeyResponse.id`

```python
id: UUID = Field(description='Unique identifier for the API key')
```

####### `leadr.auth.api.schemas.APIKeyResponse.last_used_at`

```python
last_used_at: datetime | None = Field(default=None, description='Timestamp of last successful authentication (UTC)')
```

####### `leadr.auth.api.schemas.APIKeyResponse.model_config`

```python
model_config = ConfigDict(extra='forbid')
```

####### `leadr.auth.api.schemas.APIKeyResponse.name`

```python
name: str = Field(description='Human-readable name for the API key')
```

####### `leadr.auth.api.schemas.APIKeyResponse.prefix`

```python
prefix: str = Field(description='Key prefix for identification (first 8 characters)')
```

####### `leadr.auth.api.schemas.APIKeyResponse.status`

```python
status: APIKeyStatus = Field(description='Current status (active, revoked, expired)')
```

####### `leadr.auth.api.schemas.APIKeyResponse.updated_at`

```python
updated_at: datetime = Field(description='Timestamp of last update (UTC)')
```

###### `leadr.auth.api.schemas.CreateAPIKeyRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request schema for creating an API key.

**Attributes:**

- [**account_id**](#leadr.auth.api.schemas.CreateAPIKeyRequest.account_id) (<code>[UUID](#uuid.UUID)</code>) –
- [**expires_at**](#leadr.auth.api.schemas.CreateAPIKeyRequest.expires_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**name**](./auth.md#leadr.auth.api.schemas.CreateAPIKeyRequest.name) (<code>[str](#str)</code>) –

####### `leadr.auth.api.schemas.CreateAPIKeyRequest.account_id`

```python
account_id: UUID = Field(description='ID of the account this API key belongs to')
```

####### `leadr.auth.api.schemas.CreateAPIKeyRequest.expires_at`

```python
expires_at: datetime | None = Field(default=None, description='Optional expiration timestamp (UTC). Key never expires if omitted')
```

####### `leadr.auth.api.schemas.CreateAPIKeyRequest.name`

```python
name: str = Field(description="Human-readable name for the API key (e.g., 'Production Server')")
```

###### `leadr.auth.api.schemas.CreateAPIKeyResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response schema for creating an API key.

Includes the plain API key which is only shown once.
The client must save this key as it cannot be retrieved later.

**Functions:**

- [**from_domain**](#leadr.auth.api.schemas.CreateAPIKeyResponse.from_domain) – Convert domain entity to response model with plain key.

**Attributes:**

- [**created_at**](#leadr.auth.api.schemas.CreateAPIKeyResponse.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**expires_at**](#leadr.auth.api.schemas.CreateAPIKeyResponse.expires_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**id**](./auth.md#leadr.auth.api.schemas.CreateAPIKeyResponse.id) (<code>[UUID](#uuid.UUID)</code>) –
- [**key**](./auth.md#leadr.auth.api.schemas.CreateAPIKeyResponse.key) (<code>[str](#str)</code>) –
- [**name**](./auth.md#leadr.auth.api.schemas.CreateAPIKeyResponse.name) (<code>[str](#str)</code>) –
- [**prefix**](./auth.md#leadr.auth.api.schemas.CreateAPIKeyResponse.prefix) (<code>[str](#str)</code>) –
- [**status**](./auth.md#leadr.auth.api.schemas.CreateAPIKeyResponse.status) (<code>[APIKeyStatus](#leadr.auth.domain.api_key.APIKeyStatus)</code>) –

####### `leadr.auth.api.schemas.CreateAPIKeyResponse.created_at`

```python
created_at: datetime = Field(description='Timestamp when the key was created (UTC)')
```

####### `leadr.auth.api.schemas.CreateAPIKeyResponse.expires_at`

```python
expires_at: datetime | None = Field(default=None, description='Expiration timestamp (UTC), or null if never expires')
```

####### `leadr.auth.api.schemas.CreateAPIKeyResponse.from_domain`

```python
from_domain(api_key, plain_key)
```

Convert domain entity to response model with plain key.

**Parameters:**

- **api_key** (<code>[APIKey](#leadr.auth.domain.api_key.APIKey)</code>) – The domain APIKey entity
- **plain_key** (<code>[str](#str)</code>) – The plain text API key (only available at creation)

**Returns:**

- <code>[CreateAPIKeyResponse](./auth.md#leadr.auth.api.schemas.CreateAPIKeyResponse)</code> – CreateAPIKeyResponse with all fields populated

####### `leadr.auth.api.schemas.CreateAPIKeyResponse.id`

```python
id: UUID = Field(description='Unique identifier for the API key')
```

####### `leadr.auth.api.schemas.CreateAPIKeyResponse.key`

```python
key: str = Field(description='Plain text API key. ONLY returned at creation - save this securely!')
```

####### `leadr.auth.api.schemas.CreateAPIKeyResponse.name`

```python
name: str = Field(description='Human-readable name for the API key')
```

####### `leadr.auth.api.schemas.CreateAPIKeyResponse.prefix`

```python
prefix: str = Field(description='Key prefix for identification (first 8 characters)')
```

####### `leadr.auth.api.schemas.CreateAPIKeyResponse.status`

```python
status: APIKeyStatus = Field(description='Current status of the API key')
```

###### `leadr.auth.api.schemas.UpdateAPIKeyRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request schema for updating an API key.

Can update status (e.g., to revoke) or set deleted flag for soft delete.

**Attributes:**

- [**deleted**](./auth.md#leadr.auth.api.schemas.UpdateAPIKeyRequest.deleted) (<code>[bool](#bool) | None</code>) –
- [**status**](./auth.md#leadr.auth.api.schemas.UpdateAPIKeyRequest.status) (<code>[APIKeyStatus](#leadr.auth.domain.api_key.APIKeyStatus) | None</code>) –

####### `leadr.auth.api.schemas.UpdateAPIKeyRequest.deleted`

```python
deleted: bool | None = Field(default=None, description='Set to true to soft delete the key')
```

####### `leadr.auth.api.schemas.UpdateAPIKeyRequest.status`

```python
status: APIKeyStatus | None = Field(default=None, description="Updated status (use 'revoked' to disable key)")
```

#### `leadr.auth.dependencies`

Authentication dependencies for FastAPI.

**Functions:**

- [**require_api_key**](#leadr.auth.dependencies.require_api_key) – Require and validate API key authentication.

##### `leadr.auth.dependencies.require_api_key`

```python
require_api_key(service, api_key=None)
```

Require and validate API key authentication.

This dependency validates the API key from the 'leadr-api-key' header
and returns the authenticated APIKey entity. It also records usage
of the key by updating the last_used_at timestamp.

**Parameters:**

- **api_key** (<code>[Annotated](#typing.Annotated)\[[str](#str) | None, [Header](#fastapi.Header)(alias=([leadr](#leadr) - [api](./auth.md#leadr.auth.api) - [key](#key)))\]</code>) – The API key from the 'leadr-api-key' header.
- **service** (<code>[APIKeyServiceDep](./auth.md#leadr.auth.services.dependencies.APIKeyServiceDep)</code>) – APIKeyService dependency.

**Returns:**

- <code>[APIKey](#leadr.auth.domain.api_key.APIKey)</code> – The authenticated APIKey entity.

**Raises:**

- <code>[HTTPException](#fastapi.HTTPException)</code> – 401 Unauthorized if the API key is missing or invalid.

<details class="example" open markdown="1">
<summary>Example</summary>

> > > @router.get("/protected")
> > > async def protected_endpoint(
> > > authenticated_key: Annotated[APIKey, Depends(require_api_key)]
> > > ):
> > > return {"account_id": authenticated_key.account_id}

</details>

#### `leadr.auth.domain`

**Modules:**

- [**api_key**](#leadr.auth.domain.api_key) – API Key domain model.

##### `leadr.auth.domain.api_key`

API Key domain model.

**Classes:**

- [**APIKey**](#leadr.auth.domain.api_key.APIKey) – API Key domain entity.
- [**APIKeyStatus**](#leadr.auth.domain.api_key.APIKeyStatus) – API Key status enumeration.

###### `leadr.auth.domain.api_key.APIKey`

Bases: <code>[Entity](./common.md#leadr.common.domain.models.Entity)</code>

API Key domain entity.

Represents an API key used to authenticate requests to the admin API.
Each account can have multiple API keys for different purposes.
Keys are stored hashed for security and shown only once at creation.

**Functions:**

- [**is_expired**](#leadr.auth.domain.api_key.APIKey.is_expired) – Check if the API key has expired.
- [**is_valid**](#leadr.auth.domain.api_key.APIKey.is_valid) – Check if the API key is valid for use.
- [**record_usage**](#leadr.auth.domain.api_key.APIKey.record_usage) – Record that the API key was used.
- [**restore**](#leadr.auth.domain.api_key.APIKey.restore) – Restore a soft-deleted entity.
- [**revoke**](#leadr.auth.domain.api_key.APIKey.revoke) – Revoke the API key, preventing further use.
- [**soft_delete**](#leadr.auth.domain.api_key.APIKey.soft_delete) – Mark entity as soft-deleted.
- [**validate_key_prefix**](#leadr.auth.domain.api_key.APIKey.validate_key_prefix) – Validate that key_prefix starts with 'ldr\_'.

**Attributes:**

- [**account_id**](#leadr.auth.domain.api_key.APIKey.account_id) (<code>[UUID](#uuid.UUID)</code>) –
- [**created_at**](#leadr.auth.domain.api_key.APIKey.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**deleted_at**](#leadr.auth.domain.api_key.APIKey.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**expires_at**](#leadr.auth.domain.api_key.APIKey.expires_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**id**](#leadr.auth.domain.api_key.APIKey.id) (<code>[UUID](#uuid.UUID)</code>) –
- [**is_deleted**](#leadr.auth.domain.api_key.APIKey.is_deleted) (<code>[bool](#bool)</code>) – Check if entity is soft-deleted.
- [**key_hash**](#leadr.auth.domain.api_key.APIKey.key_hash) (<code>[str](#str)</code>) –
- [**key_prefix**](#leadr.auth.domain.api_key.APIKey.key_prefix) (<code>[str](#str)</code>) –
- [**last_used_at**](#leadr.auth.domain.api_key.APIKey.last_used_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**model_config**](#leadr.auth.domain.api_key.APIKey.model_config) –
- [**name**](#leadr.auth.domain.api_key.APIKey.name) (<code>[str](#str)</code>) –
- [**status**](#leadr.auth.domain.api_key.APIKey.status) (<code>[APIKeyStatus](#leadr.auth.domain.api_key.APIKeyStatus)</code>) –
- [**updated_at**](#leadr.auth.domain.api_key.APIKey.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.auth.domain.api_key.APIKey.account_id`

```python
account_id: UUID
```

####### `leadr.auth.domain.api_key.APIKey.created_at`

```python
created_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp when entity was created (UTC)')
```

####### `leadr.auth.domain.api_key.APIKey.deleted_at`

```python
deleted_at: datetime | None = Field(default=None, description='Timestamp when entity was soft-deleted (UTC), or null if active')
```

####### `leadr.auth.domain.api_key.APIKey.expires_at`

```python
expires_at: datetime | None = None
```

####### `leadr.auth.domain.api_key.APIKey.id`

```python
id: UUID = Field(frozen=True, default_factory=uuid4, description='Unique identifier (auto-generated UUID)')
```

####### `leadr.auth.domain.api_key.APIKey.is_deleted`

```python
is_deleted: bool
```

Check if entity is soft-deleted.

**Returns:**

- <code>[bool](#bool)</code> – True if the entity has a deleted_at timestamp, False otherwise.

####### `leadr.auth.domain.api_key.APIKey.is_expired`

```python
is_expired()
```

Check if the API key has expired.

**Returns:**

- <code>[bool](#bool)</code> – True if the key has an expiration date and it's in the past.

####### `leadr.auth.domain.api_key.APIKey.is_valid`

```python
is_valid()
```

Check if the API key is valid for use.

A key is valid if it's active and not expired.

**Returns:**

- <code>[bool](#bool)</code> – True if the key can be used for authentication.

####### `leadr.auth.domain.api_key.APIKey.key_hash`

```python
key_hash: str
```

####### `leadr.auth.domain.api_key.APIKey.key_prefix`

```python
key_prefix: str
```

####### `leadr.auth.domain.api_key.APIKey.last_used_at`

```python
last_used_at: datetime | None = None
```

####### `leadr.auth.domain.api_key.APIKey.model_config`

```python
model_config = ConfigDict(validate_assignment=True)
```

####### `leadr.auth.domain.api_key.APIKey.name`

```python
name: str
```

####### `leadr.auth.domain.api_key.APIKey.record_usage`

```python
record_usage(used_at)
```

Record that the API key was used.

**Parameters:**

- **used_at** (<code>[datetime](#datetime.datetime)</code>) – Timestamp when the key was used.

####### `leadr.auth.domain.api_key.APIKey.restore`

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

####### `leadr.auth.domain.api_key.APIKey.revoke`

```python
revoke()
```

Revoke the API key, preventing further use.

####### `leadr.auth.domain.api_key.APIKey.soft_delete`

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

####### `leadr.auth.domain.api_key.APIKey.status`

```python
status: APIKeyStatus = APIKeyStatus.ACTIVE
```

####### `leadr.auth.domain.api_key.APIKey.updated_at`

```python
updated_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp of last update (UTC)')
```

####### `leadr.auth.domain.api_key.APIKey.validate_key_prefix`

```python
validate_key_prefix(value)
```

Validate that key_prefix starts with 'ldr\_'.

###### `leadr.auth.domain.api_key.APIKeyStatus`

Bases: <code>[Enum](#enum.Enum)</code>

API Key status enumeration.

**Attributes:**

- [**ACTIVE**](#leadr.auth.domain.api_key.APIKeyStatus.ACTIVE) –
- [**REVOKED**](#leadr.auth.domain.api_key.APIKeyStatus.REVOKED) –

####### `leadr.auth.domain.api_key.APIKeyStatus.ACTIVE`

```python
ACTIVE = 'active'
```

####### `leadr.auth.domain.api_key.APIKeyStatus.REVOKED`

```python
REVOKED = 'revoked'
```

#### `leadr.auth.services`

**Modules:**

- [**api_key_crypto**](#leadr.auth.services.api_key_crypto) – Cryptographic operations for API keys.
- [**api_key_service**](#leadr.auth.services.api_key_service) – API Key service for managing API key operations.
- [**dependencies**](./auth.md#leadr.auth.services.dependencies) – API Key service dependency injection factory.
- [**repositories**](./auth.md#leadr.auth.services.repositories) – API Key repository service.

##### `leadr.auth.services.api_key_crypto`

Cryptographic operations for API keys.

**Functions:**

- [**generate_api_key**](#leadr.auth.services.api_key_crypto.generate_api_key) – Generate a secure random API key with 'ldr\_' prefix.
- [**hash_api_key**](#leadr.auth.services.api_key_crypto.hash_api_key) – Hash an API key for secure storage using HMAC-SHA256.
- [**verify_api_key**](#leadr.auth.services.api_key_crypto.verify_api_key) – Verify an API key against its stored hash.

**Attributes:**

- [**API_KEY_BYTES**](#leadr.auth.services.api_key_crypto.API_KEY_BYTES) –
- [**API_KEY_PREFIX**](#leadr.auth.services.api_key_crypto.API_KEY_PREFIX) –

###### `leadr.auth.services.api_key_crypto.API_KEY_BYTES`

```python
API_KEY_BYTES = 32
```

###### `leadr.auth.services.api_key_crypto.API_KEY_PREFIX`

```python
API_KEY_PREFIX = 'ldr_'
```

###### `leadr.auth.services.api_key_crypto.generate_api_key`

```python
generate_api_key()
```

Generate a secure random API key with 'ldr\_' prefix.

The key is generated using cryptographically secure random bytes
and encoded using URL-safe base64 encoding for compatibility.

**Returns:**

- <code>[str](#str)</code> – A secure API key string starting with 'ldr\_' followed by
- <code>[str](#str)</code> – URL-safe random characters (alphanumeric, hyphen, underscore).

<details class="example" open markdown="1">
<summary>Example</summary>

> > > key = generate_api_key()
> > > key.startswith('ldr\_')
> > > True
> > > len(key) > 36
> > > True

</details>

###### `leadr.auth.services.api_key_crypto.hash_api_key`

```python
hash_api_key(key, secret)
```

Hash an API key for secure storage using HMAC-SHA256.

Uses HMAC-SHA256 with a server-side secret (pepper) to create
a one-way hash of the API key. This provides defense in depth:
database compromise alone isn't enough to validate keys.

**Parameters:**

- **key** (<code>[str](#str)</code>) – The API key to hash.
- **secret** (<code>[str](#str)</code>) – Server-side secret for additional security.

**Returns:**

- <code>[str](#str)</code> – A hexadecimal string representation of the HMAC-SHA256 hash.

<details class="example" open markdown="1">
<summary>Example</summary>

> > > secret = "my-secret"
> > > hash1 = hash_api_key('ldr_test123', secret)
> > > hash2 = hash_api_key('ldr_test123', secret)
> > > hash1 == hash2
> > > True
> > > len(hash1)
> > > 64

</details>

###### `leadr.auth.services.api_key_crypto.verify_api_key`

```python
verify_api_key(key, key_hash, secret)
```

Verify an API key against its stored hash.

Uses timing-safe comparison to prevent timing attacks.

**Parameters:**

- **key** (<code>[str](#str)</code>) – The API key to verify.
- **key_hash** (<code>[str](#str)</code>) – The stored hash to compare against.
- **secret** (<code>[str](#str)</code>) – Server-side secret for HMAC verification.

**Returns:**

- <code>[bool](#bool)</code> – True if the key matches the hash, False otherwise.

<details class="example" open markdown="1">
<summary>Example</summary>

> > > secret = "my-secret"
> > > key = 'ldr_test123'
> > > hashed = hash_api_key(key, secret)
> > > verify_api_key(key, hashed, secret)
> > > True
> > > verify_api_key('ldr_wrong', hashed, secret)
> > > False

</details>

##### `leadr.auth.services.api_key_service`

API Key service for managing API key operations.

**Classes:**

- [**APIKeyService**](#leadr.auth.services.api_key_service.APIKeyService) – Service for managing API key lifecycle and operations.

###### `leadr.auth.services.api_key_service.APIKeyService`

Bases: <code>[BaseService](./common.md#leadr.common.services.BaseService)\[[APIKey](#leadr.auth.domain.api_key.APIKey), [APIKeyRepository](./auth.md#leadr.auth.services.repositories.APIKeyRepository)\]</code>

Service for managing API key lifecycle and operations.

This service orchestrates API key creation, validation, and management
by coordinating between the domain models, cryptographic functions,
and repository layer.

**Functions:**

- [**count_active_api_keys**](#leadr.auth.services.api_key_service.APIKeyService.count_active_api_keys) – Count active API keys for an account.
- [**create_api_key**](#leadr.auth.services.api_key_service.APIKeyService.create_api_key) – Create a new API key for an account.
- [**delete**](#leadr.auth.services.api_key_service.APIKeyService.delete) – Soft-delete an entity.
- [**get_api_key**](#leadr.auth.services.api_key_service.APIKeyService.get_api_key) – Get an API key by its ID.
- [**get_by_id**](#leadr.auth.services.api_key_service.APIKeyService.get_by_id) – Get an entity by its ID.
- [**get_by_id_or_raise**](#leadr.auth.services.api_key_service.APIKeyService.get_by_id_or_raise) – Get an entity by its ID or raise EntityNotFoundError.
- [**list_account_api_keys**](#leadr.auth.services.api_key_service.APIKeyService.list_account_api_keys) – List all API keys for an account.
- [**list_all**](#leadr.auth.services.api_key_service.APIKeyService.list_all) – List all non-deleted entities.
- [**list_api_keys**](#leadr.auth.services.api_key_service.APIKeyService.list_api_keys) – List API keys for an account with optional filters.
- [**record_usage**](#leadr.auth.services.api_key_service.APIKeyService.record_usage) – Record that an API key was used at a specific time.
- [**revoke_api_key**](#leadr.auth.services.api_key_service.APIKeyService.revoke_api_key) – Revoke an API key, preventing further use.
- [**soft_delete**](#leadr.auth.services.api_key_service.APIKeyService.soft_delete) – Soft-delete an entity and return it before deletion.
- [**update_api_key_status**](#leadr.auth.services.api_key_service.APIKeyService.update_api_key_status) – Update the status of an API key.
- [**validate_api_key**](#leadr.auth.services.api_key_service.APIKeyService.validate_api_key) – Validate an API key and return the domain entity if valid.

**Attributes:**

- [**repository**](#leadr.auth.services.api_key_service.APIKeyService.repository) –

####### `leadr.auth.services.api_key_service.APIKeyService.count_active_api_keys`

```python
count_active_api_keys(account_id)
```

Count active API keys for an account.

This is useful for enforcing limits on the number of active keys
per account based on their plan or tier.

**Parameters:**

- **account_id** (<code>[UUID](#uuid.UUID)</code>) – The account ID to count keys for.

**Returns:**

- <code>[int](#int)</code> – Number of active (non-revoked) API keys.

####### `leadr.auth.services.api_key_service.APIKeyService.create_api_key`

```python
create_api_key(account_id, name, expires_at=None)
```

Create a new API key for an account.

Generates a secure random key, hashes it for storage, and persists
it to the database. The plain key is returned only once for the
caller to provide to the user.

**Parameters:**

- **account_id** (<code>[UUID](#uuid.UUID)</code>) – The account ID to create the key for.
- **name** (<code>[str](#str)</code>) – A descriptive name for the key.
- **expires_at** (<code>[datetime](#datetime.datetime) | None</code>) – Optional expiration timestamp for the key.

**Returns:**

- <code>[APIKey](#leadr.auth.domain.api_key.APIKey)</code> – A tuple of (APIKey domain entity, plain key string).
- <code>[str](#str)</code> – The plain key should be shown to the user once and not stored.

<details class="example" open markdown="1">
<summary>Example</summary>

> > > api_key, plain_key = await service.create_api_key(
> > > ... account_id=account_id,
> > > ... name="Production API Key",
> > > ... expires_at=datetime.now(UTC) + timedelta(days=90)
> > > ... )
> > > print(f"Your API key: {plain_key}")
> > > Your API key: ldr_abc123...

</details>

####### `leadr.auth.services.api_key_service.APIKeyService.delete`

```python
delete(entity_id)
```

Soft-delete an entity.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the entity doesn't exist

####### `leadr.auth.services.api_key_service.APIKeyService.get_api_key`

```python
get_api_key(key_id)
```

Get an API key by its ID.

**Parameters:**

- **key_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the API key to retrieve.

**Returns:**

- <code>[APIKey](#leadr.auth.domain.api_key.APIKey) | None</code> – The APIKey domain entity if found, None otherwise.

####### `leadr.auth.services.api_key_service.APIKeyService.get_by_id`

```python
get_by_id(entity_id)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the entity to retrieve

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.services.DomainEntityT) | None</code> – The domain entity if found, None otherwise

####### `leadr.auth.services.api_key_service.APIKeyService.get_by_id_or_raise`

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

####### `leadr.auth.services.api_key_service.APIKeyService.list_account_api_keys`

```python
list_account_api_keys(account_id, active_only=False)
```

List all API keys for an account.

**Parameters:**

- **account_id** (<code>[UUID](#uuid.UUID)</code>) – The account ID to list keys for.
- **active_only** (<code>[bool](#bool)</code>) – If True, only return active (non-revoked) keys.

**Returns:**

- <code>[list](#list)\[[APIKey](#leadr.auth.domain.api_key.APIKey)\]</code> – List of APIKey domain entities.

####### `leadr.auth.services.api_key_service.APIKeyService.list_all`

```python
list_all()
```

List all non-deleted entities.

**Returns:**

- <code>[list](#list)\[[DomainEntityT](./common.md#leadr.common.services.DomainEntityT)\]</code> – List of domain entities

####### `leadr.auth.services.api_key_service.APIKeyService.list_api_keys`

```python
list_api_keys(account_id, status=None)
```

List API keys for an account with optional filters.

**Parameters:**

- **account_id** (<code>[UUID](#uuid.UUID)</code>) – REQUIRED - Account ID to filter by (multi-tenant safety).
- **status** (<code>[str](#str) | None</code>) – Optional status string to filter by.

**Returns:**

- <code>[list](#list)\[[APIKey](#leadr.auth.domain.api_key.APIKey)\]</code> – List of APIKey domain entities matching the filters.

####### `leadr.auth.services.api_key_service.APIKeyService.record_usage`

```python
record_usage(key_id, used_at)
```

Record that an API key was used at a specific time.

This is typically called automatically during validation, but can
also be called explicitly if needed.

**Parameters:**

- **key_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the API key that was used.
- **used_at** (<code>[datetime](#datetime.datetime)</code>) – The timestamp when the key was used.

**Returns:**

- <code>[APIKey](#leadr.auth.domain.api_key.APIKey)</code> – The updated APIKey domain entity.

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the key doesn't exist.

####### `leadr.auth.services.api_key_service.APIKeyService.repository`

```python
repository = self._create_repository(session)
```

####### `leadr.auth.services.api_key_service.APIKeyService.revoke_api_key`

```python
revoke_api_key(key_id)
```

Revoke an API key, preventing further use.

**Parameters:**

- **key_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the API key to revoke.

**Returns:**

- <code>[APIKey](#leadr.auth.domain.api_key.APIKey)</code> – The updated APIKey domain entity with REVOKED status.

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the key doesn't exist.

####### `leadr.auth.services.api_key_service.APIKeyService.soft_delete`

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

####### `leadr.auth.services.api_key_service.APIKeyService.update_api_key_status`

```python
update_api_key_status(key_id, status)
```

Update the status of an API key.

**Parameters:**

- **key_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the API key to update.
- **status** (<code>[str](#str)</code>) – The new status value (active or revoked).

**Returns:**

- <code>[APIKey](#leadr.auth.domain.api_key.APIKey)</code> – The updated APIKey domain entity.

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the key doesn't exist.
- <code>[ValueError](#ValueError)</code> – If the status is invalid.

####### `leadr.auth.services.api_key_service.APIKeyService.validate_api_key`

```python
validate_api_key(plain_key)
```

Validate an API key and return the domain entity if valid.

Performs the following checks:

1. Extracts prefix and looks up key in database
1. Verifies the hash matches
1. Checks if key is active (not revoked)
1. Checks if key is not expired
1. Records usage timestamp if valid

**Parameters:**

- **plain_key** (<code>[str](#str)</code>) – The plain API key string to validate.

**Returns:**

- <code>[APIKey](#leadr.auth.domain.api_key.APIKey) | None</code> – The APIKey domain entity if valid, None otherwise.

<details class="example" open markdown="1">
<summary>Example</summary>

> > > api_key = await service.validate_api_key("ldr_abc123...")
> > > if api_key:
> > > ... print(f"Valid key for account {api_key.account_id}")
> > > ... else:
> > > ... print("Invalid or expired key")

</details>

##### `leadr.auth.services.dependencies`

API Key service dependency injection factory.

**Functions:**

- [**get_api_key_service**](#leadr.auth.services.dependencies.get_api_key_service) – Get APIKeyService dependency.

**Attributes:**

- [**APIKeyServiceDep**](./auth.md#leadr.auth.services.dependencies.APIKeyServiceDep) –

###### `leadr.auth.services.dependencies.APIKeyServiceDep`

```python
APIKeyServiceDep = Annotated[APIKeyService, Depends(get_api_key_service)]
```

###### `leadr.auth.services.dependencies.get_api_key_service`

```python
get_api_key_service(db)
```

Get APIKeyService dependency.

**Parameters:**

- **db** (<code>[DatabaseSession](./common.md#leadr.common.dependencies.DatabaseSession)</code>) – Database session injected via dependency injection

**Returns:**

- <code>[APIKeyService](#leadr.auth.services.api_key_service.APIKeyService)</code> – APIKeyService instance configured with the database session

##### `leadr.auth.services.repositories`

API Key repository service.

**Classes:**

- [**APIKeyRepository**](./auth.md#leadr.auth.services.repositories.APIKeyRepository) – API Key repository for managing API key persistence.

###### `leadr.auth.services.repositories.APIKeyRepository`

Bases: <code>[BaseRepository](./common.md#leadr.common.repositories.BaseRepository)\[[APIKey](#leadr.auth.domain.api_key.APIKey), [APIKeyORM](./auth.md#leadr.auth.adapters.orm.APIKeyORM)\]</code>

API Key repository for managing API key persistence.

**Functions:**

- [**count_active_by_account**](#leadr.auth.services.repositories.APIKeyRepository.count_active_by_account) – Count active, non-deleted API keys for a given account.
- [**create**](./auth.md#leadr.auth.services.repositories.APIKeyRepository.create) – Create a new entity in the database.
- [**delete**](./auth.md#leadr.auth.services.repositories.APIKeyRepository.delete) – Soft delete an entity by setting its deleted_at timestamp.
- [**filter**](./auth.md#leadr.auth.services.repositories.APIKeyRepository.filter) – Filter API keys by account and optional criteria.
- [**get_by_id**](#leadr.auth.services.repositories.APIKeyRepository.get_by_id) – Get an entity by its ID.
- [**get_by_prefix**](#leadr.auth.services.repositories.APIKeyRepository.get_by_prefix) – Get API key by prefix, returns None if not found or soft-deleted.
- [**update**](./auth.md#leadr.auth.services.repositories.APIKeyRepository.update) – Update an existing entity in the database.

**Attributes:**

- [**session**](./auth.md#leadr.auth.services.repositories.APIKeyRepository.session) –

####### `leadr.auth.services.repositories.APIKeyRepository.count_active_by_account`

```python
count_active_by_account(account_id)
```

Count active, non-deleted API keys for a given account.

**Parameters:**

- **account_id** (<code>[UUID](#uuid.UUID)</code>) – The account ID to count keys for.

**Returns:**

- <code>[int](#int)</code> – Number of active, non-deleted API keys for the account.

####### `leadr.auth.services.repositories.APIKeyRepository.create`

```python
create(entity)
```

Create a new entity in the database.

**Parameters:**

- **entity** (<code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code>) – Domain entity to create

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code> – Created domain entity with refreshed data

####### `leadr.auth.services.repositories.APIKeyRepository.delete`

```python
delete(entity_id)
```

Soft delete an entity by setting its deleted_at timestamp.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4)</code>) – ID of entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

####### `leadr.auth.services.repositories.APIKeyRepository.filter`

```python
filter(account_id, status=None, active_only=False, **kwargs)
```

Filter API keys by account and optional criteria.

**Parameters:**

- **account_id** (<code>[UUID](#uuid.UUID)</code>) – REQUIRED - Account ID to filter by (multi-tenant safety)
- **status** (<code>[APIKeyStatus](#leadr.auth.domain.api_key.APIKeyStatus) | None</code>) – Optional APIKeyStatus to filter by
- **active_only** (<code>[bool](#bool)</code>) – If True, only return ACTIVE keys (bool)

**Returns:**

- <code>[list](#list)\[[APIKey](#leadr.auth.domain.api_key.APIKey)\]</code> – List of API keys for the account matching the filter criteria

####### `leadr.auth.services.repositories.APIKeyRepository.get_by_id`

```python
get_by_id(entity_id, include_deleted=False)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4)</code>) – Entity ID to retrieve
- **include_deleted** (<code>[bool](#bool)</code>) – If True, include soft-deleted entities. Defaults to False.

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT) | None</code> – Domain entity if found, None otherwise

####### `leadr.auth.services.repositories.APIKeyRepository.get_by_prefix`

```python
get_by_prefix(key_prefix)
```

Get API key by prefix, returns None if not found or soft-deleted.

####### `leadr.auth.services.repositories.APIKeyRepository.session`

```python
session = session
```

####### `leadr.auth.services.repositories.APIKeyRepository.update`

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
