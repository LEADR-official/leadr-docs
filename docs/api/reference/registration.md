### `leadr.registration`

**Modules:**

- [**adapters**](./registration.md#leadr.registration.adapters) –
- [**api**](./registration.md#leadr.registration.api) –
- [**domain**](./registration.md#leadr.registration.domain) –
- [**services**](./registration.md#leadr.registration.services) –

#### `leadr.registration.adapters`

**Modules:**

- [**orm**](./registration.md#leadr.registration.adapters.orm) – Registration ORM models.

##### `leadr.registration.adapters.orm`

Registration ORM models.

**Classes:**

- [**JamCodeORM**](./registration.md#leadr.registration.adapters.orm.JamCodeORM) – Jam Code ORM model.
- [**JamCodeRedemptionORM**](./registration.md#leadr.registration.adapters.orm.JamCodeRedemptionORM) – Jam Code Redemption ORM model.
- [**VerificationCodeORM**](./registration.md#leadr.registration.adapters.orm.VerificationCodeORM) – Verification Code ORM model.
- [**VerificationCodeStatusEnum**](./registration.md#leadr.registration.adapters.orm.VerificationCodeStatusEnum) – Verification code status enum for database.
- [**VerificationCodeTypeEnum**](./registration.md#leadr.registration.adapters.orm.VerificationCodeTypeEnum) – Verification code type enum for database.

###### `leadr.registration.adapters.orm.JamCodeORM`

Bases: <code>[Base](./common.md#leadr.common.orm.Base)</code>

Jam Code ORM model.

Represents a promotional code in the database.
Maps to the jam_codes table.
Used for tracking game jam codes, marketing campaigns, and referrals.

**Functions:**

- [**from_domain**](#leadr.registration.adapters.orm.JamCodeORM.from_domain) – Convert domain entity to ORM model.
- [**to_domain**](#leadr.registration.adapters.orm.JamCodeORM.to_domain) – Convert ORM model to domain entity.

**Attributes:**

- [**active**](./registration.md#leadr.registration.adapters.orm.JamCodeORM.active) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[bool](#bool)\]</code>) –
- [**code**](./registration.md#leadr.registration.adapters.orm.JamCodeORM.code) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**created_at**](#leadr.registration.adapters.orm.JamCodeORM.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**current_uses**](#leadr.registration.adapters.orm.JamCodeORM.current_uses) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[int](#int)\]</code>) –
- [**deleted_at**](#leadr.registration.adapters.orm.JamCodeORM.deleted_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[nullable_timestamp](#leadr.common.orm.nullable_timestamp)\]</code>) –
- [**description**](./registration.md#leadr.registration.adapters.orm.JamCodeORM.description) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**expires_at**](#leadr.registration.adapters.orm.JamCodeORM.expires_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime) | None\]</code>) –
- [**features**](./registration.md#leadr.registration.adapters.orm.JamCodeORM.features) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[dict](#dict)\[[str](#str), [Any](#typing.Any)\]\]</code>) –
- [**id**](./registration.md#leadr.registration.adapters.orm.JamCodeORM.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**max_uses**](#leadr.registration.adapters.orm.JamCodeORM.max_uses) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[int](#int) | None\]</code>) –
- [**updated_at**](#leadr.registration.adapters.orm.JamCodeORM.updated_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –

####### `leadr.registration.adapters.orm.JamCodeORM.active`

```python
active: Mapped[bool] = mapped_column(Boolean, nullable=False, default=True, server_default='true')
```

####### `leadr.registration.adapters.orm.JamCodeORM.code`

```python
code: Mapped[str] = mapped_column(String(50), nullable=False, unique=True, index=True)
```

####### `leadr.registration.adapters.orm.JamCodeORM.created_at`

```python
created_at: Mapped[timestamp]
```

####### `leadr.registration.adapters.orm.JamCodeORM.current_uses`

```python
current_uses: Mapped[int] = mapped_column(Integer, nullable=False, default=0, server_default='0')
```

####### `leadr.registration.adapters.orm.JamCodeORM.deleted_at`

```python
deleted_at: Mapped[nullable_timestamp]
```

####### `leadr.registration.adapters.orm.JamCodeORM.description`

```python
description: Mapped[str] = mapped_column(String, nullable=False)
```

####### `leadr.registration.adapters.orm.JamCodeORM.expires_at`

```python
expires_at: Mapped[datetime | None] = mapped_column(DateTime(timezone=True), nullable=True)
```

####### `leadr.registration.adapters.orm.JamCodeORM.features`

```python
features: Mapped[dict[str, Any]] = mapped_column(JSON, nullable=False, default={}, server_default='{}')
```

####### `leadr.registration.adapters.orm.JamCodeORM.from_domain`

```python
from_domain(domain)
```

Convert domain entity to ORM model.

**Parameters:**

- **domain** (<code>[JamCode](#leadr.registration.domain.jam_code.JamCode)</code>) – The domain entity to convert.

**Returns:**

- <code>[JamCodeORM](./registration.md#leadr.registration.adapters.orm.JamCodeORM)</code> – The ORM model instance.

####### `leadr.registration.adapters.orm.JamCodeORM.id`

```python
id: Mapped[uuid_pk]
```

####### `leadr.registration.adapters.orm.JamCodeORM.max_uses`

```python
max_uses: Mapped[int | None] = mapped_column(Integer, nullable=True)
```

####### `leadr.registration.adapters.orm.JamCodeORM.to_domain`

```python
to_domain()
```

Convert ORM model to domain entity.

**Returns:**

- <code>[JamCode](#leadr.registration.domain.jam_code.JamCode)</code> – The domain entity instance.

####### `leadr.registration.adapters.orm.JamCodeORM.updated_at`

```python
updated_at: Mapped[timestamp] = mapped_column(onupdate=(func.now()))
```

###### `leadr.registration.adapters.orm.JamCodeRedemptionORM`

Bases: <code>[Base](./common.md#leadr.common.orm.Base)</code>

Jam Code Redemption ORM model.

Represents a single use of a jam code during registration.
Maps to the jam_code_redemptions table with foreign keys to jam_codes and accounts.
Tracks which account redeemed which code and when.

**Functions:**

- [**from_domain**](#leadr.registration.adapters.orm.JamCodeRedemptionORM.from_domain) – Convert domain entity to ORM model.
- [**to_domain**](#leadr.registration.adapters.orm.JamCodeRedemptionORM.to_domain) – Convert ORM model to domain entity.

**Attributes:**

- [**account_id**](#leadr.registration.adapters.orm.JamCodeRedemptionORM.account_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**created_at**](#leadr.registration.adapters.orm.JamCodeRedemptionORM.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**deleted_at**](#leadr.registration.adapters.orm.JamCodeRedemptionORM.deleted_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[nullable_timestamp](#leadr.common.orm.nullable_timestamp)\]</code>) –
- [**id**](./registration.md#leadr.registration.adapters.orm.JamCodeRedemptionORM.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**jam_code_id**](#leadr.registration.adapters.orm.JamCodeRedemptionORM.jam_code_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID)\]</code>) –
- [**meta**](./registration.md#leadr.registration.adapters.orm.JamCodeRedemptionORM.meta) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[dict](#dict)\[[str](#str), [Any](#typing.Any)\]\]</code>) –
- [**redeemed_at**](#leadr.registration.adapters.orm.JamCodeRedemptionORM.redeemed_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime)\]</code>) –
- [**updated_at**](#leadr.registration.adapters.orm.JamCodeRedemptionORM.updated_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –

####### `leadr.registration.adapters.orm.JamCodeRedemptionORM.account_id`

```python
account_id: Mapped[UUID] = mapped_column(ForeignKey('accounts.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.registration.adapters.orm.JamCodeRedemptionORM.created_at`

```python
created_at: Mapped[timestamp]
```

####### `leadr.registration.adapters.orm.JamCodeRedemptionORM.deleted_at`

```python
deleted_at: Mapped[nullable_timestamp]
```

####### `leadr.registration.adapters.orm.JamCodeRedemptionORM.from_domain`

```python
from_domain(domain)
```

Convert domain entity to ORM model.

**Parameters:**

- **domain** (<code>[JamCodeRedemption](#leadr.registration.domain.jam_code_redemption.JamCodeRedemption)</code>) – The domain entity to convert.

**Returns:**

- <code>[JamCodeRedemptionORM](./registration.md#leadr.registration.adapters.orm.JamCodeRedemptionORM)</code> – The ORM model instance.

####### `leadr.registration.adapters.orm.JamCodeRedemptionORM.id`

```python
id: Mapped[uuid_pk]
```

####### `leadr.registration.adapters.orm.JamCodeRedemptionORM.jam_code_id`

```python
jam_code_id: Mapped[UUID] = mapped_column(ForeignKey('jam_codes.id', ondelete='CASCADE'), nullable=False, index=True)
```

####### `leadr.registration.adapters.orm.JamCodeRedemptionORM.meta`

```python
meta: Mapped[dict[str, Any]] = mapped_column(JSON, nullable=False, default={}, server_default='{}')
```

####### `leadr.registration.adapters.orm.JamCodeRedemptionORM.redeemed_at`

```python
redeemed_at: Mapped[datetime] = mapped_column(DateTime(timezone=True), nullable=False)
```

####### `leadr.registration.adapters.orm.JamCodeRedemptionORM.to_domain`

```python
to_domain()
```

Convert ORM model to domain entity.

**Returns:**

- <code>[JamCodeRedemption](#leadr.registration.domain.jam_code_redemption.JamCodeRedemption)</code> – The domain entity instance.

####### `leadr.registration.adapters.orm.JamCodeRedemptionORM.updated_at`

```python
updated_at: Mapped[timestamp] = mapped_column(onupdate=(func.now()))
```

###### `leadr.registration.adapters.orm.VerificationCodeORM`

Bases: <code>[Base](./common.md#leadr.common.orm.Base)</code>

Verification Code ORM model.

Represents an email verification code in the database.
Maps to the verification_codes table.
Used during account registration to verify email ownership.

**Functions:**

- [**from_domain**](#leadr.registration.adapters.orm.VerificationCodeORM.from_domain) – Convert domain entity to ORM model.
- [**to_domain**](#leadr.registration.adapters.orm.VerificationCodeORM.to_domain) – Convert ORM model to domain entity.

**Attributes:**

- [**code**](./registration.md#leadr.registration.adapters.orm.VerificationCodeORM.code) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**code_type**](#leadr.registration.adapters.orm.VerificationCodeORM.code_type) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[VerificationCodeTypeEnum](./registration.md#leadr.registration.adapters.orm.VerificationCodeTypeEnum)\]</code>) –
- [**created_at**](#leadr.registration.adapters.orm.VerificationCodeORM.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**deleted_at**](#leadr.registration.adapters.orm.VerificationCodeORM.deleted_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[nullable_timestamp](#leadr.common.orm.nullable_timestamp)\]</code>) –
- [**email**](./registration.md#leadr.registration.adapters.orm.VerificationCodeORM.email) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**expires_at**](#leadr.registration.adapters.orm.VerificationCodeORM.expires_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime)\]</code>) –
- [**id**](./registration.md#leadr.registration.adapters.orm.VerificationCodeORM.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**status**](./registration.md#leadr.registration.adapters.orm.VerificationCodeORM.status) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[VerificationCodeStatusEnum](./registration.md#leadr.registration.adapters.orm.VerificationCodeStatusEnum)\]</code>) –
- [**updated_at**](#leadr.registration.adapters.orm.VerificationCodeORM.updated_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**used_at**](#leadr.registration.adapters.orm.VerificationCodeORM.used_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime) | None\]</code>) –
- [**user_id**](#leadr.registration.adapters.orm.VerificationCodeORM.user_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[UUID](#uuid.UUID) | None\]</code>) –

####### `leadr.registration.adapters.orm.VerificationCodeORM.code`

```python
code: Mapped[str] = mapped_column(String(6), nullable=False)
```

####### `leadr.registration.adapters.orm.VerificationCodeORM.code_type`

```python
code_type: Mapped[VerificationCodeTypeEnum] = mapped_column(Enum(VerificationCodeTypeEnum, name='verification_code_type', native_enum=True, values_callable=(lambda x: [(e.value) for e in x])), nullable=False, default=(VerificationCodeTypeEnum.REGISTRATION), server_default='registration')
```

####### `leadr.registration.adapters.orm.VerificationCodeORM.created_at`

```python
created_at: Mapped[timestamp]
```

####### `leadr.registration.adapters.orm.VerificationCodeORM.deleted_at`

```python
deleted_at: Mapped[nullable_timestamp]
```

####### `leadr.registration.adapters.orm.VerificationCodeORM.email`

```python
email: Mapped[str] = mapped_column(String, nullable=False, index=True)
```

####### `leadr.registration.adapters.orm.VerificationCodeORM.expires_at`

```python
expires_at: Mapped[datetime] = mapped_column(DateTime(timezone=True), nullable=False, index=True)
```

####### `leadr.registration.adapters.orm.VerificationCodeORM.from_domain`

```python
from_domain(domain)
```

Convert domain entity to ORM model.

**Parameters:**

- **domain** (<code>[VerificationCode](#leadr.registration.domain.verification_code.VerificationCode)</code>) – The domain entity to convert.

**Returns:**

- <code>[VerificationCodeORM](./registration.md#leadr.registration.adapters.orm.VerificationCodeORM)</code> – The ORM model instance.

####### `leadr.registration.adapters.orm.VerificationCodeORM.id`

```python
id: Mapped[uuid_pk]
```

####### `leadr.registration.adapters.orm.VerificationCodeORM.status`

```python
status: Mapped[VerificationCodeStatusEnum] = mapped_column(Enum(VerificationCodeStatusEnum, name='verification_code_status', native_enum=True, values_callable=(lambda x: [(e.value) for e in x])), nullable=False, default=(VerificationCodeStatusEnum.PENDING), server_default='pending')
```

####### `leadr.registration.adapters.orm.VerificationCodeORM.to_domain`

```python
to_domain()
```

Convert ORM model to domain entity.

**Returns:**

- <code>[VerificationCode](#leadr.registration.domain.verification_code.VerificationCode)</code> – The domain entity instance.

####### `leadr.registration.adapters.orm.VerificationCodeORM.updated_at`

```python
updated_at: Mapped[timestamp] = mapped_column(onupdate=(func.now()))
```

####### `leadr.registration.adapters.orm.VerificationCodeORM.used_at`

```python
used_at: Mapped[datetime | None] = mapped_column(DateTime(timezone=True), nullable=True)
```

####### `leadr.registration.adapters.orm.VerificationCodeORM.user_id`

```python
user_id: Mapped[UUID | None] = mapped_column(ForeignKey('users.id', ondelete='CASCADE'), nullable=True, index=True)
```

###### `leadr.registration.adapters.orm.VerificationCodeStatusEnum`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Verification code status enum for database.

**Attributes:**

- [**EXPIRED**](./registration.md#leadr.registration.adapters.orm.VerificationCodeStatusEnum.EXPIRED) –
- [**PENDING**](./registration.md#leadr.registration.adapters.orm.VerificationCodeStatusEnum.PENDING) –
- [**USED**](./registration.md#leadr.registration.adapters.orm.VerificationCodeStatusEnum.USED) –

####### `leadr.registration.adapters.orm.VerificationCodeStatusEnum.EXPIRED`

```python
EXPIRED = 'expired'
```

####### `leadr.registration.adapters.orm.VerificationCodeStatusEnum.PENDING`

```python
PENDING = 'pending'
```

####### `leadr.registration.adapters.orm.VerificationCodeStatusEnum.USED`

```python
USED = 'used'
```

###### `leadr.registration.adapters.orm.VerificationCodeTypeEnum`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Verification code type enum for database.

**Attributes:**

- [**INVITE**](./registration.md#leadr.registration.adapters.orm.VerificationCodeTypeEnum.INVITE) –
- [**REGISTRATION**](./registration.md#leadr.registration.adapters.orm.VerificationCodeTypeEnum.REGISTRATION) –

####### `leadr.registration.adapters.orm.VerificationCodeTypeEnum.INVITE`

```python
INVITE = 'invite'
```

####### `leadr.registration.adapters.orm.VerificationCodeTypeEnum.REGISTRATION`

```python
REGISTRATION = 'registration'
```

#### `leadr.registration.api`

**Modules:**

- [**routes**](./registration.md#leadr.registration.api.routes) – Public registration API routes.
- [**schemas**](./registration.md#leadr.registration.api.schemas) – API schemas for registration endpoints.

##### `leadr.registration.api.routes`

Public registration API routes.

**Functions:**

- [**complete_registration**](#leadr.registration.api.routes.complete_registration) – Complete registration or invite acceptance.
- [**create_jam_code**](#leadr.registration.api.routes.create_jam_code) – Create a new jam code (superadmin only).
- [**get_jam_code**](#leadr.registration.api.routes.get_jam_code) – Get a specific jam code by ID (superadmin only).
- [**initiate_registration**](#leadr.registration.api.routes.initiate_registration) – Initiate registration by sending a verification code to the provided email.
- [**invite_user**](#leadr.registration.api.routes.invite_user) – Invite a user to the authenticated admin's account.
- [**list_jam_codes**](#leadr.registration.api.routes.list_jam_codes) – List all jam codes (superadmin only).
- [**resend_verification_code**](#leadr.registration.api.routes.resend_verification_code) – Resend a verification code to the provided email.
- [**update_jam_code**](#leadr.registration.api.routes.update_jam_code) – Update a jam code (superadmin only).
- [**verify_code**](#leadr.registration.api.routes.verify_code) – Verify an email verification code and return a temporary token.

**Attributes:**

- [**public_router**](#leadr.registration.api.routes.public_router) –
- [**router**](./registration.md#leadr.registration.api.routes.router) –

###### `leadr.registration.api.routes.complete_registration`

```python
complete_registration(request, registration_service)
```

Complete registration or invite acceptance.

This endpoint handles two flows based on the verification token type:

Registration flow (new account):

- Creates account with the specified name and slug
- Creates user as account owner
- Creates API key for CLI authentication
- Optionally redeems jam code

Invite flow (joining existing account):

- Activates the invited user (changes status from INVITED to ACTIVE)
- Creates API key for CLI authentication
- account_name and jam_code are ignored

The API key is returned in plaintext and should be stored securely by the client.

###### `leadr.registration.api.routes.create_jam_code`

```python
create_jam_code(request, jam_code_service, auth)
```

Create a new jam code (superadmin only).

Jam codes can be used for promotional campaigns, game jams, or referral tracking.
They can optionally have usage limits, expiration dates, and custom features.

###### `leadr.registration.api.routes.get_jam_code`

```python
get_jam_code(jam_code_id, jam_code_service, auth)
```

Get a specific jam code by ID (superadmin only).

###### `leadr.registration.api.routes.initiate_registration`

```python
initiate_registration(request, verification_service)
```

Initiate registration by sending a verification code to the provided email.

This endpoint is publicly accessible and requires no authentication.
A 6-character verification code will be sent to the email address.

###### `leadr.registration.api.routes.invite_user`

```python
invite_user(request, invite_service, auth)
```

Invite a user to the authenticated admin's account.

Creates a user with INVITED status and sends an invite email with
a verification code. If the user already exists with INVITED status,
resends the invite (invalidates old code, sends new one).

Requires admin authentication.

###### `leadr.registration.api.routes.list_jam_codes`

```python
list_jam_codes(jam_code_service, auth, pagination)
```

List all jam codes (superadmin only).

Returns a paginated list of all jam codes, including their usage statistics.

###### `leadr.registration.api.routes.public_router`

```python
public_router = APIRouter(prefix='/register')
```

###### `leadr.registration.api.routes.resend_verification_code`

```python
resend_verification_code(request, verification_service)
```

Resend a verification code to the provided email.

This endpoint invalidates any existing codes for the email and sends a new one.

###### `leadr.registration.api.routes.router`

```python
router = APIRouter()
```

###### `leadr.registration.api.routes.update_jam_code`

```python
update_jam_code(jam_code_id, request, jam_code_service, auth)
```

Update a jam code (superadmin only).

Can update description, features, max uses, active status, and expiration.

###### `leadr.registration.api.routes.verify_code`

```python
verify_code(request, verification_service)
```

Verify an email verification code and return a temporary token.

This endpoint validates the verification code and returns a short-lived
token that can be used to complete the registration process. The response
includes the type (REGISTRATION or INVITE) so the client can determine
which fields to prompt for.

##### `leadr.registration.api.schemas`

API schemas for registration endpoints.

**Classes:**

- [**CompleteRegistrationRequest**](./registration.md#leadr.registration.api.schemas.CompleteRegistrationRequest) – Request to complete registration or invite acceptance.
- [**CompleteRegistrationResponse**](./registration.md#leadr.registration.api.schemas.CompleteRegistrationResponse) – Response after completing registration or invite acceptance.
- [**CreateJamCodeRequest**](./registration.md#leadr.registration.api.schemas.CreateJamCodeRequest) – Request to create a new jam code.
- [**InitiateRegistrationRequest**](./registration.md#leadr.registration.api.schemas.InitiateRegistrationRequest) – Request to initiate registration by sending verification code.
- [**InitiateRegistrationResponse**](./registration.md#leadr.registration.api.schemas.InitiateRegistrationResponse) – Response after initiating registration.
- [**InviteUserRequest**](./registration.md#leadr.registration.api.schemas.InviteUserRequest) – Request to invite a user to an account.
- [**InviteUserResponse**](./registration.md#leadr.registration.api.schemas.InviteUserResponse) – Response after inviting a user.
- [**JamCodeRedemptionResponse**](./registration.md#leadr.registration.api.schemas.JamCodeRedemptionResponse) – Response representing a jam code redemption.
- [**JamCodeResponse**](./registration.md#leadr.registration.api.schemas.JamCodeResponse) – Response representing a jam code.
- [**UpdateJamCodeRequest**](./registration.md#leadr.registration.api.schemas.UpdateJamCodeRequest) – Request to update a jam code.
- [**VerifyCodeRequest**](./registration.md#leadr.registration.api.schemas.VerifyCodeRequest) – Request to verify an email verification code.
- [**VerifyCodeResponse**](./registration.md#leadr.registration.api.schemas.VerifyCodeResponse) – Response after verifying a code.

###### `leadr.registration.api.schemas.CompleteRegistrationRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request to complete registration or invite acceptance.

Used for both new account registration and invited user activation.
The verification token type determines which flow is executed.

**Functions:**

- [**normalize_display_name**](#leadr.registration.api.schemas.CompleteRegistrationRequest.normalize_display_name) – Convert empty/whitespace strings to None.

**Attributes:**

- [**account_name**](#leadr.registration.api.schemas.CompleteRegistrationRequest.account_name) (<code>[str](#str) | None</code>) –
- [**account_slug**](#leadr.registration.api.schemas.CompleteRegistrationRequest.account_slug) (<code>[str](#str) | None</code>) –
- [**display_name**](#leadr.registration.api.schemas.CompleteRegistrationRequest.display_name) (<code>[str](#str) | None</code>) –
- [**jam_code**](#leadr.registration.api.schemas.CompleteRegistrationRequest.jam_code) (<code>[str](#str) | None</code>) –
- [**verification_token**](#leadr.registration.api.schemas.CompleteRegistrationRequest.verification_token) (<code>[str](#str)</code>) –

####### `leadr.registration.api.schemas.CompleteRegistrationRequest.account_name`

```python
account_name: str | None = Field(default=None, description='Name for the new account (required for registration, ignored for invite)')
```

####### `leadr.registration.api.schemas.CompleteRegistrationRequest.account_slug`

```python
account_slug: str | None = Field(default=None, description='Optional URL slug (auto-generated if not provided)')
```

####### `leadr.registration.api.schemas.CompleteRegistrationRequest.display_name`

```python
display_name: str | None = Field(default=None, description='Optional display name for user (auto-generated from email if not provided)')
```

####### `leadr.registration.api.schemas.CompleteRegistrationRequest.jam_code`

```python
jam_code: str | None = Field(default=None, description='Optional jam/promo code')
```

####### `leadr.registration.api.schemas.CompleteRegistrationRequest.normalize_display_name`

```python
normalize_display_name(value)
```

Convert empty/whitespace strings to None.

####### `leadr.registration.api.schemas.CompleteRegistrationRequest.verification_token`

```python
verification_token: str = Field(description='Token from code verification step')
```

###### `leadr.registration.api.schemas.CompleteRegistrationResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response after completing registration or invite acceptance.

**Functions:**

- [**from_domain**](#leadr.registration.api.schemas.CompleteRegistrationResponse.from_domain) – Create response from domain entities.

**Attributes:**

- [**account_id**](#leadr.registration.api.schemas.CompleteRegistrationResponse.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**account_name**](#leadr.registration.api.schemas.CompleteRegistrationResponse.account_name) (<code>[str](#str)</code>) –
- [**account_slug**](#leadr.registration.api.schemas.CompleteRegistrationResponse.account_slug) (<code>[str](#str)</code>) –
- [**api_key**](#leadr.registration.api.schemas.CompleteRegistrationResponse.api_key) (<code>[str](#str)</code>) –
- [**display_name**](#leadr.registration.api.schemas.CompleteRegistrationResponse.display_name) (<code>[str](#str)</code>) –

####### `leadr.registration.api.schemas.CompleteRegistrationResponse.account_id`

```python
account_id: AccountID = Field(description='ID of the created account')
```

####### `leadr.registration.api.schemas.CompleteRegistrationResponse.account_name`

```python
account_name: str = Field(description='Name of the account')
```

####### `leadr.registration.api.schemas.CompleteRegistrationResponse.account_slug`

```python
account_slug: str = Field(description='URL slug of the account')
```

####### `leadr.registration.api.schemas.CompleteRegistrationResponse.api_key`

```python
api_key: str = Field(description='API key for authentication')
```

####### `leadr.registration.api.schemas.CompleteRegistrationResponse.display_name`

```python
display_name: str = Field(description='Display name of the created user')
```

####### `leadr.registration.api.schemas.CompleteRegistrationResponse.from_domain`

```python
from_domain(account, user, api_key)
```

Create response from domain entities.

**Parameters:**

- **account** – Account domain entity.
- **user** – User domain entity.
- **api_key** (<code>[str](#str)</code>) – API key string.

**Returns:**

- <code>[CompleteRegistrationResponse](./registration.md#leadr.registration.api.schemas.CompleteRegistrationResponse)</code> – CompleteRegistrationResponse instance.

###### `leadr.registration.api.schemas.CreateJamCodeRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request to create a new jam code.

**Attributes:**

- [**code**](./registration.md#leadr.registration.api.schemas.CreateJamCodeRequest.code) (<code>[str](#str)</code>) –
- [**description**](./registration.md#leadr.registration.api.schemas.CreateJamCodeRequest.description) (<code>[str](#str)</code>) –
- [**expires_at**](#leadr.registration.api.schemas.CreateJamCodeRequest.expires_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**features**](./registration.md#leadr.registration.api.schemas.CreateJamCodeRequest.features) (<code>[dict](#dict)</code>) –
- [**max_uses**](#leadr.registration.api.schemas.CreateJamCodeRequest.max_uses) (<code>[int](#int) | None</code>) –

####### `leadr.registration.api.schemas.CreateJamCodeRequest.code`

```python
code: str = Field(description='Alphanumeric code (3-50 characters)', min_length=3, max_length=50)
```

####### `leadr.registration.api.schemas.CreateJamCodeRequest.description`

```python
description: str = Field(description='Human-readable description')
```

####### `leadr.registration.api.schemas.CreateJamCodeRequest.expires_at`

```python
expires_at: datetime | None = Field(default=None, description='Expiration date (null = never)')
```

####### `leadr.registration.api.schemas.CreateJamCodeRequest.features`

```python
features: dict = Field(default_factory=dict, description='Features/config for this code')
```

####### `leadr.registration.api.schemas.CreateJamCodeRequest.max_uses`

```python
max_uses: int | None = Field(default=None, description='Maximum redemptions (null = unlimited)')
```

###### `leadr.registration.api.schemas.InitiateRegistrationRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request to initiate registration by sending verification code.

**Attributes:**

- [**email**](./registration.md#leadr.registration.api.schemas.InitiateRegistrationRequest.email) (<code>[EmailStr](#pydantic.EmailStr)</code>) –

####### `leadr.registration.api.schemas.InitiateRegistrationRequest.email`

```python
email: EmailStr = Field(description='Email address to send verification code to')
```

###### `leadr.registration.api.schemas.InitiateRegistrationResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response after initiating registration.

**Attributes:**

- [**code_expires_in**](#leadr.registration.api.schemas.InitiateRegistrationResponse.code_expires_in) (<code>[int](#int)</code>) –
- [**message**](./registration.md#leadr.registration.api.schemas.InitiateRegistrationResponse.message) (<code>[str](#str)</code>) –

####### `leadr.registration.api.schemas.InitiateRegistrationResponse.code_expires_in`

```python
code_expires_in: int = Field(description='Seconds until the code expires')
```

####### `leadr.registration.api.schemas.InitiateRegistrationResponse.message`

```python
message: str = Field(description='Success message')
```

###### `leadr.registration.api.schemas.InviteUserRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request to invite a user to an account.

**Attributes:**

- [**display_name**](#leadr.registration.api.schemas.InviteUserRequest.display_name) (<code>[str](#str) | None</code>) –
- [**email**](./registration.md#leadr.registration.api.schemas.InviteUserRequest.email) (<code>[EmailStr](#pydantic.EmailStr)</code>) –

####### `leadr.registration.api.schemas.InviteUserRequest.display_name`

```python
display_name: str | None = Field(default=None, description='Optional display name (defaults to email prefix if not provided)')
```

####### `leadr.registration.api.schemas.InviteUserRequest.email`

```python
email: EmailStr = Field(description='Email address to invite')
```

###### `leadr.registration.api.schemas.InviteUserResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response after inviting a user.

**Functions:**

- [**from_domain**](#leadr.registration.api.schemas.InviteUserResponse.from_domain) – Create response from domain entity.

**Attributes:**

- [**email**](./registration.md#leadr.registration.api.schemas.InviteUserResponse.email) (<code>[str](#str)</code>) –
- [**message**](./registration.md#leadr.registration.api.schemas.InviteUserResponse.message) (<code>[str](#str)</code>) –
- [**status**](./registration.md#leadr.registration.api.schemas.InviteUserResponse.status) (<code>[str](#str)</code>) –
- [**user_id**](#leadr.registration.api.schemas.InviteUserResponse.user_id) (<code>[UserID](./common.md#leadr.common.domain.ids.UserID)</code>) –

####### `leadr.registration.api.schemas.InviteUserResponse.email`

```python
email: str = Field(description='Email address of the invited user')
```

####### `leadr.registration.api.schemas.InviteUserResponse.from_domain`

```python
from_domain(user)
```

Create response from domain entity.

**Parameters:**

- **user** – User domain entity.

**Returns:**

- <code>[InviteUserResponse](./registration.md#leadr.registration.api.schemas.InviteUserResponse)</code> – InviteUserResponse instance.

####### `leadr.registration.api.schemas.InviteUserResponse.message`

```python
message: str = Field(description='Success message')
```

####### `leadr.registration.api.schemas.InviteUserResponse.status`

```python
status: str = Field(description='User status (INVITED)')
```

####### `leadr.registration.api.schemas.InviteUserResponse.user_id`

```python
user_id: UserID = Field(description='ID of the invited user')
```

###### `leadr.registration.api.schemas.JamCodeRedemptionResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response representing a jam code redemption.

**Functions:**

- [**from_domain**](#leadr.registration.api.schemas.JamCodeRedemptionResponse.from_domain) – Create response from domain entity.

**Attributes:**

- [**account_id**](#leadr.registration.api.schemas.JamCodeRedemptionResponse.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**id**](./registration.md#leadr.registration.api.schemas.JamCodeRedemptionResponse.id) (<code>[JamCodeRedemptionID](./common.md#leadr.common.domain.ids.JamCodeRedemptionID)</code>) –
- [**jam_code_id**](#leadr.registration.api.schemas.JamCodeRedemptionResponse.jam_code_id) (<code>[JamCodeID](./common.md#leadr.common.domain.ids.JamCodeID)</code>) –
- [**meta**](./registration.md#leadr.registration.api.schemas.JamCodeRedemptionResponse.meta) (<code>[dict](#dict)</code>) –
- [**redeemed_at**](#leadr.registration.api.schemas.JamCodeRedemptionResponse.redeemed_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.registration.api.schemas.JamCodeRedemptionResponse.account_id`

```python
account_id: AccountID
```

####### `leadr.registration.api.schemas.JamCodeRedemptionResponse.from_domain`

```python
from_domain(redemption)
```

Create response from domain entity.

**Parameters:**

- **redemption** – JamCodeRedemption domain entity.

**Returns:**

- <code>[JamCodeRedemptionResponse](./registration.md#leadr.registration.api.schemas.JamCodeRedemptionResponse)</code> – JamCodeRedemptionResponse instance.

####### `leadr.registration.api.schemas.JamCodeRedemptionResponse.id`

```python
id: JamCodeRedemptionID
```

####### `leadr.registration.api.schemas.JamCodeRedemptionResponse.jam_code_id`

```python
jam_code_id: JamCodeID
```

####### `leadr.registration.api.schemas.JamCodeRedemptionResponse.meta`

```python
meta: dict
```

####### `leadr.registration.api.schemas.JamCodeRedemptionResponse.redeemed_at`

```python
redeemed_at: datetime
```

###### `leadr.registration.api.schemas.JamCodeResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response representing a jam code.

**Functions:**

- [**from_domain**](#leadr.registration.api.schemas.JamCodeResponse.from_domain) – Create response from domain entity.

**Attributes:**

- [**active**](./registration.md#leadr.registration.api.schemas.JamCodeResponse.active) (<code>[bool](#bool)</code>) –
- [**code**](./registration.md#leadr.registration.api.schemas.JamCodeResponse.code) (<code>[str](#str)</code>) –
- [**created_at**](#leadr.registration.api.schemas.JamCodeResponse.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**current_uses**](#leadr.registration.api.schemas.JamCodeResponse.current_uses) (<code>[int](#int)</code>) –
- [**description**](./registration.md#leadr.registration.api.schemas.JamCodeResponse.description) (<code>[str](#str)</code>) –
- [**expires_at**](#leadr.registration.api.schemas.JamCodeResponse.expires_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**features**](./registration.md#leadr.registration.api.schemas.JamCodeResponse.features) (<code>[dict](#dict)</code>) –
- [**id**](./registration.md#leadr.registration.api.schemas.JamCodeResponse.id) (<code>[JamCodeID](./common.md#leadr.common.domain.ids.JamCodeID)</code>) –
- [**max_uses**](#leadr.registration.api.schemas.JamCodeResponse.max_uses) (<code>[int](#int) | None</code>) –
- [**updated_at**](#leadr.registration.api.schemas.JamCodeResponse.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.registration.api.schemas.JamCodeResponse.active`

```python
active: bool
```

####### `leadr.registration.api.schemas.JamCodeResponse.code`

```python
code: str
```

####### `leadr.registration.api.schemas.JamCodeResponse.created_at`

```python
created_at: datetime
```

####### `leadr.registration.api.schemas.JamCodeResponse.current_uses`

```python
current_uses: int
```

####### `leadr.registration.api.schemas.JamCodeResponse.description`

```python
description: str
```

####### `leadr.registration.api.schemas.JamCodeResponse.expires_at`

```python
expires_at: datetime | None
```

####### `leadr.registration.api.schemas.JamCodeResponse.features`

```python
features: dict
```

####### `leadr.registration.api.schemas.JamCodeResponse.from_domain`

```python
from_domain(jam_code)
```

Create response from domain entity.

**Parameters:**

- **jam_code** – JamCode domain entity.

**Returns:**

- <code>[JamCodeResponse](./registration.md#leadr.registration.api.schemas.JamCodeResponse)</code> – JamCodeResponse instance.

####### `leadr.registration.api.schemas.JamCodeResponse.id`

```python
id: JamCodeID
```

####### `leadr.registration.api.schemas.JamCodeResponse.max_uses`

```python
max_uses: int | None
```

####### `leadr.registration.api.schemas.JamCodeResponse.updated_at`

```python
updated_at: datetime
```

###### `leadr.registration.api.schemas.UpdateJamCodeRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request to update a jam code.

**Attributes:**

- [**active**](./registration.md#leadr.registration.api.schemas.UpdateJamCodeRequest.active) (<code>[bool](#bool) | None</code>) –
- [**description**](./registration.md#leadr.registration.api.schemas.UpdateJamCodeRequest.description) (<code>[str](#str) | None</code>) –
- [**expires_at**](#leadr.registration.api.schemas.UpdateJamCodeRequest.expires_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**features**](./registration.md#leadr.registration.api.schemas.UpdateJamCodeRequest.features) (<code>[dict](#dict) | None</code>) –
- [**max_uses**](#leadr.registration.api.schemas.UpdateJamCodeRequest.max_uses) (<code>[int](#int) | None</code>) –

####### `leadr.registration.api.schemas.UpdateJamCodeRequest.active`

```python
active: bool | None = Field(default=None, description='New active status')
```

####### `leadr.registration.api.schemas.UpdateJamCodeRequest.description`

```python
description: str | None = Field(default=None, description='New description')
```

####### `leadr.registration.api.schemas.UpdateJamCodeRequest.expires_at`

```python
expires_at: datetime | None = Field(default=None, description='New expiration date')
```

####### `leadr.registration.api.schemas.UpdateJamCodeRequest.features`

```python
features: dict | None = Field(default=None, description='New features/config')
```

####### `leadr.registration.api.schemas.UpdateJamCodeRequest.max_uses`

```python
max_uses: int | None = Field(default=None, description='New max uses')
```

###### `leadr.registration.api.schemas.VerifyCodeRequest`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Request to verify an email verification code.

**Attributes:**

- [**code**](./registration.md#leadr.registration.api.schemas.VerifyCodeRequest.code) (<code>[str](#str)</code>) –
- [**email**](./registration.md#leadr.registration.api.schemas.VerifyCodeRequest.email) (<code>[EmailStr](#pydantic.EmailStr)</code>) –

####### `leadr.registration.api.schemas.VerifyCodeRequest.code`

```python
code: str = Field(description='6-character verification code', min_length=6, max_length=6)
```

####### `leadr.registration.api.schemas.VerifyCodeRequest.email`

```python
email: EmailStr = Field(description='Email address')
```

###### `leadr.registration.api.schemas.VerifyCodeResponse`

Bases: <code>[BaseModel](#pydantic.BaseModel)</code>

Response after verifying a code.

**Attributes:**

- [**expires_in**](#leadr.registration.api.schemas.VerifyCodeResponse.expires_in) (<code>[int](#int)</code>) –
- [**type**](./registration.md#leadr.registration.api.schemas.VerifyCodeResponse.type) (<code>[str](#str)</code>) –
- [**verification_token**](#leadr.registration.api.schemas.VerifyCodeResponse.verification_token) (<code>[str](#str)</code>) –

####### `leadr.registration.api.schemas.VerifyCodeResponse.expires_in`

```python
expires_in: int = Field(description='Seconds until the token expires')
```

####### `leadr.registration.api.schemas.VerifyCodeResponse.type`

```python
type: str = Field(description='Type of verification: REGISTRATION for new accounts, INVITE for invited users')
```

####### `leadr.registration.api.schemas.VerifyCodeResponse.verification_token`

```python
verification_token: str = Field(description='Temporary token for completing registration')
```

#### `leadr.registration.domain`

**Modules:**

- [**jam_code**](#leadr.registration.domain.jam_code) – Jam code domain models for promotional codes and special features.
- [**jam_code_redemption**](#leadr.registration.domain.jam_code_redemption) – Jam code redemption domain models for tracking code usage.
- [**verification_code**](#leadr.registration.domain.verification_code) – Verification code domain models for email verification during registration.

##### `leadr.registration.domain.jam_code`

Jam code domain models for promotional codes and special features.

**Classes:**

- [**JamCode**](#leadr.registration.domain.jam_code.JamCode) – Jam code domain entity.

###### `leadr.registration.domain.jam_code.JamCode`

Bases: <code>[Entity](./common.md#leadr.common.domain.models.Entity)</code>

Jam code domain entity.

Represents a promotional code that grants special features or access during registration.
Codes can be used for game jams, marketing campaigns, or referral tracking.
Supports optional usage limits, expiration dates, and custom feature flags stored as JSON.

**Functions:**

- [**activate**](#leadr.registration.domain.jam_code.JamCode.activate) – Activate the jam code, allowing redemptions.
- [**deactivate**](#leadr.registration.domain.jam_code.JamCode.deactivate) – Deactivate the jam code, preventing further redemptions.
- [**get_feature**](#leadr.registration.domain.jam_code.JamCode.get_feature) – Get a feature value from the features dictionary.
- [**has_uses_remaining**](#leadr.registration.domain.jam_code.JamCode.has_uses_remaining) – Check if the jam code has remaining uses.
- [**increment_uses**](#leadr.registration.domain.jam_code.JamCode.increment_uses) – Increment the usage count by one.
- [**is_expired**](#leadr.registration.domain.jam_code.JamCode.is_expired) – Check if the jam code has expired.
- [**is_valid**](#leadr.registration.domain.jam_code.JamCode.is_valid) – Check if the jam code is valid and can be redeemed.
- [**restore**](#leadr.registration.domain.jam_code.JamCode.restore) – Restore a soft-deleted entity.
- [**soft_delete**](#leadr.registration.domain.jam_code.JamCode.soft_delete) – Mark entity as soft-deleted.
- [**validate_code**](#leadr.registration.domain.jam_code.JamCode.validate_code) – Validate and normalize the jam code.

**Attributes:**

- [**active**](#leadr.registration.domain.jam_code.JamCode.active) (<code>[bool](#bool)</code>) –
- [**code**](#leadr.registration.domain.jam_code.JamCode.code) (<code>[str](#str)</code>) –
- [**created_at**](#leadr.registration.domain.jam_code.JamCode.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**current_uses**](#leadr.registration.domain.jam_code.JamCode.current_uses) (<code>[int](#int)</code>) –
- [**deleted_at**](#leadr.registration.domain.jam_code.JamCode.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**description**](#leadr.registration.domain.jam_code.JamCode.description) (<code>[str](#str)</code>) –
- [**expires_at**](#leadr.registration.domain.jam_code.JamCode.expires_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**features**](#leadr.registration.domain.jam_code.JamCode.features) (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\]</code>) –
- [**id**](#leadr.registration.domain.jam_code.JamCode.id) (<code>[Any](#typing.Any)</code>) –
- [**is_deleted**](#leadr.registration.domain.jam_code.JamCode.is_deleted) (<code>[bool](#bool)</code>) – Check if entity is soft-deleted.
- [**max_uses**](#leadr.registration.domain.jam_code.JamCode.max_uses) (<code>[int](#int) | None</code>) –
- [**model_config**](#leadr.registration.domain.jam_code.JamCode.model_config) –
- [**updated_at**](#leadr.registration.domain.jam_code.JamCode.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.registration.domain.jam_code.JamCode.activate`

```python
activate()
```

Activate the jam code, allowing redemptions.

Used to re-enable a previously deactivated code.

####### `leadr.registration.domain.jam_code.JamCode.active`

```python
active: bool = Field(default=True, description='Whether this code can currently be redeemed')
```

####### `leadr.registration.domain.jam_code.JamCode.code`

```python
code: str = Field(description='Alphanumeric code (3-50 characters, case-insensitive)', min_length=3, max_length=50)
```

####### `leadr.registration.domain.jam_code.JamCode.created_at`

```python
created_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp when entity was created (UTC)')
```

####### `leadr.registration.domain.jam_code.JamCode.current_uses`

```python
current_uses: int = Field(default=0, description='Current number of times this code has been redeemed')
```

####### `leadr.registration.domain.jam_code.JamCode.deactivate`

```python
deactivate()
```

Deactivate the jam code, preventing further redemptions.

Used to manually disable a code (e.g., if it's compromised or no longer needed).

####### `leadr.registration.domain.jam_code.JamCode.deleted_at`

```python
deleted_at: datetime | None = Field(default=None, description='Timestamp when entity was soft-deleted (UTC), or null if active')
```

####### `leadr.registration.domain.jam_code.JamCode.description`

```python
description: str = Field(description="Human-readable description of this code's purpose")
```

####### `leadr.registration.domain.jam_code.JamCode.expires_at`

```python
expires_at: datetime | None = Field(default=None, description='When this code expires (None = never expires)')
```

####### `leadr.registration.domain.jam_code.JamCode.features`

```python
features: dict[str, Any] = Field(default_factory=dict, description='Custom features/config for this code (e.g., CLI templates, score limits)')
```

####### `leadr.registration.domain.jam_code.JamCode.get_feature`

```python
get_feature(key, default=None)
```

Get a feature value from the features dictionary.

**Parameters:**

- **key** (<code>[str](#str)</code>) – The feature key to retrieve.
- **default** (<code>[Any](#typing.Any)</code>) – Default value if the key doesn't exist.

**Returns:**

- <code>[Any](#typing.Any)</code> – The feature value or the default.

####### `leadr.registration.domain.jam_code.JamCode.has_uses_remaining`

```python
has_uses_remaining()
```

Check if the jam code has remaining uses.

**Returns:**

- <code>[bool](#bool)</code> – True if the code has no usage limit or has not reached its limit.

####### `leadr.registration.domain.jam_code.JamCode.id`

```python
id: Any = Field(frozen=True, default_factory=uuid4, description='Unique identifier (auto-generated UUID or typed ID)')
```

####### `leadr.registration.domain.jam_code.JamCode.increment_uses`

```python
increment_uses()
```

Increment the usage count by one.

Called when a jam code is successfully redeemed during registration.

####### `leadr.registration.domain.jam_code.JamCode.is_deleted`

```python
is_deleted: bool
```

Check if entity is soft-deleted.

**Returns:**

- <code>[bool](#bool)</code> – True if the entity has a deleted_at timestamp, False otherwise.

####### `leadr.registration.domain.jam_code.JamCode.is_expired`

```python
is_expired()
```

Check if the jam code has expired.

**Returns:**

- <code>[bool](#bool)</code> – True if the code has an expiration date and it has passed.

####### `leadr.registration.domain.jam_code.JamCode.is_valid`

```python
is_valid()
```

Check if the jam code is valid and can be redeemed.

A code is valid if it's active, not expired, and has uses remaining.

**Returns:**

- <code>[bool](#bool)</code> – True if the code can be used for registration.

####### `leadr.registration.domain.jam_code.JamCode.max_uses`

```python
max_uses: int | None = Field(default=None, description='Maximum number of redemptions allowed (None = unlimited)')
```

####### `leadr.registration.domain.jam_code.JamCode.model_config`

```python
model_config = ConfigDict(validate_assignment=True)
```

####### `leadr.registration.domain.jam_code.JamCode.restore`

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

####### `leadr.registration.domain.jam_code.JamCode.soft_delete`

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

####### `leadr.registration.domain.jam_code.JamCode.updated_at`

```python
updated_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp of last update (UTC)')
```

####### `leadr.registration.domain.jam_code.JamCode.validate_code`

```python
validate_code(v)
```

Validate and normalize the jam code.

**Parameters:**

- **v** (<code>[str](#str)</code>) – The code value to validate.

**Returns:**

- <code>[str](#str)</code> – The normalized (uppercase) code.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If the code contains non-alphanumeric characters.

##### `leadr.registration.domain.jam_code_redemption`

Jam code redemption domain models for tracking code usage.

**Classes:**

- [**JamCodeRedemption**](#leadr.registration.domain.jam_code_redemption.JamCodeRedemption) – Jam code redemption domain entity.

###### `leadr.registration.domain.jam_code_redemption.JamCodeRedemption`

Bases: <code>[Entity](./common.md#leadr.common.domain.models.Entity)</code>

Jam code redemption domain entity.

Represents a single use of a jam code during account registration.
Tracks which account redeemed which code, when it was redeemed,
and any associated metadata (e.g., CLI configuration, user agent).

**Functions:**

- [**get_meta**](#leadr.registration.domain.jam_code_redemption.JamCodeRedemption.get_meta) – Get a metadata value from the meta dictionary.
- [**restore**](#leadr.registration.domain.jam_code_redemption.JamCodeRedemption.restore) – Restore a soft-deleted entity.
- [**soft_delete**](#leadr.registration.domain.jam_code_redemption.JamCodeRedemption.soft_delete) – Mark entity as soft-deleted.

**Attributes:**

- [**account_id**](#leadr.registration.domain.jam_code_redemption.JamCodeRedemption.account_id) (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) –
- [**created_at**](#leadr.registration.domain.jam_code_redemption.JamCodeRedemption.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**deleted_at**](#leadr.registration.domain.jam_code_redemption.JamCodeRedemption.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**id**](#leadr.registration.domain.jam_code_redemption.JamCodeRedemption.id) (<code>[Any](#typing.Any)</code>) –
- [**is_deleted**](#leadr.registration.domain.jam_code_redemption.JamCodeRedemption.is_deleted) (<code>[bool](#bool)</code>) – Check if entity is soft-deleted.
- [**jam_code_id**](#leadr.registration.domain.jam_code_redemption.JamCodeRedemption.jam_code_id) (<code>[UUID](#uuid.UUID)</code>) –
- [**meta**](#leadr.registration.domain.jam_code_redemption.JamCodeRedemption.meta) (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\]</code>) –
- [**model_config**](#leadr.registration.domain.jam_code_redemption.JamCodeRedemption.model_config) –
- [**redeemed_at**](#leadr.registration.domain.jam_code_redemption.JamCodeRedemption.redeemed_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**updated_at**](#leadr.registration.domain.jam_code_redemption.JamCodeRedemption.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

####### `leadr.registration.domain.jam_code_redemption.JamCodeRedemption.account_id`

```python
account_id: AccountID = Field(description='ID of the account that redeemed the code')
```

####### `leadr.registration.domain.jam_code_redemption.JamCodeRedemption.created_at`

```python
created_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp when entity was created (UTC)')
```

####### `leadr.registration.domain.jam_code_redemption.JamCodeRedemption.deleted_at`

```python
deleted_at: datetime | None = Field(default=None, description='Timestamp when entity was soft-deleted (UTC), or null if active')
```

####### `leadr.registration.domain.jam_code_redemption.JamCodeRedemption.get_meta`

```python
get_meta(key, default=None)
```

Get a metadata value from the meta dictionary.

**Parameters:**

- **key** (<code>[str](#str)</code>) – The metadata key to retrieve.
- **default** (<code>[Any](#typing.Any)</code>) – Default value if the key doesn't exist.

**Returns:**

- <code>[Any](#typing.Any)</code> – The metadata value or the default.

####### `leadr.registration.domain.jam_code_redemption.JamCodeRedemption.id`

```python
id: Any = Field(frozen=True, default_factory=uuid4, description='Unique identifier (auto-generated UUID or typed ID)')
```

####### `leadr.registration.domain.jam_code_redemption.JamCodeRedemption.is_deleted`

```python
is_deleted: bool
```

Check if entity is soft-deleted.

**Returns:**

- <code>[bool](#bool)</code> – True if the entity has a deleted_at timestamp, False otherwise.

####### `leadr.registration.domain.jam_code_redemption.JamCodeRedemption.jam_code_id`

```python
jam_code_id: UUID = Field(description='ID of the jam code that was redeemed')
```

####### `leadr.registration.domain.jam_code_redemption.JamCodeRedemption.meta`

```python
meta: dict[str, Any] = Field(default_factory=dict, description='Additional metadata about the redemption (e.g., CLI config, user agent)')
```

####### `leadr.registration.domain.jam_code_redemption.JamCodeRedemption.model_config`

```python
model_config = ConfigDict(validate_assignment=True)
```

####### `leadr.registration.domain.jam_code_redemption.JamCodeRedemption.redeemed_at`

```python
redeemed_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='When the code was redeemed (UTC)')
```

####### `leadr.registration.domain.jam_code_redemption.JamCodeRedemption.restore`

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

####### `leadr.registration.domain.jam_code_redemption.JamCodeRedemption.soft_delete`

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

####### `leadr.registration.domain.jam_code_redemption.JamCodeRedemption.updated_at`

```python
updated_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp of last update (UTC)')
```

##### `leadr.registration.domain.verification_code`

Verification code domain models for email verification during registration.

**Classes:**

- [**VerificationCode**](#leadr.registration.domain.verification_code.VerificationCode) – Verification code domain entity.
- [**VerificationCodeStatus**](#leadr.registration.domain.verification_code.VerificationCodeStatus) – Verification code status enumeration.
- [**VerificationCodeType**](#leadr.registration.domain.verification_code.VerificationCodeType) – Verification code type enumeration.

###### `leadr.registration.domain.verification_code.VerificationCode`

Bases: <code>[Entity](./common.md#leadr.common.domain.models.Entity)</code>

Verification code domain entity.

Represents a one-time email verification code used during registration or invite flows.
Codes are 6-character alphanumeric strings with configurable expiration windows
(10 minutes for registration, 24 hours for invites by default).
Once used or expired, codes become invalid and cannot be reused.

The code_type field distinguishes between REGISTRATION codes (for new account signup)
and INVITE codes (for invited users joining an existing account).

**Functions:**

- [**is_expired**](#leadr.registration.domain.verification_code.VerificationCode.is_expired) – Check if the verification code has expired.
- [**is_used**](#leadr.registration.domain.verification_code.VerificationCode.is_used) – Check if the verification code has been used.
- [**is_valid**](#leadr.registration.domain.verification_code.VerificationCode.is_valid) – Check if the verification code is valid and can be used.
- [**mark_as_expired**](#leadr.registration.domain.verification_code.VerificationCode.mark_as_expired) – Mark the verification code as expired.
- [**mark_as_used**](#leadr.registration.domain.verification_code.VerificationCode.mark_as_used) – Mark the verification code as used.
- [**restore**](#leadr.registration.domain.verification_code.VerificationCode.restore) – Restore a soft-deleted entity.
- [**soft_delete**](#leadr.registration.domain.verification_code.VerificationCode.soft_delete) – Mark entity as soft-deleted.
- [**validate_code**](#leadr.registration.domain.verification_code.VerificationCode.validate_code) – Validate and normalize the verification code.

**Attributes:**

- [**code**](#leadr.registration.domain.verification_code.VerificationCode.code) (<code>[str](#str)</code>) –
- [**code_type**](#leadr.registration.domain.verification_code.VerificationCode.code_type) (<code>[VerificationCodeType](#leadr.registration.domain.verification_code.VerificationCodeType)</code>) –
- [**created_at**](#leadr.registration.domain.verification_code.VerificationCode.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**deleted_at**](#leadr.registration.domain.verification_code.VerificationCode.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**email**](#leadr.registration.domain.verification_code.VerificationCode.email) (<code>[EmailStr](#pydantic.EmailStr)</code>) –
- [**expires_at**](#leadr.registration.domain.verification_code.VerificationCode.expires_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**id**](#leadr.registration.domain.verification_code.VerificationCode.id) (<code>[Any](#typing.Any)</code>) –
- [**is_deleted**](#leadr.registration.domain.verification_code.VerificationCode.is_deleted) (<code>[bool](#bool)</code>) – Check if entity is soft-deleted.
- [**is_invite**](#leadr.registration.domain.verification_code.VerificationCode.is_invite) (<code>[bool](#bool)</code>) – Check if this is an invite code.
- [**is_registration**](#leadr.registration.domain.verification_code.VerificationCode.is_registration) (<code>[bool](#bool)</code>) – Check if this is a registration code.
- [**model_config**](#leadr.registration.domain.verification_code.VerificationCode.model_config) –
- [**status**](#leadr.registration.domain.verification_code.VerificationCode.status) (<code>[VerificationCodeStatus](#leadr.registration.domain.verification_code.VerificationCodeStatus)</code>) –
- [**updated_at**](#leadr.registration.domain.verification_code.VerificationCode.updated_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**used_at**](#leadr.registration.domain.verification_code.VerificationCode.used_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**user_id**](#leadr.registration.domain.verification_code.VerificationCode.user_id) (<code>[UserID](./common.md#leadr.common.domain.ids.UserID) | None</code>) –

####### `leadr.registration.domain.verification_code.VerificationCode.code`

```python
code: str = Field(description='6-character alphanumeric verification code (case-insensitive)', min_length=6, max_length=6)
```

####### `leadr.registration.domain.verification_code.VerificationCode.code_type`

```python
code_type: VerificationCodeType = Field(default=(VerificationCodeType.REGISTRATION), description='Type of verification code (registration or invite)')
```

####### `leadr.registration.domain.verification_code.VerificationCode.created_at`

```python
created_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp when entity was created (UTC)')
```

####### `leadr.registration.domain.verification_code.VerificationCode.deleted_at`

```python
deleted_at: datetime | None = Field(default=None, description='Timestamp when entity was soft-deleted (UTC), or null if active')
```

####### `leadr.registration.domain.verification_code.VerificationCode.email`

```python
email: EmailStr = Field(description='Email address this code was sent to')
```

####### `leadr.registration.domain.verification_code.VerificationCode.expires_at`

```python
expires_at: datetime = Field(description='When this code expires (UTC)')
```

####### `leadr.registration.domain.verification_code.VerificationCode.id`

```python
id: Any = Field(frozen=True, default_factory=uuid4, description='Unique identifier (auto-generated UUID or typed ID)')
```

####### `leadr.registration.domain.verification_code.VerificationCode.is_deleted`

```python
is_deleted: bool
```

Check if entity is soft-deleted.

**Returns:**

- <code>[bool](#bool)</code> – True if the entity has a deleted_at timestamp, False otherwise.

####### `leadr.registration.domain.verification_code.VerificationCode.is_expired`

```python
is_expired()
```

Check if the verification code has expired.

**Returns:**

- <code>[bool](#bool)</code> – True if the code's expiration time has passed.

####### `leadr.registration.domain.verification_code.VerificationCode.is_invite`

```python
is_invite: bool
```

Check if this is an invite code.

####### `leadr.registration.domain.verification_code.VerificationCode.is_registration`

```python
is_registration: bool
```

Check if this is a registration code.

####### `leadr.registration.domain.verification_code.VerificationCode.is_used`

```python
is_used()
```

Check if the verification code has been used.

**Returns:**

- <code>[bool](#bool)</code> – True if the code status is USED.

####### `leadr.registration.domain.verification_code.VerificationCode.is_valid`

```python
is_valid()
```

Check if the verification code is valid and can be used.

A code is valid if it hasn't been used and hasn't expired.

**Returns:**

- <code>[bool](#bool)</code> – True if the code is valid and can be used for verification.

####### `leadr.registration.domain.verification_code.VerificationCode.mark_as_expired`

```python
mark_as_expired()
```

Mark the verification code as expired.

Sets the status to EXPIRED. This is typically done when cleaning up
old codes or when explicitly invalidating codes.

####### `leadr.registration.domain.verification_code.VerificationCode.mark_as_used`

```python
mark_as_used()
```

Mark the verification code as used.

Sets the status to USED and records the current timestamp in used_at.
Once marked as used, the code cannot be reused.

####### `leadr.registration.domain.verification_code.VerificationCode.model_config`

```python
model_config = ConfigDict(validate_assignment=True)
```

####### `leadr.registration.domain.verification_code.VerificationCode.restore`

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

####### `leadr.registration.domain.verification_code.VerificationCode.soft_delete`

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

####### `leadr.registration.domain.verification_code.VerificationCode.status`

```python
status: VerificationCodeStatus = VerificationCodeStatus.PENDING
```

####### `leadr.registration.domain.verification_code.VerificationCode.updated_at`

```python
updated_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp of last update (UTC)')
```

####### `leadr.registration.domain.verification_code.VerificationCode.used_at`

```python
used_at: datetime | None = None
```

####### `leadr.registration.domain.verification_code.VerificationCode.user_id`

```python
user_id: UserID | None = Field(default=None, description='User ID for invite codes (links invite to existing user record)')
```

####### `leadr.registration.domain.verification_code.VerificationCode.validate_code`

```python
validate_code(v)
```

Validate and normalize the verification code.

**Parameters:**

- **v** (<code>[str](#str)</code>) – The code value to validate.

**Returns:**

- <code>[str](#str)</code> – The normalized (uppercase) code.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If the code contains non-alphanumeric characters.

###### `leadr.registration.domain.verification_code.VerificationCodeStatus`

Bases: <code>[Enum](#enum.Enum)</code>

Verification code status enumeration.

**Attributes:**

- [**EXPIRED**](#leadr.registration.domain.verification_code.VerificationCodeStatus.EXPIRED) –
- [**PENDING**](#leadr.registration.domain.verification_code.VerificationCodeStatus.PENDING) –
- [**USED**](#leadr.registration.domain.verification_code.VerificationCodeStatus.USED) –

####### `leadr.registration.domain.verification_code.VerificationCodeStatus.EXPIRED`

```python
EXPIRED = 'expired'
```

####### `leadr.registration.domain.verification_code.VerificationCodeStatus.PENDING`

```python
PENDING = 'pending'
```

####### `leadr.registration.domain.verification_code.VerificationCodeStatus.USED`

```python
USED = 'used'
```

###### `leadr.registration.domain.verification_code.VerificationCodeType`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Verification code type enumeration.

Distinguishes between codes used for initial registration
and codes used for user invitations.

**Attributes:**

- [**INVITE**](#leadr.registration.domain.verification_code.VerificationCodeType.INVITE) – Code for invited user to join an existing account.
- [**REGISTRATION**](#leadr.registration.domain.verification_code.VerificationCodeType.REGISTRATION) – Code for new account registration flow.

####### `leadr.registration.domain.verification_code.VerificationCodeType.INVITE`

```python
INVITE = 'invite'
```

Code for invited user to join an existing account.

####### `leadr.registration.domain.verification_code.VerificationCodeType.REGISTRATION`

```python
REGISTRATION = 'registration'
```

Code for new account registration flow.

#### `leadr.registration.services`

**Modules:**

- [**dependencies**](./registration.md#leadr.registration.services.dependencies) – Dependency injection for registration services.
- [**invite_service**](#leadr.registration.services.invite_service) – Invite service for managing user invitations to accounts.
- [**jam_code_service**](#leadr.registration.services.jam_code_service) – Jam code service for managing promotional codes.
- [**registration_service**](#leadr.registration.services.registration_service) – Registration service for orchestrating account creation and invite completion flows.
- [**repositories**](./registration.md#leadr.registration.services.repositories) – Registration repository services for verification codes and jam codes.
- [**verification_service**](#leadr.registration.services.verification_service) – Verification service for generating and validating email verification codes.

##### `leadr.registration.services.dependencies`

Dependency injection for registration services.

**Functions:**

- [**get_email_service**](#leadr.registration.services.dependencies.get_email_service) – Get EmailService dependency.
- [**get_invite_service**](#leadr.registration.services.dependencies.get_invite_service) – Get InviteService dependency.
- [**get_jam_code_service**](#leadr.registration.services.dependencies.get_jam_code_service) – Get JamCodeService dependency.
- [**get_registration_service**](#leadr.registration.services.dependencies.get_registration_service) – Get RegistrationService dependency.
- [**get_verification_service**](#leadr.registration.services.dependencies.get_verification_service) – Get VerificationService dependency.

**Attributes:**

- [**EmailServiceDep**](./registration.md#leadr.registration.services.dependencies.EmailServiceDep) –
- [**InviteServiceDep**](./registration.md#leadr.registration.services.dependencies.InviteServiceDep) –
- [**JamCodeServiceDep**](./registration.md#leadr.registration.services.dependencies.JamCodeServiceDep) –
- [**RegistrationServiceDep**](./registration.md#leadr.registration.services.dependencies.RegistrationServiceDep) –
- [**VerificationServiceDep**](./registration.md#leadr.registration.services.dependencies.VerificationServiceDep) –

###### `leadr.registration.services.dependencies.EmailServiceDep`

```python
EmailServiceDep = Annotated[EmailService, Depends(get_email_service)]
```

###### `leadr.registration.services.dependencies.InviteServiceDep`

```python
InviteServiceDep = Annotated[InviteService, Depends(get_invite_service)]
```

###### `leadr.registration.services.dependencies.JamCodeServiceDep`

```python
JamCodeServiceDep = Annotated[JamCodeService, Depends(get_jam_code_service)]
```

###### `leadr.registration.services.dependencies.RegistrationServiceDep`

```python
RegistrationServiceDep = Annotated[RegistrationService, Depends(get_registration_service)]
```

###### `leadr.registration.services.dependencies.VerificationServiceDep`

```python
VerificationServiceDep = Annotated[VerificationService, Depends(get_verification_service)]
```

###### `leadr.registration.services.dependencies.get_email_service`

```python
get_email_service(db)
```

Get EmailService dependency.

**Parameters:**

- **db** (<code>[DatabaseSession](./common.md#leadr.common.dependencies.DatabaseSession)</code>) – Database session.

**Returns:**

- <code>[EmailService](./infra.md#leadr.infra.email.EmailService)</code> – EmailService instance.

###### `leadr.registration.services.dependencies.get_invite_service`

```python
get_invite_service(db, account_service, user_service, verification_service, email_service)
```

Get InviteService dependency.

**Parameters:**

- **db** (<code>[DatabaseSession](./common.md#leadr.common.dependencies.DatabaseSession)</code>) – Database session.
- **account_service** (<code>[AccountServiceDep](#leadr.accounts.services.dependencies.AccountServiceDep)</code>) – Account service.
- **user_service** (<code>[UserServiceDep](#leadr.accounts.services.dependencies.UserServiceDep)</code>) – User service.
- **verification_service** (<code>[VerificationServiceDep](./registration.md#leadr.registration.services.dependencies.VerificationServiceDep)</code>) – Verification service.
- **email_service** (<code>[EmailServiceDep](./registration.md#leadr.registration.services.dependencies.EmailServiceDep)</code>) – Email service.

**Returns:**

- <code>[InviteService](#leadr.registration.services.invite_service.InviteService)</code> – InviteService instance.

###### `leadr.registration.services.dependencies.get_jam_code_service`

```python
get_jam_code_service(db)
```

Get JamCodeService dependency.

**Parameters:**

- **db** (<code>[DatabaseSession](./common.md#leadr.common.dependencies.DatabaseSession)</code>) – Database session.

**Returns:**

- <code>[JamCodeService](#leadr.registration.services.jam_code_service.JamCodeService)</code> – JamCodeService instance.

###### `leadr.registration.services.dependencies.get_registration_service`

```python
get_registration_service(db, account_service, user_service, api_key_service, verification_service, jam_code_service, email_service)
```

Get RegistrationService dependency.

**Parameters:**

- **db** (<code>[DatabaseSession](./common.md#leadr.common.dependencies.DatabaseSession)</code>) – Database session.
- **account_service** (<code>[AccountServiceDep](#leadr.accounts.services.dependencies.AccountServiceDep)</code>) – Account service.
- **user_service** (<code>[UserServiceDep](#leadr.accounts.services.dependencies.UserServiceDep)</code>) – User service.
- **api_key_service** (<code>[APIKeyServiceDep](./auth.md#leadr.auth.services.dependencies.APIKeyServiceDep)</code>) – API key service.
- **verification_service** (<code>[VerificationServiceDep](./registration.md#leadr.registration.services.dependencies.VerificationServiceDep)</code>) – Verification service.
- **jam_code_service** (<code>[JamCodeServiceDep](./registration.md#leadr.registration.services.dependencies.JamCodeServiceDep)</code>) – Jam code service.
- **email_service** (<code>[EmailServiceDep](./registration.md#leadr.registration.services.dependencies.EmailServiceDep)</code>) – Email service.

**Returns:**

- <code>[RegistrationService](#leadr.registration.services.registration_service.RegistrationService)</code> – RegistrationService instance.

###### `leadr.registration.services.dependencies.get_verification_service`

```python
get_verification_service(db, email_service)
```

Get VerificationService dependency.

**Parameters:**

- **db** (<code>[DatabaseSession](./common.md#leadr.common.dependencies.DatabaseSession)</code>) – Database session.
- **email_service** (<code>[EmailServiceDep](./registration.md#leadr.registration.services.dependencies.EmailServiceDep)</code>) – Email service.

**Returns:**

- <code>[VerificationService](#leadr.registration.services.verification_service.VerificationService)</code> – VerificationService instance.

##### `leadr.registration.services.invite_service`

Invite service for managing user invitations to accounts.

**Classes:**

- [**InviteService**](#leadr.registration.services.invite_service.InviteService) – Service for managing user invitations.

**Attributes:**

- [**logger**](#leadr.registration.services.invite_service.logger) –

###### `leadr.registration.services.invite_service.InviteService`

```python
InviteService(db, account_service, user_service, verification_service, email_service)
```

Service for managing user invitations.

Coordinates the invite flow:

1. Create invited user with INVITED status
1. Create invite verification code
1. Send invite email

**Functions:**

- [**send_invite**](#leadr.registration.services.invite_service.InviteService.send_invite) – Invite a user to an account.

**Attributes:**

- [**account_service**](#leadr.registration.services.invite_service.InviteService.account_service) –
- [**db**](#leadr.registration.services.invite_service.InviteService.db) –
- [**email_service**](#leadr.registration.services.invite_service.InviteService.email_service) –
- [**user_service**](#leadr.registration.services.invite_service.InviteService.user_service) –
- [**verification_service**](#leadr.registration.services.invite_service.InviteService.verification_service) –

**Parameters:**

- **db** (<code>[AsyncSession](#sqlalchemy.ext.asyncio.AsyncSession)</code>) – Database session.
- **account_service** (<code>[AccountService](#leadr.accounts.services.account_service.AccountService)</code>) – Account service for fetching account info.
- **user_service** (<code>[UserService](#leadr.accounts.services.user_service.UserService)</code>) – User service for creating users.
- **verification_service** (<code>[VerificationService](#leadr.registration.services.verification_service.VerificationService)</code>) – Verification service for creating invite codes.
- **email_service** (<code>[EmailService](./infra.md#leadr.infra.email.EmailService)</code>) – Email service for sending invite emails.

####### `leadr.registration.services.invite_service.InviteService.account_service`

```python
account_service = account_service
```

####### `leadr.registration.services.invite_service.InviteService.db`

```python
db = db
```

####### `leadr.registration.services.invite_service.InviteService.email_service`

```python
email_service = email_service
```

####### `leadr.registration.services.invite_service.InviteService.send_invite`

```python
send_invite(email, account_id, display_name=None)
```

Invite a user to an account.

Creates a user with INVITED status and sends an invite email with
a verification code. If the user already exists with INVITED status,
resends the invite (invalidates old code, creates new one).

**Parameters:**

- **email** (<code>[str](#str)</code>) – Email address to invite.
- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – The account ID to invite the user to.
- **display_name** (<code>[str](#str) | None</code>) – Optional display name. Defaults to email prefix if not provided.

**Returns:**

- <code>[User](./accounts.md#leadr.accounts.domain.user.User)</code> – The created or existing User entity with INVITED status.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If user already exists with non-INVITED status.
- <code>[ValueError](#ValueError)</code> – If account doesn't exist.

####### `leadr.registration.services.invite_service.InviteService.user_service`

```python
user_service = user_service
```

####### `leadr.registration.services.invite_service.InviteService.verification_service`

```python
verification_service = verification_service
```

###### `leadr.registration.services.invite_service.logger`

```python
logger = logging.getLogger(__name__)
```

##### `leadr.registration.services.jam_code_service`

Jam code service for managing promotional codes.

**Classes:**

- [**JamCodeService**](#leadr.registration.services.jam_code_service.JamCodeService) – Service for managing jam codes and redemptions.

###### `leadr.registration.services.jam_code_service.JamCodeService`

```python
JamCodeService(db)
```

Service for managing jam codes and redemptions.

**Functions:**

- [**create_jam_code**](#leadr.registration.services.jam_code_service.JamCodeService.create_jam_code) – Create a new jam code.
- [**get_jam_code_by_id**](#leadr.registration.services.jam_code_service.JamCodeService.get_jam_code_by_id) – Get a jam code by its ID.
- [**list_jam_codes**](#leadr.registration.services.jam_code_service.JamCodeService.list_jam_codes) – List all jam codes with pagination.
- [**redeem_jam_code**](#leadr.registration.services.jam_code_service.JamCodeService.redeem_jam_code) – Redeem a jam code for an account.
- [**update_jam_code**](#leadr.registration.services.jam_code_service.JamCodeService.update_jam_code) – Update a jam code.
- [**validate_and_get_jam_code**](#leadr.registration.services.jam_code_service.JamCodeService.validate_and_get_jam_code) – Validate a jam code and return it if valid.

**Attributes:**

- [**db**](#leadr.registration.services.jam_code_service.JamCodeService.db) –
- [**jam_code_repository**](#leadr.registration.services.jam_code_service.JamCodeService.jam_code_repository) –
- [**redemption_repository**](#leadr.registration.services.jam_code_service.JamCodeService.redemption_repository) –

**Parameters:**

- **db** (<code>[AsyncSession](#sqlalchemy.ext.asyncio.AsyncSession)</code>) – Database session.

####### `leadr.registration.services.jam_code_service.JamCodeService.create_jam_code`

```python
create_jam_code(code, description, features=None, max_uses=None, expires_at=None)
```

Create a new jam code.

**Parameters:**

- **code** (<code>[str](#str)</code>) – The code value (will be normalized to uppercase).
- **description** (<code>[str](#str)</code>) – Human-readable description.
- **features** (<code>[dict](#dict) | None</code>) – Optional features dictionary.
- **max_uses** (<code>[int](#int) | None</code>) – Optional maximum number of redemptions.
- **expires_at** (<code>[datetime](#datetime.datetime) | None</code>) – Optional expiration date.

**Returns:**

- <code>[JamCode](#leadr.registration.domain.jam_code.JamCode)</code> – The created jam code.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If a jam code with this code already exists.

####### `leadr.registration.services.jam_code_service.JamCodeService.db`

```python
db = db
```

####### `leadr.registration.services.jam_code_service.JamCodeService.get_jam_code_by_id`

```python
get_jam_code_by_id(jam_code_id)
```

Get a jam code by its ID.

**Parameters:**

- **jam_code_id** (<code>[UUID](#uuid.UUID)</code>) – The jam code ID.

**Returns:**

- <code>[JamCode](#leadr.registration.domain.jam_code.JamCode) | None</code> – The jam code if found, None otherwise.

####### `leadr.registration.services.jam_code_service.JamCodeService.jam_code_repository`

```python
jam_code_repository = JamCodeRepository(db)
```

####### `leadr.registration.services.jam_code_service.JamCodeService.list_jam_codes`

```python
list_jam_codes(*, pagination)
```

List all jam codes with pagination.

**Parameters:**

- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters.

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[JamCode](#leadr.registration.domain.jam_code.JamCode)\]</code> – Paginated result of jam codes.

####### `leadr.registration.services.jam_code_service.JamCodeService.redeem_jam_code`

```python
redeem_jam_code(jam_code, account_id, meta=None)
```

Redeem a jam code for an account.

**Parameters:**

- **jam_code** (<code>[JamCode](#leadr.registration.domain.jam_code.JamCode)</code>) – The jam code to redeem.
- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – The account redeeming the code.
- **meta** (<code>[dict](#dict) | None</code>) – Optional metadata to store with the redemption.

**Returns:**

- <code>[JamCodeRedemption](#leadr.registration.domain.jam_code_redemption.JamCodeRedemption)</code> – The jam code redemption entity.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If the jam code has already been redeemed by this account.

####### `leadr.registration.services.jam_code_service.JamCodeService.redemption_repository`

```python
redemption_repository = JamCodeRedemptionRepository(db)
```

####### `leadr.registration.services.jam_code_service.JamCodeService.update_jam_code`

```python
update_jam_code(jam_code_id, description=None, features=None, max_uses=None, active=None, expires_at=None)
```

Update a jam code.

**Parameters:**

- **jam_code_id** (<code>[UUID](#uuid.UUID)</code>) – The jam code ID.
- **description** (<code>[str](#str) | None</code>) – Optional new description.
- **features** (<code>[dict](#dict) | None</code>) – Optional new features dictionary.
- **max_uses** (<code>[int](#int) | None</code>) – Optional new max uses.
- **active** (<code>[bool](#bool) | None</code>) – Optional new active status.
- **expires_at** (<code>[datetime](#datetime.datetime) | None</code>) – Optional new expiration date.

**Returns:**

- <code>[JamCode](#leadr.registration.domain.jam_code.JamCode)</code> – The updated jam code.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If the jam code doesn't exist.

####### `leadr.registration.services.jam_code_service.JamCodeService.validate_and_get_jam_code`

```python
validate_and_get_jam_code(code)
```

Validate a jam code and return it if valid.

**Parameters:**

- **code** (<code>[str](#str)</code>) – The jam code to validate.

**Returns:**

- <code>[JamCode](#leadr.registration.domain.jam_code.JamCode) | None</code> – The jam code if valid, None if invalid or not found.

##### `leadr.registration.services.registration_service`

Registration service for orchestrating account creation and invite completion flows.

**Classes:**

- [**RegistrationService**](#leadr.registration.services.registration_service.RegistrationService) – Service for orchestrating registration and invite completion flows.

###### `leadr.registration.services.registration_service.RegistrationService`

```python
RegistrationService(db, account_service, user_service, api_key_service, verification_service, jam_code_service, email_service)
```

Service for orchestrating registration and invite completion flows.

Handles two distinct flows:

- Registration: Creates new account, user (as owner), and API key
- Invite: Activates existing invited user and creates API key

**Functions:**

- [**complete_registration**](#leadr.registration.services.registration_service.RegistrationService.complete_registration) – Complete the registration process and create account, user, and API key.

**Attributes:**

- [**account_service**](#leadr.registration.services.registration_service.RegistrationService.account_service) –
- [**api_key_service**](#leadr.registration.services.registration_service.RegistrationService.api_key_service) –
- [**db**](#leadr.registration.services.registration_service.RegistrationService.db) –
- [**email_service**](#leadr.registration.services.registration_service.RegistrationService.email_service) –
- [**jam_code_service**](#leadr.registration.services.registration_service.RegistrationService.jam_code_service) –
- [**user_service**](#leadr.registration.services.registration_service.RegistrationService.user_service) –
- [**verification_service**](#leadr.registration.services.registration_service.RegistrationService.verification_service) –

**Parameters:**

- **db** (<code>[AsyncSession](#sqlalchemy.ext.asyncio.AsyncSession)</code>) – Database session.
- **account_service** (<code>[AccountService](#leadr.accounts.services.account_service.AccountService)</code>) – Service for account operations.
- **user_service** (<code>[UserService](#leadr.accounts.services.user_service.UserService)</code>) – Service for user operations.
- **api_key_service** (<code>[APIKeyService](#leadr.auth.services.api_key_service.APIKeyService)</code>) – Service for API key operations.
- **verification_service** (<code>[VerificationService](#leadr.registration.services.verification_service.VerificationService)</code>) – Service for email verification.
- **jam_code_service** (<code>[JamCodeService](#leadr.registration.services.jam_code_service.JamCodeService)</code>) – Service for jam code validation.
- **email_service** (<code>[EmailService](./infra.md#leadr.infra.email.EmailService)</code>) – Service for sending emails.

####### `leadr.registration.services.registration_service.RegistrationService.account_service`

```python
account_service = account_service
```

####### `leadr.registration.services.registration_service.RegistrationService.api_key_service`

```python
api_key_service = api_key_service
```

####### `leadr.registration.services.registration_service.RegistrationService.complete_registration`

```python
complete_registration(verification_token, account_name=None, account_slug=None, jam_code=None, display_name=None)
```

Complete the registration process and create account, user, and API key.

For invite flow: If the verification token contains a user_id, this is an
invite completion. The existing invited user is activated and an API key
is created. Account creation is skipped.

For registration flow: A new account, user, and API key are created.

**Parameters:**

- **verification_token** (<code>[str](#str)</code>) – JWT token from email verification.
- **account_name** (<code>[str](#str) | None</code>) – Name for the new account (required for registration, ignored for invite).
- **account_slug** (<code>[str](#str) | None</code>) – Optional slug (will be auto-generated if not provided).
- **jam_code** (<code>[str](#str) | None</code>) – Optional jam code for promotional features (registration only).
- **display_name** (<code>[str](#str) | None</code>) – Optional display name (will use email prefix if not provided).

**Returns:**

- <code>[tuple](#tuple)\[[Account](./accounts.md#leadr.accounts.domain.account.Account), [User](./accounts.md#leadr.accounts.domain.user.User), [str](#str)\]</code> – Tuple of (Account, User, plain_api_key).

**Raises:**

- <code>[ValueError](#ValueError)</code> – If verification token is invalid or jam code is invalid.
- <code>[ValueError](#ValueError)</code> – If account_name is missing for registration flow.

####### `leadr.registration.services.registration_service.RegistrationService.db`

```python
db = db
```

####### `leadr.registration.services.registration_service.RegistrationService.email_service`

```python
email_service = email_service
```

####### `leadr.registration.services.registration_service.RegistrationService.jam_code_service`

```python
jam_code_service = jam_code_service
```

####### `leadr.registration.services.registration_service.RegistrationService.user_service`

```python
user_service = user_service
```

####### `leadr.registration.services.registration_service.RegistrationService.verification_service`

```python
verification_service = verification_service
```

##### `leadr.registration.services.repositories`

Registration repository services for verification codes and jam codes.

**Classes:**

- [**JamCodeRedemptionRepository**](./registration.md#leadr.registration.services.repositories.JamCodeRedemptionRepository) – Jam code redemption repository for tracking code usage.
- [**JamCodeRepository**](./registration.md#leadr.registration.services.repositories.JamCodeRepository) – Jam code repository for managing promotional codes.
- [**VerificationCodeRepository**](./registration.md#leadr.registration.services.repositories.VerificationCodeRepository) – Verification code repository for managing email verification codes.

###### `leadr.registration.services.repositories.JamCodeRedemptionRepository`

Bases: <code>[BaseRepository](./common.md#leadr.common.repositories.BaseRepository)\[[JamCodeRedemption](#leadr.registration.domain.jam_code_redemption.JamCodeRedemption), [JamCodeRedemptionORM](./registration.md#leadr.registration.adapters.orm.JamCodeRedemptionORM)\]</code>

Jam code redemption repository for tracking code usage.

**Functions:**

- [**create**](./registration.md#leadr.registration.services.repositories.JamCodeRedemptionRepository.create) – Create a new entity in the database.
- [**delete**](./registration.md#leadr.registration.services.repositories.JamCodeRedemptionRepository.delete) – Soft delete an entity by setting its deleted_at timestamp.
- [**filter**](./registration.md#leadr.registration.services.repositories.JamCodeRedemptionRepository.filter) – Filter jam code redemptions by criteria with pagination.
- [**find_by_account**](#leadr.registration.services.repositories.JamCodeRedemptionRepository.find_by_account) – Find all jam code redemptions for an account.
- [**get_by_id**](#leadr.registration.services.repositories.JamCodeRedemptionRepository.get_by_id) – Get an entity by its ID.
- [**has_redeemed**](#leadr.registration.services.repositories.JamCodeRedemptionRepository.has_redeemed) – Check if an account has already redeemed a specific jam code.
- [**update**](./registration.md#leadr.registration.services.repositories.JamCodeRedemptionRepository.update) – Update an existing entity in the database.

**Attributes:**

- [**SORTABLE_FIELDS**](#leadr.registration.services.repositories.JamCodeRedemptionRepository.SORTABLE_FIELDS) –
- [**session**](./registration.md#leadr.registration.services.repositories.JamCodeRedemptionRepository.session) –

####### `leadr.registration.services.repositories.JamCodeRedemptionRepository.SORTABLE_FIELDS`

```python
SORTABLE_FIELDS = {'id', 'account_id', 'jam_code_id', 'created_at'}
```

####### `leadr.registration.services.repositories.JamCodeRedemptionRepository.create`

```python
create(entity)
```

Create a new entity in the database.

**Parameters:**

- **entity** (<code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code>) – Domain entity to create

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code> – Created domain entity with refreshed data

####### `leadr.registration.services.repositories.JamCodeRedemptionRepository.delete`

```python
delete(entity_id)
```

Soft delete an entity by setting its deleted_at timestamp.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – ID of entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

####### `leadr.registration.services.repositories.JamCodeRedemptionRepository.filter`

```python
filter(account_id=None, *, pagination, **kwargs)
```

Filter jam code redemptions by criteria with pagination.

**Parameters:**

- **account_id** (<code>[Any](#typing.Any) | None</code>) – Optional account ID to filter by.
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (required).
- \*\***kwargs** (<code>[Any](#typing.Any)</code>) – Additional filter parameters.

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[JamCodeRedemption](#leadr.registration.domain.jam_code_redemption.JamCodeRedemption)\]</code> – Paginated result of matching JamCodeRedemption entities.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If sort field is not in SORTABLE_FIELDS.
- <code>[CursorValidationError](#CursorValidationError)</code> – If cursor is invalid or state doesn't match.

####### `leadr.registration.services.repositories.JamCodeRedemptionRepository.find_by_account`

```python
find_by_account(account_id)
```

Find all jam code redemptions for an account.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – The account ID.

**Returns:**

- <code>[list](#list)\[[JamCodeRedemption](#leadr.registration.domain.jam_code_redemption.JamCodeRedemption)\]</code> – List of redemptions for the account.

####### `leadr.registration.services.repositories.JamCodeRedemptionRepository.get_by_id`

```python
get_by_id(entity_id, include_deleted=False)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – Entity ID to retrieve
- **include_deleted** (<code>[bool](#bool)</code>) – If True, include soft-deleted entities. Defaults to False.

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT) | None</code> – Domain entity if found, None otherwise

####### `leadr.registration.services.repositories.JamCodeRedemptionRepository.has_redeemed`

```python
has_redeemed(account_id, jam_code_id)
```

Check if an account has already redeemed a specific jam code.

**Parameters:**

- **account_id** (<code>[AccountID](./common.md#leadr.common.domain.ids.AccountID)</code>) – The account ID.
- **jam_code_id** (<code>[UUID](#uuid.UUID)</code>) – The jam code ID.

**Returns:**

- <code>[bool](#bool)</code> – True if the account has redeemed this code, False otherwise.

####### `leadr.registration.services.repositories.JamCodeRedemptionRepository.session`

```python
session = session
```

####### `leadr.registration.services.repositories.JamCodeRedemptionRepository.update`

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

###### `leadr.registration.services.repositories.JamCodeRepository`

Bases: <code>[BaseRepository](./common.md#leadr.common.repositories.BaseRepository)\[[JamCode](#leadr.registration.domain.jam_code.JamCode), [JamCodeORM](./registration.md#leadr.registration.adapters.orm.JamCodeORM)\]</code>

Jam code repository for managing promotional codes.

**Functions:**

- [**create**](./registration.md#leadr.registration.services.repositories.JamCodeRepository.create) – Create a new entity in the database.
- [**delete**](./registration.md#leadr.registration.services.repositories.JamCodeRepository.delete) – Soft delete an entity by setting its deleted_at timestamp.
- [**filter**](./registration.md#leadr.registration.services.repositories.JamCodeRepository.filter) – Filter jam codes by criteria with pagination.
- [**find_by_code**](#leadr.registration.services.repositories.JamCodeRepository.find_by_code) – Find a jam code by its code value.
- [**get_by_id**](#leadr.registration.services.repositories.JamCodeRepository.get_by_id) – Get an entity by its ID.
- [**update**](./registration.md#leadr.registration.services.repositories.JamCodeRepository.update) – Update an existing entity in the database.

**Attributes:**

- [**SORTABLE_FIELDS**](#leadr.registration.services.repositories.JamCodeRepository.SORTABLE_FIELDS) –
- [**session**](./registration.md#leadr.registration.services.repositories.JamCodeRepository.session) –

####### `leadr.registration.services.repositories.JamCodeRepository.SORTABLE_FIELDS`

```python
SORTABLE_FIELDS = {'id', 'code', 'active', 'current_uses', 'max_uses', 'created_at', 'updated_at'}
```

####### `leadr.registration.services.repositories.JamCodeRepository.create`

```python
create(entity)
```

Create a new entity in the database.

**Parameters:**

- **entity** (<code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code>) – Domain entity to create

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code> – Created domain entity with refreshed data

####### `leadr.registration.services.repositories.JamCodeRepository.delete`

```python
delete(entity_id)
```

Soft delete an entity by setting its deleted_at timestamp.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – ID of entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

####### `leadr.registration.services.repositories.JamCodeRepository.filter`

```python
filter(account_id=None, *, pagination, **kwargs)
```

Filter jam codes by criteria with pagination.

**Parameters:**

- **account_id** (<code>[Any](#typing.Any) | None</code>) – Not used for jam codes (top-level entity).
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (required).
- \*\***kwargs** (<code>[Any](#typing.Any)</code>) – Filter parameters (code, etc.)

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[JamCode](#leadr.registration.domain.jam_code.JamCode)\]</code> – Paginated result of matching JamCode entities.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If sort field is not in SORTABLE_FIELDS.
- <code>[CursorValidationError](#CursorValidationError)</code> – If cursor is invalid or state doesn't match.

####### `leadr.registration.services.repositories.JamCodeRepository.find_by_code`

```python
find_by_code(code)
```

Find a jam code by its code value.

**Parameters:**

- **code** (<code>[str](#str)</code>) – The jam code to look up (case-insensitive).

**Returns:**

- <code>[JamCode](#leadr.registration.domain.jam_code.JamCode) | None</code> – The jam code if found, None otherwise.

####### `leadr.registration.services.repositories.JamCodeRepository.get_by_id`

```python
get_by_id(entity_id, include_deleted=False)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – Entity ID to retrieve
- **include_deleted** (<code>[bool](#bool)</code>) – If True, include soft-deleted entities. Defaults to False.

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT) | None</code> – Domain entity if found, None otherwise

####### `leadr.registration.services.repositories.JamCodeRepository.session`

```python
session = session
```

####### `leadr.registration.services.repositories.JamCodeRepository.update`

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

###### `leadr.registration.services.repositories.VerificationCodeRepository`

Bases: <code>[BaseRepository](./common.md#leadr.common.repositories.BaseRepository)\[[VerificationCode](#leadr.registration.domain.verification_code.VerificationCode), [VerificationCodeORM](./registration.md#leadr.registration.adapters.orm.VerificationCodeORM)\]</code>

Verification code repository for managing email verification codes.

**Functions:**

- [**create**](./registration.md#leadr.registration.services.repositories.VerificationCodeRepository.create) – Create a new entity in the database.
- [**delete**](./registration.md#leadr.registration.services.repositories.VerificationCodeRepository.delete) – Soft delete an entity by setting its deleted_at timestamp.
- [**filter**](./registration.md#leadr.registration.services.repositories.VerificationCodeRepository.filter) – Filter verification codes by criteria with pagination.
- [**find_valid_code_by_email**](#leadr.registration.services.repositories.VerificationCodeRepository.find_valid_code_by_email) – Find a valid (pending) verification code by email and code value.
- [**get_by_id**](#leadr.registration.services.repositories.VerificationCodeRepository.get_by_id) – Get an entity by its ID.
- [**get_pending_invite_for_user**](#leadr.registration.services.repositories.VerificationCodeRepository.get_pending_invite_for_user) – Get a pending invite code for a specific user.
- [**invalidate_codes_for_email**](#leadr.registration.services.repositories.VerificationCodeRepository.invalidate_codes_for_email) – Mark all pending verification codes for an email as expired.
- [**update**](./registration.md#leadr.registration.services.repositories.VerificationCodeRepository.update) – Update an existing entity in the database.

**Attributes:**

- [**SORTABLE_FIELDS**](#leadr.registration.services.repositories.VerificationCodeRepository.SORTABLE_FIELDS) –
- [**session**](./registration.md#leadr.registration.services.repositories.VerificationCodeRepository.session) –

####### `leadr.registration.services.repositories.VerificationCodeRepository.SORTABLE_FIELDS`

```python
SORTABLE_FIELDS = {'id', 'email', 'status', 'created_at', 'updated_at', 'expires_at'}
```

####### `leadr.registration.services.repositories.VerificationCodeRepository.create`

```python
create(entity)
```

Create a new entity in the database.

**Parameters:**

- **entity** (<code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code>) – Domain entity to create

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code> – Created domain entity with refreshed data

####### `leadr.registration.services.repositories.VerificationCodeRepository.delete`

```python
delete(entity_id)
```

Soft delete an entity by setting its deleted_at timestamp.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – ID of entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

####### `leadr.registration.services.repositories.VerificationCodeRepository.filter`

```python
filter(account_id=None, *, pagination, **kwargs)
```

Filter verification codes by criteria with pagination.

**Parameters:**

- **account_id** (<code>[Any](#typing.Any) | None</code>) – Not used for verification codes (top-level entity).
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (required).
- \*\***kwargs** (<code>[Any](#typing.Any)</code>) – Filter parameters (email, status, etc.)

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[VerificationCode](#leadr.registration.domain.verification_code.VerificationCode)\]</code> – Paginated result of matching VerificationCode entities.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If sort field is not in SORTABLE_FIELDS.
- <code>[CursorValidationError](#CursorValidationError)</code> – If cursor is invalid or state doesn't match.

####### `leadr.registration.services.repositories.VerificationCodeRepository.find_valid_code_by_email`

```python
find_valid_code_by_email(email, code, code_type=None)
```

Find a valid (pending) verification code by email and code value.

**Parameters:**

- **email** (<code>[str](#str)</code>) – The email address.
- **code** (<code>[str](#str)</code>) – The verification code.
- **code_type** (<code>[VerificationCodeTypeEnum](./registration.md#leadr.registration.adapters.orm.VerificationCodeTypeEnum) | None</code>) – Optional code type filter (REGISTRATION or INVITE).

**Returns:**

- <code>[VerificationCode](#leadr.registration.domain.verification_code.VerificationCode) | None</code> – The verification code if found and valid, None otherwise.

####### `leadr.registration.services.repositories.VerificationCodeRepository.get_by_id`

```python
get_by_id(entity_id, include_deleted=False)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – Entity ID to retrieve
- **include_deleted** (<code>[bool](#bool)</code>) – If True, include soft-deleted entities. Defaults to False.

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT) | None</code> – Domain entity if found, None otherwise

####### `leadr.registration.services.repositories.VerificationCodeRepository.get_pending_invite_for_user`

```python
get_pending_invite_for_user(user_id)
```

Get a pending invite code for a specific user.

**Parameters:**

- **user_id** (<code>[UserID](./common.md#leadr.common.domain.ids.UserID)</code>) – The user ID to look up invite code for.

**Returns:**

- <code>[VerificationCode](#leadr.registration.domain.verification_code.VerificationCode) | None</code> – The pending invite verification code if found, None otherwise.

####### `leadr.registration.services.repositories.VerificationCodeRepository.invalidate_codes_for_email`

```python
invalidate_codes_for_email(email)
```

Mark all pending verification codes for an email as expired.

Used when generating a new code to invalidate previous ones.

**Parameters:**

- **email** (<code>[str](#str)</code>) – The email address.

####### `leadr.registration.services.repositories.VerificationCodeRepository.session`

```python
session = session
```

####### `leadr.registration.services.repositories.VerificationCodeRepository.update`

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

##### `leadr.registration.services.verification_service`

Verification service for generating and validating email verification codes.

**Classes:**

- [**VerificationService**](#leadr.registration.services.verification_service.VerificationService) – Service for managing email verification codes.

###### `leadr.registration.services.verification_service.VerificationService`

```python
VerificationService(db, email_service)
```

Service for managing email verification codes.

**Functions:**

- [**create_invite_code**](#leadr.registration.services.verification_service.VerificationService.create_invite_code) – Create an invite verification code for an existing user.
- [**get_invite_user_id**](#leadr.registration.services.verification_service.VerificationService.get_invite_user_id) – Extract the user_id from an invite verification token.
- [**initiate_verification**](#leadr.registration.services.verification_service.VerificationService.initiate_verification) – Generate and send a verification code to an email address.
- [**validate_verification_token**](#leadr.registration.services.verification_service.VerificationService.validate_verification_token) – Validate a verification token and return the email.
- [**verify_code**](#leadr.registration.services.verification_service.VerificationService.verify_code) – Verify a code and return a short-lived verification token with its type.

**Attributes:**

- [**db**](#leadr.registration.services.verification_service.VerificationService.db) –
- [**email_service**](#leadr.registration.services.verification_service.VerificationService.email_service) –
- [**repository**](#leadr.registration.services.verification_service.VerificationService.repository) –

**Parameters:**

- **db** (<code>[AsyncSession](#sqlalchemy.ext.asyncio.AsyncSession)</code>) – Database session.
- **email_service** (<code>[EmailService](./infra.md#leadr.infra.email.EmailService)</code>) – Email service for sending verification codes.

####### `leadr.registration.services.verification_service.VerificationService.create_invite_code`

```python
create_invite_code(email, user_id)
```

Create an invite verification code for an existing user.

Invalidates any existing pending invite codes for the email before creating a new one.

**Parameters:**

- **email** (<code>[str](#str)</code>) – Email address to send the invite code to.
- **user_id** (<code>[UserID](./common.md#leadr.common.domain.ids.UserID)</code>) – The ID of the user being invited.

**Returns:**

- <code>[VerificationCode](#leadr.registration.domain.verification_code.VerificationCode)</code> – The created verification code entity.

####### `leadr.registration.services.verification_service.VerificationService.db`

```python
db = db
```

####### `leadr.registration.services.verification_service.VerificationService.email_service`

```python
email_service = email_service
```

####### `leadr.registration.services.verification_service.VerificationService.get_invite_user_id`

```python
get_invite_user_id(token)
```

Extract the user_id from an invite verification token.

**Parameters:**

- **token** (<code>[str](#str)</code>) – JWT verification token.

**Returns:**

- <code>[UserID](./common.md#leadr.common.domain.ids.UserID) | None</code> – The UserID if this is an invite token, None otherwise.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If the token is invalid or expired.

####### `leadr.registration.services.verification_service.VerificationService.initiate_verification`

```python
initiate_verification(email)
```

Generate and send a verification code to an email address.

Invalidates any existing pending codes for the email before creating a new one.

**Parameters:**

- **email** (<code>[str](#str)</code>) – Email address to send the verification code to.

####### `leadr.registration.services.verification_service.VerificationService.repository`

```python
repository = VerificationCodeRepository(db)
```

####### `leadr.registration.services.verification_service.VerificationService.validate_verification_token`

```python
validate_verification_token(token)
```

Validate a verification token and return the email.

**Parameters:**

- **token** (<code>[str](#str)</code>) – JWT verification token.

**Returns:**

- <code>[str](#str)</code> – The email address from the token.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If the token is invalid or expired.

####### `leadr.registration.services.verification_service.VerificationService.verify_code`

```python
verify_code(email, code)
```

Verify a code and return a short-lived verification token with its type.

**Parameters:**

- **email** (<code>[str](#str)</code>) – Email address to verify.
- **code** (<code>[str](#str)</code>) – Verification code to check.

**Returns:**

- <code>[str](#str)</code> – A tuple of (JWT verification token, VerificationCodeType).
- <code>[VerificationCodeType](#leadr.registration.domain.verification_code.VerificationCodeType)</code> – For invite codes, the token includes user_id.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If the code is invalid, expired, or already used.
