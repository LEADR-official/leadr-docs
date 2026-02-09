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
- [**BoardRatioConfigORM**](./boards.md#leadr.boards.adapters.orm.BoardRatioConfigORM) – Board ratio config ORM model.
- [**BoardStateORM**](./boards.md#leadr.boards.adapters.orm.BoardStateORM) – Board state ORM model.
- [**BoardTemplateORM**](./boards.md#leadr.boards.adapters.orm.BoardTemplateORM) – BoardTemplate ORM model.
- [**BoardTypeEnum**](./boards.md#leadr.boards.adapters.orm.BoardTypeEnum) – Board type enum for database.
- [**KeepStrategyEnum**](./boards.md#leadr.boards.adapters.orm.KeepStrategyEnum) – Keep strategy enum for database.
- [**RatioDisplayEnum**](./boards.md#leadr.boards.adapters.orm.RatioDisplayEnum) – Ratio display enum for database.
- [**RunEntryORM**](./boards.md#leadr.boards.adapters.orm.RunEntryORM) – Run entry ORM model.
- [**TieBreakerEnum**](./boards.md#leadr.boards.adapters.orm.TieBreakerEnum) – Tie breaker enum for database.
- [**ZeroDenominatorPolicyEnum**](./boards.md#leadr.boards.adapters.orm.ZeroDenominatorPolicyEnum) – Zero denominator policy enum for database.

###### `leadr.boards.adapters.orm.BoardORM`

Bases: <code>[Base](./common.md#leadr.common.orm.Base)</code>

Board ORM model.

Represents a leaderboard/board that belongs to a game in the database.
Maps to the boards table with foreign keys to accounts and games, a
unique constraint on short_code (globally unique for direct sharing),
and a partial unique constraint on (account_id, game_id, slug) for
active boards only.

**Attributes:**

- [**account**](./boards.md#leadr.boards.adapters.orm.BoardORM.account) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[AccountORM](./accounts.md#leadr.accounts.adapters.orm.AccountORM)\]</code>) –
- [**account_id**](#leadr.boards.adapters.orm.BoardORM.account_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**board_type**](#leadr.boards.adapters.orm.BoardORM.board_type) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[BoardTypeEnum](./boards.md#leadr.boards.adapters.orm.BoardTypeEnum)\]</code>) –
- [**created_at**](#leadr.boards.adapters.orm.BoardORM.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**created_from_template_id**](#leadr.boards.adapters.orm.BoardORM.created_from_template_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID) | None\]</code>) –
- [**deleted_at**](#leadr.boards.adapters.orm.BoardORM.deleted_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[nullable_timestamp](#leadr.common.orm.nullable_timestamp)\]</code>) –
- [**description**](./boards.md#leadr.boards.adapters.orm.BoardORM.description) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**ends_at**](#leadr.boards.adapters.orm.BoardORM.ends_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime) | None\]</code>) –
- [**game**](./boards.md#leadr.boards.adapters.orm.BoardORM.game) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[GameORM](./games.md#leadr.games.adapters.orm.GameORM)\]</code>) –
- [**game_id**](#leadr.boards.adapters.orm.BoardORM.game_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**icon**](./boards.md#leadr.boards.adapters.orm.BoardORM.icon) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**id**](./boards.md#leadr.boards.adapters.orm.BoardORM.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**is_active**](#leadr.boards.adapters.orm.BoardORM.is_active) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[bool](#bool)\]</code>) –
- [**is_published**](#leadr.boards.adapters.orm.BoardORM.is_published) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[bool](#bool)\]</code>) –
- [**keep_strategy**](#leadr.boards.adapters.orm.BoardORM.keep_strategy) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[KeepStrategyEnum](./boards.md#leadr.boards.adapters.orm.KeepStrategyEnum)\]</code>) –
- [**name**](./boards.md#leadr.boards.adapters.orm.BoardORM.name) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**short_code**](#leadr.boards.adapters.orm.BoardORM.short_code) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**slug**](./boards.md#leadr.boards.adapters.orm.BoardORM.slug) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**sort_direction**](#leadr.boards.adapters.orm.BoardORM.sort_direction) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**starts_at**](#leadr.boards.adapters.orm.BoardORM.starts_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime) | None\]</code>) –
- [**tags**](./boards.md#leadr.boards.adapters.orm.BoardORM.tags) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[list](#list)\[[str](#str)\]\]</code>) –
- [**template_name**](#leadr.boards.adapters.orm.BoardORM.template_name) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**unit**](./boards.md#leadr.boards.adapters.orm.BoardORM.unit) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**updated_at**](#leadr.boards.adapters.orm.BoardORM.updated_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –

####### `leadr.boards.adapters.orm.BoardORM.account`

```python
account: Mapped[AccountORM] = relationship('AccountORM')
```

####### `leadr.boards.adapters.orm.BoardORM.account_id`

```python
account_id: Mapped[UUID] = mapped_column(ForeignKey('accounts.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.boards.adapters.orm.BoardORM.board_type`

```python
board_type: Mapped[BoardTypeEnum] = mapped_column(Enum(BoardTypeEnum, name='board_type', native_enum=True, values_callable=(lambda x: [(e.value) for e in x]), create_constraint=False), nullable=False, default=(BoardTypeEnum.RUN_IDENTITY), server_default='RUN_IDENTITY')
```

####### `leadr.boards.adapters.orm.BoardORM.created_at`

```python
created_at: Mapped[timestamp]
```

####### `leadr.boards.adapters.orm.BoardORM.created_from_template_id`

```python
created_from_template_id: Mapped[UUID | None] = mapped_column(nullable=True, default=None)
```

####### `leadr.boards.adapters.orm.BoardORM.deleted_at`

```python
deleted_at: Mapped[nullable_timestamp]
```

####### `leadr.boards.adapters.orm.BoardORM.description`

```python
description: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
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
icon: Mapped[str | None] = mapped_column(String, nullable=True)
```

####### `leadr.boards.adapters.orm.BoardORM.id`

```python
id: Mapped[uuid_pk]
```

####### `leadr.boards.adapters.orm.BoardORM.is_active`

```python
is_active: Mapped[bool] = mapped_column(Boolean, nullable=False)
```

####### `leadr.boards.adapters.orm.BoardORM.is_published`

```python
is_published: Mapped[bool] = mapped_column(Boolean, nullable=False, default=True, server_default=(sa.text('true')))
```

####### `leadr.boards.adapters.orm.BoardORM.keep_strategy`

```python
keep_strategy: Mapped[KeepStrategyEnum] = mapped_column(Enum(KeepStrategyEnum, name='keep_strategy', native_enum=True, values_callable=(lambda x: [(e.value) for e in x]), create_constraint=False), nullable=False, default=(KeepStrategyEnum.BEST), server_default='BEST')
```

####### `leadr.boards.adapters.orm.BoardORM.name`

```python
name: Mapped[str] = mapped_column(String, nullable=False)
```

####### `leadr.boards.adapters.orm.BoardORM.short_code`

```python
short_code: Mapped[str] = mapped_column(String, nullable=False, unique=True, index=True)
```

####### `leadr.boards.adapters.orm.BoardORM.slug`

```python
slug: Mapped[str] = mapped_column(String, nullable=False, index=True)
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

####### `leadr.boards.adapters.orm.BoardORM.template_name`

```python
template_name: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
```

####### `leadr.boards.adapters.orm.BoardORM.unit`

```python
unit: Mapped[str | None] = mapped_column(String, nullable=True)
```

####### `leadr.boards.adapters.orm.BoardORM.updated_at`

```python
updated_at: Mapped[timestamp] = mapped_column(onupdate=(func.now()))
```

###### `leadr.boards.adapters.orm.BoardRatioConfigORM`

Bases: <code>[Base](./common.md#leadr.common.orm.Base)</code>

Board ratio config ORM model.

Stores configuration for RATIO board types that derive their ranking
from two other boards (numerator and denominator). Maps to the
board_ratio_configs table with foreign keys to boards.

**Attributes:**

- [**board**](./boards.md#leadr.boards.adapters.orm.BoardRatioConfigORM.board) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[BoardORM](./boards.md#leadr.boards.adapters.orm.BoardORM)\]</code>) –
- [**board_id**](#leadr.boards.adapters.orm.BoardRatioConfigORM.board_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**created_at**](#leadr.boards.adapters.orm.BoardRatioConfigORM.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**decimals**](./boards.md#leadr.boards.adapters.orm.BoardRatioConfigORM.decimals) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[int](#int)\]</code>) –
- [**deleted_at**](#leadr.boards.adapters.orm.BoardRatioConfigORM.deleted_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[nullable_timestamp](#leadr.common.orm.nullable_timestamp)\]</code>) –
- [**denominator_board**](#leadr.boards.adapters.orm.BoardRatioConfigORM.denominator_board) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[BoardORM](./boards.md#leadr.boards.adapters.orm.BoardORM)\]</code>) –
- [**denominator_board_id**](#leadr.boards.adapters.orm.BoardRatioConfigORM.denominator_board_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**display**](./boards.md#leadr.boards.adapters.orm.BoardRatioConfigORM.display) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[RatioDisplayEnum](./boards.md#leadr.boards.adapters.orm.RatioDisplayEnum)\]</code>) –
- [**id**](./boards.md#leadr.boards.adapters.orm.BoardRatioConfigORM.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**min_denominator**](#leadr.boards.adapters.orm.BoardRatioConfigORM.min_denominator) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[float](#float)\]</code>) –
- [**min_numerator**](#leadr.boards.adapters.orm.BoardRatioConfigORM.min_numerator) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[float](#float)\]</code>) –
- [**numerator_board**](#leadr.boards.adapters.orm.BoardRatioConfigORM.numerator_board) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[BoardORM](./boards.md#leadr.boards.adapters.orm.BoardORM)\]</code>) –
- [**numerator_board_id**](#leadr.boards.adapters.orm.BoardRatioConfigORM.numerator_board_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**scale**](./boards.md#leadr.boards.adapters.orm.BoardRatioConfigORM.scale) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[int](#int)\]</code>) –
- [**tie_breaker**](#leadr.boards.adapters.orm.BoardRatioConfigORM.tie_breaker) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[TieBreakerEnum](./boards.md#leadr.boards.adapters.orm.TieBreakerEnum)\]</code>) –
- [**updated_at**](#leadr.boards.adapters.orm.BoardRatioConfigORM.updated_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**zero_denominator_policy**](#leadr.boards.adapters.orm.BoardRatioConfigORM.zero_denominator_policy) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[ZeroDenominatorPolicyEnum](./boards.md#leadr.boards.adapters.orm.ZeroDenominatorPolicyEnum)\]</code>) –

####### `leadr.boards.adapters.orm.BoardRatioConfigORM.board`

```python
board: Mapped[BoardORM] = relationship('BoardORM', foreign_keys=[board_id])
```

####### `leadr.boards.adapters.orm.BoardRatioConfigORM.board_id`

```python
board_id: Mapped[UUID] = mapped_column(ForeignKey('boards.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.boards.adapters.orm.BoardRatioConfigORM.created_at`

```python
created_at: Mapped[timestamp]
```

####### `leadr.boards.adapters.orm.BoardRatioConfigORM.decimals`

```python
decimals: Mapped[int] = mapped_column(Integer, nullable=False, default=2)
```

####### `leadr.boards.adapters.orm.BoardRatioConfigORM.deleted_at`

```python
deleted_at: Mapped[nullable_timestamp]
```

####### `leadr.boards.adapters.orm.BoardRatioConfigORM.denominator_board`

```python
denominator_board: Mapped[BoardORM] = relationship('BoardORM', foreign_keys=[denominator_board_id])
```

####### `leadr.boards.adapters.orm.BoardRatioConfigORM.denominator_board_id`

```python
denominator_board_id: Mapped[UUID] = mapped_column(ForeignKey('boards.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.boards.adapters.orm.BoardRatioConfigORM.display`

```python
display: Mapped[RatioDisplayEnum] = mapped_column(Enum(RatioDisplayEnum, name='ratio_display', native_enum=True, values_callable=(lambda x: [(e.value) for e in x]), create_constraint=False), nullable=False, default=(RatioDisplayEnum.RAW), server_default='RAW')
```

####### `leadr.boards.adapters.orm.BoardRatioConfigORM.id`

```python
id: Mapped[uuid_pk]
```

####### `leadr.boards.adapters.orm.BoardRatioConfigORM.min_denominator`

```python
min_denominator: Mapped[float] = mapped_column(Float, nullable=False, default=0)
```

####### `leadr.boards.adapters.orm.BoardRatioConfigORM.min_numerator`

```python
min_numerator: Mapped[float] = mapped_column(Float, nullable=False, default=0)
```

####### `leadr.boards.adapters.orm.BoardRatioConfigORM.numerator_board`

```python
numerator_board: Mapped[BoardORM] = relationship('BoardORM', foreign_keys=[numerator_board_id])
```

####### `leadr.boards.adapters.orm.BoardRatioConfigORM.numerator_board_id`

```python
numerator_board_id: Mapped[UUID] = mapped_column(ForeignKey('boards.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.boards.adapters.orm.BoardRatioConfigORM.scale`

```python
scale: Mapped[int] = mapped_column(Integer, nullable=False, default=1000000)
```

####### `leadr.boards.adapters.orm.BoardRatioConfigORM.tie_breaker`

```python
tie_breaker: Mapped[TieBreakerEnum] = mapped_column(Enum(TieBreakerEnum, name='tie_breaker', native_enum=True, values_callable=(lambda x: [(e.value) for e in x]), create_constraint=False), nullable=False, default=(TieBreakerEnum.NUMERATOR_DESC_DENOMINATOR_ASC), server_default='NUMERATOR_DESC_DENOMINATOR_ASC')
```

####### `leadr.boards.adapters.orm.BoardRatioConfigORM.updated_at`

```python
updated_at: Mapped[timestamp] = mapped_column(onupdate=(func.now()))
```

####### `leadr.boards.adapters.orm.BoardRatioConfigORM.zero_denominator_policy`

```python
zero_denominator_policy: Mapped[ZeroDenominatorPolicyEnum] = mapped_column(Enum(ZeroDenominatorPolicyEnum, name='zero_denominator_policy', native_enum=True, values_callable=(lambda x: [(e.value) for e in x]), create_constraint=False), nullable=False, default=(ZeroDenominatorPolicyEnum.NULL), server_default='NULL')
```

###### `leadr.boards.adapters.orm.BoardStateORM`

Bases: <code>[Base](./common.md#leadr.common.orm.Base)</code>

Board state ORM model.

Represents the materialized ranking state for a single identity on a single board.
Maps to the board_states table with foreign keys to boards and identities.
The primary_value can be NULL for non-rankable entries.

Denormalized fields (from Identity and ScoreEvent) are stored for query efficiency.

**Attributes:**

- [**aux**](./boards.md#leadr.boards.adapters.orm.BoardStateORM.aux) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[dict](#dict)\[[str](#str), [Any](#typing.Any)\] | None\]</code>) –
- [**board**](./boards.md#leadr.boards.adapters.orm.BoardStateORM.board) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[BoardORM](./boards.md#leadr.boards.adapters.orm.BoardORM)\]</code>) –
- [**board_id**](#leadr.boards.adapters.orm.BoardStateORM.board_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**city**](./boards.md#leadr.boards.adapters.orm.BoardStateORM.city) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**country**](./boards.md#leadr.boards.adapters.orm.BoardStateORM.country) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**created_at**](#leadr.boards.adapters.orm.BoardStateORM.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**deleted_at**](#leadr.boards.adapters.orm.BoardStateORM.deleted_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[nullable_timestamp](#leadr.common.orm.nullable_timestamp)\]</code>) –
- [**id**](./boards.md#leadr.boards.adapters.orm.BoardStateORM.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**identity**](./boards.md#leadr.boards.adapters.orm.BoardStateORM.identity) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[IdentityORM](./auth.md#leadr.auth.adapters.orm.IdentityORM)\]</code>) –
- [**identity_id**](#leadr.boards.adapters.orm.BoardStateORM.identity_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**is_test**](#leadr.boards.adapters.orm.BoardStateORM.is_test) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[bool](#bool)\]</code>) –
- [**player_name**](#leadr.boards.adapters.orm.BoardStateORM.player_name) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**primary_value**](#leadr.boards.adapters.orm.BoardStateORM.primary_value) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[float](#float) | None\]</code>) –
- [**state_metadata**](#leadr.boards.adapters.orm.BoardStateORM.state_metadata) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[Any](#typing.Any) | None\]</code>) –
- [**timezone**](./boards.md#leadr.boards.adapters.orm.BoardStateORM.timezone) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**updated_at**](#leadr.boards.adapters.orm.BoardStateORM.updated_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**value_display**](#leadr.boards.adapters.orm.BoardStateORM.value_display) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –

####### `leadr.boards.adapters.orm.BoardStateORM.aux`

```python
aux: Mapped[dict[str, Any] | None] = mapped_column(JSONB, nullable=True, default=None)
```

####### `leadr.boards.adapters.orm.BoardStateORM.board`

```python
board: Mapped[BoardORM] = relationship('BoardORM')
```

####### `leadr.boards.adapters.orm.BoardStateORM.board_id`

```python
board_id: Mapped[UUID] = mapped_column(ForeignKey('boards.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.boards.adapters.orm.BoardStateORM.city`

```python
city: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
```

####### `leadr.boards.adapters.orm.BoardStateORM.country`

```python
country: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
```

####### `leadr.boards.adapters.orm.BoardStateORM.created_at`

```python
created_at: Mapped[timestamp]
```

####### `leadr.boards.adapters.orm.BoardStateORM.deleted_at`

```python
deleted_at: Mapped[nullable_timestamp]
```

####### `leadr.boards.adapters.orm.BoardStateORM.id`

```python
id: Mapped[uuid_pk]
```

####### `leadr.boards.adapters.orm.BoardStateORM.identity`

```python
identity: Mapped[IdentityORM] = relationship('IdentityORM')
```

####### `leadr.boards.adapters.orm.BoardStateORM.identity_id`

```python
identity_id: Mapped[UUID] = mapped_column(ForeignKey('identities.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.boards.adapters.orm.BoardStateORM.is_test`

```python
is_test: Mapped[bool] = mapped_column(Boolean, nullable=False, default=False, server_default=(sa.text('false')))
```

####### `leadr.boards.adapters.orm.BoardStateORM.player_name`

```python
player_name: Mapped[str] = mapped_column(String, nullable=False, default='', server_default='')
```

####### `leadr.boards.adapters.orm.BoardStateORM.primary_value`

```python
primary_value: Mapped[float | None] = mapped_column(Float, nullable=True, default=None)
```

####### `leadr.boards.adapters.orm.BoardStateORM.state_metadata`

```python
state_metadata: Mapped[Any | None] = mapped_column('state_metadata', JSONB, nullable=True, default=None)
```

####### `leadr.boards.adapters.orm.BoardStateORM.timezone`

```python
timezone: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
```

####### `leadr.boards.adapters.orm.BoardStateORM.updated_at`

```python
updated_at: Mapped[timestamp] = mapped_column(onupdate=(func.now()))
```

####### `leadr.boards.adapters.orm.BoardStateORM.value_display`

```python
value_display: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
```

###### `leadr.boards.adapters.orm.BoardTemplateORM`

Bases: <code>[Base](./common.md#leadr.common.orm.Base)</code>

BoardTemplate ORM model.

Represents a template for automatically generating boards at regular intervals.
Maps to the board_templates table with foreign keys to accounts and games.
Uses JSONB column for config to support flexible procedural generation configuration.

**Functions:**

- [**from_domain**](#leadr.boards.adapters.orm.BoardTemplateORM.from_domain) – Convert domain entity to ORM model.
- [**to_domain**](#leadr.boards.adapters.orm.BoardTemplateORM.to_domain) – Convert ORM model to domain entity.

**Attributes:**

- [**account**](./boards.md#leadr.boards.adapters.orm.BoardTemplateORM.account) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[AccountORM](./accounts.md#leadr.accounts.adapters.orm.AccountORM)\]</code>) –
- [**account_id**](#leadr.boards.adapters.orm.BoardTemplateORM.account_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**board_type**](#leadr.boards.adapters.orm.BoardTemplateORM.board_type) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[BoardTypeEnum](./boards.md#leadr.boards.adapters.orm.BoardTypeEnum)\]</code>) –
- [**config**](./boards.md#leadr.boards.adapters.orm.BoardTemplateORM.config) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[dict](#dict)\[[str](#str), [Any](#typing.Any)\]\]</code>) –
- [**created_at**](#leadr.boards.adapters.orm.BoardTemplateORM.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**deleted_at**](#leadr.boards.adapters.orm.BoardTemplateORM.deleted_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[nullable_timestamp](#leadr.common.orm.nullable_timestamp)\]</code>) –
- [**ends_at**](#leadr.boards.adapters.orm.BoardTemplateORM.ends_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime) | None\]</code>) –
- [**game**](./boards.md#leadr.boards.adapters.orm.BoardTemplateORM.game) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[GameORM](./games.md#leadr.games.adapters.orm.GameORM)\]</code>) –
- [**game_id**](#leadr.boards.adapters.orm.BoardTemplateORM.game_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**icon**](./boards.md#leadr.boards.adapters.orm.BoardTemplateORM.icon) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**id**](./boards.md#leadr.boards.adapters.orm.BoardTemplateORM.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**is_active**](#leadr.boards.adapters.orm.BoardTemplateORM.is_active) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[bool](#bool)\]</code>) –
- [**is_published**](#leadr.boards.adapters.orm.BoardTemplateORM.is_published) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[bool](#bool)\]</code>) –
- [**keep_strategy**](#leadr.boards.adapters.orm.BoardTemplateORM.keep_strategy) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[KeepStrategyEnum](./boards.md#leadr.boards.adapters.orm.KeepStrategyEnum)\]</code>) –
- [**name**](./boards.md#leadr.boards.adapters.orm.BoardTemplateORM.name) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**name_template**](#leadr.boards.adapters.orm.BoardTemplateORM.name_template) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**next_run_at**](#leadr.boards.adapters.orm.BoardTemplateORM.next_run_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime)\]</code>) –
- [**repeat_interval**](#leadr.boards.adapters.orm.BoardTemplateORM.repeat_interval) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**series**](./boards.md#leadr.boards.adapters.orm.BoardTemplateORM.series) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**slug**](./boards.md#leadr.boards.adapters.orm.BoardTemplateORM.slug) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**sort_direction**](#leadr.boards.adapters.orm.BoardTemplateORM.sort_direction) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**starts_at**](#leadr.boards.adapters.orm.BoardTemplateORM.starts_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime) | None\]</code>) –
- [**tags**](./boards.md#leadr.boards.adapters.orm.BoardTemplateORM.tags) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[list](#list)\[[str](#str)\]\]</code>) –
- [**unit**](./boards.md#leadr.boards.adapters.orm.BoardTemplateORM.unit) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**updated_at**](#leadr.boards.adapters.orm.BoardTemplateORM.updated_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –

####### `leadr.boards.adapters.orm.BoardTemplateORM.account`

```python
account: Mapped[AccountORM] = relationship('AccountORM')
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.account_id`

```python
account_id: Mapped[UUID] = mapped_column(ForeignKey('accounts.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.board_type`

```python
board_type: Mapped[BoardTypeEnum] = mapped_column(Enum(BoardTypeEnum, name='board_type', native_enum=True, values_callable=(lambda x: [(e.value) for e in x]), create_constraint=False), nullable=False, default=(BoardTypeEnum.RUN_IDENTITY), server_default='RUN_IDENTITY')
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.config`

```python
config: Mapped[dict[str, Any]] = mapped_column(JSONB, nullable=False, default=dict, server_default='{}')
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.created_at`

```python
created_at: Mapped[timestamp]
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.deleted_at`

```python
deleted_at: Mapped[nullable_timestamp]
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.ends_at`

```python
ends_at: Mapped[datetime | None] = mapped_column(DateTime(timezone=True), nullable=True, default=None)
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.from_domain`

```python
from_domain(entity)
```

Convert domain entity to ORM model.

**Parameters:**

- **entity** (<code>[BoardTemplate](#leadr.boards.domain.board_template.BoardTemplate)</code>) – The BoardTemplate domain entity to convert.

**Returns:**

- <code>[BoardTemplateORM](./boards.md#leadr.boards.adapters.orm.BoardTemplateORM)</code> – BoardTemplateORM model with all fields populated from domain entity.

####### `leadr.boards.adapters.orm.BoardTemplateORM.game`

```python
game: Mapped[GameORM] = relationship('GameORM')
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.game_id`

```python
game_id: Mapped[UUID] = mapped_column(ForeignKey('games.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.icon`

```python
icon: Mapped[str | None] = mapped_column(String, nullable=True)
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.id`

```python
id: Mapped[uuid_pk]
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.is_active`

```python
is_active: Mapped[bool] = mapped_column(Boolean, nullable=False)
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.is_published`

```python
is_published: Mapped[bool] = mapped_column(Boolean, nullable=False, default=True, server_default=(sa.text('true')))
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.keep_strategy`

```python
keep_strategy: Mapped[KeepStrategyEnum] = mapped_column(Enum(KeepStrategyEnum, name='keep_strategy', native_enum=True, values_callable=(lambda x: [(e.value) for e in x]), create_constraint=False), nullable=False, default=(KeepStrategyEnum.BEST), server_default='BEST')
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.name`

```python
name: Mapped[str] = mapped_column(String, nullable=False)
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.name_template`

```python
name_template: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.next_run_at`

```python
next_run_at: Mapped[datetime] = mapped_column(DateTime(timezone=True), nullable=False)
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.repeat_interval`

```python
repeat_interval: Mapped[str] = mapped_column(String, nullable=False)
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.series`

```python
series: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.slug`

```python
slug: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.sort_direction`

```python
sort_direction: Mapped[str] = mapped_column(String, nullable=False)
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.starts_at`

```python
starts_at: Mapped[datetime | None] = mapped_column(DateTime(timezone=True), nullable=True, default=None)
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.tags`

```python
tags: Mapped[list[str]] = mapped_column(ARRAY(String), nullable=False, default=list, server_default='{}')
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.to_domain`

```python
to_domain()
```

Convert ORM model to domain entity.

**Returns:**

- <code>[BoardTemplate](#leadr.boards.domain.board_template.BoardTemplate)</code> – BoardTemplate domain entity with all fields populated from ORM model.

####### `leadr.boards.adapters.orm.BoardTemplateORM.unit`

```python
unit: Mapped[str | None] = mapped_column(String, nullable=True)
```

####### `leadr.boards.adapters.orm.BoardTemplateORM.updated_at`

```python
updated_at: Mapped[timestamp] = mapped_column(onupdate=(func.now()))
```

###### `leadr.boards.adapters.orm.BoardTypeEnum`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Board type enum for database.

**Attributes:**

- [**COUNTER**](./boards.md#leadr.boards.adapters.orm.BoardTypeEnum.COUNTER) –
- [**RATIO**](./boards.md#leadr.boards.adapters.orm.BoardTypeEnum.RATIO) –
- [**RUN_IDENTITY**](#leadr.boards.adapters.orm.BoardTypeEnum.RUN_IDENTITY) –
- [**RUN_RUNS**](#leadr.boards.adapters.orm.BoardTypeEnum.RUN_RUNS) –

####### `leadr.boards.adapters.orm.BoardTypeEnum.COUNTER`

```python
COUNTER = 'COUNTER'
```

####### `leadr.boards.adapters.orm.BoardTypeEnum.RATIO`

```python
RATIO = 'RATIO'
```

####### `leadr.boards.adapters.orm.BoardTypeEnum.RUN_IDENTITY`

```python
RUN_IDENTITY = 'RUN_IDENTITY'
```

####### `leadr.boards.adapters.orm.BoardTypeEnum.RUN_RUNS`

```python
RUN_RUNS = 'RUN_RUNS'
```

###### `leadr.boards.adapters.orm.KeepStrategyEnum`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Keep strategy enum for database.

**Attributes:**

- [**BEST**](./boards.md#leadr.boards.adapters.orm.KeepStrategyEnum.BEST) –
- [**FIRST**](./boards.md#leadr.boards.adapters.orm.KeepStrategyEnum.FIRST) –
- [**LATEST**](./boards.md#leadr.boards.adapters.orm.KeepStrategyEnum.LATEST) –
- [**NA**](./boards.md#leadr.boards.adapters.orm.KeepStrategyEnum.NA) –

####### `leadr.boards.adapters.orm.KeepStrategyEnum.BEST`

```python
BEST = 'BEST'
```

####### `leadr.boards.adapters.orm.KeepStrategyEnum.FIRST`

```python
FIRST = 'FIRST'
```

####### `leadr.boards.adapters.orm.KeepStrategyEnum.LATEST`

```python
LATEST = 'LATEST'
```

####### `leadr.boards.adapters.orm.KeepStrategyEnum.NA`

```python
NA = 'NA'
```

###### `leadr.boards.adapters.orm.RatioDisplayEnum`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Ratio display enum for database.

**Attributes:**

- [**PERCENT**](./boards.md#leadr.boards.adapters.orm.RatioDisplayEnum.PERCENT) –
- [**RAW**](./boards.md#leadr.boards.adapters.orm.RatioDisplayEnum.RAW) –

####### `leadr.boards.adapters.orm.RatioDisplayEnum.PERCENT`

```python
PERCENT = 'PERCENT'
```

####### `leadr.boards.adapters.orm.RatioDisplayEnum.RAW`

```python
RAW = 'RAW'
```

###### `leadr.boards.adapters.orm.RunEntryORM`

Bases: <code>[Base](./common.md#leadr.common.orm.Base)</code>

Run entry ORM model.

Represents a single scored run entry for RUN_RUNS boards where every
submission is ranked. Maps to the run_entries table with foreign keys
to boards, identities, and score_events.

Denormalized fields (from Identity and ScoreEvent) are stored for query efficiency.

**Attributes:**

- [**board**](./boards.md#leadr.boards.adapters.orm.RunEntryORM.board) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[BoardORM](./boards.md#leadr.boards.adapters.orm.BoardORM)\]</code>) –
- [**board_id**](#leadr.boards.adapters.orm.RunEntryORM.board_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**city**](./boards.md#leadr.boards.adapters.orm.RunEntryORM.city) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**country**](./boards.md#leadr.boards.adapters.orm.RunEntryORM.country) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**created_at**](#leadr.boards.adapters.orm.RunEntryORM.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**deleted_at**](#leadr.boards.adapters.orm.RunEntryORM.deleted_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[nullable_timestamp](#leadr.common.orm.nullable_timestamp)\]</code>) –
- [**entry_metadata**](#leadr.boards.adapters.orm.RunEntryORM.entry_metadata) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[Any](#typing.Any) | None\]</code>) –
- [**excluded_at**](#leadr.boards.adapters.orm.RunEntryORM.excluded_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime) | None\]</code>) –
- [**excluded_reason**](#leadr.boards.adapters.orm.RunEntryORM.excluded_reason) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**id**](./boards.md#leadr.boards.adapters.orm.RunEntryORM.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**identity**](./boards.md#leadr.boards.adapters.orm.RunEntryORM.identity) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[IdentityORM](./auth.md#leadr.auth.adapters.orm.IdentityORM)\]</code>) –
- [**identity_id**](#leadr.boards.adapters.orm.RunEntryORM.identity_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**is_test**](#leadr.boards.adapters.orm.RunEntryORM.is_test) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[bool](#bool)\]</code>) –
- [**player_name**](#leadr.boards.adapters.orm.RunEntryORM.player_name) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**primary_value**](#leadr.boards.adapters.orm.RunEntryORM.primary_value) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[float](#float)\]</code>) –
- [**score_event**](#leadr.boards.adapters.orm.RunEntryORM.score_event) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[ScoreEventORM](./scores.md#leadr.scores.adapters.orm.ScoreEventORM)\]</code>) –
- [**score_event_id**](#leadr.boards.adapters.orm.RunEntryORM.score_event_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**timezone**](./boards.md#leadr.boards.adapters.orm.RunEntryORM.timezone) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**updated_at**](#leadr.boards.adapters.orm.RunEntryORM.updated_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**value_display**](#leadr.boards.adapters.orm.RunEntryORM.value_display) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –

####### `leadr.boards.adapters.orm.RunEntryORM.board`

```python
board: Mapped[BoardORM] = relationship('BoardORM')
```

####### `leadr.boards.adapters.orm.RunEntryORM.board_id`

```python
board_id: Mapped[UUID] = mapped_column(ForeignKey('boards.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.boards.adapters.orm.RunEntryORM.city`

```python
city: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
```

####### `leadr.boards.adapters.orm.RunEntryORM.country`

```python
country: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
```

####### `leadr.boards.adapters.orm.RunEntryORM.created_at`

```python
created_at: Mapped[timestamp]
```

####### `leadr.boards.adapters.orm.RunEntryORM.deleted_at`

```python
deleted_at: Mapped[nullable_timestamp]
```

####### `leadr.boards.adapters.orm.RunEntryORM.entry_metadata`

```python
entry_metadata: Mapped[Any | None] = mapped_column('entry_metadata', JSONB, nullable=True, default=None)
```

####### `leadr.boards.adapters.orm.RunEntryORM.excluded_at`

```python
excluded_at: Mapped[datetime | None] = mapped_column(DateTime(timezone=True), nullable=True, default=None)
```

####### `leadr.boards.adapters.orm.RunEntryORM.excluded_reason`

```python
excluded_reason: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
```

####### `leadr.boards.adapters.orm.RunEntryORM.id`

```python
id: Mapped[uuid_pk]
```

####### `leadr.boards.adapters.orm.RunEntryORM.identity`

```python
identity: Mapped[IdentityORM] = relationship('IdentityORM')
```

####### `leadr.boards.adapters.orm.RunEntryORM.identity_id`

```python
identity_id: Mapped[UUID] = mapped_column(ForeignKey('identities.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.boards.adapters.orm.RunEntryORM.is_test`

```python
is_test: Mapped[bool] = mapped_column(Boolean, nullable=False, default=False, server_default=(sa.text('false')))
```

####### `leadr.boards.adapters.orm.RunEntryORM.player_name`

```python
player_name: Mapped[str] = mapped_column(String, nullable=False, default='', server_default='')
```

####### `leadr.boards.adapters.orm.RunEntryORM.primary_value`

```python
primary_value: Mapped[float] = mapped_column(Float, nullable=False)
```

####### `leadr.boards.adapters.orm.RunEntryORM.score_event`

```python
score_event: Mapped[ScoreEventORM] = relationship('ScoreEventORM')
```

####### `leadr.boards.adapters.orm.RunEntryORM.score_event_id`

```python
score_event_id: Mapped[UUID] = mapped_column(ForeignKey('score_events.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.boards.adapters.orm.RunEntryORM.timezone`

```python
timezone: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
```

####### `leadr.boards.adapters.orm.RunEntryORM.updated_at`

```python
updated_at: Mapped[timestamp] = mapped_column(onupdate=(func.now()))
```

####### `leadr.boards.adapters.orm.RunEntryORM.value_display`

```python
value_display: Mapped[str | None] = mapped_column(String, nullable=True, default=None)
```

###### `leadr.boards.adapters.orm.TieBreakerEnum`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Tie breaker enum for database.

**Attributes:**

- [**NUMERATOR_DESC_DENOMINATOR_ASC**](#leadr.boards.adapters.orm.TieBreakerEnum.NUMERATOR_DESC_DENOMINATOR_ASC) –

####### `leadr.boards.adapters.orm.TieBreakerEnum.NUMERATOR_DESC_DENOMINATOR_ASC`

```python
NUMERATOR_DESC_DENOMINATOR_ASC = 'NUMERATOR_DESC_DENOMINATOR_ASC'
```

###### `leadr.boards.adapters.orm.ZeroDenominatorPolicyEnum`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Zero denominator policy enum for database.

**Attributes:**

- [**INFINITY**](./boards.md#leadr.boards.adapters.orm.ZeroDenominatorPolicyEnum.INFINITY) –
- [**NULL**](./boards.md#leadr.boards.adapters.orm.ZeroDenominatorPolicyEnum.NULL) –
- [**ZERO**](./boards.md#leadr.boards.adapters.orm.ZeroDenominatorPolicyEnum.ZERO) –

####### `leadr.boards.adapters.orm.ZeroDenominatorPolicyEnum.INFINITY`

```python
INFINITY = 'INFINITY'
```

####### `leadr.boards.adapters.orm.ZeroDenominatorPolicyEnum.NULL`

```python
NULL = 'NULL'
```

####### `leadr.boards.adapters.orm.ZeroDenominatorPolicyEnum.ZERO`

```python
ZERO = 'ZERO'
```

#### `leadr.boards.api`

**Modules:**

- [**board_routes**](#leadr.boards.api.board_routes) – Board API routes.
- [**board_schemas**](#leadr.boards.api.board_schemas) – API request and response models for boards.
- [**board_state_routes**](#leadr.boards.api.board_state_routes) – API routes for board state management (admin only, read-only).
- [**board_state_schemas**](#leadr.boards.api.board_state_schemas) – API response models for board states.
- [**board_template_routes**](#leadr.boards.api.board_template_routes) – Board template API routes.
- [**board_template_schemas**](#leadr.boards.api.board_template_schemas) – API request and response models for board templates.
- [**run_entry_routes**](#leadr.boards.api.run_entry_routes) – API routes for run entry management (admin only, read-only).
- [**run_entry_schemas**](#leadr.boards.api.run_entry_schemas) – API response models for run entries.

##### `leadr.boards.api.board_routes`

Board API routes.

**Functions:**

- [**create_board**](#leadr.boards.api.board_routes.create_board) – Create a new board.
- [**get_board**](#leadr.boards.api.board_routes.get_board) – Get a board by ID.
- [**handle_list_boards**](#leadr.boards.api.board_routes.handle_list_boards) – Shared handler for listing boards with filtering.
- [**list_boards_admin**](#leadr.boards.api.board_routes.list_boards_admin) – List boards (Admin API).
- [**list_boards_client**](#leadr.boards.api.board_routes.list_boards_client) – List boards (Client API).
- [**update_board**](#leadr.boards.api.board_routes.update_board) – Update a board.

**Attributes:**

- [**client_router**](#leadr.boards.api.board_routes.client_router) –
- [**logger**](#leadr.boards.api.board_routes.logger) –
- [**router**](#leadr.boards.api.board_routes.router) –

###### `leadr.boards.api.board_routes.client_router`

```python
client_router = APIRouter()
```

###### `leadr.boards.api.board_routes.create_board`

```python
create_board(request, service, ratio_config_service, auth, background_tasks, pre_create_hook, post_create_hook)
```

Create a new board.

Creates a new leaderboard associated with an existing game and account.
The game must belong to the specified account.

For regular users, account_id must match their API key's account.
For superadmins, any account_id is accepted.

For RATIO boards, ratio_config is required and specifies the numerator and
denominator boards used to calculate the ratio.

**Parameters:**

- **request** (<code>[BoardCreateRequest](#leadr.boards.api.board_schemas.BoardCreateRequest)</code>) – Board creation details including account_id, game_id, name, and settings.
- **service** (<code>[BoardServiceDep](./boards.md#leadr.boards.services.dependencies.BoardServiceDep)</code>) – Injected board service dependency.
- **ratio_config_service** (<code>[BoardRatioConfigServiceDep](./boards.md#leadr.boards.services.dependencies.BoardRatioConfigServiceDep)</code>) – Injected ratio config service dependency.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.
- **pre_create_hook** (<code>[PreCreateBoardHookDep](./common.md#leadr.common.api.hooks.PreCreateBoardHookDep)</code>) – Hook called before board creation (for quota checks).
- **post_create_hook** (<code>[PostCreateBoardHookDep](./common.md#leadr.common.api.hooks.PostCreateBoardHookDep)</code>) – Hook called after successful board creation.

**Returns:**

- <code>[BoardResponse](#leadr.boards.api.board_schemas.BoardResponse)</code> – BoardResponse with the created board including auto-generated ID and timestamps.

**Raises:**

- <code>403</code> – User does not have access to the specified account.
- <code>404</code> – Game or account not found.
- <code>400</code> – Game doesn't belong to the specified account, or RATIO board missing config.

###### `leadr.boards.api.board_routes.get_board`

```python
get_board(board_id, service, ratio_config_service, auth)
```

Get a board by ID.

**Parameters:**

- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – Unique identifier for the board.
- **service** (<code>[BoardServiceDep](./boards.md#leadr.boards.services.dependencies.BoardServiceDep)</code>) – Injected board service dependency.
- **ratio_config_service** (<code>[BoardRatioConfigServiceDep](./boards.md#leadr.boards.services.dependencies.BoardRatioConfigServiceDep)</code>) – Injected ratio config service dependency.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.

**Returns:**

- <code>[BoardResponse](#leadr.boards.api.board_schemas.BoardResponse)</code> – BoardResponse with full board details (including ratio_config for RATIO boards).

**Raises:**

- <code>403</code> – User does not have access to this board's account.
- <code>404</code> – Board not found.

###### `leadr.boards.api.board_routes.handle_list_boards`

```python
handle_list_boards(auth, service, game_service, pagination, account_id, game_id, code, game_slug, slug, is_active, is_published, starts_before, starts_after, ends_before, ends_after)
```

Shared handler for listing boards with filtering.

**Parameters:**

- **auth** (<code>[AuthContext](./auth.md#leadr.auth.dependencies.AuthContext)</code>) – Authentication context with user info.
- **service** (<code>[BoardService](#leadr.boards.services.board_service.BoardService)</code>) – Board service instance.
- **game_service** (<code>[GameService](#leadr.games.services.game_service.GameService)</code>) – Game service instance for game_slug resolution.
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (cursor, limit, sort).
- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – Optional account ID to filter boards by.
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID) | None</code>) – Optional game ID to filter boards by.
- **code** (<code>[str](#str) | None</code>) – Optional short code to filter boards by.
- **game_slug** (<code>[str](#str) | None</code>) – Optional game slug to filter boards by game (resolves to game_id).
- **slug** (<code>[str](#str) | None</code>) – Optional board slug to filter by specific board (requires game_slug).
- **is_active** (<code>[bool](#bool) | None</code>) – Optional filter for active status.
- **is_published** (<code>[bool](#bool) | None</code>) – Optional filter for published status.
- **starts_before** (<code>[datetime](#datetime.datetime) | None</code>) – Optional filter for boards starting before this time.
- **starts_after** (<code>[datetime](#datetime.datetime) | None</code>) – Optional filter for boards starting after this time.
- **ends_before** (<code>[datetime](#datetime.datetime) | None</code>) – Optional filter for boards ending before this time.
- **ends_after** (<code>[datetime](#datetime.datetime) | None</code>) – Optional filter for boards ending after this time.

**Returns:**

- <code>[PaginatedResponse](./common.md#leadr.common.api.pagination.PaginatedResponse)\[[BoardResponse](#leadr.boards.api.board_schemas.BoardResponse)\]</code> – PaginatedResponse with boards and pagination metadata.

**Raises:**

- <code>400</code> – Invalid cursor, sort field, or cursor state mismatch.
- <code>404</code> – Game or board not found when using slug filters.

###### `leadr.boards.api.board_routes.list_boards_admin`

```python
list_boards_admin(auth, service, game_service, pagination, account_id=None, game_id=None, code=None, game_slug=None, slug=None, is_active=None, is_published=None, starts_before=None, starts_after=None, ends_before=None, ends_after=None)
```

List boards (Admin API).

For regular users:

- If account_id not provided, defaults to their API key's account
- If account_id provided and they are superadmin, can access any account
- If account_id provided and NOT superadmin, must match their account (validated in AuthContext)

Filtering:

- Use ?game_id={id} or ?game_slug={slug} to filter boards by game
- Use ?game_slug={game_slug}&slug={slug} to find a specific board within a game
- Use ?code={code} to filter boards by short code
- Use ?is_active=true/false to filter by active status
- Use ?is_published=true/false to filter by published status
- Use ?starts_before=<datetime>&starts_after=<datetime> for start date range
- Use ?ends_before=<datetime>&ends_after=<datetime> for end date range
- Note: board slug filter requires game_slug parameter

Pagination:

- Default: 20 items per page, sorted by created_at:desc,id:asc
- Custom sort: Use ?sort=name:asc,created_at:desc
- Valid sort fields: id, name, slug, short_code, created_at, updated_at
- Navigation: Use next_cursor/prev_cursor from response

<details class="example" open markdown="1">
<summary>Example</summary>

GET /v1/boards?account_id=acc_123&limit=50&sort=name:asc
GET /v1/boards?game_slug=my-game&is_active=true
GET /v1/boards?game_slug=my-game&slug=weekly-challenge
GET /v1/boards?starts_after=2025-01-01T00:00:00Z&ends_before=2025-12-31T23:59:59Z

</details>

**Parameters:**

- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Admin authentication context with user info.
- **service** (<code>[BoardServiceDep](./boards.md#leadr.boards.services.dependencies.BoardServiceDep)</code>) – Injected board service dependency.
- **game_service** (<code>[GameServiceDep](./games.md#leadr.games.services.dependencies.GameServiceDep)</code>) – Injected game service dependency.
- **pagination** (<code>[Annotated](#typing.Annotated)\[[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams), [Depends](#fastapi.Depends)()\]</code>) – Pagination parameters (cursor, limit, sort).
- **account_id** (<code>[Annotated](#typing.Annotated)\[[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None, [Query](#fastapi.Query)(description='Filter by account ID')\]</code>) – Optional account ID to filter boards by.
- **game_id** (<code>[Annotated](#typing.Annotated)\[[GameID](./common.md#leadr.common.domain.ids.GameID) | None, [Query](#fastapi.Query)(description='Filter by game ID')\]</code>) – Optional game ID to filter boards by.
- **code** (<code>[Annotated](#typing.Annotated)\[[str](#str) | None, [Query](#fastapi.Query)(description='Filter by short code')\]</code>) – Optional short code to filter boards by.
- **game_slug** (<code>[Annotated](#typing.Annotated)\[[str](#str) | None, [Query](#fastapi.Query)(description='Filter by game slug')\]</code>) – Optional game slug to filter boards by game (resolves to game_id).
- **slug** (<code>[Annotated](#typing.Annotated)\[[str](#str) | None, [Query](#fastapi.Query)(description='Filter by board slug (requires game_slug)')\]</code>) – Optional board slug to filter by specific board (requires game_slug).
- **is_active** (<code>[Annotated](#typing.Annotated)\[[bool](#bool) | None, [Query](#fastapi.Query)(description='Filter by active status')\]</code>) – Optional filter for active status.
- **is_published** (<code>[Annotated](#typing.Annotated)\[[bool](#bool) | None, [Query](#fastapi.Query)(description='Filter by published status')\]</code>) – Optional filter for published status.
- **starts_before** (<code>[Annotated](#typing.Annotated)\[[datetime](#datetime.datetime) | None, [Query](#fastapi.Query)(description='Filter boards starting before this time (ISO 8601)')\]</code>) – Optional filter for boards starting before this time.
- **starts_after** (<code>[Annotated](#typing.Annotated)\[[datetime](#datetime.datetime) | None, [Query](#fastapi.Query)(description='Filter boards starting after this time (ISO 8601)')\]</code>) – Optional filter for boards starting after this time.
- **ends_before** (<code>[Annotated](#typing.Annotated)\[[datetime](#datetime.datetime) | None, [Query](#fastapi.Query)(description='Filter boards ending before this time (ISO 8601)')\]</code>) – Optional filter for boards ending before this time.
- **ends_after** (<code>[Annotated](#typing.Annotated)\[[datetime](#datetime.datetime) | None, [Query](#fastapi.Query)(description='Filter boards ending after this time (ISO 8601)')\]</code>) – Optional filter for boards ending after this time.

**Returns:**

- <code>[PaginatedResponse](./common.md#leadr.common.api.pagination.PaginatedResponse)\[[BoardResponse](#leadr.boards.api.board_schemas.BoardResponse)\]</code> – PaginatedResponse with boards and pagination metadata.

**Raises:**

- <code>400</code> – Invalid cursor, sort field, cursor state mismatch, or slug without game_slug.
- <code>404</code> – Game or board not found when using slug filters.

###### `leadr.boards.api.board_routes.list_boards_client`

```python
list_boards_client(auth, service, game_service, pagination, code=None, slug=None, is_published=None, starts_before=None, starts_after=None, ends_before=None, ends_after=None)
```

List boards (Client API).

Account ID and game ID are automatically derived from the authenticated client session.
Clients can optionally filter by various criteria to find specific boards.

Filtering:

- Use ?slug={slug} to find a specific board within the authenticated game
- Use ?code={code} to filter boards by short code
- Use ?is_published=true/false to filter by published status
- Use ?starts_before=<datetime>&starts_after=<datetime> for start date range
- Use ?ends_before=<datetime>&ends_after=<datetime> for end date range

Pagination:

- Default: 20 items per page, sorted by created_at:desc,id:asc
- Custom sort: Use ?sort=name:asc,created_at:desc
- Valid sort fields: id, name, slug, short_code, created_at, updated_at
- Navigation: Use next_cursor/prev_cursor from response

<details class="example" open markdown="1">
<summary>Example</summary>

GET /v1/client/boards?code=WEEKLY-CHALLENGE&limit=50
GET /v1/client/boards?slug=weekly-challenge
GET /v1/client/boards?is_published=true
GET /v1/client/boards?starts_after=2025-01-01T00:00:00Z

</details>

**Parameters:**

- **auth** (<code>[ClientAuthContextDep](./auth.md#leadr.auth.dependencies.ClientAuthContextDep)</code>) – Client authentication context with device info.
- **service** (<code>[BoardServiceDep](./boards.md#leadr.boards.services.dependencies.BoardServiceDep)</code>) – Injected board service dependency.
- **game_service** (<code>[GameServiceDep](./games.md#leadr.games.services.dependencies.GameServiceDep)</code>) – Injected game service dependency.
- **pagination** (<code>[Annotated](#typing.Annotated)\[[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams), [Depends](#fastapi.Depends)()\]</code>) – Pagination parameters (cursor, limit, sort).
- **code** (<code>[Annotated](#typing.Annotated)\[[str](#str) | None, [Query](#fastapi.Query)(description='Filter by short code')\]</code>) – Optional short code to filter boards by.
- **slug** (<code>[Annotated](#typing.Annotated)\[[str](#str) | None, [Query](#fastapi.Query)(description='Filter by board slug')\]</code>) – Optional board slug to filter by specific board.
- **is_published** (<code>[Annotated](#typing.Annotated)\[[bool](#bool) | None, [Query](#fastapi.Query)(description='Filter by published status')\]</code>) – Optional filter for published status.
- **starts_before** (<code>[Annotated](#typing.Annotated)\[[datetime](#datetime.datetime) | None, [Query](#fastapi.Query)(description='Filter boards starting before this time (ISO 8601)')\]</code>) – Optional filter for boards starting before this time.
- **starts_after** (<code>[Annotated](#typing.Annotated)\[[datetime](#datetime.datetime) | None, [Query](#fastapi.Query)(description='Filter boards starting after this time (ISO 8601)')\]</code>) – Optional filter for boards starting after this time.
- **ends_before** (<code>[Annotated](#typing.Annotated)\[[datetime](#datetime.datetime) | None, [Query](#fastapi.Query)(description='Filter boards ending before this time (ISO 8601)')\]</code>) – Optional filter for boards ending before this time.
- **ends_after** (<code>[Annotated](#typing.Annotated)\[[datetime](#datetime.datetime) | None, [Query](#fastapi.Query)(description='Filter boards ending after this time (ISO 8601)')\]</code>) – Optional filter for boards ending after this time.

**Returns:**

- <code>[PaginatedResponse](./common.md#leadr.common.api.pagination.PaginatedResponse)\[[BoardResponse](#leadr.boards.api.board_schemas.BoardResponse)\]</code> – PaginatedResponse with boards and pagination metadata.

**Raises:**

- <code>400</code> – Invalid cursor, sort field, or cursor state mismatch.

###### `leadr.boards.api.board_routes.logger`

```python
logger = logging.getLogger(__name__)
```

###### `leadr.boards.api.board_routes.router`

```python
router = APIRouter()
```

###### `leadr.boards.api.board_routes.update_board`

```python
update_board(board_id, request, service, ratio_config_service, auth)
```

Update a board.

Supports updating any board field or soft-deleting the board.
For RATIO boards, ratio_config can be updated to change calculation settings.

**Parameters:**

- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – Unique identifier for the board.
- **request** (<code>[BoardUpdateRequest](#leadr.boards.api.board_schemas.BoardUpdateRequest)</code>) – Board update details (all fields optional).
- **service** (<code>[BoardServiceDep](./boards.md#leadr.boards.services.dependencies.BoardServiceDep)</code>) – Injected board service dependency.
- **ratio_config_service** (<code>[BoardRatioConfigServiceDep](./boards.md#leadr.boards.services.dependencies.BoardRatioConfigServiceDep)</code>) – Injected ratio config service dependency.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.

**Returns:**

- <code>[BoardResponse](#leadr.boards.api.board_schemas.BoardResponse)</code> – BoardResponse with the updated board details.

**Raises:**

- <code>403</code> – User does not have access to this board's account.
- <code>404</code> – Board not found.

##### `leadr.boards.api.board_schemas`

API request and response models for boards.

**Classes:**

- [**BoardCreateRequest**](#leadr.boards.api.board_schemas.BoardCreateRequest) – Request model for creating a board.
- [**BoardRatioConfigRequest**](#leadr.boards.api.board_schemas.BoardRatioConfigRequest) – Request model for ratio config when creating/updating a RATIO board.
- [**BoardRatioConfigResponse**](#leadr.boards.api.board_schemas.BoardRatioConfigResponse) – Response model for ratio config.
- [**BoardResponse**](#leadr.boards.api.board_schemas.BoardResponse) – Response model for a board.
- [**BoardUpdateRequest**](#leadr.boards.api.board_schemas.BoardUpdateRequest) – Request model for updating a board.

###### `leadr.boards.api.board_schemas.BoardCreateRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request model for creating a board.

**Attributes:**

- [**account_id**](#leadr.boards.api.board_schemas.BoardCreateRequest.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**board_type**](#leadr.boards.api.board_schemas.BoardCreateRequest.board_type) (<code>[BoardType](./boards.md#leadr.boards.domain.board.BoardType)</code>) –
- [**created_from_template_id**](#leadr.boards.api.board_schemas.BoardCreateRequest.created_from_template_id) (<code>[BoardTemplateID](./common.md#leadr.common.domain.ids.BoardTemplateID) | None</code>) –
- [**description**](#leadr.boards.api.board_schemas.BoardCreateRequest.description) (<code>[str](#str) | None</code>) –
- [**ends_at**](#leadr.boards.api.board_schemas.BoardCreateRequest.ends_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**game_id**](#leadr.boards.api.board_schemas.BoardCreateRequest.game_id) (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) –
- [**icon**](#leadr.boards.api.board_schemas.BoardCreateRequest.icon) (<code>[str](#str) | None</code>) –
- [**is_active**](#leadr.boards.api.board_schemas.BoardCreateRequest.is_active) (<code>[bool](#bool)</code>) –
- [**is_published**](#leadr.boards.api.board_schemas.BoardCreateRequest.is_published) (<code>[bool](#bool)</code>) –
- [**keep_strategy**](#leadr.boards.api.board_schemas.BoardCreateRequest.keep_strategy) (<code>[KeepStrategy](./boards.md#leadr.boards.domain.board.KeepStrategy) | None</code>) –
- [**name**](#leadr.boards.api.board_schemas.BoardCreateRequest.name) (<code>[str](#str)</code>) –
- [**ratio_config**](#leadr.boards.api.board_schemas.BoardCreateRequest.ratio_config) (<code>[BoardRatioConfigRequest](#leadr.boards.api.board_schemas.BoardRatioConfigRequest) | None</code>) –
- [**short_code**](#leadr.boards.api.board_schemas.BoardCreateRequest.short_code) (<code>[str](#str) | None</code>) –
- [**slug**](#leadr.boards.api.board_schemas.BoardCreateRequest.slug) (<code>[str](#str) | None</code>) –
- [**sort_direction**](#leadr.boards.api.board_schemas.BoardCreateRequest.sort_direction) (<code>[SortDirection](./boards.md#leadr.boards.domain.board.SortDirection)</code>) –
- [**starts_at**](#leadr.boards.api.board_schemas.BoardCreateRequest.starts_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**tags**](#leadr.boards.api.board_schemas.BoardCreateRequest.tags) (<code>[list](#list)\[[str](#str)\] | None</code>) –
- [**template_name**](#leadr.boards.api.board_schemas.BoardCreateRequest.template_name) (<code>[str](#str) | None</code>) –
- [**unit**](#leadr.boards.api.board_schemas.BoardCreateRequest.unit) (<code>[str](#str) | None</code>) –

####### `leadr.boards.api.board_schemas.BoardCreateRequest.account_id`

```python
account_id: AccountID = Field(description='ID of the account this board belongs to')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.board_type`

```python
board_type: BoardType = Field(default=(BoardType.RUN_IDENTITY), description='Type of board determining score behavior')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.created_from_template_id`

```python
created_from_template_id: BoardTemplateID | None = Field(default=None, description='Optional template ID this board was created from')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.description`

```python
description: str | None = Field(default=None, description='Optional short description of the board')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.ends_at`

```python
ends_at: datetime | None = Field(default=None, description='Optional end time for time-bounded boards (UTC)')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.game_id`

```python
game_id: GameID = Field(description='ID of the game this board belongs to')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.icon`

```python
icon: str | None = Field(default='fa-crown', description="Icon identifier for the board. Defaults to 'fa-crown'")
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.is_active`

```python
is_active: bool = Field(default=True, description='Whether the board is currently active')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.is_published`

```python
is_published: bool = Field(default=True, description='Whether the board is published and visible on public web views')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.keep_strategy`

```python
keep_strategy: KeepStrategy | None = Field(default=None, description='Strategy for keeping scores (RUN_IDENTITY boards only). Defaults to BEST for RUN_IDENTITY, ignored for other board types.')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.name`

```python
name: str = Field(description='Name of the board')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.ratio_config`

```python
ratio_config: BoardRatioConfigRequest | None = Field(default=None, description='Ratio config (required when board_type is RATIO)')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.short_code`

```python
short_code: str | None = Field(default=None, description='Globally unique short code for direct sharing. Auto-generated if not provided')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.slug`

```python
slug: str | None = Field(default=None, description='Optional URL-friendly slug. If not provided, will be auto-generated from name')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.sort_direction`

```python
sort_direction: SortDirection = Field(default=(SortDirection.DESCENDING), description='Direction to sort scores')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.starts_at`

```python
starts_at: datetime | None = Field(default=None, description='Optional start time for time-bounded boards (UTC)')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.tags`

```python
tags: list[str] | None = Field(default=None, description='Optional list of tags for categorization')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.template_name`

```python
template_name: str | None = Field(default=None, description='Optional template name this board was created from')
```

####### `leadr.boards.api.board_schemas.BoardCreateRequest.unit`

```python
unit: str | None = Field(default=None, description="Unit of measurement for scores (e.g., 'seconds', 'points'). Optional")
```

###### `leadr.boards.api.board_schemas.BoardRatioConfigRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request model for ratio config when creating/updating a RATIO board.

**Attributes:**

- [**decimals**](#leadr.boards.api.board_schemas.BoardRatioConfigRequest.decimals) (<code>[int](#int)</code>) –
- [**denominator_board_id**](#leadr.boards.api.board_schemas.BoardRatioConfigRequest.denominator_board_id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) –
- [**display**](#leadr.boards.api.board_schemas.BoardRatioConfigRequest.display) (<code>[RatioDisplay](#leadr.boards.domain.board_ratio_config.RatioDisplay)</code>) –
- [**min_denominator**](#leadr.boards.api.board_schemas.BoardRatioConfigRequest.min_denominator) (<code>[float](#float)</code>) –
- [**min_numerator**](#leadr.boards.api.board_schemas.BoardRatioConfigRequest.min_numerator) (<code>[float](#float)</code>) –
- [**numerator_board_id**](#leadr.boards.api.board_schemas.BoardRatioConfigRequest.numerator_board_id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) –
- [**scale**](#leadr.boards.api.board_schemas.BoardRatioConfigRequest.scale) (<code>[int](#int)</code>) –
- [**tie_breaker**](#leadr.boards.api.board_schemas.BoardRatioConfigRequest.tie_breaker) (<code>[TieBreaker](#leadr.boards.domain.board_ratio_config.TieBreaker)</code>) –
- [**zero_denominator_policy**](#leadr.boards.api.board_schemas.BoardRatioConfigRequest.zero_denominator_policy) (<code>[ZeroDenominatorPolicy](#leadr.boards.domain.board_ratio_config.ZeroDenominatorPolicy)</code>) –

####### `leadr.boards.api.board_schemas.BoardRatioConfigRequest.decimals`

```python
decimals: int = Field(default=2, description='Number of decimal places for display')
```

####### `leadr.boards.api.board_schemas.BoardRatioConfigRequest.denominator_board_id`

```python
denominator_board_id: BoardID = Field(description='ID of the denominator board')
```

####### `leadr.boards.api.board_schemas.BoardRatioConfigRequest.display`

```python
display: RatioDisplay = Field(default=(RatioDisplay.RAW), description='Display format for ratio values')
```

####### `leadr.boards.api.board_schemas.BoardRatioConfigRequest.min_denominator`

```python
min_denominator: float = Field(default=0, description='Minimum denominator value for ranking eligibility')
```

####### `leadr.boards.api.board_schemas.BoardRatioConfigRequest.min_numerator`

```python
min_numerator: float = Field(default=0, description='Minimum numerator value for ranking eligibility')
```

####### `leadr.boards.api.board_schemas.BoardRatioConfigRequest.numerator_board_id`

```python
numerator_board_id: BoardID = Field(description='ID of the numerator board')
```

####### `leadr.boards.api.board_schemas.BoardRatioConfigRequest.scale`

```python
scale: int = Field(default=1000000, description='Scaling factor for ratio storage precision')
```

####### `leadr.boards.api.board_schemas.BoardRatioConfigRequest.tie_breaker`

```python
tie_breaker: TieBreaker = Field(default=(TieBreaker.NUMERATOR_DESC_DENOMINATOR_ASC), description='Strategy for breaking ties')
```

####### `leadr.boards.api.board_schemas.BoardRatioConfigRequest.zero_denominator_policy`

```python
zero_denominator_policy: ZeroDenominatorPolicy = Field(default=(ZeroDenominatorPolicy.NULL), description='How to handle zero denominators')
```

###### `leadr.boards.api.board_schemas.BoardRatioConfigResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response model for ratio config.

**Functions:**

- [**from_domain**](#leadr.boards.api.board_schemas.BoardRatioConfigResponse.from_domain) – Convert domain entity to response model.

**Attributes:**

- [**created_at**](#leadr.boards.api.board_schemas.BoardRatioConfigResponse.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**decimals**](#leadr.boards.api.board_schemas.BoardRatioConfigResponse.decimals) (<code>[int](#int)</code>) –
- [**denominator_board_id**](#leadr.boards.api.board_schemas.BoardRatioConfigResponse.denominator_board_id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) –
- [**display**](#leadr.boards.api.board_schemas.BoardRatioConfigResponse.display) (<code>[RatioDisplay](#leadr.boards.domain.board_ratio_config.RatioDisplay)</code>) –
- [**id**](#leadr.boards.api.board_schemas.BoardRatioConfigResponse.id) (<code>[BoardRatioConfigID](./common.md#leadr.common.domain.ids.BoardRatioConfigID)</code>) –
- [**min_denominator**](#leadr.boards.api.board_schemas.BoardRatioConfigResponse.min_denominator) (<code>[float](#float)</code>) –
- [**min_numerator**](#leadr.boards.api.board_schemas.BoardRatioConfigResponse.min_numerator) (<code>[float](#float)</code>) –
- [**numerator_board_id**](#leadr.boards.api.board_schemas.BoardRatioConfigResponse.numerator_board_id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) –
- [**scale**](#leadr.boards.api.board_schemas.BoardRatioConfigResponse.scale) (<code>[int](#int)</code>) –
- [**tie_breaker**](#leadr.boards.api.board_schemas.BoardRatioConfigResponse.tie_breaker) (<code>[TieBreaker](#leadr.boards.domain.board_ratio_config.TieBreaker)</code>) –
- [**updated_at**](#leadr.boards.api.board_schemas.BoardRatioConfigResponse.updated_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**zero_denominator_policy**](#leadr.boards.api.board_schemas.BoardRatioConfigResponse.zero_denominator_policy) (<code>[ZeroDenominatorPolicy](#leadr.boards.domain.board_ratio_config.ZeroDenominatorPolicy)</code>) –

####### `leadr.boards.api.board_schemas.BoardRatioConfigResponse.created_at`

```python
created_at: datetime = Field(description='Timestamp when the config was created (UTC)')
```

####### `leadr.boards.api.board_schemas.BoardRatioConfigResponse.decimals`

```python
decimals: int = Field(description='Number of decimal places for display')
```

####### `leadr.boards.api.board_schemas.BoardRatioConfigResponse.denominator_board_id`

```python
denominator_board_id: BoardID = Field(description='ID of the denominator board')
```

####### `leadr.boards.api.board_schemas.BoardRatioConfigResponse.display`

```python
display: RatioDisplay = Field(description='Display format for ratio values')
```

####### `leadr.boards.api.board_schemas.BoardRatioConfigResponse.from_domain`

```python
from_domain(config)
```

Convert domain entity to response model.

####### `leadr.boards.api.board_schemas.BoardRatioConfigResponse.id`

```python
id: BoardRatioConfigID = Field(description='Unique identifier for the ratio config')
```

####### `leadr.boards.api.board_schemas.BoardRatioConfigResponse.min_denominator`

```python
min_denominator: float = Field(description='Minimum denominator for ranking eligibility')
```

####### `leadr.boards.api.board_schemas.BoardRatioConfigResponse.min_numerator`

```python
min_numerator: float = Field(description='Minimum numerator for ranking eligibility')
```

####### `leadr.boards.api.board_schemas.BoardRatioConfigResponse.numerator_board_id`

```python
numerator_board_id: BoardID = Field(description='ID of the numerator board')
```

####### `leadr.boards.api.board_schemas.BoardRatioConfigResponse.scale`

```python
scale: int = Field(description='Scaling factor for ratio storage')
```

####### `leadr.boards.api.board_schemas.BoardRatioConfigResponse.tie_breaker`

```python
tie_breaker: TieBreaker = Field(description='Strategy for breaking ties')
```

####### `leadr.boards.api.board_schemas.BoardRatioConfigResponse.updated_at`

```python
updated_at: datetime = Field(description='Timestamp of last update (UTC)')
```

####### `leadr.boards.api.board_schemas.BoardRatioConfigResponse.zero_denominator_policy`

```python
zero_denominator_policy: ZeroDenominatorPolicy = Field(description='How zero denominators are handled')
```

###### `leadr.boards.api.board_schemas.BoardResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response model for a board.

**Functions:**

- [**from_domain**](#leadr.boards.api.board_schemas.BoardResponse.from_domain) – Convert domain entity to response model.

**Attributes:**

- [**account_id**](#leadr.boards.api.board_schemas.BoardResponse.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**board_type**](#leadr.boards.api.board_schemas.BoardResponse.board_type) (<code>[BoardType](./boards.md#leadr.boards.domain.board.BoardType)</code>) –
- [**created_at**](#leadr.boards.api.board_schemas.BoardResponse.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**created_from_template_id**](#leadr.boards.api.board_schemas.BoardResponse.created_from_template_id) (<code>[BoardTemplateID](./common.md#leadr.common.domain.ids.BoardTemplateID) | None</code>) –
- [**description**](#leadr.boards.api.board_schemas.BoardResponse.description) (<code>[str](#str) | None</code>) –
- [**ends_at**](#leadr.boards.api.board_schemas.BoardResponse.ends_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**game_id**](#leadr.boards.api.board_schemas.BoardResponse.game_id) (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) –
- [**icon**](#leadr.boards.api.board_schemas.BoardResponse.icon) (<code>[str](#str) | None</code>) –
- [**id**](#leadr.boards.api.board_schemas.BoardResponse.id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) –
- [**is_active**](#leadr.boards.api.board_schemas.BoardResponse.is_active) (<code>[bool](#bool)</code>) –
- [**is_published**](#leadr.boards.api.board_schemas.BoardResponse.is_published) (<code>[bool](#bool)</code>) –
- [**keep_strategy**](#leadr.boards.api.board_schemas.BoardResponse.keep_strategy) (<code>[KeepStrategy](./boards.md#leadr.boards.domain.board.KeepStrategy)</code>) –
- [**name**](#leadr.boards.api.board_schemas.BoardResponse.name) (<code>[str](#str)</code>) –
- [**ratio_config**](#leadr.boards.api.board_schemas.BoardResponse.ratio_config) (<code>[BoardRatioConfigResponse](#leadr.boards.api.board_schemas.BoardRatioConfigResponse) | None</code>) –
- [**short_code**](#leadr.boards.api.board_schemas.BoardResponse.short_code) (<code>[str](#str)</code>) –
- [**slug**](#leadr.boards.api.board_schemas.BoardResponse.slug) (<code>[str](#str)</code>) –
- [**sort_direction**](#leadr.boards.api.board_schemas.BoardResponse.sort_direction) (<code>[SortDirection](./boards.md#leadr.boards.domain.board.SortDirection)</code>) –
- [**starts_at**](#leadr.boards.api.board_schemas.BoardResponse.starts_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**tags**](#leadr.boards.api.board_schemas.BoardResponse.tags) (<code>[list](#list)\[[str](#str)\]</code>) –
- [**template_name**](#leadr.boards.api.board_schemas.BoardResponse.template_name) (<code>[str](#str) | None</code>) –
- [**unit**](#leadr.boards.api.board_schemas.BoardResponse.unit) (<code>[str](#str) | None</code>) –
- [**updated_at**](#leadr.boards.api.board_schemas.BoardResponse.updated_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**url_short**](#leadr.boards.api.board_schemas.BoardResponse.url_short) (<code>[str](#str) | None</code>) – Short URL for direct board access via short_code.

####### `leadr.boards.api.board_schemas.BoardResponse.account_id`

```python
account_id: AccountID = Field(description='ID of the account this board belongs to')
```

####### `leadr.boards.api.board_schemas.BoardResponse.board_type`

```python
board_type: BoardType = Field(description='Type of board determining score behavior')
```

####### `leadr.boards.api.board_schemas.BoardResponse.created_at`

```python
created_at: datetime = Field(description='Timestamp when the board was created (UTC)')
```

####### `leadr.boards.api.board_schemas.BoardResponse.created_from_template_id`

```python
created_from_template_id: BoardTemplateID | None = Field(default=None, description='Template ID this board was created from, or null')
```

####### `leadr.boards.api.board_schemas.BoardResponse.description`

```python
description: str | None = Field(default=None, description='Short description of the board')
```

####### `leadr.boards.api.board_schemas.BoardResponse.ends_at`

```python
ends_at: datetime | None = Field(default=None, description='End time for time-bounded boards (UTC)')
```

####### `leadr.boards.api.board_schemas.BoardResponse.from_domain`

```python
from_domain(board, ratio_config=None)
```

Convert domain entity to response model.

**Parameters:**

- **board** (<code>[Board](./boards.md#leadr.boards.domain.board.Board)</code>) – The domain Board entity to convert.
- **ratio_config** (<code>[BoardRatioConfig](#leadr.boards.domain.board_ratio_config.BoardRatioConfig) | None</code>) – Optional ratio config for RATIO boards.

**Returns:**

- <code>[BoardResponse](#leadr.boards.api.board_schemas.BoardResponse)</code> – BoardResponse with all fields populated from the domain entity.

####### `leadr.boards.api.board_schemas.BoardResponse.game_id`

```python
game_id: GameID = Field(description='ID of the game this board belongs to')
```

####### `leadr.boards.api.board_schemas.BoardResponse.icon`

```python
icon: str | None = Field(description='Icon identifier for the board, or null')
```

####### `leadr.boards.api.board_schemas.BoardResponse.id`

```python
id: BoardID = Field(description='Unique identifier for the board')
```

####### `leadr.boards.api.board_schemas.BoardResponse.is_active`

```python
is_active: bool = Field(description='Whether the board is currently active')
```

####### `leadr.boards.api.board_schemas.BoardResponse.is_published`

```python
is_published: bool = Field(description='Whether the board is published and visible on public web views')
```

####### `leadr.boards.api.board_schemas.BoardResponse.keep_strategy`

```python
keep_strategy: KeepStrategy = Field(description='Strategy for keeping scores (RUN_IDENTITY only)')
```

####### `leadr.boards.api.board_schemas.BoardResponse.name`

```python
name: str = Field(description='Name of the board')
```

####### `leadr.boards.api.board_schemas.BoardResponse.ratio_config`

```python
ratio_config: BoardRatioConfigResponse | None = Field(default=None, description='Ratio config (present only for RATIO boards)')
```

####### `leadr.boards.api.board_schemas.BoardResponse.short_code`

```python
short_code: str = Field(description='Globally unique short code for direct sharing')
```

####### `leadr.boards.api.board_schemas.BoardResponse.slug`

```python
slug: str = Field(description='URL-friendly slug for the board (auto-generated, read-only)')
```

####### `leadr.boards.api.board_schemas.BoardResponse.sort_direction`

```python
sort_direction: SortDirection = Field(description='Direction to sort scores')
```

####### `leadr.boards.api.board_schemas.BoardResponse.starts_at`

```python
starts_at: datetime | None = Field(default=None, description='Start time for time-bounded boards (UTC)')
```

####### `leadr.boards.api.board_schemas.BoardResponse.tags`

```python
tags: list[str] = Field(default_factory=list, description='List of tags for categorization')
```

####### `leadr.boards.api.board_schemas.BoardResponse.template_name`

```python
template_name: str | None = Field(default=None, description='Template name this board was created from, or null')
```

####### `leadr.boards.api.board_schemas.BoardResponse.unit`

```python
unit: str | None = Field(description='Unit of measurement for scores, or null')
```

####### `leadr.boards.api.board_schemas.BoardResponse.updated_at`

```python
updated_at: datetime = Field(description='Timestamp of last update (UTC)')
```

####### `leadr.boards.api.board_schemas.BoardResponse.url_short`

```python
url_short: str | None
```

Short URL for direct board access via short_code.

Returns the URL if BOARDS_UI_DOMAIN is configured and the board is published,
otherwise None.

###### `leadr.boards.api.board_schemas.BoardUpdateRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request model for updating a board.

**Attributes:**

- [**board_type**](#leadr.boards.api.board_schemas.BoardUpdateRequest.board_type) (<code>[BoardType](./boards.md#leadr.boards.domain.board.BoardType) | None</code>) –
- [**created_from_template_id**](#leadr.boards.api.board_schemas.BoardUpdateRequest.created_from_template_id) (<code>[BoardTemplateID](./common.md#leadr.common.domain.ids.BoardTemplateID) | None</code>) –
- [**deleted**](#leadr.boards.api.board_schemas.BoardUpdateRequest.deleted) (<code>[bool](#bool) | None</code>) –
- [**description**](#leadr.boards.api.board_schemas.BoardUpdateRequest.description) (<code>[str](#str) | None</code>) –
- [**ends_at**](#leadr.boards.api.board_schemas.BoardUpdateRequest.ends_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**icon**](#leadr.boards.api.board_schemas.BoardUpdateRequest.icon) (<code>[str](#str) | None</code>) –
- [**is_active**](#leadr.boards.api.board_schemas.BoardUpdateRequest.is_active) (<code>[bool](#bool) | None</code>) –
- [**is_published**](#leadr.boards.api.board_schemas.BoardUpdateRequest.is_published) (<code>[bool](#bool) | None</code>) –
- [**keep_strategy**](#leadr.boards.api.board_schemas.BoardUpdateRequest.keep_strategy) (<code>[KeepStrategy](./boards.md#leadr.boards.domain.board.KeepStrategy) | None</code>) –
- [**name**](#leadr.boards.api.board_schemas.BoardUpdateRequest.name) (<code>[str](#str) | None</code>) –
- [**ratio_config**](#leadr.boards.api.board_schemas.BoardUpdateRequest.ratio_config) (<code>[BoardRatioConfigRequest](#leadr.boards.api.board_schemas.BoardRatioConfigRequest) | None</code>) –
- [**short_code**](#leadr.boards.api.board_schemas.BoardUpdateRequest.short_code) (<code>[str](#str) | None</code>) –
- [**sort_direction**](#leadr.boards.api.board_schemas.BoardUpdateRequest.sort_direction) (<code>[SortDirection](./boards.md#leadr.boards.domain.board.SortDirection) | None</code>) –
- [**starts_at**](#leadr.boards.api.board_schemas.BoardUpdateRequest.starts_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**tags**](#leadr.boards.api.board_schemas.BoardUpdateRequest.tags) (<code>[list](#list)\[[str](#str)\] | None</code>) –
- [**template_name**](#leadr.boards.api.board_schemas.BoardUpdateRequest.template_name) (<code>[str](#str) | None</code>) –
- [**unit**](#leadr.boards.api.board_schemas.BoardUpdateRequest.unit) (<code>[str](#str) | None</code>) –

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.board_type`

```python
board_type: BoardType | None = Field(default=None, description='Updated board type')
```

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.created_from_template_id`

```python
created_from_template_id: BoardTemplateID | None = Field(default=None, description='Updated template ID')
```

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.deleted`

```python
deleted: bool | None = Field(default=None, description='Set to true to soft delete the board')
```

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.description`

```python
description: str | None = Field(default=None, description='Updated board description')
```

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.ends_at`

```python
ends_at: datetime | None = Field(default=None, description='Updated end time')
```

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.icon`

```python
icon: str | None = Field(default=None, description='Updated icon identifier')
```

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.is_active`

```python
is_active: bool | None = Field(default=None, description='Updated active status')
```

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.is_published`

```python
is_published: bool | None = Field(default=None, description='Updated published status')
```

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.keep_strategy`

```python
keep_strategy: KeepStrategy | None = Field(default=None, description='Updated keep strategy')
```

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.name`

```python
name: str | None = Field(default=None, description='Updated board name')
```

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.ratio_config`

```python
ratio_config: BoardRatioConfigRequest | None = Field(default=None, description='Updated ratio config (for RATIO boards only)')
```

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.short_code`

```python
short_code: str | None = Field(default=None, description='Updated short code')
```

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.sort_direction`

```python
sort_direction: SortDirection | None = Field(default=None, description='Updated sort direction')
```

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.starts_at`

```python
starts_at: datetime | None = Field(default=None, description='Updated start time')
```

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.tags`

```python
tags: list[str] | None = Field(default=None, description='Updated tags list')
```

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.template_name`

```python
template_name: str | None = Field(default=None, description='Updated template name')
```

####### `leadr.boards.api.board_schemas.BoardUpdateRequest.unit`

```python
unit: str | None = Field(default=None, description='Updated unit of measurement')
```

##### `leadr.boards.api.board_state_routes`

API routes for board state management (admin only, read-only).

**Functions:**

- [**get_board_state**](#leadr.boards.api.board_state_routes.get_board_state) – Get a single board state by ID (Admin API).
- [**list_board_states**](#leadr.boards.api.board_state_routes.list_board_states) – List board states (Admin API).

**Attributes:**

- [**router**](#leadr.boards.api.board_state_routes.router) –

###### `leadr.boards.api.board_state_routes.get_board_state`

```python
get_board_state(state_id, auth, service)
```

Get a single board state by ID (Admin API).

**Parameters:**

- **state_id** (<code>[BoardStateID](./common.md#leadr.common.domain.ids.BoardStateID)</code>) – Board state ID.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Admin authentication context.
- **service** (<code>[BoardStateServiceDep](./boards.md#leadr.boards.services.dependencies.BoardStateServiceDep)</code>) – Injected board state service dependency.

**Returns:**

- <code>[BoardStateResponse](#leadr.boards.api.board_state_schemas.BoardStateResponse)</code> – Board state details.

**Raises:**

- <code>404</code> – Board state not found.

###### `leadr.boards.api.board_state_routes.list_board_states`

```python
list_board_states(auth, service, pagination, board_id=None, identity_id=None)
```

List board states (Admin API).

Returns a paginated list of board states. Board states are materialized
ranking states computed from score events.

**Parameters:**

- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Admin authentication context.
- **service** (<code>[BoardStateServiceDep](./boards.md#leadr.boards.services.dependencies.BoardStateServiceDep)</code>) – Injected board state service dependency.
- **pagination** (<code>[Annotated](#typing.Annotated)\[[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams), [Depends](#fastapi.Depends)()\]</code>) – Pagination parameters (cursor, limit, sort).
- **board_id** (<code>[Annotated](#typing.Annotated)\[[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None, [Query](#fastapi.Query)(description='Filter by board ID')\]</code>) – Optional filter by board ID.
- **identity_id** (<code>[Annotated](#typing.Annotated)\[[IdentityID](./common.md#leadr.common.domain.ids.IdentityID) | None, [Query](#fastapi.Query)(description='Filter by identity ID')\]</code>) – Optional filter by identity ID.

**Returns:**

- <code>[PaginatedResponse](./common.md#leadr.common.api.pagination.PaginatedResponse)\[[BoardStateResponse](#leadr.boards.api.board_state_schemas.BoardStateResponse)\]</code> – Paginated list of board states.

**Raises:**

- <code>400</code> – Invalid pagination cursor.

###### `leadr.boards.api.board_state_routes.router`

```python
router = APIRouter()
```

##### `leadr.boards.api.board_state_schemas`

API response models for board states.

**Classes:**

- [**BoardStateResponse**](#leadr.boards.api.board_state_schemas.BoardStateResponse) – Response model for a board state (admin only).

###### `leadr.boards.api.board_state_schemas.BoardStateResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response model for a board state (admin only).

Board states represent the materialized ranking state for an identity on a board.
They are computed from score events and used for leaderboard queries.

**Functions:**

- [**from_domain**](#leadr.boards.api.board_state_schemas.BoardStateResponse.from_domain) – Convert domain entity to response model.

**Attributes:**

- [**aux**](#leadr.boards.api.board_state_schemas.BoardStateResponse.aux) (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\] | None</code>) –
- [**board_id**](#leadr.boards.api.board_state_schemas.BoardStateResponse.board_id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) –
- [**created_at**](#leadr.boards.api.board_state_schemas.BoardStateResponse.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**id**](#leadr.boards.api.board_state_schemas.BoardStateResponse.id) (<code>[BoardStateID](./common.md#leadr.common.domain.ids.BoardStateID)</code>) –
- [**identity_id**](#leadr.boards.api.board_state_schemas.BoardStateResponse.identity_id) (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) –
- [**primary_value**](#leadr.boards.api.board_state_schemas.BoardStateResponse.primary_value) (<code>[float](#float) | None</code>) –
- [**updated_at**](#leadr.boards.api.board_state_schemas.BoardStateResponse.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.boards.api.board_state_schemas.BoardStateResponse.aux`

```python
aux: dict[str, Any] | None = Field(default=None, description='Board-type-specific auxiliary data')
```

####### `leadr.boards.api.board_state_schemas.BoardStateResponse.board_id`

```python
board_id: BoardID = Field(description='ID of the board this state belongs to')
```

####### `leadr.boards.api.board_state_schemas.BoardStateResponse.created_at`

```python
created_at: datetime = Field(description='Timestamp when the state was created (UTC)')
```

####### `leadr.boards.api.board_state_schemas.BoardStateResponse.from_domain`

```python
from_domain(state)
```

Convert domain entity to response model.

**Parameters:**

- **state** (<code>[BoardState](#leadr.boards.domain.board_state.BoardState)</code>) – The domain BoardState entity to convert.

**Returns:**

- <code>[BoardStateResponse](#leadr.boards.api.board_state_schemas.BoardStateResponse)</code> – BoardStateResponse with all fields populated from the domain entity.

####### `leadr.boards.api.board_state_schemas.BoardStateResponse.id`

```python
id: BoardStateID = Field(description='Unique identifier for the board state')
```

####### `leadr.boards.api.board_state_schemas.BoardStateResponse.identity_id`

```python
identity_id: IdentityID = Field(description='ID of the identity this state is for')
```

####### `leadr.boards.api.board_state_schemas.BoardStateResponse.primary_value`

```python
primary_value: float | None = Field(default=None, description='Rankable value (null if not rankable)')
```

####### `leadr.boards.api.board_state_schemas.BoardStateResponse.updated_at`

```python
updated_at: datetime = Field(description='Timestamp when the state was last updated (UTC)')
```

##### `leadr.boards.api.board_template_routes`

Board template API routes.

**Functions:**

- [**create_board_template**](#leadr.boards.api.board_template_routes.create_board_template) – Create a new board template.
- [**get_board_template**](#leadr.boards.api.board_template_routes.get_board_template) – Get a board template by ID.
- [**list_board_templates**](#leadr.boards.api.board_template_routes.list_board_templates) – List board templates for an account with pagination, optionally filtered by game.
- [**update_board_template**](#leadr.boards.api.board_template_routes.update_board_template) – Update a board template.

**Attributes:**

- [**router**](#leadr.boards.api.board_template_routes.router) –

###### `leadr.boards.api.board_template_routes.create_board_template`

```python
create_board_template(request, service, auth, background_tasks, pre_hook)
```

Create a new board template.

Creates a template for automatically generating boards at regular intervals.
The game must belong to the specified account.

For regular users, account_id must match their API key's account.
For superadmins, any account_id is accepted.

**Parameters:**

- **request** (<code>[BoardTemplateCreateRequest](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest)</code>) – Template creation details including repeat_interval and configuration.
- **service** (<code>[BoardTemplateServiceDep](./boards.md#leadr.boards.services.dependencies.BoardTemplateServiceDep)</code>) – Injected board template service dependency.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.
- **pre_hook** (<code>[PreCreateBoardTemplateHookDep](./common.md#leadr.common.api.hooks.PreCreateBoardTemplateHookDep)</code>) – Pre-create hook for entitlement checks.

**Returns:**

- <code>[BoardTemplateResponse](#leadr.boards.api.board_template_schemas.BoardTemplateResponse)</code> – BoardTemplateResponse with the created template including auto-generated ID.

**Raises:**

- <code>403</code> – User does not have access to the specified account, or repeat_interval not allowed.
- <code>404</code> – Game or account not found.
- <code>400</code> – Game doesn't belong to the specified account.

###### `leadr.boards.api.board_template_routes.get_board_template`

```python
get_board_template(template_id, service, auth)
```

Get a board template by ID.

**Parameters:**

- **template_id** (<code>[BoardTemplateID](./common.md#leadr.common.domain.ids.BoardTemplateID)</code>) – Unique identifier for the template.
- **service** (<code>[BoardTemplateServiceDep](./boards.md#leadr.boards.services.dependencies.BoardTemplateServiceDep)</code>) – Injected board template service dependency.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.

**Returns:**

- <code>[BoardTemplateResponse](#leadr.boards.api.board_template_schemas.BoardTemplateResponse)</code> – BoardTemplateResponse with full template details.

**Raises:**

- <code>403</code> – User does not have access to this template's account.
- <code>404</code> – Template not found.

###### `leadr.boards.api.board_template_routes.list_board_templates`

```python
list_board_templates(auth, service, pagination, account_id=None, game_id=None)
```

List board templates for an account with pagination, optionally filtered by game.

For regular users, account_id is automatically derived from their API key.
For superadmins, account_id is optional - if omitted, returns templates from all accounts.

Pagination:

- Default: 20 items per page, sorted by created_at:desc,id:asc
- Custom sort: Use ?sort=name:asc,created_at:desc
- Valid sort fields: id, name, created_at, updated_at
- Navigation: Use next_cursor/prev_cursor from response

<details class="example" open markdown="1">
<summary>Example</summary>

GET /v1/board-templates?account_id=acc_123&game_id=gam_456&limit=50&sort=name:asc

</details>

**Parameters:**

- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.
- **service** (<code>[BoardTemplateServiceDep](./boards.md#leadr.boards.services.dependencies.BoardTemplateServiceDep)</code>) – Injected board template service dependency.
- **pagination** (<code>[Annotated](#typing.Annotated)\[[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams), [Depends](#fastapi.Depends)()\]</code>) – Pagination parameters (cursor, limit, sort).
- **account_id** (<code>[Annotated](#typing.Annotated)\[[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None, [Query](#fastapi.Query)(description='Account ID filter')\]</code>) – Optional account_id query parameter (superadmins can omit to see all).
- **game_id** (<code>[Annotated](#typing.Annotated)\[[GameID](./common.md#leadr.common.domain.ids.GameID) | None, [Query](#fastapi.Query)(description='Filter by game ID')\]</code>) – Optional game ID to filter templates by.

**Returns:**

- <code>[PaginatedResponse](./common.md#leadr.common.api.pagination.PaginatedResponse)\[[BoardTemplateResponse](#leadr.boards.api.board_template_schemas.BoardTemplateResponse)\]</code> – PaginatedResponse with board templates and pagination metadata.

**Raises:**

- <code>400</code> – Invalid cursor, sort field, or cursor state mismatch.
- <code>403</code> – User does not have access to the specified account.

###### `leadr.boards.api.board_template_routes.router`

```python
router = APIRouter()
```

###### `leadr.boards.api.board_template_routes.update_board_template`

```python
update_board_template(template_id, request, service, auth, background_tasks, pre_hook)
```

Update a board template.

Supports updating any template field or soft-deleting the template.

**Parameters:**

- **template_id** (<code>[BoardTemplateID](./common.md#leadr.common.domain.ids.BoardTemplateID)</code>) – Unique identifier for the template.
- **request** (<code>[BoardTemplateUpdateRequest](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest)</code>) – Template update details (all fields optional).
- **service** (<code>[BoardTemplateServiceDep](./boards.md#leadr.boards.services.dependencies.BoardTemplateServiceDep)</code>) – Injected board template service dependency.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Authentication context with user info.
- **pre_hook** (<code>[PreUpdateBoardTemplateHookDep](./common.md#leadr.common.api.hooks.PreUpdateBoardTemplateHookDep)</code>) – Pre-update hook for entitlement checks.

**Returns:**

- <code>[BoardTemplateResponse](#leadr.boards.api.board_template_schemas.BoardTemplateResponse)</code> – BoardTemplateResponse with the updated template details.

**Raises:**

- <code>403</code> – User does not have access to this template's account, or repeat_interval not allowed.
- <code>404</code> – Template not found.

##### `leadr.boards.api.board_template_schemas`

API request and response models for board templates.

**Classes:**

- [**BoardTemplateCreateRequest**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest) – Request model for creating a board template.
- [**BoardTemplateResponse**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse) – Response model for a board template.
- [**BoardTemplateUpdateRequest**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest) – Request model for updating a board template.

###### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request model for creating a board template.

**Attributes:**

- [**account_id**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**config**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.config) (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\] | None</code>) –
- [**ends_at**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.ends_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**game_id**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.game_id) (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) –
- [**icon**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.icon) (<code>[str](#str) | None</code>) –
- [**is_active**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.is_active) (<code>[bool](#bool)</code>) –
- [**is_published**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.is_published) (<code>[bool](#bool)</code>) –
- [**keep_strategy**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.keep_strategy) (<code>[KeepStrategy](./boards.md#leadr.boards.domain.board.KeepStrategy)</code>) –
- [**name**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.name) (<code>[str](#str)</code>) –
- [**name_template**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.name_template) (<code>[str](#str) | None</code>) –
- [**next_run_at**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.next_run_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**repeat_interval**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.repeat_interval) (<code>[str](#str)</code>) –
- [**series**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.series) (<code>[str](#str) | None</code>) –
- [**slug**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.slug) (<code>[str](#str) | None</code>) –
- [**sort_direction**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.sort_direction) (<code>[SortDirection](./boards.md#leadr.boards.domain.board.SortDirection)</code>) –
- [**starts_at**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.starts_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**tags**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.tags) (<code>[list](#list)\[[str](#str)\] | None</code>) –
- [**unit**](#leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.unit) (<code>[str](#str) | None</code>) –

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.account_id`

```python
account_id: AccountID = Field(description='ID of the account this template belongs to')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.config`

```python
config: dict[str, Any] | None = Field(default=None, description='Reserved for future procedural generation (bounds, variables, randomization rules)')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.ends_at`

```python
ends_at: datetime | None = Field(default=None, description='Optional end time for time-bounded boards')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.game_id`

```python
game_id: GameID = Field(description='ID of the game this template belongs to')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.icon`

```python
icon: str | None = Field(default='fa-crown', description='Icon identifier for boards created from this template')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.is_active`

```python
is_active: bool = Field(description='Whether the template is currently active')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.is_published`

```python
is_published: bool = Field(default=True, description='Whether boards created from this template should be published')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.keep_strategy`

```python
keep_strategy: KeepStrategy = Field(default=(KeepStrategy.BEST), description='Strategy for keeping multiple scores from the same user')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.name`

```python
name: str = Field(description='Name of the template')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.name_template`

```python
name_template: str | None = Field(default=None, description='Optional template string for generating board names')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.next_run_at`

```python
next_run_at: datetime = Field(description='Next scheduled time to create a board from this template (UTC)')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.repeat_interval`

```python
repeat_interval: str = Field(description="PostgreSQL interval syntax for repeat frequency (e.g., '7 days', '1 month')")
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.series`

```python
series: str | None = Field(default=None, description='Optional series identifier for sequential board naming')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.slug`

```python
slug: str | None = Field(default=None, description='URL-friendly slug for boards created from this template')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.sort_direction`

```python
sort_direction: SortDirection = Field(default=(SortDirection.DESCENDING), description='Direction to sort scores (ascending/descending)')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.starts_at`

```python
starts_at: datetime | None = Field(default=None, description='Optional start time for time-bounded boards')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.tags`

```python
tags: list[str] | None = Field(default=None, description='List of tags for categorizing boards created from this template')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateCreateRequest.unit`

```python
unit: str | None = Field(default=None, description="Unit of measurement for scores (e.g., 'seconds', 'points')")
```

###### `leadr.boards.api.board_template_schemas.BoardTemplateResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response model for a board template.

**Functions:**

- [**from_domain**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.from_domain) – Convert domain entity to response model.

**Attributes:**

- [**account_id**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**config**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.config) (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\]</code>) –
- [**created_at**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**ends_at**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.ends_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**game_id**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.game_id) (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) –
- [**icon**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.icon) (<code>[str](#str) | None</code>) –
- [**id**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.id) (<code>[BoardTemplateID](./common.md#leadr.common.domain.ids.BoardTemplateID)</code>) –
- [**is_active**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.is_active) (<code>[bool](#bool)</code>) –
- [**is_published**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.is_published) (<code>[bool](#bool)</code>) –
- [**keep_strategy**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.keep_strategy) (<code>[KeepStrategy](./boards.md#leadr.boards.domain.board.KeepStrategy)</code>) –
- [**name**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.name) (<code>[str](#str)</code>) –
- [**name_template**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.name_template) (<code>[str](#str) | None</code>) –
- [**next_run_at**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.next_run_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**repeat_interval**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.repeat_interval) (<code>[str](#str)</code>) –
- [**series**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.series) (<code>[str](#str) | None</code>) –
- [**slug**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.slug) (<code>[str](#str) | None</code>) –
- [**sort_direction**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.sort_direction) (<code>[SortDirection](./boards.md#leadr.boards.domain.board.SortDirection)</code>) –
- [**starts_at**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.starts_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**tags**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.tags) (<code>[list](#list)\[[str](#str)\]</code>) –
- [**unit**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.unit) (<code>[str](#str) | None</code>) –
- [**updated_at**](#leadr.boards.api.board_template_schemas.BoardTemplateResponse.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.account_id`

```python
account_id: AccountID = Field(description='ID of the account this template belongs to')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.config`

```python
config: dict[str, Any] = Field(default_factory=dict, description='Reserved for future procedural generation (bounds, variables, randomization rules)')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.created_at`

```python
created_at: datetime = Field(description='Timestamp when the template was created (UTC)')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.ends_at`

```python
ends_at: datetime | None = Field(description='Optional end time for time-bounded boards')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.from_domain`

```python
from_domain(template)
```

Convert domain entity to response model.

**Parameters:**

- **template** (<code>[BoardTemplate](#leadr.boards.domain.board_template.BoardTemplate)</code>) – The domain BoardTemplate entity to convert.

**Returns:**

- <code>[BoardTemplateResponse](#leadr.boards.api.board_template_schemas.BoardTemplateResponse)</code> – BoardTemplateResponse with all fields populated from the domain entity.

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.game_id`

```python
game_id: GameID = Field(description='ID of the game this template belongs to')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.icon`

```python
icon: str | None = Field(description='Icon identifier for boards created from this template')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.id`

```python
id: BoardTemplateID = Field(description='Unique identifier for the template')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.is_active`

```python
is_active: bool = Field(description='Whether the template is currently active')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.is_published`

```python
is_published: bool = Field(description='Whether boards created from this template should be published')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.keep_strategy`

```python
keep_strategy: KeepStrategy = Field(description='Strategy for keeping multiple scores from the same user')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.name`

```python
name: str = Field(description='Name of the template')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.name_template`

```python
name_template: str | None = Field(default=None, description='Template string for generating board names, or null')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.next_run_at`

```python
next_run_at: datetime = Field(description='Next scheduled run time (UTC)')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.repeat_interval`

```python
repeat_interval: str = Field(description='Repeat frequency in PostgreSQL interval syntax')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.series`

```python
series: str | None = Field(default=None, description='Series identifier for sequential board naming, or null')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.slug`

```python
slug: str | None = Field(description='URL-friendly slug for boards created from this template, or null')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.sort_direction`

```python
sort_direction: SortDirection = Field(description='Direction to sort scores (ascending/descending)')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.starts_at`

```python
starts_at: datetime | None = Field(description='Optional start time for time-bounded boards')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.tags`

```python
tags: list[str] = Field(description='List of tags for categorizing boards created from this template')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.unit`

```python
unit: str | None = Field(description="Unit of measurement for scores (e.g., 'seconds', 'points')")
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateResponse.updated_at`

```python
updated_at: datetime = Field(description='Timestamp of last update (UTC)')
```

###### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request model for updating a board template.

**Attributes:**

- [**config**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.config) (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\] | None</code>) –
- [**deleted**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.deleted) (<code>[bool](#bool) | None</code>) –
- [**ends_at**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.ends_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**icon**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.icon) (<code>[str](#str) | None</code>) –
- [**is_active**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.is_active) (<code>[bool](#bool) | None</code>) –
- [**is_published**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.is_published) (<code>[bool](#bool) | None</code>) –
- [**keep_strategy**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.keep_strategy) (<code>[KeepStrategy](./boards.md#leadr.boards.domain.board.KeepStrategy) | None</code>) –
- [**name**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.name) (<code>[str](#str) | None</code>) –
- [**name_template**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.name_template) (<code>[str](#str) | None</code>) –
- [**next_run_at**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.next_run_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**repeat_interval**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.repeat_interval) (<code>[str](#str) | None</code>) –
- [**series**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.series) (<code>[str](#str) | None</code>) –
- [**slug**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.slug) (<code>[str](#str) | None</code>) –
- [**sort_direction**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.sort_direction) (<code>[SortDirection](./boards.md#leadr.boards.domain.board.SortDirection) | None</code>) –
- [**starts_at**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.starts_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**tags**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.tags) (<code>[list](#list)\[[str](#str)\] | None</code>) –
- [**unit**](#leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.unit) (<code>[str](#str) | None</code>) –

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.config`

```python
config: dict[str, Any] | None = Field(default=None, description='Updated config (reserved for procedural generation)')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.deleted`

```python
deleted: bool | None = Field(default=None, description='Set to true to soft delete the template')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.ends_at`

```python
ends_at: datetime | None = Field(default=None, description='Updated end time')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.icon`

```python
icon: str | None = Field(default=None, description='Updated icon identifier')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.is_active`

```python
is_active: bool | None = Field(default=None, description='Updated active status')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.is_published`

```python
is_published: bool | None = Field(default=None, description='Updated published status')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.keep_strategy`

```python
keep_strategy: KeepStrategy | None = Field(default=None, description='Updated keep strategy')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.name`

```python
name: str | None = Field(default=None, description='Updated template name')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.name_template`

```python
name_template: str | None = Field(default=None, description='Updated name template')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.next_run_at`

```python
next_run_at: datetime | None = Field(default=None, description='Updated next run time')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.repeat_interval`

```python
repeat_interval: str | None = Field(default=None, description='Updated repeat interval')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.series`

```python
series: str | None = Field(default=None, description='Updated series identifier')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.slug`

```python
slug: str | None = Field(default=None, description='Updated slug')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.sort_direction`

```python
sort_direction: SortDirection | None = Field(default=None, description='Updated sort direction')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.starts_at`

```python
starts_at: datetime | None = Field(default=None, description='Updated start time')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.tags`

```python
tags: list[str] | None = Field(default=None, description='Updated tags list')
```

####### `leadr.boards.api.board_template_schemas.BoardTemplateUpdateRequest.unit`

```python
unit: str | None = Field(default=None, description='Updated unit of measurement')
```

##### `leadr.boards.api.run_entry_routes`

API routes for run entry management (admin only, read-only).

**Functions:**

- [**get_run_entry**](#leadr.boards.api.run_entry_routes.get_run_entry) – Get a single run entry by ID (Admin API).
- [**list_run_entries**](#leadr.boards.api.run_entry_routes.list_run_entries) – List run entries (Admin API).

**Attributes:**

- [**router**](#leadr.boards.api.run_entry_routes.router) –

###### `leadr.boards.api.run_entry_routes.get_run_entry`

```python
get_run_entry(entry_id, auth, service)
```

Get a single run entry by ID (Admin API).

**Parameters:**

- **entry_id** (<code>[RunEntryID](./common.md#leadr.common.domain.ids.RunEntryID)</code>) – Run entry ID.
- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Admin authentication context.
- **service** (<code>[RunEntryServiceDep](./boards.md#leadr.boards.services.dependencies.RunEntryServiceDep)</code>) – Injected run entry service dependency.

**Returns:**

- <code>[RunEntryResponse](#leadr.boards.api.run_entry_schemas.RunEntryResponse)</code> – Run entry details.

**Raises:**

- <code>404</code> – Run entry not found.

###### `leadr.boards.api.run_entry_routes.list_run_entries`

```python
list_run_entries(auth, service, pagination, board_id=None, identity_id=None)
```

List run entries (Admin API).

Returns a paginated list of run entries. Run entries are individual scored
submissions for RUN_RUNS boards where every submission is ranked.

**Parameters:**

- **auth** (<code>[AdminAuthContextDep](./auth.md#leadr.auth.dependencies.AdminAuthContextDep)</code>) – Admin authentication context.
- **service** (<code>[RunEntryServiceDep](./boards.md#leadr.boards.services.dependencies.RunEntryServiceDep)</code>) – Injected run entry service dependency.
- **pagination** (<code>[Annotated](#typing.Annotated)\[[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams), [Depends](#fastapi.Depends)()\]</code>) – Pagination parameters (cursor, limit, sort).
- **board_id** (<code>[Annotated](#typing.Annotated)\[[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None, [Query](#fastapi.Query)(description='Filter by board ID')\]</code>) – Optional filter by board ID.
- **identity_id** (<code>[Annotated](#typing.Annotated)\[[IdentityID](./common.md#leadr.common.domain.ids.IdentityID) | None, [Query](#fastapi.Query)(description='Filter by identity ID')\]</code>) – Optional filter by identity ID.

**Returns:**

- <code>[PaginatedResponse](./common.md#leadr.common.api.pagination.PaginatedResponse)\[[RunEntryResponse](#leadr.boards.api.run_entry_schemas.RunEntryResponse)\]</code> – Paginated list of run entries.

**Raises:**

- <code>400</code> – Invalid pagination cursor.

###### `leadr.boards.api.run_entry_routes.router`

```python
router = APIRouter()
```

##### `leadr.boards.api.run_entry_schemas`

API response models for run entries.

**Classes:**

- [**RunEntryResponse**](#leadr.boards.api.run_entry_schemas.RunEntryResponse) – Response model for a run entry (admin only).

###### `leadr.boards.api.run_entry_schemas.RunEntryResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response model for a run entry (admin only).

Run entries represent individual scored submissions for RUN_RUNS boards
where every submission is ranked.

**Functions:**

- [**from_domain**](#leadr.boards.api.run_entry_schemas.RunEntryResponse.from_domain) – Convert domain entity to response model.

**Attributes:**

- [**board_id**](#leadr.boards.api.run_entry_schemas.RunEntryResponse.board_id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) –
- [**created_at**](#leadr.boards.api.run_entry_schemas.RunEntryResponse.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**id**](#leadr.boards.api.run_entry_schemas.RunEntryResponse.id) (<code>[RunEntryID](./common.md#leadr.common.domain.ids.RunEntryID)</code>) –
- [**identity_id**](#leadr.boards.api.run_entry_schemas.RunEntryResponse.identity_id) (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) –
- [**primary_value**](#leadr.boards.api.run_entry_schemas.RunEntryResponse.primary_value) (<code>[float](#float)</code>) –
- [**score_event_id**](#leadr.boards.api.run_entry_schemas.RunEntryResponse.score_event_id) (<code>[ScoreEventID](./common.md#leadr.common.domain.ids.ScoreEventID)</code>) –
- [**updated_at**](#leadr.boards.api.run_entry_schemas.RunEntryResponse.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.boards.api.run_entry_schemas.RunEntryResponse.board_id`

```python
board_id: BoardID = Field(description='ID of the board this entry belongs to')
```

####### `leadr.boards.api.run_entry_schemas.RunEntryResponse.created_at`

```python
created_at: datetime = Field(description='Timestamp when the entry was created (UTC)')
```

####### `leadr.boards.api.run_entry_schemas.RunEntryResponse.from_domain`

```python
from_domain(entry)
```

Convert domain entity to response model.

**Parameters:**

- **entry** (<code>[RunEntry](#leadr.boards.domain.run_entry.RunEntry)</code>) – The domain RunEntry entity to convert.

**Returns:**

- <code>[RunEntryResponse](#leadr.boards.api.run_entry_schemas.RunEntryResponse)</code> – RunEntryResponse with all fields populated from the domain entity.

####### `leadr.boards.api.run_entry_schemas.RunEntryResponse.id`

```python
id: RunEntryID = Field(description='Unique identifier for the run entry')
```

####### `leadr.boards.api.run_entry_schemas.RunEntryResponse.identity_id`

```python
identity_id: IdentityID = Field(description='ID of the identity that submitted this entry')
```

####### `leadr.boards.api.run_entry_schemas.RunEntryResponse.primary_value`

```python
primary_value: float = Field(description='Rankable value for this submission')
```

####### `leadr.boards.api.run_entry_schemas.RunEntryResponse.score_event_id`

```python
score_event_id: ScoreEventID = Field(description='ID of the score event that created this entry')
```

####### `leadr.boards.api.run_entry_schemas.RunEntryResponse.updated_at`

```python
updated_at: datetime = Field(description='Timestamp when the entry was last updated (UTC)')
```

#### `leadr.boards.domain`

**Modules:**

- [**board**](./boards.md#leadr.boards.domain.board) – Board domain model.
- [**board_ratio_config**](#leadr.boards.domain.board_ratio_config) – Board ratio config domain model.
- [**board_state**](#leadr.boards.domain.board_state) – BoardState domain model for materialized ranking state.
- [**board_template**](#leadr.boards.domain.board_template) – BoardTemplate domain model.
- [**interval_parser**](#leadr.boards.domain.interval_parser) – Utilities for parsing PostgreSQL interval syntax.
- [**run_entry**](#leadr.boards.domain.run_entry) – RunEntry domain model for RUN_RUNS boards.

##### `leadr.boards.domain.board`

Board domain model.

**Classes:**

- [**Board**](./boards.md#leadr.boards.domain.board.Board) – Board domain entity.
- [**BoardType**](./boards.md#leadr.boards.domain.board.BoardType) – Type of board determining score behavior.
- [**KeepStrategy**](./boards.md#leadr.boards.domain.board.KeepStrategy) – Strategy for keeping scores from the same user (RUN_IDENTITY boards only).
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
- [**validate_board_type_keep_strategy**](#leadr.boards.domain.board.Board.validate_board_type_keep_strategy) – Validate board_type and keep_strategy combination.
- [**validate_name**](#leadr.boards.domain.board.Board.validate_name) – Validate board name is not empty.
- [**validate_short_code**](#leadr.boards.domain.board.Board.validate_short_code) – Validate short_code is not empty.
- [**validate_slug**](#leadr.boards.domain.board.Board.validate_slug) – Validate slug format (lowercase alphanumeric with hyphens).

**Attributes:**

- [**account_id**](#leadr.boards.domain.board.Board.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**board_type**](#leadr.boards.domain.board.Board.board_type) (<code>[BoardType](./boards.md#leadr.boards.domain.board.BoardType)</code>) –
- [**created_at**](#leadr.boards.domain.board.Board.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**created_from_template_id**](#leadr.boards.domain.board.Board.created_from_template_id) (<code>[BoardTemplateID](./common.md#leadr.common.domain.ids.BoardTemplateID) | None</code>) –
- [**deleted_at**](#leadr.boards.domain.board.Board.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**description**](./boards.md#leadr.boards.domain.board.Board.description) (<code>[str](#str) | None</code>) –
- [**ends_at**](#leadr.boards.domain.board.Board.ends_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**game_id**](#leadr.boards.domain.board.Board.game_id) (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) –
- [**icon**](./boards.md#leadr.boards.domain.board.Board.icon) (<code>[str](#str) | None</code>) –
- [**id**](./boards.md#leadr.boards.domain.board.Board.id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) –
- [**is_active**](#leadr.boards.domain.board.Board.is_active) (<code>[bool](#bool)</code>) –
- [**is_deleted**](#leadr.boards.domain.board.Board.is_deleted) (<code>[bool](#bool)</code>) – Check if entity is soft-deleted.
- [**is_published**](#leadr.boards.domain.board.Board.is_published) (<code>[bool](#bool)</code>) –
- [**keep_strategy**](#leadr.boards.domain.board.Board.keep_strategy) (<code>[KeepStrategy](./boards.md#leadr.boards.domain.board.KeepStrategy)</code>) –
- [**model_config**](#leadr.boards.domain.board.Board.model_config) –
- [**name**](./boards.md#leadr.boards.domain.board.Board.name) (<code>[str](#str)</code>) –
- [**short_code**](#leadr.boards.domain.board.Board.short_code) (<code>[str](#str)</code>) –
- [**slug**](./boards.md#leadr.boards.domain.board.Board.slug) (<code>[str](#str)</code>) –
- [**sort_direction**](#leadr.boards.domain.board.Board.sort_direction) (<code>[SortDirection](./boards.md#leadr.boards.domain.board.SortDirection)</code>) –
- [**starts_at**](#leadr.boards.domain.board.Board.starts_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**tags**](./boards.md#leadr.boards.domain.board.Board.tags) (<code>[list](#list)\[[str](#str)\]</code>) –
- [**template_name**](#leadr.boards.domain.board.Board.template_name) (<code>[str](#str) | None</code>) –
- [**unit**](./boards.md#leadr.boards.domain.board.Board.unit) (<code>[str](#str) | None</code>) –
- [**updated_at**](#leadr.boards.domain.board.Board.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.boards.domain.board.Board.account_id`

```python
account_id: AccountID = Field(frozen=True, description='ID of the account this board belongs to (immutable)')
```

####### `leadr.boards.domain.board.Board.board_type`

```python
board_type: BoardType = Field(description='Type of board determining score behavior', default=(BoardType.RUN_IDENTITY))
```

####### `leadr.boards.domain.board.Board.created_at`

```python
created_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp when entity was created (UTC)')
```

####### `leadr.boards.domain.board.Board.created_from_template_id`

```python
created_from_template_id: BoardTemplateID | None = Field(default=None, description='Optional template ID this board was created from')
```

####### `leadr.boards.domain.board.Board.deleted_at`

```python
deleted_at: datetime | None = Field(default=None, description='Timestamp when entity was soft-deleted (UTC), or null if active')
```

####### `leadr.boards.domain.board.Board.description`

```python
description: str | None = Field(default=None, description='Short description of the board')
```

####### `leadr.boards.domain.board.Board.ends_at`

```python
ends_at: datetime | None = Field(default=None, description='Optional end time for time-bounded boards')
```

####### `leadr.boards.domain.board.Board.game_id`

```python
game_id: GameID = Field(frozen=True, description='ID of the game this board belongs to (immutable)')
```

####### `leadr.boards.domain.board.Board.icon`

```python
icon: str | None = Field(description='Icon identifier for the board', default='fa-crown')
```

####### `leadr.boards.domain.board.Board.id`

```python
id: BoardID = Field(frozen=True, default_factory=BoardID, description='Unique board identifier')
```

####### `leadr.boards.domain.board.Board.is_active`

```python
is_active: bool = Field(description='Whether the board is currently active', default=True)
```

####### `leadr.boards.domain.board.Board.is_deleted`

```python
is_deleted: bool
```

Check if entity is soft-deleted.

**Returns:**

- <code>[bool](#bool)</code> – True if the entity has a deleted_at timestamp, False otherwise.

####### `leadr.boards.domain.board.Board.is_published`

```python
is_published: bool = Field(description='Whether the board is published and visible on public web views', default=True)
```

####### `leadr.boards.domain.board.Board.keep_strategy`

```python
keep_strategy: KeepStrategy = Field(description='Strategy for keeping multiple scores from the same user (RUN_IDENTITY only)', default=(KeepStrategy.BEST))
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

####### `leadr.boards.domain.board.Board.slug`

```python
slug: str = Field(description='URL-friendly slug for the board (unique per game when active)')
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
sort_direction: SortDirection = Field(description='Direction to sort scores (ascending/descending)', default=(SortDirection.DESCENDING))
```

####### `leadr.boards.domain.board.Board.starts_at`

```python
starts_at: datetime | None = Field(default=None, description='Optional start time for time-bounded boards')
```

####### `leadr.boards.domain.board.Board.tags`

```python
tags: list[str] = Field(default_factory=list, description='List of tags for categorizing the board')
```

####### `leadr.boards.domain.board.Board.template_name`

```python
template_name: str | None = Field(default=None, description='Optional name of the template this board was created from')
```

####### `leadr.boards.domain.board.Board.unit`

```python
unit: str | None = Field(description="Unit of measurement for scores (e.g., 'seconds', 'points')", default=None)
```

####### `leadr.boards.domain.board.Board.updated_at`

```python
updated_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp of last update (UTC)')
```

####### `leadr.boards.domain.board.Board.validate_board_type_keep_strategy`

```python
validate_board_type_keep_strategy()
```

Validate board_type and keep_strategy combination.

- RUN_IDENTITY boards must have a non-NA keep_strategy (FIRST, BEST, LATEST)
- Non-RUN_IDENTITY boards (RUN_RUNS, COUNTER, RATIO) must have NA keep_strategy

**Returns:**

- <code>[Board](./boards.md#leadr.boards.domain.board.Board)</code> – The validated Board instance.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If the board_type/keep_strategy combination is invalid.

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

####### `leadr.boards.domain.board.Board.validate_slug`

```python
validate_slug(value)
```

Validate slug format (lowercase alphanumeric with hyphens).

**Parameters:**

- **value** (<code>[str](#str)</code>) – The slug to validate.

**Returns:**

- <code>[str](#str)</code> – The validated slug.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If slug is invalid.

###### `leadr.boards.domain.board.BoardType`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Type of board determining score behavior.

**Attributes:**

- [**COUNTER**](./boards.md#leadr.boards.domain.board.BoardType.COUNTER) –
- [**RATIO**](./boards.md#leadr.boards.domain.board.BoardType.RATIO) –
- [**RUN_IDENTITY**](#leadr.boards.domain.board.BoardType.RUN_IDENTITY) –
- [**RUN_RUNS**](#leadr.boards.domain.board.BoardType.RUN_RUNS) –

####### `leadr.boards.domain.board.BoardType.COUNTER`

```python
COUNTER = 'COUNTER'
```

####### `leadr.boards.domain.board.BoardType.RATIO`

```python
RATIO = 'RATIO'
```

####### `leadr.boards.domain.board.BoardType.RUN_IDENTITY`

```python
RUN_IDENTITY = 'RUN_IDENTITY'
```

####### `leadr.boards.domain.board.BoardType.RUN_RUNS`

```python
RUN_RUNS = 'RUN_RUNS'
```

###### `leadr.boards.domain.board.KeepStrategy`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Strategy for keeping scores from the same user (RUN_IDENTITY boards only).

**Attributes:**

- [**BEST**](./boards.md#leadr.boards.domain.board.KeepStrategy.BEST) –
- [**FIRST**](./boards.md#leadr.boards.domain.board.KeepStrategy.FIRST) –
- [**LATEST**](./boards.md#leadr.boards.domain.board.KeepStrategy.LATEST) –
- [**NA**](./boards.md#leadr.boards.domain.board.KeepStrategy.NA) –

####### `leadr.boards.domain.board.KeepStrategy.BEST`

```python
BEST = 'BEST'
```

####### `leadr.boards.domain.board.KeepStrategy.FIRST`

```python
FIRST = 'FIRST'
```

####### `leadr.boards.domain.board.KeepStrategy.LATEST`

```python
LATEST = 'LATEST'
```

####### `leadr.boards.domain.board.KeepStrategy.NA`

```python
NA = 'NA'
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

##### `leadr.boards.domain.board_ratio_config`

Board ratio config domain model.

**Classes:**

- [**BoardRatioConfig**](#leadr.boards.domain.board_ratio_config.BoardRatioConfig) – Configuration for a RATIO board type.
- [**RatioDisplay**](#leadr.boards.domain.board_ratio_config.RatioDisplay) – Display format for ratio values.
- [**TieBreaker**](#leadr.boards.domain.board_ratio_config.TieBreaker) – Tie-breaking strategy for equal ratios.
- [**ZeroDenominatorPolicy**](#leadr.boards.domain.board_ratio_config.ZeroDenominatorPolicy) – Policy for handling zero denominators in ratio calculations.

###### `leadr.boards.domain.board_ratio_config.BoardRatioConfig`

Bases: <code>[Entity](./common.md#leadr.common.domain.models.Entity)</code>

Configuration for a RATIO board type.

RATIO boards derive their ranking from two other boards (numerator and denominator).
The ratio is calculated as: numerator_value / denominator_value * scale

This is useful for metrics like:

- Win rate: wins / games_played
- Kill/Death ratio: kills / deaths
- Accuracy: hits / shots_fired

**Functions:**

- [**restore**](#leadr.boards.domain.board_ratio_config.BoardRatioConfig.restore) – Restore a soft-deleted entity.
- [**soft_delete**](#leadr.boards.domain.board_ratio_config.BoardRatioConfig.soft_delete) – Mark entity as soft-deleted.

**Attributes:**

- [**board_id**](#leadr.boards.domain.board_ratio_config.BoardRatioConfig.board_id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) –
- [**created_at**](#leadr.boards.domain.board_ratio_config.BoardRatioConfig.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**decimals**](#leadr.boards.domain.board_ratio_config.BoardRatioConfig.decimals) (<code>[int](#int)</code>) –
- [**deleted_at**](#leadr.boards.domain.board_ratio_config.BoardRatioConfig.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**denominator_board_id**](#leadr.boards.domain.board_ratio_config.BoardRatioConfig.denominator_board_id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) –
- [**display**](#leadr.boards.domain.board_ratio_config.BoardRatioConfig.display) (<code>[RatioDisplay](#leadr.boards.domain.board_ratio_config.RatioDisplay)</code>) –
- [**id**](#leadr.boards.domain.board_ratio_config.BoardRatioConfig.id) (<code>[BoardRatioConfigID](./common.md#leadr.common.domain.ids.BoardRatioConfigID)</code>) –
- [**is_deleted**](#leadr.boards.domain.board_ratio_config.BoardRatioConfig.is_deleted) (<code>[bool](#bool)</code>) – Check if entity is soft-deleted.
- [**min_denominator**](#leadr.boards.domain.board_ratio_config.BoardRatioConfig.min_denominator) (<code>[float](#float)</code>) –
- [**min_numerator**](#leadr.boards.domain.board_ratio_config.BoardRatioConfig.min_numerator) (<code>[float](#float)</code>) –
- [**model_config**](#leadr.boards.domain.board_ratio_config.BoardRatioConfig.model_config) –
- [**numerator_board_id**](#leadr.boards.domain.board_ratio_config.BoardRatioConfig.numerator_board_id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) –
- [**scale**](#leadr.boards.domain.board_ratio_config.BoardRatioConfig.scale) (<code>[int](#int)</code>) –
- [**tie_breaker**](#leadr.boards.domain.board_ratio_config.BoardRatioConfig.tie_breaker) (<code>[TieBreaker](#leadr.boards.domain.board_ratio_config.TieBreaker)</code>) –
- [**updated_at**](#leadr.boards.domain.board_ratio_config.BoardRatioConfig.updated_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**zero_denominator_policy**](#leadr.boards.domain.board_ratio_config.BoardRatioConfig.zero_denominator_policy) (<code>[ZeroDenominatorPolicy](#leadr.boards.domain.board_ratio_config.ZeroDenominatorPolicy)</code>) –

####### `leadr.boards.domain.board_ratio_config.BoardRatioConfig.board_id`

```python
board_id: BoardID = Field(frozen=True)
```

####### `leadr.boards.domain.board_ratio_config.BoardRatioConfig.created_at`

```python
created_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp when entity was created (UTC)')
```

####### `leadr.boards.domain.board_ratio_config.BoardRatioConfig.decimals`

```python
decimals: int = 2
```

####### `leadr.boards.domain.board_ratio_config.BoardRatioConfig.deleted_at`

```python
deleted_at: datetime | None = Field(default=None, description='Timestamp when entity was soft-deleted (UTC), or null if active')
```

####### `leadr.boards.domain.board_ratio_config.BoardRatioConfig.denominator_board_id`

```python
denominator_board_id: BoardID = Field(frozen=True)
```

####### `leadr.boards.domain.board_ratio_config.BoardRatioConfig.display`

```python
display: RatioDisplay = RatioDisplay.RAW
```

####### `leadr.boards.domain.board_ratio_config.BoardRatioConfig.id`

```python
id: BoardRatioConfigID = Field(frozen=True, default_factory=BoardRatioConfigID)
```

####### `leadr.boards.domain.board_ratio_config.BoardRatioConfig.is_deleted`

```python
is_deleted: bool
```

Check if entity is soft-deleted.

**Returns:**

- <code>[bool](#bool)</code> – True if the entity has a deleted_at timestamp, False otherwise.

####### `leadr.boards.domain.board_ratio_config.BoardRatioConfig.min_denominator`

```python
min_denominator: float = 0
```

####### `leadr.boards.domain.board_ratio_config.BoardRatioConfig.min_numerator`

```python
min_numerator: float = 0
```

####### `leadr.boards.domain.board_ratio_config.BoardRatioConfig.model_config`

```python
model_config = ConfigDict(validate_assignment=True)
```

####### `leadr.boards.domain.board_ratio_config.BoardRatioConfig.numerator_board_id`

```python
numerator_board_id: BoardID = Field(frozen=True)
```

####### `leadr.boards.domain.board_ratio_config.BoardRatioConfig.restore`

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

####### `leadr.boards.domain.board_ratio_config.BoardRatioConfig.scale`

```python
scale: int = 1000000
```

####### `leadr.boards.domain.board_ratio_config.BoardRatioConfig.soft_delete`

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

####### `leadr.boards.domain.board_ratio_config.BoardRatioConfig.tie_breaker`

```python
tie_breaker: TieBreaker = TieBreaker.NUMERATOR_DESC_DENOMINATOR_ASC
```

####### `leadr.boards.domain.board_ratio_config.BoardRatioConfig.updated_at`

```python
updated_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp of last update (UTC)')
```

####### `leadr.boards.domain.board_ratio_config.BoardRatioConfig.zero_denominator_policy`

```python
zero_denominator_policy: ZeroDenominatorPolicy = ZeroDenominatorPolicy.NULL
```

###### `leadr.boards.domain.board_ratio_config.RatioDisplay`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Display format for ratio values.

- RAW: Display the ratio value as-is (e.g., 0.75)
- PERCENT: Display as percentage (e.g., 75%)

**Attributes:**

- [**PERCENT**](#leadr.boards.domain.board_ratio_config.RatioDisplay.PERCENT) –
- [**RAW**](#leadr.boards.domain.board_ratio_config.RatioDisplay.RAW) –

####### `leadr.boards.domain.board_ratio_config.RatioDisplay.PERCENT`

```python
PERCENT = 'PERCENT'
```

####### `leadr.boards.domain.board_ratio_config.RatioDisplay.RAW`

```python
RAW = 'RAW'
```

###### `leadr.boards.domain.board_ratio_config.TieBreaker`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Tie-breaking strategy for equal ratios.

NUMERATOR_DESC_DENOMINATOR_ASC: Higher numerator wins, then lower denominator.
This favors players who achieved more (higher numerator) with less attempts
(lower denominator).

**Attributes:**

- [**NUMERATOR_DESC_DENOMINATOR_ASC**](#leadr.boards.domain.board_ratio_config.TieBreaker.NUMERATOR_DESC_DENOMINATOR_ASC) –

####### `leadr.boards.domain.board_ratio_config.TieBreaker.NUMERATOR_DESC_DENOMINATOR_ASC`

```python
NUMERATOR_DESC_DENOMINATOR_ASC = 'NUMERATOR_DESC_DENOMINATOR_ASC'
```

###### `leadr.boards.domain.board_ratio_config.ZeroDenominatorPolicy`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Policy for handling zero denominators in ratio calculations.

Determines what value to use when the denominator is zero:

- NULL: Return null/not rankable
- ZERO: Return zero
- INFINITY: Return infinity (highest rank)

**Attributes:**

- [**INFINITY**](#leadr.boards.domain.board_ratio_config.ZeroDenominatorPolicy.INFINITY) –
- [**NULL**](#leadr.boards.domain.board_ratio_config.ZeroDenominatorPolicy.NULL) –
- [**ZERO**](#leadr.boards.domain.board_ratio_config.ZeroDenominatorPolicy.ZERO) –

####### `leadr.boards.domain.board_ratio_config.ZeroDenominatorPolicy.INFINITY`

```python
INFINITY = 'INFINITY'
```

####### `leadr.boards.domain.board_ratio_config.ZeroDenominatorPolicy.NULL`

```python
NULL = 'NULL'
```

####### `leadr.boards.domain.board_ratio_config.ZeroDenominatorPolicy.ZERO`

```python
ZERO = 'ZERO'
```

##### `leadr.boards.domain.board_state`

BoardState domain model for materialized ranking state.

**Classes:**

- [**BoardState**](#leadr.boards.domain.board_state.BoardState) – Materialized ranking state for a single identity on a single board.

###### `leadr.boards.domain.board_state.BoardState`

Bases: <code>[Entity](./common.md#leadr.common.domain.models.Entity)</code>

Materialized ranking state for a single identity on a single board.

BoardState represents the current ranking state of an identity on a board.
It is computed from score events and used for leaderboard queries.

For RUN_IDENTITY boards: Contains the selected score based on keep_strategy.
For RUN_RUNS boards: Not used (run_entries table is used instead).
For COUNTER boards: Contains the accumulated total.
For RATIO boards: Contains the computed ratio value.

The aux field contains board-type-specific auxiliary data:

- RUN_IDENTITY: {"selected_event_id": str, "event_count": int}
- COUNTER: {"event_count": int, "last_event_id": str}
- RATIO: {"numerator_value": float, "denominator_value": float}

Denormalized fields (from Identity and ScoreEvent) are stored for query efficiency:

- player_name: Display name at submission time
- is_test: Test mode flag
- timezone, country, city: Geo data from GeoIP
- value_display: Formatted display string
- metadata: Game-specific JSON

**Attributes:**

- [**id**](#leadr.boards.domain.board_state.BoardState.id) (<code>[BoardStateID](./common.md#leadr.common.domain.ids.BoardStateID)</code>) – Unique identifier for this board state.
- [**board_id**](#leadr.boards.domain.board_state.BoardState.board_id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – The board this state belongs to (immutable).
- [**identity_id**](#leadr.boards.domain.board_state.BoardState.identity_id) (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) – The identity this state is for (immutable).
- [**primary_value**](#leadr.boards.domain.board_state.BoardState.primary_value) (<code>[float](#float) | None</code>) – The rankable value (NULL = not rankable).
- [**aux**](#leadr.boards.domain.board_state.BoardState.aux) (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\] | None</code>) – Board-type-specific auxiliary data.
- [**player_name**](#leadr.boards.domain.board_state.BoardState.player_name) (<code>[str](#str)</code>) – Display name at submission time.
- [**is_test**](#leadr.boards.domain.board_state.BoardState.is_test) (<code>[bool](#bool)</code>) – Whether this is a test submission.
- [**timezone**](#leadr.boards.domain.board_state.BoardState.timezone) (<code>[str](#str) | None</code>) – Timezone from GeoIP (optional).
- [**country**](#leadr.boards.domain.board_state.BoardState.country) (<code>[str](#str) | None</code>) – Country code from GeoIP (optional).
- [**city**](#leadr.boards.domain.board_state.BoardState.city) (<code>[str](#str) | None</code>) – City name from GeoIP (optional).
- [**value_display**](#leadr.boards.domain.board_state.BoardState.value_display) (<code>[str](#str) | None</code>) – Formatted display string (optional).
- [**metadata**](#leadr.boards.domain.board_state.BoardState.metadata) (<code>[Any](#typing.Any) | None</code>) – Game-specific JSON metadata (optional).
- [**created_at**](#leadr.boards.domain.board_state.BoardState.created_at) (<code>[datetime](#datetime.datetime)</code>) – Timestamp when the state was created (UTC).
- [**updated_at**](#leadr.boards.domain.board_state.BoardState.updated_at) (<code>[datetime](#datetime.datetime)</code>) – Timestamp when the state was last updated (UTC).
- [**deleted_at**](#leadr.boards.domain.board_state.BoardState.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) – Timestamp when the state was soft-deleted, or None.

**Functions:**

- [**restore**](#leadr.boards.domain.board_state.BoardState.restore) – Restore a soft-deleted entity.
- [**soft_delete**](#leadr.boards.domain.board_state.BoardState.soft_delete) – Mark entity as soft-deleted.

####### `leadr.boards.domain.board_state.BoardState.aux`

```python
aux: dict[str, Any] | None = Field(default=None, description='Board-type-specific auxiliary data')
```

####### `leadr.boards.domain.board_state.BoardState.board_id`

```python
board_id: BoardID = Field(frozen=True, description='Board this state belongs to (immutable)')
```

####### `leadr.boards.domain.board_state.BoardState.city`

```python
city: str | None = Field(default=None, description='City name from GeoIP (from ScoreEvent)')
```

####### `leadr.boards.domain.board_state.BoardState.country`

```python
country: str | None = Field(default=None, description='Country code from GeoIP (from ScoreEvent)')
```

####### `leadr.boards.domain.board_state.BoardState.created_at`

```python
created_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp when entity was created (UTC)')
```

####### `leadr.boards.domain.board_state.BoardState.deleted_at`

```python
deleted_at: datetime | None = Field(default=None, description='Timestamp when entity was soft-deleted (UTC), or null if active')
```

####### `leadr.boards.domain.board_state.BoardState.id`

```python
id: BoardStateID = Field(frozen=True, default_factory=BoardStateID, description='Unique identifier for this board state')
```

####### `leadr.boards.domain.board_state.BoardState.identity_id`

```python
identity_id: IdentityID = Field(frozen=True, description='Identity this state is for (immutable)')
```

####### `leadr.boards.domain.board_state.BoardState.is_deleted`

```python
is_deleted: bool
```

Check if entity is soft-deleted.

**Returns:**

- <code>[bool](#bool)</code> – True if the entity has a deleted_at timestamp, False otherwise.

####### `leadr.boards.domain.board_state.BoardState.is_placeholder`

```python
is_placeholder: bool = Field(default=False, description='True if this is a synthetic placeholder for around_value queries')
```

####### `leadr.boards.domain.board_state.BoardState.is_test`

```python
is_test: bool = Field(default=False, description='Whether this is a test submission (from ScoreEvent)')
```

####### `leadr.boards.domain.board_state.BoardState.metadata`

```python
metadata: Any | None = Field(default=None, description='Game-specific JSON metadata')
```

####### `leadr.boards.domain.board_state.BoardState.model_config`

```python
model_config = ConfigDict(validate_assignment=True)
```

####### `leadr.boards.domain.board_state.BoardState.player_name`

```python
player_name: str = Field(default='', description='Display name at submission time (from Identity)')
```

####### `leadr.boards.domain.board_state.BoardState.primary_value`

```python
primary_value: float | None = Field(default=None, description='Rankable value (NULL = not rankable)')
```

####### `leadr.boards.domain.board_state.BoardState.rank`

```python
rank: int = Field(default=0, description='Computed rank (transient, not persisted)')
```

####### `leadr.boards.domain.board_state.BoardState.restore`

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

####### `leadr.boards.domain.board_state.BoardState.soft_delete`

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

####### `leadr.boards.domain.board_state.BoardState.timezone`

```python
timezone: str | None = Field(default=None, description='Timezone from GeoIP (from ScoreEvent)')
```

####### `leadr.boards.domain.board_state.BoardState.updated_at`

```python
updated_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp of last update (UTC)')
```

####### `leadr.boards.domain.board_state.BoardState.value_display`

```python
value_display: str | None = Field(default=None, description='Formatted display string')
```

##### `leadr.boards.domain.board_template`

BoardTemplate domain model.

**Classes:**

- [**BoardTemplate**](#leadr.boards.domain.board_template.BoardTemplate) – BoardTemplate domain entity.

###### `leadr.boards.domain.board_template.BoardTemplate`

Bases: <code>[Entity](./common.md#leadr.common.domain.models.Entity)</code>

BoardTemplate domain entity.

Represents a template for automatically generating boards at regular intervals.
Templates belong to a game and define the configuration for boards that will be
created by the pg_cron scheduler.

Each template specifies a repeat interval (PostgreSQL interval syntax), configuration
for boards to be created, and can optionally use template variables in the name
generation. Templates can be activated/deactivated and track the next scheduled run.

**Functions:**

- [**generate_name**](#leadr.boards.domain.board_template.BoardTemplate.generate_name) – Generate a board name using the name template.
- [**restore**](#leadr.boards.domain.board_template.BoardTemplate.restore) – Restore a soft-deleted entity.
- [**soft_delete**](#leadr.boards.domain.board_template.BoardTemplate.soft_delete) – Mark entity as soft-deleted.
- [**validate_name**](#leadr.boards.domain.board_template.BoardTemplate.validate_name) – Validate template name is not empty.
- [**validate_repeat_interval**](#leadr.boards.domain.board_template.BoardTemplate.validate_repeat_interval) – Validate repeat_interval uses PostgreSQL interval syntax.
- [**validate_slug**](#leadr.boards.domain.board_template.BoardTemplate.validate_slug) – Validate slug format (lowercase alphanumeric with hyphens).

**Attributes:**

- [**account_id**](#leadr.boards.domain.board_template.BoardTemplate.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**board_type**](#leadr.boards.domain.board_template.BoardTemplate.board_type) (<code>[BoardType](./boards.md#leadr.boards.domain.board.BoardType)</code>) –
- [**config**](#leadr.boards.domain.board_template.BoardTemplate.config) (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\]</code>) –
- [**created_at**](#leadr.boards.domain.board_template.BoardTemplate.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**deleted_at**](#leadr.boards.domain.board_template.BoardTemplate.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**ends_at**](#leadr.boards.domain.board_template.BoardTemplate.ends_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**game_id**](#leadr.boards.domain.board_template.BoardTemplate.game_id) (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) –
- [**icon**](#leadr.boards.domain.board_template.BoardTemplate.icon) (<code>[str](#str) | None</code>) –
- [**id**](#leadr.boards.domain.board_template.BoardTemplate.id) (<code>[BoardTemplateID](./common.md#leadr.common.domain.ids.BoardTemplateID)</code>) –
- [**is_active**](#leadr.boards.domain.board_template.BoardTemplate.is_active) (<code>[bool](#bool)</code>) –
- [**is_deleted**](#leadr.boards.domain.board_template.BoardTemplate.is_deleted) (<code>[bool](#bool)</code>) – Check if entity is soft-deleted.
- [**is_published**](#leadr.boards.domain.board_template.BoardTemplate.is_published) (<code>[bool](#bool)</code>) –
- [**keep_strategy**](#leadr.boards.domain.board_template.BoardTemplate.keep_strategy) (<code>[KeepStrategy](./boards.md#leadr.boards.domain.board.KeepStrategy)</code>) –
- [**model_config**](#leadr.boards.domain.board_template.BoardTemplate.model_config) –
- [**name**](#leadr.boards.domain.board_template.BoardTemplate.name) (<code>[str](#str)</code>) –
- [**name_template**](#leadr.boards.domain.board_template.BoardTemplate.name_template) (<code>[str](#str) | None</code>) –
- [**next_run_at**](#leadr.boards.domain.board_template.BoardTemplate.next_run_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**repeat_interval**](#leadr.boards.domain.board_template.BoardTemplate.repeat_interval) (<code>[str](#str)</code>) –
- [**series**](#leadr.boards.domain.board_template.BoardTemplate.series) (<code>[str](#str) | None</code>) –
- [**slug**](#leadr.boards.domain.board_template.BoardTemplate.slug) (<code>[str](#str) | None</code>) –
- [**sort_direction**](#leadr.boards.domain.board_template.BoardTemplate.sort_direction) (<code>[SortDirection](./boards.md#leadr.boards.domain.board.SortDirection)</code>) –
- [**starts_at**](#leadr.boards.domain.board_template.BoardTemplate.starts_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**tags**](#leadr.boards.domain.board_template.BoardTemplate.tags) (<code>[list](#list)\[[str](#str)\]</code>) –
- [**unit**](#leadr.boards.domain.board_template.BoardTemplate.unit) (<code>[str](#str) | None</code>) –
- [**updated_at**](#leadr.boards.domain.board_template.BoardTemplate.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.boards.domain.board_template.BoardTemplate.account_id`

```python
account_id: AccountID = Field(frozen=True, description='ID of the account this template belongs to (immutable)')
```

####### `leadr.boards.domain.board_template.BoardTemplate.board_type`

```python
board_type: BoardType = Field(description='Type of board to create from this template', default=(BoardType.RUN_IDENTITY))
```

####### `leadr.boards.domain.board_template.BoardTemplate.config`

```python
config: dict[str, Any] = Field(default_factory=dict, description='Reserved for future procedural generation (bounds, variables, randomization rules)')
```

####### `leadr.boards.domain.board_template.BoardTemplate.created_at`

```python
created_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp when entity was created (UTC)')
```

####### `leadr.boards.domain.board_template.BoardTemplate.deleted_at`

```python
deleted_at: datetime | None = Field(default=None, description='Timestamp when entity was soft-deleted (UTC), or null if active')
```

####### `leadr.boards.domain.board_template.BoardTemplate.ends_at`

```python
ends_at: datetime | None = Field(default=None, description='Optional end time for time-bounded boards')
```

####### `leadr.boards.domain.board_template.BoardTemplate.game_id`

```python
game_id: GameID = Field(frozen=True, description='ID of the game this template belongs to (immutable)')
```

####### `leadr.boards.domain.board_template.BoardTemplate.generate_name`

```python
generate_name(timestamp, series_value)
```

Generate a board name using the name template.

If name_template is None, returns the template's name.
Otherwise, substitutes placeholders with values derived from the timestamp and series.

Supported placeholders:

- {year}: 4-digit year (e.g., 2025)
- {month}: Full month name (e.g., July)
- {month_short}: Abbreviated month (e.g., Jul)
- {week}: ISO week number (e.g., 29)
- {quarter}: Quarter (e.g., Q1, Q2, Q3, Q4)
- {date}: ISO date (e.g., 2025-07-15)
- {series}: Sequential series value

**Parameters:**

- **timestamp** (<code>[datetime](#datetime.datetime)</code>) – The datetime to use for generating time-based placeholders.
- **series_value** (<code>[int](#int) | None</code>) – Optional series value for {series} placeholder.

**Returns:**

- <code>[str](#str)</code> – The generated board name.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If the name_template contains invalid placeholders or if
  {series} is used but series_value is None.

####### `leadr.boards.domain.board_template.BoardTemplate.icon`

```python
icon: str | None = Field(description='Icon identifier for boards created from this template', default='fa-crown')
```

####### `leadr.boards.domain.board_template.BoardTemplate.id`

```python
id: BoardTemplateID = Field(frozen=True, default_factory=BoardTemplateID, description='Unique board template identifier')
```

####### `leadr.boards.domain.board_template.BoardTemplate.is_active`

```python
is_active: bool = Field(description='Whether the template is currently active')
```

####### `leadr.boards.domain.board_template.BoardTemplate.is_deleted`

```python
is_deleted: bool
```

Check if entity is soft-deleted.

**Returns:**

- <code>[bool](#bool)</code> – True if the entity has a deleted_at timestamp, False otherwise.

####### `leadr.boards.domain.board_template.BoardTemplate.is_published`

```python
is_published: bool = Field(description='Whether boards created from this template should be published', default=True)
```

####### `leadr.boards.domain.board_template.BoardTemplate.keep_strategy`

```python
keep_strategy: KeepStrategy = Field(description='Strategy for keeping multiple scores from the same user (RUN_IDENTITY only)', default=(KeepStrategy.BEST))
```

####### `leadr.boards.domain.board_template.BoardTemplate.model_config`

```python
model_config = ConfigDict(validate_assignment=True)
```

####### `leadr.boards.domain.board_template.BoardTemplate.name`

```python
name: str = Field(description='Name of the template')
```

####### `leadr.boards.domain.board_template.BoardTemplate.name_template`

```python
name_template: str | None = Field(default=None, description='Optional template string for generating board names')
```

####### `leadr.boards.domain.board_template.BoardTemplate.next_run_at`

```python
next_run_at: datetime = Field(description='Next scheduled time to create a board from this template')
```

####### `leadr.boards.domain.board_template.BoardTemplate.repeat_interval`

```python
repeat_interval: str = Field(description="PostgreSQL interval syntax for repeat frequency (e.g., '7 days', '1 month')")
```

####### `leadr.boards.domain.board_template.BoardTemplate.restore`

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

####### `leadr.boards.domain.board_template.BoardTemplate.series`

```python
series: str | None = Field(default=None, description="Optional series identifier for sequential board naming (e.g., 'weekly', 'seasonal')")
```

####### `leadr.boards.domain.board_template.BoardTemplate.slug`

```python
slug: str | None = Field(default=None, description='URL-friendly slug for boards created from this template')
```

####### `leadr.boards.domain.board_template.BoardTemplate.soft_delete`

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

####### `leadr.boards.domain.board_template.BoardTemplate.sort_direction`

```python
sort_direction: SortDirection = Field(description='Direction to sort scores (ascending/descending)', default=(SortDirection.DESCENDING))
```

####### `leadr.boards.domain.board_template.BoardTemplate.starts_at`

```python
starts_at: datetime | None = Field(default=None, description='Optional start time for time-bounded boards')
```

####### `leadr.boards.domain.board_template.BoardTemplate.tags`

```python
tags: list[str] = Field(default_factory=list, description='List of tags for categorizing boards created from this template')
```

####### `leadr.boards.domain.board_template.BoardTemplate.unit`

```python
unit: str | None = Field(description="Unit of measurement for scores (e.g., 'seconds', 'points')", default=None)
```

####### `leadr.boards.domain.board_template.BoardTemplate.updated_at`

```python
updated_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp of last update (UTC)')
```

####### `leadr.boards.domain.board_template.BoardTemplate.validate_name`

```python
validate_name(value)
```

Validate template name is not empty.

**Parameters:**

- **value** (<code>[str](#str)</code>) – The template name to validate.

**Returns:**

- <code>[str](#str)</code> – The validated and trimmed template name.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If template name is empty or whitespace only.

####### `leadr.boards.domain.board_template.BoardTemplate.validate_repeat_interval`

```python
validate_repeat_interval(value)
```

Validate repeat_interval uses PostgreSQL interval syntax.

**Parameters:**

- **value** (<code>[str](#str)</code>) – The interval string to validate.

**Returns:**

- <code>[str](#str)</code> – The validated interval string.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If interval syntax is invalid.

####### `leadr.boards.domain.board_template.BoardTemplate.validate_slug`

```python
validate_slug(value)
```

Validate slug format (lowercase alphanumeric with hyphens).

**Parameters:**

- **value** (<code>[str](#str) | None</code>) – The slug to validate, or None.

**Returns:**

- <code>[str](#str) | None</code> – The validated slug, or None if not provided.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If slug is invalid.

##### `leadr.boards.domain.interval_parser`

Utilities for parsing PostgreSQL interval syntax.

**Functions:**

- [**parse_interval**](#leadr.boards.domain.interval_parser.parse_interval) – Parse PostgreSQL interval syntax to Python relativedelta.

###### `leadr.boards.domain.interval_parser.parse_interval`

```python
parse_interval(interval_string)
```

Parse PostgreSQL interval syntax to Python relativedelta.

Supports formats like:

- "7 days"
- "1 week"
- "1 month"
- "1 year"
- "2 hours"

**Parameters:**

- **interval_string** (<code>[str](#str)</code>) – PostgreSQL interval syntax string.

**Returns:**

- <code>[relativedelta](#dateutil.relativedelta.relativedelta)</code> – Equivalent Python relativedelta.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If interval format is invalid or unsupported.

<details class="example" open markdown="1">
<summary>Example</summary>

> > > parse_interval("7 days")
> > > relativedelta(days=7)
> > > parse_interval("1 month")
> > > relativedelta(months=1)

</details>

##### `leadr.boards.domain.run_entry`

RunEntry domain model for RUN_RUNS boards.

**Classes:**

- [**RunEntry**](#leadr.boards.domain.run_entry.RunEntry) – A single scored run entry for RUN_RUNS boards.

###### `leadr.boards.domain.run_entry.RunEntry`

Bases: <code>[Entity](./common.md#leadr.common.domain.models.Entity)</code>

A single scored run entry for RUN_RUNS boards.

RunEntry represents an individual submission on a RUN_RUNS board where
every submission is ranked (as opposed to RUN_IDENTITY boards where
only one entry per identity is kept based on keep_strategy).

Each run entry is linked to a score event and is immutable except for
soft-delete. The primary_value is the rankable value for leaderboard queries.

Denormalized fields (from Identity and ScoreEvent) are stored for query efficiency:

- player_name: Display name at submission time
- is_test: Test mode flag
- timezone, country, city: Geo data from GeoIP
- value_display: Formatted display string
- metadata: Game-specific JSON

**Attributes:**

- [**id**](#leadr.boards.domain.run_entry.RunEntry.id) (<code>[RunEntryID](./common.md#leadr.common.domain.ids.RunEntryID)</code>) – Unique identifier for this run entry.
- [**board_id**](#leadr.boards.domain.run_entry.RunEntry.board_id) (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – The board this entry belongs to (immutable).
- [**identity_id**](#leadr.boards.domain.run_entry.RunEntry.identity_id) (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) – The identity that submitted this entry (immutable).
- [**score_event_id**](#leadr.boards.domain.run_entry.RunEntry.score_event_id) (<code>[ScoreEventID](./common.md#leadr.common.domain.ids.ScoreEventID)</code>) – The score event that created this entry (immutable).
- [**primary_value**](#leadr.boards.domain.run_entry.RunEntry.primary_value) (<code>[float](#float)</code>) – The rankable value for this submission (immutable).
- [**player_name**](#leadr.boards.domain.run_entry.RunEntry.player_name) (<code>[str](#str)</code>) – Display name at submission time.
- [**is_test**](#leadr.boards.domain.run_entry.RunEntry.is_test) (<code>[bool](#bool)</code>) – Whether this is a test submission.
- [**timezone**](#leadr.boards.domain.run_entry.RunEntry.timezone) (<code>[str](#str) | None</code>) – Timezone from GeoIP (optional).
- [**country**](#leadr.boards.domain.run_entry.RunEntry.country) (<code>[str](#str) | None</code>) – Country code from GeoIP (optional).
- [**city**](#leadr.boards.domain.run_entry.RunEntry.city) (<code>[str](#str) | None</code>) – City name from GeoIP (optional).
- [**value_display**](#leadr.boards.domain.run_entry.RunEntry.value_display) (<code>[str](#str) | None</code>) – Formatted display string (optional).
- [**metadata**](#leadr.boards.domain.run_entry.RunEntry.metadata) (<code>[Any](#typing.Any) | None</code>) – Game-specific JSON metadata (optional).
- [**created_at**](#leadr.boards.domain.run_entry.RunEntry.created_at) (<code>[datetime](#datetime.datetime)</code>) – Timestamp when the entry was created (UTC).
- [**updated_at**](#leadr.boards.domain.run_entry.RunEntry.updated_at) (<code>[datetime](#datetime.datetime)</code>) – Timestamp when the entry was last updated (UTC).
- [**deleted_at**](#leadr.boards.domain.run_entry.RunEntry.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) – Timestamp when the entry was soft-deleted, or None.

**Functions:**

- [**restore**](#leadr.boards.domain.run_entry.RunEntry.restore) – Restore a soft-deleted entity.
- [**soft_delete**](#leadr.boards.domain.run_entry.RunEntry.soft_delete) – Mark entity as soft-deleted.

####### `leadr.boards.domain.run_entry.RunEntry.board_id`

```python
board_id: BoardID = Field(frozen=True, description='Board this entry belongs to (immutable)')
```

####### `leadr.boards.domain.run_entry.RunEntry.city`

```python
city: str | None = Field(default=None, description='City name from GeoIP (from ScoreEvent)')
```

####### `leadr.boards.domain.run_entry.RunEntry.country`

```python
country: str | None = Field(default=None, description='Country code from GeoIP (from ScoreEvent)')
```

####### `leadr.boards.domain.run_entry.RunEntry.created_at`

```python
created_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp when entity was created (UTC)')
```

####### `leadr.boards.domain.run_entry.RunEntry.deleted_at`

```python
deleted_at: datetime | None = Field(default=None, description='Timestamp when entity was soft-deleted (UTC), or null if active')
```

####### `leadr.boards.domain.run_entry.RunEntry.excluded_at`

```python
excluded_at: datetime | None = Field(default=None, description='When this entry was excluded from ranking (e.g., confirmed cheat)')
```

####### `leadr.boards.domain.run_entry.RunEntry.excluded_reason`

```python
excluded_reason: str | None = Field(default=None, description="Reason for exclusion (e.g., 'confirmed_cheat')")
```

####### `leadr.boards.domain.run_entry.RunEntry.id`

```python
id: RunEntryID = Field(frozen=True, default_factory=RunEntryID, description='Unique identifier for this run entry')
```

####### `leadr.boards.domain.run_entry.RunEntry.identity_id`

```python
identity_id: IdentityID = Field(frozen=True, description='Identity that submitted this entry (immutable)')
```

####### `leadr.boards.domain.run_entry.RunEntry.is_deleted`

```python
is_deleted: bool
```

Check if entity is soft-deleted.

**Returns:**

- <code>[bool](#bool)</code> – True if the entity has a deleted_at timestamp, False otherwise.

####### `leadr.boards.domain.run_entry.RunEntry.is_placeholder`

```python
is_placeholder: bool = Field(default=False, description='True if this is a synthetic placeholder for around_value queries')
```

####### `leadr.boards.domain.run_entry.RunEntry.is_test`

```python
is_test: bool = Field(default=False, description='Whether this is a test submission (from ScoreEvent)')
```

####### `leadr.boards.domain.run_entry.RunEntry.metadata`

```python
metadata: Any | None = Field(default=None, description='Game-specific JSON metadata')
```

####### `leadr.boards.domain.run_entry.RunEntry.model_config`

```python
model_config = ConfigDict(validate_assignment=True)
```

####### `leadr.boards.domain.run_entry.RunEntry.player_name`

```python
player_name: str = Field(default='', description='Display name at submission time (from Identity)')
```

####### `leadr.boards.domain.run_entry.RunEntry.primary_value`

```python
primary_value: float = Field(frozen=True, description='Rankable value for this submission (immutable)')
```

####### `leadr.boards.domain.run_entry.RunEntry.rank`

```python
rank: int = Field(default=0, description='Computed rank (transient, not persisted)')
```

####### `leadr.boards.domain.run_entry.RunEntry.restore`

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

####### `leadr.boards.domain.run_entry.RunEntry.score_event_id`

```python
score_event_id: ScoreEventID = Field(frozen=True, description='Score event that created this entry (immutable)')
```

####### `leadr.boards.domain.run_entry.RunEntry.soft_delete`

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

####### `leadr.boards.domain.run_entry.RunEntry.timezone`

```python
timezone: str | None = Field(default=None, description='Timezone from GeoIP (from ScoreEvent)')
```

####### `leadr.boards.domain.run_entry.RunEntry.updated_at`

```python
updated_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp of last update (UTC)')
```

####### `leadr.boards.domain.run_entry.RunEntry.value_display`

```python
value_display: str | None = Field(default=None, description='Formatted display string')
```

#### `leadr.boards.services`

**Modules:**

- [**board_ratio_config_service**](#leadr.boards.services.board_ratio_config_service) – Board ratio config service for managing ratio board configurations.
- [**board_service**](#leadr.boards.services.board_service) – Board service for managing board operations.
- [**board_state_service**](#leadr.boards.services.board_state_service) – Board state service for managing materialized ranking state.
- [**board_tasks**](#leadr.boards.services.board_tasks) – Background tasks for board processing.
- [**board_template_service**](#leadr.boards.services.board_template_service) – BoardTemplate service for managing board template operations.
- [**dependencies**](./boards.md#leadr.boards.services.dependencies) – Board service dependency injection.
- [**repositories**](./boards.md#leadr.boards.services.repositories) – Board repository services.
- [**run_entry_service**](#leadr.boards.services.run_entry_service) – Run entry service for managing run entries.
- [**short_code_generator**](#leadr.boards.services.short_code_generator) – Utility for generating unique short codes for boards.

##### `leadr.boards.services.board_ratio_config_service`

Board ratio config service for managing ratio board configurations.

**Classes:**

- [**BoardRatioConfigService**](#leadr.boards.services.board_ratio_config_service.BoardRatioConfigService) – Service for managing board ratio configurations.

###### `leadr.boards.services.board_ratio_config_service.BoardRatioConfigService`

Bases: <code>[BaseService](./common.md#leadr.common.services.BaseService)\[[BoardRatioConfig](#leadr.boards.domain.board_ratio_config.BoardRatioConfig), [BoardRatioConfigRepository](./boards.md#leadr.boards.services.repositories.BoardRatioConfigRepository)\]</code>

Service for managing board ratio configurations.

**Functions:**

- [**create_ratio_config**](#leadr.boards.services.board_ratio_config_service.BoardRatioConfigService.create_ratio_config) – Create a new ratio config for a board.
- [**delete**](#leadr.boards.services.board_ratio_config_service.BoardRatioConfigService.delete) – Soft-delete an entity.
- [**get_by_board_id**](#leadr.boards.services.board_ratio_config_service.BoardRatioConfigService.get_by_board_id) – Get the ratio config for a specific board.
- [**get_by_id**](#leadr.boards.services.board_ratio_config_service.BoardRatioConfigService.get_by_id) – Get an entity by its ID.
- [**get_by_id_or_raise**](#leadr.boards.services.board_ratio_config_service.BoardRatioConfigService.get_by_id_or_raise) – Get an entity by its ID or raise EntityNotFoundError.
- [**get_ratio_config**](#leadr.boards.services.board_ratio_config_service.BoardRatioConfigService.get_ratio_config) – Get a ratio config by ID.
- [**list_all**](#leadr.boards.services.board_ratio_config_service.BoardRatioConfigService.list_all) – List all non-deleted entities.
- [**soft_delete**](#leadr.boards.services.board_ratio_config_service.BoardRatioConfigService.soft_delete) – Soft-delete an entity and return it before deletion.
- [**update_ratio_config**](#leadr.boards.services.board_ratio_config_service.BoardRatioConfigService.update_ratio_config) – Update a ratio config.

**Attributes:**

- [**repository**](#leadr.boards.services.board_ratio_config_service.BoardRatioConfigService.repository) –

####### `leadr.boards.services.board_ratio_config_service.BoardRatioConfigService.create_ratio_config`

```python
create_ratio_config(board_id, numerator_board_id, denominator_board_id, zero_denominator_policy=ZeroDenominatorPolicy.NULL, min_denominator=0, min_numerator=0, scale=1000000, display=RatioDisplay.RAW, decimals=2, tie_breaker=TieBreaker.NUMERATOR_DESC_DENOMINATOR_ASC)
```

Create a new ratio config for a board.

**Parameters:**

- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – ID of the ratio board.
- **numerator_board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – ID of the numerator board.
- **denominator_board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – ID of the denominator board.
- **zero_denominator_policy** (<code>[ZeroDenominatorPolicy](#leadr.boards.domain.board_ratio_config.ZeroDenominatorPolicy)</code>) – How to handle zero denominators.
- **min_denominator** (<code>[float](#float)</code>) – Minimum denominator for ranking eligibility.
- **min_numerator** (<code>[float](#float)</code>) – Minimum numerator for ranking eligibility.
- **scale** (<code>[int](#int)</code>) – Scaling factor for ratio storage.
- **display** (<code>[RatioDisplay](#leadr.boards.domain.board_ratio_config.RatioDisplay)</code>) – Display format for ratio values.
- **decimals** (<code>[int](#int)</code>) – Number of decimal places for display.
- **tie_breaker** (<code>[TieBreaker](#leadr.boards.domain.board_ratio_config.TieBreaker)</code>) – Strategy for breaking ties.

**Returns:**

- <code>[BoardRatioConfig](#leadr.boards.domain.board_ratio_config.BoardRatioConfig)</code> – Created BoardRatioConfig entity.

####### `leadr.boards.services.board_ratio_config_service.BoardRatioConfigService.delete`

```python
delete(entity_id)
```

Soft-delete an entity.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – The ID of the entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the entity doesn't exist

####### `leadr.boards.services.board_ratio_config_service.BoardRatioConfigService.get_by_board_id`

```python
get_by_board_id(board_id)
```

Get the ratio config for a specific board.

**Parameters:**

- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – The ratio board ID.

**Returns:**

- <code>[BoardRatioConfig](#leadr.boards.domain.board_ratio_config.BoardRatioConfig) | None</code> – BoardRatioConfig if found, None otherwise.

####### `leadr.boards.services.board_ratio_config_service.BoardRatioConfigService.get_by_id`

```python
get_by_id(entity_id)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – The ID of the entity to retrieve

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.services.DomainEntityT) | None</code> – The domain entity if found, None otherwise

####### `leadr.boards.services.board_ratio_config_service.BoardRatioConfigService.get_by_id_or_raise`

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

####### `leadr.boards.services.board_ratio_config_service.BoardRatioConfigService.get_ratio_config`

```python
get_ratio_config(config_id)
```

Get a ratio config by ID.

**Parameters:**

- **config_id** (<code>[BoardRatioConfigID](./common.md#leadr.common.domain.ids.BoardRatioConfigID)</code>) – The ratio config ID.

**Returns:**

- <code>[BoardRatioConfig](#leadr.boards.domain.board_ratio_config.BoardRatioConfig) | None</code> – BoardRatioConfig if found, None otherwise.

####### `leadr.boards.services.board_ratio_config_service.BoardRatioConfigService.list_all`

```python
list_all()
```

List all non-deleted entities.

**Returns:**

- <code>[list](#list)\[[DomainEntityT](./common.md#leadr.common.services.DomainEntityT)\]</code> – List of domain entities

####### `leadr.boards.services.board_ratio_config_service.BoardRatioConfigService.repository`

```python
repository = repository if repository is not None else self._create_repository(session)
```

####### `leadr.boards.services.board_ratio_config_service.BoardRatioConfigService.soft_delete`

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

####### `leadr.boards.services.board_ratio_config_service.BoardRatioConfigService.update_ratio_config`

```python
update_ratio_config(config_id, zero_denominator_policy=None, min_denominator=None, min_numerator=None, scale=None, display=None, decimals=None, tie_breaker=None)
```

Update a ratio config.

**Parameters:**

- **config_id** (<code>[BoardRatioConfigID](./common.md#leadr.common.domain.ids.BoardRatioConfigID)</code>) – The ratio config ID.
- **zero_denominator_policy** (<code>[ZeroDenominatorPolicy](#leadr.boards.domain.board_ratio_config.ZeroDenominatorPolicy) | None</code>) – New zero denominator policy.
- **min_denominator** (<code>[float](#float) | None</code>) – New minimum denominator.
- **min_numerator** (<code>[float](#float) | None</code>) – New minimum numerator.
- **scale** (<code>[int](#int) | None</code>) – New scale.
- **display** (<code>[RatioDisplay](#leadr.boards.domain.board_ratio_config.RatioDisplay) | None</code>) – New display format.
- **decimals** (<code>[int](#int) | None</code>) – New decimal places.
- **tie_breaker** (<code>[TieBreaker](#leadr.boards.domain.board_ratio_config.TieBreaker) | None</code>) – New tie breaker strategy.

**Returns:**

- <code>[BoardRatioConfig](#leadr.boards.domain.board_ratio_config.BoardRatioConfig)</code> – Updated BoardRatioConfig entity.

**Raises:**

- <code>[EntityNotFoundError](#EntityNotFoundError)</code> – If config not found.

##### `leadr.boards.services.board_service`

Board service for managing board operations.

**Classes:**

- [**BoardService**](#leadr.boards.services.board_service.BoardService) – Service for managing board lifecycle and operations.

**Attributes:**

- [**logger**](#leadr.boards.services.board_service.logger) –

###### `leadr.boards.services.board_service.BoardService`

Bases: <code>[BaseService](./common.md#leadr.common.services.BaseService)\[[Board](./boards.md#leadr.boards.domain.board.Board), [BoardRepository](./boards.md#leadr.boards.services.repositories.BoardRepository)\]</code>

Service for managing board lifecycle and operations.

This service orchestrates board creation, updates, and retrieval
by coordinating between the domain models and repository layer.
Ensures business rules like game validation are enforced.

**Functions:**

- [**create_board**](#leadr.boards.services.board_service.BoardService.create_board) – Create a new board.
- [**create_board_from_template**](#leadr.boards.services.board_service.BoardService.create_board_from_template) – Create a new board from a board template.
- [**delete**](#leadr.boards.services.board_service.BoardService.delete) – Soft-delete an entity.
- [**get_board**](#leadr.boards.services.board_service.BoardService.get_board) – Get a board by its ID.
- [**get_board_by_short_code**](#leadr.boards.services.board_service.BoardService.get_board_by_short_code) – Get a board by its short_code.
- [**get_by_id**](#leadr.boards.services.board_service.BoardService.get_by_id) – Get an entity by its ID.
- [**get_by_id_or_raise**](#leadr.boards.services.board_service.BoardService.get_by_id_or_raise) – Get an entity by its ID or raise EntityNotFoundError.
- [**list_all**](#leadr.boards.services.board_service.BoardService.list_all) – List all non-deleted entities.
- [**list_boards**](#leadr.boards.services.board_service.BoardService.list_boards) – List boards with optional filtering and pagination.
- [**list_boards_by_account**](#leadr.boards.services.board_service.BoardService.list_boards_by_account) – List all boards for an account.
- [**soft_delete**](#leadr.boards.services.board_service.BoardService.soft_delete) – Soft-delete an entity and return it before deletion.
- [**update_board**](#leadr.boards.services.board_service.BoardService.update_board) – Update board fields.

**Attributes:**

- [**repository**](#leadr.boards.services.board_service.BoardService.repository) –

####### `leadr.boards.services.board_service.BoardService.create_board`

```python
create_board(account_id, game_id, name, icon='fa-crown', unit=None, is_active=True, is_published=True, sort_direction=SortDirection.DESCENDING, board_type=BoardType.RUN_IDENTITY, keep_strategy=KeepStrategy.BEST, slug=None, short_code=None, created_from_template_id=None, template_name=None, starts_at=None, ends_at=None, tags=None, description=None)
```

Create a new board.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – The ID of the account that owns this board.
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) – The ID of the game this board belongs to.
- **name** (<code>[str](#str)</code>) – The board name.
- **icon** (<code>[str](#str) | None</code>) – Icon identifier for the board. Defaults to "fa-crown".
- **unit** (<code>[str](#str) | None</code>) – Unit of measurement for scores. Defaults to None.
- **is_active** (<code>[bool](#bool)</code>) – Whether the board is currently active. Defaults to True.
- **is_published** (<code>[bool](#bool)</code>) – Whether the board is published and visible on public web views.
  Defaults to True.
- **sort_direction** (<code>[SortDirection](./boards.md#leadr.boards.domain.board.SortDirection)</code>) – Direction to sort scores. Defaults to DESCENDING.
- **keep_strategy** (<code>[KeepStrategy](./boards.md#leadr.boards.domain.board.KeepStrategy)</code>) – Strategy for keeping multiple scores from same user. Defaults to ALL.
- **slug** (<code>[str](#str) | None</code>) – Optional URL-friendly slug. If not provided, auto-generated from name.
- **short_code** (<code>[str](#str) | None</code>) – Globally unique short code for direct sharing.
- **created_from_template_id** (<code>[BoardTemplateID](./common.md#leadr.common.domain.ids.BoardTemplateID) | None</code>) – Optional template ID this board was created from.
- **template_name** (<code>[str](#str) | None</code>) – Optional template name.
- **starts_at** (<code>[datetime](#datetime.datetime) | None</code>) – Optional start time for time-bounded boards.
- **ends_at** (<code>[datetime](#datetime.datetime) | None</code>) – Optional end time for time-bounded boards.
- **tags** (<code>[list](#list)\[[str](#str)\] | None</code>) – Optional list of tags for categorization.
- **description** (<code>[str](#str) | None</code>) – Optional short description of the board.

**Returns:**

- <code>[Board](./boards.md#leadr.boards.domain.board.Board)</code> – The created Board domain entity.

**Raises:**

- <code>[EntityNotFoundError](#EntityNotFoundError)</code> – If the game doesn't exist.
- <code>[ValueError](#ValueError)</code> – If the game doesn't belong to the specified account or slug is invalid.

<details class="example" open markdown="1">
<summary>Example</summary>

> > > board = await service.create_board(
> > > ... account_id=account.id,
> > > ... game_id=game.id,
> > > ... name="Speed Run Board",
> > > ... icon="trophy",
> > > ... unit="seconds",
> > > ... is_active=True,
> > > ... sort_direction=SortDirection.ASCENDING,
> > > ... keep_strategy=KeepStrategy.BEST,
> > > ... )

</details>

####### `leadr.boards.services.board_service.BoardService.create_board_from_template`

```python
create_board_from_template(template)
```

Create a new board from a board template.

Extracts configuration from the template and calculates time boundaries
based on the template's repeat_interval. Automatically generates a unique
short code for the board. If the template has a series field, generates
a sequential series value and uses it in the board name.

**Parameters:**

- **template** (<code>[BoardTemplate](#leadr.boards.domain.board_template.BoardTemplate)</code>) – The BoardTemplate to create a board from.

**Returns:**

- <code>[Board](./boards.md#leadr.boards.domain.board.Board)</code> – The created Board domain entity.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If interval parsing fails, game doesn't belong to account,
  or name generation fails.

<details class="example" open markdown="1">
<summary>Example</summary>

> > > board = await service.create_board_from_template(template)

</details>

####### `leadr.boards.services.board_service.BoardService.delete`

```python
delete(entity_id)
```

Soft-delete an entity.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – The ID of the entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the entity doesn't exist

####### `leadr.boards.services.board_service.BoardService.get_board`

```python
get_board(board_id)
```

Get a board by its ID.

**Parameters:**

- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – The ID of the board to retrieve.

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

- **entity_id** (<code>[UUID](#uuid.UUID) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – The ID of the entity to retrieve

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.services.DomainEntityT) | None</code> – The domain entity if found, None otherwise

####### `leadr.boards.services.board_service.BoardService.get_by_id_or_raise`

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

####### `leadr.boards.services.board_service.BoardService.list_all`

```python
list_all()
```

List all non-deleted entities.

**Returns:**

- <code>[list](#list)\[[DomainEntityT](./common.md#leadr.common.services.DomainEntityT)\]</code> – List of domain entities

####### `leadr.boards.services.board_service.BoardService.list_boards`

```python
list_boards(account_id=None, game_id=None, code=None, slug=None, is_active=None, is_published=None, starts_before=None, starts_after=None, ends_before=None, ends_after=None, *, pagination)
```

List boards with optional filtering and pagination.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – Optional account ID to filter by
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID) | None</code>) – Optional game ID to filter by
- **code** (<code>[str](#str) | None</code>) – Optional short code to filter by
- **slug** (<code>[str](#str) | None</code>) – Optional slug to filter by
- **is_active** (<code>[bool](#bool) | None</code>) – Optional filter for active status
- **is_published** (<code>[bool](#bool) | None</code>) – Optional filter for published status
- **starts_before** (<code>[datetime](#datetime.datetime) | None</code>) – Optional filter for boards starting before this time
- **starts_after** (<code>[datetime](#datetime.datetime) | None</code>) – Optional filter for boards starting after this time
- **ends_before** (<code>[datetime](#datetime.datetime) | None</code>) – Optional filter for boards ending before this time
- **ends_after** (<code>[datetime](#datetime.datetime) | None</code>) – Optional filter for boards ending after this time
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (required)

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[Board](./boards.md#leadr.boards.domain.board.Board)\]</code> – PaginatedResult containing Board entities matching the filter criteria.

####### `leadr.boards.services.board_service.BoardService.list_boards_by_account`

```python
list_boards_by_account(account_id)
```

List all boards for an account.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – The ID of the account to list boards for.

**Returns:**

- <code>[list](#list)\[[Board](./boards.md#leadr.boards.domain.board.Board)\]</code> – List of Board domain entities for the account.

####### `leadr.boards.services.board_service.BoardService.repository`

```python
repository = repository if repository is not None else self._create_repository(session)
```

####### `leadr.boards.services.board_service.BoardService.soft_delete`

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

####### `leadr.boards.services.board_service.BoardService.update_board`

```python
update_board(board_id, **updates)
```

Update board fields.

Accepts any fields to update as keyword arguments. Only fields
explicitly provided will be updated, allowing null values to
clear optional fields.

**Parameters:**

- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – The ID of the board to update
- \*\***updates** (<code>[Any](#typing.Any)</code>) – Field names and values to update

**Returns:**

- <code>[Board](./boards.md#leadr.boards.domain.board.Board)</code> – The updated Board domain entity

**Raises:**

- <code>[EntityNotFoundError](#EntityNotFoundError)</code> – If the board doesn't exist

###### `leadr.boards.services.board_service.logger`

```python
logger = get_logger(__name__)
```

##### `leadr.boards.services.board_state_service`

Board state service for managing materialized ranking state.

**Classes:**

- [**BoardStateService**](#leadr.boards.services.board_state_service.BoardStateService) – Service for managing board states.

###### `leadr.boards.services.board_state_service.BoardStateService`

```python
BoardStateService(session)
```

Service for managing board states.

Board states represent the materialized ranking state for identities on boards.
Each identity has at most one state per board. States are updated when new
score events are processed.

**Functions:**

- [**create_board_state**](#leadr.boards.services.board_state_service.BoardStateService.create_board_state) – Create a new board state.
- [**find_dependent_ratio_boards**](#leadr.boards.services.board_state_service.BoardStateService.find_dependent_ratio_boards) – Find RATIO boards where this board is numerator or denominator.
- [**get_board_state**](#leadr.boards.services.board_state_service.BoardStateService.get_board_state) – Get a board state by ID.
- [**get_by_board_and_identity**](#leadr.boards.services.board_state_service.BoardStateService.get_by_board_and_identity) – Get a board state by board and identity.
- [**get_by_id_or_raise**](#leadr.boards.services.board_state_service.BoardStateService.get_by_id_or_raise) – Get a board state by ID, raising if not found.
- [**list_board_states**](#leadr.boards.services.board_state_service.BoardStateService.list_board_states) – List board states with optional filters.
- [**recompute_ratio_for_identity**](#leadr.boards.services.board_state_service.BoardStateService.recompute_ratio_for_identity) – Recalculate ratio value and upsert board state.
- [**soft_delete**](#leadr.boards.services.board_state_service.BoardStateService.soft_delete) – Soft delete a board state.
- [**upsert_board_state**](#leadr.boards.services.board_state_service.BoardStateService.upsert_board_state) – Create or update a board state.

**Attributes:**

- [**repository**](#leadr.boards.services.board_state_service.BoardStateService.repository) –
- [**session**](#leadr.boards.services.board_state_service.BoardStateService.session) –

**Parameters:**

- **session** (<code>[AsyncSession](#sqlalchemy.ext.asyncio.AsyncSession)</code>) – SQLAlchemy async session

####### `leadr.boards.services.board_state_service.BoardStateService.create_board_state`

```python
create_board_state(board_id, identity_id, primary_value=None, aux=None, *, player_name='', is_test=False, timezone=None, country=None, city=None, value_display=None, metadata=None)
```

Create a new board state.

**Parameters:**

- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – Board this state belongs to
- **identity_id** (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) – Identity this state is for
- **primary_value** (<code>[float](#float) | None</code>) – Rankable value (None = not rankable)
- **aux** (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\] | None</code>) – Board-type-specific auxiliary data
- **player_name** (<code>[str](#str)</code>) – Display name at submission time
- **is_test** (<code>[bool](#bool)</code>) – Whether this is a test submission
- **timezone** (<code>[str](#str) | None</code>) – Timezone from GeoIP
- **country** (<code>[str](#str) | None</code>) – Country code from GeoIP
- **city** (<code>[str](#str) | None</code>) – City name from GeoIP
- **value_display** (<code>[str](#str) | None</code>) – Formatted display string
- **metadata** (<code>[Any](#typing.Any) | None</code>) – Game-specific JSON metadata

**Returns:**

- <code>[BoardState](#leadr.boards.domain.board_state.BoardState)</code> – Created BoardState entity

####### `leadr.boards.services.board_state_service.BoardStateService.find_dependent_ratio_boards`

```python
find_dependent_ratio_boards(board_id)
```

Find RATIO boards where this board is numerator or denominator.

**Parameters:**

- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – The board ID to check for dependencies.

**Returns:**

- <code>[list](#list)\[[BoardRatioConfig](#leadr.boards.domain.board_ratio_config.BoardRatioConfig)\]</code> – List of BoardRatioConfig entities that depend on this board.

####### `leadr.boards.services.board_state_service.BoardStateService.get_board_state`

```python
get_board_state(state_id)
```

Get a board state by ID.

**Parameters:**

- **state_id** (<code>[BoardStateID](./common.md#leadr.common.domain.ids.BoardStateID)</code>) – Board state ID

**Returns:**

- <code>[BoardState](#leadr.boards.domain.board_state.BoardState) | None</code> – BoardState if found, None otherwise

####### `leadr.boards.services.board_state_service.BoardStateService.get_by_board_and_identity`

```python
get_by_board_and_identity(board_id, identity_id)
```

Get a board state by board and identity.

**Parameters:**

- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – Board ID
- **identity_id** (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) – Identity ID

**Returns:**

- <code>[BoardState](#leadr.boards.domain.board_state.BoardState) | None</code> – BoardState if found, None otherwise

####### `leadr.boards.services.board_state_service.BoardStateService.get_by_id_or_raise`

```python
get_by_id_or_raise(state_id)
```

Get a board state by ID, raising if not found.

**Parameters:**

- **state_id** (<code>[BoardStateID](./common.md#leadr.common.domain.ids.BoardStateID)</code>) – Board state ID

**Returns:**

- <code>[BoardState](#leadr.boards.domain.board_state.BoardState)</code> – BoardState entity

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If state not found

####### `leadr.boards.services.board_state_service.BoardStateService.list_board_states`

```python
list_board_states(board_id=None, identity_id=None, is_test=None, pagination=None, around_state=None, around_value=None)
```

List board states with optional filters.

**Parameters:**

- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None</code>) – Optional filter by board
- **identity_id** (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID) | None</code>) – Optional filter by identity
- **is_test** (<code>[bool](#bool) | None</code>) – Optional filter for test entries (True=test only, False=prod only, None=all)
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams) | None</code>) – Optional pagination parameters
- **around_state** (<code>[BoardState](#leadr.boards.domain.board_state.BoardState) | None</code>) – Optional target state to center results around
- **around_value** (<code>[float](#float) | None</code>) – Optional value to center results around (creates placeholder)

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[BoardState](#leadr.boards.domain.board_state.BoardState)\]</code> – Paginated list of board states

####### `leadr.boards.services.board_state_service.BoardStateService.recompute_ratio_for_identity`

```python
recompute_ratio_for_identity(ratio_config, identity_id)
```

Recalculate ratio value and upsert board state.

Fetches the numerator and denominator values from the source boards,
calculates the ratio, and creates/updates the ratio board state.

**Parameters:**

- **ratio_config** (<code>[BoardRatioConfig](#leadr.boards.domain.board_ratio_config.BoardRatioConfig)</code>) – The ratio configuration specifying source boards.
- **identity_id** (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) – The identity to recompute the ratio for.

**Returns:**

- <code>[BoardState](#leadr.boards.domain.board_state.BoardState) | None</code> – The created/updated BoardState, or None if source data is missing.

####### `leadr.boards.services.board_state_service.BoardStateService.repository`

```python
repository = BoardStateRepository(session)
```

####### `leadr.boards.services.board_state_service.BoardStateService.session`

```python
session = session
```

####### `leadr.boards.services.board_state_service.BoardStateService.soft_delete`

```python
soft_delete(state_id)
```

Soft delete a board state.

**Parameters:**

- **state_id** (<code>[BoardStateID](./common.md#leadr.common.domain.ids.BoardStateID)</code>) – Board state ID

**Returns:**

- <code>[BoardState](#leadr.boards.domain.board_state.BoardState)</code> – The soft-deleted BoardState entity

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If state not found

####### `leadr.boards.services.board_state_service.BoardStateService.upsert_board_state`

```python
upsert_board_state(board_id, identity_id, primary_value=None, aux=None, *, player_name='', is_test=False, timezone=None, country=None, city=None, value_display=None, metadata=None)
```

Create or update a board state.

If a state already exists for the board/identity combination, it is updated.
Otherwise, a new state is created.

**Parameters:**

- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – Board this state belongs to
- **identity_id** (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) – Identity this state is for
- **primary_value** (<code>[float](#float) | None</code>) – Rankable value (None = not rankable)
- **aux** (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\] | None</code>) – Board-type-specific auxiliary data
- **player_name** (<code>[str](#str)</code>) – Display name at submission time
- **is_test** (<code>[bool](#bool)</code>) – Whether this is a test submission
- **timezone** (<code>[str](#str) | None</code>) – Timezone from GeoIP
- **country** (<code>[str](#str) | None</code>) – Country code from GeoIP
- **city** (<code>[str](#str) | None</code>) – City name from GeoIP
- **value_display** (<code>[str](#str) | None</code>) – Formatted display string
- **metadata** (<code>[Any](#typing.Any) | None</code>) – Game-specific JSON metadata

**Returns:**

- <code>[BoardState](#leadr.boards.domain.board_state.BoardState)</code> – Created or updated BoardState entity

##### `leadr.boards.services.board_tasks`

Background tasks for board processing.

Contains tasks for:

- Processing due board templates and creating boards
- Expiring boards past their end date

**Functions:**

- [**expire_boards**](#leadr.boards.services.board_tasks.expire_boards) – Expire boards that have passed their end date.
- [**process_due_templates**](#leadr.boards.services.board_tasks.process_due_templates) – Process all due board templates and create boards.

**Attributes:**

- [**logger**](#leadr.boards.services.board_tasks.logger) –

###### `leadr.boards.services.board_tasks.expire_boards`

```python
expire_boards()
```

Expire boards that have passed their end date.

Queries for active boards where ends_at \<= now() and sets is_active=False.

This task is designed to be called periodically (e.g., every minute).

###### `leadr.boards.services.board_tasks.logger`

```python
logger = logging.getLogger(__name__)
```

###### `leadr.boards.services.board_tasks.process_due_templates`

```python
process_due_templates()
```

Process all due board templates and create boards.

Queries for active templates where next_run_at \<= now(), creates boards
from each template, and updates the template's next_run_at.

This task is designed to be called periodically (e.g., every minute).

##### `leadr.boards.services.board_template_service`

BoardTemplate service for managing board template operations.

**Classes:**

- [**BoardTemplateService**](#leadr.boards.services.board_template_service.BoardTemplateService) – Service for managing board template lifecycle and operations.

**Attributes:**

- [**logger**](#leadr.boards.services.board_template_service.logger) –

###### `leadr.boards.services.board_template_service.BoardTemplateService`

Bases: <code>[BaseService](./common.md#leadr.common.services.BaseService)\[[BoardTemplate](#leadr.boards.domain.board_template.BoardTemplate), [BoardTemplateRepository](./boards.md#leadr.boards.services.repositories.BoardTemplateRepository)\]</code>

Service for managing board template lifecycle and operations.

This service orchestrates board template creation, updates, and retrieval
by coordinating between the domain models and repository layer.
Ensures business rules like game validation are enforced.

**Functions:**

- [**advance_template_schedule**](#leadr.boards.services.board_template_service.BoardTemplateService.advance_template_schedule) – Advance a template's next_run_at by its repeat_interval.
- [**create_board_template**](#leadr.boards.services.board_template_service.BoardTemplateService.create_board_template) – Create a new board template.
- [**delete**](#leadr.boards.services.board_template_service.BoardTemplateService.delete) – Soft-delete an entity.
- [**get_board_template**](#leadr.boards.services.board_template_service.BoardTemplateService.get_board_template) – Get a board template by its ID.
- [**get_by_id**](#leadr.boards.services.board_template_service.BoardTemplateService.get_by_id) – Get an entity by its ID.
- [**get_by_id_or_raise**](#leadr.boards.services.board_template_service.BoardTemplateService.get_by_id_or_raise) – Get an entity by its ID or raise EntityNotFoundError.
- [**list_all**](#leadr.boards.services.board_template_service.BoardTemplateService.list_all) – List all non-deleted entities.
- [**list_board_templates_by_account**](#leadr.boards.services.board_template_service.BoardTemplateService.list_board_templates_by_account) – List all board templates for an account with pagination.
- [**list_board_templates_by_game**](#leadr.boards.services.board_template_service.BoardTemplateService.list_board_templates_by_game) – List all board templates for a specific game with pagination.
- [**soft_delete**](#leadr.boards.services.board_template_service.BoardTemplateService.soft_delete) – Soft-delete an entity and return it before deletion.
- [**update_board_template**](#leadr.boards.services.board_template_service.BoardTemplateService.update_board_template) – Update board template fields.

**Attributes:**

- [**repository**](#leadr.boards.services.board_template_service.BoardTemplateService.repository) –

####### `leadr.boards.services.board_template_service.BoardTemplateService.advance_template_schedule`

```python
advance_template_schedule(template_id)
```

Advance a template's next_run_at by its repeat_interval.

This is typically called after successfully creating a board from the template.

**Parameters:**

- **template_id** (<code>[BoardTemplateID](./common.md#leadr.common.domain.ids.BoardTemplateID)</code>) – The ID of the template to advance.

**Returns:**

- <code>[BoardTemplate](#leadr.boards.domain.board_template.BoardTemplate)</code> – The updated BoardTemplate with advanced next_run_at.

**Raises:**

- <code>[EntityNotFoundError](#EntityNotFoundError)</code> – If the template doesn't exist.
- <code>[ValueError](#ValueError)</code> – If the repeat_interval cannot be parsed.

<details class="example" open markdown="1">
<summary>Example</summary>

> > > template = await service.advance_template_schedule(template.id)
> > >
> > > # template.next_run_at is now advanced by repeat_interval

</details>

####### `leadr.boards.services.board_template_service.BoardTemplateService.create_board_template`

```python
create_board_template(account_id, game_id, name, slug, repeat_interval, next_run_at, is_active, is_published=True, name_template=None, series=None, icon='fa-crown', unit=None, sort_direction=SortDirection.DESCENDING, keep_strategy=KeepStrategy.BEST, starts_at=None, ends_at=None, tags=None, config=None)
```

Create a new board template.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – The ID of the account that owns this template.
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) – The ID of the game this template belongs to.
- **name** (<code>[str](#str)</code>) – The template name.
- **repeat_interval** (<code>[str](#str)</code>) – PostgreSQL interval syntax for repeat frequency.
- **next_run_at** (<code>[datetime](#datetime.datetime)</code>) – Next scheduled time to create a board.
- **is_active** (<code>[bool](#bool)</code>) – Whether the template is currently active.
- **name_template** (<code>[str](#str) | None</code>) – Optional template string for generating board names.
- **series** (<code>[str](#str) | None</code>) – Optional series identifier for sequential board naming.
- **config** (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\] | None</code>) – Optional configuration object for boards created from this template.
- **config_template** – Optional template configuration for random generation.

**Returns:**

- <code>[BoardTemplate](#leadr.boards.domain.board_template.BoardTemplate)</code> – The created BoardTemplate domain entity.

**Raises:**

- <code>[EntityNotFoundError](#EntityNotFoundError)</code> – If the game doesn't exist.
- <code>[ValueError](#ValueError)</code> – If the game doesn't belong to the specified account or
  if name_template contains invalid placeholders.

<details class="example" open markdown="1">
<summary>Example</summary>

> > > template = await service.create_board_template(
> > > ... account_id=account.id,
> > > ... game_id=game.id,
> > > ... name="Weekly Speed Run Template",
> > > ... name_template="Week {series} - {year}",
> > > ... series="weekly",
> > > ... repeat_interval="7 days",
> > > ... next_run_at=datetime.now(UTC) + timedelta(days=7),
> > > ... is_active=True,
> > > ... )

</details>

####### `leadr.boards.services.board_template_service.BoardTemplateService.delete`

```python
delete(entity_id)
```

Soft-delete an entity.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – The ID of the entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the entity doesn't exist

####### `leadr.boards.services.board_template_service.BoardTemplateService.get_board_template`

```python
get_board_template(template_id)
```

Get a board template by its ID.

**Parameters:**

- **template_id** (<code>[BoardTemplateID](./common.md#leadr.common.domain.ids.BoardTemplateID)</code>) – The ID of the template to retrieve.

**Returns:**

- <code>[BoardTemplate](#leadr.boards.domain.board_template.BoardTemplate) | None</code> – The BoardTemplate domain entity if found, None otherwise.

####### `leadr.boards.services.board_template_service.BoardTemplateService.get_by_id`

```python
get_by_id(entity_id)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID](#uuid.UUID) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – The ID of the entity to retrieve

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.services.DomainEntityT) | None</code> – The domain entity if found, None otherwise

####### `leadr.boards.services.board_template_service.BoardTemplateService.get_by_id_or_raise`

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

####### `leadr.boards.services.board_template_service.BoardTemplateService.list_all`

```python
list_all()
```

List all non-deleted entities.

**Returns:**

- <code>[list](#list)\[[DomainEntityT](./common.md#leadr.common.services.DomainEntityT)\]</code> – List of domain entities

####### `leadr.boards.services.board_template_service.BoardTemplateService.list_board_templates_by_account`

```python
list_board_templates_by_account(account_id, *, pagination)
```

List all board templates for an account with pagination.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – The ID of the account to list templates for. If None, returns all
  templates (superadmin use case).
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (required).

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[BoardTemplate](#leadr.boards.domain.board_template.BoardTemplate)\]</code> – PaginatedResult containing BoardTemplate entities matching the filter criteria.

####### `leadr.boards.services.board_template_service.BoardTemplateService.list_board_templates_by_game`

```python
list_board_templates_by_game(account_id, game_id, *, pagination)
```

List all board templates for a specific game with pagination.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – The ID of the account. If None, returns templates from all accounts
  (superadmin use case).
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID)</code>) – The ID of the game to list templates for.
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (required).

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[BoardTemplate](#leadr.boards.domain.board_template.BoardTemplate)\]</code> – PaginatedResult containing BoardTemplate entities matching the filter criteria.

####### `leadr.boards.services.board_template_service.BoardTemplateService.repository`

```python
repository = repository if repository is not None else self._create_repository(session)
```

####### `leadr.boards.services.board_template_service.BoardTemplateService.soft_delete`

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

####### `leadr.boards.services.board_template_service.BoardTemplateService.update_board_template`

```python
update_board_template(template_id, **updates)
```

Update board template fields.

Accepts any fields to update as keyword arguments. Only fields
explicitly provided will be updated, allowing null values to
clear optional fields.

**Parameters:**

- **template_id** (<code>[BoardTemplateID](./common.md#leadr.common.domain.ids.BoardTemplateID)</code>) – The ID of the template to update.
- \*\***updates** (<code>[Any](#typing.Any)</code>) – Field names and values to update

**Returns:**

- <code>[BoardTemplate](#leadr.boards.domain.board_template.BoardTemplate)</code> – The updated BoardTemplate domain entity.

**Raises:**

- <code>[EntityNotFoundError](#EntityNotFoundError)</code> – If the template doesn't exist.
- <code>[ValueError](#ValueError)</code> – If name_template contains invalid placeholders.

###### `leadr.boards.services.board_template_service.logger`

```python
logger = get_logger(__name__)
```

##### `leadr.boards.services.dependencies`

Board service dependency injection.

**Functions:**

- [**get_board_ratio_config_service**](#leadr.boards.services.dependencies.get_board_ratio_config_service) – Get BoardRatioConfigService dependency.
- [**get_board_service**](#leadr.boards.services.dependencies.get_board_service) – Get BoardService dependency.
- [**get_board_state_service**](#leadr.boards.services.dependencies.get_board_state_service) – Get BoardStateService dependency.
- [**get_board_template_service**](#leadr.boards.services.dependencies.get_board_template_service) – Get BoardTemplateService dependency.
- [**get_run_entry_service**](#leadr.boards.services.dependencies.get_run_entry_service) – Get RunEntryService dependency.

**Attributes:**

- [**BoardRatioConfigServiceDep**](./boards.md#leadr.boards.services.dependencies.BoardRatioConfigServiceDep) –
- [**BoardServiceDep**](./boards.md#leadr.boards.services.dependencies.BoardServiceDep) –
- [**BoardStateServiceDep**](./boards.md#leadr.boards.services.dependencies.BoardStateServiceDep) –
- [**BoardTemplateServiceDep**](./boards.md#leadr.boards.services.dependencies.BoardTemplateServiceDep) –
- [**RunEntryServiceDep**](./boards.md#leadr.boards.services.dependencies.RunEntryServiceDep) –

###### `leadr.boards.services.dependencies.BoardRatioConfigServiceDep`

```python
BoardRatioConfigServiceDep = Annotated[BoardRatioConfigService, Depends(get_board_ratio_config_service)]
```

###### `leadr.boards.services.dependencies.BoardServiceDep`

```python
BoardServiceDep = Annotated[BoardService, Depends(get_board_service)]
```

###### `leadr.boards.services.dependencies.BoardStateServiceDep`

```python
BoardStateServiceDep = Annotated[BoardStateService, Depends(get_board_state_service)]
```

###### `leadr.boards.services.dependencies.BoardTemplateServiceDep`

```python
BoardTemplateServiceDep = Annotated[BoardTemplateService, Depends(get_board_template_service)]
```

###### `leadr.boards.services.dependencies.RunEntryServiceDep`

```python
RunEntryServiceDep = Annotated[RunEntryService, Depends(get_run_entry_service)]
```

###### `leadr.boards.services.dependencies.get_board_ratio_config_service`

```python
get_board_ratio_config_service(db)
```

Get BoardRatioConfigService dependency.

**Parameters:**

- **db** (<code>[DatabaseSession](./common.md#leadr.common.dependencies.DatabaseSession)</code>) – Database session from dependency injection

**Returns:**

- <code>[BoardRatioConfigService](#leadr.boards.services.board_ratio_config_service.BoardRatioConfigService)</code> – BoardRatioConfigService instance for handling ratio config operations

###### `leadr.boards.services.dependencies.get_board_service`

```python
get_board_service(db)
```

Get BoardService dependency.

**Parameters:**

- **db** (<code>[DatabaseSession](./common.md#leadr.common.dependencies.DatabaseSession)</code>) – Database session from dependency injection

**Returns:**

- <code>[BoardService](#leadr.boards.services.board_service.BoardService)</code> – BoardService instance for handling board operations

###### `leadr.boards.services.dependencies.get_board_state_service`

```python
get_board_state_service(db)
```

Get BoardStateService dependency.

**Parameters:**

- **db** (<code>[DatabaseSession](./common.md#leadr.common.dependencies.DatabaseSession)</code>) – Database session from dependency injection

**Returns:**

- <code>[BoardStateService](#leadr.boards.services.board_state_service.BoardStateService)</code> – BoardStateService instance for handling board state operations

###### `leadr.boards.services.dependencies.get_board_template_service`

```python
get_board_template_service(db)
```

Get BoardTemplateService dependency.

**Parameters:**

- **db** (<code>[DatabaseSession](./common.md#leadr.common.dependencies.DatabaseSession)</code>) – Database session from dependency injection

**Returns:**

- <code>[BoardTemplateService](#leadr.boards.services.board_template_service.BoardTemplateService)</code> – BoardTemplateService instance for handling board template operations

###### `leadr.boards.services.dependencies.get_run_entry_service`

```python
get_run_entry_service(db)
```

Get RunEntryService dependency.

**Parameters:**

- **db** (<code>[DatabaseSession](./common.md#leadr.common.dependencies.DatabaseSession)</code>) – Database session from dependency injection

**Returns:**

- <code>[RunEntryService](#leadr.boards.services.run_entry_service.RunEntryService)</code> – RunEntryService instance for handling run entry operations

##### `leadr.boards.services.repositories`

Board repository services.

**Classes:**

- [**BoardRatioConfigRepository**](./boards.md#leadr.boards.services.repositories.BoardRatioConfigRepository) – Repository for BoardRatioConfig persistence.
- [**BoardRepository**](./boards.md#leadr.boards.services.repositories.BoardRepository) – Board repository for managing board persistence.
- [**BoardStateRepository**](./boards.md#leadr.boards.services.repositories.BoardStateRepository) – BoardState repository for managing board state persistence.
- [**BoardTemplateRepository**](./boards.md#leadr.boards.services.repositories.BoardTemplateRepository) – BoardTemplate repository for managing board template persistence.
- [**RunEntryRepository**](./boards.md#leadr.boards.services.repositories.RunEntryRepository) – RunEntry repository for managing run entry persistence.

###### `leadr.boards.services.repositories.BoardRatioConfigRepository`

Bases: <code>[BaseRepository](./common.md#leadr.common.repositories.BaseRepository)\[[BoardRatioConfig](#leadr.boards.domain.board_ratio_config.BoardRatioConfig), [BoardRatioConfigORM](./boards.md#leadr.boards.adapters.orm.BoardRatioConfigORM)\]</code>

Repository for BoardRatioConfig persistence.

**Functions:**

- [**create**](./boards.md#leadr.boards.services.repositories.BoardRatioConfigRepository.create) – Create a new entity in the database.
- [**delete**](./boards.md#leadr.boards.services.repositories.BoardRatioConfigRepository.delete) – Soft delete an entity by setting its deleted_at timestamp.
- [**filter**](./boards.md#leadr.boards.services.repositories.BoardRatioConfigRepository.filter) – Filter ratio configs with optional criteria and pagination.
- [**get_by_board_id**](#leadr.boards.services.repositories.BoardRatioConfigRepository.get_by_board_id) – Get the ratio config for a specific board.
- [**get_by_id**](#leadr.boards.services.repositories.BoardRatioConfigRepository.get_by_id) – Get an entity by its ID.
- [**update**](./boards.md#leadr.boards.services.repositories.BoardRatioConfigRepository.update) – Update an existing entity in the database.

**Attributes:**

- [**SORTABLE_FIELDS**](#leadr.boards.services.repositories.BoardRatioConfigRepository.SORTABLE_FIELDS) –
- [**session**](./boards.md#leadr.boards.services.repositories.BoardRatioConfigRepository.session) –

####### `leadr.boards.services.repositories.BoardRatioConfigRepository.SORTABLE_FIELDS`

```python
SORTABLE_FIELDS = {'id', 'created_at', 'updated_at'}
```

####### `leadr.boards.services.repositories.BoardRatioConfigRepository.create`

```python
create(entity)
```

Create a new entity in the database.

**Parameters:**

- **entity** (<code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code>) – Domain entity to create

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code> – Created domain entity with refreshed data

####### `leadr.boards.services.repositories.BoardRatioConfigRepository.delete`

```python
delete(entity_id)
```

Soft delete an entity by setting its deleted_at timestamp.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – ID of entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

####### `leadr.boards.services.repositories.BoardRatioConfigRepository.filter`

```python
filter(board_id=None, *, pagination, **kwargs)
```

Filter ratio configs with optional criteria and pagination.

**Parameters:**

- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None</code>) – Optional board ID to filter by.
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (required).

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[BoardRatioConfig](#leadr.boards.domain.board_ratio_config.BoardRatioConfig)\]</code> – PaginatedResult containing ratio configs matching the filter criteria.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If sort field is not in SORTABLE_FIELDS.
- <code>[CursorValidationError](#CursorValidationError)</code> – If cursor is invalid or state doesn't match.

####### `leadr.boards.services.repositories.BoardRatioConfigRepository.get_by_board_id`

```python
get_by_board_id(board_id)
```

Get the ratio config for a specific board.

**Parameters:**

- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – The ID of the ratio board.

**Returns:**

- <code>[BoardRatioConfig](#leadr.boards.domain.board_ratio_config.BoardRatioConfig) | None</code> – BoardRatioConfig if found, None otherwise.

####### `leadr.boards.services.repositories.BoardRatioConfigRepository.get_by_id`

```python
get_by_id(entity_id, include_deleted=False)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – Entity ID to retrieve
- **include_deleted** (<code>[bool](#bool)</code>) – If True, include soft-deleted entities. Defaults to False.

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT) | None</code> – Domain entity if found, None otherwise

####### `leadr.boards.services.repositories.BoardRatioConfigRepository.session`

```python
session = session
```

####### `leadr.boards.services.repositories.BoardRatioConfigRepository.update`

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

###### `leadr.boards.services.repositories.BoardRepository`

Bases: <code>[BaseRepository](./common.md#leadr.common.repositories.BaseRepository)\[[Board](./boards.md#leadr.boards.domain.board.Board), [BoardORM](./boards.md#leadr.boards.adapters.orm.BoardORM)\]</code>

Board repository for managing board persistence.

**Functions:**

- [**count_boards_by_template**](#leadr.boards.services.repositories.BoardRepository.count_boards_by_template) – Count boards created from a specific template.
- [**create**](./boards.md#leadr.boards.services.repositories.BoardRepository.create) – Create a new entity in the database.
- [**delete**](./boards.md#leadr.boards.services.repositories.BoardRepository.delete) – Soft delete an entity by setting its deleted_at timestamp.
- [**filter**](./boards.md#leadr.boards.services.repositories.BoardRepository.filter) – Filter boards with optional criteria and pagination.
- [**get_by_id**](#leadr.boards.services.repositories.BoardRepository.get_by_id) – Get an entity by its ID.
- [**get_by_short_code**](#leadr.boards.services.repositories.BoardRepository.get_by_short_code) – Get board by short_code.
- [**update**](./boards.md#leadr.boards.services.repositories.BoardRepository.update) – Update an existing entity in the database.

**Attributes:**

- [**SORTABLE_FIELDS**](#leadr.boards.services.repositories.BoardRepository.SORTABLE_FIELDS) –
- [**session**](./boards.md#leadr.boards.services.repositories.BoardRepository.session) –

####### `leadr.boards.services.repositories.BoardRepository.SORTABLE_FIELDS`

```python
SORTABLE_FIELDS = {'id', 'name', 'slug', 'short_code', 'created_at', 'updated_at'}
```

####### `leadr.boards.services.repositories.BoardRepository.count_boards_by_template`

```python
count_boards_by_template(template_id)
```

Count boards created from a specific template.

**Parameters:**

- **template_id** (<code>[BoardTemplateID](./common.md#leadr.common.domain.ids.BoardTemplateID)</code>) – The template ID to count boards for

**Returns:**

- <code>[int](#int)</code> – Number of boards created from this template

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

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – ID of entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

####### `leadr.boards.services.repositories.BoardRepository.filter`

```python
filter(account_id=None, game_id=None, code=None, slug=None, is_active=None, is_published=None, starts_before=None, starts_after=None, ends_before=None, ends_after=None, *, pagination, **kwargs)
```

Filter boards with optional criteria and pagination.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – Optional account ID to filter by
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID) | None</code>) – Optional game ID to filter by
- **code** (<code>[str](#str) | None</code>) – Optional short code to filter by
- **slug** (<code>[str](#str) | None</code>) – Optional slug to filter by
- **is_active** (<code>[bool](#bool) | None</code>) – Optional filter for active status
- **is_published** (<code>[bool](#bool) | None</code>) – Optional filter for published status
- **starts_before** (<code>[datetime](#datetime.datetime) | None</code>) – Optional filter for boards starting before this time
- **starts_after** (<code>[datetime](#datetime.datetime) | None</code>) – Optional filter for boards starting after this time
- **ends_before** (<code>[datetime](#datetime.datetime) | None</code>) – Optional filter for boards ending before this time
- **ends_after** (<code>[datetime](#datetime.datetime) | None</code>) – Optional filter for boards ending after this time
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (required)

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[Board](./boards.md#leadr.boards.domain.board.Board)\]</code> – PaginatedResult containing boards matching the filter criteria

**Raises:**

- <code>[ValueError](#ValueError)</code> – If sort field is not in SORTABLE_FIELDS
- <code>[CursorValidationError](#CursorValidationError)</code> – If cursor is invalid or state doesn't match

####### `leadr.boards.services.repositories.BoardRepository.get_by_id`

```python
get_by_id(entity_id, include_deleted=False)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – Entity ID to retrieve
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

###### `leadr.boards.services.repositories.BoardStateRepository`

Bases: <code>[BaseRepository](./common.md#leadr.common.repositories.BaseRepository)\[[BoardState](#leadr.boards.domain.board_state.BoardState), [BoardStateORM](./boards.md#leadr.boards.adapters.orm.BoardStateORM)\]</code>

BoardState repository for managing board state persistence.

Board states represent the materialized ranking state for identities on boards.
Each identity has at most one state per board.

**Functions:**

- [**create**](./boards.md#leadr.boards.services.repositories.BoardStateRepository.create) – Create a new entity in the database.
- [**delete**](./boards.md#leadr.boards.services.repositories.BoardStateRepository.delete) – Soft delete an entity by setting its deleted_at timestamp.
- [**execute_around_query**](#leadr.boards.services.repositories.BoardStateRepository.execute_around_query) – Execute a query that returns states centered around a target state.
- [**execute_around_value_query**](#leadr.boards.services.repositories.BoardStateRepository.execute_around_value_query) – Execute a query that returns states centered around a hypothetical value.
- [**filter**](./boards.md#leadr.boards.services.repositories.BoardStateRepository.filter) – Filter board states with optional criteria and pagination.
- [**get_by_board_and_identity**](#leadr.boards.services.repositories.BoardStateRepository.get_by_board_and_identity) – Get a board state by board and identity.
- [**get_by_id**](#leadr.boards.services.repositories.BoardStateRepository.get_by_id) – Get an entity by its ID.
- [**get_rank**](#leadr.boards.services.repositories.BoardStateRepository.get_rank) – Compute rank for a board state using COUNT approach.
- [**update**](./boards.md#leadr.boards.services.repositories.BoardStateRepository.update) – Update an existing entity in the database.

**Attributes:**

- [**SORTABLE_FIELDS**](#leadr.boards.services.repositories.BoardStateRepository.SORTABLE_FIELDS) –
- [**session**](./boards.md#leadr.boards.services.repositories.BoardStateRepository.session) –

####### `leadr.boards.services.repositories.BoardStateRepository.SORTABLE_FIELDS`

```python
SORTABLE_FIELDS = {'id', 'primary_value', 'created_at', 'updated_at'}
```

####### `leadr.boards.services.repositories.BoardStateRepository.create`

```python
create(entity)
```

Create a new entity in the database.

**Parameters:**

- **entity** (<code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code>) – Domain entity to create

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code> – Created domain entity with refreshed data

####### `leadr.boards.services.repositories.BoardStateRepository.delete`

```python
delete(entity_id)
```

Soft delete an entity by setting its deleted_at timestamp.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – ID of entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

####### `leadr.boards.services.repositories.BoardStateRepository.execute_around_query`

```python
execute_around_query(board_id, target_state, sort_fields, limit, is_test=None)
```

Execute a query that returns states centered around a target state.

This method fetches states in a window around the target state, respecting
the sort order. For limit=5 with DESC sort, it returns 2 states above
(better ranked), the target, and 2 states below (worse ranked).

When the target is near an edge, the window adjusts to fill up to the limit.

**Parameters:**

- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – Board ID to filter by.
- **target_state** (<code>[BoardState](#leadr.boards.domain.board_state.BoardState)</code>) – The state to center results around.
- **sort_fields** (<code>[list](#list)\[[SortField](./common.md#leadr.common.domain.pagination.SortField)\]</code>) – Sort fields defining the ranking order.
- **limit** (<code>[int](#int)</code>) – Total number of states to return (including target).
- **is_test** (<code>[bool](#bool) | None</code>) – Optional filter for test entries.

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[BoardState](#leadr.boards.domain.board_state.BoardState)\]</code> – PaginatedResult with states centered around target.

####### `leadr.boards.services.repositories.BoardStateRepository.execute_around_value_query`

```python
execute_around_value_query(board_id, target_value, sort_fields, limit, is_test=None)
```

Execute a query that returns states centered around a hypothetical value.

Creates a synthetic placeholder state with the given value and returns it
along with neighboring states. The placeholder has is_placeholder=True and
uses sentinel nil UUIDs for id and identity_id.

**Parameters:**

- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – Board ID to filter by.
- **target_value** (<code>[float](#float)</code>) – The hypothetical score value to center results around.
- **sort_fields** (<code>[list](#list)\[[SortField](./common.md#leadr.common.domain.pagination.SortField)\]</code>) – Sort fields defining the ranking order.
- **limit** (<code>[int](#int)</code>) – Total number of states to return (including placeholder).
- **is_test** (<code>[bool](#bool) | None</code>) – Optional filter for test entries.

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[BoardState](#leadr.boards.domain.board_state.BoardState)\]</code> – PaginatedResult with states centered around value (including placeholder).

####### `leadr.boards.services.repositories.BoardStateRepository.filter`

```python
filter(board_id=None, identity_id=None, is_test=None, *, pagination, **kwargs)
```

Filter board states with optional criteria and pagination.

**Parameters:**

- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None</code>) – Optional board ID to filter by.
- **identity_id** (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID) | None</code>) – Optional identity ID to filter by.
- **is_test** (<code>[bool](#bool) | None</code>) – Optional filter for test entries (True=test only, False=prod only, None=all).
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (required).

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[BoardState](#leadr.boards.domain.board_state.BoardState)\]</code> – PaginatedResult containing board states matching the filter criteria.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If sort field is not in SORTABLE_FIELDS.
- <code>[CursorValidationError](#CursorValidationError)</code> – If cursor is invalid or state doesn't match.

####### `leadr.boards.services.repositories.BoardStateRepository.get_by_board_and_identity`

```python
get_by_board_and_identity(board_id, identity_id)
```

Get a board state by board and identity.

**Parameters:**

- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – The board ID to search for.
- **identity_id** (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) – The identity ID to search for.

**Returns:**

- <code>[BoardState](#leadr.boards.domain.board_state.BoardState) | None</code> – BoardState entity if found, None otherwise.

####### `leadr.boards.services.repositories.BoardStateRepository.get_by_id`

```python
get_by_id(entity_id, include_deleted=False)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – Entity ID to retrieve
- **include_deleted** (<code>[bool](#bool)</code>) – If True, include soft-deleted entities. Defaults to False.

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT) | None</code> – Domain entity if found, None otherwise

####### `leadr.boards.services.repositories.BoardStateRepository.get_rank`

```python
get_rank(state, sort_fields)
```

Compute rank for a board state using COUNT approach.

Counts how many entries rank better than the given state using the
same multi-field comparison logic used for sorting.

**Parameters:**

- **state** (<code>[BoardState](#leadr.boards.domain.board_state.BoardState)</code>) – BoardState to compute rank for.
- **sort_fields** (<code>[list](#list)\[[SortField](./common.md#leadr.common.domain.pagination.SortField)\]</code>) – Sort fields defining the ranking order.

**Returns:**

- <code>[int](#int)</code> – Rank (1-indexed, where 1 is the best).

####### `leadr.boards.services.repositories.BoardStateRepository.session`

```python
session = session
```

####### `leadr.boards.services.repositories.BoardStateRepository.update`

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

###### `leadr.boards.services.repositories.BoardTemplateRepository`

Bases: <code>[BaseRepository](./common.md#leadr.common.repositories.BaseRepository)\[[BoardTemplate](#leadr.boards.domain.board_template.BoardTemplate), [BoardTemplateORM](./boards.md#leadr.boards.adapters.orm.BoardTemplateORM)\]</code>

BoardTemplate repository for managing board template persistence.

**Functions:**

- [**create**](./boards.md#leadr.boards.services.repositories.BoardTemplateRepository.create) – Create a new entity in the database.
- [**delete**](./boards.md#leadr.boards.services.repositories.BoardTemplateRepository.delete) – Soft delete an entity by setting its deleted_at timestamp.
- [**filter**](./boards.md#leadr.boards.services.repositories.BoardTemplateRepository.filter) – Filter board templates by account and optional game with pagination.
- [**get_by_id**](#leadr.boards.services.repositories.BoardTemplateRepository.get_by_id) – Get an entity by its ID.
- [**update**](./boards.md#leadr.boards.services.repositories.BoardTemplateRepository.update) – Update an existing entity in the database.

**Attributes:**

- [**SORTABLE_FIELDS**](#leadr.boards.services.repositories.BoardTemplateRepository.SORTABLE_FIELDS) –
- [**session**](./boards.md#leadr.boards.services.repositories.BoardTemplateRepository.session) –

####### `leadr.boards.services.repositories.BoardTemplateRepository.SORTABLE_FIELDS`

```python
SORTABLE_FIELDS = {'id', 'name', 'created_at', 'updated_at'}
```

####### `leadr.boards.services.repositories.BoardTemplateRepository.create`

```python
create(entity)
```

Create a new entity in the database.

**Parameters:**

- **entity** (<code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code>) – Domain entity to create

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code> – Created domain entity with refreshed data

####### `leadr.boards.services.repositories.BoardTemplateRepository.delete`

```python
delete(entity_id)
```

Soft delete an entity by setting its deleted_at timestamp.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – ID of entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

####### `leadr.boards.services.repositories.BoardTemplateRepository.filter`

```python
filter(account_id=None, game_id=None, *, pagination, **kwargs)
```

Filter board templates by account and optional game with pagination.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID) | None</code>) – Optional account ID to filter by. If None, returns all templates
  (superadmin use case). Regular users should always pass account_id.
- **game_id** (<code>[GameID](./common.md#leadr.common.domain.ids.GameID) | None</code>) – OPTIONAL - Game ID to filter by
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (required)
- \*\***kwargs** (<code>[Any](#typing.Any)</code>) – Additional filter parameters (reserved for future use)

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[BoardTemplate](#leadr.boards.domain.board_template.BoardTemplate)\]</code> – PaginatedResult containing board templates matching the filter criteria

**Raises:**

- <code>[ValueError](#ValueError)</code> – If sort field is not in SORTABLE_FIELDS
- <code>[CursorValidationError](#CursorValidationError)</code> – If cursor is invalid or state doesn't match

####### `leadr.boards.services.repositories.BoardTemplateRepository.get_by_id`

```python
get_by_id(entity_id, include_deleted=False)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – Entity ID to retrieve
- **include_deleted** (<code>[bool](#bool)</code>) – If True, include soft-deleted entities. Defaults to False.

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT) | None</code> – Domain entity if found, None otherwise

####### `leadr.boards.services.repositories.BoardTemplateRepository.session`

```python
session = session
```

####### `leadr.boards.services.repositories.BoardTemplateRepository.update`

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

###### `leadr.boards.services.repositories.RunEntryRepository`

Bases: <code>[BaseRepository](./common.md#leadr.common.repositories.BaseRepository)\[[RunEntry](#leadr.boards.domain.run_entry.RunEntry), [RunEntryORM](./boards.md#leadr.boards.adapters.orm.RunEntryORM)\]</code>

RunEntry repository for managing run entry persistence.

Run entries represent individual scored submissions for RUN_RUNS boards
where every submission is ranked.

**Functions:**

- [**create**](./boards.md#leadr.boards.services.repositories.RunEntryRepository.create) – Create a new entity in the database.
- [**delete**](./boards.md#leadr.boards.services.repositories.RunEntryRepository.delete) – Soft delete an entity by setting its deleted_at timestamp.
- [**execute_around_query**](#leadr.boards.services.repositories.RunEntryRepository.execute_around_query) – Execute a query that returns entries centered around a target entry.
- [**execute_around_value_query**](#leadr.boards.services.repositories.RunEntryRepository.execute_around_value_query) – Execute a query that returns entries centered around a hypothetical value.
- [**filter**](./boards.md#leadr.boards.services.repositories.RunEntryRepository.filter) – Filter run entries with optional criteria and pagination.
- [**get_by_board_and_score_event**](#leadr.boards.services.repositories.RunEntryRepository.get_by_board_and_score_event) – Get a run entry by board and score event.
- [**get_by_id**](#leadr.boards.services.repositories.RunEntryRepository.get_by_id) – Get an entity by its ID.
- [**get_rank**](#leadr.boards.services.repositories.RunEntryRepository.get_rank) – Compute rank for a run entry using COUNT approach.
- [**update**](./boards.md#leadr.boards.services.repositories.RunEntryRepository.update) – Update an existing entity in the database.

**Attributes:**

- [**SORTABLE_FIELDS**](#leadr.boards.services.repositories.RunEntryRepository.SORTABLE_FIELDS) –
- [**session**](./boards.md#leadr.boards.services.repositories.RunEntryRepository.session) –

####### `leadr.boards.services.repositories.RunEntryRepository.SORTABLE_FIELDS`

```python
SORTABLE_FIELDS = {'id', 'primary_value', 'created_at', 'updated_at'}
```

####### `leadr.boards.services.repositories.RunEntryRepository.create`

```python
create(entity)
```

Create a new entity in the database.

**Parameters:**

- **entity** (<code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code>) – Domain entity to create

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code> – Created domain entity with refreshed data

####### `leadr.boards.services.repositories.RunEntryRepository.delete`

```python
delete(entity_id)
```

Soft delete an entity by setting its deleted_at timestamp.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – ID of entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

####### `leadr.boards.services.repositories.RunEntryRepository.execute_around_query`

```python
execute_around_query(board_id, target_entry, sort_fields, limit, is_test=None)
```

Execute a query that returns entries centered around a target entry.

This method fetches entries in a window around the target entry, respecting
the sort order. For limit=5 with DESC sort, it returns 2 entries above
(better ranked), the target, and 2 entries below (worse ranked).

When the target is near an edge, the window adjusts to fill up to the limit.

**Parameters:**

- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – Board ID to filter by.
- **target_entry** (<code>[RunEntry](#leadr.boards.domain.run_entry.RunEntry)</code>) – The entry to center results around.
- **sort_fields** (<code>[list](#list)\[[SortField](./common.md#leadr.common.domain.pagination.SortField)\]</code>) – Sort fields defining the ranking order.
- **limit** (<code>[int](#int)</code>) – Total number of entries to return (including target).
- **is_test** (<code>[bool](#bool) | None</code>) – Optional filter for test entries.

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[RunEntry](#leadr.boards.domain.run_entry.RunEntry)\]</code> – PaginatedResult with entries centered around target.

####### `leadr.boards.services.repositories.RunEntryRepository.execute_around_value_query`

```python
execute_around_value_query(board_id, target_value, sort_fields, limit, is_test=None)
```

Execute a query that returns entries centered around a hypothetical value.

Creates a synthetic placeholder entry with the given value and returns it
along with neighboring entries. The placeholder has is_placeholder=True and
uses sentinel nil UUIDs for id and identity_id.

**Parameters:**

- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – Board ID to filter by.
- **target_value** (<code>[float](#float)</code>) – The hypothetical score value to center results around.
- **sort_fields** (<code>[list](#list)\[[SortField](./common.md#leadr.common.domain.pagination.SortField)\]</code>) – Sort fields defining the ranking order.
- **limit** (<code>[int](#int)</code>) – Total number of entries to return (including placeholder).
- **is_test** (<code>[bool](#bool) | None</code>) – Optional filter for test entries.

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[RunEntry](#leadr.boards.domain.run_entry.RunEntry)\]</code> – PaginatedResult with entries centered around value (including placeholder).

####### `leadr.boards.services.repositories.RunEntryRepository.filter`

```python
filter(board_id=None, identity_id=None, is_test=None, *, pagination, **kwargs)
```

Filter run entries with optional criteria and pagination.

**Parameters:**

- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None</code>) – Optional board ID to filter by.
- **identity_id** (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID) | None</code>) – Optional identity ID to filter by.
- **is_test** (<code>[bool](#bool) | None</code>) – Optional filter for test entries (True=test only, False=prod only, None=all).
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (required).

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[RunEntry](#leadr.boards.domain.run_entry.RunEntry)\]</code> – PaginatedResult containing run entries matching the filter criteria.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If sort field is not in SORTABLE_FIELDS.
- <code>[CursorValidationError](#CursorValidationError)</code> – If cursor is invalid or state doesn't match.

####### `leadr.boards.services.repositories.RunEntryRepository.get_by_board_and_score_event`

```python
get_by_board_and_score_event(board_id, score_event_id)
```

Get a run entry by board and score event.

**Parameters:**

- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – The board ID to search for.
- **score_event_id** (<code>[ScoreEventID](./common.md#leadr.common.domain.ids.ScoreEventID)</code>) – The score event ID to search for.

**Returns:**

- <code>[RunEntry](#leadr.boards.domain.run_entry.RunEntry) | None</code> – RunEntry entity if found, None otherwise.

####### `leadr.boards.services.repositories.RunEntryRepository.get_by_id`

```python
get_by_id(entity_id, include_deleted=False)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – Entity ID to retrieve
- **include_deleted** (<code>[bool](#bool)</code>) – If True, include soft-deleted entities. Defaults to False.

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT) | None</code> – Domain entity if found, None otherwise

####### `leadr.boards.services.repositories.RunEntryRepository.get_rank`

```python
get_rank(entry, sort_fields)
```

Compute rank for a run entry using COUNT approach.

Counts how many entries rank better than the given entry using the
same multi-field comparison logic used for sorting.

**Parameters:**

- **entry** (<code>[RunEntry](#leadr.boards.domain.run_entry.RunEntry)</code>) – RunEntry to compute rank for.
- **sort_fields** (<code>[list](#list)\[[SortField](./common.md#leadr.common.domain.pagination.SortField)\]</code>) – Sort fields defining the ranking order.

**Returns:**

- <code>[int](#int)</code> – Rank (1-indexed, where 1 is the best).

####### `leadr.boards.services.repositories.RunEntryRepository.session`

```python
session = session
```

####### `leadr.boards.services.repositories.RunEntryRepository.update`

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

##### `leadr.boards.services.run_entry_service`

Run entry service for managing run entries.

**Classes:**

- [**RunEntryService**](#leadr.boards.services.run_entry_service.RunEntryService) – Service for managing run entries.

###### `leadr.boards.services.run_entry_service.RunEntryService`

```python
RunEntryService(session)
```

Service for managing run entries.

Run entries represent individual scored submissions for RUN_RUNS boards
where every submission is ranked.

**Functions:**

- [**create_run_entry**](#leadr.boards.services.run_entry_service.RunEntryService.create_run_entry) – Create a new run entry.
- [**get_by_board_and_score_event**](#leadr.boards.services.run_entry_service.RunEntryService.get_by_board_and_score_event) – Get a run entry by board and score event.
- [**get_by_id_or_raise**](#leadr.boards.services.run_entry_service.RunEntryService.get_by_id_or_raise) – Get a run entry by ID or raise if not found.
- [**get_run_entry**](#leadr.boards.services.run_entry_service.RunEntryService.get_run_entry) – Get a run entry by ID.
- [**list_run_entries**](#leadr.boards.services.run_entry_service.RunEntryService.list_run_entries) – List run entries with optional filtering.
- [**soft_delete**](#leadr.boards.services.run_entry_service.RunEntryService.soft_delete) – Soft delete a run entry.

**Attributes:**

- [**repository**](#leadr.boards.services.run_entry_service.RunEntryService.repository) –
- [**session**](#leadr.boards.services.run_entry_service.RunEntryService.session) –

**Parameters:**

- **session** (<code>[AsyncSession](#sqlalchemy.ext.asyncio.AsyncSession)</code>) – Database session for persistence operations.

####### `leadr.boards.services.run_entry_service.RunEntryService.create_run_entry`

```python
create_run_entry(*, board_id, identity_id, score_event_id, primary_value, player_name='', is_test=False, timezone=None, country=None, city=None, value_display=None, metadata=None)
```

Create a new run entry.

**Parameters:**

- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – The board this entry belongs to.
- **identity_id** (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID)</code>) – The identity that submitted this entry.
- **score_event_id** (<code>[ScoreEventID](./common.md#leadr.common.domain.ids.ScoreEventID)</code>) – The score event that created this entry.
- **primary_value** (<code>[float](#float)</code>) – The rankable value for this submission.
- **player_name** (<code>[str](#str)</code>) – Display name at submission time.
- **is_test** (<code>[bool](#bool)</code>) – Whether this is a test submission.
- **timezone** (<code>[str](#str) | None</code>) – Timezone from GeoIP.
- **country** (<code>[str](#str) | None</code>) – Country code from GeoIP.
- **city** (<code>[str](#str) | None</code>) – City name from GeoIP.
- **value_display** (<code>[str](#str) | None</code>) – Formatted display string.
- **metadata** (<code>[Any](#typing.Any) | None</code>) – Game-specific JSON metadata.

**Returns:**

- <code>[RunEntry](#leadr.boards.domain.run_entry.RunEntry)</code> – The created run entry.

####### `leadr.boards.services.run_entry_service.RunEntryService.get_by_board_and_score_event`

```python
get_by_board_and_score_event(board_id, score_event_id)
```

Get a run entry by board and score event.

**Parameters:**

- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID)</code>) – The board ID to search for.
- **score_event_id** (<code>[ScoreEventID](./common.md#leadr.common.domain.ids.ScoreEventID)</code>) – The score event ID to search for.

**Returns:**

- <code>[RunEntry](#leadr.boards.domain.run_entry.RunEntry) | None</code> – The run entry if found, None otherwise.

####### `leadr.boards.services.run_entry_service.RunEntryService.get_by_id_or_raise`

```python
get_by_id_or_raise(entry_id)
```

Get a run entry by ID or raise if not found.

**Parameters:**

- **entry_id** (<code>[RunEntryID](./common.md#leadr.common.domain.ids.RunEntryID)</code>) – The run entry ID to look up.

**Returns:**

- <code>[RunEntry](#leadr.boards.domain.run_entry.RunEntry)</code> – The run entry.

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the run entry does not exist.

####### `leadr.boards.services.run_entry_service.RunEntryService.get_run_entry`

```python
get_run_entry(entry_id)
```

Get a run entry by ID.

**Parameters:**

- **entry_id** (<code>[RunEntryID](./common.md#leadr.common.domain.ids.RunEntryID)</code>) – The run entry ID to look up.

**Returns:**

- <code>[RunEntry](#leadr.boards.domain.run_entry.RunEntry) | None</code> – The run entry if found, None otherwise.

####### `leadr.boards.services.run_entry_service.RunEntryService.list_run_entries`

```python
list_run_entries(*, board_id=None, identity_id=None, is_test=None, pagination=None, around_entry=None, around_value=None)
```

List run entries with optional filtering.

**Parameters:**

- **board_id** (<code>[BoardID](./common.md#leadr.common.domain.ids.BoardID) | None</code>) – Optional board ID to filter by.
- **identity_id** (<code>[IdentityID](./common.md#leadr.common.domain.ids.IdentityID) | None</code>) – Optional identity ID to filter by.
- **is_test** (<code>[bool](#bool) | None</code>) – Optional filter for test entries (True=test only, False=prod only, None=all).
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams) | None</code>) – Optional pagination parameters.
- **around_entry** (<code>[RunEntry](#leadr.boards.domain.run_entry.RunEntry) | None</code>) – Optional target entry to center results around.
- **around_value** (<code>[float](#float) | None</code>) – Optional value to center results around (creates placeholder).

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[RunEntry](#leadr.boards.domain.run_entry.RunEntry)\]</code> – Paginated list of run entries.

####### `leadr.boards.services.run_entry_service.RunEntryService.repository`

```python
repository = RunEntryRepository(session)
```

####### `leadr.boards.services.run_entry_service.RunEntryService.session`

```python
session = session
```

####### `leadr.boards.services.run_entry_service.RunEntryService.soft_delete`

```python
soft_delete(entry_id)
```

Soft delete a run entry.

**Parameters:**

- **entry_id** (<code>[RunEntryID](./common.md#leadr.common.domain.ids.RunEntryID)</code>) – The run entry ID to delete.

**Returns:**

- <code>[RunEntry](#leadr.boards.domain.run_entry.RunEntry)</code> – The deleted run entry.

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If the run entry does not exist.

##### `leadr.boards.services.short_code_generator`

Utility for generating unique short codes for boards.

Short codes are used for direct board sharing (e.g., example.com/board/ABC123XY).
They must be globally unique across all boards.

**Functions:**

- [**generate_short_code**](#leadr.boards.services.short_code_generator.generate_short_code) – Generate a random 8-character alphanumeric short code.
- [**generate_unique_short_code**](#leadr.boards.services.short_code_generator.generate_unique_short_code) – Generate a globally unique short code with collision retry logic.

**Attributes:**

- [**CHARSET**](#leadr.boards.services.short_code_generator.CHARSET) –
- [**CODE_LENGTH**](#leadr.boards.services.short_code_generator.CODE_LENGTH) –

###### `leadr.boards.services.short_code_generator.CHARSET`

```python
CHARSET = '23456789ABCDEFGHJKMNPQRSTUVWXYZ'
```

###### `leadr.boards.services.short_code_generator.CODE_LENGTH`

```python
CODE_LENGTH = 5
```

###### `leadr.boards.services.short_code_generator.generate_short_code`

```python
generate_short_code()
```

Generate a random 8-character alphanumeric short code.

Uses cryptographically strong random number generator for security.
Excludes ambiguous characters (0/O, 1/I/l) for better readability.

**Returns:**

- <code>[str](#str)</code> – 5-character uppercase alphanumeric code (e.g., 'A7B3X').

<details class="example" open markdown="1">
<summary>Example</summary>

> > > code = generate_short_code()
> > > len(code)
> > > 5
> > > code.isupper()
> > > True

</details>

###### `leadr.boards.services.short_code_generator.generate_unique_short_code`

```python
generate_unique_short_code(session, max_retries=10)
```

Generate a globally unique short code with collision retry logic.

Generates random codes and checks database for uniqueness. If a collision
is detected, retries up to max_retries times before raising an error.

**Parameters:**

- **session** (<code>[AsyncSession](#sqlalchemy.ext.asyncio.AsyncSession)</code>) – Database session for uniqueness checking.
- **max_retries** (<code>[int](#int)</code>) – Maximum number of generation attempts (default 10).

**Returns:**

- <code>[str](#str)</code> – Unique 5-character short code guaranteed not to exist in database.

**Raises:**

- <code>[RuntimeError](#RuntimeError)</code> – If unable to generate unique code within max_retries attempts.

<details class="example" open markdown="1">
<summary>Example</summary>

> > > code = await generate_unique_short_code(session)
> > >
> > > # Code is guaranteed to be unique in database

</details>
