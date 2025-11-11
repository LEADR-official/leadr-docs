## `leadr`

**Modules:**

- [**accounts**](#leadr.accounts) –
- [**auth**](#leadr.auth) –
- [**boards**](#leadr.boards) –
- [**common**](#leadr.common) –
- [**config**](#leadr.config) – Application configuration management.
- [**games**](#leadr.games) –
- [**infra**](#leadr.infra) –
- [**players**](#leadr.players) –
- [**scores**](#leadr.scores) –

### `leadr.accounts`

**Modules:**

- [**adapters**](#leadr.accounts.adapters) –
- [**api**](#leadr.accounts.api) –
- [**domain**](#leadr.accounts.domain) –

#### `leadr.accounts.adapters`

**Modules:**

- [**orm**](#leadr.accounts.adapters.orm) – Account and User ORM models.

##### `leadr.accounts.adapters.orm`

Account and User ORM models.

**Classes:**

- [**AccountORM**](#leadr.accounts.adapters.orm.AccountORM) – Account ORM model.
- [**AccountStatusEnum**](#leadr.accounts.adapters.orm.AccountStatusEnum) – Account status enum for database.
- [**UserORM**](#leadr.accounts.adapters.orm.UserORM) – User ORM model.

###### `leadr.accounts.adapters.orm.AccountORM`

Bases: <code>[Base](#leadr.common.orm.Base)</code>

Account ORM model.

Represents an organization or team in the database.
Maps to the accounts table with unique name and slug constraints.

**Attributes:**

- [**created_at**](#leadr.accounts.adapters.orm.AccountORM.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](#leadr.common.orm.timestamp)\]</code>) –
- [**deleted_at**](#leadr.accounts.adapters.orm.AccountORM.deleted_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[nullable_timestamp](#leadr.common.orm.nullable_timestamp)\]</code>) –
- [**id**](#leadr.accounts.adapters.orm.AccountORM.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**name**](#leadr.accounts.adapters.orm.AccountORM.name) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**slug**](#leadr.accounts.adapters.orm.AccountORM.slug) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**status**](#leadr.accounts.adapters.orm.AccountORM.status) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[AccountStatusEnum](#leadr.accounts.adapters.orm.AccountStatusEnum)\]</code>) –
- [**updated_at**](#leadr.accounts.adapters.orm.AccountORM.updated_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](#leadr.common.orm.timestamp)\]</code>) –
- [**users**](#leadr.accounts.adapters.orm.AccountORM.users) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[list](#list)\[[UserORM](#leadr.accounts.adapters.orm.UserORM)\]\]</code>) –

####### `leadr.accounts.adapters.orm.AccountORM.created_at`

```python
created_at: Mapped[timestamp]
```

####### `leadr.accounts.adapters.orm.AccountORM.deleted_at`

```python
deleted_at: Mapped[nullable_timestamp]
```

####### `leadr.accounts.adapters.orm.AccountORM.id`

```python
id: Mapped[uuid_pk]
```

####### `leadr.accounts.adapters.orm.AccountORM.name`

```python
name: Mapped[str] = mapped_column(String, nullable=False, unique=True, index=True)
```

####### `leadr.accounts.adapters.orm.AccountORM.slug`

```python
slug: Mapped[str] = mapped_column(String, nullable=False, unique=True, index=True)
```

####### `leadr.accounts.adapters.orm.AccountORM.status`

```python
status: Mapped[AccountStatusEnum] = mapped_column(Enum(AccountStatusEnum, name='account_status', native_enum=True, values_callable=(lambda x: [(e.value) for e in x])), nullable=False, default=(AccountStatusEnum.ACTIVE), server_default='active')
```

####### `leadr.accounts.adapters.orm.AccountORM.updated_at`

```python
updated_at: Mapped[timestamp] = mapped_column(onupdate=(func.now()))
```

####### `leadr.accounts.adapters.orm.AccountORM.users`

```python
users: Mapped[list[UserORM]] = relationship(back_populates='account', cascade='all, delete-orphan')
```

###### `leadr.accounts.adapters.orm.AccountStatusEnum`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Account status enum for database.

**Attributes:**

- [**ACTIVE**](#leadr.accounts.adapters.orm.AccountStatusEnum.ACTIVE) –
- [**SUSPENDED**](#leadr.accounts.adapters.orm.AccountStatusEnum.SUSPENDED) –

####### `leadr.accounts.adapters.orm.AccountStatusEnum.ACTIVE`

```python
ACTIVE = 'active'
```

####### `leadr.accounts.adapters.orm.AccountStatusEnum.SUSPENDED`

```python
SUSPENDED = 'suspended'
```

###### `leadr.accounts.adapters.orm.UserORM`

Bases: <code>[Base](#leadr.common.orm.Base)</code>

User ORM model.

Represents a user within an account in the database.
Maps to the users table with foreign key to accounts.

**Attributes:**

- [**account**](#leadr.accounts.adapters.orm.UserORM.account) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[AccountORM](#leadr.accounts.adapters.orm.AccountORM)\]</code>) –
- [**account_id**](#leadr.accounts.adapters.orm.UserORM.account_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**created_at**](#leadr.accounts.adapters.orm.UserORM.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](#leadr.common.orm.timestamp)\]</code>) –
- [**deleted_at**](#leadr.accounts.adapters.orm.UserORM.deleted_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[nullable_timestamp](#leadr.common.orm.nullable_timestamp)\]</code>) –
- [**display_name**](#leadr.accounts.adapters.orm.UserORM.display_name) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**email**](#leadr.accounts.adapters.orm.UserORM.email) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**id**](#leadr.accounts.adapters.orm.UserORM.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**updated_at**](#leadr.accounts.adapters.orm.UserORM.updated_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](#leadr.common.orm.timestamp)\]</code>) –

####### `leadr.accounts.adapters.orm.UserORM.account`

```python
account: Mapped[AccountORM] = relationship(back_populates='users')
```

####### `leadr.accounts.adapters.orm.UserORM.account_id`

```python
account_id: Mapped[UUID] = mapped_column(ForeignKey('accounts.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.accounts.adapters.orm.UserORM.created_at`

```python
created_at: Mapped[timestamp]
```

####### `leadr.accounts.adapters.orm.UserORM.deleted_at`

```python
deleted_at: Mapped[nullable_timestamp]
```

####### `leadr.accounts.adapters.orm.UserORM.display_name`

```python
display_name: Mapped[str] = mapped_column(String, nullable=False)
```

####### `leadr.accounts.adapters.orm.UserORM.email`

```python
email: Mapped[str] = mapped_column(String, nullable=False, unique=True, index=True)
```

####### `leadr.accounts.adapters.orm.UserORM.id`

```python
id: Mapped[uuid_pk]
```

####### `leadr.accounts.adapters.orm.UserORM.updated_at`

```python
updated_at: Mapped[timestamp] = mapped_column(onupdate=(func.now()))
```

#### `leadr.accounts.api`

**Modules:**

- [**routes**](#leadr.accounts.api.routes) – Account and User API routes.
- [**schemas**](#leadr.accounts.api.schemas) – API request and response models for accounts.

##### `leadr.accounts.api.routes`

Account and User API routes.

**Functions:**

- [**create_account**](#leadr.accounts.api.routes.create_account) – Create a new account.
- [**create_user**](#leadr.accounts.api.routes.create_user) – Create a new user.
- [**get_account**](#leadr.accounts.api.routes.get_account) – Get an account by ID.
- [**get_user**](#leadr.accounts.api.routes.get_user) – Get a user by ID.
- [**list_accounts**](#leadr.accounts.api.routes.list_accounts) – List all accounts.
- [**list_users**](#leadr.accounts.api.routes.list_users) – List users for an account.
- [**update_account**](#leadr.accounts.api.routes.update_account) – Update an account.
- [**update_user**](#leadr.accounts.api.routes.update_user) – Update a user.

**Attributes:**

- [**router**](#leadr.accounts.api.routes.router) –

###### `leadr.accounts.api.routes.create_account`

```python
create_account(request, service)
```

Create a new account.

**Parameters:**

- **request** (<code>[AccountCreateRequest](#leadr.accounts.api.schemas.AccountCreateRequest)</code>) – Account creation details including name and slug.
- **service** (<code>[AccountServiceDep](#leadr.accounts.services.dependencies.AccountServiceDep)</code>) – Injected account service dependency.

**Returns:**

- <code>[AccountResponse](#leadr.accounts.api.schemas.AccountResponse)</code> – AccountResponse with the created account including auto-generated ID and timestamps.

###### `leadr.accounts.api.routes.create_user`

```python
create_user(request, service)
```

Create a new user.

Creates a new user associated with an existing account.

**Parameters:**

- **request** (<code>[UserCreateRequest](#leadr.accounts.api.schemas.UserCreateRequest)</code>) – User creation details including account_id, email, and display name.
- **service** (<code>[UserServiceDep](#leadr.accounts.services.dependencies.UserServiceDep)</code>) – Injected user service dependency.

**Returns:**

- <code>[UserResponse](#leadr.accounts.api.schemas.UserResponse)</code> – UserResponse with the created user including auto-generated ID and timestamps.

**Raises:**

- <code>404</code> – Account not found.

###### `leadr.accounts.api.routes.get_account`

```python
get_account(account_id, service)
```

Get an account by ID.

**Parameters:**

- **account_id** (<code>[UUID4](#pydantic.UUID4)</code>) – Unique identifier for the account.
- **service** (<code>[AccountServiceDep](#leadr.accounts.services.dependencies.AccountServiceDep)</code>) – Injected account service dependency.

**Returns:**

- <code>[AccountResponse](#leadr.accounts.api.schemas.AccountResponse)</code> – AccountResponse with full account details.

**Raises:**

- <code>404</code> – Account not found.

###### `leadr.accounts.api.routes.get_user`

```python
get_user(user_id, service)
```

Get a user by ID.

**Parameters:**

- **user_id** (<code>[UUID4](#pydantic.UUID4)</code>) – Unique identifier for the user.
- **service** (<code>[UserServiceDep](#leadr.accounts.services.dependencies.UserServiceDep)</code>) – Injected user service dependency.

**Returns:**

- <code>[UserResponse](#leadr.accounts.api.schemas.UserResponse)</code> – UserResponse with full user details.

**Raises:**

- <code>404</code> – User not found.

###### `leadr.accounts.api.routes.list_accounts`

```python
list_accounts(service)
```

List all accounts.

**Parameters:**

- **service** (<code>[AccountServiceDep](#leadr.accounts.services.dependencies.AccountServiceDep)</code>) – Injected account service dependency.

**Returns:**

- <code>[list](#list)\[[AccountResponse](#leadr.accounts.api.schemas.AccountResponse)\]</code> – List of all active accounts.

###### `leadr.accounts.api.routes.list_users`

```python
list_users(service, account_id)
```

List users for an account.

TODO: Replace account_id query param with account_id from auth token.

**Parameters:**

- **service** (<code>[UserServiceDep](#leadr.accounts.services.dependencies.UserServiceDep)</code>) – Injected user service dependency.
- **account_id** (<code>[Annotated](#typing.Annotated)\[[UUID4](#pydantic.UUID4), [Query](#fastapi.Query)(description='Account ID to filter by')\]</code>) – Account ID to filter results (REQUIRED for multi-tenant safety).

**Returns:**

- <code>[list](#list)\[[UserResponse](#leadr.accounts.api.schemas.UserResponse)\]</code> – List of users for the account.

###### `leadr.accounts.api.routes.router`

```python
router = APIRouter()
```

###### `leadr.accounts.api.routes.update_account`

```python
update_account(account_id, request, service)
```

Update an account.

Supports updating name, slug, status, or soft-deleting the account.
Status changes (active/suspended) are handled through dedicated service methods.

**Parameters:**

- **account_id** (<code>[UUID4](#pydantic.UUID4)</code>) – Unique identifier for the account.
- **request** (<code>[AccountUpdateRequest](#leadr.accounts.api.schemas.AccountUpdateRequest)</code>) – Account update details (all fields optional).
- **service** (<code>[AccountServiceDep](#leadr.accounts.services.dependencies.AccountServiceDep)</code>) – Injected account service dependency.

**Returns:**

- <code>[AccountResponse](#leadr.accounts.api.schemas.AccountResponse)</code> – AccountResponse with the updated account details.

**Raises:**

- <code>404</code> – Account not found.

###### `leadr.accounts.api.routes.update_user`

```python
update_user(user_id, request, service)
```

Update a user.

Supports updating email, display name, or soft-deleting the user.

**Parameters:**

- **user_id** (<code>[UUID4](#pydantic.UUID4)</code>) – Unique identifier for the user.
- **request** (<code>[UserUpdateRequest](#leadr.accounts.api.schemas.UserUpdateRequest)</code>) – User update details (all fields optional).
- **service** (<code>[UserServiceDep](#leadr.accounts.services.dependencies.UserServiceDep)</code>) – Injected user service dependency.

**Returns:**

- <code>[UserResponse](#leadr.accounts.api.schemas.UserResponse)</code> – UserResponse with the updated user details.

**Raises:**

- <code>404</code> – User not found.

##### `leadr.accounts.api.schemas`

API request and response models for accounts.

**Classes:**

- [**AccountCreateRequest**](#leadr.accounts.api.schemas.AccountCreateRequest) – Request model for creating an account.
- [**AccountResponse**](#leadr.accounts.api.schemas.AccountResponse) – Response model for an account.
- [**AccountUpdateRequest**](#leadr.accounts.api.schemas.AccountUpdateRequest) – Request model for updating an account.
- [**UserCreateRequest**](#leadr.accounts.api.schemas.UserCreateRequest) – Request model for creating a user.
- [**UserResponse**](#leadr.accounts.api.schemas.UserResponse) – Response model for a user.
- [**UserUpdateRequest**](#leadr.accounts.api.schemas.UserUpdateRequest) – Request model for updating a user.

###### `leadr.accounts.api.schemas.AccountCreateRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request model for creating an account.

**Attributes:**

- [**name**](#leadr.accounts.api.schemas.AccountCreateRequest.name) (<code>[str](#str)</code>) –
- [**slug**](#leadr.accounts.api.schemas.AccountCreateRequest.slug) (<code>[str](#str)</code>) –

####### `leadr.accounts.api.schemas.AccountCreateRequest.name`

```python
name: str = Field(description='Account name (2-100 characters)')
```

####### `leadr.accounts.api.schemas.AccountCreateRequest.slug`

```python
slug: str = Field(description='URL-friendly identifier for the account (lowercase, alphanumeric, hyphens)')
```

###### `leadr.accounts.api.schemas.AccountResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response model for an account.

**Functions:**

- [**from_domain**](#leadr.accounts.api.schemas.AccountResponse.from_domain) – Convert domain entity to response model.

**Attributes:**

- [**created_at**](#leadr.accounts.api.schemas.AccountResponse.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**id**](#leadr.accounts.api.schemas.AccountResponse.id) (<code>[UUID](#uuid.UUID)</code>) –
- [**name**](#leadr.accounts.api.schemas.AccountResponse.name) (<code>[str](#str)</code>) –
- [**slug**](#leadr.accounts.api.schemas.AccountResponse.slug) (<code>[str](#str)</code>) –
- [**status**](#leadr.accounts.api.schemas.AccountResponse.status) (<code>[AccountStatus](#leadr.accounts.domain.account.AccountStatus)</code>) –
- [**updated_at**](#leadr.accounts.api.schemas.AccountResponse.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.accounts.api.schemas.AccountResponse.created_at`

```python
created_at: datetime = Field(description='Timestamp when the account was created (UTC)')
```

####### `leadr.accounts.api.schemas.AccountResponse.from_domain`

```python
from_domain(account)
```

Convert domain entity to response model.

**Parameters:**

- **account** (<code>[Account](#leadr.accounts.domain.account.Account)</code>) – The domain Account entity to convert.

**Returns:**

- <code>[AccountResponse](#leadr.accounts.api.schemas.AccountResponse)</code> – AccountResponse with all fields populated from the domain entity.

####### `leadr.accounts.api.schemas.AccountResponse.id`

```python
id: UUID = Field(description='Unique identifier for the account')
```

####### `leadr.accounts.api.schemas.AccountResponse.name`

```python
name: str = Field(description='Account name')
```

####### `leadr.accounts.api.schemas.AccountResponse.slug`

```python
slug: str = Field(description='URL-friendly identifier')
```

####### `leadr.accounts.api.schemas.AccountResponse.status`

```python
status: AccountStatus = Field(description='Current account status')
```

####### `leadr.accounts.api.schemas.AccountResponse.updated_at`

```python
updated_at: datetime = Field(description='Timestamp of last update (UTC)')
```

###### `leadr.accounts.api.schemas.AccountUpdateRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request model for updating an account.

**Attributes:**

- [**deleted**](#leadr.accounts.api.schemas.AccountUpdateRequest.deleted) (<code>[bool](#bool) | None</code>) –
- [**name**](#leadr.accounts.api.schemas.AccountUpdateRequest.name) (<code>[str](#str) | None</code>) –
- [**slug**](#leadr.accounts.api.schemas.AccountUpdateRequest.slug) (<code>[str](#str) | None</code>) –
- [**status**](#leadr.accounts.api.schemas.AccountUpdateRequest.status) (<code>[AccountStatus](#leadr.accounts.domain.account.AccountStatus) | None</code>) –

####### `leadr.accounts.api.schemas.AccountUpdateRequest.deleted`

```python
deleted: bool | None = Field(default=None, description='Set to true to soft delete the account')
```

####### `leadr.accounts.api.schemas.AccountUpdateRequest.name`

```python
name: str | None = Field(default=None, description='Updated account name')
```

####### `leadr.accounts.api.schemas.AccountUpdateRequest.slug`

```python
slug: str | None = Field(default=None, description='Updated URL-friendly identifier')
```

####### `leadr.accounts.api.schemas.AccountUpdateRequest.status`

```python
status: AccountStatus | None = Field(default=None, description='Account status (active, suspended, deleted)')
```

###### `leadr.accounts.api.schemas.UserCreateRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request model for creating a user.

**Attributes:**

- [**account_id**](#leadr.accounts.api.schemas.UserCreateRequest.account_id) (<code>[UUID](#uuid.UUID)</code>) –
- [**display_name**](#leadr.accounts.api.schemas.UserCreateRequest.display_name) (<code>[str](#str)</code>) –
- [**email**](#leadr.accounts.api.schemas.UserCreateRequest.email) (<code>[EmailStr](#pydantic.EmailStr)</code>) –

####### `leadr.accounts.api.schemas.UserCreateRequest.account_id`

```python
account_id: UUID = Field(description='ID of the account this user belongs to')
```

####### `leadr.accounts.api.schemas.UserCreateRequest.display_name`

```python
display_name: str = Field(description="User's display name (2-100 characters)")
```

####### `leadr.accounts.api.schemas.UserCreateRequest.email`

```python
email: EmailStr = Field(description="User's email address (must be valid email format)")
```

###### `leadr.accounts.api.schemas.UserResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response model for a user.

**Functions:**

- [**from_domain**](#leadr.accounts.api.schemas.UserResponse.from_domain) – Convert domain entity to response model.

**Attributes:**

- [**account_id**](#leadr.accounts.api.schemas.UserResponse.account_id) (<code>[UUID](#uuid.UUID)</code>) –
- [**created_at**](#leadr.accounts.api.schemas.UserResponse.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**display_name**](#leadr.accounts.api.schemas.UserResponse.display_name) (<code>[str](#str)</code>) –
- [**email**](#leadr.accounts.api.schemas.UserResponse.email) (<code>[str](#str)</code>) –
- [**id**](#leadr.accounts.api.schemas.UserResponse.id) (<code>[UUID](#uuid.UUID)</code>) –
- [**updated_at**](#leadr.accounts.api.schemas.UserResponse.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.accounts.api.schemas.UserResponse.account_id`

```python
account_id: UUID = Field(description='ID of the account this user belongs to')
```

####### `leadr.accounts.api.schemas.UserResponse.created_at`

```python
created_at: datetime = Field(description='Timestamp when the user was created (UTC)')
```

####### `leadr.accounts.api.schemas.UserResponse.display_name`

```python
display_name: str = Field(description="User's display name")
```

####### `leadr.accounts.api.schemas.UserResponse.email`

```python
email: str = Field(description="User's email address")
```

####### `leadr.accounts.api.schemas.UserResponse.from_domain`

```python
from_domain(user)
```

Convert domain entity to response model.

**Parameters:**

- **user** (<code>[User](#leadr.accounts.domain.user.User)</code>) – The domain User entity to convert.

**Returns:**

- <code>[UserResponse](#leadr.accounts.api.schemas.UserResponse)</code> – UserResponse with all fields populated from the domain entity.

####### `leadr.accounts.api.schemas.UserResponse.id`

```python
id: UUID = Field(description='Unique identifier for the user')
```

####### `leadr.accounts.api.schemas.UserResponse.updated_at`

```python
updated_at: datetime = Field(description='Timestamp of last update (UTC)')
```

###### `leadr.accounts.api.schemas.UserUpdateRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request model for updating a user.

**Attributes:**

- [**deleted**](#leadr.accounts.api.schemas.UserUpdateRequest.deleted) (<code>[bool](#bool) | None</code>) –
- [**display_name**](#leadr.accounts.api.schemas.UserUpdateRequest.display_name) (<code>[str](#str) | None</code>) –
- [**email**](#leadr.accounts.api.schemas.UserUpdateRequest.email) (<code>[EmailStr](#pydantic.EmailStr) | None</code>) –

####### `leadr.accounts.api.schemas.UserUpdateRequest.deleted`

```python
deleted: bool | None = Field(default=None, description='Set to true to soft delete the user')
```

####### `leadr.accounts.api.schemas.UserUpdateRequest.display_name`

```python
display_name: str | None = Field(default=None, description='Updated display name')
```

####### `leadr.accounts.api.schemas.UserUpdateRequest.email`

```python
email: EmailStr | None = Field(default=None, description='Updated email address')
```

#### `leadr.accounts.domain`

**Modules:**

- [**account**](#leadr.accounts.domain.account) – Account domain model.
- [**user**](#leadr.accounts.domain.user) – User domain model.

##### `leadr.accounts.domain.account`

Account domain model.

**Classes:**

- [**Account**](#leadr.accounts.domain.account.Account) – Account domain entity.
- [**AccountStatus**](#leadr.accounts.domain.account.AccountStatus) – Account status enumeration.

###### `leadr.accounts.domain.account.Account`

Bases: <code>[Entity](#leadr.common.domain.models.Entity)</code>

Account domain entity.

Represents an organization or team that owns games and manages users.
Accounts have a unique name and URL-friendly slug, and can be
active or suspended.

**Functions:**

- [**activate**](#leadr.accounts.domain.account.Account.activate) – Activate the account, allowing access.
- [**restore**](#leadr.accounts.domain.account.Account.restore) – Restore a soft-deleted entity.
- [**soft_delete**](#leadr.accounts.domain.account.Account.soft_delete) – Mark entity as soft-deleted.
- [**suspend**](#leadr.accounts.domain.account.Account.suspend) – Suspend the account, preventing access.
- [**validate_name**](#leadr.accounts.domain.account.Account.validate_name) – Validate account name length and format.
- [**validate_slug**](#leadr.accounts.domain.account.Account.validate_slug) – Validate slug format (lowercase alphanumeric with hyphens).

**Attributes:**

- [**created_at**](#leadr.accounts.domain.account.Account.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**deleted_at**](#leadr.accounts.domain.account.Account.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**id**](#leadr.accounts.domain.account.Account.id) (<code>[UUID](#uuid.UUID)</code>) –
- [**is_deleted**](#leadr.accounts.domain.account.Account.is_deleted) (<code>[bool](#bool)</code>) – Check if entity is soft-deleted.
- [**model_config**](#leadr.accounts.domain.account.Account.model_config) –
- [**name**](#leadr.accounts.domain.account.Account.name) (<code>[str](#str)</code>) –
- [**slug**](#leadr.accounts.domain.account.Account.slug) (<code>[str](#str)</code>) –
- [**status**](#leadr.accounts.domain.account.Account.status) (<code>[AccountStatus](#leadr.accounts.domain.account.AccountStatus)</code>) –
- [**updated_at**](#leadr.accounts.domain.account.Account.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.accounts.domain.account.Account.activate`

```python
activate()
```

Activate the account, allowing access.

####### `leadr.accounts.domain.account.Account.created_at`

```python
created_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp when entity was created (UTC)')
```

####### `leadr.accounts.domain.account.Account.deleted_at`

```python
deleted_at: datetime | None = Field(default=None, description='Timestamp when entity was soft-deleted (UTC), or null if active')
```

####### `leadr.accounts.domain.account.Account.id`

```python
id: UUID = Field(frozen=True, default_factory=uuid4, description='Unique identifier (auto-generated UUID)')
```

####### `leadr.accounts.domain.account.Account.is_deleted`

```python
is_deleted: bool
```

Check if entity is soft-deleted.

**Returns:**

- <code>[bool](#bool)</code> – True if the entity has a deleted_at timestamp, False otherwise.

####### `leadr.accounts.domain.account.Account.model_config`

```python
model_config = ConfigDict(validate_assignment=True)
```

####### `leadr.accounts.domain.account.Account.name`

```python
name: str
```

####### `leadr.accounts.domain.account.Account.restore`

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

####### `leadr.accounts.domain.account.Account.slug`

```python
slug: str
```

####### `leadr.accounts.domain.account.Account.soft_delete`

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

####### `leadr.accounts.domain.account.Account.status`

```python
status: AccountStatus = AccountStatus.ACTIVE
```

####### `leadr.accounts.domain.account.Account.suspend`

```python
suspend()
```

Suspend the account, preventing access.

####### `leadr.accounts.domain.account.Account.updated_at`

```python
updated_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp of last update (UTC)')
```

####### `leadr.accounts.domain.account.Account.validate_name`

```python
validate_name(value)
```

Validate account name length and format.

####### `leadr.accounts.domain.account.Account.validate_slug`

```python
validate_slug(value)
```

Validate slug format (lowercase alphanumeric with hyphens).

###### `leadr.accounts.domain.account.AccountStatus`

Bases: <code>[Enum](#enum.Enum)</code>

Account status enumeration.

**Attributes:**

- [**ACTIVE**](#leadr.accounts.domain.account.AccountStatus.ACTIVE) –
- [**SUSPENDED**](#leadr.accounts.domain.account.AccountStatus.SUSPENDED) –

####### `leadr.accounts.domain.account.AccountStatus.ACTIVE`

```python
ACTIVE = 'active'
```

####### `leadr.accounts.domain.account.AccountStatus.SUSPENDED`

```python
SUSPENDED = 'suspended'
```

##### `leadr.accounts.domain.user`

User domain model.

**Classes:**

- [**User**](#leadr.accounts.domain.user.User) – User domain entity.

###### `leadr.accounts.domain.user.User`

Bases: <code>[Entity](#leadr.common.domain.models.Entity)</code>

User domain entity.

Represents a user within an account (organization/team).
Users are scoped to a specific account and have an email
address and display name.

Each user belongs to exactly one account, and users cannot be
transferred between accounts. The email must be unique within
an account.

**Functions:**

- [**restore**](#leadr.accounts.domain.user.User.restore) – Restore a soft-deleted entity.
- [**soft_delete**](#leadr.accounts.domain.user.User.soft_delete) – Mark entity as soft-deleted.
- [**validate_display_name**](#leadr.accounts.domain.user.User.validate_display_name) – Validate display name length and format.

**Attributes:**

- [**account_id**](#leadr.accounts.domain.user.User.account_id) (<code>[UUID](#uuid.UUID)</code>) –
- [**created_at**](#leadr.accounts.domain.user.User.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**deleted_at**](#leadr.accounts.domain.user.User.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**display_name**](#leadr.accounts.domain.user.User.display_name) (<code>[str](#str)</code>) –
- [**email**](#leadr.accounts.domain.user.User.email) (<code>[EmailStr](#pydantic.EmailStr)</code>) –
- [**id**](#leadr.accounts.domain.user.User.id) (<code>[UUID](#uuid.UUID)</code>) –
- [**is_deleted**](#leadr.accounts.domain.user.User.is_deleted) (<code>[bool](#bool)</code>) – Check if entity is soft-deleted.
- [**model_config**](#leadr.accounts.domain.user.User.model_config) –
- [**updated_at**](#leadr.accounts.domain.user.User.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.accounts.domain.user.User.account_id`

```python
account_id: UUID = Field(frozen=True, description='ID of the account this user belongs to (immutable)')
```

####### `leadr.accounts.domain.user.User.created_at`

```python
created_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp when entity was created (UTC)')
```

####### `leadr.accounts.domain.user.User.deleted_at`

```python
deleted_at: datetime | None = Field(default=None, description='Timestamp when entity was soft-deleted (UTC), or null if active')
```

####### `leadr.accounts.domain.user.User.display_name`

```python
display_name: str = Field(description="User's display name (2-100 characters)")
```

####### `leadr.accounts.domain.user.User.email`

```python
email: EmailStr = Field(description="User's email address (validated format)")
```

####### `leadr.accounts.domain.user.User.id`

```python
id: UUID = Field(frozen=True, default_factory=uuid4, description='Unique identifier (auto-generated UUID)')
```

####### `leadr.accounts.domain.user.User.is_deleted`

```python
is_deleted: bool
```

Check if entity is soft-deleted.

**Returns:**

- <code>[bool](#bool)</code> – True if the entity has a deleted_at timestamp, False otherwise.

####### `leadr.accounts.domain.user.User.model_config`

```python
model_config = ConfigDict(validate_assignment=True)
```

####### `leadr.accounts.domain.user.User.restore`

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

####### `leadr.accounts.domain.user.User.soft_delete`

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

####### `leadr.accounts.domain.user.User.updated_at`

```python
updated_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp of last update (UTC)')
```

####### `leadr.accounts.domain.user.User.validate_display_name`

```python
validate_display_name(value)
```

Validate display name length and format.

**Parameters:**

- **value** (<code>[str](#str)</code>) – The display name to validate.

**Returns:**

- <code>[str](#str)</code> – The validated and trimmed display name.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If display name is empty, too short, or too long.

### `leadr.auth`

**Modules:**

- [**adapters**](#leadr.auth.adapters) –
- [**api**](#leadr.auth.api) –
- [**dependencies**](#leadr.auth.dependencies) – Authentication dependencies for FastAPI.
- [**domain**](#leadr.auth.domain) –
- [**services**](#leadr.auth.services) –

#### `leadr.auth.adapters`

**Modules:**

- [**orm**](#leadr.auth.adapters.orm) – API Key ORM models.

##### `leadr.auth.adapters.orm`

API Key ORM models.

**Classes:**

- [**APIKeyORM**](#leadr.auth.adapters.orm.APIKeyORM) – API Key ORM model.
- [**APIKeyStatusEnum**](#leadr.auth.adapters.orm.APIKeyStatusEnum) – API Key status enum for database.

###### `leadr.auth.adapters.orm.APIKeyORM`

Bases: <code>[Base](#leadr.common.orm.Base)</code>

API Key ORM model.

Represents an API key for account authentication in the database.
Maps to the api_keys table with foreign key to accounts.

**Attributes:**

- [**account_id**](#leadr.auth.adapters.orm.APIKeyORM.account_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**created_at**](#leadr.auth.adapters.orm.APIKeyORM.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](#leadr.common.orm.timestamp)\]</code>) –
- [**deleted_at**](#leadr.auth.adapters.orm.APIKeyORM.deleted_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[nullable_timestamp](#leadr.common.orm.nullable_timestamp)\]</code>) –
- [**expires_at**](#leadr.auth.adapters.orm.APIKeyORM.expires_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime) | None\]</code>) –
- [**id**](#leadr.auth.adapters.orm.APIKeyORM.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**key_hash**](#leadr.auth.adapters.orm.APIKeyORM.key_hash) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**key_prefix**](#leadr.auth.adapters.orm.APIKeyORM.key_prefix) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**last_used_at**](#leadr.auth.adapters.orm.APIKeyORM.last_used_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime) | None\]</code>) –
- [**name**](#leadr.auth.adapters.orm.APIKeyORM.name) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**status**](#leadr.auth.adapters.orm.APIKeyORM.status) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[APIKeyStatusEnum](#leadr.auth.adapters.orm.APIKeyStatusEnum)\]</code>) –
- [**updated_at**](#leadr.auth.adapters.orm.APIKeyORM.updated_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](#leadr.common.orm.timestamp)\]</code>) –

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

- [**ACTIVE**](#leadr.auth.adapters.orm.APIKeyStatusEnum.ACTIVE) –
- [**REVOKED**](#leadr.auth.adapters.orm.APIKeyStatusEnum.REVOKED) –

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

- [**routes**](#leadr.auth.api.routes) – API routes for authentication and API key management.
- [**schemas**](#leadr.auth.api.schemas) – API schemas for API Key endpoints.

##### `leadr.auth.api.routes`

API routes for authentication and API key management.

**Functions:**

- [**create_api_key**](#leadr.auth.api.routes.create_api_key) – Create a new API key for an account.
- [**get_api_key**](#leadr.auth.api.routes.get_api_key) – Get a single API key by ID.
- [**list_api_keys**](#leadr.auth.api.routes.list_api_keys) – List API keys for an account with optional filters.
- [**update_api_key**](#leadr.auth.api.routes.update_api_key) – Update an API key.

**Attributes:**

- [**router**](#leadr.auth.api.routes.router) –

###### `leadr.auth.api.routes.create_api_key`

```python
create_api_key(request, service)
```

Create a new API key for an account.

The plain API key is returned only once in this response.
Store it securely as it cannot be retrieved later.

**Returns:**

- <code>[CreateAPIKeyResponse](#leadr.auth.api.schemas.CreateAPIKeyResponse)</code> – CreateAPIKeyResponse with the plain key included.

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

- <code>[APIKeyResponse](#leadr.auth.api.schemas.APIKeyResponse)</code> – APIKeyResponse with key details (excludes the plain key).

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

- <code>[list](#list)\[[APIKeyResponse](#leadr.auth.api.schemas.APIKeyResponse)\]</code> – List of API keys matching the filters.

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
- **request** (<code>[UpdateAPIKeyRequest](#leadr.auth.api.schemas.UpdateAPIKeyRequest)</code>) – Update request with optional status and deleted fields.

**Returns:**

- <code>[APIKeyResponse](#leadr.auth.api.schemas.APIKeyResponse)</code> – APIKeyResponse with updated key details.

**Raises:**

- <code>404</code> – API key not found.

##### `leadr.auth.api.schemas`

API schemas for API Key endpoints.

**Classes:**

- [**APIKeyResponse**](#leadr.auth.api.schemas.APIKeyResponse) – Response schema for API key details.
- [**CreateAPIKeyRequest**](#leadr.auth.api.schemas.CreateAPIKeyRequest) – Request schema for creating an API key.
- [**CreateAPIKeyResponse**](#leadr.auth.api.schemas.CreateAPIKeyResponse) – Response schema for creating an API key.
- [**UpdateAPIKeyRequest**](#leadr.auth.api.schemas.UpdateAPIKeyRequest) – Request schema for updating an API key.

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
- [**id**](#leadr.auth.api.schemas.APIKeyResponse.id) (<code>[UUID](#uuid.UUID)</code>) –
- [**last_used_at**](#leadr.auth.api.schemas.APIKeyResponse.last_used_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**model_config**](#leadr.auth.api.schemas.APIKeyResponse.model_config) –
- [**name**](#leadr.auth.api.schemas.APIKeyResponse.name) (<code>[str](#str)</code>) –
- [**prefix**](#leadr.auth.api.schemas.APIKeyResponse.prefix) (<code>[str](#str)</code>) –
- [**status**](#leadr.auth.api.schemas.APIKeyResponse.status) (<code>[APIKeyStatus](#leadr.auth.domain.api_key.APIKeyStatus)</code>) –
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

- <code>[APIKeyResponse](#leadr.auth.api.schemas.APIKeyResponse)</code> – APIKeyResponse with all fields populated

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
- [**name**](#leadr.auth.api.schemas.CreateAPIKeyRequest.name) (<code>[str](#str)</code>) –

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
- [**id**](#leadr.auth.api.schemas.CreateAPIKeyResponse.id) (<code>[UUID](#uuid.UUID)</code>) –
- [**key**](#leadr.auth.api.schemas.CreateAPIKeyResponse.key) (<code>[str](#str)</code>) –
- [**name**](#leadr.auth.api.schemas.CreateAPIKeyResponse.name) (<code>[str](#str)</code>) –
- [**prefix**](#leadr.auth.api.schemas.CreateAPIKeyResponse.prefix) (<code>[str](#str)</code>) –
- [**status**](#leadr.auth.api.schemas.CreateAPIKeyResponse.status) (<code>[APIKeyStatus](#leadr.auth.domain.api_key.APIKeyStatus)</code>) –

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

- <code>[CreateAPIKeyResponse](#leadr.auth.api.schemas.CreateAPIKeyResponse)</code> – CreateAPIKeyResponse with all fields populated

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

- [**deleted**](#leadr.auth.api.schemas.UpdateAPIKeyRequest.deleted) (<code>[bool](#bool) | None</code>) –
- [**status**](#leadr.auth.api.schemas.UpdateAPIKeyRequest.status) (<code>[APIKeyStatus](#leadr.auth.domain.api_key.APIKeyStatus) | None</code>) –

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

- **api_key** (<code>[Annotated](#typing.Annotated)\[[str](#str) | None, [Header](#fastapi.Header)(alias=([leadr](#leadr) - [api](#leadr.auth.api) - [key](#key)))\]</code>) – The API key from the 'leadr-api-key' header.
- **service** (<code>[APIKeyServiceDep](#leadr.auth.services.dependencies.APIKeyServiceDep)</code>) – APIKeyService dependency.

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

Bases: <code>[Entity](#leadr.common.domain.models.Entity)</code>

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
- [**dependencies**](#leadr.auth.services.dependencies) – API Key service dependency injection factory.
- [**repositories**](#leadr.auth.services.repositories) – API Key repository service.

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

Bases: <code>[BaseService](#leadr.common.services.BaseService)\[[APIKey](#leadr.auth.domain.api_key.APIKey), [APIKeyRepository](#leadr.auth.services.repositories.APIKeyRepository)\]</code>

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

- <code>[EntityNotFoundError](#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the entity doesn't exist

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

- <code>[DomainEntityT](#leadr.common.services.DomainEntityT) | None</code> – The domain entity if found, None otherwise

####### `leadr.auth.services.api_key_service.APIKeyService.get_by_id_or_raise`

```python
get_by_id_or_raise(entity_id)
```

Get an entity by its ID or raise EntityNotFoundError.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the entity to retrieve

**Returns:**

- <code>[DomainEntityT](#leadr.common.services.DomainEntityT)</code> – The domain entity

**Raises:**

- <code>[EntityNotFoundError](#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the entity is not found
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

- <code>[list](#list)\[[DomainEntityT](#leadr.common.services.DomainEntityT)\]</code> – List of domain entities

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

- <code>[EntityNotFoundError](#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the key doesn't exist.

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

- <code>[EntityNotFoundError](#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the key doesn't exist.

####### `leadr.auth.services.api_key_service.APIKeyService.soft_delete`

```python
soft_delete(entity_id)
```

Soft-delete an entity and return it before deletion.

Useful for endpoints that need to return the deleted entity in the response.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the entity to delete

**Returns:**

- <code>[DomainEntityT](#leadr.common.services.DomainEntityT)</code> – The entity before it was deleted

**Raises:**

- <code>[EntityNotFoundError](#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the entity doesn't exist

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

- <code>[EntityNotFoundError](#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the key doesn't exist.
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

- [**APIKeyServiceDep**](#leadr.auth.services.dependencies.APIKeyServiceDep) –

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

- **db** (<code>[DatabaseSession](#leadr.common.dependencies.DatabaseSession)</code>) – Database session injected via dependency injection

**Returns:**

- <code>[APIKeyService](#leadr.auth.services.api_key_service.APIKeyService)</code> – APIKeyService instance configured with the database session

##### `leadr.auth.services.repositories`

API Key repository service.

**Classes:**

- [**APIKeyRepository**](#leadr.auth.services.repositories.APIKeyRepository) – API Key repository for managing API key persistence.

###### `leadr.auth.services.repositories.APIKeyRepository`

Bases: <code>[BaseRepository](#leadr.common.repositories.BaseRepository)\[[APIKey](#leadr.auth.domain.api_key.APIKey), [APIKeyORM](#leadr.auth.adapters.orm.APIKeyORM)\]</code>

API Key repository for managing API key persistence.

**Functions:**

- [**count_active_by_account**](#leadr.auth.services.repositories.APIKeyRepository.count_active_by_account) – Count active, non-deleted API keys for a given account.
- [**create**](#leadr.auth.services.repositories.APIKeyRepository.create) – Create a new entity in the database.
- [**delete**](#leadr.auth.services.repositories.APIKeyRepository.delete) – Soft delete an entity by setting its deleted_at timestamp.
- [**filter**](#leadr.auth.services.repositories.APIKeyRepository.filter) – Filter API keys by account and optional criteria.
- [**get_by_id**](#leadr.auth.services.repositories.APIKeyRepository.get_by_id) – Get an entity by its ID.
- [**get_by_prefix**](#leadr.auth.services.repositories.APIKeyRepository.get_by_prefix) – Get API key by prefix, returns None if not found or soft-deleted.
- [**update**](#leadr.auth.services.repositories.APIKeyRepository.update) – Update an existing entity in the database.

**Attributes:**

- [**session**](#leadr.auth.services.repositories.APIKeyRepository.session) –

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

- **entity** (<code>[DomainEntityT](#leadr.common.repositories.DomainEntityT)</code>) – Domain entity to create

**Returns:**

- <code>[DomainEntityT](#leadr.common.repositories.DomainEntityT)</code> – Created domain entity with refreshed data

####### `leadr.auth.services.repositories.APIKeyRepository.delete`

```python
delete(entity_id)
```

Soft delete an entity by setting its deleted_at timestamp.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4)</code>) – ID of entity to delete

**Raises:**

- <code>[EntityNotFoundError](#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

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

- <code>[DomainEntityT](#leadr.common.repositories.DomainEntityT) | None</code> – Domain entity if found, None otherwise

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

- **entity** (<code>[DomainEntityT](#leadr.common.repositories.DomainEntityT)</code>) – Domain entity with updated data

**Returns:**

- <code>[DomainEntityT](#leadr.common.repositories.DomainEntityT)</code> – Updated domain entity with refreshed data

**Raises:**

- <code>[EntityNotFoundError](#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

### `leadr.boards`

**Modules:**

- [**adapters**](#leadr.boards.adapters) –
- [**api**](#leadr.boards.api) –
- [**domain**](#leadr.boards.domain) –
- [**services**](#leadr.boards.services) –

#### `leadr.boards.adapters`

#### `leadr.boards.api`

#### `leadr.boards.domain`

#### `leadr.boards.services`

### `leadr.common`

**Modules:**

- [**api**](#leadr.common.api) – API utilities and exception handlers.
- [**database**](#leadr.common.database) – Database connection and session management.
- [**dependencies**](#leadr.common.dependencies) – Shared FastAPI dependencies for the application.
- [**domain**](#leadr.common.domain) –
- [**orm**](#leadr.common.orm) – Common ORM base classes and utilities.
- [**repositories**](#leadr.common.repositories) – Base repository abstraction for common CRUD operations.
- [**services**](#leadr.common.services) – Base service abstraction for common business logic patterns.

#### `leadr.common.api`

API utilities and exception handlers.

**Modules:**

- [**exceptions**](#leadr.common.api.exceptions) – Global exception handlers for API layer.

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
- [**engine**](#leadr.common.database.engine) –

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

- [**DatabaseSession**](#leadr.common.dependencies.DatabaseSession) –

##### `leadr.common.dependencies.DatabaseSession`

```python
DatabaseSession = Annotated[AsyncSession, Depends(get_db)]
```

#### `leadr.common.domain`

**Modules:**

- [**exceptions**](#leadr.common.domain.exceptions) – Domain-specific exceptions for LEADR.
- [**models**](#leadr.common.domain.models) – Common domain models and value objects.

##### `leadr.common.domain.exceptions`

Domain-specific exceptions for LEADR.

**Classes:**

- [**DomainError**](#leadr.common.domain.exceptions.DomainError) – Base exception for all domain-level errors.
- [**EntityNotFoundError**](#leadr.common.domain.exceptions.EntityNotFoundError) – Raised when an entity cannot be found in the repository.
- [**InvalidEntityStateError**](#leadr.common.domain.exceptions.InvalidEntityStateError) – Raised when an entity is in an invalid state for the requested operation.
- [**ValidationError**](#leadr.common.domain.exceptions.ValidationError) – Raised when entity validation fails.

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

- [**message**](#leadr.common.domain.exceptions.DomainError.message) –

####### `leadr.common.domain.exceptions.DomainError.message`

```python
message = message
```

###### `leadr.common.domain.exceptions.EntityNotFoundError`

```python
EntityNotFoundError(entity_type, entity_id)
```

Bases: <code>[DomainError](#leadr.common.domain.exceptions.DomainError)</code>

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
- [**message**](#leadr.common.domain.exceptions.EntityNotFoundError.message) –

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

Bases: <code>[DomainError](#leadr.common.domain.exceptions.DomainError)</code>

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
- [**message**](#leadr.common.domain.exceptions.InvalidEntityStateError.message) –
- [**reason**](#leadr.common.domain.exceptions.InvalidEntityStateError.reason) –

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

Bases: <code>[DomainError](#leadr.common.domain.exceptions.DomainError)</code>

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
- [**field**](#leadr.common.domain.exceptions.ValidationError.field) –
- [**message**](#leadr.common.domain.exceptions.ValidationError.message) –
- [**reason**](#leadr.common.domain.exceptions.ValidationError.reason) –

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

- [**Entity**](#leadr.common.domain.models.Entity) – Base class for all domain entities with ID and timestamps.

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

- [**restore**](#leadr.common.domain.models.Entity.restore) – Restore a soft-deleted entity.
- [**soft_delete**](#leadr.common.domain.models.Entity.soft_delete) – Mark entity as soft-deleted.

**Attributes:**

- [**created_at**](#leadr.common.domain.models.Entity.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**deleted_at**](#leadr.common.domain.models.Entity.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**id**](#leadr.common.domain.models.Entity.id) (<code>[UUID](#uuid.UUID)</code>) –
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

- [**Base**](#leadr.common.orm.Base) – Base class for all database models with UUID primary key and timestamps.

**Attributes:**

- [**nullable_timestamp**](#leadr.common.orm.nullable_timestamp) –
- [**timestamp**](#leadr.common.orm.timestamp) –
- [**uuid_pk**](#leadr.common.orm.uuid_pk) –

##### `leadr.common.orm.Base`

Bases: <code>[DeclarativeBase](#sqlalchemy.orm.DeclarativeBase)</code>

Base class for all database models with UUID primary key and timestamps.

**Attributes:**

- [**created_at**](#leadr.common.orm.Base.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](#leadr.common.orm.timestamp)\]</code>) –
- [**deleted_at**](#leadr.common.orm.Base.deleted_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[nullable_timestamp](#leadr.common.orm.nullable_timestamp)\]</code>) –
- [**id**](#leadr.common.orm.Base.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**updated_at**](#leadr.common.orm.Base.updated_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](#leadr.common.orm.timestamp)\]</code>) –

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

- [**BaseRepository**](#leadr.common.repositories.BaseRepository) – Abstract base repository providing common CRUD operations.

**Attributes:**

- [**DomainEntityT**](#leadr.common.repositories.DomainEntityT) –
- [**ORMModelT**](#leadr.common.repositories.ORMModelT) –

##### `leadr.common.repositories.BaseRepository`

```python
BaseRepository(session)
```

Bases: <code>[ABC](#abc.ABC)</code>, <code>[Generic](#typing.Generic)\[[DomainEntityT](#leadr.common.repositories.DomainEntityT), [ORMModelT](#leadr.common.repositories.ORMModelT)\]</code>

Abstract base repository providing common CRUD operations.

All repositories should extend this class and implement the abstract methods
for converting between domain entities and ORM models.

All delete operations are soft deletes by default, setting deleted_at timestamp.

**Functions:**

- [**create**](#leadr.common.repositories.BaseRepository.create) – Create a new entity in the database.
- [**delete**](#leadr.common.repositories.BaseRepository.delete) – Soft delete an entity by setting its deleted_at timestamp.
- [**filter**](#leadr.common.repositories.BaseRepository.filter) – Filter entities based on criteria.
- [**get_by_id**](#leadr.common.repositories.BaseRepository.get_by_id) – Get an entity by its ID.
- [**update**](#leadr.common.repositories.BaseRepository.update) – Update an existing entity in the database.

**Attributes:**

- [**session**](#leadr.common.repositories.BaseRepository.session) –

**Parameters:**

- **session** (<code>[AsyncSession](#sqlalchemy.ext.asyncio.AsyncSession)</code>) – SQLAlchemy async session

###### `leadr.common.repositories.BaseRepository.create`

```python
create(entity)
```

Create a new entity in the database.

**Parameters:**

- **entity** (<code>[DomainEntityT](#leadr.common.repositories.DomainEntityT)</code>) – Domain entity to create

**Returns:**

- <code>[DomainEntityT](#leadr.common.repositories.DomainEntityT)</code> – Created domain entity with refreshed data

###### `leadr.common.repositories.BaseRepository.delete`

```python
delete(entity_id)
```

Soft delete an entity by setting its deleted_at timestamp.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4)</code>) – ID of entity to delete

**Raises:**

- <code>[EntityNotFoundError](#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

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

- <code>[list](#list)\[[DomainEntityT](#leadr.common.repositories.DomainEntityT)\]</code> – List of domain entities matching the filter criteria

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

- <code>[DomainEntityT](#leadr.common.repositories.DomainEntityT) | None</code> – Domain entity if found, None otherwise

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

- **entity** (<code>[DomainEntityT](#leadr.common.repositories.DomainEntityT)</code>) – Domain entity with updated data

**Returns:**

- <code>[DomainEntityT](#leadr.common.repositories.DomainEntityT)</code> – Updated domain entity with refreshed data

**Raises:**

- <code>[EntityNotFoundError](#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

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

- [**BaseService**](#leadr.common.services.BaseService) – Abstract base service providing common business logic patterns.

**Attributes:**

- [**DomainEntityT**](#leadr.common.services.DomainEntityT) –
- [**RepositoryT**](#leadr.common.services.RepositoryT) –

##### `leadr.common.services.BaseService`

```python
BaseService(session)
```

Bases: <code>[ABC](#abc.ABC)</code>, <code>[Generic](#typing.Generic)\[[DomainEntityT](#leadr.common.services.DomainEntityT), [RepositoryT](#leadr.common.services.RepositoryT)\]</code>

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

- [**delete**](#leadr.common.services.BaseService.delete) – Soft-delete an entity.
- [**get_by_id**](#leadr.common.services.BaseService.get_by_id) – Get an entity by its ID.
- [**get_by_id_or_raise**](#leadr.common.services.BaseService.get_by_id_or_raise) – Get an entity by its ID or raise EntityNotFoundError.
- [**list_all**](#leadr.common.services.BaseService.list_all) – List all non-deleted entities.
- [**soft_delete**](#leadr.common.services.BaseService.soft_delete) – Soft-delete an entity and return it before deletion.

**Attributes:**

- [**repository**](#leadr.common.services.BaseService.repository) –

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

- <code>[EntityNotFoundError](#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the entity doesn't exist

###### `leadr.common.services.BaseService.get_by_id`

```python
get_by_id(entity_id)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the entity to retrieve

**Returns:**

- <code>[DomainEntityT](#leadr.common.services.DomainEntityT) | None</code> – The domain entity if found, None otherwise

###### `leadr.common.services.BaseService.get_by_id_or_raise`

```python
get_by_id_or_raise(entity_id)
```

Get an entity by its ID or raise EntityNotFoundError.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the entity to retrieve

**Returns:**

- <code>[DomainEntityT](#leadr.common.services.DomainEntityT)</code> – The domain entity

**Raises:**

- <code>[EntityNotFoundError](#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the entity is not found
  (converted to HTTP 404 by global handler)

###### `leadr.common.services.BaseService.list_all`

```python
list_all()
```

List all non-deleted entities.

**Returns:**

- <code>[list](#list)\[[DomainEntityT](#leadr.common.services.DomainEntityT)\]</code> – List of domain entities

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

- <code>[DomainEntityT](#leadr.common.services.DomainEntityT)</code> – The entity before it was deleted

**Raises:**

- <code>[EntityNotFoundError](#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the entity doesn't exist

##### `leadr.common.services.DomainEntityT`

```python
DomainEntityT = TypeVar('DomainEntityT', bound=Entity)
```

##### `leadr.common.services.RepositoryT`

```python
RepositoryT = TypeVar('RepositoryT', bound=BaseRepository)
```

### `leadr.config`

Application configuration management.

This module defines the configuration settings for the LEADR application using
Pydantic Settings. Configuration values are loaded from environment variables
and .env files, with validation and type checking.

<details class="environment-files" open markdown="1">
<summary>Environment files</summary>

- .env: Production/development configuration (default)
- .env.test: Test environment configuration (when ENV=TEST)

</details>

<details class="example" open markdown="1">
<summary>Example</summary>

Settings are automatically loaded based on the ENV variable:

> > > from leadr.config import settings
> > > settings.API_PREFIX
> > > '/v1'

</details>

**Classes:**

- [**CommonSettings**](#leadr.config.CommonSettings) – Base configuration settings shared across all environments.
- [**Settings**](#leadr.config.Settings) – Production/development environment settings.
- [**TestSettings**](#leadr.config.TestSettings) – Test environment settings.

**Attributes:**

- [**PROJ_ROOT**](#leadr.config.PROJ_ROOT) –
- [**settings**](#leadr.config.settings) –

#### `leadr.config.CommonSettings`

Bases: <code>[BaseSettings](#pydantic_settings.BaseSettings)</code>

Base configuration settings shared across all environments.

This class defines all configuration fields that are common to both
production and test environments. Specific environment classes can
override defaults or add environment-specific settings.

All settings can be configured via environment variables matching the
field names (case-sensitive).

**Functions:**

- [**validate_api_enabled**](#leadr.config.CommonSettings.validate_api_enabled) – Ensure at least one API (Admin or Client) is enabled.

**Attributes:**

- [**API_KEY_SECRET**](#leadr.config.CommonSettings.API_KEY_SECRET) (<code>[str](#str)</code>) –
- [**API_PREFIX**](#leadr.config.CommonSettings.API_PREFIX) (<code>[str](#str)</code>) –
- [**APP**](#leadr.config.CommonSettings.APP) (<code>[str](#str)</code>) –
- [**BASE_URL**](#leadr.config.CommonSettings.BASE_URL) (<code>[HttpUrl](#pydantic.HttpUrl)</code>) –
- [**DASHBOARD_URL**](#leadr.config.CommonSettings.DASHBOARD_URL) (<code>[HttpUrl](#pydantic.HttpUrl)</code>) –
- [**DB_ECHO**](#leadr.config.CommonSettings.DB_ECHO) (<code>[bool](#bool)</code>) –
- [**DB_HOST**](#leadr.config.CommonSettings.DB_HOST) (<code>[str](#str)</code>) –
- [**DB_NAME**](#leadr.config.CommonSettings.DB_NAME) (<code>[str](#str)</code>) –
- [**DB_PASSWORD**](#leadr.config.CommonSettings.DB_PASSWORD) (<code>[str](#str)</code>) –
- [**DB_POOL_MAX_OVERFLOW**](#leadr.config.CommonSettings.DB_POOL_MAX_OVERFLOW) (<code>[int](#int)</code>) –
- [**DB_POOL_RECYCLE**](#leadr.config.CommonSettings.DB_POOL_RECYCLE) (<code>[int](#int)</code>) –
- [**DB_POOL_SIZE**](#leadr.config.CommonSettings.DB_POOL_SIZE) (<code>[int](#int)</code>) –
- [**DB_PORT**](#leadr.config.CommonSettings.DB_PORT) (<code>[int](#int)</code>) –
- [**DB_USER**](#leadr.config.CommonSettings.DB_USER) (<code>[str](#str)</code>) –
- [**DEBUG**](#leadr.config.CommonSettings.DEBUG) (<code>[bool](#bool)</code>) –
- [**ENABLE_ADMIN_API**](#leadr.config.CommonSettings.ENABLE_ADMIN_API) (<code>[bool](#bool)</code>) –
- [**ENABLE_CLIENT_API**](#leadr.config.CommonSettings.ENABLE_CLIENT_API) (<code>[bool](#bool)</code>) –
- [**ENV**](#leadr.config.CommonSettings.ENV) (<code>[str](#str)</code>) –
- [**JWT_LIFETIME_SECONDS**](#leadr.config.CommonSettings.JWT_LIFETIME_SECONDS) (<code>[int](#int)</code>) –
- [**JWT_SECRET**](#leadr.config.CommonSettings.JWT_SECRET) (<code>[str](#str)</code>) –
- [**KEYS_PATH**](#leadr.config.CommonSettings.KEYS_PATH) (<code>[Path](#pathlib.Path)</code>) –
- [**MAILGUN_API_KEY**](#leadr.config.CommonSettings.MAILGUN_API_KEY) (<code>[str](#str)</code>) –
- [**MAILGUN_DOMAIN**](#leadr.config.CommonSettings.MAILGUN_DOMAIN) (<code>[str](#str)</code>) –
- [**SOURCE_OAUTH_BASE_URL**](#leadr.config.CommonSettings.SOURCE_OAUTH_BASE_URL) (<code>[HttpUrl](#pydantic.HttpUrl)</code>) –
- [**TESTING_EMAIL**](#leadr.config.CommonSettings.TESTING_EMAIL) (<code>[str](#str)</code>) –
- [**model_config**](#leadr.config.CommonSettings.model_config) –

##### `leadr.config.CommonSettings.API_KEY_SECRET`

```python
API_KEY_SECRET: str = Field(default='your-super-secret-api-key-pepper-change-in-production', description='Secret pepper for API key hashing. MUST be changed in production.')
```

##### `leadr.config.CommonSettings.API_PREFIX`

```python
API_PREFIX: str = Field(default='/v1', description="API route prefix for versioning (e.g., '/v1')")
```

##### `leadr.config.CommonSettings.APP`

```python
APP: str = Field(default='LEADR', description='Application name identifier')
```

##### `leadr.config.CommonSettings.BASE_URL`

```python
BASE_URL: HttpUrl = Field(default=(HttpUrl('http://localhost:8000')), description="Base URL for the API server (e.g., 'https://api.leadr.gg')")
```

##### `leadr.config.CommonSettings.DASHBOARD_URL`

```python
DASHBOARD_URL: HttpUrl = Field(default=(HttpUrl('http://localhost:8000')), description="URL for the web dashboard (e.g., 'https://dashboard.leadr.gg')")
```

##### `leadr.config.CommonSettings.DB_ECHO`

```python
DB_ECHO: bool = Field(default=False, description='Log all SQL queries to stdout (useful for debugging)')
```

##### `leadr.config.CommonSettings.DB_HOST`

```python
DB_HOST: str = Field(default='localhost', description='PostgreSQL database host')
```

##### `leadr.config.CommonSettings.DB_NAME`

```python
DB_NAME: str = Field(default='leadr', description='PostgreSQL database name')
```

##### `leadr.config.CommonSettings.DB_PASSWORD`

```python
DB_PASSWORD: str = Field(default='leadr', description='PostgreSQL database password')
```

##### `leadr.config.CommonSettings.DB_POOL_MAX_OVERFLOW`

```python
DB_POOL_MAX_OVERFLOW: int = Field(default=10, description='Maximum overflow connections beyond pool size')
```

##### `leadr.config.CommonSettings.DB_POOL_RECYCLE`

```python
DB_POOL_RECYCLE: int = Field(default=3600, description='Recycle database connections after this many seconds (default: 1 hour)')
```

##### `leadr.config.CommonSettings.DB_POOL_SIZE`

```python
DB_POOL_SIZE: int = Field(default=20, description='Number of database connections to maintain in the pool')
```

##### `leadr.config.CommonSettings.DB_PORT`

```python
DB_PORT: int = Field(default=5432, description='PostgreSQL database port')
```

##### `leadr.config.CommonSettings.DB_USER`

```python
DB_USER: str = Field(default='leadr', description='PostgreSQL database user')
```

##### `leadr.config.CommonSettings.DEBUG`

```python
DEBUG: bool = Field(default=False, description='Enable debug mode with verbose logging and error details')
```

##### `leadr.config.CommonSettings.ENABLE_ADMIN_API`

```python
ENABLE_ADMIN_API: bool = Field(default=False, description='Enable admin API endpoints')
```

##### `leadr.config.CommonSettings.ENABLE_CLIENT_API`

```python
ENABLE_CLIENT_API: bool = Field(default=False, description='Enable client API endpoints')
```

##### `leadr.config.CommonSettings.ENV`

```python
ENV: str = Field(default=..., description="Environment name (e.g., 'DEV', 'PROD', 'TEST'). Required.")
```

##### `leadr.config.CommonSettings.JWT_LIFETIME_SECONDS`

```python
JWT_LIFETIME_SECONDS: int = Field(default=3600, description='JWT token lifetime in seconds (default: 1 hour)')
```

##### `leadr.config.CommonSettings.JWT_SECRET`

```python
JWT_SECRET: str = Field(default='your-super-secret-jwt-key-change-in-production', description='Secret key for JWT token signing. MUST be changed in production.')
```

##### `leadr.config.CommonSettings.KEYS_PATH`

```python
KEYS_PATH: Path = Field(default=(PROJ_ROOT / '.keys'), description='Directory path for storing cryptographic keys')
```

##### `leadr.config.CommonSettings.MAILGUN_API_KEY`

```python
MAILGUN_API_KEY: str = Field(default='mailgun_api_key', description='Mailgun API key for email sending')
```

##### `leadr.config.CommonSettings.MAILGUN_DOMAIN`

```python
MAILGUN_DOMAIN: str = Field(default='example.mailgun.org', description='Mailgun domain for email sending')
```

##### `leadr.config.CommonSettings.SOURCE_OAUTH_BASE_URL`

```python
SOURCE_OAUTH_BASE_URL: HttpUrl = Field(default=(HttpUrl('http://localhost:8000')), description='Base URL for OAuth provider')
```

##### `leadr.config.CommonSettings.TESTING_EMAIL`

```python
TESTING_EMAIL: str = Field(default='hello@example.com', description='Email address used for testing purposes')
```

##### `leadr.config.CommonSettings.model_config`

```python
model_config = SettingsConfigDict(case_sensitive=True, extra='ignore')
```

##### `leadr.config.CommonSettings.validate_api_enabled`

```python
validate_api_enabled()
```

Ensure at least one API (Admin or Client) is enabled.

#### `leadr.config.PROJ_ROOT`

```python
PROJ_ROOT = Path(__file__).resolve().parent.parent.parent
```

#### `leadr.config.Settings`

Bases: <code>[CommonSettings](#leadr.config.CommonSettings)</code>

Production/development environment settings.

Inherits all settings from CommonSettings. Loads configuration from
the .env file at the project root.

This is the default settings class used when ENV != 'TEST'.

**Functions:**

- [**validate_api_enabled**](#leadr.config.Settings.validate_api_enabled) – Ensure at least one API (Admin or Client) is enabled.

**Attributes:**

- [**API_KEY_SECRET**](#leadr.config.Settings.API_KEY_SECRET) (<code>[str](#str)</code>) –
- [**API_PREFIX**](#leadr.config.Settings.API_PREFIX) (<code>[str](#str)</code>) –
- [**APP**](#leadr.config.Settings.APP) (<code>[str](#str)</code>) –
- [**BASE_URL**](#leadr.config.Settings.BASE_URL) (<code>[HttpUrl](#pydantic.HttpUrl)</code>) –
- [**DASHBOARD_URL**](#leadr.config.Settings.DASHBOARD_URL) (<code>[HttpUrl](#pydantic.HttpUrl)</code>) –
- [**DB_ECHO**](#leadr.config.Settings.DB_ECHO) (<code>[bool](#bool)</code>) –
- [**DB_HOST**](#leadr.config.Settings.DB_HOST) (<code>[str](#str)</code>) –
- [**DB_NAME**](#leadr.config.Settings.DB_NAME) (<code>[str](#str)</code>) –
- [**DB_PASSWORD**](#leadr.config.Settings.DB_PASSWORD) (<code>[str](#str)</code>) –
- [**DB_POOL_MAX_OVERFLOW**](#leadr.config.Settings.DB_POOL_MAX_OVERFLOW) (<code>[int](#int)</code>) –
- [**DB_POOL_RECYCLE**](#leadr.config.Settings.DB_POOL_RECYCLE) (<code>[int](#int)</code>) –
- [**DB_POOL_SIZE**](#leadr.config.Settings.DB_POOL_SIZE) (<code>[int](#int)</code>) –
- [**DB_PORT**](#leadr.config.Settings.DB_PORT) (<code>[int](#int)</code>) –
- [**DB_USER**](#leadr.config.Settings.DB_USER) (<code>[str](#str)</code>) –
- [**DEBUG**](#leadr.config.Settings.DEBUG) (<code>[bool](#bool)</code>) –
- [**ENABLE_ADMIN_API**](#leadr.config.Settings.ENABLE_ADMIN_API) (<code>[bool](#bool)</code>) –
- [**ENABLE_CLIENT_API**](#leadr.config.Settings.ENABLE_CLIENT_API) (<code>[bool](#bool)</code>) –
- [**ENV**](#leadr.config.Settings.ENV) (<code>[str](#str)</code>) –
- [**JWT_LIFETIME_SECONDS**](#leadr.config.Settings.JWT_LIFETIME_SECONDS) (<code>[int](#int)</code>) –
- [**JWT_SECRET**](#leadr.config.Settings.JWT_SECRET) (<code>[str](#str)</code>) –
- [**KEYS_PATH**](#leadr.config.Settings.KEYS_PATH) (<code>[Path](#pathlib.Path)</code>) –
- [**MAILGUN_API_KEY**](#leadr.config.Settings.MAILGUN_API_KEY) (<code>[str](#str)</code>) –
- [**MAILGUN_DOMAIN**](#leadr.config.Settings.MAILGUN_DOMAIN) (<code>[str](#str)</code>) –
- [**SOURCE_OAUTH_BASE_URL**](#leadr.config.Settings.SOURCE_OAUTH_BASE_URL) (<code>[HttpUrl](#pydantic.HttpUrl)</code>) –
- [**TESTING_EMAIL**](#leadr.config.Settings.TESTING_EMAIL) (<code>[str](#str)</code>) –
- [**model_config**](#leadr.config.Settings.model_config) –

#### `leadr.config.TestSettings`

Bases: <code>[CommonSettings](#leadr.config.CommonSettings)</code>

Test environment settings.

Inherits all settings from CommonSettings. Loads configuration from
the .env.test file at the project root.

Used automatically when ENV='TEST' (set by test.sh script).
Test-specific overrides can be added here.

**Functions:**

- [**validate_api_enabled**](#leadr.config.TestSettings.validate_api_enabled) – Ensure at least one API (Admin or Client) is enabled.

**Attributes:**

- [**API_KEY_SECRET**](#leadr.config.TestSettings.API_KEY_SECRET) (<code>[str](#str)</code>) –
- [**API_PREFIX**](#leadr.config.TestSettings.API_PREFIX) (<code>[str](#str)</code>) –
- [**APP**](#leadr.config.TestSettings.APP) (<code>[str](#str)</code>) –
- [**BASE_URL**](#leadr.config.TestSettings.BASE_URL) (<code>[HttpUrl](#pydantic.HttpUrl)</code>) –
- [**DASHBOARD_URL**](#leadr.config.TestSettings.DASHBOARD_URL) (<code>[HttpUrl](#pydantic.HttpUrl)</code>) –
- [**DB_ECHO**](#leadr.config.TestSettings.DB_ECHO) (<code>[bool](#bool)</code>) –
- [**DB_HOST**](#leadr.config.TestSettings.DB_HOST) (<code>[str](#str)</code>) –
- [**DB_NAME**](#leadr.config.TestSettings.DB_NAME) (<code>[str](#str)</code>) –
- [**DB_PASSWORD**](#leadr.config.TestSettings.DB_PASSWORD) (<code>[str](#str)</code>) –
- [**DB_POOL_MAX_OVERFLOW**](#leadr.config.TestSettings.DB_POOL_MAX_OVERFLOW) (<code>[int](#int)</code>) –
- [**DB_POOL_RECYCLE**](#leadr.config.TestSettings.DB_POOL_RECYCLE) (<code>[int](#int)</code>) –
- [**DB_POOL_SIZE**](#leadr.config.TestSettings.DB_POOL_SIZE) (<code>[int](#int)</code>) –
- [**DB_PORT**](#leadr.config.TestSettings.DB_PORT) (<code>[int](#int)</code>) –
- [**DB_USER**](#leadr.config.TestSettings.DB_USER) (<code>[str](#str)</code>) –
- [**DEBUG**](#leadr.config.TestSettings.DEBUG) (<code>[bool](#bool)</code>) –
- [**ENABLE_ADMIN_API**](#leadr.config.TestSettings.ENABLE_ADMIN_API) (<code>[bool](#bool)</code>) –
- [**ENABLE_CLIENT_API**](#leadr.config.TestSettings.ENABLE_CLIENT_API) (<code>[bool](#bool)</code>) –
- [**ENV**](#leadr.config.TestSettings.ENV) (<code>[str](#str)</code>) –
- [**JWT_LIFETIME_SECONDS**](#leadr.config.TestSettings.JWT_LIFETIME_SECONDS) (<code>[int](#int)</code>) –
- [**JWT_SECRET**](#leadr.config.TestSettings.JWT_SECRET) (<code>[str](#str)</code>) –
- [**KEYS_PATH**](#leadr.config.TestSettings.KEYS_PATH) (<code>[Path](#pathlib.Path)</code>) –
- [**MAILGUN_API_KEY**](#leadr.config.TestSettings.MAILGUN_API_KEY) (<code>[str](#str)</code>) –
- [**MAILGUN_DOMAIN**](#leadr.config.TestSettings.MAILGUN_DOMAIN) (<code>[str](#str)</code>) –
- [**SOURCE_OAUTH_BASE_URL**](#leadr.config.TestSettings.SOURCE_OAUTH_BASE_URL) (<code>[HttpUrl](#pydantic.HttpUrl)</code>) –
- [**TESTING_EMAIL**](#leadr.config.TestSettings.TESTING_EMAIL) (<code>[str](#str)</code>) –
- [**model_config**](#leadr.config.TestSettings.model_config) –

#### `leadr.config.settings`

```python
settings = TestSettings(_env_file=(Path(PROJ_ROOT, '.env.test'))) if os.environ.get('ENV') == 'TEST' else Settings(_env_file=(Path(PROJ_ROOT, '.env')))
```

### `leadr.games`

**Modules:**

- [**adapters**](#leadr.games.adapters) –
- [**api**](#leadr.games.api) –
- [**domain**](#leadr.games.domain) –
- [**services**](#leadr.games.services) –

#### `leadr.games.adapters`

**Modules:**

- [**orm**](#leadr.games.adapters.orm) – Game ORM model.

##### `leadr.games.adapters.orm`

Game ORM model.

**Classes:**

- [**GameORM**](#leadr.games.adapters.orm.GameORM) – Game ORM model.

###### `leadr.games.adapters.orm.GameORM`

Bases: <code>[Base](#leadr.common.orm.Base)</code>

Game ORM model.

Represents a game that belongs to an account in the database.
Maps to the games table with foreign key to accounts and unique
constraint on (account_id, name) to prevent duplicate game names
within the same account.

**Attributes:**

- [**account**](#leadr.games.adapters.orm.GameORM.account) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[AccountORM](#leadr.accounts.adapters.orm.AccountORM)\]</code>) –
- [**account_id**](#leadr.games.adapters.orm.GameORM.account_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**created_at**](#leadr.games.adapters.orm.GameORM.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](#leadr.common.orm.timestamp)\]</code>) –
- [**default_board_id**](#leadr.games.adapters.orm.GameORM.default_board_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID) | None\]</code>) –
- [**deleted_at**](#leadr.games.adapters.orm.GameORM.deleted_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[nullable_timestamp](#leadr.common.orm.nullable_timestamp)\]</code>) –
- [**id**](#leadr.games.adapters.orm.GameORM.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**name**](#leadr.games.adapters.orm.GameORM.name) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**steam_app_id**](#leadr.games.adapters.orm.GameORM.steam_app_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**updated_at**](#leadr.games.adapters.orm.GameORM.updated_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](#leadr.common.orm.timestamp)\]</code>) –

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

- [**routes**](#leadr.games.api.routes) – Game API routes.
- [**schemas**](#leadr.games.api.schemas) – API request and response models for games.

##### `leadr.games.api.routes`

Game API routes.

**Functions:**

- [**create_game**](#leadr.games.api.routes.create_game) – Create a new game.
- [**get_game**](#leadr.games.api.routes.get_game) – Get a game by ID.
- [**list_games**](#leadr.games.api.routes.list_games) – List all games for an account.
- [**update_game**](#leadr.games.api.routes.update_game) – Update a game.

**Attributes:**

- [**router**](#leadr.games.api.routes.router) –

###### `leadr.games.api.routes.create_game`

```python
create_game(request, service)
```

Create a new game.

Creates a new game associated with an existing account. Games can optionally
be configured with Steam integration and a default leaderboard.

**Parameters:**

- **request** (<code>[GameCreateRequest](#leadr.games.api.schemas.GameCreateRequest)</code>) – Game creation details including account_id, name, and optional settings.
- **service** (<code>[GameServiceDep](#leadr.games.services.dependencies.GameServiceDep)</code>) – Injected game service dependency.

**Returns:**

- <code>[GameResponse](#leadr.games.api.schemas.GameResponse)</code> – GameResponse with the created game including auto-generated ID and timestamps.

**Raises:**

- <code>404</code> – Account not found.

###### `leadr.games.api.routes.get_game`

```python
get_game(game_id, service)
```

Get a game by ID.

**Parameters:**

- **game_id** (<code>[UUID](#uuid.UUID)</code>) – Unique identifier for the game.
- **service** (<code>[GameServiceDep](#leadr.games.services.dependencies.GameServiceDep)</code>) – Injected game service dependency.

**Returns:**

- <code>[GameResponse](#leadr.games.api.schemas.GameResponse)</code> – GameResponse with full game details.

**Raises:**

- <code>404</code> – Game not found.

###### `leadr.games.api.routes.list_games`

```python
list_games(account_id, service)
```

List all games for an account.

**Parameters:**

- **account_id** (<code>[UUID](#uuid.UUID)</code>) – Account ID to filter games by.
- **service** (<code>[GameServiceDep](#leadr.games.services.dependencies.GameServiceDep)</code>) – Injected game service dependency.

**Returns:**

- <code>[list](#list)\[[GameResponse](#leadr.games.api.schemas.GameResponse)\]</code> – List of all active games for the specified account.

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
- **request** (<code>[GameUpdateRequest](#leadr.games.api.schemas.GameUpdateRequest)</code>) – Game update details (all fields optional).
- **service** (<code>[GameServiceDep](#leadr.games.services.dependencies.GameServiceDep)</code>) – Injected game service dependency.

**Returns:**

- <code>[GameResponse](#leadr.games.api.schemas.GameResponse)</code> – GameResponse with the updated game details.

**Raises:**

- <code>404</code> – Game not found.

##### `leadr.games.api.schemas`

API request and response models for games.

**Classes:**

- [**GameCreateRequest**](#leadr.games.api.schemas.GameCreateRequest) – Request model for creating a game.
- [**GameResponse**](#leadr.games.api.schemas.GameResponse) – Response model for a game.
- [**GameUpdateRequest**](#leadr.games.api.schemas.GameUpdateRequest) – Request model for updating a game.

###### `leadr.games.api.schemas.GameCreateRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request model for creating a game.

**Attributes:**

- [**account_id**](#leadr.games.api.schemas.GameCreateRequest.account_id) (<code>[UUID](#uuid.UUID)</code>) –
- [**default_board_id**](#leadr.games.api.schemas.GameCreateRequest.default_board_id) (<code>[UUID](#uuid.UUID) | None</code>) –
- [**name**](#leadr.games.api.schemas.GameCreateRequest.name) (<code>[str](#str)</code>) –
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
- [**id**](#leadr.games.api.schemas.GameResponse.id) (<code>[UUID](#uuid.UUID)</code>) –
- [**name**](#leadr.games.api.schemas.GameResponse.name) (<code>[str](#str)</code>) –
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

- **game** (<code>[Game](#leadr.games.domain.game.Game)</code>) – The domain Game entity to convert.

**Returns:**

- <code>[GameResponse](#leadr.games.api.schemas.GameResponse)</code> – GameResponse with all fields populated from the domain entity.

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
- [**deleted**](#leadr.games.api.schemas.GameUpdateRequest.deleted) (<code>[bool](#bool) | None</code>) –
- [**name**](#leadr.games.api.schemas.GameUpdateRequest.name) (<code>[str](#str) | None</code>) –
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

- [**game**](#leadr.games.domain.game) – Game domain model.

##### `leadr.games.domain.game`

Game domain model.

**Classes:**

- [**Game**](#leadr.games.domain.game.Game) – Game domain entity.

###### `leadr.games.domain.game.Game`

Bases: <code>[Entity](#leadr.common.domain.models.Entity)</code>

Game domain entity.

Represents a game that belongs to an account. Games can have optional
Steam integration via steam_app_id and can reference a default leaderboard.

Each game belongs to exactly one account and cannot be transferred. Games
can be configured with Steam integration for syncing achievements or other
Steam platform features.

**Functions:**

- [**restore**](#leadr.games.domain.game.Game.restore) – Restore a soft-deleted entity.
- [**soft_delete**](#leadr.games.domain.game.Game.soft_delete) – Mark entity as soft-deleted.
- [**validate_name**](#leadr.games.domain.game.Game.validate_name) – Validate game name is not empty.

**Attributes:**

- [**account_id**](#leadr.games.domain.game.Game.account_id) (<code>[UUID](#uuid.UUID)</code>) –
- [**created_at**](#leadr.games.domain.game.Game.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**default_board_id**](#leadr.games.domain.game.Game.default_board_id) (<code>[UUID](#uuid.UUID) | None</code>) –
- [**deleted_at**](#leadr.games.domain.game.Game.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**id**](#leadr.games.domain.game.Game.id) (<code>[UUID](#uuid.UUID)</code>) –
- [**is_deleted**](#leadr.games.domain.game.Game.is_deleted) (<code>[bool](#bool)</code>) – Check if entity is soft-deleted.
- [**model_config**](#leadr.games.domain.game.Game.model_config) –
- [**name**](#leadr.games.domain.game.Game.name) (<code>[str](#str)</code>) –
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

- [**dependencies**](#leadr.games.services.dependencies) – Game service dependencies for FastAPI dependency injection.
- [**game_service**](#leadr.games.services.game_service) – Game service for managing game operations.
- [**repositories**](#leadr.games.services.repositories) – Game repository services.

##### `leadr.games.services.dependencies`

Game service dependencies for FastAPI dependency injection.

**Functions:**

- [**get_game_service**](#leadr.games.services.dependencies.get_game_service) – Get GameService dependency.

**Attributes:**

- [**GameServiceDep**](#leadr.games.services.dependencies.GameServiceDep) –

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

Bases: <code>[BaseService](#leadr.common.services.BaseService)\[[Game](#leadr.games.domain.game.Game), [GameRepository](#leadr.games.services.repositories.GameRepository)\]</code>

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

- <code>[Game](#leadr.games.domain.game.Game)</code> – The created Game domain entity.

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

- <code>[EntityNotFoundError](#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the entity doesn't exist

####### `leadr.games.services.game_service.GameService.get_by_id`

```python
get_by_id(entity_id)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the entity to retrieve

**Returns:**

- <code>[DomainEntityT](#leadr.common.services.DomainEntityT) | None</code> – The domain entity if found, None otherwise

####### `leadr.games.services.game_service.GameService.get_by_id_or_raise`

```python
get_by_id_or_raise(entity_id)
```

Get an entity by its ID or raise EntityNotFoundError.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the entity to retrieve

**Returns:**

- <code>[DomainEntityT](#leadr.common.services.DomainEntityT)</code> – The domain entity

**Raises:**

- <code>[EntityNotFoundError](#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the entity is not found
  (converted to HTTP 404 by global handler)

####### `leadr.games.services.game_service.GameService.get_game`

```python
get_game(game_id)
```

Get a game by its ID.

**Parameters:**

- **game_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the game to retrieve.

**Returns:**

- <code>[Game](#leadr.games.domain.game.Game) | None</code> – The Game domain entity if found, None otherwise.

####### `leadr.games.services.game_service.GameService.list_all`

```python
list_all()
```

List all non-deleted entities.

**Returns:**

- <code>[list](#list)\[[DomainEntityT](#leadr.common.services.DomainEntityT)\]</code> – List of domain entities

####### `leadr.games.services.game_service.GameService.list_games`

```python
list_games(account_id)
```

List all games for an account.

**Parameters:**

- **account_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the account to list games for.

**Returns:**

- <code>[list](#list)\[[Game](#leadr.games.domain.game.Game)\]</code> – List of Game domain entities for the account.

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

- <code>[DomainEntityT](#leadr.common.services.DomainEntityT)</code> – The entity before it was deleted

**Raises:**

- <code>[EntityNotFoundError](#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the entity doesn't exist

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

- <code>[Game](#leadr.games.domain.game.Game)</code> – The updated Game domain entity

**Raises:**

- <code>[EntityNotFoundError](#EntityNotFoundError)</code> – If the game doesn't exist

##### `leadr.games.services.repositories`

Game repository services.

**Classes:**

- [**GameRepository**](#leadr.games.services.repositories.GameRepository) – Game repository for managing game persistence.

###### `leadr.games.services.repositories.GameRepository`

Bases: <code>[BaseRepository](#leadr.common.repositories.BaseRepository)\[[Game](#leadr.games.domain.game.Game), [GameORM](#leadr.games.adapters.orm.GameORM)\]</code>

Game repository for managing game persistence.

**Functions:**

- [**create**](#leadr.games.services.repositories.GameRepository.create) – Create a new entity in the database.
- [**delete**](#leadr.games.services.repositories.GameRepository.delete) – Soft delete an entity by setting its deleted_at timestamp.
- [**filter**](#leadr.games.services.repositories.GameRepository.filter) – Filter games by account and optional criteria.
- [**get_by_id**](#leadr.games.services.repositories.GameRepository.get_by_id) – Get an entity by its ID.
- [**update**](#leadr.games.services.repositories.GameRepository.update) – Update an existing entity in the database.

**Attributes:**

- [**session**](#leadr.games.services.repositories.GameRepository.session) –

####### `leadr.games.services.repositories.GameRepository.create`

```python
create(entity)
```

Create a new entity in the database.

**Parameters:**

- **entity** (<code>[DomainEntityT](#leadr.common.repositories.DomainEntityT)</code>) – Domain entity to create

**Returns:**

- <code>[DomainEntityT](#leadr.common.repositories.DomainEntityT)</code> – Created domain entity with refreshed data

####### `leadr.games.services.repositories.GameRepository.delete`

```python
delete(entity_id)
```

Soft delete an entity by setting its deleted_at timestamp.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4)</code>) – ID of entity to delete

**Raises:**

- <code>[EntityNotFoundError](#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

####### `leadr.games.services.repositories.GameRepository.filter`

```python
filter(account_id, **kwargs)
```

Filter games by account and optional criteria.

**Parameters:**

- **account_id** (<code>[UUID4](#pydantic.UUID4)</code>) – REQUIRED - Account ID to filter by (multi-tenant safety)
- \*\***kwargs** (<code>[Any](#typing.Any)</code>) – Additional filter parameters (reserved for future use)

**Returns:**

- <code>[list](#list)\[[Game](#leadr.games.domain.game.Game)\]</code> – List of games for the account matching the filter criteria

####### `leadr.games.services.repositories.GameRepository.get_by_id`

```python
get_by_id(entity_id, include_deleted=False)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4)</code>) – Entity ID to retrieve
- **include_deleted** (<code>[bool](#bool)</code>) – If True, include soft-deleted entities. Defaults to False.

**Returns:**

- <code>[DomainEntityT](#leadr.common.repositories.DomainEntityT) | None</code> – Domain entity if found, None otherwise

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

- **entity** (<code>[DomainEntityT](#leadr.common.repositories.DomainEntityT)</code>) – Domain entity with updated data

**Returns:**

- <code>[DomainEntityT](#leadr.common.repositories.DomainEntityT)</code> – Updated domain entity with refreshed data

**Raises:**

- <code>[EntityNotFoundError](#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

### `leadr.infra`

**Modules:**

- [**blob_storage**](#leadr.infra.blob_storage) –
- [**cache**](#leadr.infra.cache) –

#### `leadr.infra.blob_storage`

**Modules:**

- [**adapters**](#leadr.infra.blob_storage.adapters) –
- [**domain**](#leadr.infra.blob_storage.domain) –
- [**services**](#leadr.infra.blob_storage.services) –

##### `leadr.infra.blob_storage.adapters`

##### `leadr.infra.blob_storage.domain`

##### `leadr.infra.blob_storage.services`

#### `leadr.infra.cache`

**Modules:**

- [**adapters**](#leadr.infra.cache.adapters) –
- [**domain**](#leadr.infra.cache.domain) –
- [**services**](#leadr.infra.cache.services) –

##### `leadr.infra.cache.adapters`

##### `leadr.infra.cache.domain`

##### `leadr.infra.cache.services`

### `leadr.players`

**Modules:**

- [**adapters**](#leadr.players.adapters) –
- [**api**](#leadr.players.api) –
- [**domain**](#leadr.players.domain) –

#### `leadr.players.adapters`

#### `leadr.players.api`

#### `leadr.players.domain`

### `leadr.scores`

**Modules:**

- [**adapters**](#leadr.scores.adapters) –
- [**api**](#leadr.scores.api) –
- [**domain**](#leadr.scores.domain) –
- [**services**](#leadr.scores.services) –

#### `leadr.scores.adapters`

#### `leadr.scores.api`

#### `leadr.scores.domain`

#### `leadr.scores.services`
