### `leadr.scores`

**Modules:**

- [**adapters**](./scores.md#leadr.scores.adapters) –
- [**api**](./scores.md#leadr.scores.api) –
- [**domain**](./scores.md#leadr.scores.domain) –
- [**services**](./scores.md#leadr.scores.services) –

#### `leadr.scores.adapters`

**Modules:**

- [**orm**](./scores.md#leadr.scores.adapters.orm) – Score ORM models.

##### `leadr.scores.adapters.orm`

Score ORM models.

**Classes:**

- [**ScoreFlagORM**](./scores.md#leadr.scores.adapters.orm.ScoreFlagORM) – Score flag ORM model for anti-cheat detections.
- [**ScoreORM**](./scores.md#leadr.scores.adapters.orm.ScoreORM) – Score ORM model.
- [**ScoreSubmissionMetaORM**](./scores.md#leadr.scores.adapters.orm.ScoreSubmissionMetaORM) – Score submission metadata ORM model for anti-cheat tracking.

###### `leadr.scores.adapters.orm.ScoreFlagORM`

Bases: <code>[Base](./common.md#leadr.common.orm.Base)</code>

Score flag ORM model for anti-cheat detections.

Records suspicious patterns detected by the anti-cheat system.
Flags can be reviewed by admins to confirm or dismiss detections.

**Functions:**

- [**from_domain**](#leadr.scores.adapters.orm.ScoreFlagORM.from_domain) – Convert domain entity to ORM model.
- [**to_domain**](#leadr.scores.adapters.orm.ScoreFlagORM.to_domain) – Convert ORM model to domain entity.

**Attributes:**

- [**confidence**](./scores.md#leadr.scores.adapters.orm.ScoreFlagORM.confidence) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**created_at**](#leadr.scores.adapters.orm.ScoreFlagORM.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**deleted_at**](#leadr.scores.adapters.orm.ScoreFlagORM.deleted_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[nullable_timestamp](#leadr.common.orm.nullable_timestamp)\]</code>) –
- [**flag_metadata**](#leadr.scores.adapters.orm.ScoreFlagORM.flag_metadata) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[dict](#dict)\[[str](#str), [Any](#typing.Any)\]\]</code>) –
- [**flag_type**](#leadr.scores.adapters.orm.ScoreFlagORM.flag_type) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**id**](./scores.md#leadr.scores.adapters.orm.ScoreFlagORM.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**reviewed_at**](#leadr.scores.adapters.orm.ScoreFlagORM.reviewed_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime) | None\]</code>) –
- [**reviewer_decision**](#leadr.scores.adapters.orm.ScoreFlagORM.reviewer_decision) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**reviewer_id**](#leadr.scores.adapters.orm.ScoreFlagORM.reviewer_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID) | None\]</code>) –
- [**score_id**](#leadr.scores.adapters.orm.ScoreFlagORM.score_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**status**](./scores.md#leadr.scores.adapters.orm.ScoreFlagORM.status) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**updated_at**](#leadr.scores.adapters.orm.ScoreFlagORM.updated_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –

####### `leadr.scores.adapters.orm.ScoreFlagORM.confidence`

```python
confidence: Mapped[str] = mapped_column(String, nullable=False, index=True)
```

####### `leadr.scores.adapters.orm.ScoreFlagORM.created_at`

```python
created_at: Mapped[timestamp]
```

####### `leadr.scores.adapters.orm.ScoreFlagORM.deleted_at`

```python
deleted_at: Mapped[nullable_timestamp]
```

####### `leadr.scores.adapters.orm.ScoreFlagORM.flag_metadata`

```python
flag_metadata: Mapped[dict[str, Any]] = mapped_column('metadata', JSONB, nullable=False, default=dict, server_default='{}')
```

####### `leadr.scores.adapters.orm.ScoreFlagORM.flag_type`

```python
flag_type: Mapped[str] = mapped_column(String, nullable=False, index=True)
```

####### `leadr.scores.adapters.orm.ScoreFlagORM.from_domain`

```python
from_domain(entity)
```

Convert domain entity to ORM model.

####### `leadr.scores.adapters.orm.ScoreFlagORM.id`

```python
id: Mapped[uuid_pk]
```

####### `leadr.scores.adapters.orm.ScoreFlagORM.reviewed_at`

```python
reviewed_at: Mapped[datetime | None] = mapped_column(DateTime(timezone=True), nullable=True, default=None)
```

####### `leadr.scores.adapters.orm.ScoreFlagORM.reviewer_decision`

```python
reviewer_decision: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
```

####### `leadr.scores.adapters.orm.ScoreFlagORM.reviewer_id`

```python
reviewer_id: Mapped[UUID | None] = mapped_column(nullable=True, default=None)
```

####### `leadr.scores.adapters.orm.ScoreFlagORM.score_id`

```python
score_id: Mapped[UUID] = mapped_column(ForeignKey('scores.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.scores.adapters.orm.ScoreFlagORM.status`

```python
status: Mapped[str] = mapped_column(String, nullable=False, default='PENDING', index=True)
```

####### `leadr.scores.adapters.orm.ScoreFlagORM.to_domain`

```python
to_domain()
```

Convert ORM model to domain entity.

####### `leadr.scores.adapters.orm.ScoreFlagORM.updated_at`

```python
updated_at: Mapped[timestamp] = mapped_column(onupdate=(func.now()))
```

###### `leadr.scores.adapters.orm.ScoreORM`

Bases: <code>[Base](./common.md#leadr.common.orm.Base)</code>

Score ORM model.

Represents a player's score submission for a board in the database.
Maps to the scores table with foreign keys to accounts, devices, games, and boards.

**Attributes:**

- [**account**](./scores.md#leadr.scores.adapters.orm.ScoreORM.account) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[AccountORM](./accounts.md#leadr.accounts.adapters.orm.AccountORM)\]</code>) –
- [**account_id**](#leadr.scores.adapters.orm.ScoreORM.account_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**board**](./scores.md#leadr.scores.adapters.orm.ScoreORM.board) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[BoardORM](./boards.md#leadr.boards.adapters.orm.BoardORM)\]</code>) –
- [**board_id**](#leadr.scores.adapters.orm.ScoreORM.board_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**created_at**](#leadr.scores.adapters.orm.ScoreORM.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**deleted_at**](#leadr.scores.adapters.orm.ScoreORM.deleted_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[nullable_timestamp](#leadr.common.orm.nullable_timestamp)\]</code>) –
- [**device_id**](#leadr.scores.adapters.orm.ScoreORM.device_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**filter_city**](#leadr.scores.adapters.orm.ScoreORM.filter_city) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**filter_country**](#leadr.scores.adapters.orm.ScoreORM.filter_country) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**filter_timezone**](#leadr.scores.adapters.orm.ScoreORM.filter_timezone) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**game**](./scores.md#leadr.scores.adapters.orm.ScoreORM.game) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[GameORM](./games.md#leadr.games.adapters.orm.GameORM)\]</code>) –
- [**game_id**](#leadr.scores.adapters.orm.ScoreORM.game_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**id**](./scores.md#leadr.scores.adapters.orm.ScoreORM.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**player_name**](#leadr.scores.adapters.orm.ScoreORM.player_name) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**score_metadata**](#leadr.scores.adapters.orm.ScoreORM.score_metadata) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[Any](#typing.Any) | None\]</code>) –
- [**updated_at**](#leadr.scores.adapters.orm.ScoreORM.updated_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**value**](./scores.md#leadr.scores.adapters.orm.ScoreORM.value) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[float](#float)\]</code>) –
- [**value_display**](#leadr.scores.adapters.orm.ScoreORM.value_display) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –

####### `leadr.scores.adapters.orm.ScoreORM.account`

```python
account: Mapped[AccountORM] = relationship('AccountORM')
```

####### `leadr.scores.adapters.orm.ScoreORM.account_id`

```python
account_id: Mapped[UUID] = mapped_column(ForeignKey('accounts.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.scores.adapters.orm.ScoreORM.board`

```python
board: Mapped[BoardORM] = relationship('BoardORM')
```

####### `leadr.scores.adapters.orm.ScoreORM.board_id`

```python
board_id: Mapped[UUID] = mapped_column(ForeignKey('boards.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.scores.adapters.orm.ScoreORM.created_at`

```python
created_at: Mapped[timestamp]
```

####### `leadr.scores.adapters.orm.ScoreORM.deleted_at`

```python
deleted_at: Mapped[nullable_timestamp]
```

####### `leadr.scores.adapters.orm.ScoreORM.device_id`

```python
device_id: Mapped[UUID] = mapped_column(nullable=False, index=True)
```

####### `leadr.scores.adapters.orm.ScoreORM.filter_city`

```python
filter_city: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
```

####### `leadr.scores.adapters.orm.ScoreORM.filter_country`

```python
filter_country: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
```

####### `leadr.scores.adapters.orm.ScoreORM.filter_timezone`

```python
filter_timezone: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
```

####### `leadr.scores.adapters.orm.ScoreORM.game`

```python
game: Mapped[GameORM] = relationship('GameORM')
```

####### `leadr.scores.adapters.orm.ScoreORM.game_id`

```python
game_id: Mapped[UUID] = mapped_column(ForeignKey('games.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.scores.adapters.orm.ScoreORM.id`

```python
id: Mapped[uuid_pk]
```

####### `leadr.scores.adapters.orm.ScoreORM.player_name`

```python
player_name: Mapped[str] = mapped_column(String, nullable=False)
```

####### `leadr.scores.adapters.orm.ScoreORM.score_metadata`

```python
score_metadata: Mapped[Any | None] = mapped_column('score_metadata', JSON, nullable=True, default=None)
```

####### `leadr.scores.adapters.orm.ScoreORM.updated_at`

```python
updated_at: Mapped[timestamp] = mapped_column(onupdate=(func.now()))
```

####### `leadr.scores.adapters.orm.ScoreORM.value`

```python
value: Mapped[float] = mapped_column(Float, nullable=False)
```

####### `leadr.scores.adapters.orm.ScoreORM.value_display`

```python
value_display: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
```

###### `leadr.scores.adapters.orm.ScoreSubmissionMetaORM`

Bases: <code>[Base](./common.md#leadr.common.orm.Base)</code>

Score submission metadata ORM model for anti-cheat tracking.

Tracks submission history per device/board combination to enable
detection of suspicious patterns like rapid-fire submissions.

**Functions:**

- [**from_domain**](#leadr.scores.adapters.orm.ScoreSubmissionMetaORM.from_domain) – Convert domain entity to ORM model.
- [**to_domain**](#leadr.scores.adapters.orm.ScoreSubmissionMetaORM.to_domain) – Convert ORM model to domain entity.

**Attributes:**

- [**board_id**](#leadr.scores.adapters.orm.ScoreSubmissionMetaORM.board_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**created_at**](#leadr.scores.adapters.orm.ScoreSubmissionMetaORM.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**deleted_at**](#leadr.scores.adapters.orm.ScoreSubmissionMetaORM.deleted_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[nullable_timestamp](#leadr.common.orm.nullable_timestamp)\]</code>) –
- [**device_id**](#leadr.scores.adapters.orm.ScoreSubmissionMetaORM.device_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**id**](./scores.md#leadr.scores.adapters.orm.ScoreSubmissionMetaORM.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**last_score_value**](#leadr.scores.adapters.orm.ScoreSubmissionMetaORM.last_score_value) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[float](#float) | None\]</code>) –
- [**last_submission_at**](#leadr.scores.adapters.orm.ScoreSubmissionMetaORM.last_submission_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime)\]</code>) –
- [**score_id**](#leadr.scores.adapters.orm.ScoreSubmissionMetaORM.score_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**submission_count**](#leadr.scores.adapters.orm.ScoreSubmissionMetaORM.submission_count) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[int](#int)\]</code>) –
- [**updated_at**](#leadr.scores.adapters.orm.ScoreSubmissionMetaORM.updated_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –

####### `leadr.scores.adapters.orm.ScoreSubmissionMetaORM.board_id`

```python
board_id: Mapped[UUID] = mapped_column(nullable=False, index=True)
```

####### `leadr.scores.adapters.orm.ScoreSubmissionMetaORM.created_at`

```python
created_at: Mapped[timestamp]
```

####### `leadr.scores.adapters.orm.ScoreSubmissionMetaORM.deleted_at`

```python
deleted_at: Mapped[nullable_timestamp]
```

####### `leadr.scores.adapters.orm.ScoreSubmissionMetaORM.device_id`

```python
device_id: Mapped[UUID] = mapped_column(nullable=False, index=True)
```

####### `leadr.scores.adapters.orm.ScoreSubmissionMetaORM.from_domain`

```python
from_domain(entity)
```

Convert domain entity to ORM model.

####### `leadr.scores.adapters.orm.ScoreSubmissionMetaORM.id`

```python
id: Mapped[uuid_pk]
```

####### `leadr.scores.adapters.orm.ScoreSubmissionMetaORM.last_score_value`

```python
last_score_value: Mapped[float | None] = mapped_column(Float, nullable=True, default=None)
```

####### `leadr.scores.adapters.orm.ScoreSubmissionMetaORM.last_submission_at`

```python
last_submission_at: Mapped[datetime] = mapped_column(DateTime(timezone=True), nullable=False)
```

####### `leadr.scores.adapters.orm.ScoreSubmissionMetaORM.score_id`

```python
score_id: Mapped[UUID] = mapped_column(ForeignKey('scores.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.scores.adapters.orm.ScoreSubmissionMetaORM.submission_count`

```python
submission_count: Mapped[int] = mapped_column(Integer, nullable=False, default=1)
```

####### `leadr.scores.adapters.orm.ScoreSubmissionMetaORM.to_domain`

```python
to_domain()
```

Convert ORM model to domain entity.

####### `leadr.scores.adapters.orm.ScoreSubmissionMetaORM.updated_at`

```python
updated_at: Mapped[timestamp] = mapped_column(onupdate=(func.now()))
```

#### `leadr.scores.api`

**Modules:**

- [**score_flag_routes**](#leadr.scores.api.score_flag_routes) – API routes for score flag management.
- [**score_flag_schemas**](#leadr.scores.api.score_flag_schemas) – API request and response models for score flags.
- [**score_routes**](#leadr.scores.api.score_routes) – API routes for score management.
- [**score_schemas**](#leadr.scores.api.score_schemas) – API request and response models for scores.
- [**score_submission_meta_routes**](#leadr.scores.api.score_submission_meta_routes) – API routes for score submission metadata management.
- [**score_submission_meta_schemas**](#leadr.scores.api.score_submission_meta_schemas) – API schemas for score submission metadata.

##### `leadr.scores.api.score_flag_routes`

API routes for score flag management.

**Functions:**

- [**get_score_flag**](#leadr.scores.api.score_flag_routes.get_score_flag) – Get a score flag by ID.
- [**list_score_flags**](#leadr.scores.api.score_flag_routes.list_score_flags) – List score flags for an account with optional filters.
- [**update_score_flag**](#leadr.scores.api.score_flag_routes.update_score_flag) – Update a score flag (review or soft-delete).

**Attributes:**

- [**router**](#leadr.scores.api.score_flag_routes.router) –

###### `leadr.scores.api.score_flag_routes.get_score_flag`

```python
get_score_flag(flag_id, service, auth)
```

Get a score flag by ID.

**Parameters:**

- **flag_id** (<code>[ScoreFlagID](./common.md#leadr.common.domain.ids.ScoreFlagID)</code>) – Flag identifier to retrieve.
- **service** (<code>[ScoreFlagServiceDep](./scores.md#leadr.scores.services.dependencies.ScoreFlagServiceDep)</code>) – Injected score flag service dependency.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.

**Returns:**

- <code>[ScoreFlagResponse](#leadr.scores.api.score_flag_schemas.ScoreFlagResponse)</code> – ScoreFlagResponse with the flag details.

**Raises:**

- <code>403</code> – User does not have access to this flag's account.
- <code>404</code> – Flag not found or soft-deleted.

###### `leadr.scores.api.score_flag_routes.list_score_flags`

```python
list_score_flags(auth, service, account_id=None, board_id=None, game_id=None, status=None, flag_type=None)
```

List score flags for an account with optional filters.

Returns all non-deleted flags for the specified account, with optional
filtering by board, game, status, or flag type.

For regular users, account_id is automatically derived from their API key.
For superadmins, account_id must be explicitly provided as a query parameter.

**Parameters:**

- **auth** (<code>[AdminAuthContextWithAccountIDDep](./auth.md#leadr.auth.dependencies.AdminAuthContextWithAccountIDDep)</code>) – Authentication context with user info.
- **service** (<code>[ScoreFlagServiceDep](./scores.md#leadr.scores.services.dependencies.ScoreFlagServiceDep)</code>) – Injected score flag service dependency.
- **account_id** (<code>[Annotated](#typing.Annotated)\[[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None, [Query](#fastapi.Query)(description='Account ID filter')\]</code>) – Optional account_id query parameter (required for superadmins).
- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None</code>) – Optional board ID to filter by.
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID) | None</code>) – Optional game ID to filter by.
- **status** (<code>[str](#str) | None</code>) – Optional status to filter by (PENDING, CONFIRMED_CHEAT, etc.).
- **flag_type** (<code>[str](#str) | None</code>) – Optional flag type to filter by (VELOCITY, DUPLICATE, etc.).

**Returns:**

- <code>[list](#list)\[[ScoreFlagResponse](#leadr.scores.api.score_flag_schemas.ScoreFlagResponse)\]</code> – List of ScoreFlagResponse objects matching the filter criteria.

**Raises:**

- <code>400</code> – Superadmin did not provide account_id.
- <code>403</code> – User does not have access to the specified account.

###### `leadr.scores.api.score_flag_routes.router`

```python
router = APIRouter()
```

###### `leadr.scores.api.score_flag_routes.update_score_flag`

```python
update_score_flag(flag_id, request, service, auth)
```

Update a score flag (review or soft-delete).

Allows reviewing a flag (updating status and reviewer decision) or
soft-deleting the flag.

**Parameters:**

- **flag_id** (<code>[ScoreFlagID](./common.md#leadr.common.domain.ids.ScoreFlagID)</code>) – Flag identifier to update.
- **request** (<code>[ScoreFlagUpdateRequest](#leadr.scores.api.score_flag_schemas.ScoreFlagUpdateRequest)</code>) – Update details (status, reviewer_decision, or deleted flag).
- **service** (<code>[ScoreFlagServiceDep](./scores.md#leadr.scores.services.dependencies.ScoreFlagServiceDep)</code>) – Injected score flag service dependency.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.

**Returns:**

- <code>[ScoreFlagResponse](#leadr.scores.api.score_flag_schemas.ScoreFlagResponse)</code> – ScoreFlagResponse with the updated flag details.

**Raises:**

- <code>403</code> – User does not have access to this flag's account.
- <code>404</code> – Flag not found.
- <code>400</code> – Invalid update request.

##### `leadr.scores.api.score_flag_schemas`

API request and response models for score flags.

**Classes:**

- [**ScoreFlagResponse**](#leadr.scores.api.score_flag_schemas.ScoreFlagResponse) – Response model for a score flag.
- [**ScoreFlagUpdateRequest**](#leadr.scores.api.score_flag_schemas.ScoreFlagUpdateRequest) – Request model for updating a score flag (reviewing).

###### `leadr.scores.api.score_flag_schemas.ScoreFlagResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response model for a score flag.

**Functions:**

- [**from_domain**](#leadr.scores.api.score_flag_schemas.ScoreFlagResponse.from_domain) – Convert domain entity to response model.

**Attributes:**

- [**confidence**](#leadr.scores.api.score_flag_schemas.ScoreFlagResponse.confidence) (<code>[str](#str)</code>) –
- [**created_at**](#leadr.scores.api.score_flag_schemas.ScoreFlagResponse.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**flag_type**](#leadr.scores.api.score_flag_schemas.ScoreFlagResponse.flag_type) (<code>[str](#str)</code>) –
- [**id**](#leadr.scores.api.score_flag_schemas.ScoreFlagResponse.id) (<code>[ScoreFlagID](./common.md#leadr.common.domain.ids.ScoreFlagID)</code>) –
- [**metadata**](#leadr.scores.api.score_flag_schemas.ScoreFlagResponse.metadata) (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\]</code>) –
- [**reviewed_at**](#leadr.scores.api.score_flag_schemas.ScoreFlagResponse.reviewed_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**reviewer_decision**](#leadr.scores.api.score_flag_schemas.ScoreFlagResponse.reviewer_decision) (<code>[str](#str) | None</code>) –
- [**reviewer_id**](#leadr.scores.api.score_flag_schemas.ScoreFlagResponse.reviewer_id) (<code>[UserID](./common.md#leadr.common.domain.ids.UserID) | None</code>) –
- [**score_id**](#leadr.scores.api.score_flag_schemas.ScoreFlagResponse.score_id) (<code>[ScoreID](./common.md#leadr.common.domain.ids.ScoreID)</code>) –
- [**status**](#leadr.scores.api.score_flag_schemas.ScoreFlagResponse.status) (<code>[str](#str)</code>) –
- [**updated_at**](#leadr.scores.api.score_flag_schemas.ScoreFlagResponse.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.scores.api.score_flag_schemas.ScoreFlagResponse.confidence`

```python
confidence: str = Field(description='Confidence level of the flag (LOW, MEDIUM, HIGH)')
```

####### `leadr.scores.api.score_flag_schemas.ScoreFlagResponse.created_at`

```python
created_at: datetime = Field(description='Timestamp when the flag was created (UTC)')
```

####### `leadr.scores.api.score_flag_schemas.ScoreFlagResponse.flag_type`

```python
flag_type: str = Field(description='Type of flag (e.g., VELOCITY, DUPLICATE, RATE_LIMIT)')
```

####### `leadr.scores.api.score_flag_schemas.ScoreFlagResponse.from_domain`

```python
from_domain(flag)
```

Convert domain entity to response model.

**Parameters:**

- **flag** (<code>[ScoreFlag](#leadr.scores.domain.anti_cheat.models.ScoreFlag)</code>) – The domain ScoreFlag entity to convert.

**Returns:**

- <code>[ScoreFlagResponse](#leadr.scores.api.score_flag_schemas.ScoreFlagResponse)</code> – ScoreFlagResponse with all fields populated from the domain entity.

####### `leadr.scores.api.score_flag_schemas.ScoreFlagResponse.id`

```python
id: ScoreFlagID = Field(description='Unique identifier for the score flag')
```

####### `leadr.scores.api.score_flag_schemas.ScoreFlagResponse.metadata`

```python
metadata: dict[str, Any] = Field(description='Additional metadata about the flag')
```

####### `leadr.scores.api.score_flag_schemas.ScoreFlagResponse.reviewed_at`

```python
reviewed_at: datetime | None = Field(default=None, description='Timestamp when flag was reviewed, or null')
```

####### `leadr.scores.api.score_flag_schemas.ScoreFlagResponse.reviewer_decision`

```python
reviewer_decision: str | None = Field(default=None, description="Admin's decision/notes, or null")
```

####### `leadr.scores.api.score_flag_schemas.ScoreFlagResponse.reviewer_id`

```python
reviewer_id: UserID | None = Field(default=None, description='ID of the user who reviewed this flag, or null')
```

####### `leadr.scores.api.score_flag_schemas.ScoreFlagResponse.score_id`

```python
score_id: ScoreID = Field(description='ID of the score that was flagged')
```

####### `leadr.scores.api.score_flag_schemas.ScoreFlagResponse.status`

```python
status: str = Field(description='Status: PENDING, CONFIRMED_CHEAT, FALSE_POSITIVE, or DISMISSED')
```

####### `leadr.scores.api.score_flag_schemas.ScoreFlagResponse.updated_at`

```python
updated_at: datetime = Field(description='Timestamp of last update (UTC)')
```

###### `leadr.scores.api.score_flag_schemas.ScoreFlagUpdateRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request model for updating a score flag (reviewing).

**Attributes:**

- [**deleted**](#leadr.scores.api.score_flag_schemas.ScoreFlagUpdateRequest.deleted) (<code>[bool](#bool) | None</code>) –
- [**reviewer_decision**](#leadr.scores.api.score_flag_schemas.ScoreFlagUpdateRequest.reviewer_decision) (<code>[str](#str) | None</code>) –
- [**status**](#leadr.scores.api.score_flag_schemas.ScoreFlagUpdateRequest.status) (<code>[str](#str) | None</code>) –

####### `leadr.scores.api.score_flag_schemas.ScoreFlagUpdateRequest.deleted`

```python
deleted: bool | None = Field(default=None, description='Set to true to soft delete the flag')
```

####### `leadr.scores.api.score_flag_schemas.ScoreFlagUpdateRequest.reviewer_decision`

```python
reviewer_decision: str | None = Field(default=None, description="Admin's decision/notes about the flag")
```

####### `leadr.scores.api.score_flag_schemas.ScoreFlagUpdateRequest.status`

```python
status: str | None = Field(default=None, description='Updated status: PENDING, CONFIRMED_CHEAT, FALSE_POSITIVE, or DISMISSED')
```

##### `leadr.scores.api.score_routes`

API routes for score management.

**Functions:**

- [**create_score_admin**](#leadr.scores.api.score_routes.create_score_admin) – Create a new score (Admin API).
- [**create_score_client**](#leadr.scores.api.score_routes.create_score_client) – Create a new score (Client API).
- [**get_score**](#leadr.scores.api.score_routes.get_score) – Get a score by ID.
- [**handle_list_scores**](#leadr.scores.api.score_routes.handle_list_scores) – Handle list scores logic for both admin and client endpoints.
- [**list_scores_admin**](#leadr.scores.api.score_routes.list_scores_admin) – List scores for an account with optional filters and pagination.
- [**list_scores_client**](#leadr.scores.api.score_routes.list_scores_client) – List scores for an account with optional filters and pagination.
- [**update_score**](#leadr.scores.api.score_routes.update_score) – Update a score.

**Attributes:**

- [**client_router**](#leadr.scores.api.score_routes.client_router) –
- [**router**](#leadr.scores.api.score_routes.router) –

###### `leadr.scores.api.score_routes.client_router`

```python
client_router = APIRouter()
```

###### `leadr.scores.api.score_routes.create_score_admin`

```python
create_score_admin(score_request, request, service, background_tasks, auth)
```

Create a new score (Admin API).

Creates a new score submission for a board. Performs three-level validation:
board exists, board belongs to the specified account, and game matches
the board's game.

For regular admins: account_id is derived from auth, must provide game_id and device_id.
For superadmins: can provide account_id to create scores for any account.

**Parameters:**

- **score_request** (<code>[ScoreCreateRequest](#leadr.scores.api.score_schemas.ScoreCreateRequest)</code>) – Score creation details including board_id, player_name, value,
  and optionally account_id (superadmin only), game_id, device_id.
- **request** (<code>[Request](#fastapi.Request)</code>) – FastAPI request object for accessing geo data.
- **service** (<code>[ScoreServiceDep](./scores.md#leadr.scores.services.dependencies.ScoreServiceDep)</code>) – Injected score service dependency.
- **background_tasks** (<code>[BackgroundTasks](#fastapi.BackgroundTasks)</code>) – FastAPI background tasks for async metadata updates.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Admin authentication context.

**Returns:**

- <code>[ScoreResponse](#leadr.scores.api.score_schemas.ScoreResponse)</code> – ScoreResponse with the created score including auto-generated ID and timestamps.

**Raises:**

- <code>403</code> – Non-superadmin tries to specify account_id, or access denied.
- <code>400</code> – Missing required fields (game_id or device_id).
- <code>404</code> – Account, game, board, or device not found.
- <code>400</code> – Validation failed (board doesn't belong to account, or game doesn't
  match board's game).

###### `leadr.scores.api.score_routes.create_score_client`

```python
create_score_client(score_request, request, service, background_tasks, auth)
```

Create a new score (Client API).

Creates a new score submission for a board. All IDs (account_id, game_id, device_id)
are automatically derived from the authenticated device session.

**Parameters:**

- **score_request** (<code>[ScoreClientCreateRequest](#leadr.scores.api.score_schemas.ScoreClientCreateRequest)</code>) – Score creation details including board_id, player_name, and value.
- **request** (<code>[Request](#fastapi.Request)</code>) – FastAPI request object for accessing geo data.
- **service** (<code>[ScoreServiceDep](./scores.md#leadr.scores.services.dependencies.ScoreServiceDep)</code>) – Injected score service dependency.
- **background_tasks** (<code>[BackgroundTasks](#fastapi.BackgroundTasks)</code>) – FastAPI background tasks for async metadata updates.
- **auth** (<code>[ClientAuthContextWithNonceDep](./auth.md#leadr.auth.dependencies.ClientAuthContextWithNonceDep)</code>) – Client authentication context with device info.

**Returns:**

- <code>[ScoreClientResponse](#leadr.scores.api.score_schemas.ScoreClientResponse)</code> – ScoreClientResponse with the created score (excludes device_id).

**Raises:**

- <code>404</code> – Board not found.
- <code>400</code> – Validation failed (board doesn't belong to account, or game doesn't
  match board's game).

###### `leadr.scores.api.score_routes.get_score`

```python
get_score(score_id, service, auth)
```

Get a score by ID.

**Parameters:**

- **score_id** (<code>[ScoreID](./common.md#leadr.common.domain.ids.ScoreID)</code>) – Score identifier to retrieve.
- **service** (<code>[ScoreServiceDep](./scores.md#leadr.scores.services.dependencies.ScoreServiceDep)</code>) – Injected score service dependency.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.

**Returns:**

- <code>[ScoreResponse](#leadr.scores.api.score_schemas.ScoreResponse)</code> – ScoreResponse with the score details.

**Raises:**

- <code>403</code> – User does not have access to this score's account.
- <code>404</code> – Score not found or soft-deleted.

###### `leadr.scores.api.score_routes.handle_list_scores`

```python
handle_list_scores(auth, service, pagination, account_id, board_id, game_id, device_id)
```

Handle list scores logic for both admin and client endpoints.

This shared handler implements the core list scores functionality and returns
different response models based on the authentication type:

- Admin auth: Returns ScoreResponse with device_id and geo fields
- Client auth: Returns ScoreClientResponse without device_id and geo fields

**Parameters:**

- **auth** (<code>[AuthContext](./auth.md#leadr.auth.dependencies.AuthContext)</code>) – Authentication context (admin or client).
- **service** (<code>[ScoreService](#leadr.scores.services.score_service.ScoreService)</code>) – Score service for data access.
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (cursor, limit, sort).
- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – Optional account ID filter.
- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None</code>) – Optional board ID filter.
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID) | None</code>) – Optional game ID filter.
- **device_id** (<code>[DeviceID](./common.md#leadr.common.domain.ids.DeviceID) | None</code>) – Optional device ID filter.

**Returns:**

- <code>[PaginatedResponse](./common.md#leadr.common.api.pagination.PaginatedResponse)\[[ScoreResponse](#leadr.scores.api.score_schemas.ScoreResponse)\] | [PaginatedResponse](./common.md#leadr.common.api.pagination.PaginatedResponse)\[[ScoreClientResponse](#leadr.scores.api.score_schemas.ScoreClientResponse)\]</code> – PaginatedResponse with scores and appropriate response model based on auth type.

**Raises:**

- <code>[HTTPException](#fastapi.HTTPException)</code> – 400 if cursor is invalid or sort field is invalid.

###### `leadr.scores.api.score_routes.list_scores_admin`

```python
list_scores_admin(auth, service, pagination, account_id=None, board_id=None, game_id=None, device_id=None)
```

List scores for an account with optional filters and pagination.

Returns paginated scores for the specified account, with optional
filtering by board, game, or device. Supports cursor-based pagination
with bidirectional navigation and custom sorting.

For regular admin users, account_id is automatically derived from their API key.
For superadmins, account_id must be explicitly provided as a query parameter.

Pagination:

- Default: 20 items per page, sorted by created_at:desc,id:asc
- Custom sort: Use ?sort=value:desc,created_at:asc
- Valid sort fields: id, value, player_name, filter_timezone, filter_country,
  filter_city, created_at, updated_at
- Navigation: Use next_cursor/prev_cursor from response

<details class="example" open markdown="1">
<summary>Example</summary>

GET /v1/scores?board_id=brd_123&limit=50&sort=value:desc,created_at:asc

</details>

**Parameters:**

- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.
- **service** (<code>[ScoreServiceDep](./scores.md#leadr.scores.services.dependencies.ScoreServiceDep)</code>) – Injected score service dependency.
- **pagination** (<code>[Annotated](#typing.Annotated)\[[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams), [Depends](#fastapi.Depends)()\]</code>) – Pagination parameters (cursor, limit, sort).
- **account_id** (<code>[Annotated](#typing.Annotated)\[[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None, [Query](#fastapi.Query)(description='Account ID filter')\]</code>) – Optional account_id query parameter (required for superadmins).
- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None</code>) – Optional board ID to filter by.
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID) | None</code>) – Optional game ID to filter by.
- **device_id** (<code>[DeviceID](./common.md#leadr.common.domain.ids.DeviceID) | None</code>) – Optional device ID to filter by.

**Returns:**

- <code>[PaginatedResponse](./common.md#leadr.common.api.pagination.PaginatedResponse)\[[ScoreResponse](#leadr.scores.api.score_schemas.ScoreResponse)\]</code> – PaginatedResponse with scores and pagination metadata.

**Raises:**

- <code>400</code> – Invalid cursor, sort field, or cursor state mismatch.
- <code>400</code> – Superadmin did not provide account_id.
- <code>403</code> – User does not have access to the specified account.

###### `leadr.scores.api.score_routes.list_scores_client`

```python
list_scores_client(auth, service, pagination, board_id=None)
```

List scores for an account with optional filters and pagination.

Returns paginated scores for the specified account, with optional
filtering by board. Supports cursor-based pagination
with bidirectional navigation and custom sorting.

Pagination:

- Default: 20 items per page, sorted by created_at:desc,id:asc
- Custom sort: Use ?sort=value:desc,created_at:asc
- Valid sort fields: id, value, player_name, filter_timezone, filter_country,
  filter_city, created_at, updated_at
- Navigation: Use next_cursor/prev_cursor from response

<details class="example" open markdown="1">
<summary>Example</summary>

GET /v1/scores?board_id=brd_123&limit=50&sort=value:desc,created_at:asc

</details>

**Parameters:**

- **auth** (<code>[ClientAuthContextDep](./auth.md#leadr.auth.dependencies.ClientAuthContextDep)</code>) – Authentication context with user info.
- **service** (<code>[ScoreServiceDep](./scores.md#leadr.scores.services.dependencies.ScoreServiceDep)</code>) – Injected score service dependency.
- **pagination** (<code>[Annotated](#typing.Annotated)\[[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams), [Depends](#fastapi.Depends)()\]</code>) – Pagination parameters (cursor, limit, sort).
- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None</code>) – Optional board ID to filter by.

**Returns:**

- <code>[PaginatedResponse](./common.md#leadr.common.api.pagination.PaginatedResponse)\[[ScoreClientResponse](#leadr.scores.api.score_schemas.ScoreClientResponse)\]</code> – PaginatedResponse with scores and pagination metadata.

**Raises:**

- <code>400</code> – Invalid cursor, sort field, or cursor state mismatch.
- <code>400</code> – Superadmin did not provide account_id.
- <code>403</code> – User does not have access to the specified account.

###### `leadr.scores.api.score_routes.router`

```python
router = APIRouter()
```

###### `leadr.scores.api.score_routes.update_score`

```python
update_score(score_id, request, service, auth)
```

Update a score.

Supports partial updates of score fields. Any field not provided will
remain unchanged. Set deleted: true to soft delete the score.

**Parameters:**

- **score_id** (<code>[ScoreID](./common.md#leadr.common.domain.ids.ScoreID)</code>) – Score identifier to update.
- **request** (<code>[ScoreUpdateRequest](#leadr.scores.api.score_schemas.ScoreUpdateRequest)</code>) – Score update details with optional fields to modify.
- **service** (<code>[ScoreServiceDep](./scores.md#leadr.scores.services.dependencies.ScoreServiceDep)</code>) – Injected score service dependency.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.

**Returns:**

- <code>[ScoreResponse](#leadr.scores.api.score_schemas.ScoreResponse)</code> – ScoreResponse with the updated score details.

**Raises:**

- <code>403</code> – User does not have access to this score's account.
- <code>404</code> – Score not found or already soft-deleted.

##### `leadr.scores.api.score_schemas`

API request and response models for scores.

**Classes:**

- [**ScoreClientCreateRequest**](#leadr.scores.api.score_schemas.ScoreClientCreateRequest) – Request model for creating a score (Client API).
- [**ScoreClientResponse**](#leadr.scores.api.score_schemas.ScoreClientResponse) – Response model for a score (client API - excludes device_id and geo fields).
- [**ScoreCreateRequest**](#leadr.scores.api.score_schemas.ScoreCreateRequest) – Request model for creating a score (Admin API).
- [**ScoreCreateRequestBase**](#leadr.scores.api.score_schemas.ScoreCreateRequestBase) – Base request model for score creation with common fields.
- [**ScoreResponse**](#leadr.scores.api.score_schemas.ScoreResponse) – Response model for a score.
- [**ScoreUpdateRequest**](#leadr.scores.api.score_schemas.ScoreUpdateRequest) – Request model for updating a score.

###### `leadr.scores.api.score_schemas.ScoreClientCreateRequest`

Bases: <code>[ScoreCreateRequestBase](#leadr.scores.api.score_schemas.ScoreCreateRequestBase)</code>

Request model for creating a score (Client API).

For client authentication, account_id, game_id, and device_id are automatically
derived from the authenticated device session. Only game-specific fields are required.

Note: Timezone, country, and city are automatically populated from the client's
IP address via GeoIP middleware.

**Functions:**

- [**validate_metadata_size**](#leadr.scores.api.score_schemas.ScoreClientCreateRequest.validate_metadata_size) – Validate that metadata does not exceed size limit.

**Attributes:**

- [**board_id**](#leadr.scores.api.score_schemas.ScoreClientCreateRequest.board_id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) –
- [**metadata**](#leadr.scores.api.score_schemas.ScoreClientCreateRequest.metadata) (<code>[Any](#typing.Any) | None</code>) –
- [**player_name**](#leadr.scores.api.score_schemas.ScoreClientCreateRequest.player_name) (<code>[str](#str)</code>) –
- [**value**](#leadr.scores.api.score_schemas.ScoreClientCreateRequest.value) (<code>[float](#float)</code>) –
- [**value_display**](#leadr.scores.api.score_schemas.ScoreClientCreateRequest.value_display) (<code>[str](#str) | None</code>) –

###### `leadr.scores.api.score_schemas.ScoreClientResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response model for a score (client API - excludes device_id and geo fields).

**Functions:**

- [**from_domain**](#leadr.scores.api.score_schemas.ScoreClientResponse.from_domain) – Convert domain entity to client response model (without device_id or geo fields).

**Attributes:**

- [**account_id**](#leadr.scores.api.score_schemas.ScoreClientResponse.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**board_id**](#leadr.scores.api.score_schemas.ScoreClientResponse.board_id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) –
- [**created_at**](#leadr.scores.api.score_schemas.ScoreClientResponse.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**game_id**](#leadr.scores.api.score_schemas.ScoreClientResponse.game_id) (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) –
- [**id**](#leadr.scores.api.score_schemas.ScoreClientResponse.id) (<code>[ScoreID](./common.md#leadr.common.domain.ids.ScoreID)</code>) –
- [**metadata**](#leadr.scores.api.score_schemas.ScoreClientResponse.metadata) (<code>[Any](#typing.Any) | None</code>) –
- [**player_name**](#leadr.scores.api.score_schemas.ScoreClientResponse.player_name) (<code>[str](#str)</code>) –
- [**updated_at**](#leadr.scores.api.score_schemas.ScoreClientResponse.updated_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**value**](#leadr.scores.api.score_schemas.ScoreClientResponse.value) (<code>[float](#float)</code>) –
- [**value_display**](#leadr.scores.api.score_schemas.ScoreClientResponse.value_display) (<code>[str](#str) | None</code>) –

####### `leadr.scores.api.score_schemas.ScoreClientResponse.account_id`

```python
account_id: AccountID = Field(description='ID of the account this score belongs to')
```

####### `leadr.scores.api.score_schemas.ScoreClientResponse.board_id`

```python
board_id: BoardID = Field(description='ID of the board this score belongs to')
```

####### `leadr.scores.api.score_schemas.ScoreClientResponse.created_at`

```python
created_at: datetime = Field(description='Timestamp when the score was created (UTC)')
```

####### `leadr.scores.api.score_schemas.ScoreClientResponse.from_domain`

```python
from_domain(score)
```

Convert domain entity to client response model (without device_id or geo fields).

**Parameters:**

- **score** (<code>[Score](./scores.md#leadr.scores.domain.score.Score)</code>) – The domain Score entity to convert.

**Returns:**

- <code>[ScoreClientResponse](#leadr.scores.api.score_schemas.ScoreClientResponse)</code> – ScoreClientResponse with all fields except device_id, timezone, country, and city.

####### `leadr.scores.api.score_schemas.ScoreClientResponse.game_id`

```python
game_id: GameID = Field(description='ID of the game this score belongs to')
```

####### `leadr.scores.api.score_schemas.ScoreClientResponse.id`

```python
id: ScoreID = Field(description='Unique identifier for the score')
```

####### `leadr.scores.api.score_schemas.ScoreClientResponse.metadata`

```python
metadata: Any | None = Field(default=None, description='Game-specific metadata, or null')
```

####### `leadr.scores.api.score_schemas.ScoreClientResponse.player_name`

```python
player_name: str = Field(description='Display name of the player')
```

####### `leadr.scores.api.score_schemas.ScoreClientResponse.updated_at`

```python
updated_at: datetime = Field(description='Timestamp of last update (UTC)')
```

####### `leadr.scores.api.score_schemas.ScoreClientResponse.value`

```python
value: float = Field(description='Numeric value of the score')
```

####### `leadr.scores.api.score_schemas.ScoreClientResponse.value_display`

```python
value_display: str | None = Field(default=None, description='Formatted display string, or null')
```

###### `leadr.scores.api.score_schemas.ScoreCreateRequest`

Bases: <code>[ScoreCreateRequestBase](#leadr.scores.api.score_schemas.ScoreCreateRequestBase)</code>

Request model for creating a score (Admin API).

Note: Timezone, country, and city are automatically populated from the client's
IP address via GeoIP middleware but can be overriden by admins in the request body.

For regular admins: account_id is derived from auth context, must provide game_id and
device_id. For superadmins: can provide account_id to create scores for any account,
must provide game_id and device_id.

**Functions:**

- [**validate_metadata_size**](#leadr.scores.api.score_schemas.ScoreCreateRequest.validate_metadata_size) – Validate that metadata does not exceed size limit.

**Attributes:**

- [**account_id**](#leadr.scores.api.score_schemas.ScoreCreateRequest.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) –
- [**board_id**](#leadr.scores.api.score_schemas.ScoreCreateRequest.board_id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) –
- [**city**](#leadr.scores.api.score_schemas.ScoreCreateRequest.city) (<code>[str](#str) | None</code>) –
- [**country**](#leadr.scores.api.score_schemas.ScoreCreateRequest.country) (<code>[str](#str) | None</code>) –
- [**device_id**](#leadr.scores.api.score_schemas.ScoreCreateRequest.device_id) (<code>[DeviceID](./common.md#leadr.common.domain.ids.DeviceID)</code>) –
- [**game_id**](#leadr.scores.api.score_schemas.ScoreCreateRequest.game_id) (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) –
- [**metadata**](#leadr.scores.api.score_schemas.ScoreCreateRequest.metadata) (<code>[Any](#typing.Any) | None</code>) –
- [**player_name**](#leadr.scores.api.score_schemas.ScoreCreateRequest.player_name) (<code>[str](#str)</code>) –
- [**timezone**](#leadr.scores.api.score_schemas.ScoreCreateRequest.timezone) (<code>[str](#str) | None</code>) –
- [**value**](#leadr.scores.api.score_schemas.ScoreCreateRequest.value) (<code>[float](#float)</code>) –
- [**value_display**](#leadr.scores.api.score_schemas.ScoreCreateRequest.value_display) (<code>[str](#str) | None</code>) –

####### `leadr.scores.api.score_schemas.ScoreCreateRequest.account_id`

```python
account_id: AccountID | None = Field(default=None, description='ID of the account (only for superadmins, regular admins use their auth account)')
```

####### `leadr.scores.api.score_schemas.ScoreCreateRequest.board_id`

```python
board_id: BoardID = Field(description='ID of the board this score belongs to')
```

####### `leadr.scores.api.score_schemas.ScoreCreateRequest.city`

```python
city: str | None = Field(default=None, description='Optional override of GeoIP metadata')
```

####### `leadr.scores.api.score_schemas.ScoreCreateRequest.country`

```python
country: str | None = Field(default=None, description='Optional override of GeoIP metadata')
```

####### `leadr.scores.api.score_schemas.ScoreCreateRequest.device_id`

```python
device_id: DeviceID = Field(description='ID of the device that submitted this score (required for admin API)')
```

####### `leadr.scores.api.score_schemas.ScoreCreateRequest.game_id`

```python
game_id: GameID = Field(description='ID of the game this score belongs to (required for admin API)')
```

####### `leadr.scores.api.score_schemas.ScoreCreateRequest.metadata`

```python
metadata: Any | None = Field(default=None, description='Optional JSON metadata for game-specific data (max 1KB)')
```

####### `leadr.scores.api.score_schemas.ScoreCreateRequest.player_name`

```python
player_name: str = Field(description='Display name of the player')
```

####### `leadr.scores.api.score_schemas.ScoreCreateRequest.timezone`

```python
timezone: str | None = Field(default=None, description='Optional override of GeoIP metadata')
```

####### `leadr.scores.api.score_schemas.ScoreCreateRequest.validate_metadata_size`

```python
validate_metadata_size(v)
```

Validate that metadata does not exceed size limit.

####### `leadr.scores.api.score_schemas.ScoreCreateRequest.value`

```python
value: float = Field(description='Numeric value of the score for sorting/comparison')
```

####### `leadr.scores.api.score_schemas.ScoreCreateRequest.value_display`

```python
value_display: str | None = Field(default=None, description="Optional formatted display string (e.g., '1:23.45', '1,234 points')")
```

###### `leadr.scores.api.score_schemas.ScoreCreateRequestBase`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Base request model for score creation with common fields.

**Functions:**

- [**validate_metadata_size**](#leadr.scores.api.score_schemas.ScoreCreateRequestBase.validate_metadata_size) – Validate that metadata does not exceed size limit.

**Attributes:**

- [**board_id**](#leadr.scores.api.score_schemas.ScoreCreateRequestBase.board_id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) –
- [**metadata**](#leadr.scores.api.score_schemas.ScoreCreateRequestBase.metadata) (<code>[Any](#typing.Any) | None</code>) –
- [**player_name**](#leadr.scores.api.score_schemas.ScoreCreateRequestBase.player_name) (<code>[str](#str)</code>) –
- [**value**](#leadr.scores.api.score_schemas.ScoreCreateRequestBase.value) (<code>[float](#float)</code>) –
- [**value_display**](#leadr.scores.api.score_schemas.ScoreCreateRequestBase.value_display) (<code>[str](#str) | None</code>) –

####### `leadr.scores.api.score_schemas.ScoreCreateRequestBase.board_id`

```python
board_id: BoardID = Field(description='ID of the board this score belongs to')
```

####### `leadr.scores.api.score_schemas.ScoreCreateRequestBase.metadata`

```python
metadata: Any | None = Field(default=None, description='Optional JSON metadata for game-specific data (max 1KB)')
```

####### `leadr.scores.api.score_schemas.ScoreCreateRequestBase.player_name`

```python
player_name: str = Field(description='Display name of the player')
```

####### `leadr.scores.api.score_schemas.ScoreCreateRequestBase.validate_metadata_size`

```python
validate_metadata_size(v)
```

Validate that metadata does not exceed size limit.

####### `leadr.scores.api.score_schemas.ScoreCreateRequestBase.value`

```python
value: float = Field(description='Numeric value of the score for sorting/comparison')
```

####### `leadr.scores.api.score_schemas.ScoreCreateRequestBase.value_display`

```python
value_display: str | None = Field(default=None, description="Optional formatted display string (e.g., '1:23.45', '1,234 points')")
```

###### `leadr.scores.api.score_schemas.ScoreResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response model for a score.

**Functions:**

- [**from_domain**](#leadr.scores.api.score_schemas.ScoreResponse.from_domain) – Convert domain entity to response model.

**Attributes:**

- [**account_id**](#leadr.scores.api.score_schemas.ScoreResponse.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**board_id**](#leadr.scores.api.score_schemas.ScoreResponse.board_id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) –
- [**city**](#leadr.scores.api.score_schemas.ScoreResponse.city) (<code>[str](#str) | None</code>) –
- [**country**](#leadr.scores.api.score_schemas.ScoreResponse.country) (<code>[str](#str) | None</code>) –
- [**created_at**](#leadr.scores.api.score_schemas.ScoreResponse.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**device_id**](#leadr.scores.api.score_schemas.ScoreResponse.device_id) (<code>[DeviceID](./common.md#leadr.common.domain.ids.DeviceID)</code>) –
- [**game_id**](#leadr.scores.api.score_schemas.ScoreResponse.game_id) (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) –
- [**id**](#leadr.scores.api.score_schemas.ScoreResponse.id) (<code>[ScoreID](./common.md#leadr.common.domain.ids.ScoreID)</code>) –
- [**metadata**](#leadr.scores.api.score_schemas.ScoreResponse.metadata) (<code>[Any](#typing.Any) | None</code>) –
- [**player_name**](#leadr.scores.api.score_schemas.ScoreResponse.player_name) (<code>[str](#str)</code>) –
- [**timezone**](#leadr.scores.api.score_schemas.ScoreResponse.timezone) (<code>[str](#str) | None</code>) –
- [**updated_at**](#leadr.scores.api.score_schemas.ScoreResponse.updated_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**value**](#leadr.scores.api.score_schemas.ScoreResponse.value) (<code>[float](#float)</code>) –
- [**value_display**](#leadr.scores.api.score_schemas.ScoreResponse.value_display) (<code>[str](#str) | None</code>) –

####### `leadr.scores.api.score_schemas.ScoreResponse.account_id`

```python
account_id: AccountID = Field(description='ID of the account this score belongs to')
```

####### `leadr.scores.api.score_schemas.ScoreResponse.board_id`

```python
board_id: BoardID = Field(description='ID of the board this score belongs to')
```

####### `leadr.scores.api.score_schemas.ScoreResponse.city`

```python
city: str | None = Field(default=None, description='City for categorization, or null')
```

####### `leadr.scores.api.score_schemas.ScoreResponse.country`

```python
country: str | None = Field(default=None, description='Country for categorization, or null')
```

####### `leadr.scores.api.score_schemas.ScoreResponse.created_at`

```python
created_at: datetime = Field(description='Timestamp when the score was created (UTC)')
```

####### `leadr.scores.api.score_schemas.ScoreResponse.device_id`

```python
device_id: DeviceID = Field(description='ID of the device that submitted this score')
```

####### `leadr.scores.api.score_schemas.ScoreResponse.from_domain`

```python
from_domain(score)
```

Convert domain entity to response model.

**Parameters:**

- **score** (<code>[Score](./scores.md#leadr.scores.domain.score.Score)</code>) – The domain Score entity to convert.

**Returns:**

- <code>[ScoreResponse](#leadr.scores.api.score_schemas.ScoreResponse)</code> – ScoreResponse with all fields populated from the domain entity.

####### `leadr.scores.api.score_schemas.ScoreResponse.game_id`

```python
game_id: GameID = Field(description='ID of the game this score belongs to')
```

####### `leadr.scores.api.score_schemas.ScoreResponse.id`

```python
id: ScoreID = Field(description='Unique identifier for the score')
```

####### `leadr.scores.api.score_schemas.ScoreResponse.metadata`

```python
metadata: Any | None = Field(default=None, description='Game-specific metadata, or null')
```

####### `leadr.scores.api.score_schemas.ScoreResponse.player_name`

```python
player_name: str = Field(description='Display name of the player')
```

####### `leadr.scores.api.score_schemas.ScoreResponse.timezone`

```python
timezone: str | None = Field(default=None, description='Timezone for categorization, or null')
```

####### `leadr.scores.api.score_schemas.ScoreResponse.updated_at`

```python
updated_at: datetime = Field(description='Timestamp of last update (UTC)')
```

####### `leadr.scores.api.score_schemas.ScoreResponse.value`

```python
value: float = Field(description='Numeric value of the score')
```

####### `leadr.scores.api.score_schemas.ScoreResponse.value_display`

```python
value_display: str | None = Field(default=None, description='Formatted display string, or null')
```

###### `leadr.scores.api.score_schemas.ScoreUpdateRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request model for updating a score.

**Functions:**

- [**validate_metadata_size**](#leadr.scores.api.score_schemas.ScoreUpdateRequest.validate_metadata_size) – Validate that metadata does not exceed size limit.

**Attributes:**

- [**city**](#leadr.scores.api.score_schemas.ScoreUpdateRequest.city) (<code>[str](#str) | None</code>) –
- [**country**](#leadr.scores.api.score_schemas.ScoreUpdateRequest.country) (<code>[str](#str) | None</code>) –
- [**deleted**](#leadr.scores.api.score_schemas.ScoreUpdateRequest.deleted) (<code>[bool](#bool) | None</code>) –
- [**metadata**](#leadr.scores.api.score_schemas.ScoreUpdateRequest.metadata) (<code>[Any](#typing.Any) | None</code>) –
- [**player_name**](#leadr.scores.api.score_schemas.ScoreUpdateRequest.player_name) (<code>[str](#str) | None</code>) –
- [**timezone**](#leadr.scores.api.score_schemas.ScoreUpdateRequest.timezone) (<code>[str](#str) | None</code>) –
- [**value**](#leadr.scores.api.score_schemas.ScoreUpdateRequest.value) (<code>[float](#float) | None</code>) –
- [**value_display**](#leadr.scores.api.score_schemas.ScoreUpdateRequest.value_display) (<code>[str](#str) | None</code>) –

####### `leadr.scores.api.score_schemas.ScoreUpdateRequest.city`

```python
city: str | None = Field(default=None, description='Updated city')
```

####### `leadr.scores.api.score_schemas.ScoreUpdateRequest.country`

```python
country: str | None = Field(default=None, description='Updated country')
```

####### `leadr.scores.api.score_schemas.ScoreUpdateRequest.deleted`

```python
deleted: bool | None = Field(default=None, description='Set to true to soft delete the score')
```

####### `leadr.scores.api.score_schemas.ScoreUpdateRequest.metadata`

```python
metadata: Any | None = Field(default=None, description='Updated metadata')
```

####### `leadr.scores.api.score_schemas.ScoreUpdateRequest.player_name`

```python
player_name: str | None = Field(default=None, description='Updated player name')
```

####### `leadr.scores.api.score_schemas.ScoreUpdateRequest.timezone`

```python
timezone: str | None = Field(default=None, description='Updated timezone')
```

####### `leadr.scores.api.score_schemas.ScoreUpdateRequest.validate_metadata_size`

```python
validate_metadata_size(v)
```

Validate that metadata does not exceed size limit.

####### `leadr.scores.api.score_schemas.ScoreUpdateRequest.value`

```python
value: float | None = Field(default=None, description='Updated score value')
```

####### `leadr.scores.api.score_schemas.ScoreUpdateRequest.value_display`

```python
value_display: str | None = Field(default=None, description='Updated display string')
```

##### `leadr.scores.api.score_submission_meta_routes`

API routes for score submission metadata management.

**Functions:**

- [**get_submission_meta**](#leadr.scores.api.score_submission_meta_routes.get_submission_meta) – Get score submission metadata by ID.
- [**list_submission_meta**](#leadr.scores.api.score_submission_meta_routes.list_submission_meta) – List score submission metadata for an account with optional filters.

**Attributes:**

- [**router**](#leadr.scores.api.score_submission_meta_routes.router) –

###### `leadr.scores.api.score_submission_meta_routes.get_submission_meta`

```python
get_submission_meta(meta_id, service, auth)
```

Get score submission metadata by ID.

**Parameters:**

- **meta_id** (<code>[ScoreSubmissionMetaID](./common.md#leadr.common.domain.ids.ScoreSubmissionMetaID)</code>) – Submission metadata identifier to retrieve.
- **service** (<code>[ScoreSubmissionMetaServiceDep](./scores.md#leadr.scores.services.dependencies.ScoreSubmissionMetaServiceDep)</code>) – Injected submission metadata service dependency.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.

**Returns:**

- <code>[ScoreSubmissionMetaResponse](#leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse)</code> – ScoreSubmissionMetaResponse with the submission metadata details.

**Raises:**

- <code>403</code> – User does not have access to this metadata's account.
- <code>404</code> – Submission metadata not found or soft-deleted.

###### `leadr.scores.api.score_submission_meta_routes.list_submission_meta`

```python
list_submission_meta(auth, service, account_id=None, board_id=None, device_id=None)
```

List score submission metadata for an account with optional filters.

Returns all non-deleted submission metadata for the specified account, with optional
filtering by board or device.

For regular users, account_id is automatically derived from their API key.
For superadmins, account_id must be explicitly provided as a query parameter.

**Parameters:**

- **auth** (<code>[AdminAuthContextWithAccountIDDep](./auth.md#leadr.auth.dependencies.AdminAuthContextWithAccountIDDep)</code>) – Authentication context with user info.
- **service** (<code>[ScoreSubmissionMetaServiceDep](./scores.md#leadr.scores.services.dependencies.ScoreSubmissionMetaServiceDep)</code>) – Injected submission metadata service dependency.
- **account_id** (<code>[Annotated](#typing.Annotated)\[[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None, [Query](#fastapi.Query)(description='Account ID filter')\]</code>) – Optional account_id query parameter (required for superadmins).
- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None</code>) – Optional board ID to filter by.
- **device_id** (<code>[DeviceID](./common.md#leadr.common.domain.ids.DeviceID) | None</code>) – Optional device ID to filter by.

**Returns:**

- <code>[list](#list)\[[ScoreSubmissionMetaResponse](#leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse)\]</code> – List of ScoreSubmissionMetaResponse objects matching the filter criteria.

**Raises:**

- <code>400</code> – Superadmin did not provide account_id.
- <code>403</code> – User does not have access to the specified account.

###### `leadr.scores.api.score_submission_meta_routes.router`

```python
router = APIRouter()
```

##### `leadr.scores.api.score_submission_meta_schemas`

API schemas for score submission metadata.

**Classes:**

- [**ScoreSubmissionMetaResponse**](#leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse) – Response model for score submission metadata.

###### `leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response model for score submission metadata.

**Functions:**

- [**from_domain**](#leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse.from_domain) – Convert domain entity to API response.

**Attributes:**

- [**board_id**](#leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse.board_id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) –
- [**created_at**](#leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**device_id**](#leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse.device_id) (<code>[DeviceID](./common.md#leadr.common.domain.ids.DeviceID)</code>) –
- [**id**](#leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse.id) (<code>[ScoreSubmissionMetaID](./common.md#leadr.common.domain.ids.ScoreSubmissionMetaID)</code>) –
- [**last_score_value**](#leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse.last_score_value) (<code>[float](#float) | None</code>) –
- [**last_submission_at**](#leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse.last_submission_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**score_id**](#leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse.score_id) (<code>[ScoreID](./common.md#leadr.common.domain.ids.ScoreID)</code>) –
- [**submission_count**](#leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse.submission_count) (<code>[int](#int)</code>) –
- [**updated_at**](#leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse.board_id`

```python
board_id: BoardID
```

####### `leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse.created_at`

```python
created_at: datetime
```

####### `leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse.device_id`

```python
device_id: DeviceID
```

####### `leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse.from_domain`

```python
from_domain(meta)
```

Convert domain entity to API response.

####### `leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse.id`

```python
id: ScoreSubmissionMetaID
```

####### `leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse.last_score_value`

```python
last_score_value: float | None
```

####### `leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse.last_submission_at`

```python
last_submission_at: datetime
```

####### `leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse.score_id`

```python
score_id: ScoreID
```

####### `leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse.submission_count`

```python
submission_count: int
```

####### `leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse.updated_at`

```python
updated_at: datetime
```

#### `leadr.scores.domain`

**Modules:**

- [**anti_cheat**](#leadr.scores.domain.anti_cheat) – Anti-cheat domain models and enums.
- [**score**](./scores.md#leadr.scores.domain.score) – Score domain entity.

##### `leadr.scores.domain.anti_cheat`

Anti-cheat domain models and enums.

**Modules:**

- [**enums**](#leadr.scores.domain.anti_cheat.enums) – Anti-cheat enums for flag types, confidence levels, and actions.
- [**models**](#leadr.scores.domain.anti_cheat.models) – Anti-cheat domain models.

**Classes:**

- [**AntiCheatResult**](#leadr.scores.domain.anti_cheat.AntiCheatResult) – Result of anti-cheat analysis on a score submission.
- [**FlagAction**](#leadr.scores.domain.anti_cheat.FlagAction) – Action to take based on anti-cheat analysis.
- [**FlagConfidence**](#leadr.scores.domain.anti_cheat.FlagConfidence) – Confidence level for anti-cheat detection.
- [**FlagType**](#leadr.scores.domain.anti_cheat.FlagType) – Type of anti-cheat flag detected.
- [**ScoreFlag**](#leadr.scores.domain.anti_cheat.ScoreFlag) – Record of an anti-cheat flag raised for a score submission.
- [**ScoreSubmissionMeta**](#leadr.scores.domain.anti_cheat.ScoreSubmissionMeta) – Metadata tracking submission history for anti-cheat analysis.
- [**TrustTier**](#leadr.scores.domain.anti_cheat.TrustTier) – Trust tier for devices/users, determining anti-cheat thresholds.

###### `leadr.scores.domain.anti_cheat.AntiCheatResult`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Result of anti-cheat analysis on a score submission.

This is a value object that encapsulates the decision made by the anti-cheat
system. It indicates whether to accept, flag, or reject a score submission,
along with the reasoning and supporting metadata.

**Attributes:**

- [**action**](#leadr.scores.domain.anti_cheat.AntiCheatResult.action) (<code>[FlagAction](#leadr.scores.domain.anti_cheat.enums.FlagAction)</code>) –
- [**confidence**](#leadr.scores.domain.anti_cheat.AntiCheatResult.confidence) (<code>[FlagConfidence](#leadr.scores.domain.anti_cheat.enums.FlagConfidence) | None</code>) –
- [**flag_type**](#leadr.scores.domain.anti_cheat.AntiCheatResult.flag_type) (<code>[FlagType](#leadr.scores.domain.anti_cheat.enums.FlagType) | None</code>) –
- [**metadata**](#leadr.scores.domain.anti_cheat.AntiCheatResult.metadata) (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\] | None</code>) –
- [**model_config**](#leadr.scores.domain.anti_cheat.AntiCheatResult.model_config) –
- [**reason**](#leadr.scores.domain.anti_cheat.AntiCheatResult.reason) (<code>[str](#str) | None</code>) –

####### `leadr.scores.domain.anti_cheat.AntiCheatResult.action`

```python
action: FlagAction = Field(description='Action to take (ACCEPT/FLAG/REJECT)')
```

####### `leadr.scores.domain.anti_cheat.AntiCheatResult.confidence`

```python
confidence: FlagConfidence | None = Field(default=None, description='Confidence level of detection (if flagged/rejected)')
```

####### `leadr.scores.domain.anti_cheat.AntiCheatResult.flag_type`

```python
flag_type: FlagType | None = Field(default=None, description='Type of flag detected (if flagged/rejected)')
```

####### `leadr.scores.domain.anti_cheat.AntiCheatResult.metadata`

```python
metadata: dict[str, Any] | None = Field(default=None, description='Additional context and data supporting the decision')
```

####### `leadr.scores.domain.anti_cheat.AntiCheatResult.model_config`

```python
model_config = {'frozen': True}
```

####### `leadr.scores.domain.anti_cheat.AntiCheatResult.reason`

```python
reason: str | None = Field(default=None, description='Human-readable reason for the action')
```

###### `leadr.scores.domain.anti_cheat.FlagAction`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Action to take based on anti-cheat analysis.

Determines how the score submission should be handled.

**Attributes:**

- [**ACCEPT**](#leadr.scores.domain.anti_cheat.FlagAction.ACCEPT) – Accept the score submission without any flags.
- [**FLAG**](#leadr.scores.domain.anti_cheat.FlagAction.FLAG) – Accept the score but flag it for manual review.
- [**REJECT**](#leadr.scores.domain.anti_cheat.FlagAction.REJECT) – Reject the score submission (do not save to database).

####### `leadr.scores.domain.anti_cheat.FlagAction.ACCEPT`

```python
ACCEPT = 'ACCEPT'
```

Accept the score submission without any flags.

####### `leadr.scores.domain.anti_cheat.FlagAction.FLAG`

```python
FLAG = 'FLAG'
```

Accept the score but flag it for manual review.

####### `leadr.scores.domain.anti_cheat.FlagAction.REJECT`

```python
REJECT = 'REJECT'
```

Reject the score submission (do not save to database).

###### `leadr.scores.domain.anti_cheat.FlagConfidence`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Confidence level for anti-cheat detection.

Determines the action taken when a flag is raised:

- HIGH: Auto-reject submission
- MEDIUM: Flag for manual review, accept submission
- LOW: Log for analysis, accept submission

**Attributes:**

- [**HIGH**](#leadr.scores.domain.anti_cheat.FlagConfidence.HIGH) – High confidence detection - reject submission.
- [**LOW**](#leadr.scores.domain.anti_cheat.FlagConfidence.LOW) – Low confidence detection - log but accept.
- [**MEDIUM**](#leadr.scores.domain.anti_cheat.FlagConfidence.MEDIUM) – Medium confidence detection - flag for review but accept.

####### `leadr.scores.domain.anti_cheat.FlagConfidence.HIGH`

```python
HIGH = 'HIGH'
```

High confidence detection - reject submission.

####### `leadr.scores.domain.anti_cheat.FlagConfidence.LOW`

```python
LOW = 'LOW'
```

Low confidence detection - log but accept.

####### `leadr.scores.domain.anti_cheat.FlagConfidence.MEDIUM`

```python
MEDIUM = 'MEDIUM'
```

Medium confidence detection - flag for review but accept.

###### `leadr.scores.domain.anti_cheat.FlagType`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Type of anti-cheat flag detected.

Each flag type represents a different detection tactic used to identify
potentially suspicious score submissions.

**Attributes:**

- [**CLUSTER**](#leadr.scores.domain.anti_cheat.FlagType.CLUSTER) – Multiple users submitting identical scores in short time window.
- [**DUPLICATE**](#leadr.scores.domain.anti_cheat.FlagType.DUPLICATE) – Identical score value submitted multiple times in short time window.
- [**IMPOSSIBLE_VALUE**](#leadr.scores.domain.anti_cheat.FlagType.IMPOSSIBLE_VALUE) – Score contains mathematically impossible value (negative, NaN, etc).
- [**OUTLIER**](#leadr.scores.domain.anti_cheat.FlagType.OUTLIER) – Score is statistically anomalous compared to board distribution.
- [**PATTERN**](#leadr.scores.domain.anti_cheat.FlagType.PATTERN) – Suspicious pattern detected in submission history (all round numbers, etc).
- [**PROGRESSION**](#leadr.scores.domain.anti_cheat.FlagType.PROGRESSION) – Unrealistic improvement percentage between submissions.
- [**RATE_LIMIT**](#leadr.scores.domain.anti_cheat.FlagType.RATE_LIMIT) – Score submission exceeds rate limits for the user/board.
- [**VELOCITY**](#leadr.scores.domain.anti_cheat.FlagType.VELOCITY) – Submissions are happening too quickly (< 2 seconds apart).

####### `leadr.scores.domain.anti_cheat.FlagType.CLUSTER`

```python
CLUSTER = 'CLUSTER'
```

Multiple users submitting identical scores in short time window.

####### `leadr.scores.domain.anti_cheat.FlagType.DUPLICATE`

```python
DUPLICATE = 'DUPLICATE'
```

Identical score value submitted multiple times in short time window.

####### `leadr.scores.domain.anti_cheat.FlagType.IMPOSSIBLE_VALUE`

```python
IMPOSSIBLE_VALUE = 'IMPOSSIBLE_VALUE'
```

Score contains mathematically impossible value (negative, NaN, etc).

####### `leadr.scores.domain.anti_cheat.FlagType.OUTLIER`

```python
OUTLIER = 'OUTLIER'
```

Score is statistically anomalous compared to board distribution.

####### `leadr.scores.domain.anti_cheat.FlagType.PATTERN`

```python
PATTERN = 'PATTERN'
```

Suspicious pattern detected in submission history (all round numbers, etc).

####### `leadr.scores.domain.anti_cheat.FlagType.PROGRESSION`

```python
PROGRESSION = 'PROGRESSION'
```

Unrealistic improvement percentage between submissions.

####### `leadr.scores.domain.anti_cheat.FlagType.RATE_LIMIT`

```python
RATE_LIMIT = 'RATE_LIMIT'
```

Score submission exceeds rate limits for the user/board.

####### `leadr.scores.domain.anti_cheat.FlagType.VELOCITY`

```python
VELOCITY = 'VELOCITY'
```

Submissions are happening too quickly (< 2 seconds apart).

###### `leadr.scores.domain.anti_cheat.ScoreFlag`

Bases: <code>[Entity](./common.md#leadr.common.domain.models.Entity)</code>

Record of an anti-cheat flag raised for a score submission.

Represents a suspicious pattern detected by the anti-cheat system.
Flags can be reviewed by admins to confirm or dismiss the detection.

**Functions:**

- [**restore**](#leadr.scores.domain.anti_cheat.ScoreFlag.restore) – Restore a soft-deleted entity.
- [**soft_delete**](#leadr.scores.domain.anti_cheat.ScoreFlag.soft_delete) – Mark entity as soft-deleted.

**Attributes:**

- [**confidence**](#leadr.scores.domain.anti_cheat.ScoreFlag.confidence) (<code>[FlagConfidence](#leadr.scores.domain.anti_cheat.enums.FlagConfidence)</code>) –
- [**created_at**](#leadr.scores.domain.anti_cheat.ScoreFlag.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**deleted_at**](#leadr.scores.domain.anti_cheat.ScoreFlag.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**flag_type**](#leadr.scores.domain.anti_cheat.ScoreFlag.flag_type) (<code>[FlagType](#leadr.scores.domain.anti_cheat.enums.FlagType)</code>) –
- [**id**](#leadr.scores.domain.anti_cheat.ScoreFlag.id) (<code>[ScoreFlagID](./common.md#leadr.common.domain.ids.ScoreFlagID)</code>) –
- [**is_deleted**](#leadr.scores.domain.anti_cheat.ScoreFlag.is_deleted) (<code>[bool](#bool)</code>) – Check if entity is soft-deleted.
- [**metadata**](#leadr.scores.domain.anti_cheat.ScoreFlag.metadata) (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\]</code>) –
- [**model_config**](#leadr.scores.domain.anti_cheat.ScoreFlag.model_config) –
- [**reviewed_at**](#leadr.scores.domain.anti_cheat.ScoreFlag.reviewed_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**reviewer_decision**](#leadr.scores.domain.anti_cheat.ScoreFlag.reviewer_decision) (<code>[str](#str) | None</code>) –
- [**reviewer_id**](#leadr.scores.domain.anti_cheat.ScoreFlag.reviewer_id) (<code>[UserID](./common.md#leadr.common.domain.ids.UserID) | None</code>) –
- [**score_id**](#leadr.scores.domain.anti_cheat.ScoreFlag.score_id) (<code>[ScoreID](./common.md#leadr.common.domain.ids.ScoreID)</code>) –
- [**status**](#leadr.scores.domain.anti_cheat.ScoreFlag.status) (<code>[ScoreFlagStatus](#leadr.scores.domain.anti_cheat.enums.ScoreFlagStatus)</code>) –
- [**updated_at**](#leadr.scores.domain.anti_cheat.ScoreFlag.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.scores.domain.anti_cheat.ScoreFlag.confidence`

```python
confidence: FlagConfidence = Field(description='Confidence level of detection')
```

####### `leadr.scores.domain.anti_cheat.ScoreFlag.created_at`

```python
created_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp when entity was created (UTC)')
```

####### `leadr.scores.domain.anti_cheat.ScoreFlag.deleted_at`

```python
deleted_at: datetime | None = Field(default=None, description='Timestamp when entity was soft-deleted (UTC), or null if active')
```

####### `leadr.scores.domain.anti_cheat.ScoreFlag.flag_type`

```python
flag_type: FlagType = Field(description='Type of suspicious behavior detected')
```

####### `leadr.scores.domain.anti_cheat.ScoreFlag.id`

```python
id: ScoreFlagID = Field(frozen=True, default_factory=ScoreFlagID, description='Unique score flag identifier')
```

####### `leadr.scores.domain.anti_cheat.ScoreFlag.is_deleted`

```python
is_deleted: bool
```

Check if entity is soft-deleted.

**Returns:**

- <code>[bool](#bool)</code> – True if the entity has a deleted_at timestamp, False otherwise.

####### `leadr.scores.domain.anti_cheat.ScoreFlag.metadata`

```python
metadata: dict[str, Any] = Field(default_factory=dict, description='Supporting data for the detection')
```

####### `leadr.scores.domain.anti_cheat.ScoreFlag.model_config`

```python
model_config = ConfigDict(validate_assignment=True)
```

####### `leadr.scores.domain.anti_cheat.ScoreFlag.restore`

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

####### `leadr.scores.domain.anti_cheat.ScoreFlag.reviewed_at`

```python
reviewed_at: datetime | None = Field(default=None, description='When the flag was reviewed by an admin')
```

####### `leadr.scores.domain.anti_cheat.ScoreFlag.reviewer_decision`

```python
reviewer_decision: str | None = Field(default=None, description="Admin's decision/notes on the flag")
```

####### `leadr.scores.domain.anti_cheat.ScoreFlag.reviewer_id`

```python
reviewer_id: UserID | None = Field(default=None, description='ID of the admin who reviewed the flag')
```

####### `leadr.scores.domain.anti_cheat.ScoreFlag.score_id`

```python
score_id: ScoreID = Field(description='ID of the flagged score')
```

####### `leadr.scores.domain.anti_cheat.ScoreFlag.soft_delete`

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

####### `leadr.scores.domain.anti_cheat.ScoreFlag.status`

```python
status: ScoreFlagStatus = Field(default=(ScoreFlagStatus.PENDING), description='Review status (PENDING/CONFIRMED_CHEAT/FALSE_POSITIVE/DISMISSED)')
```

####### `leadr.scores.domain.anti_cheat.ScoreFlag.updated_at`

```python
updated_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp of last update (UTC)')
```

###### `leadr.scores.domain.anti_cheat.ScoreSubmissionMeta`

Bases: <code>[Entity](./common.md#leadr.common.domain.models.Entity)</code>

Metadata tracking submission history for anti-cheat analysis.

Tracks the number and timing of score submissions per device/board combination
to enable detection of suspicious patterns like rapid-fire submissions or
excessive submission rates.

**Functions:**

- [**restore**](#leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.restore) – Restore a soft-deleted entity.
- [**soft_delete**](#leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.soft_delete) – Mark entity as soft-deleted.

**Attributes:**

- [**board_id**](#leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.board_id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) –
- [**created_at**](#leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**deleted_at**](#leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**device_id**](#leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.device_id) (<code>[DeviceID](./common.md#leadr.common.domain.ids.DeviceID)</code>) –
- [**id**](#leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.id) (<code>[ScoreSubmissionMetaID](./common.md#leadr.common.domain.ids.ScoreSubmissionMetaID)</code>) –
- [**is_deleted**](#leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.is_deleted) (<code>[bool](#bool)</code>) – Check if entity is soft-deleted.
- [**last_score_value**](#leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.last_score_value) (<code>[float](#float) | None</code>) –
- [**last_submission_at**](#leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.last_submission_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**model_config**](#leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.model_config) –
- [**score_id**](#leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.score_id) (<code>[ScoreID](./common.md#leadr.common.domain.ids.ScoreID)</code>) –
- [**submission_count**](#leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.submission_count) (<code>[int](#int)</code>) –
- [**updated_at**](#leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.board_id`

```python
board_id: BoardID = Field(description='ID of the board being submitted to')
```

####### `leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.created_at`

```python
created_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp when entity was created (UTC)')
```

####### `leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.deleted_at`

```python
deleted_at: datetime | None = Field(default=None, description='Timestamp when entity was soft-deleted (UTC), or null if active')
```

####### `leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.device_id`

```python
device_id: DeviceID = Field(description='ID of the device submitting scores')
```

####### `leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.id`

```python
id: ScoreSubmissionMetaID = Field(frozen=True, default_factory=ScoreSubmissionMetaID, description='Unique submission metadata identifier')
```

####### `leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.is_deleted`

```python
is_deleted: bool
```

Check if entity is soft-deleted.

**Returns:**

- <code>[bool](#bool)</code> – True if the entity has a deleted_at timestamp, False otherwise.

####### `leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.last_score_value`

```python
last_score_value: float | None = Field(default=None, description='Value of the most recent score submission for duplicate detection')
```

####### `leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.last_submission_at`

```python
last_submission_at: datetime = Field(description='Timestamp of the most recent submission')
```

####### `leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.model_config`

```python
model_config = ConfigDict(validate_assignment=True)
```

####### `leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.restore`

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

####### `leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.score_id`

```python
score_id: ScoreID = Field(description='ID of the most recent score submission')
```

####### `leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.soft_delete`

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

####### `leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.submission_count`

```python
submission_count: int = Field(default=1, description='Total number of submissions by this device to this board')
```

####### `leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.updated_at`

```python
updated_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp of last update (UTC)')
```

###### `leadr.scores.domain.anti_cheat.TrustTier`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Trust tier for devices/users, determining anti-cheat thresholds.

Different tiers have different rate limits and detection thresholds:

- Tier A (Trusted): Most lenient thresholds, highest rate limits
- Tier B (Verified): Moderate thresholds and rate limits
- Tier C (Unverified): Strictest thresholds, lowest rate limits

**Attributes:**

- [**A**](#leadr.scores.domain.anti_cheat.TrustTier.A) – Tier A - Trusted devices with verified attestation.
- [**B**](#leadr.scores.domain.anti_cheat.TrustTier.B) – Tier B - Verified devices without full attestation.
- [**C**](#leadr.scores.domain.anti_cheat.TrustTier.C) – Tier C - Unverified or new devices.

####### `leadr.scores.domain.anti_cheat.TrustTier.A`

```python
A = 'A'
```

Tier A - Trusted devices with verified attestation.

####### `leadr.scores.domain.anti_cheat.TrustTier.B`

```python
B = 'B'
```

Tier B - Verified devices without full attestation.

####### `leadr.scores.domain.anti_cheat.TrustTier.C`

```python
C = 'C'
```

Tier C - Unverified or new devices.

###### `leadr.scores.domain.anti_cheat.enums`

Anti-cheat enums for flag types, confidence levels, and actions.

**Classes:**

- [**FlagAction**](#leadr.scores.domain.anti_cheat.enums.FlagAction) – Action to take based on anti-cheat analysis.
- [**FlagConfidence**](#leadr.scores.domain.anti_cheat.enums.FlagConfidence) – Confidence level for anti-cheat detection.
- [**FlagType**](#leadr.scores.domain.anti_cheat.enums.FlagType) – Type of anti-cheat flag detected.
- [**ScoreFlagStatus**](#leadr.scores.domain.anti_cheat.enums.ScoreFlagStatus) – Status of a score flag review.
- [**TrustTier**](#leadr.scores.domain.anti_cheat.enums.TrustTier) – Trust tier for devices/users, determining anti-cheat thresholds.

####### `leadr.scores.domain.anti_cheat.enums.FlagAction`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Action to take based on anti-cheat analysis.

Determines how the score submission should be handled.

**Attributes:**

- [**ACCEPT**](#leadr.scores.domain.anti_cheat.enums.FlagAction.ACCEPT) – Accept the score submission without any flags.
- [**FLAG**](#leadr.scores.domain.anti_cheat.enums.FlagAction.FLAG) – Accept the score but flag it for manual review.
- [**REJECT**](#leadr.scores.domain.anti_cheat.enums.FlagAction.REJECT) – Reject the score submission (do not save to database).

######## `leadr.scores.domain.anti_cheat.enums.FlagAction.ACCEPT`

```python
ACCEPT = 'ACCEPT'
```

Accept the score submission without any flags.

######## `leadr.scores.domain.anti_cheat.enums.FlagAction.FLAG`

```python
FLAG = 'FLAG'
```

Accept the score but flag it for manual review.

######## `leadr.scores.domain.anti_cheat.enums.FlagAction.REJECT`

```python
REJECT = 'REJECT'
```

Reject the score submission (do not save to database).

####### `leadr.scores.domain.anti_cheat.enums.FlagConfidence`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Confidence level for anti-cheat detection.

Determines the action taken when a flag is raised:

- HIGH: Auto-reject submission
- MEDIUM: Flag for manual review, accept submission
- LOW: Log for analysis, accept submission

**Attributes:**

- [**HIGH**](#leadr.scores.domain.anti_cheat.enums.FlagConfidence.HIGH) – High confidence detection - reject submission.
- [**LOW**](#leadr.scores.domain.anti_cheat.enums.FlagConfidence.LOW) – Low confidence detection - log but accept.
- [**MEDIUM**](#leadr.scores.domain.anti_cheat.enums.FlagConfidence.MEDIUM) – Medium confidence detection - flag for review but accept.

######## `leadr.scores.domain.anti_cheat.enums.FlagConfidence.HIGH`

```python
HIGH = 'HIGH'
```

High confidence detection - reject submission.

######## `leadr.scores.domain.anti_cheat.enums.FlagConfidence.LOW`

```python
LOW = 'LOW'
```

Low confidence detection - log but accept.

######## `leadr.scores.domain.anti_cheat.enums.FlagConfidence.MEDIUM`

```python
MEDIUM = 'MEDIUM'
```

Medium confidence detection - flag for review but accept.

####### `leadr.scores.domain.anti_cheat.enums.FlagType`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Type of anti-cheat flag detected.

Each flag type represents a different detection tactic used to identify
potentially suspicious score submissions.

**Attributes:**

- [**CLUSTER**](#leadr.scores.domain.anti_cheat.enums.FlagType.CLUSTER) – Multiple users submitting identical scores in short time window.
- [**DUPLICATE**](#leadr.scores.domain.anti_cheat.enums.FlagType.DUPLICATE) – Identical score value submitted multiple times in short time window.
- [**IMPOSSIBLE_VALUE**](#leadr.scores.domain.anti_cheat.enums.FlagType.IMPOSSIBLE_VALUE) – Score contains mathematically impossible value (negative, NaN, etc).
- [**OUTLIER**](#leadr.scores.domain.anti_cheat.enums.FlagType.OUTLIER) – Score is statistically anomalous compared to board distribution.
- [**PATTERN**](#leadr.scores.domain.anti_cheat.enums.FlagType.PATTERN) – Suspicious pattern detected in submission history (all round numbers, etc).
- [**PROGRESSION**](#leadr.scores.domain.anti_cheat.enums.FlagType.PROGRESSION) – Unrealistic improvement percentage between submissions.
- [**RATE_LIMIT**](#leadr.scores.domain.anti_cheat.enums.FlagType.RATE_LIMIT) – Score submission exceeds rate limits for the user/board.
- [**VELOCITY**](#leadr.scores.domain.anti_cheat.enums.FlagType.VELOCITY) – Submissions are happening too quickly (< 2 seconds apart).

######## `leadr.scores.domain.anti_cheat.enums.FlagType.CLUSTER`

```python
CLUSTER = 'CLUSTER'
```

Multiple users submitting identical scores in short time window.

######## `leadr.scores.domain.anti_cheat.enums.FlagType.DUPLICATE`

```python
DUPLICATE = 'DUPLICATE'
```

Identical score value submitted multiple times in short time window.

######## `leadr.scores.domain.anti_cheat.enums.FlagType.IMPOSSIBLE_VALUE`

```python
IMPOSSIBLE_VALUE = 'IMPOSSIBLE_VALUE'
```

Score contains mathematically impossible value (negative, NaN, etc).

######## `leadr.scores.domain.anti_cheat.enums.FlagType.OUTLIER`

```python
OUTLIER = 'OUTLIER'
```

Score is statistically anomalous compared to board distribution.

######## `leadr.scores.domain.anti_cheat.enums.FlagType.PATTERN`

```python
PATTERN = 'PATTERN'
```

Suspicious pattern detected in submission history (all round numbers, etc).

######## `leadr.scores.domain.anti_cheat.enums.FlagType.PROGRESSION`

```python
PROGRESSION = 'PROGRESSION'
```

Unrealistic improvement percentage between submissions.

######## `leadr.scores.domain.anti_cheat.enums.FlagType.RATE_LIMIT`

```python
RATE_LIMIT = 'RATE_LIMIT'
```

Score submission exceeds rate limits for the user/board.

######## `leadr.scores.domain.anti_cheat.enums.FlagType.VELOCITY`

```python
VELOCITY = 'VELOCITY'
```

Submissions are happening too quickly (< 2 seconds apart).

####### `leadr.scores.domain.anti_cheat.enums.ScoreFlagStatus`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Status of a score flag review.

Indicates whether a flag has been reviewed and what decision was made.

**Attributes:**

- [**CONFIRMED_CHEAT**](#leadr.scores.domain.anti_cheat.enums.ScoreFlagStatus.CONFIRMED_CHEAT) – Admin confirmed this is cheating behavior.
- [**DISMISSED**](#leadr.scores.domain.anti_cheat.enums.ScoreFlagStatus.DISMISSED) – Admin dismissed the flag without a specific determination.
- [**FALSE_POSITIVE**](#leadr.scores.domain.anti_cheat.enums.ScoreFlagStatus.FALSE_POSITIVE) – Admin determined this was legitimate gameplay.
- [**PENDING**](#leadr.scores.domain.anti_cheat.enums.ScoreFlagStatus.PENDING) – Flag has not been reviewed yet.

######## `leadr.scores.domain.anti_cheat.enums.ScoreFlagStatus.CONFIRMED_CHEAT`

```python
CONFIRMED_CHEAT = 'CONFIRMED_CHEAT'
```

Admin confirmed this is cheating behavior.

######## `leadr.scores.domain.anti_cheat.enums.ScoreFlagStatus.DISMISSED`

```python
DISMISSED = 'DISMISSED'
```

Admin dismissed the flag without a specific determination.

######## `leadr.scores.domain.anti_cheat.enums.ScoreFlagStatus.FALSE_POSITIVE`

```python
FALSE_POSITIVE = 'FALSE_POSITIVE'
```

Admin determined this was legitimate gameplay.

######## `leadr.scores.domain.anti_cheat.enums.ScoreFlagStatus.PENDING`

```python
PENDING = 'PENDING'
```

Flag has not been reviewed yet.

####### `leadr.scores.domain.anti_cheat.enums.TrustTier`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Trust tier for devices/users, determining anti-cheat thresholds.

Different tiers have different rate limits and detection thresholds:

- Tier A (Trusted): Most lenient thresholds, highest rate limits
- Tier B (Verified): Moderate thresholds and rate limits
- Tier C (Unverified): Strictest thresholds, lowest rate limits

**Attributes:**

- [**A**](#leadr.scores.domain.anti_cheat.enums.TrustTier.A) – Tier A - Trusted devices with verified attestation.
- [**B**](#leadr.scores.domain.anti_cheat.enums.TrustTier.B) – Tier B - Verified devices without full attestation.
- [**C**](#leadr.scores.domain.anti_cheat.enums.TrustTier.C) – Tier C - Unverified or new devices.

######## `leadr.scores.domain.anti_cheat.enums.TrustTier.A`

```python
A = 'A'
```

Tier A - Trusted devices with verified attestation.

######## `leadr.scores.domain.anti_cheat.enums.TrustTier.B`

```python
B = 'B'
```

Tier B - Verified devices without full attestation.

######## `leadr.scores.domain.anti_cheat.enums.TrustTier.C`

```python
C = 'C'
```

Tier C - Unverified or new devices.

###### `leadr.scores.domain.anti_cheat.models`

Anti-cheat domain models.

**Classes:**

- [**AntiCheatResult**](#leadr.scores.domain.anti_cheat.models.AntiCheatResult) – Result of anti-cheat analysis on a score submission.
- [**ScoreFlag**](#leadr.scores.domain.anti_cheat.models.ScoreFlag) – Record of an anti-cheat flag raised for a score submission.
- [**ScoreSubmissionMeta**](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta) – Metadata tracking submission history for anti-cheat analysis.

####### `leadr.scores.domain.anti_cheat.models.AntiCheatResult`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Result of anti-cheat analysis on a score submission.

This is a value object that encapsulates the decision made by the anti-cheat
system. It indicates whether to accept, flag, or reject a score submission,
along with the reasoning and supporting metadata.

**Attributes:**

- [**action**](#leadr.scores.domain.anti_cheat.models.AntiCheatResult.action) (<code>[FlagAction](#leadr.scores.domain.anti_cheat.enums.FlagAction)</code>) –
- [**confidence**](#leadr.scores.domain.anti_cheat.models.AntiCheatResult.confidence) (<code>[FlagConfidence](#leadr.scores.domain.anti_cheat.enums.FlagConfidence) | None</code>) –
- [**flag_type**](#leadr.scores.domain.anti_cheat.models.AntiCheatResult.flag_type) (<code>[FlagType](#leadr.scores.domain.anti_cheat.enums.FlagType) | None</code>) –
- [**metadata**](#leadr.scores.domain.anti_cheat.models.AntiCheatResult.metadata) (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\] | None</code>) –
- [**model_config**](#leadr.scores.domain.anti_cheat.models.AntiCheatResult.model_config) –
- [**reason**](#leadr.scores.domain.anti_cheat.models.AntiCheatResult.reason) (<code>[str](#str) | None</code>) –

######## `leadr.scores.domain.anti_cheat.models.AntiCheatResult.action`

```python
action: FlagAction = Field(description='Action to take (ACCEPT/FLAG/REJECT)')
```

######## `leadr.scores.domain.anti_cheat.models.AntiCheatResult.confidence`

```python
confidence: FlagConfidence | None = Field(default=None, description='Confidence level of detection (if flagged/rejected)')
```

######## `leadr.scores.domain.anti_cheat.models.AntiCheatResult.flag_type`

```python
flag_type: FlagType | None = Field(default=None, description='Type of flag detected (if flagged/rejected)')
```

######## `leadr.scores.domain.anti_cheat.models.AntiCheatResult.metadata`

```python
metadata: dict[str, Any] | None = Field(default=None, description='Additional context and data supporting the decision')
```

######## `leadr.scores.domain.anti_cheat.models.AntiCheatResult.model_config`

```python
model_config = {'frozen': True}
```

######## `leadr.scores.domain.anti_cheat.models.AntiCheatResult.reason`

```python
reason: str | None = Field(default=None, description='Human-readable reason for the action')
```

####### `leadr.scores.domain.anti_cheat.models.ScoreFlag`

Bases: <code>[Entity](./common.md#leadr.common.domain.models.Entity)</code>

Record of an anti-cheat flag raised for a score submission.

Represents a suspicious pattern detected by the anti-cheat system.
Flags can be reviewed by admins to confirm or dismiss the detection.

**Functions:**

- [**restore**](#leadr.scores.domain.anti_cheat.models.ScoreFlag.restore) – Restore a soft-deleted entity.
- [**soft_delete**](#leadr.scores.domain.anti_cheat.models.ScoreFlag.soft_delete) – Mark entity as soft-deleted.

**Attributes:**

- [**confidence**](#leadr.scores.domain.anti_cheat.models.ScoreFlag.confidence) (<code>[FlagConfidence](#leadr.scores.domain.anti_cheat.enums.FlagConfidence)</code>) –
- [**created_at**](#leadr.scores.domain.anti_cheat.models.ScoreFlag.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**deleted_at**](#leadr.scores.domain.anti_cheat.models.ScoreFlag.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**flag_type**](#leadr.scores.domain.anti_cheat.models.ScoreFlag.flag_type) (<code>[FlagType](#leadr.scores.domain.anti_cheat.enums.FlagType)</code>) –
- [**id**](#leadr.scores.domain.anti_cheat.models.ScoreFlag.id) (<code>[ScoreFlagID](./common.md#leadr.common.domain.ids.ScoreFlagID)</code>) –
- [**is_deleted**](#leadr.scores.domain.anti_cheat.models.ScoreFlag.is_deleted) (<code>[bool](#bool)</code>) – Check if entity is soft-deleted.
- [**metadata**](#leadr.scores.domain.anti_cheat.models.ScoreFlag.metadata) (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\]</code>) –
- [**model_config**](#leadr.scores.domain.anti_cheat.models.ScoreFlag.model_config) –
- [**reviewed_at**](#leadr.scores.domain.anti_cheat.models.ScoreFlag.reviewed_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**reviewer_decision**](#leadr.scores.domain.anti_cheat.models.ScoreFlag.reviewer_decision) (<code>[str](#str) | None</code>) –
- [**reviewer_id**](#leadr.scores.domain.anti_cheat.models.ScoreFlag.reviewer_id) (<code>[UserID](./common.md#leadr.common.domain.ids.UserID) | None</code>) –
- [**score_id**](#leadr.scores.domain.anti_cheat.models.ScoreFlag.score_id) (<code>[ScoreID](./common.md#leadr.common.domain.ids.ScoreID)</code>) –
- [**status**](#leadr.scores.domain.anti_cheat.models.ScoreFlag.status) (<code>[ScoreFlagStatus](#leadr.scores.domain.anti_cheat.enums.ScoreFlagStatus)</code>) –
- [**updated_at**](#leadr.scores.domain.anti_cheat.models.ScoreFlag.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

######## `leadr.scores.domain.anti_cheat.models.ScoreFlag.confidence`

```python
confidence: FlagConfidence = Field(description='Confidence level of detection')
```

######## `leadr.scores.domain.anti_cheat.models.ScoreFlag.created_at`

```python
created_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp when entity was created (UTC)')
```

######## `leadr.scores.domain.anti_cheat.models.ScoreFlag.deleted_at`

```python
deleted_at: datetime | None = Field(default=None, description='Timestamp when entity was soft-deleted (UTC), or null if active')
```

######## `leadr.scores.domain.anti_cheat.models.ScoreFlag.flag_type`

```python
flag_type: FlagType = Field(description='Type of suspicious behavior detected')
```

######## `leadr.scores.domain.anti_cheat.models.ScoreFlag.id`

```python
id: ScoreFlagID = Field(frozen=True, default_factory=ScoreFlagID, description='Unique score flag identifier')
```

######## `leadr.scores.domain.anti_cheat.models.ScoreFlag.is_deleted`

```python
is_deleted: bool
```

Check if entity is soft-deleted.

**Returns:**

- <code>[bool](#bool)</code> – True if the entity has a deleted_at timestamp, False otherwise.

######## `leadr.scores.domain.anti_cheat.models.ScoreFlag.metadata`

```python
metadata: dict[str, Any] = Field(default_factory=dict, description='Supporting data for the detection')
```

######## `leadr.scores.domain.anti_cheat.models.ScoreFlag.model_config`

```python
model_config = ConfigDict(validate_assignment=True)
```

######## `leadr.scores.domain.anti_cheat.models.ScoreFlag.restore`

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

######## `leadr.scores.domain.anti_cheat.models.ScoreFlag.reviewed_at`

```python
reviewed_at: datetime | None = Field(default=None, description='When the flag was reviewed by an admin')
```

######## `leadr.scores.domain.anti_cheat.models.ScoreFlag.reviewer_decision`

```python
reviewer_decision: str | None = Field(default=None, description="Admin's decision/notes on the flag")
```

######## `leadr.scores.domain.anti_cheat.models.ScoreFlag.reviewer_id`

```python
reviewer_id: UserID | None = Field(default=None, description='ID of the admin who reviewed the flag')
```

######## `leadr.scores.domain.anti_cheat.models.ScoreFlag.score_id`

```python
score_id: ScoreID = Field(description='ID of the flagged score')
```

######## `leadr.scores.domain.anti_cheat.models.ScoreFlag.soft_delete`

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

######## `leadr.scores.domain.anti_cheat.models.ScoreFlag.status`

```python
status: ScoreFlagStatus = Field(default=(ScoreFlagStatus.PENDING), description='Review status (PENDING/CONFIRMED_CHEAT/FALSE_POSITIVE/DISMISSED)')
```

######## `leadr.scores.domain.anti_cheat.models.ScoreFlag.updated_at`

```python
updated_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp of last update (UTC)')
```

####### `leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta`

Bases: <code>[Entity](./common.md#leadr.common.domain.models.Entity)</code>

Metadata tracking submission history for anti-cheat analysis.

Tracks the number and timing of score submissions per device/board combination
to enable detection of suspicious patterns like rapid-fire submissions or
excessive submission rates.

**Functions:**

- [**restore**](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.restore) – Restore a soft-deleted entity.
- [**soft_delete**](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.soft_delete) – Mark entity as soft-deleted.

**Attributes:**

- [**board_id**](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.board_id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) –
- [**created_at**](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**deleted_at**](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**device_id**](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.device_id) (<code>[DeviceID](./common.md#leadr.common.domain.ids.DeviceID)</code>) –
- [**id**](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.id) (<code>[ScoreSubmissionMetaID](./common.md#leadr.common.domain.ids.ScoreSubmissionMetaID)</code>) –
- [**is_deleted**](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.is_deleted) (<code>[bool](#bool)</code>) – Check if entity is soft-deleted.
- [**last_score_value**](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.last_score_value) (<code>[float](#float) | None</code>) –
- [**last_submission_at**](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.last_submission_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**model_config**](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.model_config) –
- [**score_id**](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.score_id) (<code>[ScoreID](./common.md#leadr.common.domain.ids.ScoreID)</code>) –
- [**submission_count**](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.submission_count) (<code>[int](#int)</code>) –
- [**updated_at**](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

######## `leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.board_id`

```python
board_id: BoardID = Field(description='ID of the board being submitted to')
```

######## `leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.created_at`

```python
created_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp when entity was created (UTC)')
```

######## `leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.deleted_at`

```python
deleted_at: datetime | None = Field(default=None, description='Timestamp when entity was soft-deleted (UTC), or null if active')
```

######## `leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.device_id`

```python
device_id: DeviceID = Field(description='ID of the device submitting scores')
```

######## `leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.id`

```python
id: ScoreSubmissionMetaID = Field(frozen=True, default_factory=ScoreSubmissionMetaID, description='Unique submission metadata identifier')
```

######## `leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.is_deleted`

```python
is_deleted: bool
```

Check if entity is soft-deleted.

**Returns:**

- <code>[bool](#bool)</code> – True if the entity has a deleted_at timestamp, False otherwise.

######## `leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.last_score_value`

```python
last_score_value: float | None = Field(default=None, description='Value of the most recent score submission for duplicate detection')
```

######## `leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.last_submission_at`

```python
last_submission_at: datetime = Field(description='Timestamp of the most recent submission')
```

######## `leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.model_config`

```python
model_config = ConfigDict(validate_assignment=True)
```

######## `leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.restore`

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

######## `leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.score_id`

```python
score_id: ScoreID = Field(description='ID of the most recent score submission')
```

######## `leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.soft_delete`

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

######## `leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.submission_count`

```python
submission_count: int = Field(default=1, description='Total number of submissions by this device to this board')
```

######## `leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.updated_at`

```python
updated_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp of last update (UTC)')
```

##### `leadr.scores.domain.score`

Score domain entity.

**Classes:**

- [**Score**](./scores.md#leadr.scores.domain.score.Score) – Score represents a player's score submission for a board.

###### `leadr.scores.domain.score.Score`

Bases: <code>[Entity](./common.md#leadr.common.domain.models.Entity)</code>

Score represents a player's score submission for a board.

Scores are immutable in terms of their associations (account, game, board, device)
but mutable in terms of their value and metadata for corrections/updates.

**Functions:**

- [**restore**](./scores.md#leadr.scores.domain.score.Score.restore) – Restore a soft-deleted entity.
- [**soft_delete**](#leadr.scores.domain.score.Score.soft_delete) – Mark entity as soft-deleted.
- [**validate_metadata_size**](#leadr.scores.domain.score.Score.validate_metadata_size) – Validate that metadata does not exceed size limit.
- [**validate_player_name**](#leadr.scores.domain.score.Score.validate_player_name) – Validate that player_name is not empty and strip whitespace.

**Attributes:**

- [**account_id**](#leadr.scores.domain.score.Score.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**board_id**](#leadr.scores.domain.score.Score.board_id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) –
- [**city**](./scores.md#leadr.scores.domain.score.Score.city) (<code>[str](#str) | None</code>) –
- [**country**](./scores.md#leadr.scores.domain.score.Score.country) (<code>[str](#str) | None</code>) –
- [**created_at**](#leadr.scores.domain.score.Score.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**deleted_at**](#leadr.scores.domain.score.Score.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**device_id**](#leadr.scores.domain.score.Score.device_id) (<code>[DeviceID](./common.md#leadr.common.domain.ids.DeviceID)</code>) –
- [**game_id**](#leadr.scores.domain.score.Score.game_id) (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) –
- [**id**](./scores.md#leadr.scores.domain.score.Score.id) (<code>[ScoreID](./common.md#leadr.common.domain.ids.ScoreID)</code>) –
- [**is_deleted**](#leadr.scores.domain.score.Score.is_deleted) (<code>[bool](#bool)</code>) – Check if entity is soft-deleted.
- [**metadata**](./scores.md#leadr.scores.domain.score.Score.metadata) (<code>[Any](#typing.Any) | None</code>) –
- [**model_config**](#leadr.scores.domain.score.Score.model_config) –
- [**player_name**](#leadr.scores.domain.score.Score.player_name) (<code>[str](#str)</code>) –
- [**timezone**](./scores.md#leadr.scores.domain.score.Score.timezone) (<code>[str](#str) | None</code>) –
- [**updated_at**](#leadr.scores.domain.score.Score.updated_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**value**](./scores.md#leadr.scores.domain.score.Score.value) (<code>[float](#float)</code>) –
- [**value_display**](#leadr.scores.domain.score.Score.value_display) (<code>[str](#str) | None</code>) –

####### `leadr.scores.domain.score.Score.account_id`

```python
account_id: AccountID = Field(frozen=True, description='ID of the account this score belongs to (immutable)')
```

####### `leadr.scores.domain.score.Score.board_id`

```python
board_id: BoardID = Field(frozen=True, description='ID of the board this score belongs to (immutable)')
```

####### `leadr.scores.domain.score.Score.city`

```python
city: str | None = Field(default=None, description='Optional city filter for score categorization')
```

####### `leadr.scores.domain.score.Score.country`

```python
country: str | None = Field(default=None, description='Optional country filter for score categorization')
```

####### `leadr.scores.domain.score.Score.created_at`

```python
created_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp when entity was created (UTC)')
```

####### `leadr.scores.domain.score.Score.deleted_at`

```python
deleted_at: datetime | None = Field(default=None, description='Timestamp when entity was soft-deleted (UTC), or null if active')
```

####### `leadr.scores.domain.score.Score.device_id`

```python
device_id: DeviceID = Field(frozen=True, description='ID of the device that submitted this score (immutable)')
```

####### `leadr.scores.domain.score.Score.game_id`

```python
game_id: GameID = Field(frozen=True, description='ID of the game this score belongs to (immutable)')
```

####### `leadr.scores.domain.score.Score.id`

```python
id: ScoreID = Field(frozen=True, default_factory=ScoreID, description='Unique score identifier')
```

####### `leadr.scores.domain.score.Score.is_deleted`

```python
is_deleted: bool
```

Check if entity is soft-deleted.

**Returns:**

- <code>[bool](#bool)</code> – True if the entity has a deleted_at timestamp, False otherwise.

####### `leadr.scores.domain.score.Score.metadata`

```python
metadata: Any | None = Field(default=None, description='Optional JSON metadata for game-specific data (loadouts, seeds, etc.)')
```

####### `leadr.scores.domain.score.Score.model_config`

```python
model_config = ConfigDict(validate_assignment=True)
```

####### `leadr.scores.domain.score.Score.player_name`

```python
player_name: str = Field(description='Display name of the player')
```

####### `leadr.scores.domain.score.Score.restore`

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

####### `leadr.scores.domain.score.Score.soft_delete`

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

####### `leadr.scores.domain.score.Score.timezone`

```python
timezone: str | None = Field(default=None, description='Optional timezone filter for score categorization')
```

####### `leadr.scores.domain.score.Score.updated_at`

```python
updated_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp of last update (UTC)')
```

####### `leadr.scores.domain.score.Score.validate_metadata_size`

```python
validate_metadata_size(v)
```

Validate that metadata does not exceed size limit.

**Parameters:**

- **v** (<code>[Any](#typing.Any)</code>) – The metadata to validate.

**Returns:**

- <code>[Any](#typing.Any)</code> – The validated metadata.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If metadata exceeds the configured size limit.

####### `leadr.scores.domain.score.Score.validate_player_name`

```python
validate_player_name(v)
```

Validate that player_name is not empty and strip whitespace.

**Parameters:**

- **v** (<code>[str](#str)</code>) – The player_name to validate.

**Returns:**

- <code>[str](#str)</code> – The validated and trimmed player_name.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If player_name is empty or whitespace only.

####### `leadr.scores.domain.score.Score.value`

```python
value: float = Field(description='Numeric value of the score for sorting/comparison')
```

####### `leadr.scores.domain.score.Score.value_display`

```python
value_display: str | None = Field(default=None, description="Optional formatted display string (e.g., '1:23.45', '1,234 points')")
```

#### `leadr.scores.services`

**Modules:**

- [**anti_cheat_repositories**](#leadr.scores.services.anti_cheat_repositories) – Anti-cheat repository services.
- [**anti_cheat_service**](#leadr.scores.services.anti_cheat_service) – Anti-cheat service for detecting suspicious score submissions.
- [**dependencies**](./scores.md#leadr.scores.services.dependencies) – Score service dependencies for FastAPI dependency injection.
- [**repositories**](./scores.md#leadr.scores.services.repositories) – Score repository services.
- [**score_flag_service**](#leadr.scores.services.score_flag_service) – Score flag service for managing flag operations.
- [**score_service**](#leadr.scores.services.score_service) – Score service for managing score operations.
- [**score_submission_meta_service**](#leadr.scores.services.score_submission_meta_service) – Service for score submission metadata management.

##### `leadr.scores.services.anti_cheat_repositories`

Anti-cheat repository services.

**Classes:**

- [**ScoreFlagRepository**](#leadr.scores.services.anti_cheat_repositories.ScoreFlagRepository) – Repository for managing score flag persistence.
- [**ScoreSubmissionMetaRepository**](#leadr.scores.services.anti_cheat_repositories.ScoreSubmissionMetaRepository) – Repository for managing score submission metadata persistence.

###### `leadr.scores.services.anti_cheat_repositories.ScoreFlagRepository`

Bases: <code>[BaseRepository](./common.md#leadr.common.repositories.BaseRepository)\[[ScoreFlag](#leadr.scores.domain.anti_cheat.models.ScoreFlag), [ScoreFlagORM](./scores.md#leadr.scores.adapters.orm.ScoreFlagORM)\]</code>

Repository for managing score flag persistence.

**Functions:**

- [**create**](#leadr.scores.services.anti_cheat_repositories.ScoreFlagRepository.create) – Create a new entity in the database.
- [**delete**](#leadr.scores.services.anti_cheat_repositories.ScoreFlagRepository.delete) – Soft delete an entity by setting its deleted_at timestamp.
- [**filter**](#leadr.scores.services.anti_cheat_repositories.ScoreFlagRepository.filter) – Filter flags by account and optional criteria.
- [**get_by_id**](#leadr.scores.services.anti_cheat_repositories.ScoreFlagRepository.get_by_id) – Get an entity by its ID.
- [**get_flags_by_score_id**](#leadr.scores.services.anti_cheat_repositories.ScoreFlagRepository.get_flags_by_score_id) – Get all flags for a specific score.
- [**get_pending_flags**](#leadr.scores.services.anti_cheat_repositories.ScoreFlagRepository.get_pending_flags) – Get all pending (unreviewed) flags.
- [**update**](#leadr.scores.services.anti_cheat_repositories.ScoreFlagRepository.update) – Update an existing entity in the database.

**Attributes:**

- [**session**](#leadr.scores.services.anti_cheat_repositories.ScoreFlagRepository.session) –

####### `leadr.scores.services.anti_cheat_repositories.ScoreFlagRepository.create`

```python
create(entity)
```

Create a new entity in the database.

**Parameters:**

- **entity** (<code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code>) – Domain entity to create

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code> – Created domain entity with refreshed data

####### `leadr.scores.services.anti_cheat_repositories.ScoreFlagRepository.delete`

```python
delete(entity_id)
```

Soft delete an entity by setting its deleted_at timestamp.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – ID of entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

####### `leadr.scores.services.anti_cheat_repositories.ScoreFlagRepository.filter`

```python
filter(account_id=None, board_id=None, game_id=None, status=None, flag_type=None, **kwargs)
```

Filter flags by account and optional criteria.

Joins with scores table to filter by account_id since flags don't have
a direct account relation.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – REQUIRED - Account ID to filter by (multi-tenant safety)
- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None</code>) – Optional board ID to filter by
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID) | None</code>) – Optional game ID to filter by
- **status** (<code>[str](#str) | None</code>) – Optional status to filter by (PENDING, CONFIRMED_CHEAT, etc.)
- **flag_type** (<code>[str](#str) | None</code>) – Optional flag type to filter by (VELOCITY, DUPLICATE, etc.)
- \*\***kwargs** (<code>[Any](#typing.Any)</code>) – Additional filter parameters (reserved for future use)

**Returns:**

- <code>[list](#list)\[[ScoreFlag](#leadr.scores.domain.anti_cheat.models.ScoreFlag)\]</code> – List of flags for the account matching the filter criteria

####### `leadr.scores.services.anti_cheat_repositories.ScoreFlagRepository.get_by_id`

```python
get_by_id(entity_id, include_deleted=False)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – Entity ID to retrieve
- **include_deleted** (<code>[bool](#bool)</code>) – If True, include soft-deleted entities. Defaults to False.

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT) | None</code> – Domain entity if found, None otherwise

####### `leadr.scores.services.anti_cheat_repositories.ScoreFlagRepository.get_flags_by_score_id`

```python
get_flags_by_score_id(score_id)
```

Get all flags for a specific score.

**Parameters:**

- **score_id** (<code>[ScoreID](./common.md#leadr.common.domain.ids.ScoreID)</code>) – ID of the score to get flags for

**Returns:**

- <code>[list](#list)\[[ScoreFlag](#leadr.scores.domain.anti_cheat.models.ScoreFlag)\]</code> – List of flags for the score (excludes soft-deleted)

####### `leadr.scores.services.anti_cheat_repositories.ScoreFlagRepository.get_pending_flags`

```python
get_pending_flags()
```

Get all pending (unreviewed) flags.

**Returns:**

- <code>[list](#list)\[[ScoreFlag](#leadr.scores.domain.anti_cheat.models.ScoreFlag)\]</code> – List of flags with status PENDING (excludes soft-deleted)

####### `leadr.scores.services.anti_cheat_repositories.ScoreFlagRepository.session`

```python
session = session
```

####### `leadr.scores.services.anti_cheat_repositories.ScoreFlagRepository.update`

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

###### `leadr.scores.services.anti_cheat_repositories.ScoreSubmissionMetaRepository`

Bases: <code>[BaseRepository](./common.md#leadr.common.repositories.BaseRepository)\[[ScoreSubmissionMeta](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta), [ScoreSubmissionMetaORM](./scores.md#leadr.scores.adapters.orm.ScoreSubmissionMetaORM)\]</code>

Repository for managing score submission metadata persistence.

**Functions:**

- [**create**](#leadr.scores.services.anti_cheat_repositories.ScoreSubmissionMetaRepository.create) – Create a new entity in the database.
- [**delete**](#leadr.scores.services.anti_cheat_repositories.ScoreSubmissionMetaRepository.delete) – Soft delete an entity by setting its deleted_at timestamp.
- [**filter**](#leadr.scores.services.anti_cheat_repositories.ScoreSubmissionMetaRepository.filter) – Filter submission metadata by account and optional criteria.
- [**get_by_device_and_board**](#leadr.scores.services.anti_cheat_repositories.ScoreSubmissionMetaRepository.get_by_device_and_board) – Get submission metadata for a device/board combination.
- [**get_by_id**](#leadr.scores.services.anti_cheat_repositories.ScoreSubmissionMetaRepository.get_by_id) – Get an entity by its ID.
- [**update**](#leadr.scores.services.anti_cheat_repositories.ScoreSubmissionMetaRepository.update) – Update an existing entity in the database.

**Attributes:**

- [**session**](#leadr.scores.services.anti_cheat_repositories.ScoreSubmissionMetaRepository.session) –

####### `leadr.scores.services.anti_cheat_repositories.ScoreSubmissionMetaRepository.create`

```python
create(entity)
```

Create a new entity in the database.

**Parameters:**

- **entity** (<code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code>) – Domain entity to create

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code> – Created domain entity with refreshed data

####### `leadr.scores.services.anti_cheat_repositories.ScoreSubmissionMetaRepository.delete`

```python
delete(entity_id)
```

Soft delete an entity by setting its deleted_at timestamp.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – ID of entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

####### `leadr.scores.services.anti_cheat_repositories.ScoreSubmissionMetaRepository.filter`

```python
filter(account_id=None, board_id=None, device_id=None, **kwargs)
```

Filter submission metadata by account and optional criteria.

Joins with scores table to filter by account_id since submission meta doesn't have
a direct account relation.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – REQUIRED - Account ID to filter by (multi-tenant safety)
- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None</code>) – Optional board ID to filter by
- **device_id** (<code>[DeviceID](./common.md#leadr.common.domain.ids.DeviceID) | None</code>) – Optional device ID to filter by
- \*\***kwargs** (<code>[Any](#typing.Any)</code>) – Additional filter parameters (reserved for future use)

**Returns:**

- <code>[list](#list)\[[ScoreSubmissionMeta](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta)\]</code> – List of submission metadata for the account matching the filter criteria

####### `leadr.scores.services.anti_cheat_repositories.ScoreSubmissionMetaRepository.get_by_device_and_board`

```python
get_by_device_and_board(device_id, board_id)
```

Get submission metadata for a device/board combination.

**Parameters:**

- **device_id** (<code>[DeviceID](./common.md#leadr.common.domain.ids.DeviceID)</code>) – ID of the device submitting scores
- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – ID of the board being submitted to

**Returns:**

- <code>[ScoreSubmissionMeta](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta) | None</code> – ScoreSubmissionMeta if found, None otherwise

####### `leadr.scores.services.anti_cheat_repositories.ScoreSubmissionMetaRepository.get_by_id`

```python
get_by_id(entity_id, include_deleted=False)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – Entity ID to retrieve
- **include_deleted** (<code>[bool](#bool)</code>) – If True, include soft-deleted entities. Defaults to False.

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT) | None</code> – Domain entity if found, None otherwise

####### `leadr.scores.services.anti_cheat_repositories.ScoreSubmissionMetaRepository.session`

```python
session = session
```

####### `leadr.scores.services.anti_cheat_repositories.ScoreSubmissionMetaRepository.update`

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

##### `leadr.scores.services.anti_cheat_service`

Anti-cheat service for detecting suspicious score submissions.

**Classes:**

- [**AntiCheatService**](#leadr.scores.services.anti_cheat_service.AntiCheatService) – Service for anti-cheat detection and analysis.

###### `leadr.scores.services.anti_cheat_service.AntiCheatService`

```python
AntiCheatService(session)
```

Service for anti-cheat detection and analysis.

Implements various detection tactics to identify suspicious score submissions:

- Rate limiting: Prevents excessive submissions per device/board
- Duplicate detection: Identifies repeated identical scores
- Velocity detection: Detects rapid-fire submissions
- Statistical outliers: Identifies anomalous scores
- Pattern detection: Finds suspicious submission patterns

**Functions:**

- [**check_submission**](#leadr.scores.services.anti_cheat_service.AntiCheatService.check_submission) – Check a score submission for suspicious patterns.

**Attributes:**

- [**meta_repo**](#leadr.scores.services.anti_cheat_service.AntiCheatService.meta_repo) –
- [**session**](#leadr.scores.services.anti_cheat_service.AntiCheatService.session) –

**Parameters:**

- **session** (<code>[AsyncSession](#sqlalchemy.ext.asyncio.AsyncSession)</code>) – Database session for querying metadata

####### `leadr.scores.services.anti_cheat_service.AntiCheatService.check_submission`

```python
check_submission(score, trust_tier, device_id, board_id)
```

Check a score submission for suspicious patterns.

**Parameters:**

- **score** (<code>[Score](./scores.md#leadr.scores.domain.score.Score)</code>) – Score being submitted
- **trust_tier** (<code>[TrustTier](#leadr.scores.domain.anti_cheat.enums.TrustTier)</code>) – Trust tier of the device (A/B/C)
- **device_id** (<code>[DeviceID](./common.md#leadr.common.domain.ids.DeviceID)</code>) – ID of the device submitting the score
- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – ID of the board being submitted to

**Returns:**

- <code>[AntiCheatResult](#leadr.scores.domain.anti_cheat.models.AntiCheatResult)</code> – AntiCheatResult indicating action to take (ACCEPT/FLAG/REJECT)

####### `leadr.scores.services.anti_cheat_service.AntiCheatService.meta_repo`

```python
meta_repo = ScoreSubmissionMetaRepository(session)
```

####### `leadr.scores.services.anti_cheat_service.AntiCheatService.session`

```python
session = session
```

##### `leadr.scores.services.dependencies`

Score service dependencies for FastAPI dependency injection.

**Functions:**

- [**get_score_flag_service**](#leadr.scores.services.dependencies.get_score_flag_service) – Get ScoreFlagService dependency.
- [**get_score_service**](#leadr.scores.services.dependencies.get_score_service) – Get ScoreService dependency.
- [**get_score_submission_meta_service**](#leadr.scores.services.dependencies.get_score_submission_meta_service) – Get ScoreSubmissionMetaService dependency.

**Attributes:**

- [**ScoreFlagServiceDep**](./scores.md#leadr.scores.services.dependencies.ScoreFlagServiceDep) –
- [**ScoreServiceDep**](./scores.md#leadr.scores.services.dependencies.ScoreServiceDep) –
- [**ScoreSubmissionMetaServiceDep**](./scores.md#leadr.scores.services.dependencies.ScoreSubmissionMetaServiceDep) –

###### `leadr.scores.services.dependencies.ScoreFlagServiceDep`

```python
ScoreFlagServiceDep = Annotated[ScoreFlagService, Depends(get_score_flag_service)]
```

###### `leadr.scores.services.dependencies.ScoreServiceDep`

```python
ScoreServiceDep = Annotated[ScoreService, Depends(get_score_service)]
```

###### `leadr.scores.services.dependencies.ScoreSubmissionMetaServiceDep`

```python
ScoreSubmissionMetaServiceDep = Annotated[ScoreSubmissionMetaService, Depends(get_score_submission_meta_service)]
```

###### `leadr.scores.services.dependencies.get_score_flag_service`

```python
get_score_flag_service(db)
```

Get ScoreFlagService dependency.

**Parameters:**

- **db** (<code>[DatabaseSession](./common.md#leadr.common.dependencies.DatabaseSession)</code>) – Database session from dependency injection

**Returns:**

- <code>[ScoreFlagService](#leadr.scores.services.score_flag_service.ScoreFlagService)</code> – Initialized ScoreFlagService instance

###### `leadr.scores.services.dependencies.get_score_service`

```python
get_score_service(db)
```

Get ScoreService dependency.

**Parameters:**

- **db** (<code>[DatabaseSession](./common.md#leadr.common.dependencies.DatabaseSession)</code>) – Database session from dependency injection

**Returns:**

- <code>[ScoreService](#leadr.scores.services.score_service.ScoreService)</code> – Initialized ScoreService instance

###### `leadr.scores.services.dependencies.get_score_submission_meta_service`

```python
get_score_submission_meta_service(db)
```

Get ScoreSubmissionMetaService dependency.

**Parameters:**

- **db** (<code>[DatabaseSession](./common.md#leadr.common.dependencies.DatabaseSession)</code>) – Database session from dependency injection

**Returns:**

- <code>[ScoreSubmissionMetaService](#leadr.scores.services.score_submission_meta_service.ScoreSubmissionMetaService)</code> – Initialized ScoreSubmissionMetaService instance

##### `leadr.scores.services.repositories`

Score repository services.

**Classes:**

- [**ScoreRepository**](./scores.md#leadr.scores.services.repositories.ScoreRepository) – Score repository for managing score persistence.

###### `leadr.scores.services.repositories.ScoreRepository`

Bases: <code>[BaseRepository](./common.md#leadr.common.repositories.BaseRepository)\[[Score](./scores.md#leadr.scores.domain.score.Score), [ScoreORM](./scores.md#leadr.scores.adapters.orm.ScoreORM)\]</code>

Score repository for managing score persistence.

**Functions:**

- [**create**](./scores.md#leadr.scores.services.repositories.ScoreRepository.create) – Create a new entity in the database.
- [**delete**](./scores.md#leadr.scores.services.repositories.ScoreRepository.delete) – Soft delete an entity by setting its deleted_at timestamp.
- [**filter**](./scores.md#leadr.scores.services.repositories.ScoreRepository.filter) – Filter scores by account and optional criteria.
- [**get_by_id**](#leadr.scores.services.repositories.ScoreRepository.get_by_id) – Get an entity by its ID.
- [**update**](./scores.md#leadr.scores.services.repositories.ScoreRepository.update) – Update an existing entity in the database.

**Attributes:**

- [**SORTABLE_FIELDS**](#leadr.scores.services.repositories.ScoreRepository.SORTABLE_FIELDS) –
- [**session**](./scores.md#leadr.scores.services.repositories.ScoreRepository.session) –

####### `leadr.scores.services.repositories.ScoreRepository.SORTABLE_FIELDS`

```python
SORTABLE_FIELDS = {'id', 'value', 'player_name', 'filter_timezone', 'filter_country', 'filter_city', 'created_at', 'updated_at'}
```

####### `leadr.scores.services.repositories.ScoreRepository.create`

```python
create(entity)
```

Create a new entity in the database.

**Parameters:**

- **entity** (<code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code>) – Domain entity to create

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code> – Created domain entity with refreshed data

####### `leadr.scores.services.repositories.ScoreRepository.delete`

```python
delete(entity_id)
```

Soft delete an entity by setting its deleted_at timestamp.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – ID of entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

####### `leadr.scores.services.repositories.ScoreRepository.filter`

```python
filter(account_id=None, board_id=None, game_id=None, device_id=None, pagination=None, **kwargs)
```

Filter scores by account and optional criteria.

**Parameters:**

- **account_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID) | None</code>) – REQUIRED - Account ID to filter by (multi-tenant safety)
- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None</code>) – Optional board ID to filter by
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID) | None</code>) – Optional game ID to filter by
- **device_id** (<code>[DeviceID](./common.md#leadr.common.domain.ids.DeviceID) | None</code>) – Optional device ID to filter by
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams) | None</code>) – Optional pagination parameters
- \*\***kwargs** (<code>[Any](#typing.Any)</code>) – Additional filter parameters (reserved for future use)

**Returns:**

- <code>[list](#list)\[[Score](./scores.md#leadr.scores.domain.score.Score)\] | [PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[Score](./scores.md#leadr.scores.domain.score.Score)\]</code> – List of scores if no pagination, PaginatedResult if pagination provided

**Raises:**

- <code>[ValueError](#ValueError)</code> – If account_id is None (required for multi-tenant safety)
- <code>[ValueError](#ValueError)</code> – If sort field is not in SORTABLE_FIELDS
- <code>[CursorValidationError](#CursorValidationError)</code> – If cursor is invalid or state doesn't match

####### `leadr.scores.services.repositories.ScoreRepository.get_by_id`

```python
get_by_id(entity_id, include_deleted=False)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – Entity ID to retrieve
- **include_deleted** (<code>[bool](#bool)</code>) – If True, include soft-deleted entities. Defaults to False.

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT) | None</code> – Domain entity if found, None otherwise

####### `leadr.scores.services.repositories.ScoreRepository.session`

```python
session = session
```

####### `leadr.scores.services.repositories.ScoreRepository.update`

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

##### `leadr.scores.services.score_flag_service`

Score flag service for managing flag operations.

**Classes:**

- [**ScoreFlagService**](#leadr.scores.services.score_flag_service.ScoreFlagService) – Service for managing score flag lifecycle and operations.

###### `leadr.scores.services.score_flag_service.ScoreFlagService`

Bases: <code>[BaseService](./common.md#leadr.common.services.BaseService)\[[ScoreFlag](#leadr.scores.domain.anti_cheat.models.ScoreFlag), [ScoreFlagRepository](#leadr.scores.services.anti_cheat_repositories.ScoreFlagRepository)\]</code>

Service for managing score flag lifecycle and operations.

This service orchestrates flag listing, retrieval, and review operations
by coordinating between the domain models and repository layer.

**Functions:**

- [**delete**](#leadr.scores.services.score_flag_service.ScoreFlagService.delete) – Soft-delete an entity.
- [**get_by_id**](#leadr.scores.services.score_flag_service.ScoreFlagService.get_by_id) – Get an entity by its ID.
- [**get_by_id_or_raise**](#leadr.scores.services.score_flag_service.ScoreFlagService.get_by_id_or_raise) – Get an entity by its ID or raise EntityNotFoundError.
- [**get_flag**](#leadr.scores.services.score_flag_service.ScoreFlagService.get_flag) – Get a flag by its ID.
- [**list_all**](#leadr.scores.services.score_flag_service.ScoreFlagService.list_all) – List all non-deleted entities.
- [**list_flags**](#leadr.scores.services.score_flag_service.ScoreFlagService.list_flags) – List score flags for an account with optional filters.
- [**review_flag**](#leadr.scores.services.score_flag_service.ScoreFlagService.review_flag) – Review a flag and update its status.
- [**soft_delete**](#leadr.scores.services.score_flag_service.ScoreFlagService.soft_delete) – Soft-delete an entity and return it before deletion.
- [**update_flag**](#leadr.scores.services.score_flag_service.ScoreFlagService.update_flag) – Update a flag's status and/or reviewer decision.

**Attributes:**

- [**repository**](#leadr.scores.services.score_flag_service.ScoreFlagService.repository) –

####### `leadr.scores.services.score_flag_service.ScoreFlagService.delete`

```python
delete(entity_id)
```

Soft-delete an entity.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – The ID of the entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the entity doesn't exist

####### `leadr.scores.services.score_flag_service.ScoreFlagService.get_by_id`

```python
get_by_id(entity_id)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – The ID of the entity to retrieve

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.services.DomainEntityT) | None</code> – The domain entity if found, None otherwise

####### `leadr.scores.services.score_flag_service.ScoreFlagService.get_by_id_or_raise`

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

####### `leadr.scores.services.score_flag_service.ScoreFlagService.get_flag`

```python
get_flag(flag_id)
```

Get a flag by its ID.

**Parameters:**

- **flag_id** (<code>[ScoreFlagID](./common.md#leadr.common.domain.ids.ScoreFlagID)</code>) – The ID of the flag to retrieve

**Returns:**

- <code>[ScoreFlag](#leadr.scores.domain.anti_cheat.models.ScoreFlag) | None</code> – The flag if found, None otherwise

<details class="example" open markdown="1">
<summary>Example</summary>

> > > flag = await service.get_flag(flag_id)

</details>

####### `leadr.scores.services.score_flag_service.ScoreFlagService.list_all`

```python
list_all()
```

List all non-deleted entities.

**Returns:**

- <code>[list](#list)\[[DomainEntityT](./common.md#leadr.common.services.DomainEntityT)\]</code> – List of domain entities

####### `leadr.scores.services.score_flag_service.ScoreFlagService.list_flags`

```python
list_flags(account_id, board_id=None, game_id=None, status=None, flag_type=None)
```

List score flags for an account with optional filters.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – REQUIRED - Account ID to filter by (multi-tenant safety)
- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None</code>) – Optional board ID to filter by
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID) | None</code>) – Optional game ID to filter by
- **status** (<code>[str](#str) | None</code>) – Optional status to filter by (PENDING, CONFIRMED_CHEAT, etc.)
- **flag_type** (<code>[str](#str) | None</code>) – Optional flag type to filter by (VELOCITY, DUPLICATE, etc.)

**Returns:**

- <code>[list](#list)\[[ScoreFlag](#leadr.scores.domain.anti_cheat.models.ScoreFlag)\]</code> – List of flags matching the filter criteria

<details class="example" open markdown="1">
<summary>Example</summary>

> > > flags = await service.list_flags(
> > > ... account_id=account.id,
> > > ... status="PENDING",
> > > ... )

</details>

####### `leadr.scores.services.score_flag_service.ScoreFlagService.repository`

```python
repository = self._create_repository(session)
```

####### `leadr.scores.services.score_flag_service.ScoreFlagService.review_flag`

```python
review_flag(flag_id, status, reviewer_decision=None, reviewer_id=None)
```

Review a flag and update its status.

**Parameters:**

- **flag_id** (<code>[ScoreFlagID](./common.md#leadr.common.domain.ids.ScoreFlagID)</code>) – The ID of the flag to review
- **status** (<code>[ScoreFlagStatus](#leadr.scores.domain.anti_cheat.enums.ScoreFlagStatus)</code>) – New status (CONFIRMED_CHEAT, FALSE_POSITIVE, DISMISSED)
- **reviewer_decision** (<code>[str](#str) | None</code>) – Optional admin notes/decision
- **reviewer_id** (<code>[UserID](./common.md#leadr.common.domain.ids.UserID) | None</code>) – Optional ID of the reviewing admin

**Returns:**

- <code>[ScoreFlag](#leadr.scores.domain.anti_cheat.models.ScoreFlag)</code> – The updated flag

**Raises:**

- <code>[EntityNotFoundError](#EntityNotFoundError)</code> – If the flag doesn't exist

<details class="example" open markdown="1">
<summary>Example</summary>

> > > flag = await service.review_flag(
> > > ... flag_id=flag.id,
> > > ... status=ScoreFlagStatus.CONFIRMED_CHEAT,
> > > ... reviewer_decision="Verified cheating behavior",
> > > ... )

</details>

####### `leadr.scores.services.score_flag_service.ScoreFlagService.soft_delete`

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

####### `leadr.scores.services.score_flag_service.ScoreFlagService.update_flag`

```python
update_flag(flag_id, status=None, reviewer_decision=None)
```

Update a flag's status and/or reviewer decision.

**Parameters:**

- **flag_id** (<code>[ScoreFlagID](./common.md#leadr.common.domain.ids.ScoreFlagID)</code>) – The ID of the flag to update
- **status** (<code>[ScoreFlagStatus](#leadr.scores.domain.anti_cheat.enums.ScoreFlagStatus) | None</code>) – Optional new status
- **reviewer_decision** (<code>[str](#str) | None</code>) – Optional new reviewer decision

**Returns:**

- <code>[ScoreFlag](#leadr.scores.domain.anti_cheat.models.ScoreFlag)</code> – The updated flag

**Raises:**

- <code>[EntityNotFoundError](#EntityNotFoundError)</code> – If the flag doesn't exist

<details class="example" open markdown="1">
<summary>Example</summary>

> > > flag = await service.update_flag(
> > > ... flag_id=flag.id,
> > > ... status=ScoreFlagStatus.FALSE_POSITIVE,
> > > ... )

</details>

##### `leadr.scores.services.score_service`

Score service for managing score operations.

**Classes:**

- [**ScoreService**](#leadr.scores.services.score_service.ScoreService) – Service for managing score lifecycle and operations.

###### `leadr.scores.services.score_service.ScoreService`

Bases: <code>[BaseService](./common.md#leadr.common.services.BaseService)\[[Score](./scores.md#leadr.scores.domain.score.Score), [ScoreRepository](./scores.md#leadr.scores.services.repositories.ScoreRepository)\]</code>

Service for managing score lifecycle and operations.

This service orchestrates score creation, updates, and retrieval
by coordinating between the domain models and repository layer.
Ensures business rules like board/game validation are enforced.

**Functions:**

- [**create_score**](#leadr.scores.services.score_service.ScoreService.create_score) – Create a new score.
- [**delete**](#leadr.scores.services.score_service.ScoreService.delete) – Soft-delete an entity.
- [**get_by_id**](#leadr.scores.services.score_service.ScoreService.get_by_id) – Get an entity by its ID.
- [**get_by_id_or_raise**](#leadr.scores.services.score_service.ScoreService.get_by_id_or_raise) – Get an entity by its ID or raise EntityNotFoundError.
- [**get_score**](#leadr.scores.services.score_service.ScoreService.get_score) – Get a score by its ID.
- [**list_all**](#leadr.scores.services.score_service.ScoreService.list_all) – List all non-deleted entities.
- [**list_scores**](#leadr.scores.services.score_service.ScoreService.list_scores) – List scores for an account with optional filters and pagination.
- [**soft_delete**](#leadr.scores.services.score_service.ScoreService.soft_delete) – Soft-delete an entity and return it before deletion.
- [**update_score**](#leadr.scores.services.score_service.ScoreService.update_score) – Update a score's mutable fields.
- [**update_submission_metadata**](#leadr.scores.services.score_service.ScoreService.update_submission_metadata) – Update submission metadata and create flags if needed.

**Attributes:**

- [**repository**](#leadr.scores.services.score_service.ScoreService.repository) –

####### `leadr.scores.services.score_service.ScoreService.create_score`

```python
create_score(account_id, game_id, board_id, device_id, player_name, value, value_display=None, timezone=None, country=None, city=None, metadata=None, trust_tier=TrustTier.B, background_tasks=None)
```

Create a new score.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – The ID of the account this score belongs to.
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) – The ID of the game this score belongs to.
- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – The ID of the board this score belongs to.
- **device_id** (<code>[DeviceID](./common.md#leadr.common.domain.ids.DeviceID)</code>) – The ID of the device that submitted this score.
- **player_name** (<code>[str](#str)</code>) – Display name of the player.
- **value** (<code>[float](#float)</code>) – Numeric value of the score for sorting/comparison.
- **value_display** (<code>[str](#str) | None</code>) – Optional formatted display string.
- **timezone** (<code>[str](#str) | None</code>) – Optional timezone filter for categorization.
- **country** (<code>[str](#str) | None</code>) – Optional country filter for categorization.
- **city** (<code>[str](#str) | None</code>) – Optional city filter for categorization.
- **metadata** (<code>[Any](#typing.Any) | None</code>) – Optional JSON metadata for game-specific data.
- **trust_tier** (<code>[TrustTier](#leadr.scores.domain.anti_cheat.enums.TrustTier)</code>) – Trust tier of the device (defaults to B/medium trust).

**Returns:**

- <code>[tuple](#tuple)\[[Score](./scores.md#leadr.scores.domain.score.Score), [AntiCheatResult](#leadr.scores.domain.anti_cheat.models.AntiCheatResult) | None\]</code> – Tuple of (created Score domain entity, AntiCheatResult or None).

**Raises:**

- <code>[EntityNotFoundError](#EntityNotFoundError)</code> – If the board doesn't exist.
- <code>[ValueError](#ValueError)</code> – If validation fails (board doesn't belong to account,
  game doesn't match board's game, or anti-cheat rejects submission).

<details class="example" open markdown="1">
<summary>Example</summary>

> > > score = await service.create_score(
> > > ... account_id=account.id,
> > > ... game_id=game.id,
> > > ... board_id=board.id,
> > > ... device_id=device.id,
> > > ... player_name="SpeedRunner99",
> > > ... value=123.45,
> > > ... )

</details>

####### `leadr.scores.services.score_service.ScoreService.delete`

```python
delete(entity_id)
```

Soft-delete an entity.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – The ID of the entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the entity doesn't exist

####### `leadr.scores.services.score_service.ScoreService.get_by_id`

```python
get_by_id(entity_id)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – The ID of the entity to retrieve

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.services.DomainEntityT) | None</code> – The domain entity if found, None otherwise

####### `leadr.scores.services.score_service.ScoreService.get_by_id_or_raise`

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

####### `leadr.scores.services.score_service.ScoreService.get_score`

```python
get_score(score_id)
```

Get a score by its ID.

**Parameters:**

- **score_id** (<code>[ScoreID](./common.md#leadr.common.domain.ids.ScoreID)</code>) – The ID of the score to retrieve.

**Returns:**

- <code>[Score](./scores.md#leadr.scores.domain.score.Score) | None</code> – The Score domain entity if found, None otherwise.

####### `leadr.scores.services.score_service.ScoreService.list_all`

```python
list_all()
```

List all non-deleted entities.

**Returns:**

- <code>[list](#list)\[[DomainEntityT](./common.md#leadr.common.services.DomainEntityT)\]</code> – List of domain entities

####### `leadr.scores.services.score_service.ScoreService.list_scores`

```python
list_scores(account_id, board_id=None, game_id=None, device_id=None, pagination=None)
```

List scores for an account with optional filters and pagination.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – REQUIRED - Account ID to filter by (multi-tenant safety).
- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None</code>) – Optional board ID to filter by.
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID) | None</code>) – Optional game ID to filter by.
- **device_id** (<code>[DeviceID](./common.md#leadr.common.domain.ids.DeviceID) | None</code>) – Optional device ID to filter by.
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams) | None</code>) – Optional pagination parameters.

**Returns:**

- <code>[list](#list)\[[Score](./scores.md#leadr.scores.domain.score.Score)\] | [PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[Score](./scores.md#leadr.scores.domain.score.Score)\]</code> – List of Score entities if no pagination, PaginatedResult if pagination provided.

####### `leadr.scores.services.score_service.ScoreService.repository`

```python
repository = self._create_repository(session)
```

####### `leadr.scores.services.score_service.ScoreService.soft_delete`

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

####### `leadr.scores.services.score_service.ScoreService.update_score`

```python
update_score(score_id, player_name=None, value=None, value_display=None, timezone=None, country=None, city=None, metadata=None)
```

Update a score's mutable fields.

**Parameters:**

- **score_id** (<code>[ScoreID](./common.md#leadr.common.domain.ids.ScoreID)</code>) – The ID of the score to update.
- **player_name** (<code>[str](#str) | None</code>) – Optional new player name.
- **value** (<code>[float](#float) | None</code>) – Optional new value.
- **value_display** (<code>[str](#str) | None</code>) – Optional new value display string.
- **timezone** (<code>[str](#str) | None</code>) – Optional new timezone.
- **country** (<code>[str](#str) | None</code>) – Optional new country.
- **city** (<code>[str](#str) | None</code>) – Optional new city.
- **metadata** (<code>[Any](#typing.Any) | None</code>) – Optional new metadata.

**Returns:**

- <code>[Score](./scores.md#leadr.scores.domain.score.Score)</code> – The updated Score entity.

**Raises:**

- <code>[EntityNotFoundError](#EntityNotFoundError)</code> – If the score doesn't exist.

####### `leadr.scores.services.score_service.ScoreService.update_submission_metadata`

```python
update_submission_metadata(saved_score, device_id, board_id, anti_cheat_result)
```

Update submission metadata and create flags if needed.

This method is designed to be called as a background task after score creation
to avoid blocking the HTTP response.

**Parameters:**

- **saved_score** (<code>[Score](./scores.md#leadr.scores.domain.score.Score)</code>) – The score that was created
- **device_id** (<code>[DeviceID](./common.md#leadr.common.domain.ids.DeviceID)</code>) – ID of the device that submitted the score
- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – ID of the board the score was submitted to
- **anti_cheat_result** (<code>[AntiCheatResult](#leadr.scores.domain.anti_cheat.models.AntiCheatResult) | None</code>) – Result from anti-cheat check (or None)

##### `leadr.scores.services.score_submission_meta_service`

Service for score submission metadata management.

**Classes:**

- [**ScoreSubmissionMetaService**](#leadr.scores.services.score_submission_meta_service.ScoreSubmissionMetaService) – Service for managing score submission metadata.

###### `leadr.scores.services.score_submission_meta_service.ScoreSubmissionMetaService`

Bases: <code>[BaseService](./common.md#leadr.common.services.BaseService)\[[ScoreSubmissionMeta](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta), [ScoreSubmissionMetaRepository](#leadr.scores.services.anti_cheat_repositories.ScoreSubmissionMetaRepository)\]</code>

Service for managing score submission metadata.

Provides read-only access to submission metadata for debugging and analysis.

**Functions:**

- [**delete**](#leadr.scores.services.score_submission_meta_service.ScoreSubmissionMetaService.delete) – Soft-delete an entity.
- [**get_by_id**](#leadr.scores.services.score_submission_meta_service.ScoreSubmissionMetaService.get_by_id) – Get an entity by its ID.
- [**get_by_id_or_raise**](#leadr.scores.services.score_submission_meta_service.ScoreSubmissionMetaService.get_by_id_or_raise) – Get an entity by its ID or raise EntityNotFoundError.
- [**get_submission_meta**](#leadr.scores.services.score_submission_meta_service.ScoreSubmissionMetaService.get_submission_meta) – Get submission metadata by its ID.
- [**list_all**](#leadr.scores.services.score_submission_meta_service.ScoreSubmissionMetaService.list_all) – List all non-deleted entities.
- [**list_submission_meta**](#leadr.scores.services.score_submission_meta_service.ScoreSubmissionMetaService.list_submission_meta) – List score submission metadata for an account with optional filters.
- [**soft_delete**](#leadr.scores.services.score_submission_meta_service.ScoreSubmissionMetaService.soft_delete) – Soft-delete an entity and return it before deletion.

**Attributes:**

- [**repository**](#leadr.scores.services.score_submission_meta_service.ScoreSubmissionMetaService.repository) –

####### `leadr.scores.services.score_submission_meta_service.ScoreSubmissionMetaService.delete`

```python
delete(entity_id)
```

Soft-delete an entity.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – The ID of the entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the entity doesn't exist

####### `leadr.scores.services.score_submission_meta_service.ScoreSubmissionMetaService.get_by_id`

```python
get_by_id(entity_id)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – The ID of the entity to retrieve

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.services.DomainEntityT) | None</code> – The domain entity if found, None otherwise

####### `leadr.scores.services.score_submission_meta_service.ScoreSubmissionMetaService.get_by_id_or_raise`

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

####### `leadr.scores.services.score_submission_meta_service.ScoreSubmissionMetaService.get_submission_meta`

```python
get_submission_meta(meta_id)
```

Get submission metadata by its ID.

**Parameters:**

- **meta_id** (<code>[ScoreSubmissionMetaID](./common.md#leadr.common.domain.ids.ScoreSubmissionMetaID)</code>) – The ID of the submission metadata to retrieve

**Returns:**

- <code>[ScoreSubmissionMeta](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta) | None</code> – The submission metadata if found, None otherwise

<details class="example" open markdown="1">
<summary>Example</summary>

> > > meta = await service.get_submission_meta(meta_id)

</details>

####### `leadr.scores.services.score_submission_meta_service.ScoreSubmissionMetaService.list_all`

```python
list_all()
```

List all non-deleted entities.

**Returns:**

- <code>[list](#list)\[[DomainEntityT](./common.md#leadr.common.services.DomainEntityT)\]</code> – List of domain entities

####### `leadr.scores.services.score_submission_meta_service.ScoreSubmissionMetaService.list_submission_meta`

```python
list_submission_meta(account_id, board_id=None, device_id=None)
```

List score submission metadata for an account with optional filters.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – REQUIRED - Account ID to filter by (multi-tenant safety)
- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None</code>) – Optional board ID to filter by
- **device_id** (<code>[DeviceID](./common.md#leadr.common.domain.ids.DeviceID) | None</code>) – Optional device ID to filter by

**Returns:**

- <code>[list](#list)\[[ScoreSubmissionMeta](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta)\]</code> – List of submission metadata matching the filter criteria

<details class="example" open markdown="1">
<summary>Example</summary>

> > > metas = await service.list_submission_meta(
> > > ... account_id=account.id,
> > > ... board_id=board.id,
> > > ... )

</details>

####### `leadr.scores.services.score_submission_meta_service.ScoreSubmissionMetaService.repository`

```python
repository = self._create_repository(session)
```

####### `leadr.scores.services.score_submission_meta_service.ScoreSubmissionMetaService.soft_delete`

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
