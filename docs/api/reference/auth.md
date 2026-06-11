### `leadr.auth`

**Modules:**

- [**adapters**](./auth.md#leadr.auth.adapters) –
- [**api**](./auth.md#leadr.auth.api) –
- [**bootstrap**](./auth.md#leadr.auth.bootstrap) – Superadmin bootstrap functionality.
- [**dependencies**](./auth.md#leadr.auth.dependencies) – Authentication dependencies for FastAPI.
- [**domain**](./auth.md#leadr.auth.domain) –
- [**services**](./auth.md#leadr.auth.services) –

#### `leadr.auth.adapters`

**Modules:**

- [**orm**](./auth.md#leadr.auth.adapters.orm) – Auth ORM models.

##### `leadr.auth.adapters.orm`

Auth ORM models.

**Classes:**

- [**APIKeyORM**](./auth.md#leadr.auth.adapters.orm.APIKeyORM) – API Key ORM model.
- [**APIKeyStatusEnum**](./auth.md#leadr.auth.adapters.orm.APIKeyStatusEnum) – API Key status enum for database.
- [**DeviceORM**](./auth.md#leadr.auth.adapters.orm.DeviceORM) – Device ORM model.
- [**DeviceStatusEnum**](./auth.md#leadr.auth.adapters.orm.DeviceStatusEnum) – Device status enum for database.
- [**IdentityKindEnum**](./auth.md#leadr.auth.adapters.orm.IdentityKindEnum) – Identity kind enum for database.
- [**IdentityORM**](./auth.md#leadr.auth.adapters.orm.IdentityORM) – Identity ORM model.
- [**IdentitySessionORM**](./auth.md#leadr.auth.adapters.orm.IdentitySessionORM) – IdentitySession ORM model.
- [**NonceORM**](./auth.md#leadr.auth.adapters.orm.NonceORM) – Nonce ORM model.
- [**NonceStatusEnum**](./auth.md#leadr.auth.adapters.orm.NonceStatusEnum) – Nonce status enum for database.

###### `leadr.auth.adapters.orm.APIKeyORM`

Bases: <code>[Base](./common.md#leadr.common.orm.Base)</code>

API Key ORM model.

Represents an API key for account authentication in the database.
Maps to the api_keys table with foreign key to accounts and users.
Each API key is owned by a specific user within the account.

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
- [**user_id**](#leadr.auth.adapters.orm.APIKeyORM.user_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –

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

####### `leadr.auth.adapters.orm.APIKeyORM.user_id`

```python
user_id: Mapped[UUID] = mapped_column(ForeignKey('users.id', ondelete='CASCADE'), nullable=False, index=True)
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

###### `leadr.auth.adapters.orm.DeviceORM`

Bases: <code>[Base](./common.md#leadr.common.orm.Base)</code>

Device ORM model.

Represents a game client device (e.g., mobile device, PC, console) in the database.
Maps to the devices table with foreign key to games.
Devices are scoped per-game for client authentication.

**Functions:**

- [**from_domain**](#leadr.auth.adapters.orm.DeviceORM.from_domain) – Convert Device domain entity to ORM model.
- [**to_domain**](#leadr.auth.adapters.orm.DeviceORM.to_domain) – Convert ORM model to Device domain entity.

**Attributes:**

- [**account_id**](#leadr.auth.adapters.orm.DeviceORM.account_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**client_fingerprint**](#leadr.auth.adapters.orm.DeviceORM.client_fingerprint) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**created_at**](#leadr.auth.adapters.orm.DeviceORM.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**deleted_at**](#leadr.auth.adapters.orm.DeviceORM.deleted_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[nullable_timestamp](#leadr.common.orm.nullable_timestamp)\]</code>) –
- [**device_metadata**](#leadr.auth.adapters.orm.DeviceORM.device_metadata) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[dict](#dict)\[[str](#str), [Any](#typing.Any)\]\]</code>) –
- [**first_seen_at**](#leadr.auth.adapters.orm.DeviceORM.first_seen_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime)\]</code>) –
- [**game**](./auth.md#leadr.auth.adapters.orm.DeviceORM.game) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[GameORM](./games.md#leadr.games.adapters.orm.GameORM)\]</code>) –
- [**game_id**](#leadr.auth.adapters.orm.DeviceORM.game_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**id**](./auth.md#leadr.auth.adapters.orm.DeviceORM.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**last_seen_at**](#leadr.auth.adapters.orm.DeviceORM.last_seen_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime)\]</code>) –
- [**platform**](./auth.md#leadr.auth.adapters.orm.DeviceORM.platform) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**status**](./auth.md#leadr.auth.adapters.orm.DeviceORM.status) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[DeviceStatusEnum](./auth.md#leadr.auth.adapters.orm.DeviceStatusEnum)\]</code>) –
- [**updated_at**](#leadr.auth.adapters.orm.DeviceORM.updated_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –

####### `leadr.auth.adapters.orm.DeviceORM.account_id`

```python
account_id: Mapped[UUID] = mapped_column(nullable=False, index=True)
```

####### `leadr.auth.adapters.orm.DeviceORM.client_fingerprint`

```python
client_fingerprint: Mapped[str] = mapped_column(String(64), nullable=False)
```

####### `leadr.auth.adapters.orm.DeviceORM.created_at`

```python
created_at: Mapped[timestamp]
```

####### `leadr.auth.adapters.orm.DeviceORM.deleted_at`

```python
deleted_at: Mapped[nullable_timestamp]
```

####### `leadr.auth.adapters.orm.DeviceORM.device_metadata`

```python
device_metadata: Mapped[dict[str, Any]] = mapped_column('metadata', JSON, nullable=False, default=dict, server_default='{}')
```

####### `leadr.auth.adapters.orm.DeviceORM.first_seen_at`

```python
first_seen_at: Mapped[datetime] = mapped_column(DateTime(timezone=True), nullable=False)
```

####### `leadr.auth.adapters.orm.DeviceORM.from_domain`

```python
from_domain(device)
```

Convert Device domain entity to ORM model.

####### `leadr.auth.adapters.orm.DeviceORM.game`

```python
game: Mapped[GameORM] = relationship('GameORM')
```

####### `leadr.auth.adapters.orm.DeviceORM.game_id`

```python
game_id: Mapped[UUID] = mapped_column(ForeignKey('games.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.auth.adapters.orm.DeviceORM.id`

```python
id: Mapped[uuid_pk]
```

####### `leadr.auth.adapters.orm.DeviceORM.last_seen_at`

```python
last_seen_at: Mapped[datetime] = mapped_column(DateTime(timezone=True), nullable=False)
```

####### `leadr.auth.adapters.orm.DeviceORM.platform`

```python
platform: Mapped[str | None] = mapped_column(String, nullable=True)
```

####### `leadr.auth.adapters.orm.DeviceORM.status`

```python
status: Mapped[DeviceStatusEnum] = mapped_column(Enum(DeviceStatusEnum, name='device_status', native_enum=True, values_callable=(lambda x: [(e.value) for e in x])), nullable=False, default=(DeviceStatusEnum.ACTIVE), server_default='active')
```

####### `leadr.auth.adapters.orm.DeviceORM.to_domain`

```python
to_domain()
```

Convert ORM model to Device domain entity.

####### `leadr.auth.adapters.orm.DeviceORM.updated_at`

```python
updated_at: Mapped[timestamp] = mapped_column(onupdate=(func.now()))
```

###### `leadr.auth.adapters.orm.DeviceStatusEnum`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Device status enum for database.

**Attributes:**

- [**ACTIVE**](./auth.md#leadr.auth.adapters.orm.DeviceStatusEnum.ACTIVE) –
- [**BANNED**](./auth.md#leadr.auth.adapters.orm.DeviceStatusEnum.BANNED) –
- [**SUSPENDED**](./auth.md#leadr.auth.adapters.orm.DeviceStatusEnum.SUSPENDED) –

####### `leadr.auth.adapters.orm.DeviceStatusEnum.ACTIVE`

```python
ACTIVE = 'active'
```

####### `leadr.auth.adapters.orm.DeviceStatusEnum.BANNED`

```python
BANNED = 'banned'
```

####### `leadr.auth.adapters.orm.DeviceStatusEnum.SUSPENDED`

```python
SUSPENDED = 'suspended'
```

###### `leadr.auth.adapters.orm.IdentityKindEnum`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Identity kind enum for database.

**Attributes:**

- [**CUSTOM**](./auth.md#leadr.auth.adapters.orm.IdentityKindEnum.CUSTOM) –
- [**DEVICE**](./auth.md#leadr.auth.adapters.orm.IdentityKindEnum.DEVICE) –
- [**STEAM**](./auth.md#leadr.auth.adapters.orm.IdentityKindEnum.STEAM) –

####### `leadr.auth.adapters.orm.IdentityKindEnum.CUSTOM`

```python
CUSTOM = 'CUSTOM'
```

####### `leadr.auth.adapters.orm.IdentityKindEnum.DEVICE`

```python
DEVICE = 'DEVICE'
```

####### `leadr.auth.adapters.orm.IdentityKindEnum.STEAM`

```python
STEAM = 'STEAM'
```

###### `leadr.auth.adapters.orm.IdentityORM`

Bases: <code>[Base](./common.md#leadr.common.orm.Base)</code>

Identity ORM model.

Represents a player identity within a game in the database.
Maps to the identities table with foreign keys to accounts and games.
Identities are the ranking key for leaderboards.

**Functions:**

- [**from_domain**](#leadr.auth.adapters.orm.IdentityORM.from_domain) – Convert Identity domain entity to ORM model.
- [**to_domain**](#leadr.auth.adapters.orm.IdentityORM.to_domain) – Convert ORM model to Identity domain entity.

**Attributes:**

- [**account_id**](#leadr.auth.adapters.orm.IdentityORM.account_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**created_at**](#leadr.auth.adapters.orm.IdentityORM.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**deleted_at**](#leadr.auth.adapters.orm.IdentityORM.deleted_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[nullable_timestamp](#leadr.common.orm.nullable_timestamp)\]</code>) –
- [**display_name**](#leadr.auth.adapters.orm.IdentityORM.display_name) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**external_key**](#leadr.auth.adapters.orm.IdentityORM.external_key) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**game**](./auth.md#leadr.auth.adapters.orm.IdentityORM.game) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[GameORM](./games.md#leadr.games.adapters.orm.GameORM)\]</code>) –
- [**game_id**](#leadr.auth.adapters.orm.IdentityORM.game_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**id**](./auth.md#leadr.auth.adapters.orm.IdentityORM.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**kind**](./auth.md#leadr.auth.adapters.orm.IdentityORM.kind) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[IdentityKindEnum](./auth.md#leadr.auth.adapters.orm.IdentityKindEnum)\]</code>) –
- [**nonces**](./auth.md#leadr.auth.adapters.orm.IdentityORM.nonces) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[list](#list)\[[NonceORM](./auth.md#leadr.auth.adapters.orm.NonceORM)\]\]</code>) –
- [**sessions**](./auth.md#leadr.auth.adapters.orm.IdentityORM.sessions) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[list](#list)\[[IdentitySessionORM](./auth.md#leadr.auth.adapters.orm.IdentitySessionORM)\]\]</code>) –
- [**updated_at**](#leadr.auth.adapters.orm.IdentityORM.updated_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –

####### `leadr.auth.adapters.orm.IdentityORM.account_id`

```python
account_id: Mapped[UUID] = mapped_column(ForeignKey('accounts.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.auth.adapters.orm.IdentityORM.created_at`

```python
created_at: Mapped[timestamp]
```

####### `leadr.auth.adapters.orm.IdentityORM.deleted_at`

```python
deleted_at: Mapped[nullable_timestamp]
```

####### `leadr.auth.adapters.orm.IdentityORM.display_name`

```python
display_name: Mapped[str | None] = mapped_column(String, nullable=True)
```

####### `leadr.auth.adapters.orm.IdentityORM.external_key`

```python
external_key: Mapped[str] = mapped_column(String, nullable=False)
```

####### `leadr.auth.adapters.orm.IdentityORM.from_domain`

```python
from_domain(identity)
```

Convert Identity domain entity to ORM model.

####### `leadr.auth.adapters.orm.IdentityORM.game`

```python
game: Mapped[GameORM] = relationship('GameORM')
```

####### `leadr.auth.adapters.orm.IdentityORM.game_id`

```python
game_id: Mapped[UUID] = mapped_column(ForeignKey('games.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.auth.adapters.orm.IdentityORM.id`

```python
id: Mapped[uuid_pk]
```

####### `leadr.auth.adapters.orm.IdentityORM.kind`

```python
kind: Mapped[IdentityKindEnum] = mapped_column(Enum(IdentityKindEnum, name='identity_kind', native_enum=True, values_callable=(lambda x: [(e.value) for e in x])), nullable=False)
```

####### `leadr.auth.adapters.orm.IdentityORM.nonces`

```python
nonces: Mapped[list[NonceORM]] = relationship('NonceORM', cascade='all, delete-orphan')
```

####### `leadr.auth.adapters.orm.IdentityORM.sessions`

```python
sessions: Mapped[list[IdentitySessionORM]] = relationship('IdentitySessionORM', back_populates='identity', cascade='all, delete-orphan')
```

####### `leadr.auth.adapters.orm.IdentityORM.to_domain`

```python
to_domain()
```

Convert ORM model to Identity domain entity.

####### `leadr.auth.adapters.orm.IdentityORM.updated_at`

```python
updated_at: Mapped[timestamp] = mapped_column(onupdate=(func.now()))
```

###### `leadr.auth.adapters.orm.IdentitySessionORM`

Bases: <code>[Base](./common.md#leadr.common.orm.Base)</code>

IdentitySession ORM model.

Represents an active authentication session for an identity in the database.
Maps to the identity_sessions table with foreign key to identities.
Sessions include both access and refresh tokens with token rotation support.

**Functions:**

- [**from_domain**](#leadr.auth.adapters.orm.IdentitySessionORM.from_domain) – Convert IdentitySession domain entity to ORM model.
- [**to_domain**](#leadr.auth.adapters.orm.IdentitySessionORM.to_domain) – Convert ORM model to IdentitySession domain entity.

**Attributes:**

- [**access_token_hash**](#leadr.auth.adapters.orm.IdentitySessionORM.access_token_hash) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**created_at**](#leadr.auth.adapters.orm.IdentitySessionORM.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**deleted_at**](#leadr.auth.adapters.orm.IdentitySessionORM.deleted_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[nullable_timestamp](#leadr.common.orm.nullable_timestamp)\]</code>) –
- [**expires_at**](#leadr.auth.adapters.orm.IdentitySessionORM.expires_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime)\]</code>) –
- [**id**](./auth.md#leadr.auth.adapters.orm.IdentitySessionORM.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**identity**](./auth.md#leadr.auth.adapters.orm.IdentitySessionORM.identity) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[IdentityORM](./auth.md#leadr.auth.adapters.orm.IdentityORM)\]</code>) –
- [**identity_id**](#leadr.auth.adapters.orm.IdentitySessionORM.identity_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**refresh_expires_at**](#leadr.auth.adapters.orm.IdentitySessionORM.refresh_expires_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime)\]</code>) –
- [**refresh_token_hash**](#leadr.auth.adapters.orm.IdentitySessionORM.refresh_token_hash) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**revoked_at**](#leadr.auth.adapters.orm.IdentitySessionORM.revoked_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime) | None\]</code>) –
- [**token_version**](#leadr.auth.adapters.orm.IdentitySessionORM.token_version) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[int](#int)\]</code>) –
- [**updated_at**](#leadr.auth.adapters.orm.IdentitySessionORM.updated_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –

####### `leadr.auth.adapters.orm.IdentitySessionORM.access_token_hash`

```python
access_token_hash: Mapped[str] = mapped_column(String, nullable=False, index=True)
```

####### `leadr.auth.adapters.orm.IdentitySessionORM.created_at`

```python
created_at: Mapped[timestamp]
```

####### `leadr.auth.adapters.orm.IdentitySessionORM.deleted_at`

```python
deleted_at: Mapped[nullable_timestamp]
```

####### `leadr.auth.adapters.orm.IdentitySessionORM.expires_at`

```python
expires_at: Mapped[datetime] = mapped_column(DateTime(timezone=True), nullable=False, index=True)
```

####### `leadr.auth.adapters.orm.IdentitySessionORM.from_domain`

```python
from_domain(session)
```

Convert IdentitySession domain entity to ORM model.

####### `leadr.auth.adapters.orm.IdentitySessionORM.id`

```python
id: Mapped[uuid_pk]
```

####### `leadr.auth.adapters.orm.IdentitySessionORM.identity`

```python
identity: Mapped[IdentityORM] = relationship('IdentityORM', back_populates='sessions')
```

####### `leadr.auth.adapters.orm.IdentitySessionORM.identity_id`

```python
identity_id: Mapped[UUID] = mapped_column(ForeignKey('identities.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.auth.adapters.orm.IdentitySessionORM.refresh_expires_at`

```python
refresh_expires_at: Mapped[datetime] = mapped_column(DateTime(timezone=True), nullable=False, index=True)
```

####### `leadr.auth.adapters.orm.IdentitySessionORM.refresh_token_hash`

```python
refresh_token_hash: Mapped[str] = mapped_column(String, nullable=False, index=True)
```

####### `leadr.auth.adapters.orm.IdentitySessionORM.revoked_at`

```python
revoked_at: Mapped[datetime | None] = mapped_column(DateTime(timezone=True), nullable=True)
```

####### `leadr.auth.adapters.orm.IdentitySessionORM.to_domain`

```python
to_domain()
```

Convert ORM model to IdentitySession domain entity.

####### `leadr.auth.adapters.orm.IdentitySessionORM.token_version`

```python
token_version: Mapped[int] = mapped_column(Integer, nullable=False, default=1, server_default='1')
```

####### `leadr.auth.adapters.orm.IdentitySessionORM.updated_at`

```python
updated_at: Mapped[timestamp] = mapped_column(onupdate=(func.now()))
```

###### `leadr.auth.adapters.orm.NonceORM`

Bases: <code>[Base](./common.md#leadr.common.orm.Base)</code>

Nonce ORM model.

Represents a single-use nonce for replay protection in the database.
Maps to the nonces table with foreign key to identities.
Nonces are short-lived tokens (typically 60 seconds) that must be
obtained before making mutating requests.

**Functions:**

- [**from_domain**](#leadr.auth.adapters.orm.NonceORM.from_domain) – Convert Nonce domain entity to ORM model.
- [**to_domain**](#leadr.auth.adapters.orm.NonceORM.to_domain) – Convert ORM model to Nonce domain entity.

**Attributes:**

- [**created_at**](#leadr.auth.adapters.orm.NonceORM.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**deleted_at**](#leadr.auth.adapters.orm.NonceORM.deleted_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[nullable_timestamp](#leadr.common.orm.nullable_timestamp)\]</code>) –
- [**expires_at**](#leadr.auth.adapters.orm.NonceORM.expires_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime)\]</code>) –
- [**id**](./auth.md#leadr.auth.adapters.orm.NonceORM.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**identity**](./auth.md#leadr.auth.adapters.orm.NonceORM.identity) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[IdentityORM](./auth.md#leadr.auth.adapters.orm.IdentityORM)\]</code>) –
- [**identity_id**](#leadr.auth.adapters.orm.NonceORM.identity_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**nonce_value**](#leadr.auth.adapters.orm.NonceORM.nonce_value) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**status**](./auth.md#leadr.auth.adapters.orm.NonceORM.status) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[NonceStatusEnum](./auth.md#leadr.auth.adapters.orm.NonceStatusEnum)\]</code>) –
- [**updated_at**](#leadr.auth.adapters.orm.NonceORM.updated_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**used_at**](#leadr.auth.adapters.orm.NonceORM.used_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime) | None\]</code>) –

####### `leadr.auth.adapters.orm.NonceORM.created_at`

```python
created_at: Mapped[timestamp]
```

####### `leadr.auth.adapters.orm.NonceORM.deleted_at`

```python
deleted_at: Mapped[nullable_timestamp]
```

####### `leadr.auth.adapters.orm.NonceORM.expires_at`

```python
expires_at: Mapped[datetime] = mapped_column(DateTime(timezone=True), nullable=False, index=True)
```

####### `leadr.auth.adapters.orm.NonceORM.from_domain`

```python
from_domain(nonce)
```

Convert Nonce domain entity to ORM model.

####### `leadr.auth.adapters.orm.NonceORM.id`

```python
id: Mapped[uuid_pk]
```

####### `leadr.auth.adapters.orm.NonceORM.identity`

```python
identity: Mapped[IdentityORM] = relationship('IdentityORM', overlaps='nonces')
```

####### `leadr.auth.adapters.orm.NonceORM.identity_id`

```python
identity_id: Mapped[UUID] = mapped_column(ForeignKey('identities.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.auth.adapters.orm.NonceORM.nonce_value`

```python
nonce_value: Mapped[str] = mapped_column(String, nullable=False, unique=True, index=True)
```

####### `leadr.auth.adapters.orm.NonceORM.status`

```python
status: Mapped[NonceStatusEnum] = mapped_column(Enum(NonceStatusEnum, name='nonce_status', native_enum=True, values_callable=(lambda x: [(e.value) for e in x])), nullable=False, default=(NonceStatusEnum.PENDING), server_default='pending')
```

####### `leadr.auth.adapters.orm.NonceORM.to_domain`

```python
to_domain()
```

Convert ORM model to Nonce domain entity.

####### `leadr.auth.adapters.orm.NonceORM.updated_at`

```python
updated_at: Mapped[timestamp] = mapped_column(onupdate=(func.now()))
```

####### `leadr.auth.adapters.orm.NonceORM.used_at`

```python
used_at: Mapped[datetime | None] = mapped_column(DateTime(timezone=True), nullable=True)
```

###### `leadr.auth.adapters.orm.NonceStatusEnum`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Nonce status enum for database.

**Attributes:**

- [**EXPIRED**](./auth.md#leadr.auth.adapters.orm.NonceStatusEnum.EXPIRED) –
- [**PENDING**](./auth.md#leadr.auth.adapters.orm.NonceStatusEnum.PENDING) –
- [**USED**](./auth.md#leadr.auth.adapters.orm.NonceStatusEnum.USED) –

####### `leadr.auth.adapters.orm.NonceStatusEnum.EXPIRED`

```python
EXPIRED = 'expired'
```

####### `leadr.auth.adapters.orm.NonceStatusEnum.PENDING`

```python
PENDING = 'pending'
```

####### `leadr.auth.adapters.orm.NonceStatusEnum.USED`

```python
USED = 'used'
```

#### `leadr.auth.api`

**Modules:**

- [**api_key_routes**](#leadr.auth.api.api_key_routes) – API routes for authentication and API key management.
- [**api_key_schemas**](#leadr.auth.api.api_key_schemas) – API schemas for Authentication endpoints.
- [**client_routes**](#leadr.auth.api.client_routes) – API routes for client authentication using Identity.
- [**client_schemas**](#leadr.auth.api.client_schemas) – API request and response models for client authentication.
- [**device_routes**](#leadr.auth.api.device_routes) – API routes for device management.
- [**device_schemas**](#leadr.auth.api.device_schemas) – API request and response models for devices.
- [**identity_routes**](#leadr.auth.api.identity_routes) – API routes for identity management.
- [**identity_schemas**](#leadr.auth.api.identity_schemas) – API request and response models for identities.
- [**identity_session_routes**](#leadr.auth.api.identity_session_routes) – API routes for identity session management.

##### `leadr.auth.api.api_key_routes`

API routes for authentication and API key management.

**Functions:**

- [**create_api_key**](#leadr.auth.api.api_key_routes.create_api_key) – Create a new API key for an account.
- [**get_api_key**](#leadr.auth.api.api_key_routes.get_api_key) – Get a single API key by ID.
- [**list_api_keys**](#leadr.auth.api.api_key_routes.list_api_keys) – List API keys for an account with optional filters and pagination.
- [**update_api_key**](#leadr.auth.api.api_key_routes.update_api_key) – Update an API key.

**Attributes:**

- [**router**](#leadr.auth.api.api_key_routes.router) –

###### `leadr.auth.api.api_key_routes.create_api_key`

```python
create_api_key(request, service, auth)
```

Create a new API key for an account.

The plain API key is returned only once in this response.
Store it securely as it cannot be retrieved later.

For regular users, account_id must match their API key's account.
For superadmins, any account_id is accepted.

**Returns:**

- <code>[CreateAPIKeyResponse](#leadr.auth.api.api_key_schemas.CreateAPIKeyResponse)</code> – CreateAPIKeyResponse with the plain key included.

**Raises:**

- <code>403</code> – User does not have access to the specified account.
- <code>404</code> – Account not found.

###### `leadr.auth.api.api_key_routes.get_api_key`

```python
get_api_key(key_id, service, auth)
```

Get a single API key by ID.

**Parameters:**

- **key_id** (<code>[APIKeyID](./common.md#leadr.common.domain.ids.APIKeyID)</code>) – The UUID of the API key to retrieve.
- **service** (<code>[APIKeyServiceDep](./auth.md#leadr.auth.services.dependencies.APIKeyServiceDep)</code>) – Injected API key service dependency.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.

**Returns:**

- <code>[APIKeyResponse](#leadr.auth.api.api_key_schemas.APIKeyResponse)</code> – APIKeyResponse with key details (excludes the plain key).

**Raises:**

- <code>403</code> – User does not have access to this API key's account.
- <code>404</code> – API key not found.

###### `leadr.auth.api.api_key_routes.list_api_keys`

```python
list_api_keys(auth, service, pagination, account_id=None, key_status=None)
```

List API keys for an account with optional filters and pagination.

For regular users, account_id is automatically derived from their API key.
For superadmins, account_id is optional - if omitted, returns API keys from all accounts.

Pagination:

- Default: 20 items per page, sorted by created_at:desc,id:asc
- Custom sort: Use ?sort=name:asc,created_at:desc
- Valid sort fields: id, name, created_at, updated_at
- Navigation: Use next_cursor/prev_cursor from response

<details class="example" open markdown="1">
<summary>Example</summary>

GET /v1/api-keys?account_id=acc_123&status=active&limit=50&sort=name:asc

</details>

**Parameters:**

- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.
- **service** (<code>[APIKeyServiceDep](./auth.md#leadr.auth.services.dependencies.APIKeyServiceDep)</code>) – Injected API key service dependency.
- **pagination** (<code>[Annotated](#typing.Annotated)\[[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams), [Depends](#fastapi.Depends)()\]</code>) – Pagination parameters (cursor, limit, sort).
- **account_id** (<code>[Annotated](#typing.Annotated)\[[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None, [Query](#fastapi.Query)(description='Account ID filter')\]</code>) – Optional account_id query parameter (superadmins can omit to see all).
- **key_status** (<code>[Annotated](#typing.Annotated)\[[APIKeyStatus](#leadr.auth.domain.api_key.APIKeyStatus) | None, [Query](#fastapi.Query)(alias=[status](#fastapi.status), description='Filter by status')\]</code>) – Optional status to filter results (active or revoked).

**Returns:**

- <code>[PaginatedResponse](./common.md#leadr.common.api.pagination.PaginatedResponse)\[[APIKeyResponse](#leadr.auth.api.api_key_schemas.APIKeyResponse)\]</code> – PaginatedResponse with API keys and pagination metadata.

**Raises:**

- <code>400</code> – Invalid cursor, sort field, or cursor state mismatch.
- <code>403</code> – User does not have access to the specified account.

###### `leadr.auth.api.api_key_routes.router`

```python
router = APIRouter()
```

###### `leadr.auth.api.api_key_routes.update_api_key`

```python
update_api_key(key_id, request, service, auth)
```

Update an API key.

Currently supports:

- Updating status (e.g., to revoke a key)
- Soft delete via deleted flag

**Parameters:**

- **key_id** (<code>[APIKeyID](./common.md#leadr.common.domain.ids.APIKeyID)</code>) – The UUID of the API key to update.
- **request** (<code>[UpdateAPIKeyRequest](#leadr.auth.api.api_key_schemas.UpdateAPIKeyRequest)</code>) – Update request with optional status and deleted fields.
- **service** (<code>[APIKeyServiceDep](./auth.md#leadr.auth.services.dependencies.APIKeyServiceDep)</code>) – Injected API key service dependency.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.

**Returns:**

- <code>[APIKeyResponse](#leadr.auth.api.api_key_schemas.APIKeyResponse)</code> – APIKeyResponse with updated key details.

**Raises:**

- <code>403</code> – User does not have access to this API key's account.
- <code>404</code> – API key not found.

##### `leadr.auth.api.api_key_schemas`

API schemas for Authentication endpoints.

**Classes:**

- [**APIKeyResponse**](#leadr.auth.api.api_key_schemas.APIKeyResponse) – Response schema for API key details.
- [**CreateAPIKeyRequest**](#leadr.auth.api.api_key_schemas.CreateAPIKeyRequest) – Request schema for creating an API key.
- [**CreateAPIKeyResponse**](#leadr.auth.api.api_key_schemas.CreateAPIKeyResponse) – Response schema for creating an API key.
- [**UpdateAPIKeyRequest**](#leadr.auth.api.api_key_schemas.UpdateAPIKeyRequest) – Request schema for updating an API key.

###### `leadr.auth.api.api_key_schemas.APIKeyResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response schema for API key details.

Excludes sensitive information like key_hash.
The full key is never returned after creation.

**Functions:**

- [**from_domain**](#leadr.auth.api.api_key_schemas.APIKeyResponse.from_domain) – Convert domain entity to response model.

**Attributes:**

- [**account_id**](#leadr.auth.api.api_key_schemas.APIKeyResponse.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**created_at**](#leadr.auth.api.api_key_schemas.APIKeyResponse.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**expires_at**](#leadr.auth.api.api_key_schemas.APIKeyResponse.expires_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**id**](#leadr.auth.api.api_key_schemas.APIKeyResponse.id) (<code>[APIKeyID](./common.md#leadr.common.domain.ids.APIKeyID)</code>) –
- [**last_used_at**](#leadr.auth.api.api_key_schemas.APIKeyResponse.last_used_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**model_config**](#leadr.auth.api.api_key_schemas.APIKeyResponse.model_config) –
- [**name**](#leadr.auth.api.api_key_schemas.APIKeyResponse.name) (<code>[str](#str)</code>) –
- [**prefix**](#leadr.auth.api.api_key_schemas.APIKeyResponse.prefix) (<code>[str](#str)</code>) –
- [**status**](#leadr.auth.api.api_key_schemas.APIKeyResponse.status) (<code>[APIKeyStatus](#leadr.auth.domain.api_key.APIKeyStatus)</code>) –
- [**updated_at**](#leadr.auth.api.api_key_schemas.APIKeyResponse.updated_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**user_id**](#leadr.auth.api.api_key_schemas.APIKeyResponse.user_id) (<code>[UserID](./common.md#leadr.common.domain.ids.UserID)</code>) –

####### `leadr.auth.api.api_key_schemas.APIKeyResponse.account_id`

```python
account_id: AccountID = Field(description='ID of the account this key belongs to')
```

####### `leadr.auth.api.api_key_schemas.APIKeyResponse.created_at`

```python
created_at: datetime = Field(description='Timestamp when the key was created (UTC)')
```

####### `leadr.auth.api.api_key_schemas.APIKeyResponse.expires_at`

```python
expires_at: datetime | None = Field(default=None, description='Expiration timestamp (UTC), or null if never expires')
```

####### `leadr.auth.api.api_key_schemas.APIKeyResponse.from_domain`

```python
from_domain(api_key)
```

Convert domain entity to response model.

**Parameters:**

- **api_key** (<code>[APIKey](#leadr.auth.domain.api_key.APIKey)</code>) – The domain APIKey entity

**Returns:**

- <code>[APIKeyResponse](#leadr.auth.api.api_key_schemas.APIKeyResponse)</code> – APIKeyResponse with all fields populated

####### `leadr.auth.api.api_key_schemas.APIKeyResponse.id`

```python
id: APIKeyID = Field(description='Unique identifier for the API key')
```

####### `leadr.auth.api.api_key_schemas.APIKeyResponse.last_used_at`

```python
last_used_at: datetime | None = Field(default=None, description='Timestamp of last successful authentication (UTC)')
```

####### `leadr.auth.api.api_key_schemas.APIKeyResponse.model_config`

```python
model_config = ConfigDict(extra='forbid')
```

####### `leadr.auth.api.api_key_schemas.APIKeyResponse.name`

```python
name: str = Field(description='Human-readable name for the API key')
```

####### `leadr.auth.api.api_key_schemas.APIKeyResponse.prefix`

```python
prefix: str = Field(description='Key prefix for identification (first 8 characters)')
```

####### `leadr.auth.api.api_key_schemas.APIKeyResponse.status`

```python
status: APIKeyStatus = Field(description='Current status (active, revoked, expired)')
```

####### `leadr.auth.api.api_key_schemas.APIKeyResponse.updated_at`

```python
updated_at: datetime = Field(description='Timestamp of last update (UTC)')
```

####### `leadr.auth.api.api_key_schemas.APIKeyResponse.user_id`

```python
user_id: UserID = Field(description='ID of the user who owns this API key')
```

###### `leadr.auth.api.api_key_schemas.CreateAPIKeyRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request schema for creating an API key.

**Attributes:**

- [**account_id**](#leadr.auth.api.api_key_schemas.CreateAPIKeyRequest.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**expires_at**](#leadr.auth.api.api_key_schemas.CreateAPIKeyRequest.expires_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**name**](#leadr.auth.api.api_key_schemas.CreateAPIKeyRequest.name) (<code>[str](#str)</code>) –
- [**user_id**](#leadr.auth.api.api_key_schemas.CreateAPIKeyRequest.user_id) (<code>[UserID](./common.md#leadr.common.domain.ids.UserID)</code>) –

####### `leadr.auth.api.api_key_schemas.CreateAPIKeyRequest.account_id`

```python
account_id: AccountID = Field(description='ID of the account this API key belongs to')
```

####### `leadr.auth.api.api_key_schemas.CreateAPIKeyRequest.expires_at`

```python
expires_at: datetime | None = Field(default=None, description='Optional expiration timestamp (UTC). Key never expires if omitted')
```

####### `leadr.auth.api.api_key_schemas.CreateAPIKeyRequest.name`

```python
name: str = Field(description="Human-readable name for the API key (e.g., 'Production Server')")
```

####### `leadr.auth.api.api_key_schemas.CreateAPIKeyRequest.user_id`

```python
user_id: UserID = Field(description='ID of the user who owns this API key')
```

###### `leadr.auth.api.api_key_schemas.CreateAPIKeyResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response schema for creating an API key.

Includes the plain API key which is only shown once.
The client must save this key as it cannot be retrieved later.

**Functions:**

- [**from_domain**](#leadr.auth.api.api_key_schemas.CreateAPIKeyResponse.from_domain) – Convert domain entity to response model with plain key.

**Attributes:**

- [**created_at**](#leadr.auth.api.api_key_schemas.CreateAPIKeyResponse.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**expires_at**](#leadr.auth.api.api_key_schemas.CreateAPIKeyResponse.expires_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**id**](#leadr.auth.api.api_key_schemas.CreateAPIKeyResponse.id) (<code>[APIKeyID](./common.md#leadr.common.domain.ids.APIKeyID)</code>) –
- [**key**](#leadr.auth.api.api_key_schemas.CreateAPIKeyResponse.key) (<code>[str](#str)</code>) –
- [**name**](#leadr.auth.api.api_key_schemas.CreateAPIKeyResponse.name) (<code>[str](#str)</code>) –
- [**prefix**](#leadr.auth.api.api_key_schemas.CreateAPIKeyResponse.prefix) (<code>[str](#str)</code>) –
- [**status**](#leadr.auth.api.api_key_schemas.CreateAPIKeyResponse.status) (<code>[APIKeyStatus](#leadr.auth.domain.api_key.APIKeyStatus)</code>) –

####### `leadr.auth.api.api_key_schemas.CreateAPIKeyResponse.created_at`

```python
created_at: datetime = Field(description='Timestamp when the key was created (UTC)')
```

####### `leadr.auth.api.api_key_schemas.CreateAPIKeyResponse.expires_at`

```python
expires_at: datetime | None = Field(default=None, description='Expiration timestamp (UTC), or null if never expires')
```

####### `leadr.auth.api.api_key_schemas.CreateAPIKeyResponse.from_domain`

```python
from_domain(api_key, plain_key)
```

Convert domain entity to response model with plain key.

**Parameters:**

- **api_key** (<code>[APIKey](#leadr.auth.domain.api_key.APIKey)</code>) – The domain APIKey entity
- **plain_key** (<code>[str](#str)</code>) – The plain text API key (only available at creation)

**Returns:**

- <code>[CreateAPIKeyResponse](#leadr.auth.api.api_key_schemas.CreateAPIKeyResponse)</code> – CreateAPIKeyResponse with all fields populated

####### `leadr.auth.api.api_key_schemas.CreateAPIKeyResponse.id`

```python
id: APIKeyID = Field(description='Unique identifier for the API key')
```

####### `leadr.auth.api.api_key_schemas.CreateAPIKeyResponse.key`

```python
key: str = Field(description='Plain text API key. ONLY returned at creation - save this securely!')
```

####### `leadr.auth.api.api_key_schemas.CreateAPIKeyResponse.name`

```python
name: str = Field(description='Human-readable name for the API key')
```

####### `leadr.auth.api.api_key_schemas.CreateAPIKeyResponse.prefix`

```python
prefix: str = Field(description='Key prefix for identification (first 8 characters)')
```

####### `leadr.auth.api.api_key_schemas.CreateAPIKeyResponse.status`

```python
status: APIKeyStatus = Field(description='Current status of the API key')
```

###### `leadr.auth.api.api_key_schemas.UpdateAPIKeyRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request schema for updating an API key.

Can update status (e.g., to revoke) or set deleted flag for soft delete.

**Attributes:**

- [**deleted**](#leadr.auth.api.api_key_schemas.UpdateAPIKeyRequest.deleted) (<code>[bool](#bool) | None</code>) –
- [**status**](#leadr.auth.api.api_key_schemas.UpdateAPIKeyRequest.status) (<code>[APIKeyStatus](#leadr.auth.domain.api_key.APIKeyStatus) | None</code>) –

####### `leadr.auth.api.api_key_schemas.UpdateAPIKeyRequest.deleted`

```python
deleted: bool | None = Field(default=None, description='Set to true to soft delete the key')
```

####### `leadr.auth.api.api_key_schemas.UpdateAPIKeyRequest.status`

```python
status: APIKeyStatus | None = Field(default=None, description="Updated status (use 'revoked' to disable key)")
```

##### `leadr.auth.api.client_routes`

API routes for client authentication using Identity.

**Functions:**

- [**generate_nonce**](#leadr.auth.api.client_routes.generate_nonce) – Generate a fresh nonce for replay protection.
- [**refresh_session**](#leadr.auth.api.client_routes.refresh_session) – Refresh an expired access token using a valid refresh token.
- [**start_session**](#leadr.auth.api.client_routes.start_session) – Start a new identity session for a game client.

**Attributes:**

- [**protected_router**](#leadr.auth.api.client_routes.protected_router) –
- [**public_router**](#leadr.auth.api.client_routes.public_router) –

###### `leadr.auth.api.client_routes.generate_nonce`

```python
generate_nonce(auth, service)
```

Generate a fresh nonce for replay protection.

Nonces are single-use tokens with short TTL (60 seconds) that clients must
obtain before making mutating requests (POST, PATCH, DELETE). This prevents
replay attacks by ensuring each request is fresh and authorized.

Requires identity authentication via access token.

**Parameters:**

- **auth** (<code>[ClientAuthContextDep](./auth.md#leadr.auth.dependencies.ClientAuthContextDep)</code>) – Authenticated client auth context (identity guaranteed non-None)
- **service** (<code>[NonceServiceDep](./auth.md#leadr.auth.services.dependencies.NonceServiceDep)</code>) – NonceService dependency

**Returns:**

- <code>[NonceResponse](#leadr.auth.api.client_schemas.NonceResponse)</code> – NonceResponse with nonce_value and expires_at

**Raises:**

- <code>401</code> – Invalid or missing access token

<details class="example" open markdown="1">
<summary>Example</summary>

1. Client calls GET /client/nonce with Authorization header
1. Server returns nonce_value and expires_at
1. Client includes nonce in leadr-client-nonce header for mutations
1. Server validates and consumes nonce (single-use)

</details>

###### `leadr.auth.api.client_routes.protected_router`

```python
protected_router = APIRouter()
```

###### `leadr.auth.api.client_routes.public_router`

```python
public_router = APIRouter(prefix='/client')
```

###### `leadr.auth.api.client_routes.refresh_session`

```python
refresh_session(request, identity_service)
```

Refresh an expired access token using a valid refresh token.

This endpoint implements token rotation for security:

- Returns new access and refresh tokens
- Increments the token version
- Invalidates the old refresh token (prevents replay attacks)

No authentication is required (the refresh token itself is the credential).

**Parameters:**

- **request** (<code>[RefreshTokenRequest](#leadr.auth.api.client_schemas.RefreshTokenRequest)</code>) – Refresh token request
- **identity_service** (<code>[IdentityServiceDep](./auth.md#leadr.auth.services.dependencies.IdentityServiceDep)</code>) – IdentityService dependency

**Returns:**

- <code>[RefreshTokenResponse](#leadr.auth.api.client_schemas.RefreshTokenResponse)</code> – RefreshTokenResponse with new tokens

**Raises:**

- <code>401</code> – Invalid or expired refresh token
- <code>422</code> – Invalid request (missing refresh_token)

###### `leadr.auth.api.client_routes.start_session`

```python
start_session(request, session_request, identity_service, _geo)
```

Start a new identity session for a game client.

This endpoint authenticates game clients and provides JWT access tokens.
It is idempotent - calling multiple times for the same fingerprint updates
the device record and creates a new identity session.

No authentication is required to call this endpoint (it IS the authentication).

The \_geo parameter triggers GeoIP lookup for this endpoint. Geo data is
available for future use via \_geo.timezone, \_geo.country, \_geo.city.

**Parameters:**

- **request** (<code>[Request](#fastapi.Request)</code>) – FastAPI request object (used for access logging)
- **session_request** (<code>[StartSessionRequest](#leadr.auth.api.client_schemas.StartSessionRequest)</code>) – Session start request with game_id and fingerprint
- **identity_service** (<code>[IdentityServiceDep](./auth.md#leadr.auth.services.dependencies.IdentityServiceDep)</code>) – IdentityService dependency (handles device and identity creation)
- **\_geo** (<code>[GeoInfoDep](./common.md#leadr.common.dependencies.GeoInfoDep)</code>) – GeoIP information extracted from client IP address (available for future use)

**Returns:**

- <code>[StartSessionResponse](#leadr.auth.api.client_schemas.StartSessionResponse)</code> – StartSessionResponse with identity info and access tokens

**Raises:**

- <code>404</code> – Game not found
- <code>422</code> – Invalid request (missing required fields, invalid UUID format)

##### `leadr.auth.api.client_schemas`

API request and response models for client authentication.

**Classes:**

- [**NonceResponse**](#leadr.auth.api.client_schemas.NonceResponse) – Response schema for nonce generation.
- [**RefreshTokenRequest**](#leadr.auth.api.client_schemas.RefreshTokenRequest) – Request schema for refreshing an access token.
- [**RefreshTokenResponse**](#leadr.auth.api.client_schemas.RefreshTokenResponse) – Response schema for token refresh.
- [**StartSessionRequest**](#leadr.auth.api.client_schemas.StartSessionRequest) – Request schema for starting a device session.
- [**StartSessionResponse**](#leadr.auth.api.client_schemas.StartSessionResponse) – Response schema for starting an identity session.

###### `leadr.auth.api.client_schemas.NonceResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response schema for nonce generation.

Nonces are single-use tokens with short TTL (60 seconds) that clients must
obtain before making mutating requests. This prevents replay attacks.

**Attributes:**

- [**expires_at**](#leadr.auth.api.client_schemas.NonceResponse.expires_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**nonce_value**](#leadr.auth.api.client_schemas.NonceResponse.nonce_value) (<code>[str](#str)</code>) –

####### `leadr.auth.api.client_schemas.NonceResponse.expires_at`

```python
expires_at: datetime = Field(description='Nonce expiration timestamp (UTC)')
```

####### `leadr.auth.api.client_schemas.NonceResponse.nonce_value`

```python
nonce_value: str = Field(description='Unique nonce value (UUID)')
```

###### `leadr.auth.api.client_schemas.RefreshTokenRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request schema for refreshing an access token.

Used by clients when their access token has expired.

**Attributes:**

- [**refresh_token**](#leadr.auth.api.client_schemas.RefreshTokenRequest.refresh_token) (<code>[str](#str)</code>) –

####### `leadr.auth.api.client_schemas.RefreshTokenRequest.refresh_token`

```python
refresh_token: str = Field(description='JWT refresh token obtained from start_session')
```

###### `leadr.auth.api.client_schemas.RefreshTokenResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response schema for token refresh.

Returns new access and refresh tokens with incremented version.
The old refresh token is invalidated and cannot be reused.

**Attributes:**

- [**access_token**](#leadr.auth.api.client_schemas.RefreshTokenResponse.access_token) (<code>[str](#str)</code>) –
- [**expires_in**](#leadr.auth.api.client_schemas.RefreshTokenResponse.expires_in) (<code>[int](#int)</code>) –
- [**refresh_token**](#leadr.auth.api.client_schemas.RefreshTokenResponse.refresh_token) (<code>[str](#str)</code>) –

####### `leadr.auth.api.client_schemas.RefreshTokenResponse.access_token`

```python
access_token: str = Field(description='New JWT access token')
```

####### `leadr.auth.api.client_schemas.RefreshTokenResponse.expires_in`

```python
expires_in: int = Field(description='Access token expiration time in seconds')
```

####### `leadr.auth.api.client_schemas.RefreshTokenResponse.refresh_token`

```python
refresh_token: str = Field(description='New JWT refresh token (old token is invalidated)')
```

###### `leadr.auth.api.client_schemas.StartSessionRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request schema for starting a device session.

Used by game clients to authenticate and obtain an access token.

**Attributes:**

- [**client_fingerprint**](#leadr.auth.api.client_schemas.StartSessionRequest.client_fingerprint) (<code>[str](#str)</code>) –
- [**game_id**](#leadr.auth.api.client_schemas.StartSessionRequest.game_id) (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) –
- [**metadata**](#leadr.auth.api.client_schemas.StartSessionRequest.metadata) (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\] | None</code>) –
- [**platform**](#leadr.auth.api.client_schemas.StartSessionRequest.platform) (<code>[str](#str) | None</code>) –
- [**test_mode**](#leadr.auth.api.client_schemas.StartSessionRequest.test_mode) (<code>[bool](#bool)</code>) –

####### `leadr.auth.api.client_schemas.StartSessionRequest.client_fingerprint`

```python
client_fingerprint: str = Field(pattern='^[a-fA-F0-9]{64}$', description='Client-generated SHA256 device fingerprint (64 hex characters)')
```

####### `leadr.auth.api.client_schemas.StartSessionRequest.game_id`

```python
game_id: GameID = Field(description='ID of the game this device belongs to')
```

####### `leadr.auth.api.client_schemas.StartSessionRequest.metadata`

```python
metadata: dict[str, Any] | None = Field(default=None, description='Optional device metadata (e.g., OS version, device model)')
```

####### `leadr.auth.api.client_schemas.StartSessionRequest.platform`

```python
platform: str | None = Field(default=None, description="Device platform (e.g., 'ios', 'android', 'pc', 'console')")
```

####### `leadr.auth.api.client_schemas.StartSessionRequest.test_mode`

```python
test_mode: bool = Field(default=False, description='If true, session is in test mode and scores will be marked as test')
```

###### `leadr.auth.api.client_schemas.StartSessionResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response schema for starting an identity session.

Includes both access and refresh tokens which must be saved by the client.

- Access token: Short-lived, used for API requests in Authorization header
- Refresh token: Long-lived, used to obtain new access tokens when expired

**Functions:**

- [**from_domain**](#leadr.auth.api.client_schemas.StartSessionResponse.from_domain) – Convert domain entity to response model with tokens.

**Attributes:**

- [**access_token**](#leadr.auth.api.client_schemas.StartSessionResponse.access_token) (<code>[str](#str)</code>) –
- [**account_id**](#leadr.auth.api.client_schemas.StartSessionResponse.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**display_name**](#leadr.auth.api.client_schemas.StartSessionResponse.display_name) (<code>[str](#str) | None</code>) –
- [**expires_in**](#leadr.auth.api.client_schemas.StartSessionResponse.expires_in) (<code>[int](#int)</code>) –
- [**game_id**](#leadr.auth.api.client_schemas.StartSessionResponse.game_id) (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) –
- [**identity_id**](#leadr.auth.api.client_schemas.StartSessionResponse.identity_id) (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) –
- [**kind**](#leadr.auth.api.client_schemas.StartSessionResponse.kind) (<code>[IdentityKind](./auth.md#leadr.auth.domain.identity.IdentityKind)</code>) –
- [**refresh_token**](#leadr.auth.api.client_schemas.StartSessionResponse.refresh_token) (<code>[str](#str)</code>) –
- [**test_mode**](#leadr.auth.api.client_schemas.StartSessionResponse.test_mode) (<code>[bool](#bool)</code>) –

####### `leadr.auth.api.client_schemas.StartSessionResponse.access_token`

```python
access_token: str = Field(description='JWT access token for authenticating API requests')
```

####### `leadr.auth.api.client_schemas.StartSessionResponse.account_id`

```python
account_id: AccountID = Field(description='ID of the account that owns the game')
```

####### `leadr.auth.api.client_schemas.StartSessionResponse.display_name`

```python
display_name: str | None = Field(default=None, description='Player display name')
```

####### `leadr.auth.api.client_schemas.StartSessionResponse.expires_in`

```python
expires_in: int = Field(description='Access token expiration time in seconds')
```

####### `leadr.auth.api.client_schemas.StartSessionResponse.from_domain`

```python
from_domain(identity, access_token, refresh_token, expires_in, test_mode=False)
```

Convert domain entity to response model with tokens.

**Parameters:**

- **identity** (<code>[Identity](./auth.md#leadr.auth.domain.identity.Identity)</code>) – The domain Identity entity
- **access_token** (<code>[str](#str)</code>) – The plain JWT access token
- **refresh_token** (<code>[str](#str)</code>) – The plain JWT refresh token
- **expires_in** (<code>[int](#int)</code>) – Access token expiration time in seconds
- **test_mode** (<code>[bool](#bool)</code>) – Whether session is in test mode

**Returns:**

- <code>[StartSessionResponse](#leadr.auth.api.client_schemas.StartSessionResponse)</code> – StartSessionResponse with all fields populated

####### `leadr.auth.api.client_schemas.StartSessionResponse.game_id`

```python
game_id: GameID = Field(description='ID of the game')
```

####### `leadr.auth.api.client_schemas.StartSessionResponse.identity_id`

```python
identity_id: IdentityID = Field(description='Unique identifier for the player identity')
```

####### `leadr.auth.api.client_schemas.StartSessionResponse.kind`

```python
kind: IdentityKind = Field(description='Identity type (DEVICE, STEAM, CUSTOM)')
```

####### `leadr.auth.api.client_schemas.StartSessionResponse.refresh_token`

```python
refresh_token: str = Field(description='JWT refresh token for obtaining new access tokens')
```

####### `leadr.auth.api.client_schemas.StartSessionResponse.test_mode`

```python
test_mode: bool = Field(description='Whether session is in test mode')
```

##### `leadr.auth.api.device_routes`

API routes for device management.

**Functions:**

- [**get_device**](#leadr.auth.api.device_routes.get_device) – Get a device by ID.
- [**list_devices**](#leadr.auth.api.device_routes.list_devices) – List devices for an account with optional filters and pagination.
- [**update_device**](#leadr.auth.api.device_routes.update_device) – Update a device (change status).

**Attributes:**

- [**router**](#leadr.auth.api.device_routes.router) –

###### `leadr.auth.api.device_routes.get_device`

```python
get_device(device_id, service, auth)
```

Get a device by ID.

**Parameters:**

- **device_id** (<code>[DeviceID](./common.md#leadr.common.domain.ids.DeviceID)</code>) – Device identifier to retrieve.
- **service** (<code>[DeviceServiceDep](./auth.md#leadr.auth.services.dependencies.DeviceServiceDep)</code>) – Injected device service dependency.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.

**Returns:**

- <code>[DeviceResponse](#leadr.auth.api.device_schemas.DeviceResponse)</code> – DeviceResponse with the device details.

**Raises:**

- <code>403</code> – User does not have access to this device's account.
- <code>404</code> – Device not found or soft-deleted.

###### `leadr.auth.api.device_routes.list_devices`

```python
list_devices(auth, service, pagination, account_id=None, game_id=None, device_status=None)
```

List devices for an account with optional filters and pagination.

Returns all non-deleted devices for the specified account, with optional
filtering by game or status.

For regular users, account_id is automatically derived from their API key.
For superadmins, account_id is optional - if omitted, returns devices from all accounts.

Pagination:

- Default: 20 items per page, sorted by created_at:desc,id:asc
- Custom sort: Use ?sort=name:asc,created_at:desc
- Valid sort fields: id, platform, created_at, updated_at
- Navigation: Use next_cursor/prev_cursor from response

<details class="example" open markdown="1">
<summary>Example</summary>

GET /v1/devices?account_id=acc_123&game_id=game_456&status=active&limit=50

</details>

**Parameters:**

- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.
- **service** (<code>[DeviceServiceDep](./auth.md#leadr.auth.services.dependencies.DeviceServiceDep)</code>) – Injected device service dependency.
- **pagination** (<code>[Annotated](#typing.Annotated)\[[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams), [Depends](#fastapi.Depends)()\]</code>) – Pagination parameters (cursor, limit, sort).
- **account_id** (<code>[Annotated](#typing.Annotated)\[[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None, [Query](#fastapi.Query)(description='Account ID filter')\]</code>) – Optional account_id query parameter (superadmins can omit to see all).
- **game_id** (<code>[Annotated](#typing.Annotated)\[[GameID](./common.md#leadr.common.domain.ids.GameID) | None, [Query](#fastapi.Query)(description='Filter by game ID')\]</code>) – Optional game ID to filter by.
- **device_status** (<code>[Annotated](#typing.Annotated)\[[str](#str) | None, [Query](#fastapi.Query)(alias=[status](#fastapi.status), description='Filter by status')\]</code>) – Optional status to filter by (active, banned, suspended).

**Returns:**

- <code>[PaginatedResponse](./common.md#leadr.common.api.pagination.PaginatedResponse)\[[DeviceResponse](#leadr.auth.api.device_schemas.DeviceResponse)\]</code> – PaginatedResponse with devices and pagination metadata.

**Raises:**

- <code>400</code> – Invalid cursor, sort field, or cursor state mismatch.
- <code>403</code> – User does not have access to the specified account.

###### `leadr.auth.api.device_routes.router`

```python
router = APIRouter()
```

###### `leadr.auth.api.device_routes.update_device`

```python
update_device(device_id, request, service, auth)
```

Update a device (change status).

Allows changing device status to ban, suspend, or activate devices.

**Parameters:**

- **device_id** (<code>[DeviceID](./common.md#leadr.common.domain.ids.DeviceID)</code>) – Device identifier to update.
- **request** (<code>[DeviceUpdateRequest](#leadr.auth.api.device_schemas.DeviceUpdateRequest)</code>) – Update details (status).
- **service** (<code>[DeviceServiceDep](./auth.md#leadr.auth.services.dependencies.DeviceServiceDep)</code>) – Injected device service dependency.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.

**Returns:**

- <code>[DeviceResponse](#leadr.auth.api.device_schemas.DeviceResponse)</code> – DeviceResponse with the updated device details.

**Raises:**

- <code>403</code> – User does not have access to this device's account.
- <code>404</code> – Device not found.
- <code>400</code> – Invalid status value.

##### `leadr.auth.api.device_schemas`

API request and response models for devices.

**Classes:**

- [**DeviceResponse**](#leadr.auth.api.device_schemas.DeviceResponse) – Response model for a device.
- [**DeviceUpdateRequest**](#leadr.auth.api.device_schemas.DeviceUpdateRequest) – Request model for updating a device.

###### `leadr.auth.api.device_schemas.DeviceResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response model for a device.

**Functions:**

- [**from_domain**](#leadr.auth.api.device_schemas.DeviceResponse.from_domain) – Convert domain entity to response model.

**Attributes:**

- [**account_id**](#leadr.auth.api.device_schemas.DeviceResponse.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**client_fingerprint**](#leadr.auth.api.device_schemas.DeviceResponse.client_fingerprint) (<code>[str](#str)</code>) –
- [**created_at**](#leadr.auth.api.device_schemas.DeviceResponse.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**first_seen_at**](#leadr.auth.api.device_schemas.DeviceResponse.first_seen_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**game_id**](#leadr.auth.api.device_schemas.DeviceResponse.game_id) (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) –
- [**id**](#leadr.auth.api.device_schemas.DeviceResponse.id) (<code>[DeviceID](./common.md#leadr.common.domain.ids.DeviceID)</code>) –
- [**last_seen_at**](#leadr.auth.api.device_schemas.DeviceResponse.last_seen_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**metadata**](#leadr.auth.api.device_schemas.DeviceResponse.metadata) (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\]</code>) –
- [**platform**](#leadr.auth.api.device_schemas.DeviceResponse.platform) (<code>[str](#str) | None</code>) –
- [**status**](#leadr.auth.api.device_schemas.DeviceResponse.status) (<code>[str](#str)</code>) –
- [**updated_at**](#leadr.auth.api.device_schemas.DeviceResponse.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.auth.api.device_schemas.DeviceResponse.account_id`

```python
account_id: AccountID = Field(description='ID of the account this device belongs to')
```

####### `leadr.auth.api.device_schemas.DeviceResponse.client_fingerprint`

```python
client_fingerprint: str = Field(description='Client-generated SHA256 device fingerprint (64 hex characters)')
```

####### `leadr.auth.api.device_schemas.DeviceResponse.created_at`

```python
created_at: datetime = Field(description='Timestamp when device record was created (UTC)')
```

####### `leadr.auth.api.device_schemas.DeviceResponse.first_seen_at`

```python
first_seen_at: datetime = Field(description='Timestamp when device was first seen (UTC)')
```

####### `leadr.auth.api.device_schemas.DeviceResponse.from_domain`

```python
from_domain(device)
```

Convert domain entity to response model.

**Parameters:**

- **device** (<code>[Device](./auth.md#leadr.auth.domain.device.Device)</code>) – The domain Device entity to convert.

**Returns:**

- <code>[DeviceResponse](#leadr.auth.api.device_schemas.DeviceResponse)</code> – DeviceResponse with all fields populated from the domain entity.

####### `leadr.auth.api.device_schemas.DeviceResponse.game_id`

```python
game_id: GameID = Field(description='ID of the game this device belongs to')
```

####### `leadr.auth.api.device_schemas.DeviceResponse.id`

```python
id: DeviceID = Field(description='Unique identifier for the device')
```

####### `leadr.auth.api.device_schemas.DeviceResponse.last_seen_at`

```python
last_seen_at: datetime = Field(description='Timestamp when device was last seen (UTC)')
```

####### `leadr.auth.api.device_schemas.DeviceResponse.metadata`

```python
metadata: dict[str, Any] = Field(description='Additional device metadata')
```

####### `leadr.auth.api.device_schemas.DeviceResponse.platform`

```python
platform: str | None = Field(default=None, description='Platform (iOS, Android, etc.), or null')
```

####### `leadr.auth.api.device_schemas.DeviceResponse.status`

```python
status: str = Field(description='Device status: active, banned, or suspended')
```

####### `leadr.auth.api.device_schemas.DeviceResponse.updated_at`

```python
updated_at: datetime = Field(description='Timestamp of last update (UTC)')
```

###### `leadr.auth.api.device_schemas.DeviceUpdateRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request model for updating a device.

**Attributes:**

- [**status**](#leadr.auth.api.device_schemas.DeviceUpdateRequest.status) (<code>[str](#str) | None</code>) –

####### `leadr.auth.api.device_schemas.DeviceUpdateRequest.status`

```python
status: str | None = Field(default=None, description='Updated status: active, banned, or suspended')
```

##### `leadr.auth.api.identity_routes`

API routes for identity management.

**Functions:**

- [**get_identity**](#leadr.auth.api.identity_routes.get_identity) – Get an identity by ID.
- [**list_identities**](#leadr.auth.api.identity_routes.list_identities) – List identities for an account with optional filters and pagination.
- [**update_identity**](#leadr.auth.api.identity_routes.update_identity) – Update an identity.

**Attributes:**

- [**router**](#leadr.auth.api.identity_routes.router) –

###### `leadr.auth.api.identity_routes.get_identity`

```python
get_identity(identity_id, service, auth)
```

Get an identity by ID.

**Parameters:**

- **identity_id** (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) – Identity identifier to retrieve.
- **service** (<code>[IdentityServiceDep](./auth.md#leadr.auth.services.dependencies.IdentityServiceDep)</code>) – Injected identity service dependency.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.

**Returns:**

- <code>[IdentityResponse](#leadr.auth.api.identity_schemas.IdentityResponse)</code> – IdentityResponse with the identity details.

**Raises:**

- <code>403</code> – User does not have access to this identity's account.
- <code>404</code> – Identity not found or soft-deleted.

###### `leadr.auth.api.identity_routes.list_identities`

```python
list_identities(auth, service, pagination, account_id=None, game_id=None, kind=None)
```

List identities for an account with optional filters and pagination.

Returns all non-deleted identities for the specified account, with optional
filtering by game or kind.

For regular users, account_id is automatically derived from their API key.
For superadmins, account_id is optional - if omitted, returns identities from all accounts.

Pagination:

- Default: 20 items per page, sorted by created_at:desc,id:asc
- Custom sort: Use ?sort=display_name:asc,created_at:desc
- Valid sort fields: id, display_name, kind, created_at, updated_at
- Navigation: Use next_cursor/prev_cursor from response

<details class="example" open markdown="1">
<summary>Example</summary>

GET /v1/identities?account_id=acc_123&game_id=game_456&kind=DEVICE&limit=50

</details>

**Parameters:**

- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.
- **service** (<code>[IdentityServiceDep](./auth.md#leadr.auth.services.dependencies.IdentityServiceDep)</code>) – Injected identity service dependency.
- **pagination** (<code>[Annotated](#typing.Annotated)\[[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams), [Depends](#fastapi.Depends)()\]</code>) – Pagination parameters (cursor, limit, sort).
- **account_id** (<code>[Annotated](#typing.Annotated)\[[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None, [Query](#fastapi.Query)(description='Account ID filter')\]</code>) – Optional account_id query parameter (superadmins can omit to see all).
- **game_id** (<code>[Annotated](#typing.Annotated)\[[GameID](./common.md#leadr.common.domain.ids.GameID) | None, [Query](#fastapi.Query)(description='Filter by game ID')\]</code>) – Optional game ID to filter by.
- **kind** (<code>[Annotated](#typing.Annotated)\[[str](#str) | None, [Query](#fastapi.Query)(description='Filter by identity kind')\]</code>) – Optional kind to filter by (DEVICE, STEAM, CUSTOM).

**Returns:**

- <code>[PaginatedResponse](./common.md#leadr.common.api.pagination.PaginatedResponse)\[[IdentityResponse](#leadr.auth.api.identity_schemas.IdentityResponse)\]</code> – PaginatedResponse with identities and pagination metadata.

**Raises:**

- <code>400</code> – Invalid cursor, sort field, kind, or cursor state mismatch.
- <code>403</code> – User does not have access to the specified account.

###### `leadr.auth.api.identity_routes.router`

```python
router = APIRouter()
```

###### `leadr.auth.api.identity_routes.update_identity`

```python
update_identity(identity_id, request, service, auth)
```

Update an identity.

Allows updating display name or soft-deleting the identity.

**Parameters:**

- **identity_id** (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) – Identity identifier to update.
- **request** (<code>[IdentityUpdateRequest](#leadr.auth.api.identity_schemas.IdentityUpdateRequest)</code>) – Update details (display_name, deleted).
- **service** (<code>[IdentityServiceDep](./auth.md#leadr.auth.services.dependencies.IdentityServiceDep)</code>) – Injected identity service dependency.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.

**Returns:**

- <code>[IdentityResponse](#leadr.auth.api.identity_schemas.IdentityResponse)</code> – IdentityResponse with the updated identity details.

**Raises:**

- <code>403</code> – User does not have access to this identity's account.
- <code>404</code> – Identity not found.

##### `leadr.auth.api.identity_schemas`

API request and response models for identities.

**Classes:**

- [**IdentityResponse**](#leadr.auth.api.identity_schemas.IdentityResponse) – Response model for an identity.
- [**IdentitySessionResponse**](#leadr.auth.api.identity_schemas.IdentitySessionResponse) – Response model for an identity session.
- [**IdentityUpdateRequest**](#leadr.auth.api.identity_schemas.IdentityUpdateRequest) – Request model for updating an identity.

###### `leadr.auth.api.identity_schemas.IdentityResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response model for an identity.

**Functions:**

- [**from_domain**](#leadr.auth.api.identity_schemas.IdentityResponse.from_domain) – Convert domain entity to response model.

**Attributes:**

- [**account_id**](#leadr.auth.api.identity_schemas.IdentityResponse.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**created_at**](#leadr.auth.api.identity_schemas.IdentityResponse.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**display_name**](#leadr.auth.api.identity_schemas.IdentityResponse.display_name) (<code>[str](#str) | None</code>) –
- [**external_key**](#leadr.auth.api.identity_schemas.IdentityResponse.external_key) (<code>[str](#str)</code>) –
- [**game_id**](#leadr.auth.api.identity_schemas.IdentityResponse.game_id) (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) –
- [**id**](#leadr.auth.api.identity_schemas.IdentityResponse.id) (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) –
- [**kind**](#leadr.auth.api.identity_schemas.IdentityResponse.kind) (<code>[str](#str)</code>) –
- [**updated_at**](#leadr.auth.api.identity_schemas.IdentityResponse.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.auth.api.identity_schemas.IdentityResponse.account_id`

```python
account_id: AccountID = Field(description='ID of the account this identity belongs to')
```

####### `leadr.auth.api.identity_schemas.IdentityResponse.created_at`

```python
created_at: datetime = Field(description='Timestamp when identity was created (UTC)')
```

####### `leadr.auth.api.identity_schemas.IdentityResponse.display_name`

```python
display_name: str | None = Field(default=None, description='Player display name')
```

####### `leadr.auth.api.identity_schemas.IdentityResponse.external_key`

```python
external_key: str = Field(description='External identifier (device ID, Steam ID, etc.)')
```

####### `leadr.auth.api.identity_schemas.IdentityResponse.from_domain`

```python
from_domain(identity)
```

Convert domain entity to response model.

**Parameters:**

- **identity** (<code>[Identity](./auth.md#leadr.auth.domain.identity.Identity)</code>) – The domain Identity entity to convert.

**Returns:**

- <code>[IdentityResponse](#leadr.auth.api.identity_schemas.IdentityResponse)</code> – IdentityResponse with all fields populated from the domain entity.

####### `leadr.auth.api.identity_schemas.IdentityResponse.game_id`

```python
game_id: GameID = Field(description='ID of the game this identity belongs to')
```

####### `leadr.auth.api.identity_schemas.IdentityResponse.id`

```python
id: IdentityID = Field(description='Unique identifier for the identity')
```

####### `leadr.auth.api.identity_schemas.IdentityResponse.kind`

```python
kind: str = Field(description='Identity kind: DEVICE, STEAM, or CUSTOM')
```

####### `leadr.auth.api.identity_schemas.IdentityResponse.updated_at`

```python
updated_at: datetime = Field(description='Timestamp of last update (UTC)')
```

###### `leadr.auth.api.identity_schemas.IdentitySessionResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response model for an identity session.

**Functions:**

- [**from_domain**](#leadr.auth.api.identity_schemas.IdentitySessionResponse.from_domain) – Convert domain entity to response model.

**Attributes:**

- [**created_at**](#leadr.auth.api.identity_schemas.IdentitySessionResponse.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**expires_at**](#leadr.auth.api.identity_schemas.IdentitySessionResponse.expires_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**id**](#leadr.auth.api.identity_schemas.IdentitySessionResponse.id) (<code>[IdentitySessionID](./common.md#leadr.common.domain.ids.IdentitySessionID)</code>) –
- [**identity_id**](#leadr.auth.api.identity_schemas.IdentitySessionResponse.identity_id) (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) –
- [**refresh_expires_at**](#leadr.auth.api.identity_schemas.IdentitySessionResponse.refresh_expires_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**revoked_at**](#leadr.auth.api.identity_schemas.IdentitySessionResponse.revoked_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**updated_at**](#leadr.auth.api.identity_schemas.IdentitySessionResponse.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.auth.api.identity_schemas.IdentitySessionResponse.created_at`

```python
created_at: datetime = Field(description='Timestamp when session was created (UTC)')
```

####### `leadr.auth.api.identity_schemas.IdentitySessionResponse.expires_at`

```python
expires_at: datetime = Field(description='Access token expiration time (UTC)')
```

####### `leadr.auth.api.identity_schemas.IdentitySessionResponse.from_domain`

```python
from_domain(session)
```

Convert domain entity to response model.

**Parameters:**

- **session** (<code>[IdentitySession](./auth.md#leadr.auth.domain.identity.IdentitySession)</code>) – The domain IdentitySession entity to convert.

**Returns:**

- <code>[IdentitySessionResponse](#leadr.auth.api.identity_schemas.IdentitySessionResponse)</code> – IdentitySessionResponse with all fields populated from the domain entity.

####### `leadr.auth.api.identity_schemas.IdentitySessionResponse.id`

```python
id: IdentitySessionID = Field(description='Unique identifier for the session')
```

####### `leadr.auth.api.identity_schemas.IdentitySessionResponse.identity_id`

```python
identity_id: IdentityID = Field(description='ID of the identity this session belongs to')
```

####### `leadr.auth.api.identity_schemas.IdentitySessionResponse.refresh_expires_at`

```python
refresh_expires_at: datetime = Field(description='Refresh token expiration time (UTC)')
```

####### `leadr.auth.api.identity_schemas.IdentitySessionResponse.revoked_at`

```python
revoked_at: datetime | None = Field(default=None, description='Time when session was revoked')
```

####### `leadr.auth.api.identity_schemas.IdentitySessionResponse.updated_at`

```python
updated_at: datetime = Field(description='Timestamp of last update (UTC)')
```

###### `leadr.auth.api.identity_schemas.IdentityUpdateRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request model for updating an identity.

**Attributes:**

- [**deleted**](#leadr.auth.api.identity_schemas.IdentityUpdateRequest.deleted) (<code>[bool](#bool) | None</code>) –
- [**display_name**](#leadr.auth.api.identity_schemas.IdentityUpdateRequest.display_name) (<code>[str](#str) | None</code>) –

####### `leadr.auth.api.identity_schemas.IdentityUpdateRequest.deleted`

```python
deleted: bool | None = Field(default=None, description='Set to true to soft-delete the identity')
```

####### `leadr.auth.api.identity_schemas.IdentityUpdateRequest.display_name`

```python
display_name: str | None = Field(default=None, description='Updated display name')
```

##### `leadr.auth.api.identity_session_routes`

API routes for identity session management.

**Functions:**

- [**get_identity_session**](#leadr.auth.api.identity_session_routes.get_identity_session) – Get an identity session by ID.
- [**list_identity_sessions**](#leadr.auth.api.identity_session_routes.list_identity_sessions) – List identity sessions with optional filters and pagination.
- [**revoke_identity_session**](#leadr.auth.api.identity_session_routes.revoke_identity_session) – Revoke an identity session.

**Attributes:**

- [**router**](#leadr.auth.api.identity_session_routes.router) –

###### `leadr.auth.api.identity_session_routes.get_identity_session`

```python
get_identity_session(session_id, service, auth)
```

Get an identity session by ID.

**Parameters:**

- **session_id** (<code>[IdentitySessionID](./common.md#leadr.common.domain.ids.IdentitySessionID)</code>) – Session identifier to retrieve.
- **service** (<code>[IdentityServiceDep](./auth.md#leadr.auth.services.dependencies.IdentityServiceDep)</code>) – Injected identity service dependency.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.

**Returns:**

- <code>[IdentitySessionResponse](#leadr.auth.api.identity_schemas.IdentitySessionResponse)</code> – IdentitySessionResponse with the session details.

**Raises:**

- <code>403</code> – User does not have access to this session's account.
- <code>404</code> – Session not found or soft-deleted.

###### `leadr.auth.api.identity_session_routes.list_identity_sessions`

```python
list_identity_sessions(auth, service, pagination, account_id=None, identity_id=None)
```

List identity sessions with optional filters and pagination.

Returns all non-deleted sessions, with optional filtering by account or identity.

For regular users, account_id is automatically derived from their API key.
For superadmins, account_id is optional - if omitted, returns sessions from all accounts.

Pagination:

- Default: 20 items per page, sorted by created_at:desc,id:asc
- Custom sort: Use ?sort=created_at:desc
- Valid sort fields: id, created_at, updated_at
- Navigation: Use next_cursor/prev_cursor from response

<details class="example" open markdown="1">
<summary>Example</summary>

GET /v1/identity-sessions?account_id=acc_123&identity_id=ide_456&limit=50

</details>

**Parameters:**

- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.
- **service** (<code>[IdentityServiceDep](./auth.md#leadr.auth.services.dependencies.IdentityServiceDep)</code>) – Injected identity service dependency.
- **pagination** (<code>[Annotated](#typing.Annotated)\[[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams), [Depends](#fastapi.Depends)()\]</code>) – Pagination parameters (cursor, limit, sort).
- **account_id** (<code>[Annotated](#typing.Annotated)\[[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None, [Query](#fastapi.Query)(description='Account ID filter')\]</code>) – Optional account_id query parameter (superadmins can omit to see all).
- **identity_id** (<code>[Annotated](#typing.Annotated)\[[IdentityID](./common.md#leadr.common.domain.ids.IdentityID) | None, [Query](#fastapi.Query)(description='Filter by identity ID')\]</code>) – Optional identity ID to filter by.

**Returns:**

- <code>[PaginatedResponse](./common.md#leadr.common.api.pagination.PaginatedResponse)\[[IdentitySessionResponse](#leadr.auth.api.identity_schemas.IdentitySessionResponse)\]</code> – PaginatedResponse with sessions and pagination metadata.

**Raises:**

- <code>400</code> – Invalid cursor, sort field, or cursor state mismatch.
- <code>403</code> – User does not have access to the specified account.

###### `leadr.auth.api.identity_session_routes.revoke_identity_session`

```python
revoke_identity_session(session_id, service, auth)
```

Revoke an identity session.

Marks the session as revoked, preventing further use.

**Parameters:**

- **session_id** (<code>[IdentitySessionID](./common.md#leadr.common.domain.ids.IdentitySessionID)</code>) – Session identifier to revoke.
- **service** (<code>[IdentityServiceDep](./auth.md#leadr.auth.services.dependencies.IdentityServiceDep)</code>) – Injected identity service dependency.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.

**Returns:**

- <code>[IdentitySessionResponse](#leadr.auth.api.identity_schemas.IdentitySessionResponse)</code> – IdentitySessionResponse with the revoked session details.

**Raises:**

- <code>403</code> – User does not have access to this session's account.
- <code>404</code> – Session not found.

###### `leadr.auth.api.identity_session_routes.router`

```python
router = APIRouter()
```

#### `leadr.auth.bootstrap`

Superadmin bootstrap functionality.

This module provides functionality to automatically create a superadmin user
and associated account on application startup if none exists.

**Functions:**

- [**ensure_superadmin_exists**](#leadr.auth.bootstrap.ensure_superadmin_exists) – Ensure a superadmin user exists, creating one if necessary.

**Attributes:**

- [**logger**](./auth.md#leadr.auth.bootstrap.logger) –

##### `leadr.auth.bootstrap.ensure_superadmin_exists`

```python
ensure_superadmin_exists(session)
```

Ensure a superadmin user exists, creating one if necessary.

This function is idempotent and safe to call multiple times. It will:

1. Check if any superadmin user already exists
1. If not, create:
   - A system account (configured via SUPERADMIN_ACCOUNT_NAME/SLUG)
   - A superadmin user (configured via SUPERADMIN_EMAIL/DISPLAY_NAME)
   - An API key for the superadmin (using SUPERADMIN_API_KEY)

The function commits the transaction if it creates entities.

**Parameters:**

- **session** (<code>[AsyncSession](#sqlalchemy.ext.asyncio.AsyncSession)</code>) – Database session to use for queries and inserts.

<details class="example" open markdown="1">
<summary>Example</summary>

> > > async with get_session() as session:
> > > ... await ensure_superadmin_exists(session)

</details>

##### `leadr.auth.bootstrap.logger`

```python
logger = logging.getLogger(__name__)
```

#### `leadr.auth.dependencies`

Authentication dependencies for FastAPI.

**Classes:**

- [**AdminAuthContext**](./auth.md#leadr.auth.dependencies.AdminAuthContext) – Admin authentication context with guaranteed user and api_key fields.
- [**AuthContext**](./auth.md#leadr.auth.dependencies.AuthContext) – Unified authentication context for both admin and client auth.
- [**AuthContextDependency**](./auth.md#leadr.auth.dependencies.AuthContextDependency) – Parameterizable authentication dependency using FastAPI class instance pattern.
- [**ClientAuthContext**](./auth.md#leadr.auth.dependencies.ClientAuthContext) – Client authentication context with guaranteed identity field.

**Attributes:**

- [**AdminAuthContextDep**](./auth.md#leadr.auth.dependencies.AdminAuthContextDep) –
- [**AdminAuthContextWithAccountIDDep**](./auth.md#leadr.auth.dependencies.AdminAuthContextWithAccountIDDep) –
- [**ClientAuthContextDep**](./auth.md#leadr.auth.dependencies.ClientAuthContextDep) –
- [**ClientAuthContextWithNonceDep**](./auth.md#leadr.auth.dependencies.ClientAuthContextWithNonceDep) –
- [**SuperAdminAuthContextDep**](./auth.md#leadr.auth.dependencies.SuperAdminAuthContextDep) –
- [**logger**](./auth.md#leadr.auth.dependencies.logger) –
- [**require_admin_auth**](#leadr.auth.dependencies.require_admin_auth) –
- [**require_admin_auth_with_account_id**](#leadr.auth.dependencies.require_admin_auth_with_account_id) –
- [**require_client_auth**](#leadr.auth.dependencies.require_client_auth) –
- [**require_client_auth_with_nonce**](#leadr.auth.dependencies.require_client_auth_with_nonce) –
- [**require_superadmin_auth**](#leadr.auth.dependencies.require_superadmin_auth) –

##### `leadr.auth.dependencies.AdminAuthContext`

```python
AdminAuthContext(account_id, user, api_key, identity=None)
```

Bases: <code>[AuthContext](./auth.md#leadr.auth.dependencies.AuthContext)</code>

Admin authentication context with guaranteed user and api_key fields.

This subclass is returned by admin-only authentication dependencies,
providing type-safe access to user and api_key without None checks.

Note: This class does not use @dataclass to avoid conflicts between
frozen dataclass fields and property overrides.

**Attributes:**

- [**account_id**](#leadr.auth.dependencies.AdminAuthContext.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – The account ID for this request (may differ from API key's
  account for superadmins).
- [**user**](./auth.md#leadr.auth.dependencies.AdminAuthContext.user) (<code>[User](./accounts.md#leadr.accounts.domain.user.User)</code>) – The authenticated user (guaranteed non-None).
- [**api_key**](#leadr.auth.dependencies.AdminAuthContext.api_key) (<code>[APIKey](#leadr.auth.domain.api_key.APIKey)</code>) – The authenticated API key (guaranteed non-None).
- [**identity**](./auth.md#leadr.auth.dependencies.AdminAuthContext.identity) (<code>None</code>) – Always None for admin auth.

**Functions:**

- [**has_access_to_account**](#leadr.auth.dependencies.AdminAuthContext.has_access_to_account) – Check if the authenticated context has access to a specific account.

###### `leadr.auth.dependencies.AdminAuthContext.account_id`

```python
account_id: AccountID
```

Get account ID.

###### `leadr.auth.dependencies.AdminAuthContext.api_key`

```python
api_key: APIKey
```

Get API key (guaranteed non-None for admin auth).

###### `leadr.auth.dependencies.AdminAuthContext.auth_type`

```python
auth_type: Literal['admin', 'client']
```

Return the authentication type.

**Returns:**

- <code>[Literal](#typing.Literal)['admin', 'client']</code> – "admin" if authenticated via API key, "client" if via identity token.

###### `leadr.auth.dependencies.AdminAuthContext.has_access_to_account`

```python
has_access_to_account(account_id)
```

Check if the authenticated context has access to a specific account.

<details class="for-admin-auth" open markdown="1">
<summary>For admin auth</summary>

- Superadmins have access to all accounts
- Regular users only have access to their own account

</details>

<details class="for-client-auth" open markdown="1">
<summary>For client auth</summary>

- Identities only have access to their game's account

</details>

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – The account ID to check access for.

**Returns:**

- <code>[bool](#bool)</code> – True if context has access to the account, False otherwise.

###### `leadr.auth.dependencies.AdminAuthContext.identity`

```python
identity: None
```

Get identity (always None for admin auth).

###### `leadr.auth.dependencies.AdminAuthContext.is_superadmin`

```python
is_superadmin: bool
```

Check if the authenticated user has superadmin privileges.

Only applies to admin auth. Client auth never has superadmin privileges.

**Returns:**

- <code>[bool](#bool)</code> – True if user is a superadmin, False otherwise.

###### `leadr.auth.dependencies.AdminAuthContext.user`

```python
user: User
```

Get user (guaranteed non-None for admin auth).

##### `leadr.auth.dependencies.AdminAuthContextDep`

```python
AdminAuthContextDep = Annotated[AdminAuthContext, Depends(require_admin_auth)]
```

##### `leadr.auth.dependencies.AdminAuthContextWithAccountIDDep`

```python
AdminAuthContextWithAccountIDDep = Annotated[AdminAuthContext, Depends(require_admin_auth_with_account_id)]
```

##### `leadr.auth.dependencies.AuthContext`

```python
AuthContext(account_id, user=None, api_key=None, identity=None)
```

Unified authentication context for both admin and client auth.

This context provides a unified interface for both API key (admin) and
identity token (client) authentication. It includes helper methods for
authorization checks that work transparently across both auth types.

**Attributes:**

- [**account_id**](#leadr.auth.dependencies.AuthContext.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – The account ID associated with this auth context.
- [**user**](./auth.md#leadr.auth.dependencies.AuthContext.user) (<code>[User](./accounts.md#leadr.accounts.domain.user.User) | None</code>) – The user entity (present for admin auth only).
- [**api_key**](#leadr.auth.dependencies.AuthContext.api_key) (<code>[APIKey](#leadr.auth.domain.api_key.APIKey) | None</code>) – The API key entity (present for admin auth only).
- [**identity**](./auth.md#leadr.auth.dependencies.AuthContext.identity) (<code>[Identity](./auth.md#leadr.auth.domain.identity.Identity) | None</code>) – The identity entity (present for client auth only).

**Functions:**

- [**has_access_to_account**](#leadr.auth.dependencies.AuthContext.has_access_to_account) – Check if the authenticated context has access to a specific account.

###### `leadr.auth.dependencies.AuthContext.account_id`

```python
account_id: AccountID
```

###### `leadr.auth.dependencies.AuthContext.api_key`

```python
api_key: APIKey | None = None
```

###### `leadr.auth.dependencies.AuthContext.auth_type`

```python
auth_type: Literal['admin', 'client']
```

Return the authentication type.

**Returns:**

- <code>[Literal](#typing.Literal)['admin', 'client']</code> – "admin" if authenticated via API key, "client" if via identity token.

###### `leadr.auth.dependencies.AuthContext.has_access_to_account`

```python
has_access_to_account(account_id)
```

Check if the authenticated context has access to a specific account.

<details class="for-admin-auth" open markdown="1">
<summary>For admin auth</summary>

- Superadmins have access to all accounts
- Regular users only have access to their own account

</details>

<details class="for-client-auth" open markdown="1">
<summary>For client auth</summary>

- Identities only have access to their game's account

</details>

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – The account ID to check access for.

**Returns:**

- <code>[bool](#bool)</code> – True if context has access to the account, False otherwise.

###### `leadr.auth.dependencies.AuthContext.identity`

```python
identity: Identity | None = None
```

###### `leadr.auth.dependencies.AuthContext.is_superadmin`

```python
is_superadmin: bool
```

Check if the authenticated user has superadmin privileges.

Only applies to admin auth. Client auth never has superadmin privileges.

**Returns:**

- <code>[bool](#bool)</code> – True if user is a superadmin, False otherwise.

###### `leadr.auth.dependencies.AuthContext.user`

```python
user: User | None = None
```

##### `leadr.auth.dependencies.AuthContextDependency`

```python
AuthContextDependency(require_admin=False, require_client=False, require_nonce=False, require_superadmin_account_id=False, require_superadmin=False)
```

Parameterizable authentication dependency using FastAPI class instance pattern.

This class implements the callable instance pattern to provide flexible
authentication requirements. Create instances with different parameters
to require different auth types.

**Examples:**

```pycon
>>> require_admin_auth = AuthContextDependency(require_admin=True)
>>> require_client_auth = AuthContextDependency(require_client=True)
>>> require_either_auth = AuthContextDependency(require_admin=True, require_client=True)
>>>
>>> @router.get("/admin-only")
>>> async def admin_endpoint(
>>>     auth: Annotated[AuthContext, Depends(require_admin_auth)]
>>> ):
>>>     return {"account": auth.account_id}
```

**Attributes:**

- [**require_admin**](#leadr.auth.dependencies.AuthContextDependency.require_admin) –
- [**require_client**](#leadr.auth.dependencies.AuthContextDependency.require_client) –
- [**require_nonce**](#leadr.auth.dependencies.AuthContextDependency.require_nonce) –
- [**require_superadmin**](#leadr.auth.dependencies.AuthContextDependency.require_superadmin) –
- [**require_superadmin_account_id**](#leadr.auth.dependencies.AuthContextDependency.require_superadmin_account_id) –

**Parameters:**

- **require_admin** (<code>[bool](#bool)</code>) – If True, admin API key authentication is required.
- **require_client** (<code>[bool](#bool)</code>) – If True, client device token authentication is required.
- **require_nonce** (<code>[bool](#bool)</code>) – If True, nonce validation is required for client auth (mutations).
- **require_superadmin_account_id** (<code>[bool](#bool)</code>) – If True, superadmins must provide account_id
  query parameter on GET requests. Used for list endpoints.
- **require_superadmin** (<code>[bool](#bool)</code>) – If True, only superadmin users are allowed. Returns 403
  for non-superadmin users. Implies require_admin=True.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If neither require_admin nor require_client is True.

###### `leadr.auth.dependencies.AuthContextDependency.require_admin`

```python
require_admin = require_admin
```

###### `leadr.auth.dependencies.AuthContextDependency.require_client`

```python
require_client = require_client
```

###### `leadr.auth.dependencies.AuthContextDependency.require_nonce`

```python
require_nonce = require_nonce
```

###### `leadr.auth.dependencies.AuthContextDependency.require_superadmin`

```python
require_superadmin = require_superadmin
```

###### `leadr.auth.dependencies.AuthContextDependency.require_superadmin_account_id`

```python
require_superadmin_account_id = require_superadmin_account_id
```

##### `leadr.auth.dependencies.ClientAuthContext`

```python
ClientAuthContext(account_id, identity, user=None, api_key=None, test_mode=False)
```

Bases: <code>[AuthContext](./auth.md#leadr.auth.dependencies.AuthContext)</code>

Client authentication context with guaranteed identity field.

This subclass is returned by client-only authentication dependencies,
providing type-safe access to identity without None checks.

Note: This class does not use @dataclass to avoid conflicts between
frozen dataclass fields and property overrides.

**Attributes:**

- [**account_id**](#leadr.auth.dependencies.ClientAuthContext.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – The account ID from the identity's game.
- [**identity**](./auth.md#leadr.auth.dependencies.ClientAuthContext.identity) (<code>[Identity](./auth.md#leadr.auth.domain.identity.Identity)</code>) – The player identity (guaranteed non-None).
- [**user**](./auth.md#leadr.auth.dependencies.ClientAuthContext.user) (<code>None</code>) – Always None for client auth.
- [**api_key**](#leadr.auth.dependencies.ClientAuthContext.api_key) (<code>None</code>) – Always None for client auth.
- [**test_mode**](#leadr.auth.dependencies.ClientAuthContext.test_mode) (<code>[bool](#bool)</code>) – Whether this session is in test mode.

**Functions:**

- [**has_access_to_account**](#leadr.auth.dependencies.ClientAuthContext.has_access_to_account) – Check if the authenticated context has access to a specific account.

###### `leadr.auth.dependencies.ClientAuthContext.account_id`

```python
account_id: AccountID
```

Get account ID.

###### `leadr.auth.dependencies.ClientAuthContext.api_key`

```python
api_key: None
```

Get API key (always None for client auth).

###### `leadr.auth.dependencies.ClientAuthContext.auth_type`

```python
auth_type: Literal['admin', 'client']
```

Return the authentication type.

**Returns:**

- <code>[Literal](#typing.Literal)['admin', 'client']</code> – "admin" if authenticated via API key, "client" if via identity token.

###### `leadr.auth.dependencies.ClientAuthContext.game_id`

```python
game_id: GameID
```

Get game ID from identity (convenience property).

###### `leadr.auth.dependencies.ClientAuthContext.has_access_to_account`

```python
has_access_to_account(account_id)
```

Check if the authenticated context has access to a specific account.

<details class="for-admin-auth" open markdown="1">
<summary>For admin auth</summary>

- Superadmins have access to all accounts
- Regular users only have access to their own account

</details>

<details class="for-client-auth" open markdown="1">
<summary>For client auth</summary>

- Identities only have access to their game's account

</details>

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – The account ID to check access for.

**Returns:**

- <code>[bool](#bool)</code> – True if context has access to the account, False otherwise.

###### `leadr.auth.dependencies.ClientAuthContext.identity`

```python
identity: Identity
```

Get identity (guaranteed non-None for client auth).

###### `leadr.auth.dependencies.ClientAuthContext.is_superadmin`

```python
is_superadmin: bool
```

Check if the authenticated user has superadmin privileges.

Only applies to admin auth. Client auth never has superadmin privileges.

**Returns:**

- <code>[bool](#bool)</code> – True if user is a superadmin, False otherwise.

###### `leadr.auth.dependencies.ClientAuthContext.test_mode`

```python
test_mode: bool
```

Get test_mode flag (whether session is in test mode).

###### `leadr.auth.dependencies.ClientAuthContext.user`

```python
user: None
```

Get user (always None for client auth).

##### `leadr.auth.dependencies.ClientAuthContextDep`

```python
ClientAuthContextDep = Annotated[ClientAuthContext, Depends(require_client_auth)]
```

##### `leadr.auth.dependencies.ClientAuthContextWithNonceDep`

```python
ClientAuthContextWithNonceDep = Annotated[ClientAuthContext, Depends(require_client_auth_with_nonce)]
```

##### `leadr.auth.dependencies.SuperAdminAuthContextDep`

```python
SuperAdminAuthContextDep = Annotated[AdminAuthContext, Depends(require_superadmin_auth)]
```

##### `leadr.auth.dependencies.logger`

```python
logger = logging.getLogger(__name__)
```

##### `leadr.auth.dependencies.require_admin_auth`

```python
require_admin_auth = AuthContextDependency(require_admin=True)
```

##### `leadr.auth.dependencies.require_admin_auth_with_account_id`

```python
require_admin_auth_with_account_id = AuthContextDependency(require_admin=True, require_superadmin_account_id=True)
```

##### `leadr.auth.dependencies.require_client_auth`

```python
require_client_auth = AuthContextDependency(require_client=True)
```

##### `leadr.auth.dependencies.require_client_auth_with_nonce`

```python
require_client_auth_with_nonce = AuthContextDependency(require_client=True, require_nonce=True)
```

##### `leadr.auth.dependencies.require_superadmin_auth`

```python
require_superadmin_auth = AuthContextDependency(require_superadmin=True)
```

#### `leadr.auth.domain`

**Modules:**

- [**api_key**](#leadr.auth.domain.api_key) – API Key domain model.
- [**device**](./auth.md#leadr.auth.domain.device) – Device domain models for client authentication.
- [**identity**](./auth.md#leadr.auth.domain.identity) – Identity domain models for player identification.
- [**nonce**](./auth.md#leadr.auth.domain.nonce) – Nonce domain entity for replay protection.

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
Each API key is owned by a specific user within the account.

**Functions:**

- [**is_expired**](#leadr.auth.domain.api_key.APIKey.is_expired) – Check if the API key has expired.
- [**is_valid**](#leadr.auth.domain.api_key.APIKey.is_valid) – Check if the API key is valid for use.
- [**record_usage**](#leadr.auth.domain.api_key.APIKey.record_usage) – Record that the API key was used.
- [**restore**](#leadr.auth.domain.api_key.APIKey.restore) – Restore a soft-deleted entity.
- [**revoke**](#leadr.auth.domain.api_key.APIKey.revoke) – Revoke the API key, preventing further use.
- [**soft_delete**](#leadr.auth.domain.api_key.APIKey.soft_delete) – Mark entity as soft-deleted.
- [**validate_key_prefix**](#leadr.auth.domain.api_key.APIKey.validate_key_prefix) – Validate that key_prefix starts with 'ldr\_'.

**Attributes:**

- [**account_id**](#leadr.auth.domain.api_key.APIKey.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**created_at**](#leadr.auth.domain.api_key.APIKey.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**deleted_at**](#leadr.auth.domain.api_key.APIKey.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**expires_at**](#leadr.auth.domain.api_key.APIKey.expires_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**id**](#leadr.auth.domain.api_key.APIKey.id) (<code>[APIKeyID](./common.md#leadr.common.domain.ids.APIKeyID)</code>) –
- [**is_deleted**](#leadr.auth.domain.api_key.APIKey.is_deleted) (<code>[bool](#bool)</code>) – Check if entity is soft-deleted.
- [**key_hash**](#leadr.auth.domain.api_key.APIKey.key_hash) (<code>[str](#str)</code>) –
- [**key_prefix**](#leadr.auth.domain.api_key.APIKey.key_prefix) (<code>[str](#str)</code>) –
- [**last_used_at**](#leadr.auth.domain.api_key.APIKey.last_used_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**model_config**](#leadr.auth.domain.api_key.APIKey.model_config) –
- [**name**](#leadr.auth.domain.api_key.APIKey.name) (<code>[str](#str)</code>) –
- [**status**](#leadr.auth.domain.api_key.APIKey.status) (<code>[APIKeyStatus](#leadr.auth.domain.api_key.APIKeyStatus)</code>) –
- [**updated_at**](#leadr.auth.domain.api_key.APIKey.updated_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**user_id**](#leadr.auth.domain.api_key.APIKey.user_id) (<code>[UserID](./common.md#leadr.common.domain.ids.UserID)</code>) –

####### `leadr.auth.domain.api_key.APIKey.account_id`

```python
account_id: AccountID
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
id: APIKeyID = Field(frozen=True, default_factory=APIKeyID, description='Unique API key identifier')
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

####### `leadr.auth.domain.api_key.APIKey.user_id`

```python
user_id: UserID
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

##### `leadr.auth.domain.device`

Device domain models for client authentication.

**Classes:**

- [**Device**](./auth.md#leadr.auth.domain.device.Device) – Device domain entity.
- [**DeviceStatus**](./auth.md#leadr.auth.domain.device.DeviceStatus) – Device status enumeration.

###### `leadr.auth.domain.device.Device`

Bases: <code>[Entity](./common.md#leadr.common.domain.models.Entity)</code>

Device domain entity.

Represents a game client device (e.g., mobile device, PC, console).
Devices are scoped per-game and used for client authentication.
Each device is identified by a client-generated SHA256 fingerprint.

**Functions:**

- [**activate**](./auth.md#leadr.auth.domain.device.Device.activate) – Activate the device, allowing authentication.
- [**ban**](./auth.md#leadr.auth.domain.device.Device.ban) – Ban the device, preventing further authentication.
- [**is_active**](#leadr.auth.domain.device.Device.is_active) – Check if the device is active.
- [**restore**](./auth.md#leadr.auth.domain.device.Device.restore) – Restore a soft-deleted entity.
- [**soft_delete**](#leadr.auth.domain.device.Device.soft_delete) – Mark entity as soft-deleted.
- [**suspend**](./auth.md#leadr.auth.domain.device.Device.suspend) – Suspend the device temporarily.
- [**update_last_seen**](#leadr.auth.domain.device.Device.update_last_seen) – Update the last_seen_at timestamp to current time.
- [**validate_sha256**](#leadr.auth.domain.device.Device.validate_sha256) – Validate that client_fingerprint is a valid SHA256 hash.

**Attributes:**

- [**account_id**](#leadr.auth.domain.device.Device.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**client_fingerprint**](#leadr.auth.domain.device.Device.client_fingerprint) (<code>[str](#str)</code>) –
- [**created_at**](#leadr.auth.domain.device.Device.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**deleted_at**](#leadr.auth.domain.device.Device.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**first_seen_at**](#leadr.auth.domain.device.Device.first_seen_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**game_id**](#leadr.auth.domain.device.Device.game_id) (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) –
- [**id**](./auth.md#leadr.auth.domain.device.Device.id) (<code>[DeviceID](./common.md#leadr.common.domain.ids.DeviceID)</code>) –
- [**is_deleted**](#leadr.auth.domain.device.Device.is_deleted) (<code>[bool](#bool)</code>) – Check if entity is soft-deleted.
- [**last_seen_at**](#leadr.auth.domain.device.Device.last_seen_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**metadata**](./auth.md#leadr.auth.domain.device.Device.metadata) (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\]</code>) –
- [**model_config**](#leadr.auth.domain.device.Device.model_config) –
- [**platform**](./auth.md#leadr.auth.domain.device.Device.platform) (<code>[str](#str) | None</code>) –
- [**status**](./auth.md#leadr.auth.domain.device.Device.status) (<code>[DeviceStatus](./auth.md#leadr.auth.domain.device.DeviceStatus)</code>) –
- [**updated_at**](#leadr.auth.domain.device.Device.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.auth.domain.device.Device.account_id`

```python
account_id: AccountID
```

####### `leadr.auth.domain.device.Device.activate`

```python
activate()
```

Activate the device, allowing authentication.

####### `leadr.auth.domain.device.Device.ban`

```python
ban()
```

Ban the device, preventing further authentication.

####### `leadr.auth.domain.device.Device.client_fingerprint`

```python
client_fingerprint: str = Field(description='Client-generated SHA256 device fingerprint (64 hex characters)')
```

####### `leadr.auth.domain.device.Device.created_at`

```python
created_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp when entity was created (UTC)')
```

####### `leadr.auth.domain.device.Device.deleted_at`

```python
deleted_at: datetime | None = Field(default=None, description='Timestamp when entity was soft-deleted (UTC), or null if active')
```

####### `leadr.auth.domain.device.Device.first_seen_at`

```python
first_seen_at: datetime
```

####### `leadr.auth.domain.device.Device.game_id`

```python
game_id: GameID
```

####### `leadr.auth.domain.device.Device.id`

```python
id: DeviceID = Field(frozen=True, default_factory=DeviceID, description='Unique device identifier')
```

####### `leadr.auth.domain.device.Device.is_active`

```python
is_active()
```

Check if the device is active.

**Returns:**

- <code>[bool](#bool)</code> – True if the device status is ACTIVE.

####### `leadr.auth.domain.device.Device.is_deleted`

```python
is_deleted: bool
```

Check if entity is soft-deleted.

**Returns:**

- <code>[bool](#bool)</code> – True if the entity has a deleted_at timestamp, False otherwise.

####### `leadr.auth.domain.device.Device.last_seen_at`

```python
last_seen_at: datetime
```

####### `leadr.auth.domain.device.Device.metadata`

```python
metadata: dict[str, Any] = {}
```

####### `leadr.auth.domain.device.Device.model_config`

```python
model_config = ConfigDict(validate_assignment=True)
```

####### `leadr.auth.domain.device.Device.platform`

```python
platform: str | None = None
```

####### `leadr.auth.domain.device.Device.restore`

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

####### `leadr.auth.domain.device.Device.soft_delete`

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

####### `leadr.auth.domain.device.Device.status`

```python
status: DeviceStatus = DeviceStatus.ACTIVE
```

####### `leadr.auth.domain.device.Device.suspend`

```python
suspend()
```

Suspend the device temporarily.

####### `leadr.auth.domain.device.Device.update_last_seen`

```python
update_last_seen()
```

Update the last_seen_at timestamp to current time.

####### `leadr.auth.domain.device.Device.updated_at`

```python
updated_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp of last update (UTC)')
```

####### `leadr.auth.domain.device.Device.validate_sha256`

```python
validate_sha256(v)
```

Validate that client_fingerprint is a valid SHA256 hash.

**Parameters:**

- **v** (<code>[str](#str)</code>) – The client_fingerprint value to validate.

**Returns:**

- <code>[str](#str)</code> – The normalized (lowercase) client_fingerprint.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If the fingerprint is not a valid 64-character hex string.

###### `leadr.auth.domain.device.DeviceStatus`

Bases: <code>[Enum](#enum.Enum)</code>

Device status enumeration.

**Attributes:**

- [**ACTIVE**](./auth.md#leadr.auth.domain.device.DeviceStatus.ACTIVE) –
- [**BANNED**](./auth.md#leadr.auth.domain.device.DeviceStatus.BANNED) –
- [**SUSPENDED**](./auth.md#leadr.auth.domain.device.DeviceStatus.SUSPENDED) –

####### `leadr.auth.domain.device.DeviceStatus.ACTIVE`

```python
ACTIVE = 'active'
```

####### `leadr.auth.domain.device.DeviceStatus.BANNED`

```python
BANNED = 'banned'
```

####### `leadr.auth.domain.device.DeviceStatus.SUSPENDED`

```python
SUSPENDED = 'suspended'
```

##### `leadr.auth.domain.identity`

Identity domain models for player identification.

**Classes:**

- [**Identity**](./auth.md#leadr.auth.domain.identity.Identity) – Identity domain entity.
- [**IdentityKind**](./auth.md#leadr.auth.domain.identity.IdentityKind) – Identity provider type enumeration.
- [**IdentitySession**](./auth.md#leadr.auth.domain.identity.IdentitySession) – Identity session domain entity.

###### `leadr.auth.domain.identity.Identity`

Bases: <code>[Entity](./common.md#leadr.common.domain.models.Entity)</code>

Identity domain entity.

Represents a player identity within a game. Identities are the ranking key
for leaderboards, decoupling player identity from specific authentication
mechanisms (devices, Steam accounts, etc.).

Each identity is scoped to an account and game, and is uniquely identified
by the combination of kind and external_key.

**Functions:**

- [**restore**](./auth.md#leadr.auth.domain.identity.Identity.restore) – Restore a soft-deleted entity.
- [**soft_delete**](#leadr.auth.domain.identity.Identity.soft_delete) – Mark entity as soft-deleted.
- [**update_display_name**](#leadr.auth.domain.identity.Identity.update_display_name) – Update the display name.

**Attributes:**

- [**account_id**](#leadr.auth.domain.identity.Identity.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**created_at**](#leadr.auth.domain.identity.Identity.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**deleted_at**](#leadr.auth.domain.identity.Identity.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**display_name**](#leadr.auth.domain.identity.Identity.display_name) (<code>[str](#str) | None</code>) –
- [**external_key**](#leadr.auth.domain.identity.Identity.external_key) (<code>[str](#str)</code>) –
- [**game_id**](#leadr.auth.domain.identity.Identity.game_id) (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) –
- [**id**](./auth.md#leadr.auth.domain.identity.Identity.id) (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) –
- [**is_deleted**](#leadr.auth.domain.identity.Identity.is_deleted) (<code>[bool](#bool)</code>) – Check if entity is soft-deleted.
- [**kind**](./auth.md#leadr.auth.domain.identity.Identity.kind) (<code>[IdentityKind](./auth.md#leadr.auth.domain.identity.IdentityKind)</code>) –
- [**model_config**](#leadr.auth.domain.identity.Identity.model_config) –
- [**updated_at**](#leadr.auth.domain.identity.Identity.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.auth.domain.identity.Identity.account_id`

```python
account_id: AccountID = Field(frozen=True, description='Account this identity belongs to')
```

####### `leadr.auth.domain.identity.Identity.created_at`

```python
created_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp when entity was created (UTC)')
```

####### `leadr.auth.domain.identity.Identity.deleted_at`

```python
deleted_at: datetime | None = Field(default=None, description='Timestamp when entity was soft-deleted (UTC), or null if active')
```

####### `leadr.auth.domain.identity.Identity.display_name`

```python
display_name: str | None = Field(default=None, description='Player display name')
```

####### `leadr.auth.domain.identity.Identity.external_key`

```python
external_key: str = Field(description='External identifier (e.g., device ID, Steam ID, custom user ID)')
```

####### `leadr.auth.domain.identity.Identity.game_id`

```python
game_id: GameID = Field(frozen=True, description='Game this identity belongs to')
```

####### `leadr.auth.domain.identity.Identity.id`

```python
id: IdentityID = Field(frozen=True, default_factory=IdentityID, description='Unique identity identifier')
```

####### `leadr.auth.domain.identity.Identity.is_deleted`

```python
is_deleted: bool
```

Check if entity is soft-deleted.

**Returns:**

- <code>[bool](#bool)</code> – True if the entity has a deleted_at timestamp, False otherwise.

####### `leadr.auth.domain.identity.Identity.kind`

```python
kind: IdentityKind = Field(description='Type of identity provider')
```

####### `leadr.auth.domain.identity.Identity.model_config`

```python
model_config = ConfigDict(validate_assignment=True)
```

####### `leadr.auth.domain.identity.Identity.restore`

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

####### `leadr.auth.domain.identity.Identity.soft_delete`

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

####### `leadr.auth.domain.identity.Identity.update_display_name`

```python
update_display_name(name)
```

Update the display name.

**Parameters:**

- **name** (<code>[str](#str) | None</code>) – New display name, or None to clear.

####### `leadr.auth.domain.identity.Identity.updated_at`

```python
updated_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp of last update (UTC)')
```

###### `leadr.auth.domain.identity.IdentityKind`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Identity provider type enumeration.

**Attributes:**

- [**CUSTOM**](./auth.md#leadr.auth.domain.identity.IdentityKind.CUSTOM) –
- [**DEVICE**](./auth.md#leadr.auth.domain.identity.IdentityKind.DEVICE) –
- [**STEAM**](./auth.md#leadr.auth.domain.identity.IdentityKind.STEAM) –

####### `leadr.auth.domain.identity.IdentityKind.CUSTOM`

```python
CUSTOM = 'CUSTOM'
```

####### `leadr.auth.domain.identity.IdentityKind.DEVICE`

```python
DEVICE = 'DEVICE'
```

####### `leadr.auth.domain.identity.IdentityKind.STEAM`

```python
STEAM = 'STEAM'
```

###### `leadr.auth.domain.identity.IdentitySession`

Bases: <code>[Entity](./common.md#leadr.common.domain.models.Entity)</code>

Identity session domain entity.

Represents an active authentication session for an identity.
Sessions have an expiration time and can be revoked manually.
Includes both access and refresh tokens with token rotation support.

Replaces DeviceSession with identity-based authentication.

**Functions:**

- [**is_expired**](#leadr.auth.domain.identity.IdentitySession.is_expired) – Check if the access token has expired.
- [**is_refresh_expired**](#leadr.auth.domain.identity.IdentitySession.is_refresh_expired) – Check if the refresh token has expired.
- [**is_revoked**](#leadr.auth.domain.identity.IdentitySession.is_revoked) – Check if the session has been manually revoked.
- [**is_valid**](#leadr.auth.domain.identity.IdentitySession.is_valid) – Check if the session is valid for use.
- [**restore**](./auth.md#leadr.auth.domain.identity.IdentitySession.restore) – Restore a soft-deleted entity.
- [**revoke**](./auth.md#leadr.auth.domain.identity.IdentitySession.revoke) – Revoke the session, preventing further use.
- [**rotate_tokens**](#leadr.auth.domain.identity.IdentitySession.rotate_tokens) – Increment token version for token rotation.
- [**soft_delete**](#leadr.auth.domain.identity.IdentitySession.soft_delete) – Mark entity as soft-deleted.

**Attributes:**

- [**access_token_hash**](#leadr.auth.domain.identity.IdentitySession.access_token_hash) (<code>[str](#str)</code>) –
- [**created_at**](#leadr.auth.domain.identity.IdentitySession.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**deleted_at**](#leadr.auth.domain.identity.IdentitySession.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**expires_at**](#leadr.auth.domain.identity.IdentitySession.expires_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**id**](./auth.md#leadr.auth.domain.identity.IdentitySession.id) (<code>[IdentitySessionID](./common.md#leadr.common.domain.ids.IdentitySessionID)</code>) –
- [**identity_id**](#leadr.auth.domain.identity.IdentitySession.identity_id) (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) –
- [**is_deleted**](#leadr.auth.domain.identity.IdentitySession.is_deleted) (<code>[bool](#bool)</code>) – Check if entity is soft-deleted.
- [**model_config**](#leadr.auth.domain.identity.IdentitySession.model_config) –
- [**refresh_expires_at**](#leadr.auth.domain.identity.IdentitySession.refresh_expires_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**refresh_token_hash**](#leadr.auth.domain.identity.IdentitySession.refresh_token_hash) (<code>[str](#str)</code>) –
- [**revoked_at**](#leadr.auth.domain.identity.IdentitySession.revoked_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**token_version**](#leadr.auth.domain.identity.IdentitySession.token_version) (<code>[int](#int)</code>) –
- [**updated_at**](#leadr.auth.domain.identity.IdentitySession.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.auth.domain.identity.IdentitySession.access_token_hash`

```python
access_token_hash: str
```

####### `leadr.auth.domain.identity.IdentitySession.created_at`

```python
created_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp when entity was created (UTC)')
```

####### `leadr.auth.domain.identity.IdentitySession.deleted_at`

```python
deleted_at: datetime | None = Field(default=None, description='Timestamp when entity was soft-deleted (UTC), or null if active')
```

####### `leadr.auth.domain.identity.IdentitySession.expires_at`

```python
expires_at: datetime
```

####### `leadr.auth.domain.identity.IdentitySession.id`

```python
id: IdentitySessionID = Field(frozen=True, default_factory=IdentitySessionID, description='Unique identity session identifier')
```

####### `leadr.auth.domain.identity.IdentitySession.identity_id`

```python
identity_id: IdentityID = Field(frozen=True, description='Identity this session belongs to')
```

####### `leadr.auth.domain.identity.IdentitySession.is_deleted`

```python
is_deleted: bool
```

Check if entity is soft-deleted.

**Returns:**

- <code>[bool](#bool)</code> – True if the entity has a deleted_at timestamp, False otherwise.

####### `leadr.auth.domain.identity.IdentitySession.is_expired`

```python
is_expired()
```

Check if the access token has expired.

**Returns:**

- <code>[bool](#bool)</code> – True if the current time is past the expiration time.

####### `leadr.auth.domain.identity.IdentitySession.is_refresh_expired`

```python
is_refresh_expired()
```

Check if the refresh token has expired.

**Returns:**

- <code>[bool](#bool)</code> – True if the current time is past the refresh expiration time.

####### `leadr.auth.domain.identity.IdentitySession.is_revoked`

```python
is_revoked()
```

Check if the session has been manually revoked.

**Returns:**

- <code>[bool](#bool)</code> – True if revoked_at is set.

####### `leadr.auth.domain.identity.IdentitySession.is_valid`

```python
is_valid()
```

Check if the session is valid for use.

A session is valid if it's not expired and not revoked.

**Returns:**

- <code>[bool](#bool)</code> – True if the session can be used for authentication.

####### `leadr.auth.domain.identity.IdentitySession.model_config`

```python
model_config = ConfigDict(validate_assignment=True)
```

####### `leadr.auth.domain.identity.IdentitySession.refresh_expires_at`

```python
refresh_expires_at: datetime
```

####### `leadr.auth.domain.identity.IdentitySession.refresh_token_hash`

```python
refresh_token_hash: str
```

####### `leadr.auth.domain.identity.IdentitySession.restore`

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

####### `leadr.auth.domain.identity.IdentitySession.revoke`

```python
revoke()
```

Revoke the session, preventing further use.

####### `leadr.auth.domain.identity.IdentitySession.revoked_at`

```python
revoked_at: datetime | None = None
```

####### `leadr.auth.domain.identity.IdentitySession.rotate_tokens`

```python
rotate_tokens()
```

Increment token version for token rotation.

Called when refreshing tokens to invalidate old refresh tokens.

####### `leadr.auth.domain.identity.IdentitySession.soft_delete`

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

####### `leadr.auth.domain.identity.IdentitySession.token_version`

```python
token_version: int = 1
```

####### `leadr.auth.domain.identity.IdentitySession.updated_at`

```python
updated_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp of last update (UTC)')
```

##### `leadr.auth.domain.nonce`

Nonce domain entity for replay protection.

**Classes:**

- [**Nonce**](./auth.md#leadr.auth.domain.nonce.Nonce) – Request nonce for replay protection.
- [**NonceStatus**](./auth.md#leadr.auth.domain.nonce.NonceStatus) – Nonce status enumeration.

###### `leadr.auth.domain.nonce.Nonce`

Bases: <code>[Entity](./common.md#leadr.common.domain.models.Entity)</code>

Request nonce for replay protection.

Nonces are single-use tokens that clients must obtain before making
mutating requests (POST, PATCH, DELETE). Each nonce has a short TTL
(typically 60 seconds) and can only be used once.

This prevents replay attacks by ensuring that each mutating request
is fresh and authorized by the server.

**Functions:**

- [**is_expired**](#leadr.auth.domain.nonce.Nonce.is_expired) – Check if nonce has expired.
- [**is_used**](#leadr.auth.domain.nonce.Nonce.is_used) – Check if nonce has been used.
- [**is_valid**](#leadr.auth.domain.nonce.Nonce.is_valid) – Check if nonce is valid (not used and not expired).
- [**mark_expired**](#leadr.auth.domain.nonce.Nonce.mark_expired) – Mark nonce as expired.
- [**mark_used**](#leadr.auth.domain.nonce.Nonce.mark_used) – Mark nonce as used.
- [**restore**](./auth.md#leadr.auth.domain.nonce.Nonce.restore) – Restore a soft-deleted entity.
- [**soft_delete**](#leadr.auth.domain.nonce.Nonce.soft_delete) – Mark entity as soft-deleted.

**Attributes:**

- [**created_at**](#leadr.auth.domain.nonce.Nonce.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**deleted_at**](#leadr.auth.domain.nonce.Nonce.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**expires_at**](#leadr.auth.domain.nonce.Nonce.expires_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**id**](./auth.md#leadr.auth.domain.nonce.Nonce.id) (<code>[NonceID](./common.md#leadr.common.domain.ids.NonceID)</code>) –
- [**identity_id**](#leadr.auth.domain.nonce.Nonce.identity_id) (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) –
- [**is_deleted**](#leadr.auth.domain.nonce.Nonce.is_deleted) (<code>[bool](#bool)</code>) – Check if entity is soft-deleted.
- [**model_config**](#leadr.auth.domain.nonce.Nonce.model_config) –
- [**nonce_value**](#leadr.auth.domain.nonce.Nonce.nonce_value) (<code>[str](#str)</code>) –
- [**status**](./auth.md#leadr.auth.domain.nonce.Nonce.status) (<code>[NonceStatus](./auth.md#leadr.auth.domain.nonce.NonceStatus)</code>) –
- [**updated_at**](#leadr.auth.domain.nonce.Nonce.updated_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**used_at**](#leadr.auth.domain.nonce.Nonce.used_at) (<code>[datetime](#datetime.datetime) | None</code>) –

####### `leadr.auth.domain.nonce.Nonce.created_at`

```python
created_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp when entity was created (UTC)')
```

####### `leadr.auth.domain.nonce.Nonce.deleted_at`

```python
deleted_at: datetime | None = Field(default=None, description='Timestamp when entity was soft-deleted (UTC), or null if active')
```

####### `leadr.auth.domain.nonce.Nonce.expires_at`

```python
expires_at: datetime = Field(description='Nonce expiration timestamp')
```

####### `leadr.auth.domain.nonce.Nonce.id`

```python
id: NonceID = Field(frozen=True, default_factory=NonceID, description='Unique nonce identifier')
```

####### `leadr.auth.domain.nonce.Nonce.identity_id`

```python
identity_id: IdentityID = Field(description='Identity that owns this nonce')
```

####### `leadr.auth.domain.nonce.Nonce.is_deleted`

```python
is_deleted: bool
```

Check if entity is soft-deleted.

**Returns:**

- <code>[bool](#bool)</code> – True if the entity has a deleted_at timestamp, False otherwise.

####### `leadr.auth.domain.nonce.Nonce.is_expired`

```python
is_expired()
```

Check if nonce has expired.

**Returns:**

- <code>[bool](#bool)</code> – True if current time is at or past expires_at

####### `leadr.auth.domain.nonce.Nonce.is_used`

```python
is_used()
```

Check if nonce has been used.

**Returns:**

- <code>[bool](#bool)</code> – True if status is USED

####### `leadr.auth.domain.nonce.Nonce.is_valid`

```python
is_valid()
```

Check if nonce is valid (not used and not expired).

**Returns:**

- <code>[bool](#bool)</code> – True if nonce is pending and not expired

####### `leadr.auth.domain.nonce.Nonce.mark_expired`

```python
mark_expired()
```

Mark nonce as expired.

Only marks nonce as expired if it's currently pending.
Does not change status if already used or expired.

####### `leadr.auth.domain.nonce.Nonce.mark_used`

```python
mark_used()
```

Mark nonce as used.

Sets status to USED and records used_at timestamp.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If nonce is not valid (already used or expired)

####### `leadr.auth.domain.nonce.Nonce.model_config`

```python
model_config = ConfigDict(validate_assignment=True)
```

####### `leadr.auth.domain.nonce.Nonce.nonce_value`

```python
nonce_value: str = Field(description='Unique nonce value (UUID string)')
```

####### `leadr.auth.domain.nonce.Nonce.restore`

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

####### `leadr.auth.domain.nonce.Nonce.soft_delete`

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

####### `leadr.auth.domain.nonce.Nonce.status`

```python
status: NonceStatus = Field(default=(NonceStatus.PENDING), description='Nonce status')
```

####### `leadr.auth.domain.nonce.Nonce.updated_at`

```python
updated_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp of last update (UTC)')
```

####### `leadr.auth.domain.nonce.Nonce.used_at`

```python
used_at: datetime | None = Field(default=None, description='When nonce was consumed')
```

###### `leadr.auth.domain.nonce.NonceStatus`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Nonce status enumeration.

**Attributes:**

- [**EXPIRED**](./auth.md#leadr.auth.domain.nonce.NonceStatus.EXPIRED) –
- [**PENDING**](./auth.md#leadr.auth.domain.nonce.NonceStatus.PENDING) –
- [**USED**](./auth.md#leadr.auth.domain.nonce.NonceStatus.USED) –

####### `leadr.auth.domain.nonce.NonceStatus.EXPIRED`

```python
EXPIRED = 'expired'
```

####### `leadr.auth.domain.nonce.NonceStatus.PENDING`

```python
PENDING = 'pending'
```

####### `leadr.auth.domain.nonce.NonceStatus.USED`

```python
USED = 'used'
```

#### `leadr.auth.services`

**Modules:**

- [**api_key_crypto**](#leadr.auth.services.api_key_crypto) – Cryptographic operations for API keys.
- [**api_key_service**](#leadr.auth.services.api_key_service) – API Key service for managing API key operations.
- [**dependencies**](./auth.md#leadr.auth.services.dependencies) – Auth service dependency injection factories.
- [**device_service**](#leadr.auth.services.device_service) – Device authentication service.
- [**device_token_crypto**](#leadr.auth.services.device_token_crypto) – Cryptographic operations for device access and refresh tokens.
- [**identity_service**](#leadr.auth.services.identity_service) – Identity service for player identity management.
- [**nonce_service**](#leadr.auth.services.nonce_service) – Nonce service for managing request nonces.
- [**nonce_tasks**](#leadr.auth.services.nonce_tasks) – Background tasks for nonce cleanup.
- [**repositories**](./auth.md#leadr.auth.services.repositories) – API Key, Device, Identity, and Nonce repository services.

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
- [**create_api_key**](#leadr.auth.services.api_key_service.APIKeyService.create_api_key) – Create a new API key for a user within an account.
- [**create_api_key_with_value**](#leadr.auth.services.api_key_service.APIKeyService.create_api_key_with_value) – Create a new API key with a specific key value (for bootstrap/testing).
- [**delete**](#leadr.auth.services.api_key_service.APIKeyService.delete) – Soft-delete an entity.
- [**get_api_key**](#leadr.auth.services.api_key_service.APIKeyService.get_api_key) – Get an API key by its ID.
- [**get_by_id**](#leadr.auth.services.api_key_service.APIKeyService.get_by_id) – Get an entity by its ID.
- [**get_by_id_or_raise**](#leadr.auth.services.api_key_service.APIKeyService.get_by_id_or_raise) – Get an entity by its ID or raise EntityNotFoundError.
- [**list_account_api_keys**](#leadr.auth.services.api_key_service.APIKeyService.list_account_api_keys) – List all API keys for an account.
- [**list_all**](#leadr.auth.services.api_key_service.APIKeyService.list_all) – List all non-deleted entities.
- [**list_api_keys**](#leadr.auth.services.api_key_service.APIKeyService.list_api_keys) – List API keys for an account with optional filters and pagination.
- [**record_usage**](#leadr.auth.services.api_key_service.APIKeyService.record_usage) – Record that an API key was used at a specific time.
- [**record_usage_async**](#leadr.auth.services.api_key_service.APIKeyService.record_usage_async) – Record API key usage asynchronously (for background tasks).
- [**revoke_api_key**](#leadr.auth.services.api_key_service.APIKeyService.revoke_api_key) – Revoke an API key, preventing further use.
- [**should_update_usage**](#leadr.auth.services.api_key_service.APIKeyService.should_update_usage) – Check if last_used_at needs updating based on configurable threshold.
- [**soft_delete**](#leadr.auth.services.api_key_service.APIKeyService.soft_delete) – Soft-delete an entity and return it before deletion.
- [**update_api_key_status**](#leadr.auth.services.api_key_service.APIKeyService.update_api_key_status) – Update the status of an API key.
- [**validate_api_key**](#leadr.auth.services.api_key_service.APIKeyService.validate_api_key) – Validate an API key and return the domain entity if valid.
- [**validate_api_key_with_user**](#leadr.auth.services.api_key_service.APIKeyService.validate_api_key_with_user) – Validate an API key and return both the key and associated user.

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

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – The account ID to count keys for.

**Returns:**

- <code>[int](#int)</code> – Number of active (non-revoked) API keys.

####### `leadr.auth.services.api_key_service.APIKeyService.create_api_key`

```python
create_api_key(account_id, user_id, name, expires_at=None)
```

Create a new API key for a user within an account.

Generates a secure random key, hashes it for storage, and persists
it to the database. The plain key is returned only once for the
caller to provide to the user.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – The account ID the key belongs to.
- **user_id** (<code>[UserID](./common.md#leadr.common.domain.ids.UserID)</code>) – The user ID the key belongs to.
- **name** (<code>[str](#str)</code>) – A descriptive name for the key.
- **expires_at** (<code>[datetime](#datetime.datetime) | None</code>) – Optional expiration timestamp for the key.

**Returns:**

- <code>[APIKey](#leadr.auth.domain.api_key.APIKey)</code> – A tuple of (APIKey domain entity, plain key string).
- <code>[str](#str)</code> – The plain key should be shown to the user once and not stored.

<details class="example" open markdown="1">
<summary>Example</summary>

> > > api_key, plain_key = await service.create_api_key(
> > > ... account_id=account_id,
> > > ... user_id=user_id,
> > > ... name="Production API Key",
> > > ... expires_at=datetime.now(UTC) + timedelta(days=90)
> > > ... )
> > > print(f"Your API key: {plain_key}")
> > > Your API key: ldr_abc123...

</details>

####### `leadr.auth.services.api_key_service.APIKeyService.create_api_key_with_value`

```python
create_api_key_with_value(account_id, user_id, name, key_value, expires_at=None)
```

Create a new API key with a specific key value (for bootstrap/testing).

This method is used for creating API keys with predetermined values,
such as during superadmin bootstrap. Unlike create_api_key, this does
not generate a random key and only returns the APIKey entity.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – The account ID the key belongs to.
- **user_id** (<code>[UserID](./common.md#leadr.common.domain.ids.UserID)</code>) – The user ID the key belongs to.
- **name** (<code>[str](#str)</code>) – A descriptive name for the key.
- **key_value** (<code>[str](#str)</code>) – The specific API key value to use.
- **expires_at** (<code>[datetime](#datetime.datetime) | None</code>) – Optional expiration timestamp for the key.

**Returns:**

- <code>[APIKey](#leadr.auth.domain.api_key.APIKey)</code> – The created APIKey domain entity.

<details class="example" open markdown="1">
<summary>Example</summary>

> > > api_key = await service.create_api_key_with_value(
> > > ... account_id=account_id,
> > > ... user_id=user_id,
> > > ... name="Superadmin Key",
> > > ... key_value="ldr_fixed_key_for_bootstrap",
> > > ... )

</details>

####### `leadr.auth.services.api_key_service.APIKeyService.delete`

```python
delete(entity_id)
```

Soft-delete an entity.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – The ID of the entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the entity doesn't exist

####### `leadr.auth.services.api_key_service.APIKeyService.get_api_key`

```python
get_api_key(key_id)
```

Get an API key by its ID.

**Parameters:**

- **key_id** (<code>[APIKeyID](./common.md#leadr.common.domain.ids.APIKeyID)</code>) – The ID of the API key to retrieve.

**Returns:**

- <code>[APIKey](#leadr.auth.domain.api_key.APIKey) | None</code> – The APIKey domain entity if found, None otherwise.

####### `leadr.auth.services.api_key_service.APIKeyService.get_by_id`

```python
get_by_id(entity_id)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – The ID of the entity to retrieve

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.services.DomainEntityT) | None</code> – The domain entity if found, None otherwise

####### `leadr.auth.services.api_key_service.APIKeyService.get_by_id_or_raise`

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

####### `leadr.auth.services.api_key_service.APIKeyService.list_account_api_keys`

```python
list_account_api_keys(account_id, active_only=False)
```

List all API keys for an account.

This is an internal helper that returns a plain list. API keys per account
are typically limited, so pagination isn't needed for internal use cases.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – The account ID to list keys for.
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
list_api_keys(account_id, *, status=None, pagination)
```

List API keys for an account with optional filters and pagination.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – Account ID to filter by. If None, returns all API keys
  (superadmin use case).
- **status** (<code>[str](#str) | None</code>) – Optional status string to filter by.
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (required).

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[APIKey](#leadr.auth.domain.api_key.APIKey)\]</code> – PaginatedResult containing APIKey entities.

####### `leadr.auth.services.api_key_service.APIKeyService.record_usage`

```python
record_usage(key_id, used_at)
```

Record that an API key was used at a specific time.

This is typically called automatically during validation, but can
also be called explicitly if needed.

**Parameters:**

- **key_id** (<code>[APIKeyID](./common.md#leadr.common.domain.ids.APIKeyID)</code>) – The ID of the API key that was used.
- **used_at** (<code>[datetime](#datetime.datetime)</code>) – The timestamp when the key was used.

**Returns:**

- <code>[APIKey](#leadr.auth.domain.api_key.APIKey)</code> – The updated APIKey domain entity.

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the key doesn't exist.

####### `leadr.auth.services.api_key_service.APIKeyService.record_usage_async`

```python
record_usage_async(key_id)
```

Record API key usage asynchronously (for background tasks).

This method is designed to be called as a background task. It silently
handles missing keys to avoid errors in background processing.

**Parameters:**

- **key_id** (<code>[APIKeyID](./common.md#leadr.common.domain.ids.APIKeyID)</code>) – The ID of the API key that was used.

####### `leadr.auth.services.api_key_service.APIKeyService.repository`

```python
repository = repository if repository is not None else self._create_repository(session)
```

####### `leadr.auth.services.api_key_service.APIKeyService.revoke_api_key`

```python
revoke_api_key(key_id)
```

Revoke an API key, preventing further use.

**Parameters:**

- **key_id** (<code>[APIKeyID](./common.md#leadr.common.domain.ids.APIKeyID)</code>) – The ID of the API key to revoke.

**Returns:**

- <code>[APIKey](#leadr.auth.domain.api_key.APIKey)</code> – The updated APIKey domain entity with REVOKED status.

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the key doesn't exist.

####### `leadr.auth.services.api_key_service.APIKeyService.should_update_usage`

```python
should_update_usage(api_key)
```

Check if last_used_at needs updating based on configurable threshold.

Returns True if:

- last_used_at is None (never used before), or
- last_used_at is older than API_KEY_USAGE_UPDATE_THRESHOLD_SECONDS

**Parameters:**

- **api_key** (<code>[APIKey](#leadr.auth.domain.api_key.APIKey)</code>) – The API key to check.

**Returns:**

- <code>[bool](#bool)</code> – True if usage should be updated, False otherwise.

####### `leadr.auth.services.api_key_service.APIKeyService.soft_delete`

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

####### `leadr.auth.services.api_key_service.APIKeyService.update_api_key_status`

```python
update_api_key_status(key_id, status)
```

Update the status of an API key.

**Parameters:**

- **key_id** (<code>[APIKeyID](./common.md#leadr.common.domain.ids.APIKeyID)</code>) – The ID of the API key to update.
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

Note: This method does NOT update last_used_at. The caller should check
should_update_usage() and schedule record_usage_async() via background task
if needed.

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

####### `leadr.auth.services.api_key_service.APIKeyService.validate_api_key_with_user`

```python
validate_api_key_with_user(plain_key)
```

Validate an API key and return both the key and associated user.

This method performs a single JOIN query to retrieve both the API key
and user in one database round-trip, reducing auth latency.

Performs the following checks:

1. Extracts prefix and looks up key + user in database via JOIN
1. Verifies the hash matches
1. Checks if key is active (not revoked)
1. Checks if key is not expired

Note: This method does NOT update last_used_at. The caller should check
should_update_usage() and schedule record_usage_async() via background task
if needed.

**Parameters:**

- **plain_key** (<code>[str](#str)</code>) – The plain API key string to validate.

**Returns:**

- <code>[tuple](#tuple)\[[APIKey](#leadr.auth.domain.api_key.APIKey), [User](./accounts.md#leadr.accounts.domain.user.User)\] | None</code> – A tuple of (APIKey, User) if valid, None otherwise.

<details class="example" open markdown="1">
<summary>Example</summary>

> > > result = await service.validate_api_key_with_user("ldr_abc123...")
> > > if result:
> > > ... api_key, user = result
> > > ... print(f"Valid key for user {user.email}")
> > > ... else:
> > > ... print("Invalid or expired key")

</details>

##### `leadr.auth.services.dependencies`

Auth service dependency injection factories.

**Functions:**

- [**get_api_key_service**](#leadr.auth.services.dependencies.get_api_key_service) – Get APIKeyService dependency.
- [**get_device_service**](#leadr.auth.services.dependencies.get_device_service) – Get DeviceService dependency.
- [**get_identity_service**](#leadr.auth.services.dependencies.get_identity_service) – Get IdentityService dependency with DeviceService injected.
- [**get_nonce_service**](#leadr.auth.services.dependencies.get_nonce_service) – Get NonceService dependency.

**Attributes:**

- [**APIKeyServiceDep**](./auth.md#leadr.auth.services.dependencies.APIKeyServiceDep) –
- [**DeviceServiceDep**](./auth.md#leadr.auth.services.dependencies.DeviceServiceDep) –
- [**IdentityServiceDep**](./auth.md#leadr.auth.services.dependencies.IdentityServiceDep) –
- [**NonceServiceDep**](./auth.md#leadr.auth.services.dependencies.NonceServiceDep) –

###### `leadr.auth.services.dependencies.APIKeyServiceDep`

```python
APIKeyServiceDep = Annotated[APIKeyService, Depends(get_api_key_service)]
```

###### `leadr.auth.services.dependencies.DeviceServiceDep`

```python
DeviceServiceDep = Annotated[DeviceService, Depends(get_device_service)]
```

###### `leadr.auth.services.dependencies.IdentityServiceDep`

```python
IdentityServiceDep = Annotated[IdentityService, Depends(get_identity_service)]
```

###### `leadr.auth.services.dependencies.NonceServiceDep`

```python
NonceServiceDep = Annotated[NonceService, Depends(get_nonce_service)]
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

###### `leadr.auth.services.dependencies.get_device_service`

```python
get_device_service(db)
```

Get DeviceService dependency.

**Parameters:**

- **db** (<code>[DatabaseSession](./common.md#leadr.common.dependencies.DatabaseSession)</code>) – Database session injected via dependency injection

**Returns:**

- <code>[DeviceService](#leadr.auth.services.device_service.DeviceService)</code> – DeviceService instance configured with the database session

###### `leadr.auth.services.dependencies.get_identity_service`

```python
get_identity_service(db, device_service=Depends(get_device_service))
```

Get IdentityService dependency with DeviceService injected.

**Parameters:**

- **db** (<code>[DatabaseSession](./common.md#leadr.common.dependencies.DatabaseSession)</code>) – Database session injected via dependency injection
- **device_service** (<code>[DeviceService](#leadr.auth.services.device_service.DeviceService)</code>) – DeviceService injected via dependency injection

**Returns:**

- <code>[IdentityService](#leadr.auth.services.identity_service.IdentityService)</code> – IdentityService instance configured with the database session and device service

###### `leadr.auth.services.dependencies.get_nonce_service`

```python
get_nonce_service(db)
```

Get NonceService dependency.

**Parameters:**

- **db** (<code>[DatabaseSession](./common.md#leadr.common.dependencies.DatabaseSession)</code>) – Database session injected via dependency injection

**Returns:**

- <code>[NonceService](#leadr.auth.services.nonce_service.NonceService)</code> – NonceService instance configured with the database session

##### `leadr.auth.services.device_service`

Device authentication service.

**Classes:**

- [**DeviceService**](#leadr.auth.services.device_service.DeviceService) – Service for device management.

###### `leadr.auth.services.device_service.DeviceService`

```python
DeviceService(session)
```

Bases: <code>[BaseService](./common.md#leadr.common.services.BaseService)\[[Device](./auth.md#leadr.auth.domain.device.Device), [DeviceRepository](./auth.md#leadr.auth.services.repositories.DeviceRepository)\]</code>

Service for device management.

Devices are internal lookup tables that map client fingerprints to games/accounts.
For session management, use IdentityService instead.

**Functions:**

- [**activate_device**](#leadr.auth.services.device_service.DeviceService.activate_device) – Activate a device, allowing authentication.
- [**ban_device**](#leadr.auth.services.device_service.DeviceService.ban_device) – Ban a device, preventing further authentication.
- [**delete**](#leadr.auth.services.device_service.DeviceService.delete) – Soft-delete an entity.
- [**get_by_id**](#leadr.auth.services.device_service.DeviceService.get_by_id) – Get an entity by its ID.
- [**get_by_id_or_raise**](#leadr.auth.services.device_service.DeviceService.get_by_id_or_raise) – Get an entity by its ID or raise EntityNotFoundError.
- [**get_device**](#leadr.auth.services.device_service.DeviceService.get_device) – Get a device by its ID.
- [**get_or_create_device**](#leadr.auth.services.device_service.DeviceService.get_or_create_device) – Get or create a device record.
- [**list_all**](#leadr.auth.services.device_service.DeviceService.list_all) – List all non-deleted entities.
- [**list_devices**](#leadr.auth.services.device_service.DeviceService.list_devices) – List devices for an account with optional filters and pagination.
- [**soft_delete**](#leadr.auth.services.device_service.DeviceService.soft_delete) – Soft-delete an entity and return it before deletion.
- [**suspend_device**](#leadr.auth.services.device_service.DeviceService.suspend_device) – Suspend a device temporarily.

**Attributes:**

- [**repository**](#leadr.auth.services.device_service.DeviceService.repository) –
- [**session**](#leadr.auth.services.device_service.DeviceService.session) –

**Parameters:**

- **session** (<code>[AsyncSession](#sqlalchemy.ext.asyncio.AsyncSession)</code>) – SQLAlchemy async session

####### `leadr.auth.services.device_service.DeviceService.activate_device`

```python
activate_device(device_id)
```

Activate a device, allowing authentication.

**Parameters:**

- **device_id** (<code>[DeviceID](./common.md#leadr.common.domain.ids.DeviceID)</code>) – The ID of the device to activate

**Returns:**

- <code>[Device](./auth.md#leadr.auth.domain.device.Device)</code> – The updated device

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the device doesn't exist

<details class="example" open markdown="1">
<summary>Example</summary>

> > > device = await service.activate_device(device_id)

</details>

####### `leadr.auth.services.device_service.DeviceService.ban_device`

```python
ban_device(device_id)
```

Ban a device, preventing further authentication.

**Parameters:**

- **device_id** (<code>[DeviceID](./common.md#leadr.common.domain.ids.DeviceID)</code>) – The ID of the device to ban

**Returns:**

- <code>[Device](./auth.md#leadr.auth.domain.device.Device)</code> – The updated device

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the device doesn't exist

<details class="example" open markdown="1">
<summary>Example</summary>

> > > device = await service.ban_device(device_id)

</details>

####### `leadr.auth.services.device_service.DeviceService.delete`

```python
delete(entity_id)
```

Soft-delete an entity.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – The ID of the entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the entity doesn't exist

####### `leadr.auth.services.device_service.DeviceService.get_by_id`

```python
get_by_id(entity_id)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – The ID of the entity to retrieve

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.services.DomainEntityT) | None</code> – The domain entity if found, None otherwise

####### `leadr.auth.services.device_service.DeviceService.get_by_id_or_raise`

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

####### `leadr.auth.services.device_service.DeviceService.get_device`

```python
get_device(device_id)
```

Get a device by its ID.

**Parameters:**

- **device_id** (<code>[UUID](#uuid.UUID)</code>) – The ID of the device to retrieve

**Returns:**

- <code>[Device](./auth.md#leadr.auth.domain.device.Device) | None</code> – The device if found, None otherwise

<details class="example" open markdown="1">
<summary>Example</summary>

> > > device = await service.get_device(device_id)

</details>

####### `leadr.auth.services.device_service.DeviceService.get_or_create_device`

```python
get_or_create_device(game_id, client_fingerprint, platform=None, metadata=None)
```

Get or create a device record.

This is used as an internal lookup table to map fingerprints to games/accounts.
Does NOT create sessions - use IdentityService.start_session() for that.

**Parameters:**

- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) – Game UUID
- **client_fingerprint** (<code>[str](#str)</code>) – Client-generated SHA256 device fingerprint
- **platform** (<code>[str](#str) | None</code>) – Device platform (ios, android, etc.)
- **metadata** (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\] | None</code>) – Additional device metadata

**Returns:**

- **Device** (<code>[Device](./auth.md#leadr.auth.domain.device.Device)</code>) – The device record (new or existing)

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If game doesn't exist

####### `leadr.auth.services.device_service.DeviceService.list_all`

```python
list_all()
```

List all non-deleted entities.

**Returns:**

- <code>[list](#list)\[[DomainEntityT](./common.md#leadr.common.services.DomainEntityT)\]</code> – List of domain entities

####### `leadr.auth.services.device_service.DeviceService.list_devices`

```python
list_devices(account_id, *, game_id=None, status=None, pagination)
```

List devices for an account with optional filters and pagination.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – Account ID to filter by. If None, returns all devices
  (superadmin use case).
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID) | None</code>) – Optional game ID to filter by
- **status** (<code>[str](#str) | None</code>) – Optional status to filter by (active, banned, suspended)
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (required).

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[Device](./auth.md#leadr.auth.domain.device.Device)\]</code> – PaginatedResult containing Device entities.

<details class="example" open markdown="1">
<summary>Example</summary>

> > > devices = await service.list_devices(
> > > ... account_id=account.id,
> > > ... status="active",
> > > ... pagination=pagination,
> > > ... )

</details>

####### `leadr.auth.services.device_service.DeviceService.repository`

```python
repository = repository if repository is not None else self._create_repository(session)
```

####### `leadr.auth.services.device_service.DeviceService.session`

```python
session = session
```

####### `leadr.auth.services.device_service.DeviceService.soft_delete`

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

####### `leadr.auth.services.device_service.DeviceService.suspend_device`

```python
suspend_device(device_id)
```

Suspend a device temporarily.

**Parameters:**

- **device_id** (<code>[DeviceID](./common.md#leadr.common.domain.ids.DeviceID)</code>) – The ID of the device to suspend

**Returns:**

- <code>[Device](./auth.md#leadr.auth.domain.device.Device)</code> – The updated device

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the device doesn't exist

<details class="example" open markdown="1">
<summary>Example</summary>

> > > device = await service.suspend_device(device_id)

</details>

##### `leadr.auth.services.device_token_crypto`

Cryptographic operations for device access and refresh tokens.

**Functions:**

- [**generate_access_token**](#leadr.auth.services.device_token_crypto.generate_access_token) – Generate JWT access token for device authentication.
- [**generate_refresh_token**](#leadr.auth.services.device_token_crypto.generate_refresh_token) – Generate JWT refresh token for device authentication.
- [**hash_token**](#leadr.auth.services.device_token_crypto.hash_token) – Hash token for secure storage using HMAC-SHA256.
- [**validate_access_token**](#leadr.auth.services.device_token_crypto.validate_access_token) – Validate and decode JWT access token.
- [**validate_refresh_token**](#leadr.auth.services.device_token_crypto.validate_refresh_token) – Validate and decode JWT refresh token.

###### `leadr.auth.services.device_token_crypto.generate_access_token`

```python
generate_access_token(client_fingerprint, game_id, account_id, expires_delta, secret, test_mode=False, identity_id=None)
```

Generate JWT access token for device authentication.

Creates a JWT with device, game, and account claims, signs it with the secret,
and returns both the plain token and its SHA-256 hash for storage.

**Parameters:**

- **device_id** – Client-generated SHA256 device fingerprint
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) – Game UUID
- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – Account UUID (for multi-tenant isolation)
- **expires_delta** (<code>[timedelta](#datetime.timedelta)</code>) – Time until token expires
- **secret** (<code>[str](#str)</code>) – Server-side secret for JWT signing

**Returns:**

- <code>[tuple](#tuple)\[[str](#str), [str](#str)\]</code> – tuple\[str, str\]: (token_plain, token_hash)
- token_plain: JWT access token to return to client
- token_hash: SHA-256 hash for secure storage

<details class="example" open markdown="1">
<summary>Example</summary>

> > > device_id = "device-123"
> > > game_id = UUID("...")
> > > account_id = UUID("...")
> > > token, token_hash = generate_access_token(
> > > ... device_id, game_id, account_id, timedelta(hours=1), "secret"
> > > ... )
> > > token.count(".")
> > > 2

</details>

###### `leadr.auth.services.device_token_crypto.generate_refresh_token`

```python
generate_refresh_token(client_fingerprint, game_id, account_id, token_version, expires_delta, secret, test_mode=False, identity_id=None)
```

Generate JWT refresh token for device authentication.

Creates a JWT with device, game, account, and version claims, signs it with the secret,
and returns both the plain token and its SHA-256 hash for storage.

The token_version claim enables token rotation: when a refresh token is used,
the version is incremented and old tokens with lower versions are invalidated.

**Parameters:**

- **device_id** – Client-generated SHA256 device fingerprint
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) – Game UUID
- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – Account UUID (for multi-tenant isolation)
- **token_version** (<code>[int](#int)</code>) – Current token version for rotation tracking
- **expires_delta** (<code>[timedelta](#datetime.timedelta)</code>) – Time until token expires (typically 30 days)
- **secret** (<code>[str](#str)</code>) – Server-side secret for JWT signing

**Returns:**

- <code>[tuple](#tuple)\[[str](#str), [str](#str)\]</code> – tuple\[str, str\]: (token_plain, token_hash)
- token_plain: JWT refresh token to return to client
- token_hash: SHA-256 hash for secure storage

<details class="example" open markdown="1">
<summary>Example</summary>

> > > device_id = "device-123"
> > > game_id = UUID("...")
> > > account_id = UUID("...")
> > > token, token_hash = generate_refresh_token(
> > > ... device_id, game_id, account_id, 1, timedelta(days=30), "secret"
> > > ... )
> > > token.count(".")
> > > 2

</details>

###### `leadr.auth.services.device_token_crypto.hash_token`

```python
hash_token(token, secret)
```

Hash token for secure storage using HMAC-SHA256.

Uses HMAC-SHA256 with a server-side secret (pepper) to create
a one-way hash of the token. This provides defense in depth:
database compromise alone isn't enough to use tokens.

**Parameters:**

- **token** (<code>[str](#str)</code>) – The JWT token to hash
- **secret** (<code>[str](#str)</code>) – Server-side secret for additional security

**Returns:**

- <code>[str](#str)</code> – A hexadecimal string representation of the HMAC-SHA256 hash

<details class="example" open markdown="1">
<summary>Example</summary>

> > > secret = "my-secret"
> > > hash1 = hash_token("token123", secret)
> > > hash2 = hash_token("token123", secret)
> > > hash1 == hash2
> > > True
> > > len(hash1)
> > > 64

</details>

###### `leadr.auth.services.device_token_crypto.validate_access_token`

```python
validate_access_token(token, secret)
```

Validate and decode JWT access token.

Verifies the token signature and expiration. Returns decoded claims if valid.

**Parameters:**

- **token** (<code>[str](#str)</code>) – JWT access token to validate
- **secret** (<code>[str](#str)</code>) – Server-side secret for JWT verification

**Returns:**

- <code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\] | None</code> – dict with claims (sub, game_id, account_id, exp, iat, jti) or None if invalid

<details class="example" open markdown="1">
<summary>Example</summary>

> > > token = "eyJ..."
> > > claims = validate_access_token(token, "secret")
> > > claims["sub"] if claims else None
> > > 'device-123'

</details>

###### `leadr.auth.services.device_token_crypto.validate_refresh_token`

```python
validate_refresh_token(token, secret)
```

Validate and decode JWT refresh token.

Verifies the token signature and expiration. Returns decoded claims if valid.

**Parameters:**

- **token** (<code>[str](#str)</code>) – JWT refresh token to validate
- **secret** (<code>[str](#str)</code>) – Server-side secret for JWT verification

**Returns:**

- <code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\] | None</code> – dict with claims (sub, game_id, account_id, token_version, exp, iat, jti) or None if invalid

<details class="example" open markdown="1">
<summary>Example</summary>

> > > token = "eyJ..."
> > > claims = validate_refresh_token(token, "secret")
> > > claims["token_version"] if claims else None
> > > 1

</details>

##### `leadr.auth.services.identity_service`

Identity service for player identity management.

**Classes:**

- [**IdentityService**](#leadr.auth.services.identity_service.IdentityService) – Service for identity management and session handling.

###### `leadr.auth.services.identity_service.IdentityService`

```python
IdentityService(session, device_service)
```

Bases: <code>[BaseService](./common.md#leadr.common.services.BaseService)\[[Identity](./auth.md#leadr.auth.domain.identity.Identity), [IdentityRepository](./auth.md#leadr.auth.services.repositories.IdentityRepository)\]</code>

Service for identity management and session handling.

**Functions:**

- [**delete**](#leadr.auth.services.identity_service.IdentityService.delete) – Soft-delete an entity.
- [**get_by_id**](#leadr.auth.services.identity_service.IdentityService.get_by_id) – Get an entity by its ID.
- [**get_by_id_or_raise**](#leadr.auth.services.identity_service.IdentityService.get_by_id_or_raise) – Get an entity by its ID or raise EntityNotFoundError.
- [**get_identity**](#leadr.auth.services.identity_service.IdentityService.get_identity) – Get an identity by its ID.
- [**get_identity_or_raise**](#leadr.auth.services.identity_service.IdentityService.get_identity_or_raise) – Get an identity by its ID or raise EntityNotFoundError.
- [**get_or_create_identity**](#leadr.auth.services.identity_service.IdentityService.get_or_create_identity) – Get an existing identity or create a new one.
- [**get_session**](#leadr.auth.services.identity_service.IdentityService.get_session) – Get an identity session by its ID.
- [**get_session_or_raise**](#leadr.auth.services.identity_service.IdentityService.get_session_or_raise) – Get an identity session by its ID or raise EntityNotFoundError.
- [**list_all**](#leadr.auth.services.identity_service.IdentityService.list_all) – List all non-deleted entities.
- [**list_identities**](#leadr.auth.services.identity_service.IdentityService.list_identities) – List identities for an account with optional filters and pagination.
- [**list_sessions**](#leadr.auth.services.identity_service.IdentityService.list_sessions) – List identity sessions with optional filters and pagination.
- [**refresh_access_token**](#leadr.auth.services.identity_service.IdentityService.refresh_access_token) – Refresh access token using a valid refresh token.
- [**revoke_session**](#leadr.auth.services.identity_service.IdentityService.revoke_session) – Revoke an identity session.
- [**soft_delete**](#leadr.auth.services.identity_service.IdentityService.soft_delete) – Soft-delete an entity and return it before deletion.
- [**start_session**](#leadr.auth.services.identity_service.IdentityService.start_session) – Start a new identity session.
- [**update_identity**](#leadr.auth.services.identity_service.IdentityService.update_identity) – Update an identity's mutable fields.
- [**validate_identity_token**](#leadr.auth.services.identity_service.IdentityService.validate_identity_token) – Validate access token and return associated identity.

**Attributes:**

- [**repository**](#leadr.auth.services.identity_service.IdentityService.repository) –
- [**session**](#leadr.auth.services.identity_service.IdentityService.session) –
- [**session_repo**](#leadr.auth.services.identity_service.IdentityService.session_repo) –

**Parameters:**

- **session** (<code>[AsyncSession](#sqlalchemy.ext.asyncio.AsyncSession)</code>) – SQLAlchemy async session
- **device_service** (<code>[DeviceService](#leadr.auth.services.device_service.DeviceService)</code>) – DeviceService for device lookup

####### `leadr.auth.services.identity_service.IdentityService.delete`

```python
delete(entity_id)
```

Soft-delete an entity.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – The ID of the entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the entity doesn't exist

####### `leadr.auth.services.identity_service.IdentityService.get_by_id`

```python
get_by_id(entity_id)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – The ID of the entity to retrieve

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.services.DomainEntityT) | None</code> – The domain entity if found, None otherwise

####### `leadr.auth.services.identity_service.IdentityService.get_by_id_or_raise`

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

####### `leadr.auth.services.identity_service.IdentityService.get_identity`

```python
get_identity(identity_id)
```

Get an identity by its ID.

**Parameters:**

- **identity_id** (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID) | [UUID](#uuid.UUID)</code>) – The ID of the identity to retrieve

**Returns:**

- <code>[Identity](./auth.md#leadr.auth.domain.identity.Identity) | None</code> – The identity if found, None otherwise

####### `leadr.auth.services.identity_service.IdentityService.get_identity_or_raise`

```python
get_identity_or_raise(identity_id)
```

Get an identity by its ID or raise EntityNotFoundError.

**Parameters:**

- **identity_id** (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID) | [UUID](#uuid.UUID)</code>) – The ID of the identity to retrieve

**Returns:**

- <code>[Identity](./auth.md#leadr.auth.domain.identity.Identity)</code> – The identity

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the identity doesn't exist

####### `leadr.auth.services.identity_service.IdentityService.get_or_create_identity`

```python
get_or_create_identity(account_id, game_id, kind, external_key, display_name=None)
```

Get an existing identity or create a new one.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – Account ID
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) – Game ID
- **kind** (<code>[IdentityKind](./auth.md#leadr.auth.domain.identity.IdentityKind)</code>) – Identity kind (DEVICE, STEAM, CUSTOM)
- **external_key** (<code>[str](#str)</code>) – External identifier (e.g., device ID, Steam ID)
- **display_name** (<code>[str](#str) | None</code>) – Optional display name

**Returns:**

- <code>[tuple](#tuple)\[[Identity](./auth.md#leadr.auth.domain.identity.Identity), [bool](#bool)\]</code> – tuple\[Identity, bool\]: (identity, created) where created is True if new

####### `leadr.auth.services.identity_service.IdentityService.get_session`

```python
get_session(session_id)
```

Get an identity session by its ID.

**Parameters:**

- **session_id** (<code>[IdentitySessionID](./common.md#leadr.common.domain.ids.IdentitySessionID) | [UUID](#uuid.UUID)</code>) – The ID of the session to retrieve

**Returns:**

- <code>[IdentitySession](./auth.md#leadr.auth.domain.identity.IdentitySession) | None</code> – The session if found, None otherwise

####### `leadr.auth.services.identity_service.IdentityService.get_session_or_raise`

```python
get_session_or_raise(session_id)
```

Get an identity session by its ID or raise EntityNotFoundError.

**Parameters:**

- **session_id** (<code>[IdentitySessionID](./common.md#leadr.common.domain.ids.IdentitySessionID)</code>) – The ID of the session to retrieve

**Returns:**

- <code>[IdentitySession](./auth.md#leadr.auth.domain.identity.IdentitySession)</code> – The session

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the session doesn't exist

####### `leadr.auth.services.identity_service.IdentityService.list_all`

```python
list_all()
```

List all non-deleted entities.

**Returns:**

- <code>[list](#list)\[[DomainEntityT](./common.md#leadr.common.services.DomainEntityT)\]</code> – List of domain entities

####### `leadr.auth.services.identity_service.IdentityService.list_identities`

```python
list_identities(account_id, *, game_id=None, kind=None, pagination)
```

List identities for an account with optional filters and pagination.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – Account ID to filter by. If None, returns all identities
  (superadmin use case).
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID) | None</code>) – Optional game ID to filter by
- **kind** (<code>[IdentityKind](./auth.md#leadr.auth.domain.identity.IdentityKind) | None</code>) – Optional identity kind to filter by
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (required).

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[Identity](./auth.md#leadr.auth.domain.identity.Identity)\]</code> – PaginatedResult containing Identity entities.

####### `leadr.auth.services.identity_service.IdentityService.list_sessions`

```python
list_sessions(account_id, *, identity_id=None, pagination)
```

List identity sessions with optional filters and pagination.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – Account ID to filter by. If None, returns all sessions
  (superadmin use case).
- **identity_id** (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID) | None</code>) – Optional identity ID to filter by
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (required).

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[IdentitySession](./auth.md#leadr.auth.domain.identity.IdentitySession)\]</code> – PaginatedResult containing IdentitySession entities.

####### `leadr.auth.services.identity_service.IdentityService.refresh_access_token`

```python
refresh_access_token(refresh_token)
```

Refresh access token using a valid refresh token.

**Parameters:**

- **refresh_token** (<code>[str](#str)</code>) – JWT refresh token

**Returns:**

- <code>[tuple](#tuple)\[[str](#str), [str](#str), [int](#int)\] | None</code> – tuple\[str, str, int\]: (access_token_plain, refresh_token_plain, expires_in_seconds)
- <code>[tuple](#tuple)\[[str](#str), [str](#str), [int](#int)\] | None</code> – or None if refresh token is invalid

####### `leadr.auth.services.identity_service.IdentityService.repository`

```python
repository = repository if repository is not None else self._create_repository(session)
```

####### `leadr.auth.services.identity_service.IdentityService.revoke_session`

```python
revoke_session(session_id)
```

Revoke an identity session.

**Parameters:**

- **session_id** (<code>[IdentitySessionID](./common.md#leadr.common.domain.ids.IdentitySessionID)</code>) – The ID of the session to revoke

**Returns:**

- <code>[IdentitySession](./auth.md#leadr.auth.domain.identity.IdentitySession)</code> – The updated session

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the session doesn't exist

####### `leadr.auth.services.identity_service.IdentityService.session`

```python
session = session
```

####### `leadr.auth.services.identity_service.IdentityService.session_repo`

```python
session_repo = IdentitySessionRepository(session)
```

####### `leadr.auth.services.identity_service.IdentityService.soft_delete`

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

####### `leadr.auth.services.identity_service.IdentityService.start_session`

```python
start_session(game_id, client_fingerprint, platform=None, metadata=None, test_mode=False)
```

Start a new identity session.

Internally:

1. Get or create Device (via DeviceService)
1. Get or create Identity
1. Create IdentitySession with tokens

**Parameters:**

- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) – Game UUID
- **client_fingerprint** (<code>[str](#str)</code>) – Client-generated SHA256 device fingerprint
- **platform** (<code>[str](#str) | None</code>) – Device platform (ios, android, etc.)
- **metadata** (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\] | None</code>) – Additional device metadata
- **test_mode** (<code>[bool](#bool)</code>) – If True, session is in test mode

**Returns:**

- <code>[tuple](#tuple)\[[Identity](./auth.md#leadr.auth.domain.identity.Identity), [str](#str), [str](#str), [int](#int)\]</code> – tuple\[Identity, str, str, int\]: (identity, access_token, refresh_token, expires_in)

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If game doesn't exist

####### `leadr.auth.services.identity_service.IdentityService.update_identity`

```python
update_identity(identity_id, display_name=None)
```

Update an identity's mutable fields.

**Parameters:**

- **identity_id** (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) – The ID of the identity to update
- **display_name** (<code>[str](#str) | None</code>) – New display name (None to clear)

**Returns:**

- <code>[Identity](./auth.md#leadr.auth.domain.identity.Identity)</code> – The updated identity

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the identity doesn't exist

####### `leadr.auth.services.identity_service.IdentityService.validate_identity_token`

```python
validate_identity_token(token)
```

Validate access token and return associated identity.

Validates JWT signature and expiration, checks session validity,
and returns the identity.

**Parameters:**

- **token** (<code>[str](#str)</code>) – JWT access token

**Returns:**

- <code>[Identity](./auth.md#leadr.auth.domain.identity.Identity) | None</code> – Identity if token is valid, None otherwise

##### `leadr.auth.services.nonce_service`

Nonce service for managing request nonces.

**Classes:**

- [**NonceService**](#leadr.auth.services.nonce_service.NonceService) – Service for managing request nonces.

###### `leadr.auth.services.nonce_service.NonceService`

Bases: <code>[BaseService](./common.md#leadr.common.services.BaseService)\[[Nonce](./auth.md#leadr.auth.domain.nonce.Nonce), [NonceRepository](./auth.md#leadr.auth.services.repositories.NonceRepository)\]</code>

Service for managing request nonces.

Nonces are single-use tokens that clients must obtain before making
mutating requests. This prevents replay attacks by ensuring each
request is fresh and authorized by the server.

**Functions:**

- [**cleanup_expired_nonces**](#leadr.auth.services.nonce_service.NonceService.cleanup_expired_nonces) – Clean up expired nonces older than specified hours.
- [**delete**](#leadr.auth.services.nonce_service.NonceService.delete) – Soft-delete an entity.
- [**generate_nonce**](#leadr.auth.services.nonce_service.NonceService.generate_nonce) – Generate a fresh nonce for an identity.
- [**get_by_id**](#leadr.auth.services.nonce_service.NonceService.get_by_id) – Get an entity by its ID.
- [**get_by_id_or_raise**](#leadr.auth.services.nonce_service.NonceService.get_by_id_or_raise) – Get an entity by its ID or raise EntityNotFoundError.
- [**list_all**](#leadr.auth.services.nonce_service.NonceService.list_all) – List all non-deleted entities.
- [**soft_delete**](#leadr.auth.services.nonce_service.NonceService.soft_delete) – Soft-delete an entity and return it before deletion.
- [**validate_and_consume_nonce**](#leadr.auth.services.nonce_service.NonceService.validate_and_consume_nonce) – Validate nonce and mark as used (atomic operation).

**Attributes:**

- [**repository**](#leadr.auth.services.nonce_service.NonceService.repository) –

####### `leadr.auth.services.nonce_service.NonceService.cleanup_expired_nonces`

```python
cleanup_expired_nonces(older_than_hours=24)
```

Clean up expired nonces older than specified hours.

Only deletes nonces with PENDING status. Used nonces are kept
for audit/debugging purposes.

**Parameters:**

- **older_than_hours** (<code>[int](#int)</code>) – Delete nonces expired before this many hours ago (default 24)

**Returns:**

- <code>[int](#int)</code> – Number of nonces deleted

<details class="example" open markdown="1">
<summary>Example</summary>

> > > # In background task or cron job
> > >
> > > deleted = await service.cleanup_expired_nonces(older_than_hours=24)
> > > logger.info(f"Cleaned up {deleted} expired nonces")

</details>

####### `leadr.auth.services.nonce_service.NonceService.delete`

```python
delete(entity_id)
```

Soft-delete an entity.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – The ID of the entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the entity doesn't exist

####### `leadr.auth.services.nonce_service.NonceService.generate_nonce`

```python
generate_nonce(identity_id, ttl_seconds=60)
```

Generate a fresh nonce for an identity.

**Parameters:**

- **identity_id** (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) – Identity ID to associate nonce with
- **ttl_seconds** (<code>[int](#int)</code>) – Time-to-live in seconds (default 60)

**Returns:**

- <code>[tuple](#tuple)\[[str](#str), [datetime](#datetime.datetime)\]</code> – tuple\[str, datetime\]: (nonce_value, expires_at)

<details class="example" open markdown="1">
<summary>Example</summary>

> > > nonce_value, expires_at = await service.generate_nonce(identity_id)
> > >
> > > # Client includes nonce_value in leadr-client-nonce header

</details>

####### `leadr.auth.services.nonce_service.NonceService.get_by_id`

```python
get_by_id(entity_id)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – The ID of the entity to retrieve

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.services.DomainEntityT) | None</code> – The domain entity if found, None otherwise

####### `leadr.auth.services.nonce_service.NonceService.get_by_id_or_raise`

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

####### `leadr.auth.services.nonce_service.NonceService.list_all`

```python
list_all()
```

List all non-deleted entities.

**Returns:**

- <code>[list](#list)\[[DomainEntityT](./common.md#leadr.common.services.DomainEntityT)\]</code> – List of domain entities

####### `leadr.auth.services.nonce_service.NonceService.repository`

```python
repository = repository if repository is not None else self._create_repository(session)
```

####### `leadr.auth.services.nonce_service.NonceService.soft_delete`

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

####### `leadr.auth.services.nonce_service.NonceService.validate_and_consume_nonce`

```python
validate_and_consume_nonce(nonce_value, identity_id)
```

Validate nonce and mark as used (atomic operation).

**Parameters:**

- **nonce_value** (<code>[str](#str)</code>) – The nonce value to validate
- **identity_id** (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) – Expected identity ID (must match nonce owner)

**Returns:**

- <code>[bool](#bool)</code> – True if nonce was valid and consumed

**Raises:**

- <code>[ValueError](#ValueError)</code> – If nonce is invalid (expired, already used, wrong identity, or not found)

<details class="example" open markdown="1">
<summary>Example</summary>

> > > try:
> > > ... await service.validate_and_consume_nonce(nonce_value, identity.id)
> > > ... except ValueError as e:
> > > ... # Handle invalid nonce (return 412 error to client)
> > > ... raise HTTPException(status_code=412, detail=str(e))

</details>

##### `leadr.auth.services.nonce_tasks`

Background tasks for nonce cleanup.

Contains tasks for:

- Cleaning up expired nonces to prevent database bloat

**Functions:**

- [**cleanup_expired_nonces**](#leadr.auth.services.nonce_tasks.cleanup_expired_nonces) – Clean up expired pending nonces.

**Attributes:**

- [**logger**](#leadr.auth.services.nonce_tasks.logger) –

###### `leadr.auth.services.nonce_tasks.cleanup_expired_nonces`

```python
cleanup_expired_nonces()
```

Clean up expired pending nonces.

Deletes nonces that are:

- Status: PENDING (unused)
- Expired before current time

Used and expired nonces are kept for audit purposes.

This task is designed to be called periodically (e.g., every hour).

###### `leadr.auth.services.nonce_tasks.logger`

```python
logger = logging.getLogger(__name__)
```

##### `leadr.auth.services.repositories`

API Key, Device, Identity, and Nonce repository services.

**Classes:**

- [**APIKeyRepository**](./auth.md#leadr.auth.services.repositories.APIKeyRepository) – API Key repository for managing API key persistence.
- [**DeviceRepository**](./auth.md#leadr.auth.services.repositories.DeviceRepository) – Device repository for managing device persistence.
- [**IdentityRepository**](./auth.md#leadr.auth.services.repositories.IdentityRepository) – Identity repository for managing identity persistence.
- [**IdentitySessionRepository**](./auth.md#leadr.auth.services.repositories.IdentitySessionRepository) – IdentitySession repository for managing identity session persistence.
- [**NonceRepository**](./auth.md#leadr.auth.services.repositories.NonceRepository) – Nonce repository for managing nonce persistence.

###### `leadr.auth.services.repositories.APIKeyRepository`

Bases: <code>[BaseRepository](./common.md#leadr.common.repositories.BaseRepository)\[[APIKey](#leadr.auth.domain.api_key.APIKey), [APIKeyORM](./auth.md#leadr.auth.adapters.orm.APIKeyORM)\]</code>

API Key repository for managing API key persistence.

**Functions:**

- [**count_active_by_account**](#leadr.auth.services.repositories.APIKeyRepository.count_active_by_account) – Count active, non-deleted API keys for a given account.
- [**create**](./auth.md#leadr.auth.services.repositories.APIKeyRepository.create) – Create a new entity in the database.
- [**delete**](./auth.md#leadr.auth.services.repositories.APIKeyRepository.delete) – Soft delete an entity by setting its deleted_at timestamp.
- [**filter**](./auth.md#leadr.auth.services.repositories.APIKeyRepository.filter) – Filter API keys by account and optional criteria with pagination.
- [**get_by_id**](#leadr.auth.services.repositories.APIKeyRepository.get_by_id) – Get an entity by its ID.
- [**get_by_prefix**](#leadr.auth.services.repositories.APIKeyRepository.get_by_prefix) – Get API key by prefix, returns None if not found or soft-deleted.
- [**get_by_prefix_with_user**](#leadr.auth.services.repositories.APIKeyRepository.get_by_prefix_with_user) – Get API key and associated user in a single query.
- [**update**](./auth.md#leadr.auth.services.repositories.APIKeyRepository.update) – Update an existing entity in the database.

**Attributes:**

- [**SORTABLE_FIELDS**](#leadr.auth.services.repositories.APIKeyRepository.SORTABLE_FIELDS) –
- [**session**](./auth.md#leadr.auth.services.repositories.APIKeyRepository.session) –

####### `leadr.auth.services.repositories.APIKeyRepository.SORTABLE_FIELDS`

```python
SORTABLE_FIELDS = {'id', 'name', 'created_at', 'updated_at'}
```

####### `leadr.auth.services.repositories.APIKeyRepository.count_active_by_account`

```python
count_active_by_account(account_id)
```

Count active, non-deleted API keys for a given account.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – The account ID to count keys for.

**Returns:**

- <code>[int](#int)</code> – Number of active, non-deleted API keys for the account.

####### `leadr.auth.services.repositories.APIKeyRepository.create`

```python
create(entity)
```

Create a new entity in the database.

**Parameters:**

- **entity** (<code>[\_EntityBaseT](#leadr.common.repositories._EntityBaseT)</code>) – Domain entity to create

**Returns:**

- <code>[\_EntityBaseT](#leadr.common.repositories._EntityBaseT)</code> – Created domain entity with refreshed data

####### `leadr.auth.services.repositories.APIKeyRepository.delete`

```python
delete(entity_id)
```

Soft delete an entity by setting its deleted_at timestamp.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – ID of entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

####### `leadr.auth.services.repositories.APIKeyRepository.filter`

```python
filter(account_id=None, *, status=None, active_only=False, pagination, **kwargs)
```

Filter API keys by account and optional criteria with pagination.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – Optional account ID to filter by. If None, returns all API keys
  (superadmin use case). Regular users should always pass account_id.
- **status** (<code>[APIKeyStatus](#leadr.auth.domain.api_key.APIKeyStatus) | None</code>) – Optional APIKeyStatus to filter by
- **active_only** (<code>[bool](#bool)</code>) – If True, only return ACTIVE keys (bool)
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (required).
- \*\***kwargs** (<code>[Any](#typing.Any)</code>) – Additional filter parameters (reserved for future use)

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[APIKey](#leadr.auth.domain.api_key.APIKey)\]</code> – PaginatedResult containing API keys.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If sort field is not in SORTABLE_FIELDS
- <code>[CursorValidationError](#CursorValidationError)</code> – If cursor is invalid or state doesn't match

####### `leadr.auth.services.repositories.APIKeyRepository.get_by_id`

```python
get_by_id(entity_id, include_deleted=False)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – Entity ID to retrieve
- **include_deleted** (<code>[bool](#bool)</code>) – If True, include soft-deleted entities. Defaults to False.

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT) | None</code> – Domain entity if found, None otherwise

####### `leadr.auth.services.repositories.APIKeyRepository.get_by_prefix`

```python
get_by_prefix(key_prefix)
```

Get API key by prefix, returns None if not found or soft-deleted.

####### `leadr.auth.services.repositories.APIKeyRepository.get_by_prefix_with_user`

```python
get_by_prefix_with_user(key_prefix)
```

Get API key and associated user in a single query.

This method performs a JOIN between api_keys and users tables to retrieve
both entities in one database round-trip, reducing auth latency.

**Parameters:**

- **key_prefix** (<code>[str](#str)</code>) – The API key prefix to search for.

**Returns:**

- <code>[tuple](#tuple)\[[APIKey](#leadr.auth.domain.api_key.APIKey), [User](./accounts.md#leadr.accounts.domain.user.User)\] | None</code> – A tuple of (APIKey, User) if found and neither soft-deleted, None otherwise.

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

###### `leadr.auth.services.repositories.DeviceRepository`

Bases: <code>[BaseRepository](./common.md#leadr.common.repositories.BaseRepository)\[[Device](./auth.md#leadr.auth.domain.device.Device), [DeviceORM](./auth.md#leadr.auth.adapters.orm.DeviceORM)\]</code>

Device repository for managing device persistence.

**Functions:**

- [**create**](./auth.md#leadr.auth.services.repositories.DeviceRepository.create) – Create a new entity in the database.
- [**delete**](./auth.md#leadr.auth.services.repositories.DeviceRepository.delete) – Soft delete an entity by setting its deleted_at timestamp.
- [**filter**](./auth.md#leadr.auth.services.repositories.DeviceRepository.filter) – Filter devices by account and optional criteria with pagination.
- [**get_by_game_and_fingerprint**](#leadr.auth.services.repositories.DeviceRepository.get_by_game_and_fingerprint) – Get device by game_id and client_fingerprint, returns None if not found or soft-deleted.
- [**get_by_id**](#leadr.auth.services.repositories.DeviceRepository.get_by_id) – Get an entity by its ID.
- [**update**](./auth.md#leadr.auth.services.repositories.DeviceRepository.update) – Update an existing entity in the database.

**Attributes:**

- [**SORTABLE_FIELDS**](#leadr.auth.services.repositories.DeviceRepository.SORTABLE_FIELDS) –
- [**session**](./auth.md#leadr.auth.services.repositories.DeviceRepository.session) –

####### `leadr.auth.services.repositories.DeviceRepository.SORTABLE_FIELDS`

```python
SORTABLE_FIELDS = {'id', 'platform', 'created_at', 'updated_at'}
```

####### `leadr.auth.services.repositories.DeviceRepository.create`

```python
create(entity)
```

Create a new entity in the database.

**Parameters:**

- **entity** (<code>[\_EntityBaseT](#leadr.common.repositories._EntityBaseT)</code>) – Domain entity to create

**Returns:**

- <code>[\_EntityBaseT](#leadr.common.repositories._EntityBaseT)</code> – Created domain entity with refreshed data

####### `leadr.auth.services.repositories.DeviceRepository.delete`

```python
delete(entity_id)
```

Soft delete an entity by setting its deleted_at timestamp.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – ID of entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

####### `leadr.auth.services.repositories.DeviceRepository.filter`

```python
filter(account_id=None, *, game_id=None, status=None, pagination, **kwargs)
```

Filter devices by account and optional criteria with pagination.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – Optional account ID to filter by. If None, returns all devices
  (superadmin use case). Regular users should always pass account_id.
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID) | None</code>) – Optional game ID to filter by
- **status** (<code>[str](#str) | None</code>) – Optional status string to filter by (active, banned, suspended)
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (required).
- \*\***kwargs** (<code>[Any](#typing.Any)</code>) – Additional filter parameters (reserved for future use)

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[Device](./auth.md#leadr.auth.domain.device.Device)\]</code> – PaginatedResult containing devices.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If sort field is not in SORTABLE_FIELDS
- <code>[CursorValidationError](#CursorValidationError)</code> – If cursor is invalid or state doesn't match

####### `leadr.auth.services.repositories.DeviceRepository.get_by_game_and_fingerprint`

```python
get_by_game_and_fingerprint(game_id, client_fingerprint)
```

Get device by game_id and client_fingerprint, returns None if not found or soft-deleted.

**Parameters:**

- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) – The game ID
- **client_fingerprint** (<code>[str](#str)</code>) – The client-generated SHA256 device fingerprint

**Returns:**

- <code>[Device](./auth.md#leadr.auth.domain.device.Device) | None</code> – Device if found and not deleted, None otherwise

####### `leadr.auth.services.repositories.DeviceRepository.get_by_id`

```python
get_by_id(entity_id, include_deleted=False)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – Entity ID to retrieve
- **include_deleted** (<code>[bool](#bool)</code>) – If True, include soft-deleted entities. Defaults to False.

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT) | None</code> – Domain entity if found, None otherwise

####### `leadr.auth.services.repositories.DeviceRepository.session`

```python
session = session
```

####### `leadr.auth.services.repositories.DeviceRepository.update`

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

###### `leadr.auth.services.repositories.IdentityRepository`

Bases: <code>[BaseRepository](./common.md#leadr.common.repositories.BaseRepository)\[[Identity](./auth.md#leadr.auth.domain.identity.Identity), [IdentityORM](./auth.md#leadr.auth.adapters.orm.IdentityORM)\]</code>

Identity repository for managing identity persistence.

**Functions:**

- [**create**](./auth.md#leadr.auth.services.repositories.IdentityRepository.create) – Create a new entity in the database.
- [**delete**](./auth.md#leadr.auth.services.repositories.IdentityRepository.delete) – Soft delete an entity by setting its deleted_at timestamp.
- [**filter**](./auth.md#leadr.auth.services.repositories.IdentityRepository.filter) – Filter identities by account and optional criteria with pagination.
- [**get_by_external_key**](#leadr.auth.services.repositories.IdentityRepository.get_by_external_key) – Get identity by unique key combination.
- [**get_by_id**](#leadr.auth.services.repositories.IdentityRepository.get_by_id) – Get an entity by its ID.
- [**update**](./auth.md#leadr.auth.services.repositories.IdentityRepository.update) – Update an existing entity in the database.

**Attributes:**

- [**SORTABLE_FIELDS**](#leadr.auth.services.repositories.IdentityRepository.SORTABLE_FIELDS) –
- [**session**](./auth.md#leadr.auth.services.repositories.IdentityRepository.session) –

####### `leadr.auth.services.repositories.IdentityRepository.SORTABLE_FIELDS`

```python
SORTABLE_FIELDS = {'id', 'display_name', 'kind', 'created_at', 'updated_at'}
```

####### `leadr.auth.services.repositories.IdentityRepository.create`

```python
create(entity)
```

Create a new entity in the database.

**Parameters:**

- **entity** (<code>[\_EntityBaseT](#leadr.common.repositories._EntityBaseT)</code>) – Domain entity to create

**Returns:**

- <code>[\_EntityBaseT](#leadr.common.repositories._EntityBaseT)</code> – Created domain entity with refreshed data

####### `leadr.auth.services.repositories.IdentityRepository.delete`

```python
delete(entity_id)
```

Soft delete an entity by setting its deleted_at timestamp.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – ID of entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

####### `leadr.auth.services.repositories.IdentityRepository.filter`

```python
filter(account_id=None, *, game_id=None, kind=None, pagination, **kwargs)
```

Filter identities by account and optional criteria with pagination.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – Optional account ID to filter by. If None, returns all identities
  (superadmin use case). Regular users should always pass account_id.
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID) | None</code>) – Optional game ID to filter by
- **kind** (<code>[IdentityKind](./auth.md#leadr.auth.domain.identity.IdentityKind) | None</code>) – Optional identity kind to filter by
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (required).
- \*\***kwargs** (<code>[Any](#typing.Any)</code>) – Additional filter parameters (reserved for future use)

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[Identity](./auth.md#leadr.auth.domain.identity.Identity)\]</code> – PaginatedResult containing identities.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If sort field is not in SORTABLE_FIELDS
- <code>[CursorValidationError](#CursorValidationError)</code> – If cursor is invalid or state doesn't match

####### `leadr.auth.services.repositories.IdentityRepository.get_by_external_key`

```python
get_by_external_key(account_id, game_id, kind, external_key)
```

Get identity by unique key combination.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – The account ID
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) – The game ID
- **kind** (<code>[IdentityKind](./auth.md#leadr.auth.domain.identity.IdentityKind)</code>) – The identity kind (DEVICE, STEAM, CUSTOM)
- **external_key** (<code>[str](#str)</code>) – The external identifier

**Returns:**

- <code>[Identity](./auth.md#leadr.auth.domain.identity.Identity) | None</code> – Identity if found and not deleted, None otherwise

####### `leadr.auth.services.repositories.IdentityRepository.get_by_id`

```python
get_by_id(entity_id, include_deleted=False)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – Entity ID to retrieve
- **include_deleted** (<code>[bool](#bool)</code>) – If True, include soft-deleted entities. Defaults to False.

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT) | None</code> – Domain entity if found, None otherwise

####### `leadr.auth.services.repositories.IdentityRepository.session`

```python
session = session
```

####### `leadr.auth.services.repositories.IdentityRepository.update`

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

###### `leadr.auth.services.repositories.IdentitySessionRepository`

Bases: <code>[BaseRepository](./common.md#leadr.common.repositories.BaseRepository)\[[IdentitySession](./auth.md#leadr.auth.domain.identity.IdentitySession), [IdentitySessionORM](./auth.md#leadr.auth.adapters.orm.IdentitySessionORM)\]</code>

IdentitySession repository for managing identity session persistence.

**Functions:**

- [**create**](./auth.md#leadr.auth.services.repositories.IdentitySessionRepository.create) – Create a new entity in the database.
- [**delete**](./auth.md#leadr.auth.services.repositories.IdentitySessionRepository.delete) – Soft delete an entity by setting its deleted_at timestamp.
- [**filter**](./auth.md#leadr.auth.services.repositories.IdentitySessionRepository.filter) – Filter sessions by account and optional criteria with pagination.
- [**get_by_id**](#leadr.auth.services.repositories.IdentitySessionRepository.get_by_id) – Get an entity by its ID.
- [**get_by_refresh_token_hash**](#leadr.auth.services.repositories.IdentitySessionRepository.get_by_refresh_token_hash) – Get session by refresh token hash, returns None if not found or soft-deleted.
- [**get_by_token_hash**](#leadr.auth.services.repositories.IdentitySessionRepository.get_by_token_hash) – Get session by access token hash, returns None if not found or soft-deleted.
- [**update**](./auth.md#leadr.auth.services.repositories.IdentitySessionRepository.update) – Update an existing entity in the database.

**Attributes:**

- [**SORTABLE_FIELDS**](#leadr.auth.services.repositories.IdentitySessionRepository.SORTABLE_FIELDS) –
- [**session**](./auth.md#leadr.auth.services.repositories.IdentitySessionRepository.session) –

####### `leadr.auth.services.repositories.IdentitySessionRepository.SORTABLE_FIELDS`

```python
SORTABLE_FIELDS = {'id', 'created_at', 'updated_at'}
```

####### `leadr.auth.services.repositories.IdentitySessionRepository.create`

```python
create(entity)
```

Create a new entity in the database.

**Parameters:**

- **entity** (<code>[\_EntityBaseT](#leadr.common.repositories._EntityBaseT)</code>) – Domain entity to create

**Returns:**

- <code>[\_EntityBaseT](#leadr.common.repositories._EntityBaseT)</code> – Created domain entity with refreshed data

####### `leadr.auth.services.repositories.IdentitySessionRepository.delete`

```python
delete(entity_id)
```

Soft delete an entity by setting its deleted_at timestamp.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – ID of entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

####### `leadr.auth.services.repositories.IdentitySessionRepository.filter`

```python
filter(account_id=None, *, identity_id=None, pagination, **kwargs)
```

Filter sessions by account and optional criteria with pagination.

Note: account_id is used for multi-tenant safety via JOIN with identities table.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – Optional account ID to filter by. If None, returns all sessions
  (superadmin use case). Regular users should always pass account_id.
- **identity_id** (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID) | None</code>) – Optional identity ID to filter by
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (required).
- \*\***kwargs** (<code>[Any](#typing.Any)</code>) – Additional filter parameters (reserved for future use)

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[IdentitySession](./auth.md#leadr.auth.domain.identity.IdentitySession)\]</code> – PaginatedResult containing identity sessions.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If sort field is not in SORTABLE_FIELDS
- <code>[CursorValidationError](#CursorValidationError)</code> – If cursor is invalid or state doesn't match

####### `leadr.auth.services.repositories.IdentitySessionRepository.get_by_id`

```python
get_by_id(entity_id, include_deleted=False)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – Entity ID to retrieve
- **include_deleted** (<code>[bool](#bool)</code>) – If True, include soft-deleted entities. Defaults to False.

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT) | None</code> – Domain entity if found, None otherwise

####### `leadr.auth.services.repositories.IdentitySessionRepository.get_by_refresh_token_hash`

```python
get_by_refresh_token_hash(refresh_token_hash)
```

Get session by refresh token hash, returns None if not found or soft-deleted.

**Parameters:**

- **refresh_token_hash** (<code>[str](#str)</code>) – The hashed refresh token

**Returns:**

- <code>[IdentitySession](./auth.md#leadr.auth.domain.identity.IdentitySession) | None</code> – IdentitySession if found and not deleted, None otherwise

####### `leadr.auth.services.repositories.IdentitySessionRepository.get_by_token_hash`

```python
get_by_token_hash(token_hash)
```

Get session by access token hash, returns None if not found or soft-deleted.

**Parameters:**

- **token_hash** (<code>[str](#str)</code>) – The hashed access token

**Returns:**

- <code>[IdentitySession](./auth.md#leadr.auth.domain.identity.IdentitySession) | None</code> – IdentitySession if found and not deleted, None otherwise

####### `leadr.auth.services.repositories.IdentitySessionRepository.session`

```python
session = session
```

####### `leadr.auth.services.repositories.IdentitySessionRepository.update`

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

###### `leadr.auth.services.repositories.NonceRepository`

Bases: <code>[BaseRepository](./common.md#leadr.common.repositories.BaseRepository)\[[Nonce](./auth.md#leadr.auth.domain.nonce.Nonce), [NonceORM](./auth.md#leadr.auth.adapters.orm.NonceORM)\]</code>

Nonce repository for managing nonce persistence.

**Functions:**

- [**cleanup_expired_nonces**](#leadr.auth.services.repositories.NonceRepository.cleanup_expired_nonces) – Delete expired nonces older than specified time.
- [**create**](./auth.md#leadr.auth.services.repositories.NonceRepository.create) – Create a new entity in the database.
- [**delete**](./auth.md#leadr.auth.services.repositories.NonceRepository.delete) – Soft delete an entity by setting its deleted_at timestamp.
- [**filter**](./auth.md#leadr.auth.services.repositories.NonceRepository.filter) – Filter nonces by account and optional criteria.
- [**get_by_id**](#leadr.auth.services.repositories.NonceRepository.get_by_id) – Get an entity by its ID.
- [**get_by_nonce_value**](#leadr.auth.services.repositories.NonceRepository.get_by_nonce_value) – Get nonce by nonce_value, returns None if not found or soft-deleted.
- [**update**](./auth.md#leadr.auth.services.repositories.NonceRepository.update) – Update an existing entity in the database.

**Attributes:**

- [**session**](./auth.md#leadr.auth.services.repositories.NonceRepository.session) –

####### `leadr.auth.services.repositories.NonceRepository.cleanup_expired_nonces`

```python
cleanup_expired_nonces(before)
```

Delete expired nonces older than specified time.

Only deletes nonces with PENDING status. Used and expired nonces
are kept for audit/debugging purposes.

**Parameters:**

- **before** (<code>[datetime](#datetime.datetime)</code>) – Delete nonces that expired before this datetime

**Returns:**

- <code>[int](#int)</code> – Number of nonces deleted

####### `leadr.auth.services.repositories.NonceRepository.create`

```python
create(entity)
```

Create a new entity in the database.

**Parameters:**

- **entity** (<code>[\_EntityBaseT](#leadr.common.repositories._EntityBaseT)</code>) – Domain entity to create

**Returns:**

- <code>[\_EntityBaseT](#leadr.common.repositories._EntityBaseT)</code> – Created domain entity with refreshed data

####### `leadr.auth.services.repositories.NonceRepository.delete`

```python
delete(entity_id)
```

Soft delete an entity by setting its deleted_at timestamp.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – ID of entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

####### `leadr.auth.services.repositories.NonceRepository.filter`

```python
filter(account_id=None, identity_id=None, **kwargs)
```

Filter nonces by account and optional criteria.

Note: account_id is used for multi-tenant safety via JOIN with identities table.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – REQUIRED - Account ID to filter by (multi-tenant safety)
- **identity_id** (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID) | None</code>) – Optional identity ID to filter by

**Returns:**

- <code>[list](#list)\[[Nonce](./auth.md#leadr.auth.domain.nonce.Nonce)\]</code> – List of nonces matching the filter criteria

**Raises:**

- <code>[ValueError](#ValueError)</code> – If account_id is None (required for multi-tenant safety)

####### `leadr.auth.services.repositories.NonceRepository.get_by_id`

```python
get_by_id(entity_id, include_deleted=False)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – Entity ID to retrieve
- **include_deleted** (<code>[bool](#bool)</code>) – If True, include soft-deleted entities. Defaults to False.

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT) | None</code> – Domain entity if found, None otherwise

####### `leadr.auth.services.repositories.NonceRepository.get_by_nonce_value`

```python
get_by_nonce_value(nonce_value)
```

Get nonce by nonce_value, returns None if not found or soft-deleted.

**Parameters:**

- **nonce_value** (<code>[str](#str)</code>) – The unique nonce value to search for

**Returns:**

- <code>[Nonce](./auth.md#leadr.auth.domain.nonce.Nonce) | None</code> – Nonce if found and not deleted, None otherwise

####### `leadr.auth.services.repositories.NonceRepository.session`

```python
session = session
```

####### `leadr.auth.services.repositories.NonceRepository.update`

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
