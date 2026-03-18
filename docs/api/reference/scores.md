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

- [**ScoreEventORM**](./scores.md#leadr.scores.adapters.orm.ScoreEventORM) – Score event ORM model for append-only event sourcing.
- [**ScoreFlagORM**](./scores.md#leadr.scores.adapters.orm.ScoreFlagORM) – Score flag ORM model for anti-cheat detections.
- [**ScoreSubmissionMetaORM**](./scores.md#leadr.scores.adapters.orm.ScoreSubmissionMetaORM) – Score submission metadata ORM model for anti-cheat tracking.

###### `leadr.scores.adapters.orm.ScoreEventORM`

Bases: <code>[ImmutableBase](./common.md#leadr.common.orm.ImmutableBase)</code>

Score event ORM model for append-only event sourcing.

Represents an immutable fact about a score submission in the database.
ScoreEvents are never updated or deleted - they are append-only.
Maps to the score_events table with foreign keys to accounts, games, boards, and identities.

**Attributes:**

- [**account**](./scores.md#leadr.scores.adapters.orm.ScoreEventORM.account) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[AccountORM](./accounts.md#leadr.accounts.adapters.orm.AccountORM)\]</code>) –
- [**account_id**](#leadr.scores.adapters.orm.ScoreEventORM.account_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**board**](./scores.md#leadr.scores.adapters.orm.ScoreEventORM.board) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[BoardORM](./boards.md#leadr.boards.adapters.orm.BoardORM)\]</code>) –
- [**board_id**](#leadr.scores.adapters.orm.ScoreEventORM.board_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**city**](./scores.md#leadr.scores.adapters.orm.ScoreEventORM.city) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**country**](./scores.md#leadr.scores.adapters.orm.ScoreEventORM.country) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**created_at**](#leadr.scores.adapters.orm.ScoreEventORM.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**event_payload**](#leadr.scores.adapters.orm.ScoreEventORM.event_payload) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[dict](#dict)\[[str](#str), [Any](#typing.Any)\]\]</code>) –
- [**game**](./scores.md#leadr.scores.adapters.orm.ScoreEventORM.game) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[GameORM](./games.md#leadr.games.adapters.orm.GameORM)\]</code>) –
- [**game_id**](#leadr.scores.adapters.orm.ScoreEventORM.game_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**id**](./scores.md#leadr.scores.adapters.orm.ScoreEventORM.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**identity**](./scores.md#leadr.scores.adapters.orm.ScoreEventORM.identity) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[IdentityORM](./auth.md#leadr.auth.adapters.orm.IdentityORM)\]</code>) –
- [**identity_id**](#leadr.scores.adapters.orm.ScoreEventORM.identity_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**is_test**](#leadr.scores.adapters.orm.ScoreEventORM.is_test) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[bool](#bool)\]</code>) –
- [**metadata**](./scores.md#leadr.scores.adapters.orm.ScoreEventORM.metadata) –
- [**registry**](./scores.md#leadr.scores.adapters.orm.ScoreEventORM.registry) –
- [**timezone**](./scores.md#leadr.scores.adapters.orm.ScoreEventORM.timezone) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –

####### `leadr.scores.adapters.orm.ScoreEventORM.account`

```python
account: Mapped[AccountORM] = relationship('AccountORM')
```

####### `leadr.scores.adapters.orm.ScoreEventORM.account_id`

```python
account_id: Mapped[UUID] = mapped_column(ForeignKey('accounts.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.scores.adapters.orm.ScoreEventORM.board`

```python
board: Mapped[BoardORM] = relationship('BoardORM')
```

####### `leadr.scores.adapters.orm.ScoreEventORM.board_id`

```python
board_id: Mapped[UUID] = mapped_column(ForeignKey('boards.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.scores.adapters.orm.ScoreEventORM.city`

```python
city: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
```

####### `leadr.scores.adapters.orm.ScoreEventORM.country`

```python
country: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
```

####### `leadr.scores.adapters.orm.ScoreEventORM.created_at`

```python
created_at: Mapped[timestamp]
```

####### `leadr.scores.adapters.orm.ScoreEventORM.event_payload`

```python
event_payload: Mapped[dict[str, Any]] = mapped_column(JSONB, nullable=False, default=dict, server_default='{}')
```

####### `leadr.scores.adapters.orm.ScoreEventORM.game`

```python
game: Mapped[GameORM] = relationship('GameORM')
```

####### `leadr.scores.adapters.orm.ScoreEventORM.game_id`

```python
game_id: Mapped[UUID] = mapped_column(ForeignKey('games.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.scores.adapters.orm.ScoreEventORM.id`

```python
id: Mapped[uuid_pk]
```

####### `leadr.scores.adapters.orm.ScoreEventORM.identity`

```python
identity: Mapped[IdentityORM] = relationship('IdentityORM')
```

####### `leadr.scores.adapters.orm.ScoreEventORM.identity_id`

```python
identity_id: Mapped[UUID] = mapped_column(ForeignKey('identities.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.scores.adapters.orm.ScoreEventORM.is_test`

```python
is_test: Mapped[bool] = mapped_column(Boolean, nullable=False, default=False)
```

####### `leadr.scores.adapters.orm.ScoreEventORM.metadata`

```python
metadata = Base.metadata
```

####### `leadr.scores.adapters.orm.ScoreEventORM.registry`

```python
registry = Base.registry
```

####### `leadr.scores.adapters.orm.ScoreEventORM.timezone`

```python
timezone: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
```

###### `leadr.scores.adapters.orm.ScoreFlagORM`

Bases: <code>[Base](./common.md#leadr.common.orm.Base)</code>

Score flag ORM model for anti-cheat detections.

Records suspicious patterns detected by the anti-cheat system.
Flags can be reviewed by admins to confirm or dismiss detections.
Uses score_event_id instead of score_id, linking to the immutable
ScoreEvent in the event-sourcing architecture.

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
- [**score_event**](#leadr.scores.adapters.orm.ScoreFlagORM.score_event) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[ScoreEventORM](./scores.md#leadr.scores.adapters.orm.ScoreEventORM)\]</code>) –
- [**score_event_id**](#leadr.scores.adapters.orm.ScoreFlagORM.score_event_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
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

####### `leadr.scores.adapters.orm.ScoreFlagORM.score_event`

```python
score_event: Mapped[ScoreEventORM] = relationship('ScoreEventORM')
```

####### `leadr.scores.adapters.orm.ScoreFlagORM.score_event_id`

```python
score_event_id: Mapped[UUID] = mapped_column(ForeignKey('score_events.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.scores.adapters.orm.ScoreFlagORM.status`

```python
status: Mapped[str] = mapped_column(String, nullable=False, default='pending', index=True)
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

###### `leadr.scores.adapters.orm.ScoreSubmissionMetaORM`

Bases: <code>[Base](./common.md#leadr.common.orm.Base)</code>

Score submission metadata ORM model for anti-cheat tracking.

Tracks submission history per identity/board combination to enable
detection of suspicious patterns like rapid-fire submissions.
Uses identity_id as the tracking key instead of device_id, aligning with
the event-sourcing architecture where identity is the ranking key.

**Functions:**

- [**from_domain**](#leadr.scores.adapters.orm.ScoreSubmissionMetaORM.from_domain) – Convert domain entity to ORM model.
- [**to_domain**](#leadr.scores.adapters.orm.ScoreSubmissionMetaORM.to_domain) – Convert ORM model to domain entity.

**Attributes:**

- [**board**](./scores.md#leadr.scores.adapters.orm.ScoreSubmissionMetaORM.board) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[BoardORM](./boards.md#leadr.boards.adapters.orm.BoardORM)\]</code>) –
- [**board_id**](#leadr.scores.adapters.orm.ScoreSubmissionMetaORM.board_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**created_at**](#leadr.scores.adapters.orm.ScoreSubmissionMetaORM.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**deleted_at**](#leadr.scores.adapters.orm.ScoreSubmissionMetaORM.deleted_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[nullable_timestamp](#leadr.common.orm.nullable_timestamp)\]</code>) –
- [**id**](./scores.md#leadr.scores.adapters.orm.ScoreSubmissionMetaORM.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**identity**](./scores.md#leadr.scores.adapters.orm.ScoreSubmissionMetaORM.identity) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[IdentityORM](./auth.md#leadr.auth.adapters.orm.IdentityORM)\]</code>) –
- [**identity_id**](#leadr.scores.adapters.orm.ScoreSubmissionMetaORM.identity_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**last_score_value**](#leadr.scores.adapters.orm.ScoreSubmissionMetaORM.last_score_value) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[float](#float) | None\]</code>) –
- [**last_submission_at**](#leadr.scores.adapters.orm.ScoreSubmissionMetaORM.last_submission_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime)\]</code>) –
- [**score_event**](#leadr.scores.adapters.orm.ScoreSubmissionMetaORM.score_event) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[ScoreEventORM](./scores.md#leadr.scores.adapters.orm.ScoreEventORM)\]</code>) –
- [**score_event_id**](#leadr.scores.adapters.orm.ScoreSubmissionMetaORM.score_event_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**submission_count**](#leadr.scores.adapters.orm.ScoreSubmissionMetaORM.submission_count) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[int](#int)\]</code>) –
- [**updated_at**](#leadr.scores.adapters.orm.ScoreSubmissionMetaORM.updated_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –

####### `leadr.scores.adapters.orm.ScoreSubmissionMetaORM.board`

```python
board: Mapped[BoardORM] = relationship('BoardORM')
```

####### `leadr.scores.adapters.orm.ScoreSubmissionMetaORM.board_id`

```python
board_id: Mapped[UUID] = mapped_column(ForeignKey('boards.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.scores.adapters.orm.ScoreSubmissionMetaORM.created_at`

```python
created_at: Mapped[timestamp]
```

####### `leadr.scores.adapters.orm.ScoreSubmissionMetaORM.deleted_at`

```python
deleted_at: Mapped[nullable_timestamp]
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

####### `leadr.scores.adapters.orm.ScoreSubmissionMetaORM.identity`

```python
identity: Mapped[IdentityORM] = relationship('IdentityORM')
```

####### `leadr.scores.adapters.orm.ScoreSubmissionMetaORM.identity_id`

```python
identity_id: Mapped[UUID] = mapped_column(ForeignKey('identities.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.scores.adapters.orm.ScoreSubmissionMetaORM.last_score_value`

```python
last_score_value: Mapped[float | None] = mapped_column(Float, nullable=True, default=None)
```

####### `leadr.scores.adapters.orm.ScoreSubmissionMetaORM.last_submission_at`

```python
last_submission_at: Mapped[datetime] = mapped_column(DateTime(timezone=True), nullable=False)
```

####### `leadr.scores.adapters.orm.ScoreSubmissionMetaORM.score_event`

```python
score_event: Mapped[ScoreEventORM] = relationship('ScoreEventORM')
```

####### `leadr.scores.adapters.orm.ScoreSubmissionMetaORM.score_event_id`

```python
score_event_id: Mapped[UUID] = mapped_column(ForeignKey('score_events.id', ondelete='CASCADE'), nullable=False, index=True)
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

- [**score_event_routes**](#leadr.scores.api.score_event_routes) – API routes for score event management (admin only).
- [**score_event_schemas**](#leadr.scores.api.score_event_schemas) – API request and response models for score events.
- [**score_flag_routes**](#leadr.scores.api.score_flag_routes) – API routes for score flag management.
- [**score_flag_schemas**](#leadr.scores.api.score_flag_schemas) – API request and response models for score flags.
- [**score_routes**](#leadr.scores.api.score_routes) – API routes for score management.
- [**score_schemas**](#leadr.scores.api.score_schemas) – API request and response models for scores.
- [**score_submission_meta_routes**](#leadr.scores.api.score_submission_meta_routes) – API routes for score submission metadata management.
- [**score_submission_meta_schemas**](#leadr.scores.api.score_submission_meta_schemas) – API schemas for score submission metadata.

##### `leadr.scores.api.score_event_routes`

API routes for score event management (admin only).

**Functions:**

- [**create_score_event**](#leadr.scores.api.score_event_routes.create_score_event) – Create a score event (Admin API).
- [**get_score_event**](#leadr.scores.api.score_event_routes.get_score_event) – Get a single score event by ID (Admin API).
- [**list_score_events**](#leadr.scores.api.score_event_routes.list_score_events) – List score events (Admin API).

**Attributes:**

- [**router**](#leadr.scores.api.score_event_routes.router) –

###### `leadr.scores.api.score_event_routes.create_score_event`

```python
create_score_event(request, auth, score_service, board_service, background_tasks)
```

Create a score event (Admin API).

Creates a score event using the same processing as client submissions:

- Runs anti-cheat checks
- Updates rankings (BoardState/RunEntry)
- Validates board type and payload

This endpoint is for admin testing, data seeding, and demo purposes.

**Parameters:**

- **request** (<code>[ScoreEventCreateRequest](#leadr.scores.api.score_event_schemas.ScoreEventCreateRequest)</code>) – Score event creation request
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Admin authentication context
- **score_service** (<code>[ScoreServiceDep](./scores.md#leadr.scores.services.dependencies.ScoreServiceDep)</code>) – Score service for submission
- **board_service** (<code>[BoardServiceDep](./boards.md#leadr.boards.services.dependencies.BoardServiceDep)</code>) – Board service for validation

**Returns:**

- <code>[ScoreEventResponse](#leadr.scores.api.score_event_schemas.ScoreEventResponse)</code> – Created score event

**Raises:**

- <code>404</code> – Board not found
- <code>403</code> – Non-superadmin accessing another account's board
- <code>400</code> – Validation error (wrong board type, etc.)

###### `leadr.scores.api.score_event_routes.get_score_event`

```python
get_score_event(event_id, auth, service)
```

Get a single score event by ID (Admin API).

**Parameters:**

- **event_id** (<code>[ScoreEventID](./common.md#leadr.common.domain.ids.ScoreEventID)</code>) – Score event ID.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Admin authentication context.
- **service** (<code>[ScoreEventServiceDep](./scores.md#leadr.scores.services.dependencies.ScoreEventServiceDep)</code>) – Injected score event service dependency.

**Returns:**

- <code>[ScoreEventResponse](#leadr.scores.api.score_event_schemas.ScoreEventResponse)</code> – Score event details.

**Raises:**

- <code>404</code> – Score event not found.
- <code>403</code> – Non-superadmin trying to access another account's event.

###### `leadr.scores.api.score_event_routes.list_score_events`

```python
list_score_events(auth, service, pagination, account_id=None, board_id=None, identity_id=None, is_test=None)
```

List score events (Admin API).

Returns a paginated list of score events. Score events are immutable
facts about score submissions and cannot be updated or deleted.

For regular admins: account_id defaults to their account.
For superadmins: can view events across all accounts.

**Parameters:**

- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Admin authentication context.
- **service** (<code>[ScoreEventServiceDep](./scores.md#leadr.scores.services.dependencies.ScoreEventServiceDep)</code>) – Injected score event service dependency.
- **pagination** (<code>[Annotated](#typing.Annotated)\[[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams), [Depends](#fastapi.Depends)()\]</code>) – Pagination parameters (cursor, limit, sort).
- **account_id** (<code>[Annotated](#typing.Annotated)\[[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None, [Query](#fastapi.Query)(description='Filter by account ID')\]</code>) – Optional filter by account ID.
- **board_id** (<code>[Annotated](#typing.Annotated)\[[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None, [Query](#fastapi.Query)(description='Filter by board ID')\]</code>) – Optional filter by board ID.
- **identity_id** (<code>[Annotated](#typing.Annotated)\[[IdentityID](./common.md#leadr.common.domain.ids.IdentityID) | None, [Query](#fastapi.Query)(description='Filter by identity ID')\]</code>) – Optional filter by identity ID.
- **is_test** (<code>[Annotated](#typing.Annotated)\[[bool](#bool) | None, [Query](#fastapi.Query)(description='Filter by test mode')\]</code>) – Optional filter for test events.

**Returns:**

- <code>[PaginatedResponse](./common.md#leadr.common.api.pagination.PaginatedResponse)\[[ScoreEventResponse](#leadr.scores.api.score_event_schemas.ScoreEventResponse)\]</code> – Paginated list of score events.

**Raises:**

- <code>400</code> – Invalid pagination cursor.

###### `leadr.scores.api.score_event_routes.router`

```python
router = APIRouter()
```

##### `leadr.scores.api.score_event_schemas`

API request and response models for score events.

**Classes:**

- [**ScoreEventCreateRequest**](#leadr.scores.api.score_event_schemas.ScoreEventCreateRequest) – Request model for creating a score event (admin only).
- [**ScoreEventResponse**](#leadr.scores.api.score_event_schemas.ScoreEventResponse) – Response model for a score event (admin only).

###### `leadr.scores.api.score_event_schemas.ScoreEventCreateRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request model for creating a score event (admin only).

Creates a score event using the same processing as client submissions:

- Runs anti-cheat checks
- Updates rankings (BoardState/RunEntry)
- Validates board type and payload

**Attributes:**

- [**board_id**](#leadr.scores.api.score_event_schemas.ScoreEventCreateRequest.board_id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) –
- [**city**](#leadr.scores.api.score_event_schemas.ScoreEventCreateRequest.city) (<code>[str](#str) | None</code>) –
- [**country**](#leadr.scores.api.score_event_schemas.ScoreEventCreateRequest.country) (<code>[str](#str) | None</code>) –
- [**identity_id**](#leadr.scores.api.score_event_schemas.ScoreEventCreateRequest.identity_id) (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) –
- [**is_test**](#leadr.scores.api.score_event_schemas.ScoreEventCreateRequest.is_test) (<code>[bool](#bool)</code>) –
- [**player_name**](#leadr.scores.api.score_event_schemas.ScoreEventCreateRequest.player_name) (<code>[str](#str) | None</code>) –
- [**timezone**](#leadr.scores.api.score_event_schemas.ScoreEventCreateRequest.timezone) (<code>[str](#str) | None</code>) –
- [**value**](#leadr.scores.api.score_event_schemas.ScoreEventCreateRequest.value) (<code>[float](#float)</code>) –

####### `leadr.scores.api.score_event_schemas.ScoreEventCreateRequest.board_id`

```python
board_id: BoardID = Field(description='Board to submit to')
```

####### `leadr.scores.api.score_event_schemas.ScoreEventCreateRequest.city`

```python
city: str | None = Field(default=None, description='Optional city name')
```

####### `leadr.scores.api.score_event_schemas.ScoreEventCreateRequest.country`

```python
country: str | None = Field(default=None, description='Optional country code')
```

####### `leadr.scores.api.score_event_schemas.ScoreEventCreateRequest.identity_id`

```python
identity_id: IdentityID = Field(description='Identity submitting the score')
```

####### `leadr.scores.api.score_event_schemas.ScoreEventCreateRequest.is_test`

```python
is_test: bool = Field(default=False, description='Whether this is a test event')
```

####### `leadr.scores.api.score_event_schemas.ScoreEventCreateRequest.player_name`

```python
player_name: str | None = Field(default=None, description='Optional display name')
```

####### `leadr.scores.api.score_event_schemas.ScoreEventCreateRequest.timezone`

```python
timezone: str | None = Field(default=None, description='Optional timezone')
```

####### `leadr.scores.api.score_event_schemas.ScoreEventCreateRequest.value`

```python
value: float = Field(description='Score value (or delta for COUNTER boards)')
```

###### `leadr.scores.api.score_event_schemas.ScoreEventResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response model for a score event (admin only).

Score events are immutable facts about score submissions.
They are append-only and cannot be updated or deleted.

**Functions:**

- [**from_domain**](#leadr.scores.api.score_event_schemas.ScoreEventResponse.from_domain) – Convert domain entity to response model.

**Attributes:**

- [**account_id**](#leadr.scores.api.score_event_schemas.ScoreEventResponse.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**board_id**](#leadr.scores.api.score_event_schemas.ScoreEventResponse.board_id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) –
- [**city**](#leadr.scores.api.score_event_schemas.ScoreEventResponse.city) (<code>[str](#str) | None</code>) –
- [**country**](#leadr.scores.api.score_event_schemas.ScoreEventResponse.country) (<code>[str](#str) | None</code>) –
- [**created_at**](#leadr.scores.api.score_event_schemas.ScoreEventResponse.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**event_payload**](#leadr.scores.api.score_event_schemas.ScoreEventResponse.event_payload) (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\]</code>) –
- [**game_id**](#leadr.scores.api.score_event_schemas.ScoreEventResponse.game_id) (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) –
- [**id**](#leadr.scores.api.score_event_schemas.ScoreEventResponse.id) (<code>[ScoreEventID](./common.md#leadr.common.domain.ids.ScoreEventID)</code>) –
- [**identity_id**](#leadr.scores.api.score_event_schemas.ScoreEventResponse.identity_id) (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) –
- [**is_test**](#leadr.scores.api.score_event_schemas.ScoreEventResponse.is_test) (<code>[bool](#bool)</code>) –
- [**timezone**](#leadr.scores.api.score_event_schemas.ScoreEventResponse.timezone) (<code>[str](#str) | None</code>) –

####### `leadr.scores.api.score_event_schemas.ScoreEventResponse.account_id`

```python
account_id: AccountID = Field(description='ID of the account this event belongs to')
```

####### `leadr.scores.api.score_event_schemas.ScoreEventResponse.board_id`

```python
board_id: BoardID = Field(description='ID of the board this event was submitted to')
```

####### `leadr.scores.api.score_event_schemas.ScoreEventResponse.city`

```python
city: str | None = Field(default=None, description='City name from GeoIP lookup')
```

####### `leadr.scores.api.score_event_schemas.ScoreEventResponse.country`

```python
country: str | None = Field(default=None, description='Country code from GeoIP lookup')
```

####### `leadr.scores.api.score_event_schemas.ScoreEventResponse.created_at`

```python
created_at: datetime = Field(description='Timestamp when the event was created (UTC)')
```

####### `leadr.scores.api.score_event_schemas.ScoreEventResponse.event_payload`

```python
event_payload: dict[str, Any] = Field(description='Board-type-specific payload (value for RUN boards, delta for COUNTER)')
```

####### `leadr.scores.api.score_event_schemas.ScoreEventResponse.from_domain`

```python
from_domain(event)
```

Convert domain entity to response model.

**Parameters:**

- **event** (<code>[ScoreEvent](#leadr.scores.domain.score_event.ScoreEvent)</code>) – The domain ScoreEvent entity to convert.

**Returns:**

- <code>[ScoreEventResponse](#leadr.scores.api.score_event_schemas.ScoreEventResponse)</code> – ScoreEventResponse with all fields populated from the domain entity.

####### `leadr.scores.api.score_event_schemas.ScoreEventResponse.game_id`

```python
game_id: GameID = Field(description='ID of the game this event belongs to')
```

####### `leadr.scores.api.score_event_schemas.ScoreEventResponse.id`

```python
id: ScoreEventID = Field(description='Unique identifier for the score event')
```

####### `leadr.scores.api.score_event_schemas.ScoreEventResponse.identity_id`

```python
identity_id: IdentityID = Field(description='ID of the identity that submitted this score')
```

####### `leadr.scores.api.score_event_schemas.ScoreEventResponse.is_test`

```python
is_test: bool = Field(description='True if this was a test submission')
```

####### `leadr.scores.api.score_event_schemas.ScoreEventResponse.timezone`

```python
timezone: str | None = Field(default=None, description='Timezone from GeoIP lookup')
```

##### `leadr.scores.api.score_flag_routes`

API routes for score flag management.

**Functions:**

- [**create_score_flag**](#leadr.scores.api.score_flag_routes.create_score_flag) – Create a score flag (manual flagging by admin).
- [**get_score_flag**](#leadr.scores.api.score_flag_routes.get_score_flag) – Get a score flag by ID.
- [**list_score_flags**](#leadr.scores.api.score_flag_routes.list_score_flags) – List score flags for an account with optional filters and pagination.
- [**update_score_flag**](#leadr.scores.api.score_flag_routes.update_score_flag) – Update a score flag (review or soft-delete).

**Attributes:**

- [**router**](#leadr.scores.api.score_flag_routes.router) –

###### `leadr.scores.api.score_flag_routes.create_score_flag`

```python
create_score_flag(request, service, auth)
```

Create a score flag (manual flagging by admin).

Allows game admins to manually flag a score for review. By default, flags
are created with type 'manual' and confidence 'medium', but admins can
override these to specify a different flag type (e.g., duplicate, velocity).

**Parameters:**

- **request** (<code>[ScoreFlagCreateRequest](#leadr.scores.api.score_flag_schemas.ScoreFlagCreateRequest)</code>) – Flag creation details (score_event_id, optional flag_type,
  confidence, and metadata).
- **service** (<code>[ScoreFlagServiceDep](./scores.md#leadr.scores.services.dependencies.ScoreFlagServiceDep)</code>) – Injected score flag service dependency.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.

**Returns:**

- <code>[ScoreFlagResponse](#leadr.scores.api.score_flag_schemas.ScoreFlagResponse)</code> – ScoreFlagResponse with the created flag details.

**Raises:**

- <code>422</code> – Invalid flag_type or confidence value.
- <code>403</code> – User does not have access to this score event's account.
- <code>404</code> – Score event not found.

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
list_score_flags(auth, service, pagination, account_id=None, board_id=None, game_id=None, status=None, flag_type=None)
```

List score flags for an account with optional filters and pagination.

Returns paginated flags for the specified account, with optional
filtering by board, game, status, or flag type. Supports cursor-based
pagination with bidirectional navigation and custom sorting.

For regular users, account_id is automatically derived from their API key.
For superadmins, account_id is optional - if omitted, returns flags from all accounts.

**Parameters:**

- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.
- **service** (<code>[ScoreFlagServiceDep](./scores.md#leadr.scores.services.dependencies.ScoreFlagServiceDep)</code>) – Injected score flag service dependency.
- **pagination** (<code>[Annotated](#typing.Annotated)\[[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams), [Depends](#fastapi.Depends)()\]</code>) – Pagination parameters (cursor, limit, sort).
- **account_id** (<code>[Annotated](#typing.Annotated)\[[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None, [Query](#fastapi.Query)(description='Account ID filter')\]</code>) – Optional account_id query parameter (superadmins can omit to see all).
- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None</code>) – Optional board ID to filter by.
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID) | None</code>) – Optional game ID to filter by.
- **status** (<code>[str](#str) | None</code>) – Optional status to filter by (pending, confirmed_cheat, etc.).
- **flag_type** (<code>[str](#str) | None</code>) – Optional flag type to filter by (velocity, duplicate, etc.).

**Returns:**

- <code>[PaginatedResponse](./common.md#leadr.common.api.pagination.PaginatedResponse)\[[ScoreFlagResponse](#leadr.scores.api.score_flag_schemas.ScoreFlagResponse)\]</code> – PaginatedResponse containing ScoreFlagResponse objects matching the filter criteria.

**Raises:**

- <code>400</code> – Invalid cursor or sort field.
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

- [**ScoreFlagCreateRequest**](#leadr.scores.api.score_flag_schemas.ScoreFlagCreateRequest) – Request model for creating a score flag (manual flagging by admin).
- [**ScoreFlagResponse**](#leadr.scores.api.score_flag_schemas.ScoreFlagResponse) – Response model for a score flag.
- [**ScoreFlagUpdateRequest**](#leadr.scores.api.score_flag_schemas.ScoreFlagUpdateRequest) – Request model for updating a score flag (reviewing).

###### `leadr.scores.api.score_flag_schemas.ScoreFlagCreateRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request model for creating a score flag (manual flagging by admin).

**Attributes:**

- [**confidence**](#leadr.scores.api.score_flag_schemas.ScoreFlagCreateRequest.confidence) (<code>[FlagConfidence](#leadr.scores.domain.anti_cheat.enums.FlagConfidence)</code>) –
- [**flag_type**](#leadr.scores.api.score_flag_schemas.ScoreFlagCreateRequest.flag_type) (<code>[FlagType](#leadr.scores.domain.anti_cheat.enums.FlagType)</code>) –
- [**metadata**](#leadr.scores.api.score_flag_schemas.ScoreFlagCreateRequest.metadata) (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\] | None</code>) –
- [**score_event_id**](#leadr.scores.api.score_flag_schemas.ScoreFlagCreateRequest.score_event_id) (<code>[ScoreEventID](./common.md#leadr.common.domain.ids.ScoreEventID)</code>) –
- [**status**](#leadr.scores.api.score_flag_schemas.ScoreFlagCreateRequest.status) (<code>[ScoreFlagStatus](#leadr.scores.domain.anti_cheat.enums.ScoreFlagStatus) | None</code>) –

####### `leadr.scores.api.score_flag_schemas.ScoreFlagCreateRequest.confidence`

```python
confidence: FlagConfidence = Field(default=(FlagConfidence.MEDIUM), description='Confidence level (low, medium, high)')
```

####### `leadr.scores.api.score_flag_schemas.ScoreFlagCreateRequest.flag_type`

```python
flag_type: FlagType = Field(default=(FlagType.MANUAL), description='Type of flag (manual, duplicate, velocity, rate_limit, outlier, etc.)')
```

####### `leadr.scores.api.score_flag_schemas.ScoreFlagCreateRequest.metadata`

```python
metadata: dict[str, Any] | None = Field(default=None, description='Optional metadata/notes about the flag')
```

####### `leadr.scores.api.score_flag_schemas.ScoreFlagCreateRequest.score_event_id`

```python
score_event_id: ScoreEventID = Field(description='ID of the score event to flag')
```

####### `leadr.scores.api.score_flag_schemas.ScoreFlagCreateRequest.status`

```python
status: ScoreFlagStatus | None = Field(default=(ScoreFlagStatus.REMOVED), description='Flag status (defaults to removed for manual admin flagging)')
```

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
- [**score_event_id**](#leadr.scores.api.score_flag_schemas.ScoreFlagResponse.score_event_id) (<code>[ScoreEventID](./common.md#leadr.common.domain.ids.ScoreEventID)</code>) –
- [**status**](#leadr.scores.api.score_flag_schemas.ScoreFlagResponse.status) (<code>[str](#str)</code>) –
- [**updated_at**](#leadr.scores.api.score_flag_schemas.ScoreFlagResponse.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.scores.api.score_flag_schemas.ScoreFlagResponse.confidence`

```python
confidence: str = Field(description='Confidence level of the flag (low, medium, high)')
```

####### `leadr.scores.api.score_flag_schemas.ScoreFlagResponse.created_at`

```python
created_at: datetime = Field(description='Timestamp when the flag was created (UTC)')
```

####### `leadr.scores.api.score_flag_schemas.ScoreFlagResponse.flag_type`

```python
flag_type: str = Field(description='Type of flag (e.g., velocity, duplicate, rate_limit)')
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

####### `leadr.scores.api.score_flag_schemas.ScoreFlagResponse.score_event_id`

```python
score_event_id: ScoreEventID = Field(description='ID of the score event that was flagged')
```

####### `leadr.scores.api.score_flag_schemas.ScoreFlagResponse.status`

```python
status: str = Field(description='Status: pending, confirmed_cheat, false_positive, or dismissed')
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
- [**status**](#leadr.scores.api.score_flag_schemas.ScoreFlagUpdateRequest.status) (<code>[ScoreFlagStatus](#leadr.scores.domain.anti_cheat.enums.ScoreFlagStatus) | None</code>) –

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
status: ScoreFlagStatus | None = Field(default=None, description='Updated status: pending, confirmed_cheat, false_positive, or dismissed')
```

##### `leadr.scores.api.score_routes`

API routes for score management.

**Functions:**

- [**create_score_client**](#leadr.scores.api.score_routes.create_score_client) – Create a new score (Client API).
- [**get_score**](#leadr.scores.api.score_routes.get_score) – Get a score by ID.
- [**get_score_client**](#leadr.scores.api.score_routes.get_score_client) – Get a score by ID (Client API).
- [**handle_list_scores**](#leadr.scores.api.score_routes.handle_list_scores) – Handle list scores logic for both admin and client endpoints.
- [**list_scores_admin**](#leadr.scores.api.score_routes.list_scores_admin) – List scores for a board with optional filters and pagination.
- [**list_scores_client**](#leadr.scores.api.score_routes.list_scores_client) – List scores for a board with optional filters and pagination.

**Attributes:**

- [**client_router**](#leadr.scores.api.score_routes.client_router) –
- [**router**](#leadr.scores.api.score_routes.router) –

###### `leadr.scores.api.score_routes.client_router`

```python
client_router = APIRouter()
```

###### `leadr.scores.api.score_routes.create_score_client`

```python
create_score_client(score_request, geo, service, board_service, background_tasks, auth, identity_service, pre_create_hook, post_create_hook)
```

Create a new score (Client API).

Creates a new score submission for a board. All IDs (account_id, game_id, identity_id)
are automatically derived from the authenticated session.

**Parameters:**

- **score_request** (<code>[ScoreClientCreateRequest](#leadr.scores.api.score_schemas.ScoreClientCreateRequest)</code>) – Score creation details including board_id, player_name, and value.
- **geo** (<code>[GeoInfoDep](./common.md#leadr.common.dependencies.GeoInfoDep)</code>) – GeoIP information extracted from client IP address.
- **service** (<code>[ScoreServiceDep](./scores.md#leadr.scores.services.dependencies.ScoreServiceDep)</code>) – Injected score service dependency.
- **board_service** (<code>[BoardServiceDep](./boards.md#leadr.boards.services.dependencies.BoardServiceDep)</code>) – Injected board service for board lookup.
- **background_tasks** (<code>[BackgroundTasks](#fastapi.BackgroundTasks)</code>) – FastAPI background tasks for async metadata updates.
- **auth** (<code>[ClientAuthContextWithNonceDep](./auth.md#leadr.auth.dependencies.ClientAuthContextWithNonceDep)</code>) – Client authentication context with device and identity info.
- **pre_create_hook** (<code>[PreCreateScoreHookDep](./common.md#leadr.common.api.hooks.PreCreateScoreHookDep)</code>) – Hook called before score creation (for quota checks).
- **post_create_hook** (<code>[PostCreateScoreHookDep](./common.md#leadr.common.api.hooks.PostCreateScoreHookDep)</code>) – Hook called after successful score creation.

**Returns:**

- <code>[ScoreClientResponse](#leadr.scores.api.score_schemas.ScoreClientResponse)</code> – ScoreClientResponse with the created score (excludes device_id).

**Raises:**

- <code>404</code> – Board not found.
- <code>400</code> – Validation failed (board doesn't belong to account, or game doesn't
  match board's game).
- <code>403</code> – Score rejected by anti-cheat (rate limit exceeded).

###### `leadr.scores.api.score_routes.get_score`

```python
get_score(score_id, service, auth)
```

Get a score by ID.

Returns the score with its computed rank based on the board's sort direction.
The rank represents the score's position in the leaderboard (1 = first place).

**Parameters:**

- **score_id** (<code>[ScoreID](./common.md#leadr.common.domain.ids.ScoreID)</code>) – Score identifier to retrieve.
- **service** (<code>[ScoreServiceDep](./scores.md#leadr.scores.services.dependencies.ScoreServiceDep)</code>) – Injected score service dependency.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.

**Returns:**

- <code>[ScoreResponse](#leadr.scores.api.score_schemas.ScoreResponse)</code> – ScoreResponse with the score details including rank.

**Raises:**

- <code>403</code> – User does not have access to this score's account.
- <code>404</code> – Score not found or soft-deleted.

###### `leadr.scores.api.score_routes.get_score_client`

```python
get_score_client(score_id, service, auth)
```

Get a score by ID (Client API).

Returns the score with its computed rank based on the board's sort direction.
The rank represents the score's position in the leaderboard (1 = first place).

Clients can only access scores from boards belonging to the same game
as their authenticated device.

**Parameters:**

- **score_id** (<code>[ScoreID](./common.md#leadr.common.domain.ids.ScoreID)</code>) – Score identifier to retrieve.
- **service** (<code>[ScoreServiceDep](./scores.md#leadr.scores.services.dependencies.ScoreServiceDep)</code>) – Injected score service dependency.
- **auth** (<code>[ClientAuthContextDep](./auth.md#leadr.auth.dependencies.ClientAuthContextDep)</code>) – Client authentication context with device info.

**Returns:**

- <code>[ScoreClientResponse](#leadr.scores.api.score_schemas.ScoreClientResponse)</code> – ScoreClientResponse with the score details including rank.

**Raises:**

- <code>403</code> – Client does not have access to this score's game.
- <code>404</code> – Score not found or soft-deleted.

###### `leadr.scores.api.score_routes.handle_list_scores`

```python
handle_list_scores(auth, service, board_service, pagination, account_id, board_id, game_id, identity_id, is_test=None, around_score_id=None, around_score_value=None)
```

Handle list scores logic for both admin and client endpoints.

This shared handler implements the core list scores functionality and returns
different response models based on the authentication type:

- Admin auth: Returns ScoreResponse with geo fields
- Client auth: Returns ScoreClientResponse without geo fields

**Parameters:**

- **auth** (<code>[AuthContext](./auth.md#leadr.auth.dependencies.AuthContext)</code>) – Authentication context (admin or client).
- **service** (<code>[ScoreService](#leadr.scores.services.score_service.ScoreService)</code>) – Score service for data access.
- **board_service** – Board service for fetching board details.
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (cursor, limit, sort).
- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – Optional account ID filter.
- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – Board ID to list scores for.
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID) | None</code>) – Optional game ID filter.
- **identity_id** (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID) | None</code>) – Optional identity ID filter.
- **is_test** (<code>[bool](#bool) | None</code>) – Optional filter for test scores. True returns only test scores,
  False returns only production scores, None returns all scores.
- **around_score_id** (<code>[ScoreID](./common.md#leadr.common.domain.ids.ScoreID) | None</code>) – Optional score ID to center results around.
- **around_score_value** (<code>[float](#float) | None</code>) – Optional score value to center results around (with placeholder).

**Returns:**

- <code>[PaginatedResponse](./common.md#leadr.common.api.pagination.PaginatedResponse)\[[ScoreResponse](#leadr.scores.api.score_schemas.ScoreResponse)\] | [PaginatedResponse](./common.md#leadr.common.api.pagination.PaginatedResponse)\[[ScoreClientResponse](#leadr.scores.api.score_schemas.ScoreClientResponse)\]</code> – PaginatedResponse with scores and appropriate response model based on auth type.

**Raises:**

- <code>[HTTPException](#fastapi.HTTPException)</code> – 400 if cursor is invalid, sort field is invalid,
  or validation fails for around_score_id/around_score_value.
- <code>[HTTPException](#fastapi.HTTPException)</code> – 404 if around_score_id score not found.

###### `leadr.scores.api.score_routes.list_scores_admin`

```python
list_scores_admin(auth, service, board_service, pagination, board_id, account_id=None, game_id=None, identity_id=None, is_test=IsTestFilter.FALSE, around_score_id=None, around_score_value=None)
```

List scores for a board with optional filters and pagination.

Returns paginated scores for the specified board, with optional
filtering by game or identity. Supports cursor-based pagination
with bidirectional navigation and custom sorting.

For regular admin users, account_id is automatically derived from their API key.
For superadmins, account_id must be explicitly provided as a query parameter.

Pagination:

- Default: 20 items per page, sorted by created_at:desc,id:asc
- Custom sort: Use ?sort=value:desc,created_at:asc
- Valid sort fields: id, value, player_name, created_at, updated_at
- Navigation: Use next_cursor/prev_cursor from response

Around Score:

- Use around_score_id to get scores centered around a specific score
- Use around_score_value to get scores centered around a hypothetical value
  (returns a placeholder score with is_placeholder=True)
- Mutually exclusive with cursor pagination and each other
- Returns a window of scores with the target in the middle
- Respects limit (e.g., limit=5 returns 2 above + target + 2 below)

<details class="example" open markdown="1">
<summary>Example</summary>

GET /v1/scores?board_id=brd_123&limit=50&sort=value:desc,created_at:asc
GET /v1/scores?board_id=brd_123&around_score_id=scr_456&limit=11
GET /v1/scores?board_id=brd_123&around_score_value=1500&limit=11

</details>

**Parameters:**

- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.
- **service** (<code>[ScoreServiceDep](./scores.md#leadr.scores.services.dependencies.ScoreServiceDep)</code>) – Injected score service dependency.
- **pagination** (<code>[Annotated](#typing.Annotated)\[[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams), [Depends](#fastapi.Depends)()\]</code>) – Pagination parameters (cursor, limit, sort).
- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – Board ID to list scores for.
- **account_id** (<code>[Annotated](#typing.Annotated)\[[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None, [Query](#fastapi.Query)(description='Account ID filter')\]</code>) – Optional account_id query parameter (required for superadmins).
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID) | None</code>) – Optional game ID to filter by.
- **identity_id** (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID) | None</code>) – Optional identity ID to filter by.
- **around_score_id** (<code>[Annotated](#typing.Annotated)\[[ScoreID](./common.md#leadr.common.domain.ids.ScoreID) | None, [Query](#fastapi.Query)(description='Center results around this score ID')\]</code>) – Optional score ID to center results around.
- **around_score_value** (<code>[Annotated](#typing.Annotated)\[[float](#float) | None, [Query](#fastapi.Query)(description='Center results around this score value (returns placeholder)')\]</code>) – Optional value to center results around (with placeholder).

**Returns:**

- <code>[PaginatedResponse](./common.md#leadr.common.api.pagination.PaginatedResponse)\[[ScoreResponse](#leadr.scores.api.score_schemas.ScoreResponse)\]</code> – PaginatedResponse with scores and pagination metadata.

**Raises:**

- <code>400</code> – Invalid cursor, sort field, cursor state mismatch, or around validation.
- <code>400</code> – Superadmin did not provide account_id.
- <code>403</code> – User does not have access to the specified account.
- <code>404</code> – around_score_id score not found.

###### `leadr.scores.api.score_routes.list_scores_client`

```python
list_scores_client(auth, service, board_service, pagination, board_id, identity_id=None, around_score_id=None, around_score_value=None)
```

List scores for a board with optional filters and pagination.

Returns paginated scores for the specified board, with optional
filtering by identity. Supports cursor-based pagination
with bidirectional navigation and custom sorting.

Pagination:

- Default: 20 items per page, sorted by created_at:desc,id:asc
- Custom sort: Use ?sort=value:desc,created_at:asc
- Valid sort fields: id, value, player_name, created_at, updated_at
- Navigation: Use next_cursor/prev_cursor from response

Around Score:

- Use around_score_id to get scores centered around a specific score
- Use around_score_value to get scores centered around a hypothetical value
  (returns a placeholder score with is_placeholder=True)
- Mutually exclusive with cursor pagination and each other
- Returns a window of scores with the target in the middle
- Respects limit (e.g., limit=5 returns 2 above + target + 2 below)

<details class="example" open markdown="1">
<summary>Example</summary>

GET /client/scores?board_id=brd_123&limit=50&sort=value:desc,created_at:asc
GET /client/scores?board_id=brd_123&around_score_id=scr_456&limit=11
GET /client/scores?board_id=brd_123&around_score_value=1500&limit=11
GET /client/scores?board_id=brd_123&identity_id=me (filter to current identity)

</details>

**Parameters:**

- **auth** (<code>[ClientAuthContextDep](./auth.md#leadr.auth.dependencies.ClientAuthContextDep)</code>) – Authentication context with user info.
- **service** (<code>[ScoreServiceDep](./scores.md#leadr.scores.services.dependencies.ScoreServiceDep)</code>) – Injected score service dependency.
- **pagination** (<code>[Annotated](#typing.Annotated)\[[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams), [Depends](#fastapi.Depends)()\]</code>) – Pagination parameters (cursor, limit, sort).
- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – Board ID to list scores for.
- **identity_id** (<code>[Annotated](#typing.Annotated)\[[IdentityID](./common.md#leadr.common.domain.ids.IdentityID) | [Literal](#typing.Literal)['me'] | None, [Query](#fastapi.Query)(description="Identity ID to filter by, or 'me' for current identity")\]</code>) – Optional identity ID to filter by, or "me" for current identity.
- **around_score_id** (<code>[Annotated](#typing.Annotated)\[[ScoreID](./common.md#leadr.common.domain.ids.ScoreID) | None, [Query](#fastapi.Query)(description='Center results around this score ID')\]</code>) – Optional score ID to center results around.
- **around_score_value** (<code>[Annotated](#typing.Annotated)\[[float](#float) | None, [Query](#fastapi.Query)(description='Center results around this score value (returns placeholder)')\]</code>) – Optional value to center results around (with placeholder).

**Returns:**

- <code>[PaginatedResponse](./common.md#leadr.common.api.pagination.PaginatedResponse)\[[ScoreClientResponse](#leadr.scores.api.score_schemas.ScoreClientResponse)\]</code> – PaginatedResponse with scores and pagination metadata.

**Raises:**

- <code>400</code> – Invalid cursor, sort field, cursor state mismatch, or around validation.
- <code>403</code> – User does not have access to the specified account.
- <code>404</code> – around_score_id score not found.

###### `leadr.scores.api.score_routes.router`

```python
router = APIRouter()
```

##### `leadr.scores.api.score_schemas`

API request and response models for scores.

**Classes:**

- [**IsTestFilter**](#leadr.scores.api.score_schemas.IsTestFilter) – Filter options for is_test query parameter in admin score listing.
- [**ScoreClientCreateRequest**](#leadr.scores.api.score_schemas.ScoreClientCreateRequest) – Request model for creating a score (Client API).
- [**ScoreClientResponse**](#leadr.scores.api.score_schemas.ScoreClientResponse) – Response model for a score returned to clients.
- [**ScoreCreateRequestBase**](#leadr.scores.api.score_schemas.ScoreCreateRequestBase) – Base request model for score creation with common fields.
- [**ScoreResponse**](#leadr.scores.api.score_schemas.ScoreResponse) – Response model for a score.

###### `leadr.scores.api.score_schemas.IsTestFilter`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Filter options for is_test query parameter in admin score listing.

**Attributes:**

- [**ALL**](#leadr.scores.api.score_schemas.IsTestFilter.ALL) –
- [**FALSE**](#leadr.scores.api.score_schemas.IsTestFilter.FALSE) –
- [**TRUE**](#leadr.scores.api.score_schemas.IsTestFilter.TRUE) –

####### `leadr.scores.api.score_schemas.IsTestFilter.ALL`

```python
ALL = 'all'
```

####### `leadr.scores.api.score_schemas.IsTestFilter.FALSE`

```python
FALSE = 'false'
```

####### `leadr.scores.api.score_schemas.IsTestFilter.TRUE`

```python
TRUE = 'true'
```

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

Response model for a score returned to clients.

Similar to ScoreResponse but excludes sensitive geo data (timezone, country, city)
that clients should not see for other players' scores.

**Functions:**

- [**from_board_state**](#leadr.scores.api.score_schemas.ScoreClientResponse.from_board_state) – Convert BoardState to ScoreClientResponse with masked ID.
- [**from_run_entry**](#leadr.scores.api.score_schemas.ScoreClientResponse.from_run_entry) – Convert RunEntry to ScoreClientResponse with masked ID.

**Attributes:**

- [**account_id**](#leadr.scores.api.score_schemas.ScoreClientResponse.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**board_id**](#leadr.scores.api.score_schemas.ScoreClientResponse.board_id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) –
- [**created_at**](#leadr.scores.api.score_schemas.ScoreClientResponse.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**game_id**](#leadr.scores.api.score_schemas.ScoreClientResponse.game_id) (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) –
- [**id**](#leadr.scores.api.score_schemas.ScoreClientResponse.id) (<code>[ScoreID](./common.md#leadr.common.domain.ids.ScoreID)</code>) –
- [**identity_id**](#leadr.scores.api.score_schemas.ScoreClientResponse.identity_id) (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) –
- [**is_placeholder**](#leadr.scores.api.score_schemas.ScoreClientResponse.is_placeholder) (<code>[bool](#bool)</code>) –
- [**is_test**](#leadr.scores.api.score_schemas.ScoreClientResponse.is_test) (<code>[bool](#bool)</code>) –
- [**metadata**](#leadr.scores.api.score_schemas.ScoreClientResponse.metadata) (<code>[Any](#typing.Any) | None</code>) –
- [**player_name**](#leadr.scores.api.score_schemas.ScoreClientResponse.player_name) (<code>[str](#str)</code>) –
- [**rank**](#leadr.scores.api.score_schemas.ScoreClientResponse.rank) (<code>[int](#int) | None</code>) –
- [**status**](#leadr.scores.api.score_schemas.ScoreClientResponse.status) (<code>[ScoreStatus](#leadr.scores.domain.anti_cheat.enums.ScoreStatus)</code>) –
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

####### `leadr.scores.api.score_schemas.ScoreClientResponse.from_board_state`

```python
from_board_state(state, account_id, game_id, rank)
```

Convert BoardState to ScoreClientResponse with masked ID.

Uses denormalized fields from BoardState directly, no joins required.

**Parameters:**

- **state** (<code>[BoardState](#leadr.boards.domain.board_state.BoardState)</code>) – The BoardState entity representing materialized ranking.
- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – The account ID (from board lookup).
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) – The game ID (from board lookup).
- **rank** (<code>[int](#int)</code>) – The computed rank position (1-indexed).

**Returns:**

- <code>[ScoreClientResponse](#leadr.scores.api.score_schemas.ScoreClientResponse)</code> – ScoreClientResponse with ID masked from bst\_ to scr\_ prefix.

####### `leadr.scores.api.score_schemas.ScoreClientResponse.from_run_entry`

```python
from_run_entry(entry, account_id, game_id, rank)
```

Convert RunEntry to ScoreClientResponse with masked ID.

Uses denormalized fields from RunEntry directly, no joins required.

**Parameters:**

- **entry** (<code>[RunEntry](#leadr.boards.domain.run_entry.RunEntry)</code>) – The RunEntry entity representing a single run.
- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – The account ID (from board lookup).
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) – The game ID (from board lookup).
- **rank** (<code>[int](#int)</code>) – The computed rank position (1-indexed).

**Returns:**

- <code>[ScoreClientResponse](#leadr.scores.api.score_schemas.ScoreClientResponse)</code> – ScoreClientResponse with ID masked from run\_ to scr\_ prefix.

####### `leadr.scores.api.score_schemas.ScoreClientResponse.game_id`

```python
game_id: GameID = Field(description='ID of the game this score belongs to')
```

####### `leadr.scores.api.score_schemas.ScoreClientResponse.id`

```python
id: ScoreID = Field(description='Unique identifier for the score')
```

####### `leadr.scores.api.score_schemas.ScoreClientResponse.identity_id`

```python
identity_id: IdentityID = Field(description='ID of the identity that submitted this score')
```

####### `leadr.scores.api.score_schemas.ScoreClientResponse.is_placeholder`

```python
is_placeholder: bool = Field(default=False, description='True if this is a synthetic placeholder score (from around_score_value query)')
```

####### `leadr.scores.api.score_schemas.ScoreClientResponse.is_test`

```python
is_test: bool = Field(default=False, description='True if this score was submitted in test mode')
```

####### `leadr.scores.api.score_schemas.ScoreClientResponse.metadata`

```python
metadata: Any | None = Field(default=None, description='Game-specific metadata, or null')
```

####### `leadr.scores.api.score_schemas.ScoreClientResponse.player_name`

```python
player_name: str = Field(description='Display name of the player')
```

####### `leadr.scores.api.score_schemas.ScoreClientResponse.rank`

```python
rank: int | None = Field(default=None, description='Leaderboard position (1 = first). Null if not querying by board_id.')
```

####### `leadr.scores.api.score_schemas.ScoreClientResponse.status`

```python
status: ScoreStatus = Field(description='Score lifecycle status (active, under_review, rejected)')
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

This response model is built from BoardState or RunEntry data
with denormalized fields for query efficiency.

**Functions:**

- [**from_board_state**](#leadr.scores.api.score_schemas.ScoreResponse.from_board_state) – Convert BoardState to ScoreResponse with masked ID.
- [**from_run_entry**](#leadr.scores.api.score_schemas.ScoreResponse.from_run_entry) – Convert RunEntry to ScoreResponse with masked ID.

**Attributes:**

- [**account_id**](#leadr.scores.api.score_schemas.ScoreResponse.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**board_id**](#leadr.scores.api.score_schemas.ScoreResponse.board_id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) –
- [**city**](#leadr.scores.api.score_schemas.ScoreResponse.city) (<code>[str](#str) | None</code>) –
- [**country**](#leadr.scores.api.score_schemas.ScoreResponse.country) (<code>[str](#str) | None</code>) –
- [**created_at**](#leadr.scores.api.score_schemas.ScoreResponse.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**game_id**](#leadr.scores.api.score_schemas.ScoreResponse.game_id) (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) –
- [**id**](#leadr.scores.api.score_schemas.ScoreResponse.id) (<code>[ScoreID](./common.md#leadr.common.domain.ids.ScoreID)</code>) –
- [**identity_id**](#leadr.scores.api.score_schemas.ScoreResponse.identity_id) (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) –
- [**is_placeholder**](#leadr.scores.api.score_schemas.ScoreResponse.is_placeholder) (<code>[bool](#bool)</code>) –
- [**is_test**](#leadr.scores.api.score_schemas.ScoreResponse.is_test) (<code>[bool](#bool)</code>) –
- [**metadata**](#leadr.scores.api.score_schemas.ScoreResponse.metadata) (<code>[Any](#typing.Any) | None</code>) –
- [**player_name**](#leadr.scores.api.score_schemas.ScoreResponse.player_name) (<code>[str](#str)</code>) –
- [**rank**](#leadr.scores.api.score_schemas.ScoreResponse.rank) (<code>[int](#int) | None</code>) –
- [**score_event_id**](#leadr.scores.api.score_schemas.ScoreResponse.score_event_id) (<code>[ScoreEventID](./common.md#leadr.common.domain.ids.ScoreEventID) | None</code>) –
- [**status**](#leadr.scores.api.score_schemas.ScoreResponse.status) (<code>[ScoreStatus](#leadr.scores.domain.anti_cheat.enums.ScoreStatus)</code>) –
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

####### `leadr.scores.api.score_schemas.ScoreResponse.from_board_state`

```python
from_board_state(state, account_id, game_id, rank)
```

Convert BoardState to ScoreResponse with masked ID.

Uses denormalized fields from BoardState directly, no joins required.

**Parameters:**

- **state** (<code>[BoardState](#leadr.boards.domain.board_state.BoardState)</code>) – The BoardState entity representing materialized ranking.
- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – The account ID (from board lookup).
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) – The game ID (from board lookup).
- **rank** (<code>[int](#int)</code>) – The computed rank position (1-indexed).

**Returns:**

- <code>[ScoreResponse](#leadr.scores.api.score_schemas.ScoreResponse)</code> – ScoreResponse with ID masked from bst\_ to scr\_ prefix.

####### `leadr.scores.api.score_schemas.ScoreResponse.from_run_entry`

```python
from_run_entry(entry, account_id, game_id, rank)
```

Convert RunEntry to ScoreResponse with masked ID.

Uses denormalized fields from RunEntry directly, no joins required.

**Parameters:**

- **entry** (<code>[RunEntry](#leadr.boards.domain.run_entry.RunEntry)</code>) – The RunEntry entity representing a single run.
- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – The account ID (from board lookup).
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) – The game ID (from board lookup).
- **rank** (<code>[int](#int)</code>) – The computed rank position (1-indexed).

**Returns:**

- <code>[ScoreResponse](#leadr.scores.api.score_schemas.ScoreResponse)</code> – ScoreResponse with ID masked from run\_ to scr\_ prefix.

####### `leadr.scores.api.score_schemas.ScoreResponse.game_id`

```python
game_id: GameID = Field(description='ID of the game this score belongs to')
```

####### `leadr.scores.api.score_schemas.ScoreResponse.id`

```python
id: ScoreID = Field(description='Unique identifier for the score')
```

####### `leadr.scores.api.score_schemas.ScoreResponse.identity_id`

```python
identity_id: IdentityID = Field(description='ID of the identity that submitted this score')
```

####### `leadr.scores.api.score_schemas.ScoreResponse.is_placeholder`

```python
is_placeholder: bool = Field(default=False, description='True if this is a synthetic placeholder score (from around_score_value query)')
```

####### `leadr.scores.api.score_schemas.ScoreResponse.is_test`

```python
is_test: bool = Field(default=False, description='True if this score was submitted in test mode')
```

####### `leadr.scores.api.score_schemas.ScoreResponse.metadata`

```python
metadata: Any | None = Field(default=None, description='Game-specific metadata, or null')
```

####### `leadr.scores.api.score_schemas.ScoreResponse.player_name`

```python
player_name: str = Field(description='Display name of the player')
```

####### `leadr.scores.api.score_schemas.ScoreResponse.rank`

```python
rank: int | None = Field(default=None, description='Leaderboard position (1 = first). Null if not querying by board_id.')
```

####### `leadr.scores.api.score_schemas.ScoreResponse.score_event_id`

```python
score_event_id: ScoreEventID | None = Field(default=None, description='ID of the score event that created/updated this score. Null for RATIO boards which derive values from other boards.')
```

####### `leadr.scores.api.score_schemas.ScoreResponse.status`

```python
status: ScoreStatus = Field(description='Score lifecycle status (active, under_review, rejected)')
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

##### `leadr.scores.api.score_submission_meta_routes`

API routes for score submission metadata management.

**Functions:**

- [**get_submission_meta**](#leadr.scores.api.score_submission_meta_routes.get_submission_meta) – Get score submission metadata by ID.
- [**list_submission_meta**](#leadr.scores.api.score_submission_meta_routes.list_submission_meta) – List score submission metadata for an account with optional filters and pagination.

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
list_submission_meta(auth, service, pagination, account_id=None, board_id=None)
```

List score submission metadata for an account with optional filters and pagination.

Returns paginated submission metadata for the specified account, with optional
filtering by board. Supports cursor-based pagination with bidirectional
navigation and custom sorting.

For regular users, account_id is automatically derived from their API key.
For superadmins, account_id is optional - if omitted, returns metadata from all accounts.

**Parameters:**

- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.
- **service** (<code>[ScoreSubmissionMetaServiceDep](./scores.md#leadr.scores.services.dependencies.ScoreSubmissionMetaServiceDep)</code>) – Injected submission metadata service dependency.
- **pagination** (<code>[Annotated](#typing.Annotated)\[[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams), [Depends](#fastapi.Depends)()\]</code>) – Pagination parameters (cursor, limit, sort).
- **account_id** (<code>[Annotated](#typing.Annotated)\[[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None, [Query](#fastapi.Query)(description='Account ID filter')\]</code>) – Optional account_id query parameter (superadmins can omit to see all).
- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None</code>) – Optional board ID to filter by.

**Returns:**

- <code>[PaginatedResponse](./common.md#leadr.common.api.pagination.PaginatedResponse)\[[ScoreSubmissionMetaResponse](#leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse)\]</code> – PaginatedResponse containing ScoreSubmissionMetaResponse objects matching the filter.

**Raises:**

- <code>400</code> – Invalid cursor or sort field.
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
- [**id**](#leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse.id) (<code>[ScoreSubmissionMetaID](./common.md#leadr.common.domain.ids.ScoreSubmissionMetaID)</code>) –
- [**identity_id**](#leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse.identity_id) (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) –
- [**last_score_value**](#leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse.last_score_value) (<code>[float](#float) | None</code>) –
- [**last_submission_at**](#leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse.last_submission_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**score_event_id**](#leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse.score_event_id) (<code>[ScoreEventID](./common.md#leadr.common.domain.ids.ScoreEventID)</code>) –
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

####### `leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse.from_domain`

```python
from_domain(meta)
```

Convert domain entity to API response.

####### `leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse.id`

```python
id: ScoreSubmissionMetaID
```

####### `leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse.identity_id`

```python
identity_id: IdentityID
```

####### `leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse.last_score_value`

```python
last_score_value: float | None
```

####### `leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse.last_submission_at`

```python
last_submission_at: datetime
```

####### `leadr.scores.api.score_submission_meta_schemas.ScoreSubmissionMetaResponse.score_event_id`

```python
score_event_id: ScoreEventID
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
- [**score_event**](#leadr.scores.domain.score_event) – ScoreEvent domain model for append-only score event sourcing.

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
ACCEPT = 'accept'
```

Accept the score submission without any flags.

####### `leadr.scores.domain.anti_cheat.FlagAction.FLAG`

```python
FLAG = 'flag'
```

Accept the score but flag it for manual review.

####### `leadr.scores.domain.anti_cheat.FlagAction.REJECT`

```python
REJECT = 'reject'
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
HIGH = 'high'
```

High confidence detection - reject submission.

####### `leadr.scores.domain.anti_cheat.FlagConfidence.LOW`

```python
LOW = 'low'
```

Low confidence detection - log but accept.

####### `leadr.scores.domain.anti_cheat.FlagConfidence.MEDIUM`

```python
MEDIUM = 'medium'
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
- [**MANUAL**](#leadr.scores.domain.anti_cheat.FlagType.MANUAL) – Admin manually flagged this score for review.
- [**OUTLIER**](#leadr.scores.domain.anti_cheat.FlagType.OUTLIER) – Score is statistically anomalous compared to board distribution.
- [**PATTERN**](#leadr.scores.domain.anti_cheat.FlagType.PATTERN) – Suspicious pattern detected in submission history (all round numbers, etc).
- [**PROGRESSION**](#leadr.scores.domain.anti_cheat.FlagType.PROGRESSION) – Unrealistic improvement percentage between submissions.
- [**RATE_LIMIT**](#leadr.scores.domain.anti_cheat.FlagType.RATE_LIMIT) – Score submission exceeds rate limits for the user/board.
- [**VELOCITY**](#leadr.scores.domain.anti_cheat.FlagType.VELOCITY) – Submissions are happening too quickly (< 2 seconds apart).

####### `leadr.scores.domain.anti_cheat.FlagType.CLUSTER`

```python
CLUSTER = 'cluster'
```

Multiple users submitting identical scores in short time window.

####### `leadr.scores.domain.anti_cheat.FlagType.DUPLICATE`

```python
DUPLICATE = 'duplicate'
```

Identical score value submitted multiple times in short time window.

####### `leadr.scores.domain.anti_cheat.FlagType.IMPOSSIBLE_VALUE`

```python
IMPOSSIBLE_VALUE = 'impossible_value'
```

Score contains mathematically impossible value (negative, NaN, etc).

####### `leadr.scores.domain.anti_cheat.FlagType.MANUAL`

```python
MANUAL = 'manual'
```

Admin manually flagged this score for review.

####### `leadr.scores.domain.anti_cheat.FlagType.OUTLIER`

```python
OUTLIER = 'outlier'
```

Score is statistically anomalous compared to board distribution.

####### `leadr.scores.domain.anti_cheat.FlagType.PATTERN`

```python
PATTERN = 'pattern'
```

Suspicious pattern detected in submission history (all round numbers, etc).

####### `leadr.scores.domain.anti_cheat.FlagType.PROGRESSION`

```python
PROGRESSION = 'progression'
```

Unrealistic improvement percentage between submissions.

####### `leadr.scores.domain.anti_cheat.FlagType.RATE_LIMIT`

```python
RATE_LIMIT = 'rate_limit'
```

Score submission exceeds rate limits for the user/board.

####### `leadr.scores.domain.anti_cheat.FlagType.VELOCITY`

```python
VELOCITY = 'velocity'
```

Submissions are happening too quickly (< 2 seconds apart).

###### `leadr.scores.domain.anti_cheat.ScoreFlag`

Bases: <code>[Entity](./common.md#leadr.common.domain.models.Entity)</code>

Record of an anti-cheat flag raised for a score submission.

Represents a suspicious pattern detected by the anti-cheat system.
Flags can be reviewed by admins to confirm or dismiss the detection.

Uses score_event_id instead of score_id, linking to the immutable
ScoreEvent in the event-sourcing architecture.

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
- [**score_event_id**](#leadr.scores.domain.anti_cheat.ScoreFlag.score_event_id) (<code>[ScoreEventID](./common.md#leadr.common.domain.ids.ScoreEventID)</code>) –
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

####### `leadr.scores.domain.anti_cheat.ScoreFlag.score_event_id`

```python
score_event_id: ScoreEventID = Field(description='ID of the flagged score event')
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

Tracks the number and timing of score submissions per identity/board combination
to enable detection of suspicious patterns like rapid-fire submissions or
excessive submission rates.

Uses identity_id as the tracking key instead of device_id, aligning with
the event-sourcing architecture where identity is the ranking key.

**Functions:**

- [**restore**](#leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.restore) – Restore a soft-deleted entity.
- [**soft_delete**](#leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.soft_delete) – Mark entity as soft-deleted.

**Attributes:**

- [**board_id**](#leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.board_id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) –
- [**created_at**](#leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**deleted_at**](#leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**id**](#leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.id) (<code>[ScoreSubmissionMetaID](./common.md#leadr.common.domain.ids.ScoreSubmissionMetaID)</code>) –
- [**identity_id**](#leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.identity_id) (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) –
- [**is_deleted**](#leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.is_deleted) (<code>[bool](#bool)</code>) – Check if entity is soft-deleted.
- [**last_score_value**](#leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.last_score_value) (<code>[float](#float) | None</code>) –
- [**last_submission_at**](#leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.last_submission_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**model_config**](#leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.model_config) –
- [**score_event_id**](#leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.score_event_id) (<code>[ScoreEventID](./common.md#leadr.common.domain.ids.ScoreEventID)</code>) –
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

####### `leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.id`

```python
id: ScoreSubmissionMetaID = Field(frozen=True, default_factory=ScoreSubmissionMetaID, description='Unique submission metadata identifier')
```

####### `leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.identity_id`

```python
identity_id: IdentityID = Field(description='ID of the identity submitting scores')
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

####### `leadr.scores.domain.anti_cheat.ScoreSubmissionMeta.score_event_id`

```python
score_event_id: ScoreEventID = Field(description='ID of the most recent score event submission')
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
submission_count: int = Field(default=1, description='Total number of submissions by this identity to this board')
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
A = 'a'
```

Tier A - Trusted devices with verified attestation.

####### `leadr.scores.domain.anti_cheat.TrustTier.B`

```python
B = 'b'
```

Tier B - Verified devices without full attestation.

####### `leadr.scores.domain.anti_cheat.TrustTier.C`

```python
C = 'c'
```

Tier C - Unverified or new devices.

###### `leadr.scores.domain.anti_cheat.enums`

Anti-cheat enums for flag types, confidence levels, and actions.

**Classes:**

- [**FlagAction**](#leadr.scores.domain.anti_cheat.enums.FlagAction) – Action to take based on anti-cheat analysis.
- [**FlagConfidence**](#leadr.scores.domain.anti_cheat.enums.FlagConfidence) – Confidence level for anti-cheat detection.
- [**FlagType**](#leadr.scores.domain.anti_cheat.enums.FlagType) – Type of anti-cheat flag detected.
- [**ScoreFlagStatus**](#leadr.scores.domain.anti_cheat.enums.ScoreFlagStatus) – Status of a score flag review.
- [**ScoreStatus**](#leadr.scores.domain.anti_cheat.enums.ScoreStatus) – DEPRECATED: Legacy lifecycle status field.
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
ACCEPT = 'accept'
```

Accept the score submission without any flags.

######## `leadr.scores.domain.anti_cheat.enums.FlagAction.FLAG`

```python
FLAG = 'flag'
```

Accept the score but flag it for manual review.

######## `leadr.scores.domain.anti_cheat.enums.FlagAction.REJECT`

```python
REJECT = 'reject'
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
HIGH = 'high'
```

High confidence detection - reject submission.

######## `leadr.scores.domain.anti_cheat.enums.FlagConfidence.LOW`

```python
LOW = 'low'
```

Low confidence detection - log but accept.

######## `leadr.scores.domain.anti_cheat.enums.FlagConfidence.MEDIUM`

```python
MEDIUM = 'medium'
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
- [**MANUAL**](#leadr.scores.domain.anti_cheat.enums.FlagType.MANUAL) – Admin manually flagged this score for review.
- [**OUTLIER**](#leadr.scores.domain.anti_cheat.enums.FlagType.OUTLIER) – Score is statistically anomalous compared to board distribution.
- [**PATTERN**](#leadr.scores.domain.anti_cheat.enums.FlagType.PATTERN) – Suspicious pattern detected in submission history (all round numbers, etc).
- [**PROGRESSION**](#leadr.scores.domain.anti_cheat.enums.FlagType.PROGRESSION) – Unrealistic improvement percentage between submissions.
- [**RATE_LIMIT**](#leadr.scores.domain.anti_cheat.enums.FlagType.RATE_LIMIT) – Score submission exceeds rate limits for the user/board.
- [**VELOCITY**](#leadr.scores.domain.anti_cheat.enums.FlagType.VELOCITY) – Submissions are happening too quickly (< 2 seconds apart).

######## `leadr.scores.domain.anti_cheat.enums.FlagType.CLUSTER`

```python
CLUSTER = 'cluster'
```

Multiple users submitting identical scores in short time window.

######## `leadr.scores.domain.anti_cheat.enums.FlagType.DUPLICATE`

```python
DUPLICATE = 'duplicate'
```

Identical score value submitted multiple times in short time window.

######## `leadr.scores.domain.anti_cheat.enums.FlagType.IMPOSSIBLE_VALUE`

```python
IMPOSSIBLE_VALUE = 'impossible_value'
```

Score contains mathematically impossible value (negative, NaN, etc).

######## `leadr.scores.domain.anti_cheat.enums.FlagType.MANUAL`

```python
MANUAL = 'manual'
```

Admin manually flagged this score for review.

######## `leadr.scores.domain.anti_cheat.enums.FlagType.OUTLIER`

```python
OUTLIER = 'outlier'
```

Score is statistically anomalous compared to board distribution.

######## `leadr.scores.domain.anti_cheat.enums.FlagType.PATTERN`

```python
PATTERN = 'pattern'
```

Suspicious pattern detected in submission history (all round numbers, etc).

######## `leadr.scores.domain.anti_cheat.enums.FlagType.PROGRESSION`

```python
PROGRESSION = 'progression'
```

Unrealistic improvement percentage between submissions.

######## `leadr.scores.domain.anti_cheat.enums.FlagType.RATE_LIMIT`

```python
RATE_LIMIT = 'rate_limit'
```

Score submission exceeds rate limits for the user/board.

######## `leadr.scores.domain.anti_cheat.enums.FlagType.VELOCITY`

```python
VELOCITY = 'velocity'
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
- [**REMOVED**](#leadr.scores.domain.anti_cheat.enums.ScoreFlagStatus.REMOVED) – Admin has chosen to remove this score.

######## `leadr.scores.domain.anti_cheat.enums.ScoreFlagStatus.CONFIRMED_CHEAT`

```python
CONFIRMED_CHEAT = 'confirmed_cheat'
```

Admin confirmed this is cheating behavior.

######## `leadr.scores.domain.anti_cheat.enums.ScoreFlagStatus.DISMISSED`

```python
DISMISSED = 'dismissed'
```

Admin dismissed the flag without a specific determination.

######## `leadr.scores.domain.anti_cheat.enums.ScoreFlagStatus.FALSE_POSITIVE`

```python
FALSE_POSITIVE = 'false_positive'
```

Admin determined this was legitimate gameplay.

######## `leadr.scores.domain.anti_cheat.enums.ScoreFlagStatus.PENDING`

```python
PENDING = 'pending'
```

Flag has not been reviewed yet.

######## `leadr.scores.domain.anti_cheat.enums.ScoreFlagStatus.REMOVED`

```python
REMOVED = 'removed'
```

Admin has chosen to remove this score.

####### `leadr.scores.domain.anti_cheat.enums.ScoreStatus`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

DEPRECATED: Legacy lifecycle status field.

This enum is retained for API backwards compatibility only. Score visibility
is now controlled via ScoreFlag status and materialized views:

- RunEntry.excluded_at for RUN_RUNS boards
- BoardState recomputation for RUN_IDENTITY/COUNTER boards

All API responses return ACTIVE regardless of actual flag status.

**Attributes:**

- [**ACTIVE**](#leadr.scores.domain.anti_cheat.enums.ScoreStatus.ACTIVE) – Score passed anti-cheat checks and is visible on leaderboards.
- [**PROVISIONAL**](#leadr.scores.domain.anti_cheat.enums.ScoreStatus.PROVISIONAL) – Initial transient state before anti-cheat check completes.
- [**REJECTED**](#leadr.scores.domain.anti_cheat.enums.ScoreStatus.REJECTED) – Admin confirmed cheating - hidden from leaderboards.
- [**UNDER_REVIEW**](#leadr.scores.domain.anti_cheat.enums.ScoreStatus.UNDER_REVIEW) – Score was flagged by anti-cheat, pending admin review. Still visible.

######## `leadr.scores.domain.anti_cheat.enums.ScoreStatus.ACTIVE`

```python
ACTIVE = 'active'
```

Score passed anti-cheat checks and is visible on leaderboards.

######## `leadr.scores.domain.anti_cheat.enums.ScoreStatus.PROVISIONAL`

```python
PROVISIONAL = 'provisional'
```

Initial transient state before anti-cheat check completes.

######## `leadr.scores.domain.anti_cheat.enums.ScoreStatus.REJECTED`

```python
REJECTED = 'rejected'
```

Admin confirmed cheating - hidden from leaderboards.

######## `leadr.scores.domain.anti_cheat.enums.ScoreStatus.UNDER_REVIEW`

```python
UNDER_REVIEW = 'under_review'
```

Score was flagged by anti-cheat, pending admin review. Still visible.

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
A = 'a'
```

Tier A - Trusted devices with verified attestation.

######## `leadr.scores.domain.anti_cheat.enums.TrustTier.B`

```python
B = 'b'
```

Tier B - Verified devices without full attestation.

######## `leadr.scores.domain.anti_cheat.enums.TrustTier.C`

```python
C = 'c'
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

Uses score_event_id instead of score_id, linking to the immutable
ScoreEvent in the event-sourcing architecture.

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
- [**score_event_id**](#leadr.scores.domain.anti_cheat.models.ScoreFlag.score_event_id) (<code>[ScoreEventID](./common.md#leadr.common.domain.ids.ScoreEventID)</code>) –
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

######## `leadr.scores.domain.anti_cheat.models.ScoreFlag.score_event_id`

```python
score_event_id: ScoreEventID = Field(description='ID of the flagged score event')
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

Tracks the number and timing of score submissions per identity/board combination
to enable detection of suspicious patterns like rapid-fire submissions or
excessive submission rates.

Uses identity_id as the tracking key instead of device_id, aligning with
the event-sourcing architecture where identity is the ranking key.

**Functions:**

- [**restore**](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.restore) – Restore a soft-deleted entity.
- [**soft_delete**](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.soft_delete) – Mark entity as soft-deleted.

**Attributes:**

- [**board_id**](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.board_id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) –
- [**created_at**](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**deleted_at**](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**id**](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.id) (<code>[ScoreSubmissionMetaID](./common.md#leadr.common.domain.ids.ScoreSubmissionMetaID)</code>) –
- [**identity_id**](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.identity_id) (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) –
- [**is_deleted**](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.is_deleted) (<code>[bool](#bool)</code>) – Check if entity is soft-deleted.
- [**last_score_value**](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.last_score_value) (<code>[float](#float) | None</code>) –
- [**last_submission_at**](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.last_submission_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**model_config**](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.model_config) –
- [**score_event_id**](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.score_event_id) (<code>[ScoreEventID](./common.md#leadr.common.domain.ids.ScoreEventID)</code>) –
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

######## `leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.id`

```python
id: ScoreSubmissionMetaID = Field(frozen=True, default_factory=ScoreSubmissionMetaID, description='Unique submission metadata identifier')
```

######## `leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.identity_id`

```python
identity_id: IdentityID = Field(description='ID of the identity submitting scores')
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

######## `leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.score_event_id`

```python
score_event_id: ScoreEventID = Field(description='ID of the most recent score event submission')
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
submission_count: int = Field(default=1, description='Total number of submissions by this identity to this board')
```

######## `leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta.updated_at`

```python
updated_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp of last update (UTC)')
```

##### `leadr.scores.domain.score_event`

ScoreEvent domain model for append-only score event sourcing.

**Classes:**

- [**ScoreEvent**](#leadr.scores.domain.score_event.ScoreEvent) – Append-only score event entity.

###### `leadr.scores.domain.score_event.ScoreEvent`

Bases: <code>[ImmutableEntity](./common.md#leadr.common.domain.models.ImmutableEntity)</code>

Append-only score event entity.

ScoreEvent represents an immutable fact about a score submission.
Unlike regular entities, ScoreEvents:

- Have no updated_at (immutable after creation)
- Have no deleted_at (append-only, never soft-deleted)
- Are the source of truth for score history

The event_payload contains board-type-specific data:

- RUN_IDENTITY/RUN_RUNS: {"value": <numeric>}
- COUNTER: {"delta": <numeric>}
- RATIO: No direct events (derived from other boards)

**Attributes:**

- [**id**](#leadr.scores.domain.score_event.ScoreEvent.id) (<code>[ScoreEventID](./common.md#leadr.common.domain.ids.ScoreEventID)</code>) – Unique identifier for this event.
- [**account_id**](#leadr.scores.domain.score_event.ScoreEvent.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – The account that owns this event.
- [**game_id**](#leadr.scores.domain.score_event.ScoreEvent.game_id) (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) – The game this event belongs to.
- [**board_id**](#leadr.scores.domain.score_event.ScoreEvent.board_id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – The board this event was submitted to.
- [**identity_id**](#leadr.scores.domain.score_event.ScoreEvent.identity_id) (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) – The identity that submitted this score.
- [**event_payload**](#leadr.scores.domain.score_event.ScoreEvent.event_payload) (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\]</code>) – Board-type-specific payload (value or delta).
- [**is_test**](#leadr.scores.domain.score_event.ScoreEvent.is_test) (<code>[bool](#bool)</code>) – Whether this is a test submission (excluded from rankings).
- [**timezone**](#leadr.scores.domain.score_event.ScoreEvent.timezone) (<code>[str](#str) | None</code>) – Timezone extracted from GeoIP lookup.
- [**country**](#leadr.scores.domain.score_event.ScoreEvent.country) (<code>[str](#str) | None</code>) – Country code extracted from GeoIP lookup.
- [**city**](#leadr.scores.domain.score_event.ScoreEvent.city) (<code>[str](#str) | None</code>) – City name extracted from GeoIP lookup.
- [**created_at**](#leadr.scores.domain.score_event.ScoreEvent.created_at) (<code>[datetime](#datetime.datetime)</code>) – Timestamp when the event was created (UTC).

####### `leadr.scores.domain.score_event.ScoreEvent.account_id`

```python
account_id: AccountID = Field(description='Account that owns this event')
```

####### `leadr.scores.domain.score_event.ScoreEvent.board_id`

```python
board_id: BoardID = Field(description='Board this event was submitted to')
```

####### `leadr.scores.domain.score_event.ScoreEvent.city`

```python
city: str | None = Field(default=None, description='City name from GeoIP lookup')
```

####### `leadr.scores.domain.score_event.ScoreEvent.country`

```python
country: str | None = Field(default=None, description='Country code from GeoIP lookup')
```

####### `leadr.scores.domain.score_event.ScoreEvent.created_at`

```python
created_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp when entity was created (UTC)')
```

####### `leadr.scores.domain.score_event.ScoreEvent.event_payload`

```python
event_payload: dict[str, Any] = Field(description='Board-type-specific payload (value for RUN boards, delta for COUNTER)')
```

####### `leadr.scores.domain.score_event.ScoreEvent.game_id`

```python
game_id: GameID = Field(description='Game this event belongs to')
```

####### `leadr.scores.domain.score_event.ScoreEvent.id`

```python
id: ScoreEventID = Field(frozen=True, default_factory=ScoreEventID, description='Unique identifier for this event')
```

####### `leadr.scores.domain.score_event.ScoreEvent.identity_id`

```python
identity_id: IdentityID = Field(description='Identity that submitted this score')
```

####### `leadr.scores.domain.score_event.ScoreEvent.is_test`

```python
is_test: bool = Field(default=False, description='Whether this is a test submission')
```

####### `leadr.scores.domain.score_event.ScoreEvent.model_config`

```python
model_config = ConfigDict(validate_assignment=True)
```

####### `leadr.scores.domain.score_event.ScoreEvent.timezone`

```python
timezone: str | None = Field(default=None, description='Timezone from GeoIP lookup')
```

#### `leadr.scores.services`

**Modules:**

- [**anti_cheat_repositories**](#leadr.scores.services.anti_cheat_repositories) – Anti-cheat repository services.
- [**anti_cheat_service**](#leadr.scores.services.anti_cheat_service) – Anti-cheat service for detecting suspicious score submissions.
- [**dependencies**](./scores.md#leadr.scores.services.dependencies) – Score service dependencies for FastAPI dependency injection.
- [**repositories**](./scores.md#leadr.scores.services.repositories) – Score repository services.
- [**score_event_service**](#leadr.scores.services.score_event_service) – Score event service for managing immutable score events.
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
- [**filter**](#leadr.scores.services.anti_cheat_repositories.ScoreFlagRepository.filter) – Filter flags by account and optional criteria with pagination.
- [**get_by_id**](#leadr.scores.services.anti_cheat_repositories.ScoreFlagRepository.get_by_id) – Get an entity by its ID.
- [**get_flags_by_score_event_id**](#leadr.scores.services.anti_cheat_repositories.ScoreFlagRepository.get_flags_by_score_event_id) – Get all flags for a specific score event.
- [**get_pending_flags**](#leadr.scores.services.anti_cheat_repositories.ScoreFlagRepository.get_pending_flags) – Get all pending (unreviewed) flags.
- [**update**](#leadr.scores.services.anti_cheat_repositories.ScoreFlagRepository.update) – Update an existing entity in the database.

**Attributes:**

- [**SORTABLE_FIELDS**](#leadr.scores.services.anti_cheat_repositories.ScoreFlagRepository.SORTABLE_FIELDS) –
- [**session**](#leadr.scores.services.anti_cheat_repositories.ScoreFlagRepository.session) –

####### `leadr.scores.services.anti_cheat_repositories.ScoreFlagRepository.SORTABLE_FIELDS`

```python
SORTABLE_FIELDS = {'id', 'score_event_id', 'flag_type', 'confidence', 'status', 'created_at', 'updated_at'}
```

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
filter(account_id=None, board_id=None, game_id=None, status=None, flag_type=None, *, pagination, **kwargs)
```

Filter flags by account and optional criteria with pagination.

Joins with score_events table to filter by account_id since flags don't have
a direct account relation.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – Optional account ID to filter by. If None, returns all flags
  (superadmin use case). Regular users should always pass account_id.
- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None</code>) – Optional board ID to filter by
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID) | None</code>) – Optional game ID to filter by
- **status** (<code>[str](#str) | None</code>) – Optional status to filter by (PENDING, CONFIRMED_CHEAT, etc.)
- **flag_type** (<code>[str](#str) | None</code>) – Optional flag type to filter by (VELOCITY, DUPLICATE, etc.)
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (required)
- \*\***kwargs** (<code>[Any](#typing.Any)</code>) – Additional filter parameters (reserved for future use)

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[ScoreFlag](#leadr.scores.domain.anti_cheat.models.ScoreFlag)\]</code> – PaginatedResult containing flags matching the filter criteria

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

####### `leadr.scores.services.anti_cheat_repositories.ScoreFlagRepository.get_flags_by_score_event_id`

```python
get_flags_by_score_event_id(score_event_id)
```

Get all flags for a specific score event.

**Parameters:**

- **score_event_id** (<code>[ScoreEventID](./common.md#leadr.common.domain.ids.ScoreEventID)</code>) – ID of the score event to get flags for

**Returns:**

- <code>[list](#list)\[[ScoreFlag](#leadr.scores.domain.anti_cheat.models.ScoreFlag)\]</code> – List of flags for the score event (excludes soft-deleted)

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
- [**filter**](#leadr.scores.services.anti_cheat_repositories.ScoreSubmissionMetaRepository.filter) – Filter submission metadata by account and optional criteria with pagination.
- [**get_by_id**](#leadr.scores.services.anti_cheat_repositories.ScoreSubmissionMetaRepository.get_by_id) – Get an entity by its ID.
- [**get_by_identity_and_board**](#leadr.scores.services.anti_cheat_repositories.ScoreSubmissionMetaRepository.get_by_identity_and_board) – Get submission metadata for an identity/board combination.
- [**update**](#leadr.scores.services.anti_cheat_repositories.ScoreSubmissionMetaRepository.update) – Update an existing entity in the database.

**Attributes:**

- [**SORTABLE_FIELDS**](#leadr.scores.services.anti_cheat_repositories.ScoreSubmissionMetaRepository.SORTABLE_FIELDS) –
- [**session**](#leadr.scores.services.anti_cheat_repositories.ScoreSubmissionMetaRepository.session) –

####### `leadr.scores.services.anti_cheat_repositories.ScoreSubmissionMetaRepository.SORTABLE_FIELDS`

```python
SORTABLE_FIELDS = {'id', 'identity_id', 'board_id', 'submission_count', 'last_submission_at', 'last_score_value', 'created_at', 'updated_at'}
```

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
filter(account_id=None, board_id=None, identity_id=None, *, pagination, **kwargs)
```

Filter submission metadata by account and optional criteria with pagination.

Joins with score_events table to filter by account_id since submission meta doesn't have
a direct account relation.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – Optional account ID to filter by. If None, returns all metadata
  (superadmin use case). Regular users should always pass account_id.
- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None</code>) – Optional board ID to filter by
- **identity_id** (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID) | None</code>) – Optional identity ID to filter by
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (required)
- \*\***kwargs** (<code>[Any](#typing.Any)</code>) – Additional filter parameters (reserved for future use)

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[ScoreSubmissionMeta](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta)\]</code> – PaginatedResult containing submission metadata matching the filter criteria

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

####### `leadr.scores.services.anti_cheat_repositories.ScoreSubmissionMetaRepository.get_by_identity_and_board`

```python
get_by_identity_and_board(identity_id, board_id)
```

Get submission metadata for an identity/board combination.

**Parameters:**

- **identity_id** (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) – ID of the identity submitting scores
- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – ID of the board being submitted to

**Returns:**

- <code>[ScoreSubmissionMeta](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta) | None</code> – ScoreSubmissionMeta if found, None otherwise

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

- Rate limiting: Prevents excessive submissions per identity/board
- Duplicate detection: Identifies repeated identical scores
- Velocity detection: Detects rapid-fire submissions
- Statistical outliers: Identifies anomalous scores
- Pattern detection: Finds suspicious submission patterns

Uses identity_id as the tracking key instead of device_id, aligning with
the event-sourcing architecture where identity is the ranking key.

**Functions:**

- [**check_submission_for_event**](#leadr.scores.services.anti_cheat_service.AntiCheatService.check_submission_for_event) – Check a score event submission for suspicious patterns.

**Attributes:**

- [**meta_repo**](#leadr.scores.services.anti_cheat_service.AntiCheatService.meta_repo) –
- [**session**](#leadr.scores.services.anti_cheat_service.AntiCheatService.session) –

**Parameters:**

- **session** (<code>[AsyncSession](#sqlalchemy.ext.asyncio.AsyncSession)</code>) – Database session for querying metadata

####### `leadr.scores.services.anti_cheat_service.AntiCheatService.check_submission_for_event`

```python
check_submission_for_event(score_event, trust_tier, identity_id, board_id)
```

Check a score event submission for suspicious patterns.

**Parameters:**

- **score_event** (<code>[ScoreEvent](#leadr.scores.domain.score_event.ScoreEvent)</code>) – ScoreEvent being submitted
- **trust_tier** (<code>[TrustTier](#leadr.scores.domain.anti_cheat.enums.TrustTier)</code>) – Trust tier of the identity (A/B/C)
- **identity_id** (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) – ID of the identity submitting the score
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

- [**get_score_event_service**](#leadr.scores.services.dependencies.get_score_event_service) – Get ScoreEventService dependency.
- [**get_score_flag_service**](#leadr.scores.services.dependencies.get_score_flag_service) – Get ScoreFlagService dependency.
- [**get_score_service**](#leadr.scores.services.dependencies.get_score_service) – Get ScoreService dependency.
- [**get_score_submission_meta_service**](#leadr.scores.services.dependencies.get_score_submission_meta_service) – Get ScoreSubmissionMetaService dependency.

**Attributes:**

- [**ScoreEventServiceDep**](./scores.md#leadr.scores.services.dependencies.ScoreEventServiceDep) –
- [**ScoreFlagServiceDep**](./scores.md#leadr.scores.services.dependencies.ScoreFlagServiceDep) –
- [**ScoreServiceDep**](./scores.md#leadr.scores.services.dependencies.ScoreServiceDep) –
- [**ScoreSubmissionMetaServiceDep**](./scores.md#leadr.scores.services.dependencies.ScoreSubmissionMetaServiceDep) –

###### `leadr.scores.services.dependencies.ScoreEventServiceDep`

```python
ScoreEventServiceDep = Annotated[ScoreEventService, Depends(get_score_event_service)]
```

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

###### `leadr.scores.services.dependencies.get_score_event_service`

```python
get_score_event_service(db)
```

Get ScoreEventService dependency.

**Parameters:**

- **db** (<code>[DatabaseSession](./common.md#leadr.common.dependencies.DatabaseSession)</code>) – Database session from dependency injection

**Returns:**

- <code>[ScoreEventService](#leadr.scores.services.score_event_service.ScoreEventService)</code> – Initialized ScoreEventService instance

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

- [**ScoreEventRepository**](./scores.md#leadr.scores.services.repositories.ScoreEventRepository) – Repository for managing score event persistence.

###### `leadr.scores.services.repositories.ScoreEventRepository`

Bases: <code>[ImmutableBaseRepository](./common.md#leadr.common.repositories.ImmutableBaseRepository)\[[ScoreEvent](#leadr.scores.domain.score_event.ScoreEvent), [ScoreEventORM](./scores.md#leadr.scores.adapters.orm.ScoreEventORM)\]</code>

Repository for managing score event persistence.

Score events are immutable (append-only) so this repository
does not support update or delete operations.

**Functions:**

- [**create**](./scores.md#leadr.scores.services.repositories.ScoreEventRepository.create) – Create a new immutable entity in the database.
- [**filter**](./scores.md#leadr.scores.services.repositories.ScoreEventRepository.filter) – Filter score events based on criteria with pagination.
- [**get_by_id**](#leadr.scores.services.repositories.ScoreEventRepository.get_by_id) – Get an immutable entity by its ID.

**Attributes:**

- [**session**](./scores.md#leadr.scores.services.repositories.ScoreEventRepository.session) –

####### `leadr.scores.services.repositories.ScoreEventRepository.create`

```python
create(entity)
```

Create a new immutable entity in the database.

**Parameters:**

- **entity** (<code>[ImmutableEntityT](./common.md#leadr.common.repositories.ImmutableEntityT)</code>) – Domain entity to create

**Returns:**

- <code>[ImmutableEntityT](./common.md#leadr.common.repositories.ImmutableEntityT)</code> – Created domain entity with refreshed data

####### `leadr.scores.services.repositories.ScoreEventRepository.filter`

```python
filter(account_id=None, board_id=None, identity_id=None, is_test=None, *, pagination, **kwargs)
```

Filter score events based on criteria with pagination.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – Optional account ID filter
- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None</code>) – Optional board ID filter
- **identity_id** (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID) | None</code>) – Optional identity ID filter
- **is_test** (<code>[bool](#bool) | None</code>) – Optional filter for test events
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Required pagination parameters

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[ScoreEvent](#leadr.scores.domain.score_event.ScoreEvent)\]</code> – PaginatedResult containing score events

####### `leadr.scores.services.repositories.ScoreEventRepository.get_by_id`

```python
get_by_id(entity_id)
```

Get an immutable entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – Entity ID to retrieve

**Returns:**

- <code>[ImmutableEntityT](./common.md#leadr.common.repositories.ImmutableEntityT) | None</code> – Domain entity if found, None otherwise

####### `leadr.scores.services.repositories.ScoreEventRepository.session`

```python
session = session
```

##### `leadr.scores.services.score_event_service`

Score event service for managing immutable score events.

**Classes:**

- [**ScoreEventService**](#leadr.scores.services.score_event_service.ScoreEventService) – Service for managing score events.

###### `leadr.scores.services.score_event_service.ScoreEventService`

```python
ScoreEventService(session)
```

Service for managing score events.

Score events are immutable (append-only) facts about score submissions.
This service only provides create, get, and list operations.
No update or delete operations are available.

**Functions:**

- [**create_score_event**](#leadr.scores.services.score_event_service.ScoreEventService.create_score_event) – Create a new score event.
- [**get_by_id_or_raise**](#leadr.scores.services.score_event_service.ScoreEventService.get_by_id_or_raise) – Get a score event by ID, raising if not found.
- [**get_score_event**](#leadr.scores.services.score_event_service.ScoreEventService.get_score_event) – Get a score event by ID.
- [**list_score_events**](#leadr.scores.services.score_event_service.ScoreEventService.list_score_events) – List score events with optional filters.

**Attributes:**

- [**repository**](#leadr.scores.services.score_event_service.ScoreEventService.repository) –
- [**session**](#leadr.scores.services.score_event_service.ScoreEventService.session) –

**Parameters:**

- **session** (<code>[AsyncSession](#sqlalchemy.ext.asyncio.AsyncSession)</code>) – SQLAlchemy async session

####### `leadr.scores.services.score_event_service.ScoreEventService.create_score_event`

```python
create_score_event(account_id, game_id, board_id, identity_id, event_payload, is_test=False, timezone=None, country=None, city=None)
```

Create a new score event.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – Account that owns this event
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) – Game this event belongs to
- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – Board this event was submitted to
- **identity_id** (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) – Identity that submitted this score
- **event_payload** (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\]</code>) – Board-type-specific payload (value or delta)
- **is_test** (<code>[bool](#bool)</code>) – Whether this is a test submission
- **timezone** (<code>[str](#str) | None</code>) – Timezone from GeoIP lookup
- **country** (<code>[str](#str) | None</code>) – Country code from GeoIP lookup
- **city** (<code>[str](#str) | None</code>) – City name from GeoIP lookup

**Returns:**

- <code>[ScoreEvent](#leadr.scores.domain.score_event.ScoreEvent)</code> – Created ScoreEvent entity

####### `leadr.scores.services.score_event_service.ScoreEventService.get_by_id_or_raise`

```python
get_by_id_or_raise(event_id)
```

Get a score event by ID, raising if not found.

**Parameters:**

- **event_id** (<code>[ScoreEventID](./common.md#leadr.common.domain.ids.ScoreEventID)</code>) – Score event ID

**Returns:**

- <code>[ScoreEvent](#leadr.scores.domain.score_event.ScoreEvent)</code> – ScoreEvent entity

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If event not found

####### `leadr.scores.services.score_event_service.ScoreEventService.get_score_event`

```python
get_score_event(event_id)
```

Get a score event by ID.

**Parameters:**

- **event_id** (<code>[ScoreEventID](./common.md#leadr.common.domain.ids.ScoreEventID)</code>) – Score event ID

**Returns:**

- <code>[ScoreEvent](#leadr.scores.domain.score_event.ScoreEvent) | None</code> – ScoreEvent if found, None otherwise

####### `leadr.scores.services.score_event_service.ScoreEventService.list_score_events`

```python
list_score_events(account_id=None, board_id=None, identity_id=None, is_test=None, limit=50)
```

List score events with optional filters.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – Optional filter by account
- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None</code>) – Optional filter by board
- **identity_id** (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID) | None</code>) – Optional filter by identity
- **is_test** (<code>[bool](#bool) | None</code>) – Optional filter by test flag
- **limit** (<code>[int](#int)</code>) – Maximum number of results

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[ScoreEvent](#leadr.scores.domain.score_event.ScoreEvent)\]</code> – Paginated list of score events

####### `leadr.scores.services.score_event_service.ScoreEventService.repository`

```python
repository = ScoreEventRepository(session)
```

####### `leadr.scores.services.score_event_service.ScoreEventService.session`

```python
session = session
```

##### `leadr.scores.services.score_flag_service`

Score flag service for managing flag operations.

**Classes:**

- [**ScoreFlagService**](#leadr.scores.services.score_flag_service.ScoreFlagService) – Service for managing score flag lifecycle and operations.

###### `leadr.scores.services.score_flag_service.ScoreFlagService`

```python
ScoreFlagService(session)
```

Bases: <code>[BaseService](./common.md#leadr.common.services.BaseService)\[[ScoreFlag](#leadr.scores.domain.anti_cheat.models.ScoreFlag), [ScoreFlagRepository](#leadr.scores.services.anti_cheat_repositories.ScoreFlagRepository)\]</code>

Service for managing score flag lifecycle and operations.

This service orchestrates flag listing, retrieval, and review operations
by coordinating between the domain models and repository layer.

**Functions:**

- [**create_flag**](#leadr.scores.services.score_flag_service.ScoreFlagService.create_flag) – Create a new score flag (for manual admin flagging).
- [**delete**](#leadr.scores.services.score_flag_service.ScoreFlagService.delete) – Soft-delete an entity.
- [**get_by_id**](#leadr.scores.services.score_flag_service.ScoreFlagService.get_by_id) – Get an entity by its ID.
- [**get_by_id_or_raise**](#leadr.scores.services.score_flag_service.ScoreFlagService.get_by_id_or_raise) – Get an entity by its ID or raise EntityNotFoundError.
- [**get_flag**](#leadr.scores.services.score_flag_service.ScoreFlagService.get_flag) – Get a flag by its ID.
- [**list_all**](#leadr.scores.services.score_flag_service.ScoreFlagService.list_all) – List all non-deleted entities.
- [**list_flags**](#leadr.scores.services.score_flag_service.ScoreFlagService.list_flags) – List score flags for an account with optional filters and pagination.
- [**review_flag**](#leadr.scores.services.score_flag_service.ScoreFlagService.review_flag) – Review a flag and update its status.
- [**soft_delete**](#leadr.scores.services.score_flag_service.ScoreFlagService.soft_delete) – Soft-delete an entity and return it before deletion.
- [**update_flag**](#leadr.scores.services.score_flag_service.ScoreFlagService.update_flag) – Update a flag's status and/or reviewer decision.

**Attributes:**

- [**repository**](#leadr.scores.services.score_flag_service.ScoreFlagService.repository) –
- [**session**](#leadr.scores.services.score_flag_service.ScoreFlagService.session) –

**Parameters:**

- **session** (<code>[AsyncSession](#sqlalchemy.ext.asyncio.AsyncSession)</code>) – SQLAlchemy async session for database operations

####### `leadr.scores.services.score_flag_service.ScoreFlagService.create_flag`

```python
create_flag(score_event_id, flag_type, confidence, status=ScoreFlagStatus.PENDING, metadata=None)
```

Create a new score flag (for manual admin flagging).

**Parameters:**

- **score_event_id** (<code>[ScoreEventID](./common.md#leadr.common.domain.ids.ScoreEventID)</code>) – ID of the score event to flag
- **flag_type** (<code>[FlagType](#leadr.scores.domain.anti_cheat.enums.FlagType)</code>) – Type of flag (MANUAL, DUPLICATE, etc.)
- **confidence** (<code>[FlagConfidence](#leadr.scores.domain.anti_cheat.enums.FlagConfidence)</code>) – Confidence level (LOW, MEDIUM, HIGH)
- **status** (<code>[ScoreFlagStatus](#leadr.scores.domain.anti_cheat.enums.ScoreFlagStatus)</code>) – Initial status (defaults to PENDING)
- **metadata** (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\] | None</code>) – Optional metadata/notes about the flag

**Returns:**

- <code>[ScoreFlag](#leadr.scores.domain.anti_cheat.models.ScoreFlag)</code> – The created ScoreFlag

<details class="example" open markdown="1">
<summary>Example</summary>

> > > flag = await service.create_flag(
> > > ... score_event_id=event.id,
> > > ... flag_type=FlagType.MANUAL,
> > > ... confidence=FlagConfidence.MEDIUM,
> > > ... metadata={"reason": "Suspicious score"},
> > > ... )

</details>

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
list_flags(account_id, board_id=None, game_id=None, status=None, flag_type=None, *, pagination)
```

List score flags for an account with optional filters and pagination.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – Account ID to filter by. If None, returns all flags
  (superadmin use case).
- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None</code>) – Optional board ID to filter by
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID) | None</code>) – Optional game ID to filter by
- **status** (<code>[str](#str) | None</code>) – Optional status to filter by (PENDING, CONFIRMED_CHEAT, etc.)
- **flag_type** (<code>[str](#str) | None</code>) – Optional flag type to filter by (VELOCITY, DUPLICATE, etc.)
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (required)

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[ScoreFlag](#leadr.scores.domain.anti_cheat.models.ScoreFlag)\]</code> – PaginatedResult containing flags matching the filter criteria

<details class="example" open markdown="1">
<summary>Example</summary>

> > > flags = await service.list_flags(
> > > ... account_id=account.id,
> > > ... status="pending",
> > > ... pagination=PaginationParams(cursor=None, limit=100, sort=None),
> > > ... )

</details>

####### `leadr.scores.services.score_flag_service.ScoreFlagService.repository`

```python
repository = repository if repository is not None else self._create_repository(session)
```

####### `leadr.scores.services.score_flag_service.ScoreFlagService.review_flag`

```python
review_flag(flag_id, status, reviewer_decision=None, reviewer_id=None)
```

Review a flag and update its status.

Note: Ranking updates for flag status changes are not yet implemented
in the event-sourcing architecture.

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

####### `leadr.scores.services.score_flag_service.ScoreFlagService.session`

```python
session = session
```

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
update_flag(flag_id, **updates)
```

Update a flag's status and/or reviewer decision.

Accepts any fields to update as keyword arguments. Only fields
explicitly provided will be updated, allowing null values to
clear optional fields.

Note: When status is updated, reviewed_at is automatically set
to the current time.

**Parameters:**

- **flag_id** (<code>[ScoreFlagID](./common.md#leadr.common.domain.ids.ScoreFlagID)</code>) – The ID of the flag to update
- \*\***updates** (<code>[Any](#typing.Any)</code>) – Field names and values to update

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

```python
ScoreService(session)
```

Service for managing score lifecycle and operations.

This service orchestrates score submission via event-sourcing, and provides
query methods that delegate to BoardStateService and RunEntryService for
reading materialized ranking data.

The Score entity has been replaced by:

- ScoreEvent: immutable event log
- BoardState/RunEntry: materialized ranking views

All GET queries return BoardState or RunEntry data with IDs masked to scr\_ prefix.

**Functions:**

- [**get_score_by_id**](#leadr.scores.services.score_service.ScoreService.get_score_by_id) – Get a score by its ID with computed rank.
- [**list_scores**](#leadr.scores.services.score_service.ScoreService.list_scores) – List scores for a board with optional filters and pagination.
- [**submit_score**](#leadr.scores.services.score_service.ScoreService.submit_score) – Submit a score using the event-sourcing architecture.

**Attributes:**

- [**session**](#leadr.scores.services.score_service.ScoreService.session) –

**Parameters:**

- **session** (<code>[AsyncSession](#sqlalchemy.ext.asyncio.AsyncSession)</code>) – SQLAlchemy async session

####### `leadr.scores.services.score_service.ScoreService.get_score_by_id`

```python
get_score_by_id(score_id, account_id=None, game_id=None)
```

Get a score by its ID with computed rank.

The score_id uses scr\_ prefix but internally maps to BoardState (bst\_) or
RunEntry (run\_) based on board type. This method tries both services.

**Parameters:**

- **score_id** (<code>[ScoreID](./common.md#leadr.common.domain.ids.ScoreID)</code>) – The score ID (scr\_ prefix).
- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – Optional account ID for authorization check.
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID) | None</code>) – Optional game ID for authorization check.

**Returns:**

- <code>[BoardState](#leadr.boards.domain.board_state.BoardState) | [RunEntry](#leadr.boards.domain.run_entry.RunEntry)</code> – Tuple of (BoardState or RunEntry, Board, rank) with the ranking data,
- <code>[Board](./boards.md#leadr.boards.domain.board.Board)</code> – board, and computed rank (1-indexed).

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If no matching BoardState or RunEntry is found.

####### `leadr.scores.services.score_service.ScoreService.list_scores`

```python
list_scores(board_id, account_id=None, game_id=None, identity_id=None, is_test=None, *, pagination, around_score_id=None, around_score_value=None)
```

List scores for a board with optional filters and pagination.

Delegates to BoardStateService or RunEntryService based on board type.

**Parameters:**

- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – Board ID to list scores for.
- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – Optional account ID to filter by (for authorization).
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID) | None</code>) – Optional game ID filter.
- **identity_id** (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID) | None</code>) – Optional identity ID filter.
- **is_test** (<code>[bool](#bool) | None</code>) – Optional filter for test scores.
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters.
- **around_score_id** (<code>[ScoreID](./common.md#leadr.common.domain.ids.ScoreID) | None</code>) – Optional score ID to center results around.
- **around_score_value** (<code>[float](#float) | None</code>) – Optional value to center results around.

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[BoardState](#leadr.boards.domain.board_state.BoardState)\] | [PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[RunEntry](#leadr.boards.domain.run_entry.RunEntry)\]</code> – PaginatedResult containing BoardState or RunEntry objects.

####### `leadr.scores.services.score_service.ScoreService.session`

```python
session = session
```

####### `leadr.scores.services.score_service.ScoreService.submit_score`

```python
submit_score(board_id, identity_id, value=None, delta=None, player_name=None, timezone=None, country=None, city=None, is_test=False, trust_tier=TrustTier.B, background_tasks=None, value_display=None, metadata=None)
```

Submit a score using the event-sourcing architecture.

This method creates a ScoreEvent, runs anti-cheat checks, and then
updates the appropriate materialized view (BoardState or RunEntry)
based on the board type and anti-cheat result.

**Parameters:**

- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – The board to submit to.
- **identity_id** (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) – The identity submitting the score.
- **value** (<code>[float](#float) | None</code>) – Score value for RUN_IDENTITY and RUN_RUNS boards.
- **delta** (<code>[float](#float) | None</code>) – Delta value for COUNTER boards.
- **player_name** (<code>[str](#str) | None</code>) – Optional display name for the player.
- **timezone** (<code>[str](#str) | None</code>) – Optional timezone from GeoIP.
- **country** (<code>[str](#str) | None</code>) – Optional country code from GeoIP.
- **city** (<code>[str](#str) | None</code>) – Optional city name from GeoIP.
- **is_test** (<code>[bool](#bool)</code>) – Whether this is a test submission.
- **trust_tier** (<code>[TrustTier](#leadr.scores.domain.anti_cheat.enums.TrustTier)</code>) – Trust tier for anti-cheat thresholds (defaults to B).
- **background_tasks** (<code>[BackgroundTasks](#starlette.background.BackgroundTasks) | None</code>) – Optional BackgroundTasks for async ratio updates.
- **value_display** (<code>[str](#str) | None</code>) – Optional formatted display string for the score value.
- **metadata** (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\] | None</code>) – Optional custom metadata dictionary.

**Returns:**

- <code>[ScoreEvent](#leadr.scores.domain.score_event.ScoreEvent)</code> – Tuple of (ScoreEvent, ranking_entry, anti_cheat_result).
- <code>[BoardState](#leadr.boards.domain.board_state.BoardState) | [RunEntry](#leadr.boards.domain.run_entry.RunEntry) | None</code> – ranking_entry is BoardState for RUN_IDENTITY/COUNTER boards,
- <code>[AntiCheatResult](#leadr.scores.domain.anti_cheat.models.AntiCheatResult) | None</code> – RunEntry for RUN_RUNS boards, or None if no ranking update
- <code>[tuple](#tuple)\[[ScoreEvent](#leadr.scores.domain.score_event.ScoreEvent), [BoardState](#leadr.boards.domain.board_state.BoardState) | [RunEntry](#leadr.boards.domain.run_entry.RunEntry) | None, [AntiCheatResult](#leadr.scores.domain.anti_cheat.models.AntiCheatResult) | None\]</code> – (e.g., if anti-cheat REJECTs).

**Raises:**

- <code>[ValueError](#ValueError)</code> – If validation fails (missing required fields, invalid board type).
- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If board or identity doesn't exist.

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
- [**list_submission_meta**](#leadr.scores.services.score_submission_meta_service.ScoreSubmissionMetaService.list_submission_meta) – List score submission metadata for an account with optional filters and pagination.
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
list_submission_meta(account_id, board_id=None, *, pagination)
```

List score submission metadata for an account with optional filters and pagination.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – Account ID to filter by. If None, returns all metadata
  (superadmin use case).
- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None</code>) – Optional board ID to filter by
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (required)

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[ScoreSubmissionMeta](#leadr.scores.domain.anti_cheat.models.ScoreSubmissionMeta)\]</code> – PaginatedResult containing submission metadata matching the filter criteria

<details class="example" open markdown="1">
<summary>Example</summary>

> > > metas = await service.list_submission_meta(
> > > ... account_id=account.id,
> > > ... board_id=board.id,
> > > ... pagination=PaginationParams(cursor=None, limit=100, sort=None),
> > > ... )

</details>

####### `leadr.scores.services.score_submission_meta_service.ScoreSubmissionMetaService.repository`

```python
repository = repository if repository is not None else self._create_repository(session)
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
