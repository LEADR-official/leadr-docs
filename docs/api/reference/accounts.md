### `leadr.accounts`

**Modules:**

- [**adapters**](./accounts.md#leadr.accounts.adapters) –
- [**api**](./accounts.md#leadr.accounts.api) –
- [**domain**](./accounts.md#leadr.accounts.domain) –

#### `leadr.accounts.adapters`

**Modules:**

- [**orm**](./accounts.md#leadr.accounts.adapters.orm) – Account and User ORM models.

##### `leadr.accounts.adapters.orm`

Account and User ORM models.

**Classes:**

- [**AccountORM**](./accounts.md#leadr.accounts.adapters.orm.AccountORM) – Account ORM model.
- [**AccountStatusEnum**](./accounts.md#leadr.accounts.adapters.orm.AccountStatusEnum) – Account status enum for database.
- [**UserORM**](./accounts.md#leadr.accounts.adapters.orm.UserORM) – User ORM model.

###### `leadr.accounts.adapters.orm.AccountORM`

Bases: <code>[Base](./common.md#leadr.common.orm.Base)</code>

Account ORM model.

Represents an organization or team in the database.
Maps to the accounts table with unique name and slug constraints.

**Attributes:**

- [**created_at**](#leadr.accounts.adapters.orm.AccountORM.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**deleted_at**](#leadr.accounts.adapters.orm.AccountORM.deleted_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[nullable_timestamp](#leadr.common.orm.nullable_timestamp)\]</code>) –
- [**id**](./accounts.md#leadr.accounts.adapters.orm.AccountORM.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**name**](./accounts.md#leadr.accounts.adapters.orm.AccountORM.name) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**slug**](./accounts.md#leadr.accounts.adapters.orm.AccountORM.slug) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**status**](./accounts.md#leadr.accounts.adapters.orm.AccountORM.status) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[AccountStatusEnum](./accounts.md#leadr.accounts.adapters.orm.AccountStatusEnum)\]</code>) –
- [**updated_at**](#leadr.accounts.adapters.orm.AccountORM.updated_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**users**](./accounts.md#leadr.accounts.adapters.orm.AccountORM.users) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[list](#list)\[[UserORM](./accounts.md#leadr.accounts.adapters.orm.UserORM)\]\]</code>) –

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

- [**ACTIVE**](./accounts.md#leadr.accounts.adapters.orm.AccountStatusEnum.ACTIVE) –
- [**SUSPENDED**](./accounts.md#leadr.accounts.adapters.orm.AccountStatusEnum.SUSPENDED) –

####### `leadr.accounts.adapters.orm.AccountStatusEnum.ACTIVE`

```python
ACTIVE = 'active'
```

####### `leadr.accounts.adapters.orm.AccountStatusEnum.SUSPENDED`

```python
SUSPENDED = 'suspended'
```

###### `leadr.accounts.adapters.orm.UserORM`

Bases: <code>[Base](./common.md#leadr.common.orm.Base)</code>

User ORM model.

Represents a user within an account in the database.
Maps to the users table with foreign key to accounts.

**Attributes:**

- [**account**](./accounts.md#leadr.accounts.adapters.orm.UserORM.account) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[AccountORM](./accounts.md#leadr.accounts.adapters.orm.AccountORM)\]</code>) –
- [**account_id**](#leadr.accounts.adapters.orm.UserORM.account_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**created_at**](#leadr.accounts.adapters.orm.UserORM.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**deleted_at**](#leadr.accounts.adapters.orm.UserORM.deleted_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[nullable_timestamp](#leadr.common.orm.nullable_timestamp)\]</code>) –
- [**display_name**](#leadr.accounts.adapters.orm.UserORM.display_name) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**email**](./accounts.md#leadr.accounts.adapters.orm.UserORM.email) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**id**](./accounts.md#leadr.accounts.adapters.orm.UserORM.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**updated_at**](#leadr.accounts.adapters.orm.UserORM.updated_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –

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

- [**routes**](./accounts.md#leadr.accounts.api.routes) – Account and User API routes.
- [**schemas**](./accounts.md#leadr.accounts.api.schemas) – API request and response models for accounts.

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

- [**router**](./accounts.md#leadr.accounts.api.routes.router) –

###### `leadr.accounts.api.routes.create_account`

```python
create_account(request, service)
```

Create a new account.

**Parameters:**

- **request** (<code>[AccountCreateRequest](./accounts.md#leadr.accounts.api.schemas.AccountCreateRequest)</code>) – Account creation details including name and slug.
- **service** (<code>[AccountServiceDep](#leadr.accounts.services.dependencies.AccountServiceDep)</code>) – Injected account service dependency.

**Returns:**

- <code>[AccountResponse](./accounts.md#leadr.accounts.api.schemas.AccountResponse)</code> – AccountResponse with the created account including auto-generated ID and timestamps.

###### `leadr.accounts.api.routes.create_user`

```python
create_user(request, service)
```

Create a new user.

Creates a new user associated with an existing account.

**Parameters:**

- **request** (<code>[UserCreateRequest](./accounts.md#leadr.accounts.api.schemas.UserCreateRequest)</code>) – User creation details including account_id, email, and display name.
- **service** (<code>[UserServiceDep](#leadr.accounts.services.dependencies.UserServiceDep)</code>) – Injected user service dependency.

**Returns:**

- <code>[UserResponse](./accounts.md#leadr.accounts.api.schemas.UserResponse)</code> – UserResponse with the created user including auto-generated ID and timestamps.

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

- <code>[AccountResponse](./accounts.md#leadr.accounts.api.schemas.AccountResponse)</code> – AccountResponse with full account details.

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

- <code>[UserResponse](./accounts.md#leadr.accounts.api.schemas.UserResponse)</code> – UserResponse with full user details.

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

- <code>[list](#list)\[[AccountResponse](./accounts.md#leadr.accounts.api.schemas.AccountResponse)\]</code> – List of all active accounts.

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

- <code>[list](#list)\[[UserResponse](./accounts.md#leadr.accounts.api.schemas.UserResponse)\]</code> – List of users for the account.

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
- **request** (<code>[AccountUpdateRequest](./accounts.md#leadr.accounts.api.schemas.AccountUpdateRequest)</code>) – Account update details (all fields optional).
- **service** (<code>[AccountServiceDep](#leadr.accounts.services.dependencies.AccountServiceDep)</code>) – Injected account service dependency.

**Returns:**

- <code>[AccountResponse](./accounts.md#leadr.accounts.api.schemas.AccountResponse)</code> – AccountResponse with the updated account details.

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
- **request** (<code>[UserUpdateRequest](./accounts.md#leadr.accounts.api.schemas.UserUpdateRequest)</code>) – User update details (all fields optional).
- **service** (<code>[UserServiceDep](#leadr.accounts.services.dependencies.UserServiceDep)</code>) – Injected user service dependency.

**Returns:**

- <code>[UserResponse](./accounts.md#leadr.accounts.api.schemas.UserResponse)</code> – UserResponse with the updated user details.

**Raises:**

- <code>404</code> – User not found.

##### `leadr.accounts.api.schemas`

API request and response models for accounts.

**Classes:**

- [**AccountCreateRequest**](./accounts.md#leadr.accounts.api.schemas.AccountCreateRequest) – Request model for creating an account.
- [**AccountResponse**](./accounts.md#leadr.accounts.api.schemas.AccountResponse) – Response model for an account.
- [**AccountUpdateRequest**](./accounts.md#leadr.accounts.api.schemas.AccountUpdateRequest) – Request model for updating an account.
- [**UserCreateRequest**](./accounts.md#leadr.accounts.api.schemas.UserCreateRequest) – Request model for creating a user.
- [**UserResponse**](./accounts.md#leadr.accounts.api.schemas.UserResponse) – Response model for a user.
- [**UserUpdateRequest**](./accounts.md#leadr.accounts.api.schemas.UserUpdateRequest) – Request model for updating a user.

###### `leadr.accounts.api.schemas.AccountCreateRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request model for creating an account.

**Attributes:**

- [**name**](./accounts.md#leadr.accounts.api.schemas.AccountCreateRequest.name) (<code>[str](#str)</code>) –
- [**slug**](./accounts.md#leadr.accounts.api.schemas.AccountCreateRequest.slug) (<code>[str](#str)</code>) –

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
- [**id**](./accounts.md#leadr.accounts.api.schemas.AccountResponse.id) (<code>[UUID](#uuid.UUID)</code>) –
- [**name**](./accounts.md#leadr.accounts.api.schemas.AccountResponse.name) (<code>[str](#str)</code>) –
- [**slug**](./accounts.md#leadr.accounts.api.schemas.AccountResponse.slug) (<code>[str](#str)</code>) –
- [**status**](./accounts.md#leadr.accounts.api.schemas.AccountResponse.status) (<code>[AccountStatus](./accounts.md#leadr.accounts.domain.account.AccountStatus)</code>) –
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

- **account** (<code>[Account](./accounts.md#leadr.accounts.domain.account.Account)</code>) – The domain Account entity to convert.

**Returns:**

- <code>[AccountResponse](./accounts.md#leadr.accounts.api.schemas.AccountResponse)</code> – AccountResponse with all fields populated from the domain entity.

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

- [**deleted**](./accounts.md#leadr.accounts.api.schemas.AccountUpdateRequest.deleted) (<code>[bool](#bool) | None</code>) –
- [**name**](./accounts.md#leadr.accounts.api.schemas.AccountUpdateRequest.name) (<code>[str](#str) | None</code>) –
- [**slug**](./accounts.md#leadr.accounts.api.schemas.AccountUpdateRequest.slug) (<code>[str](#str) | None</code>) –
- [**status**](./accounts.md#leadr.accounts.api.schemas.AccountUpdateRequest.status) (<code>[AccountStatus](./accounts.md#leadr.accounts.domain.account.AccountStatus) | None</code>) –

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
- [**email**](./accounts.md#leadr.accounts.api.schemas.UserCreateRequest.email) (<code>[EmailStr](#pydantic.EmailStr)</code>) –

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
- [**email**](./accounts.md#leadr.accounts.api.schemas.UserResponse.email) (<code>[str](#str)</code>) –
- [**id**](./accounts.md#leadr.accounts.api.schemas.UserResponse.id) (<code>[UUID](#uuid.UUID)</code>) –
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

- **user** (<code>[User](./accounts.md#leadr.accounts.domain.user.User)</code>) – The domain User entity to convert.

**Returns:**

- <code>[UserResponse](./accounts.md#leadr.accounts.api.schemas.UserResponse)</code> – UserResponse with all fields populated from the domain entity.

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

- [**deleted**](./accounts.md#leadr.accounts.api.schemas.UserUpdateRequest.deleted) (<code>[bool](#bool) | None</code>) –
- [**display_name**](#leadr.accounts.api.schemas.UserUpdateRequest.display_name) (<code>[str](#str) | None</code>) –
- [**email**](./accounts.md#leadr.accounts.api.schemas.UserUpdateRequest.email) (<code>[EmailStr](#pydantic.EmailStr) | None</code>) –

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

- [**account**](./accounts.md#leadr.accounts.domain.account) – Account domain model.
- [**user**](./accounts.md#leadr.accounts.domain.user) – User domain model.

##### `leadr.accounts.domain.account`

Account domain model.

**Classes:**

- [**Account**](./accounts.md#leadr.accounts.domain.account.Account) – Account domain entity.
- [**AccountStatus**](./accounts.md#leadr.accounts.domain.account.AccountStatus) – Account status enumeration.

###### `leadr.accounts.domain.account.Account`

Bases: <code>[Entity](./common.md#leadr.common.domain.models.Entity)</code>

Account domain entity.

Represents an organization or team that owns games and manages users.
Accounts have a unique name and URL-friendly slug, and can be
active or suspended.

**Functions:**

- [**activate**](./accounts.md#leadr.accounts.domain.account.Account.activate) – Activate the account, allowing access.
- [**restore**](./accounts.md#leadr.accounts.domain.account.Account.restore) – Restore a soft-deleted entity.
- [**soft_delete**](#leadr.accounts.domain.account.Account.soft_delete) – Mark entity as soft-deleted.
- [**suspend**](./accounts.md#leadr.accounts.domain.account.Account.suspend) – Suspend the account, preventing access.
- [**validate_name**](#leadr.accounts.domain.account.Account.validate_name) – Validate account name length and format.
- [**validate_slug**](#leadr.accounts.domain.account.Account.validate_slug) – Validate slug format (lowercase alphanumeric with hyphens).

**Attributes:**

- [**created_at**](#leadr.accounts.domain.account.Account.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**deleted_at**](#leadr.accounts.domain.account.Account.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**id**](./accounts.md#leadr.accounts.domain.account.Account.id) (<code>[UUID](#uuid.UUID)</code>) –
- [**is_deleted**](#leadr.accounts.domain.account.Account.is_deleted) (<code>[bool](#bool)</code>) – Check if entity is soft-deleted.
- [**model_config**](#leadr.accounts.domain.account.Account.model_config) –
- [**name**](./accounts.md#leadr.accounts.domain.account.Account.name) (<code>[str](#str)</code>) –
- [**slug**](./accounts.md#leadr.accounts.domain.account.Account.slug) (<code>[str](#str)</code>) –
- [**status**](./accounts.md#leadr.accounts.domain.account.Account.status) (<code>[AccountStatus](./accounts.md#leadr.accounts.domain.account.AccountStatus)</code>) –
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

- [**ACTIVE**](./accounts.md#leadr.accounts.domain.account.AccountStatus.ACTIVE) –
- [**SUSPENDED**](./accounts.md#leadr.accounts.domain.account.AccountStatus.SUSPENDED) –

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

- [**User**](./accounts.md#leadr.accounts.domain.user.User) – User domain entity.

###### `leadr.accounts.domain.user.User`

Bases: <code>[Entity](./common.md#leadr.common.domain.models.Entity)</code>

User domain entity.

Represents a user within an account (organization/team).
Users are scoped to a specific account and have an email
address and display name.

Each user belongs to exactly one account, and users cannot be
transferred between accounts. The email must be unique within
an account.

**Functions:**

- [**restore**](./accounts.md#leadr.accounts.domain.user.User.restore) – Restore a soft-deleted entity.
- [**soft_delete**](#leadr.accounts.domain.user.User.soft_delete) – Mark entity as soft-deleted.
- [**validate_display_name**](#leadr.accounts.domain.user.User.validate_display_name) – Validate display name length and format.

**Attributes:**

- [**account_id**](#leadr.accounts.domain.user.User.account_id) (<code>[UUID](#uuid.UUID)</code>) –
- [**created_at**](#leadr.accounts.domain.user.User.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**deleted_at**](#leadr.accounts.domain.user.User.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**display_name**](#leadr.accounts.domain.user.User.display_name) (<code>[str](#str)</code>) –
- [**email**](./accounts.md#leadr.accounts.domain.user.User.email) (<code>[EmailStr](#pydantic.EmailStr)</code>) –
- [**id**](./accounts.md#leadr.accounts.domain.user.User.id) (<code>[UUID](#uuid.UUID)</code>) –
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
