### `leadr.infra`

**Modules:**

- [**blob_storage**](#leadr.infra.blob_storage) –
- [**cache**](./infra.md#leadr.infra.cache) – Cache infrastructure module.
- [**email**](./infra.md#leadr.infra.email) – Email infrastructure domain with factory functions for easy integration.

#### `leadr.infra.blob_storage`

**Modules:**

- [**adapters**](#leadr.infra.blob_storage.adapters) –
- [**domain**](#leadr.infra.blob_storage.domain) –
- [**services**](#leadr.infra.blob_storage.services) –

##### `leadr.infra.blob_storage.adapters`

##### `leadr.infra.blob_storage.domain`

##### `leadr.infra.blob_storage.services`

#### `leadr.infra.cache`

Cache infrastructure module.

**Modules:**

- [**adapters**](./infra.md#leadr.infra.cache.adapters) – Cache adapters module.
- [**domain**](./infra.md#leadr.infra.cache.domain) – Cache domain module.
- [**services**](./infra.md#leadr.infra.cache.services) – Cache services module.

**Classes:**

- [**CacheBackend**](./infra.md#leadr.infra.cache.CacheBackend) – Protocol for cache backends.
- [**InMemoryCache**](./infra.md#leadr.infra.cache.InMemoryCache) – Thread-safe in-memory cache with TTL support.

**Functions:**

- [**get_cache**](#leadr.infra.cache.get_cache) – Get the cache backend singleton.

**Attributes:**

- [**CacheDep**](./infra.md#leadr.infra.cache.CacheDep) –

##### `leadr.infra.cache.CacheBackend`

Bases: <code>[Protocol](#typing.Protocol)</code>

Protocol for cache backends.

Defines the interface for cache implementations.
This abstraction allows swapping cache backends (e.g., in-memory to Redis)
without changing the consuming code.

**Functions:**

- [**delete**](./infra.md#leadr.infra.cache.CacheBackend.delete) – Delete a key from the cache.
- [**get**](./infra.md#leadr.infra.cache.CacheBackend.get) – Get a value from the cache.
- [**set**](./infra.md#leadr.infra.cache.CacheBackend.set) – Set a value in the cache with a TTL.

###### `leadr.infra.cache.CacheBackend.delete`

```python
delete(key)
```

Delete a key from the cache.

**Parameters:**

- **key** (<code>[str](#str)</code>) – The cache key to delete.

###### `leadr.infra.cache.CacheBackend.get`

```python
get(key)
```

Get a value from the cache.

**Parameters:**

- **key** (<code>[str](#str)</code>) – The cache key to retrieve.

**Returns:**

- <code>[Any](#typing.Any) | None</code> – The cached value, or None if not found or expired.

###### `leadr.infra.cache.CacheBackend.set`

```python
set(key, value, ttl_seconds)
```

Set a value in the cache with a TTL.

**Parameters:**

- **key** (<code>[str](#str)</code>) – The cache key.
- **value** (<code>[Any](#typing.Any)</code>) – The value to cache.
- **ttl_seconds** (<code>[int](#int)</code>) – Time-to-live in seconds.

##### `leadr.infra.cache.CacheDep`

```python
CacheDep = Annotated[CacheBackend, Depends(get_cache)]
```

##### `leadr.infra.cache.InMemoryCache`

```python
InMemoryCache()
```

Thread-safe in-memory cache with TTL support.

This implementation uses a simple dict with expiration checking on read.
Suitable for single-process applications. For multi-process or distributed
deployments, replace with a Redis-backed implementation.

<details class="usage" open markdown="1">
<summary>Usage</summary>

# Create a new instance

cache = InMemoryCache()
cache.set("key", "value", ttl_seconds=60)
value = cache.get("key")

# Or use the singleton for application-wide caching

cache = InMemoryCache.get_instance()

</details>

**Functions:**

- [**clear**](./infra.md#leadr.infra.cache.InMemoryCache.clear) – Clear all entries from the cache.
- [**delete**](./infra.md#leadr.infra.cache.InMemoryCache.delete) – Delete a key from the cache.
- [**get**](./infra.md#leadr.infra.cache.InMemoryCache.get) – Get a value from the cache.
- [**get_instance**](#leadr.infra.cache.InMemoryCache.get_instance) – Get the singleton instance.
- [**reset_instance**](#leadr.infra.cache.InMemoryCache.reset_instance) – Reset the singleton instance.
- [**set**](./infra.md#leadr.infra.cache.InMemoryCache.set) – Set a value in the cache with a TTL.

###### `leadr.infra.cache.InMemoryCache.clear`

```python
clear()
```

Clear all entries from the cache.

###### `leadr.infra.cache.InMemoryCache.delete`

```python
delete(key)
```

Delete a key from the cache.

**Parameters:**

- **key** (<code>[str](#str)</code>) – The cache key to delete.

###### `leadr.infra.cache.InMemoryCache.get`

```python
get(key)
```

Get a value from the cache.

**Parameters:**

- **key** (<code>[str](#str)</code>) – The cache key to retrieve.

**Returns:**

- <code>[Any](#typing.Any) | None</code> – The cached value, or None if not found or expired.

###### `leadr.infra.cache.InMemoryCache.get_instance`

```python
get_instance()
```

Get the singleton instance.

Thread-safe singleton pattern for application-wide caching.

**Returns:**

- <code>[InMemoryCache](./infra.md#leadr.infra.cache.adapters.memory.InMemoryCache)</code> – The singleton InMemoryCache instance.

###### `leadr.infra.cache.InMemoryCache.reset_instance`

```python
reset_instance()
```

Reset the singleton instance.

Primarily useful for testing to ensure a clean state.

###### `leadr.infra.cache.InMemoryCache.set`

```python
set(key, value, ttl_seconds)
```

Set a value in the cache with a TTL.

**Parameters:**

- **key** (<code>[str](#str)</code>) – The cache key.
- **value** (<code>[Any](#typing.Any)</code>) – The value to cache.
- **ttl_seconds** (<code>[int](#int)</code>) – Time-to-live in seconds.

##### `leadr.infra.cache.adapters`

Cache adapters module.

**Modules:**

- [**memory**](./infra.md#leadr.infra.cache.adapters.memory) – In-memory cache implementation.

**Classes:**

- [**InMemoryCache**](./infra.md#leadr.infra.cache.adapters.InMemoryCache) – Thread-safe in-memory cache with TTL support.

###### `leadr.infra.cache.adapters.InMemoryCache`

```python
InMemoryCache()
```

Thread-safe in-memory cache with TTL support.

This implementation uses a simple dict with expiration checking on read.
Suitable for single-process applications. For multi-process or distributed
deployments, replace with a Redis-backed implementation.

<details class="usage" open markdown="1">
<summary>Usage</summary>

# Create a new instance

cache = InMemoryCache()
cache.set("key", "value", ttl_seconds=60)
value = cache.get("key")

# Or use the singleton for application-wide caching

cache = InMemoryCache.get_instance()

</details>

**Functions:**

- [**clear**](./infra.md#leadr.infra.cache.adapters.InMemoryCache.clear) – Clear all entries from the cache.
- [**delete**](./infra.md#leadr.infra.cache.adapters.InMemoryCache.delete) – Delete a key from the cache.
- [**get**](./infra.md#leadr.infra.cache.adapters.InMemoryCache.get) – Get a value from the cache.
- [**get_instance**](#leadr.infra.cache.adapters.InMemoryCache.get_instance) – Get the singleton instance.
- [**reset_instance**](#leadr.infra.cache.adapters.InMemoryCache.reset_instance) – Reset the singleton instance.
- [**set**](./infra.md#leadr.infra.cache.adapters.InMemoryCache.set) – Set a value in the cache with a TTL.

####### `leadr.infra.cache.adapters.InMemoryCache.clear`

```python
clear()
```

Clear all entries from the cache.

####### `leadr.infra.cache.adapters.InMemoryCache.delete`

```python
delete(key)
```

Delete a key from the cache.

**Parameters:**

- **key** (<code>[str](#str)</code>) – The cache key to delete.

####### `leadr.infra.cache.adapters.InMemoryCache.get`

```python
get(key)
```

Get a value from the cache.

**Parameters:**

- **key** (<code>[str](#str)</code>) – The cache key to retrieve.

**Returns:**

- <code>[Any](#typing.Any) | None</code> – The cached value, or None if not found or expired.

####### `leadr.infra.cache.adapters.InMemoryCache.get_instance`

```python
get_instance()
```

Get the singleton instance.

Thread-safe singleton pattern for application-wide caching.

**Returns:**

- <code>[InMemoryCache](./infra.md#leadr.infra.cache.adapters.memory.InMemoryCache)</code> – The singleton InMemoryCache instance.

####### `leadr.infra.cache.adapters.InMemoryCache.reset_instance`

```python
reset_instance()
```

Reset the singleton instance.

Primarily useful for testing to ensure a clean state.

####### `leadr.infra.cache.adapters.InMemoryCache.set`

```python
set(key, value, ttl_seconds)
```

Set a value in the cache with a TTL.

**Parameters:**

- **key** (<code>[str](#str)</code>) – The cache key.
- **value** (<code>[Any](#typing.Any)</code>) – The value to cache.
- **ttl_seconds** (<code>[int](#int)</code>) – Time-to-live in seconds.

###### `leadr.infra.cache.adapters.memory`

In-memory cache implementation.

**Classes:**

- [**CacheEntry**](./infra.md#leadr.infra.cache.adapters.memory.CacheEntry) – A cache entry with value and expiration time.
- [**InMemoryCache**](./infra.md#leadr.infra.cache.adapters.memory.InMemoryCache) – Thread-safe in-memory cache with TTL support.

####### `leadr.infra.cache.adapters.memory.CacheEntry`

```python
CacheEntry(value, expires_at)
```

A cache entry with value and expiration time.

**Attributes:**

- [**expires_at**](#leadr.infra.cache.adapters.memory.CacheEntry.expires_at) (<code>[float](#float)</code>) –
- [**value**](#leadr.infra.cache.adapters.memory.CacheEntry.value) (<code>[Any](#typing.Any)</code>) –

######## `leadr.infra.cache.adapters.memory.CacheEntry.expires_at`

```python
expires_at: float
```

######## `leadr.infra.cache.adapters.memory.CacheEntry.value`

```python
value: Any
```

####### `leadr.infra.cache.adapters.memory.InMemoryCache`

```python
InMemoryCache()
```

Thread-safe in-memory cache with TTL support.

This implementation uses a simple dict with expiration checking on read.
Suitable for single-process applications. For multi-process or distributed
deployments, replace with a Redis-backed implementation.

<details class="usage" open markdown="1">
<summary>Usage</summary>

# Create a new instance

cache = InMemoryCache()
cache.set("key", "value", ttl_seconds=60)
value = cache.get("key")

# Or use the singleton for application-wide caching

cache = InMemoryCache.get_instance()

</details>

**Functions:**

- [**clear**](#leadr.infra.cache.adapters.memory.InMemoryCache.clear) – Clear all entries from the cache.
- [**delete**](#leadr.infra.cache.adapters.memory.InMemoryCache.delete) – Delete a key from the cache.
- [**get**](#leadr.infra.cache.adapters.memory.InMemoryCache.get) – Get a value from the cache.
- [**get_instance**](#leadr.infra.cache.adapters.memory.InMemoryCache.get_instance) – Get the singleton instance.
- [**reset_instance**](#leadr.infra.cache.adapters.memory.InMemoryCache.reset_instance) – Reset the singleton instance.
- [**set**](#leadr.infra.cache.adapters.memory.InMemoryCache.set) – Set a value in the cache with a TTL.

######## `leadr.infra.cache.adapters.memory.InMemoryCache.clear`

```python
clear()
```

Clear all entries from the cache.

######## `leadr.infra.cache.adapters.memory.InMemoryCache.delete`

```python
delete(key)
```

Delete a key from the cache.

**Parameters:**

- **key** (<code>[str](#str)</code>) – The cache key to delete.

######## `leadr.infra.cache.adapters.memory.InMemoryCache.get`

```python
get(key)
```

Get a value from the cache.

**Parameters:**

- **key** (<code>[str](#str)</code>) – The cache key to retrieve.

**Returns:**

- <code>[Any](#typing.Any) | None</code> – The cached value, or None if not found or expired.

######## `leadr.infra.cache.adapters.memory.InMemoryCache.get_instance`

```python
get_instance()
```

Get the singleton instance.

Thread-safe singleton pattern for application-wide caching.

**Returns:**

- <code>[InMemoryCache](./infra.md#leadr.infra.cache.adapters.memory.InMemoryCache)</code> – The singleton InMemoryCache instance.

######## `leadr.infra.cache.adapters.memory.InMemoryCache.reset_instance`

```python
reset_instance()
```

Reset the singleton instance.

Primarily useful for testing to ensure a clean state.

######## `leadr.infra.cache.adapters.memory.InMemoryCache.set`

```python
set(key, value, ttl_seconds)
```

Set a value in the cache with a TTL.

**Parameters:**

- **key** (<code>[str](#str)</code>) – The cache key.
- **value** (<code>[Any](#typing.Any)</code>) – The value to cache.
- **ttl_seconds** (<code>[int](#int)</code>) – Time-to-live in seconds.

##### `leadr.infra.cache.domain`

Cache domain module.

**Modules:**

- [**interfaces**](./infra.md#leadr.infra.cache.domain.interfaces) – Cache backend protocol definition.

**Classes:**

- [**CacheBackend**](./infra.md#leadr.infra.cache.domain.CacheBackend) – Protocol for cache backends.

###### `leadr.infra.cache.domain.CacheBackend`

Bases: <code>[Protocol](#typing.Protocol)</code>

Protocol for cache backends.

Defines the interface for cache implementations.
This abstraction allows swapping cache backends (e.g., in-memory to Redis)
without changing the consuming code.

**Functions:**

- [**delete**](./infra.md#leadr.infra.cache.domain.CacheBackend.delete) – Delete a key from the cache.
- [**get**](./infra.md#leadr.infra.cache.domain.CacheBackend.get) – Get a value from the cache.
- [**set**](./infra.md#leadr.infra.cache.domain.CacheBackend.set) – Set a value in the cache with a TTL.

####### `leadr.infra.cache.domain.CacheBackend.delete`

```python
delete(key)
```

Delete a key from the cache.

**Parameters:**

- **key** (<code>[str](#str)</code>) – The cache key to delete.

####### `leadr.infra.cache.domain.CacheBackend.get`

```python
get(key)
```

Get a value from the cache.

**Parameters:**

- **key** (<code>[str](#str)</code>) – The cache key to retrieve.

**Returns:**

- <code>[Any](#typing.Any) | None</code> – The cached value, or None if not found or expired.

####### `leadr.infra.cache.domain.CacheBackend.set`

```python
set(key, value, ttl_seconds)
```

Set a value in the cache with a TTL.

**Parameters:**

- **key** (<code>[str](#str)</code>) – The cache key.
- **value** (<code>[Any](#typing.Any)</code>) – The value to cache.
- **ttl_seconds** (<code>[int](#int)</code>) – Time-to-live in seconds.

###### `leadr.infra.cache.domain.interfaces`

Cache backend protocol definition.

**Classes:**

- [**CacheBackend**](./infra.md#leadr.infra.cache.domain.interfaces.CacheBackend) – Protocol for cache backends.

####### `leadr.infra.cache.domain.interfaces.CacheBackend`

Bases: <code>[Protocol](#typing.Protocol)</code>

Protocol for cache backends.

Defines the interface for cache implementations.
This abstraction allows swapping cache backends (e.g., in-memory to Redis)
without changing the consuming code.

**Functions:**

- [**delete**](#leadr.infra.cache.domain.interfaces.CacheBackend.delete) – Delete a key from the cache.
- [**get**](#leadr.infra.cache.domain.interfaces.CacheBackend.get) – Get a value from the cache.
- [**set**](#leadr.infra.cache.domain.interfaces.CacheBackend.set) – Set a value in the cache with a TTL.

######## `leadr.infra.cache.domain.interfaces.CacheBackend.delete`

```python
delete(key)
```

Delete a key from the cache.

**Parameters:**

- **key** (<code>[str](#str)</code>) – The cache key to delete.

######## `leadr.infra.cache.domain.interfaces.CacheBackend.get`

```python
get(key)
```

Get a value from the cache.

**Parameters:**

- **key** (<code>[str](#str)</code>) – The cache key to retrieve.

**Returns:**

- <code>[Any](#typing.Any) | None</code> – The cached value, or None if not found or expired.

######## `leadr.infra.cache.domain.interfaces.CacheBackend.set`

```python
set(key, value, ttl_seconds)
```

Set a value in the cache with a TTL.

**Parameters:**

- **key** (<code>[str](#str)</code>) – The cache key.
- **value** (<code>[Any](#typing.Any)</code>) – The value to cache.
- **ttl_seconds** (<code>[int](#int)</code>) – Time-to-live in seconds.

##### `leadr.infra.cache.get_cache`

```python
get_cache()
```

Get the cache backend singleton.

**Returns:**

- <code>[CacheBackend](./infra.md#leadr.infra.cache.domain.interfaces.CacheBackend)</code> – The application-wide cache backend instance.

##### `leadr.infra.cache.services`

Cache services module.

**Modules:**

- [**dependencies**](./infra.md#leadr.infra.cache.services.dependencies) – FastAPI dependencies for cache infrastructure.

**Functions:**

- [**get_cache**](#leadr.infra.cache.services.get_cache) – Get the cache backend singleton.

**Attributes:**

- [**CacheDep**](./infra.md#leadr.infra.cache.services.CacheDep) –

###### `leadr.infra.cache.services.CacheDep`

```python
CacheDep = Annotated[CacheBackend, Depends(get_cache)]
```

###### `leadr.infra.cache.services.dependencies`

FastAPI dependencies for cache infrastructure.

**Functions:**

- [**get_cache**](#leadr.infra.cache.services.dependencies.get_cache) – Get the cache backend singleton.

**Attributes:**

- [**CacheDep**](./infra.md#leadr.infra.cache.services.dependencies.CacheDep) –

####### `leadr.infra.cache.services.dependencies.CacheDep`

```python
CacheDep = Annotated[CacheBackend, Depends(get_cache)]
```

####### `leadr.infra.cache.services.dependencies.get_cache`

```python
get_cache()
```

Get the cache backend singleton.

**Returns:**

- <code>[CacheBackend](./infra.md#leadr.infra.cache.domain.interfaces.CacheBackend)</code> – The application-wide cache backend instance.

###### `leadr.infra.cache.services.get_cache`

```python
get_cache()
```

Get the cache backend singleton.

**Returns:**

- <code>[CacheBackend](./infra.md#leadr.infra.cache.domain.interfaces.CacheBackend)</code> – The application-wide cache backend instance.

#### `leadr.infra.email`

Email infrastructure domain with factory functions for easy integration.

**Modules:**

- [**adapters**](./infra.md#leadr.infra.email.adapters) – Email adapter implementations.
- [**domain**](./infra.md#leadr.infra.email.domain) – Email domain models and interfaces.
- [**service**](./infra.md#leadr.infra.email.service) – Email service with dependency injection and convenience methods.

**Classes:**

- [**Email**](./infra.md#leadr.infra.email.Email) – Email domain entity.
- [**EmailError**](./infra.md#leadr.infra.email.EmailError) – Base exception for email domain errors.
- [**EmailPriority**](./infra.md#leadr.infra.email.EmailPriority) – Email priority enumeration.
- [**EmailProvider**](./infra.md#leadr.infra.email.EmailProvider) – Interface for email service providers.
- [**EmailSendError**](./infra.md#leadr.infra.email.EmailSendError) – Raised when email sending fails.
- [**EmailService**](./infra.md#leadr.infra.email.EmailService) – Email service with dependency injection for testing and flexibility.
- [**EmailStatus**](./infra.md#leadr.infra.email.EmailStatus) – Email status enumeration.
- [**EmailValidationError**](./infra.md#leadr.infra.email.EmailValidationError) – Raised when email validation fails.
- [**MailgunEmailProvider**](./infra.md#leadr.infra.email.MailgunEmailProvider) – Mailgun email service provider implementation.
- [**SMTPEmailProvider**](./infra.md#leadr.infra.email.SMTPEmailProvider) – SMTP email provider implementation for development/testing.

**Functions:**

- [**create_email_service**](#leadr.infra.email.create_email_service) – Create an email service with the specified or default provider.

##### `leadr.infra.email.Email`

Bases: <code>[Entity](./common.md#leadr.common.domain.models.Entity)</code>

Email domain entity.

**Functions:**

- [**create**](./infra.md#leadr.infra.email.Email.create) – Create a new Email entity.
- [**mark_as_delivered**](#leadr.infra.email.Email.mark_as_delivered) – Mark email as delivered.
- [**mark_as_failed**](#leadr.infra.email.Email.mark_as_failed) – Mark email as failed.
- [**mark_as_sent**](#leadr.infra.email.Email.mark_as_sent) – Mark email as sent.
- [**restore**](./infra.md#leadr.infra.email.Email.restore) – Restore a soft-deleted entity.
- [**soft_delete**](#leadr.infra.email.Email.soft_delete) – Mark entity as soft-deleted.
- [**validate_bcc_emails**](#leadr.infra.email.Email.validate_bcc_emails) – Validate BCC email addresses.
- [**validate_body**](#leadr.infra.email.Email.validate_body) – Validate email body.
- [**validate_cc_emails**](#leadr.infra.email.Email.validate_cc_emails) – Validate CC email addresses.
- [**validate_from_email**](#leadr.infra.email.Email.validate_from_email) – Validate sender email address.
- [**validate_reply_to**](#leadr.infra.email.Email.validate_reply_to) – Validate reply-to email address.
- [**validate_subject**](#leadr.infra.email.Email.validate_subject) – Validate email subject.
- [**validate_to_email**](#leadr.infra.email.Email.validate_to_email) – Validate recipient email address.

**Attributes:**

- [**bcc**](./infra.md#leadr.infra.email.Email.bcc) (<code>[list](#list)\[[str](#str)\]</code>) –
- [**body**](./infra.md#leadr.infra.email.Email.body) (<code>[str](#str)</code>) –
- [**cc**](./infra.md#leadr.infra.email.Email.cc) (<code>[list](#list)\[[str](#str)\]</code>) –
- [**created_at**](#leadr.infra.email.Email.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**deleted_at**](#leadr.infra.email.Email.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**error_message**](#leadr.infra.email.Email.error_message) (<code>[str](#str) | None</code>) –
- [**failed_at**](#leadr.infra.email.Email.failed_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**from_email**](#leadr.infra.email.Email.from_email) (<code>[str](#str) | None</code>) –
- [**id**](./infra.md#leadr.infra.email.Email.id) (<code>[EmailID](./common.md#leadr.common.domain.ids.EmailID)</code>) –
- [**is_deleted**](#leadr.infra.email.Email.is_deleted) (<code>[bool](#bool)</code>) – Check if entity is soft-deleted.
- [**model_config**](#leadr.infra.email.Email.model_config) –
- [**priority**](./infra.md#leadr.infra.email.Email.priority) (<code>[EmailPriority](./infra.md#leadr.infra.email.domain.models.EmailPriority)</code>) –
- [**provider_message_id**](#leadr.infra.email.Email.provider_message_id) (<code>[str](#str) | None</code>) –
- [**provider_response**](#leadr.infra.email.Email.provider_response) (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\] | None</code>) –
- [**reply_to**](#leadr.infra.email.Email.reply_to) (<code>[str](#str) | None</code>) –
- [**sent_at**](#leadr.infra.email.Email.sent_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**status**](./infra.md#leadr.infra.email.Email.status) (<code>[EmailStatus](./infra.md#leadr.infra.email.domain.models.EmailStatus)</code>) –
- [**subject**](./infra.md#leadr.infra.email.Email.subject) (<code>[str](#str)</code>) –
- [**template_data**](#leadr.infra.email.Email.template_data) (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\] | None</code>) –
- [**to**](./infra.md#leadr.infra.email.Email.to) (<code>[str](#str)</code>) –
- [**updated_at**](#leadr.infra.email.Email.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

###### `leadr.infra.email.Email.bcc`

```python
bcc: list[str] = Field(default_factory=list, description='BCC recipients')
```

###### `leadr.infra.email.Email.body`

```python
body: str = Field(..., description='Email body content')
```

###### `leadr.infra.email.Email.cc`

```python
cc: list[str] = Field(default_factory=list, description='CC recipients')
```

###### `leadr.infra.email.Email.create`

```python
create(to, subject, body, from_email=None, reply_to=None, cc=None, bcc=None, priority=EmailPriority.NORMAL, template_data=None)
```

Create a new Email entity.

###### `leadr.infra.email.Email.created_at`

```python
created_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp when entity was created (UTC)')
```

###### `leadr.infra.email.Email.deleted_at`

```python
deleted_at: datetime | None = Field(default=None, description='Timestamp when entity was soft-deleted (UTC), or null if active')
```

###### `leadr.infra.email.Email.error_message`

```python
error_message: str | None = Field(None, description='Error message if failed')
```

###### `leadr.infra.email.Email.failed_at`

```python
failed_at: datetime | None = Field(None, description='Time email failed')
```

###### `leadr.infra.email.Email.from_email`

```python
from_email: str | None = Field(None, description='Sender email address')
```

###### `leadr.infra.email.Email.id`

```python
id: EmailID = Field(frozen=True, default_factory=EmailID, description='Unique email identifier')
```

###### `leadr.infra.email.Email.is_deleted`

```python
is_deleted: bool
```

Check if entity is soft-deleted.

**Returns:**

- <code>[bool](#bool)</code> – True if the entity has a deleted_at timestamp, False otherwise.

###### `leadr.infra.email.Email.mark_as_delivered`

```python
mark_as_delivered()
```

Mark email as delivered.

###### `leadr.infra.email.Email.mark_as_failed`

```python
mark_as_failed(error_message, provider_response=None)
```

Mark email as failed.

###### `leadr.infra.email.Email.mark_as_sent`

```python
mark_as_sent(provider_message_id, provider_response)
```

Mark email as sent.

###### `leadr.infra.email.Email.model_config`

```python
model_config = ConfigDict(validate_assignment=True)
```

###### `leadr.infra.email.Email.priority`

```python
priority: EmailPriority = Field(default=(EmailPriority.NORMAL), description='Email priority')
```

###### `leadr.infra.email.Email.provider_message_id`

```python
provider_message_id: str | None = Field(None, description='Provider message ID')
```

###### `leadr.infra.email.Email.provider_response`

```python
provider_response: dict[str, Any] | None = Field(None, description='Provider API response')
```

###### `leadr.infra.email.Email.reply_to`

```python
reply_to: str | None = Field(None, description='Reply-to email address')
```

###### `leadr.infra.email.Email.restore`

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

###### `leadr.infra.email.Email.sent_at`

```python
sent_at: datetime | None = Field(None, description='Time email was sent')
```

###### `leadr.infra.email.Email.soft_delete`

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

###### `leadr.infra.email.Email.status`

```python
status: EmailStatus = Field(default=(EmailStatus.PENDING), description='Email status')
```

###### `leadr.infra.email.Email.subject`

```python
subject: str = Field(..., description='Email subject')
```

###### `leadr.infra.email.Email.template_data`

```python
template_data: dict[str, Any] | None = Field(None, description='Template data for email rendering')
```

###### `leadr.infra.email.Email.to`

```python
to: str = Field(..., description='Recipient email address')
```

###### `leadr.infra.email.Email.updated_at`

```python
updated_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp of last update (UTC)')
```

###### `leadr.infra.email.Email.validate_bcc_emails`

```python
validate_bcc_emails(v)
```

Validate BCC email addresses.

###### `leadr.infra.email.Email.validate_body`

```python
validate_body(v)
```

Validate email body.

###### `leadr.infra.email.Email.validate_cc_emails`

```python
validate_cc_emails(v)
```

Validate CC email addresses.

###### `leadr.infra.email.Email.validate_from_email`

```python
validate_from_email(v)
```

Validate sender email address.

###### `leadr.infra.email.Email.validate_reply_to`

```python
validate_reply_to(v)
```

Validate reply-to email address.

###### `leadr.infra.email.Email.validate_subject`

```python
validate_subject(v)
```

Validate email subject.

###### `leadr.infra.email.Email.validate_to_email`

```python
validate_to_email(v)
```

Validate recipient email address.

##### `leadr.infra.email.EmailError`

Bases: <code>[Exception](#Exception)</code>

Base exception for email domain errors.

##### `leadr.infra.email.EmailPriority`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Email priority enumeration.

**Attributes:**

- [**HIGH**](./infra.md#leadr.infra.email.EmailPriority.HIGH) –
- [**LOW**](./infra.md#leadr.infra.email.EmailPriority.LOW) –
- [**NORMAL**](./infra.md#leadr.infra.email.EmailPriority.NORMAL) –
- [**URGENT**](./infra.md#leadr.infra.email.EmailPriority.URGENT) –

###### `leadr.infra.email.EmailPriority.HIGH`

```python
HIGH = 'high'
```

###### `leadr.infra.email.EmailPriority.LOW`

```python
LOW = 'low'
```

###### `leadr.infra.email.EmailPriority.NORMAL`

```python
NORMAL = 'normal'
```

###### `leadr.infra.email.EmailPriority.URGENT`

```python
URGENT = 'urgent'
```

##### `leadr.infra.email.EmailProvider`

Bases: <code>[ABC](#abc.ABC)</code>

Interface for email service providers.

**Functions:**

- [**send**](./infra.md#leadr.infra.email.EmailProvider.send) – Send an email and return provider response.
- [**validate_config**](#leadr.infra.email.EmailProvider.validate_config) – Validate provider configuration.

###### `leadr.infra.email.EmailProvider.send`

```python
send(email)
```

Send an email and return provider response.

###### `leadr.infra.email.EmailProvider.validate_config`

```python
validate_config()
```

Validate provider configuration.

##### `leadr.infra.email.EmailSendError`

```python
EmailSendError(message, provider_response=None)
```

Bases: <code>[EmailError](./infra.md#leadr.infra.email.domain.exceptions.EmailError)</code>

Raised when email sending fails.

**Attributes:**

- [**provider_response**](#leadr.infra.email.EmailSendError.provider_response) –

###### `leadr.infra.email.EmailSendError.provider_response`

```python
provider_response = provider_response
```

##### `leadr.infra.email.EmailService`

```python
EmailService(provider, db=None, validate_on_init=False)
```

Email service with dependency injection for testing and flexibility.

**Functions:**

- [**get_default_from_email**](#leadr.infra.email.EmailService.get_default_from_email) – Get default from email address.
- [**send_email**](#leadr.infra.email.EmailService.send_email) – Send an email using the configured provider.
- [**send_invite_email**](#leadr.infra.email.EmailService.send_invite_email) – Send an invite email when a user is invited to an account.
- [**send_notification_email**](#leadr.infra.email.EmailService.send_notification_email) – Send a notification email.
- [**send_verification_code**](#leadr.infra.email.EmailService.send_verification_code) – Send a verification code email for LEADR registration.
- [**send_welcome_email**](#leadr.infra.email.EmailService.send_welcome_email) – Send a welcome email after successful LEADR registration.
- [**validate_provider_config**](#leadr.infra.email.EmailService.validate_provider_config) – Validate the email provider configuration.

**Attributes:**

- [**db**](./infra.md#leadr.infra.email.EmailService.db) –
- [**provider**](./infra.md#leadr.infra.email.EmailService.provider) –
- [**repository**](./infra.md#leadr.infra.email.EmailService.repository) –
- [**templates_dir**](#leadr.infra.email.EmailService.templates_dir) –

**Parameters:**

- **provider** (<code>[EmailProvider](./infra.md#leadr.infra.email.domain.interfaces.EmailProvider)</code>) – Email provider implementation (e.g., Mailgun).
- **db** (<code>[AsyncSession](#sqlalchemy.ext.asyncio.AsyncSession) | None</code>) – Optional database session for persisting email records.
- **validate_on_init** (<code>[bool](#bool)</code>) – Whether to validate provider config on initialization.

###### `leadr.infra.email.EmailService.db`

```python
db = db
```

###### `leadr.infra.email.EmailService.get_default_from_email`

```python
get_default_from_email()
```

Get default from email address.

###### `leadr.infra.email.EmailService.provider`

```python
provider = provider
```

###### `leadr.infra.email.EmailService.repository`

```python
repository = EmailRepository(db) if db else None
```

###### `leadr.infra.email.EmailService.send_email`

```python
send_email(to, subject, body, from_email=None, reply_to=None, cc=None, bcc=None, priority=EmailPriority.NORMAL, template_data=None)
```

Send an email using the configured provider.

###### `leadr.infra.email.EmailService.send_invite_email`

```python
send_invite_email(to, account_name, code)
```

Send an invite email when a user is invited to an account.

**Parameters:**

- **to** (<code>[str](#str)</code>) – Email address to send the invite to.
- **account_name** (<code>[str](#str)</code>) – Name of the account the user is being invited to.
- **code** (<code>[str](#str)</code>) – The 6-character verification code.

**Returns:**

- <code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\]</code> – Email provider response dict.

###### `leadr.infra.email.EmailService.send_notification_email`

```python
send_notification_email(to, subject, message, priority=EmailPriority.NORMAL, from_email=None)
```

Send a notification email.

###### `leadr.infra.email.EmailService.send_verification_code`

```python
send_verification_code(to, code)
```

Send a verification code email for LEADR registration.

###### `leadr.infra.email.EmailService.send_welcome_email`

```python
send_welcome_email(to, user_name, account_name, account_slug, from_email=None)
```

Send a welcome email after successful LEADR registration.

###### `leadr.infra.email.EmailService.templates_dir`

```python
templates_dir = Path(__file__).parent / 'templates'
```

###### `leadr.infra.email.EmailService.validate_provider_config`

```python
validate_provider_config()
```

Validate the email provider configuration.

##### `leadr.infra.email.EmailStatus`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Email status enumeration.

**Attributes:**

- [**DELIVERED**](./infra.md#leadr.infra.email.EmailStatus.DELIVERED) –
- [**FAILED**](./infra.md#leadr.infra.email.EmailStatus.FAILED) –
- [**PENDING**](./infra.md#leadr.infra.email.EmailStatus.PENDING) –
- [**SENT**](./infra.md#leadr.infra.email.EmailStatus.SENT) –

###### `leadr.infra.email.EmailStatus.DELIVERED`

```python
DELIVERED = 'delivered'
```

###### `leadr.infra.email.EmailStatus.FAILED`

```python
FAILED = 'failed'
```

###### `leadr.infra.email.EmailStatus.PENDING`

```python
PENDING = 'pending'
```

###### `leadr.infra.email.EmailStatus.SENT`

```python
SENT = 'sent'
```

##### `leadr.infra.email.EmailValidationError`

Bases: <code>[EmailError](./infra.md#leadr.infra.email.domain.exceptions.EmailError)</code>

Raised when email validation fails.

##### `leadr.infra.email.MailgunEmailProvider`

```python
MailgunEmailProvider()
```

Bases: <code>[EmailProvider](./infra.md#leadr.infra.email.domain.interfaces.EmailProvider)</code>

Mailgun email service provider implementation.

**Functions:**

- [**send**](./infra.md#leadr.infra.email.MailgunEmailProvider.send) – Send email via Mailgun API.
- [**validate_config**](#leadr.infra.email.MailgunEmailProvider.validate_config) – Validate Mailgun configuration.

**Attributes:**

- [**api_key**](#leadr.infra.email.MailgunEmailProvider.api_key) –
- [**client**](./infra.md#leadr.infra.email.MailgunEmailProvider.client) –
- [**domain**](./infra.md#leadr.infra.email.MailgunEmailProvider.domain) –

###### `leadr.infra.email.MailgunEmailProvider.api_key`

```python
api_key = settings.MAILGUN_API_KEY
```

###### `leadr.infra.email.MailgunEmailProvider.client`

```python
client = Client(auth=('api', self.api_key), api_url=(settings.MAILGUN_API_URL))
```

###### `leadr.infra.email.MailgunEmailProvider.domain`

```python
domain = settings.MAILGUN_DOMAIN
```

###### `leadr.infra.email.MailgunEmailProvider.send`

```python
send(email)
```

Send email via Mailgun API.

###### `leadr.infra.email.MailgunEmailProvider.validate_config`

```python
validate_config()
```

Validate Mailgun configuration.

##### `leadr.infra.email.SMTPEmailProvider`

```python
SMTPEmailProvider(host=None, port=None)
```

Bases: <code>[EmailProvider](./infra.md#leadr.infra.email.domain.interfaces.EmailProvider)</code>

SMTP email provider implementation for development/testing.

**Functions:**

- [**send**](./infra.md#leadr.infra.email.SMTPEmailProvider.send) – Send email via SMTP.
- [**validate_config**](#leadr.infra.email.SMTPEmailProvider.validate_config) – Validate SMTP configuration.

**Attributes:**

- [**host**](./infra.md#leadr.infra.email.SMTPEmailProvider.host) –
- [**port**](./infra.md#leadr.infra.email.SMTPEmailProvider.port) –

**Parameters:**

- **host** (<code>[str](#str) | None</code>) – SMTP server hostname (defaults to settings.SMTP_HOST or localhost)
- **port** (<code>[int](#int) | None</code>) – SMTP server port (defaults to settings.SMTP_PORT or 1025)

###### `leadr.infra.email.SMTPEmailProvider.host`

```python
host = host or getattr(settings, 'SMTP_HOST', 'localhost')
```

###### `leadr.infra.email.SMTPEmailProvider.port`

```python
port = port or getattr(settings, 'SMTP_PORT', 1025)
```

###### `leadr.infra.email.SMTPEmailProvider.send`

```python
send(email)
```

Send email via SMTP.

###### `leadr.infra.email.SMTPEmailProvider.validate_config`

```python
validate_config()
```

Validate SMTP configuration.

##### `leadr.infra.email.adapters`

Email adapter implementations.

**Modules:**

- [**mailgun**](./infra.md#leadr.infra.email.adapters.mailgun) – Mailgun email adapter implementation.
- [**orm**](./infra.md#leadr.infra.email.adapters.orm) – Email ORM models.
- [**repositories**](./infra.md#leadr.infra.email.adapters.repositories) – Email repository for database operations.
- [**smtp**](./infra.md#leadr.infra.email.adapters.smtp) – SMTP email adapter implementation for testing.

###### `leadr.infra.email.adapters.mailgun`

Mailgun email adapter implementation.

**Classes:**

- [**MailgunEmailProvider**](./infra.md#leadr.infra.email.adapters.mailgun.MailgunEmailProvider) – Mailgun email service provider implementation.

####### `leadr.infra.email.adapters.mailgun.MailgunEmailProvider`

```python
MailgunEmailProvider()
```

Bases: <code>[EmailProvider](./infra.md#leadr.infra.email.domain.interfaces.EmailProvider)</code>

Mailgun email service provider implementation.

**Functions:**

- [**send**](#leadr.infra.email.adapters.mailgun.MailgunEmailProvider.send) – Send email via Mailgun API.
- [**validate_config**](#leadr.infra.email.adapters.mailgun.MailgunEmailProvider.validate_config) – Validate Mailgun configuration.

**Attributes:**

- [**api_key**](#leadr.infra.email.adapters.mailgun.MailgunEmailProvider.api_key) –
- [**client**](#leadr.infra.email.adapters.mailgun.MailgunEmailProvider.client) –
- [**domain**](#leadr.infra.email.adapters.mailgun.MailgunEmailProvider.domain) –

######## `leadr.infra.email.adapters.mailgun.MailgunEmailProvider.api_key`

```python
api_key = settings.MAILGUN_API_KEY
```

######## `leadr.infra.email.adapters.mailgun.MailgunEmailProvider.client`

```python
client = Client(auth=('api', self.api_key), api_url=(settings.MAILGUN_API_URL))
```

######## `leadr.infra.email.adapters.mailgun.MailgunEmailProvider.domain`

```python
domain = settings.MAILGUN_DOMAIN
```

######## `leadr.infra.email.adapters.mailgun.MailgunEmailProvider.send`

```python
send(email)
```

Send email via Mailgun API.

######## `leadr.infra.email.adapters.mailgun.MailgunEmailProvider.validate_config`

```python
validate_config()
```

Validate Mailgun configuration.

###### `leadr.infra.email.adapters.orm`

Email ORM models.

**Classes:**

- [**EmailORM**](./infra.md#leadr.infra.email.adapters.orm.EmailORM) – Email ORM model.
- [**EmailPriorityEnum**](./infra.md#leadr.infra.email.adapters.orm.EmailPriorityEnum) – Email priority enum for database.
- [**EmailStatusEnum**](./infra.md#leadr.infra.email.adapters.orm.EmailStatusEnum) – Email status enum for database.

####### `leadr.infra.email.adapters.orm.EmailORM`

Bases: <code>[Base](./common.md#leadr.common.orm.Base)</code>

Email ORM model.

Represents an email in the database for tracking and auditing purposes.
Maps to the emails table.

**Functions:**

- [**from_domain**](#leadr.infra.email.adapters.orm.EmailORM.from_domain) – Convert domain entity to ORM model.
- [**to_domain**](#leadr.infra.email.adapters.orm.EmailORM.to_domain) – Convert ORM model to domain entity.

**Attributes:**

- [**bcc**](#leadr.infra.email.adapters.orm.EmailORM.bcc) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[list](#list)\[[str](#str)\]\]</code>) –
- [**body**](#leadr.infra.email.adapters.orm.EmailORM.body) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**cc**](#leadr.infra.email.adapters.orm.EmailORM.cc) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[list](#list)\[[str](#str)\]\]</code>) –
- [**created_at**](#leadr.infra.email.adapters.orm.EmailORM.created_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –
- [**deleted_at**](#leadr.infra.email.adapters.orm.EmailORM.deleted_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[nullable_timestamp](#leadr.common.orm.nullable_timestamp)\]</code>) –
- [**error_message**](#leadr.infra.email.adapters.orm.EmailORM.error_message) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**failed_at**](#leadr.infra.email.adapters.orm.EmailORM.failed_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime) | None\]</code>) –
- [**from_email**](#leadr.infra.email.adapters.orm.EmailORM.from_email) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**id**](#leadr.infra.email.adapters.orm.EmailORM.id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[uuid_pk](#leadr.common.orm.uuid_pk)\]</code>) –
- [**priority**](#leadr.infra.email.adapters.orm.EmailORM.priority) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[EmailPriorityEnum](./infra.md#leadr.infra.email.adapters.orm.EmailPriorityEnum)\]</code>) –
- [**provider_message_id**](#leadr.infra.email.adapters.orm.EmailORM.provider_message_id) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**provider_response**](#leadr.infra.email.adapters.orm.EmailORM.provider_response) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[dict](#dict)\[[str](#str), [Any](#typing.Any)\] | None\]</code>) –
- [**reply_to**](#leadr.infra.email.adapters.orm.EmailORM.reply_to) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str) | None\]</code>) –
- [**sent_at**](#leadr.infra.email.adapters.orm.EmailORM.sent_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[datetime](#datetime.datetime) | None\]</code>) –
- [**status**](#leadr.infra.email.adapters.orm.EmailORM.status) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[EmailStatusEnum](./infra.md#leadr.infra.email.adapters.orm.EmailStatusEnum)\]</code>) –
- [**subject**](#leadr.infra.email.adapters.orm.EmailORM.subject) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**template_data**](#leadr.infra.email.adapters.orm.EmailORM.template_data) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[dict](#dict)\[[str](#str), [Any](#typing.Any)\] | None\]</code>) –
- [**to**](#leadr.infra.email.adapters.orm.EmailORM.to) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[str](#str)\]</code>) –
- [**updated_at**](#leadr.infra.email.adapters.orm.EmailORM.updated_at) (<code>[Mapped](#sqlalchemy.orm.Mapped)\[[timestamp](./common.md#leadr.common.orm.timestamp)\]</code>) –

######## `leadr.infra.email.adapters.orm.EmailORM.bcc`

```python
bcc: Mapped[list[str]] = mapped_column(JSON, nullable=False, default=list, server_default='[]')
```

######## `leadr.infra.email.adapters.orm.EmailORM.body`

```python
body: Mapped[str] = mapped_column(Text, nullable=False)
```

######## `leadr.infra.email.adapters.orm.EmailORM.cc`

```python
cc: Mapped[list[str]] = mapped_column(JSON, nullable=False, default=list, server_default='[]')
```

######## `leadr.infra.email.adapters.orm.EmailORM.created_at`

```python
created_at: Mapped[timestamp]
```

######## `leadr.infra.email.adapters.orm.EmailORM.deleted_at`

```python
deleted_at: Mapped[nullable_timestamp]
```

######## `leadr.infra.email.adapters.orm.EmailORM.error_message`

```python
error_message: Mapped[str | None] = mapped_column(Text, nullable=True)
```

######## `leadr.infra.email.adapters.orm.EmailORM.failed_at`

```python
failed_at: Mapped[datetime | None] = mapped_column(DateTime(timezone=True), nullable=True)
```

######## `leadr.infra.email.adapters.orm.EmailORM.from_domain`

```python
from_domain(domain)
```

Convert domain entity to ORM model.

**Parameters:**

- **domain** (<code>[Email](./infra.md#leadr.infra.email.domain.models.Email)</code>) – The domain entity to convert.

**Returns:**

- <code>[EmailORM](./infra.md#leadr.infra.email.adapters.orm.EmailORM)</code> – The ORM model instance.

######## `leadr.infra.email.adapters.orm.EmailORM.from_email`

```python
from_email: Mapped[str | None] = mapped_column(String, nullable=True)
```

######## `leadr.infra.email.adapters.orm.EmailORM.id`

```python
id: Mapped[uuid_pk]
```

######## `leadr.infra.email.adapters.orm.EmailORM.priority`

```python
priority: Mapped[EmailPriorityEnum] = mapped_column(Enum(EmailPriorityEnum, name='email_priority', native_enum=True, values_callable=(lambda x: [(e.value) for e in x])), nullable=False, default=(EmailPriorityEnum.NORMAL), server_default='normal')
```

######## `leadr.infra.email.adapters.orm.EmailORM.provider_message_id`

```python
provider_message_id: Mapped[str | None] = mapped_column(String, nullable=True, index=True)
```

######## `leadr.infra.email.adapters.orm.EmailORM.provider_response`

```python
provider_response: Mapped[dict[str, Any] | None] = mapped_column(JSON, nullable=True)
```

######## `leadr.infra.email.adapters.orm.EmailORM.reply_to`

```python
reply_to: Mapped[str | None] = mapped_column(String, nullable=True)
```

######## `leadr.infra.email.adapters.orm.EmailORM.sent_at`

```python
sent_at: Mapped[datetime | None] = mapped_column(DateTime(timezone=True), nullable=True)
```

######## `leadr.infra.email.adapters.orm.EmailORM.status`

```python
status: Mapped[EmailStatusEnum] = mapped_column(Enum(EmailStatusEnum, name='email_status', native_enum=True, values_callable=(lambda x: [(e.value) for e in x])), nullable=False, default=(EmailStatusEnum.PENDING), server_default='pending', index=True)
```

######## `leadr.infra.email.adapters.orm.EmailORM.subject`

```python
subject: Mapped[str] = mapped_column(String, nullable=False)
```

######## `leadr.infra.email.adapters.orm.EmailORM.template_data`

```python
template_data: Mapped[dict[str, Any] | None] = mapped_column(JSON, nullable=True)
```

######## `leadr.infra.email.adapters.orm.EmailORM.to`

```python
to: Mapped[str] = mapped_column(String, nullable=False, index=True)
```

######## `leadr.infra.email.adapters.orm.EmailORM.to_domain`

```python
to_domain()
```

Convert ORM model to domain entity.

**Returns:**

- <code>[Email](./infra.md#leadr.infra.email.domain.models.Email)</code> – The domain entity instance.

######## `leadr.infra.email.adapters.orm.EmailORM.updated_at`

```python
updated_at: Mapped[timestamp] = mapped_column(onupdate=(func.now()))
```

####### `leadr.infra.email.adapters.orm.EmailPriorityEnum`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Email priority enum for database.

**Attributes:**

- [**HIGH**](#leadr.infra.email.adapters.orm.EmailPriorityEnum.HIGH) –
- [**LOW**](#leadr.infra.email.adapters.orm.EmailPriorityEnum.LOW) –
- [**NORMAL**](#leadr.infra.email.adapters.orm.EmailPriorityEnum.NORMAL) –
- [**URGENT**](#leadr.infra.email.adapters.orm.EmailPriorityEnum.URGENT) –

######## `leadr.infra.email.adapters.orm.EmailPriorityEnum.HIGH`

```python
HIGH = 'high'
```

######## `leadr.infra.email.adapters.orm.EmailPriorityEnum.LOW`

```python
LOW = 'low'
```

######## `leadr.infra.email.adapters.orm.EmailPriorityEnum.NORMAL`

```python
NORMAL = 'normal'
```

######## `leadr.infra.email.adapters.orm.EmailPriorityEnum.URGENT`

```python
URGENT = 'urgent'
```

####### `leadr.infra.email.adapters.orm.EmailStatusEnum`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Email status enum for database.

**Attributes:**

- [**DELIVERED**](#leadr.infra.email.adapters.orm.EmailStatusEnum.DELIVERED) –
- [**FAILED**](#leadr.infra.email.adapters.orm.EmailStatusEnum.FAILED) –
- [**PENDING**](#leadr.infra.email.adapters.orm.EmailStatusEnum.PENDING) –
- [**SENT**](#leadr.infra.email.adapters.orm.EmailStatusEnum.SENT) –

######## `leadr.infra.email.adapters.orm.EmailStatusEnum.DELIVERED`

```python
DELIVERED = 'delivered'
```

######## `leadr.infra.email.adapters.orm.EmailStatusEnum.FAILED`

```python
FAILED = 'failed'
```

######## `leadr.infra.email.adapters.orm.EmailStatusEnum.PENDING`

```python
PENDING = 'pending'
```

######## `leadr.infra.email.adapters.orm.EmailStatusEnum.SENT`

```python
SENT = 'sent'
```

###### `leadr.infra.email.adapters.repositories`

Email repository for database operations.

**Classes:**

- [**EmailRepository**](./infra.md#leadr.infra.email.adapters.repositories.EmailRepository) – Repository for Email entities.

####### `leadr.infra.email.adapters.repositories.EmailRepository`

```python
EmailRepository(db)
```

Bases: <code>[BaseRepository](./common.md#leadr.common.repositories.BaseRepository)\[[Email](./infra.md#leadr.infra.email.domain.models.Email), [EmailORM](./infra.md#leadr.infra.email.adapters.orm.EmailORM)\]</code>

Repository for Email entities.

**Functions:**

- [**create**](#leadr.infra.email.adapters.repositories.EmailRepository.create) – Create a new entity in the database.
- [**delete**](#leadr.infra.email.adapters.repositories.EmailRepository.delete) – Soft delete an entity by setting its deleted_at timestamp.
- [**filter**](#leadr.infra.email.adapters.repositories.EmailRepository.filter) – Filter emails by criteria with pagination.
- [**get_by_id**](#leadr.infra.email.adapters.repositories.EmailRepository.get_by_id) – Get an entity by its ID.
- [**update**](#leadr.infra.email.adapters.repositories.EmailRepository.update) – Update an existing entity in the database.

**Attributes:**

- [**SORTABLE_FIELDS**](#leadr.infra.email.adapters.repositories.EmailRepository.SORTABLE_FIELDS) –
- [**session**](#leadr.infra.email.adapters.repositories.EmailRepository.session) –

**Parameters:**

- **db** (<code>[AsyncSession](#sqlalchemy.ext.asyncio.AsyncSession)</code>) – Database session.

######## `leadr.infra.email.adapters.repositories.EmailRepository.SORTABLE_FIELDS`

```python
SORTABLE_FIELDS = {'id', 'to', 'status', 'priority', 'created_at', 'sent_at', 'updated_at'}
```

######## `leadr.infra.email.adapters.repositories.EmailRepository.create`

```python
create(entity)
```

Create a new entity in the database.

**Parameters:**

- **entity** (<code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code>) – Domain entity to create

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT)</code> – Created domain entity with refreshed data

######## `leadr.infra.email.adapters.repositories.EmailRepository.delete`

```python
delete(entity_id)
```

Soft delete an entity by setting its deleted_at timestamp.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – ID of entity to delete

**Raises:**

- <code>[EntityNotFoundError](./common.md#leadr.common.domain.exceptions.EntityNotFoundError)</code> – If entity is not found

######## `leadr.infra.email.adapters.repositories.EmailRepository.filter`

```python
filter(account_id=None, *, pagination, **kwargs)
```

Filter emails by criteria with pagination.

**Parameters:**

- **account_id** (<code>[Any](#typing.Any) | None</code>) – Not used for emails (top-level entity).
- **pagination** (<code>[PaginationParams](./common.md#leadr.common.api.pagination.PaginationParams)</code>) – Pagination parameters (required).
- \*\***kwargs** (<code>[Any](#typing.Any)</code>) – Filter parameters (to, status, etc.)

**Returns:**

- <code>[PaginatedResult](#leadr.common.domain.pagination_result.PaginatedResult)\[[Email](./infra.md#leadr.infra.email.domain.models.Email)\]</code> – Paginated result of matching Email entities.

**Raises:**

- <code>[ValueError](#ValueError)</code> – If sort field is not in SORTABLE_FIELDS.
- <code>[CursorValidationError](#CursorValidationError)</code> – If cursor is invalid or state doesn't match.

######## `leadr.infra.email.adapters.repositories.EmailRepository.get_by_id`

```python
get_by_id(entity_id, include_deleted=False)
```

Get an entity by its ID.

**Parameters:**

- **entity_id** (<code>[UUID4](#pydantic.UUID4) | [PrefixedID](./common.md#leadr.common.domain.ids.PrefixedID)</code>) – Entity ID to retrieve
- **include_deleted** (<code>[bool](#bool)</code>) – If True, include soft-deleted entities. Defaults to False.

**Returns:**

- <code>[DomainEntityT](./common.md#leadr.common.repositories.DomainEntityT) | None</code> – Domain entity if found, None otherwise

######## `leadr.infra.email.adapters.repositories.EmailRepository.session`

```python
session = session
```

######## `leadr.infra.email.adapters.repositories.EmailRepository.update`

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

###### `leadr.infra.email.adapters.smtp`

SMTP email adapter implementation for testing.

**Classes:**

- [**SMTPEmailProvider**](./infra.md#leadr.infra.email.adapters.smtp.SMTPEmailProvider) – SMTP email provider implementation for development/testing.

####### `leadr.infra.email.adapters.smtp.SMTPEmailProvider`

```python
SMTPEmailProvider(host=None, port=None)
```

Bases: <code>[EmailProvider](./infra.md#leadr.infra.email.domain.interfaces.EmailProvider)</code>

SMTP email provider implementation for development/testing.

**Functions:**

- [**send**](#leadr.infra.email.adapters.smtp.SMTPEmailProvider.send) – Send email via SMTP.
- [**validate_config**](#leadr.infra.email.adapters.smtp.SMTPEmailProvider.validate_config) – Validate SMTP configuration.

**Attributes:**

- [**host**](#leadr.infra.email.adapters.smtp.SMTPEmailProvider.host) –
- [**port**](#leadr.infra.email.adapters.smtp.SMTPEmailProvider.port) –

**Parameters:**

- **host** (<code>[str](#str) | None</code>) – SMTP server hostname (defaults to settings.SMTP_HOST or localhost)
- **port** (<code>[int](#int) | None</code>) – SMTP server port (defaults to settings.SMTP_PORT or 1025)

######## `leadr.infra.email.adapters.smtp.SMTPEmailProvider.host`

```python
host = host or getattr(settings, 'SMTP_HOST', 'localhost')
```

######## `leadr.infra.email.adapters.smtp.SMTPEmailProvider.port`

```python
port = port or getattr(settings, 'SMTP_PORT', 1025)
```

######## `leadr.infra.email.adapters.smtp.SMTPEmailProvider.send`

```python
send(email)
```

Send email via SMTP.

######## `leadr.infra.email.adapters.smtp.SMTPEmailProvider.validate_config`

```python
validate_config()
```

Validate SMTP configuration.

##### `leadr.infra.email.create_email_service`

```python
create_email_service(provider=None, db=None)
```

Create an email service with the specified or default provider.

**Parameters:**

- **provider** (<code>[EmailProvider](./infra.md#leadr.infra.email.domain.interfaces.EmailProvider) | None</code>) – Email provider instance. If None, uses MailgunEmailProvider
  in production or SMTPEmailProvider in TEST environment.
- **db** (<code>[AsyncSession](#sqlalchemy.ext.asyncio.AsyncSession) | None</code>) – Optional database session for persisting email records.

**Returns:**

- <code>[EmailService](./infra.md#leadr.infra.email.service.EmailService)</code> – EmailService instance ready for use.

<details class="example" open markdown="1">
<summary>Example</summary>

# Use default provider (Mailgun in prod, SMTP in test)

email_service = create_email_service()

# With database persistence

email_service = create_email_service(db=session)

# Use custom provider

custom_provider = MyCustomEmailProvider()
email_service = create_email_service(provider=custom_provider)

</details>

##### `leadr.infra.email.domain`

Email domain models and interfaces.

**Modules:**

- [**exceptions**](./infra.md#leadr.infra.email.domain.exceptions) – Email domain exceptions.
- [**interfaces**](./infra.md#leadr.infra.email.domain.interfaces) – Email domain interfaces.
- [**models**](./infra.md#leadr.infra.email.domain.models) – Email domain models.

###### `leadr.infra.email.domain.exceptions`

Email domain exceptions.

**Classes:**

- [**EmailError**](./infra.md#leadr.infra.email.domain.exceptions.EmailError) – Base exception for email domain errors.
- [**EmailSendError**](./infra.md#leadr.infra.email.domain.exceptions.EmailSendError) – Raised when email sending fails.
- [**EmailValidationError**](./infra.md#leadr.infra.email.domain.exceptions.EmailValidationError) – Raised when email validation fails.

####### `leadr.infra.email.domain.exceptions.EmailError`

Bases: <code>[Exception](#Exception)</code>

Base exception for email domain errors.

####### `leadr.infra.email.domain.exceptions.EmailSendError`

```python
EmailSendError(message, provider_response=None)
```

Bases: <code>[EmailError](./infra.md#leadr.infra.email.domain.exceptions.EmailError)</code>

Raised when email sending fails.

**Attributes:**

- [**provider_response**](#leadr.infra.email.domain.exceptions.EmailSendError.provider_response) –

######## `leadr.infra.email.domain.exceptions.EmailSendError.provider_response`

```python
provider_response = provider_response
```

####### `leadr.infra.email.domain.exceptions.EmailValidationError`

Bases: <code>[EmailError](./infra.md#leadr.infra.email.domain.exceptions.EmailError)</code>

Raised when email validation fails.

###### `leadr.infra.email.domain.interfaces`

Email domain interfaces.

**Classes:**

- [**EmailProvider**](./infra.md#leadr.infra.email.domain.interfaces.EmailProvider) – Interface for email service providers.

####### `leadr.infra.email.domain.interfaces.EmailProvider`

Bases: <code>[ABC](#abc.ABC)</code>

Interface for email service providers.

**Functions:**

- [**send**](#leadr.infra.email.domain.interfaces.EmailProvider.send) – Send an email and return provider response.
- [**validate_config**](#leadr.infra.email.domain.interfaces.EmailProvider.validate_config) – Validate provider configuration.

######## `leadr.infra.email.domain.interfaces.EmailProvider.send`

```python
send(email)
```

Send an email and return provider response.

######## `leadr.infra.email.domain.interfaces.EmailProvider.validate_config`

```python
validate_config()
```

Validate provider configuration.

###### `leadr.infra.email.domain.models`

Email domain models.

**Classes:**

- [**Email**](./infra.md#leadr.infra.email.domain.models.Email) – Email domain entity.
- [**EmailPriority**](./infra.md#leadr.infra.email.domain.models.EmailPriority) – Email priority enumeration.
- [**EmailStatus**](./infra.md#leadr.infra.email.domain.models.EmailStatus) – Email status enumeration.

####### `leadr.infra.email.domain.models.Email`

Bases: <code>[Entity](./common.md#leadr.common.domain.models.Entity)</code>

Email domain entity.

**Functions:**

- [**create**](#leadr.infra.email.domain.models.Email.create) – Create a new Email entity.
- [**mark_as_delivered**](#leadr.infra.email.domain.models.Email.mark_as_delivered) – Mark email as delivered.
- [**mark_as_failed**](#leadr.infra.email.domain.models.Email.mark_as_failed) – Mark email as failed.
- [**mark_as_sent**](#leadr.infra.email.domain.models.Email.mark_as_sent) – Mark email as sent.
- [**restore**](#leadr.infra.email.domain.models.Email.restore) – Restore a soft-deleted entity.
- [**soft_delete**](#leadr.infra.email.domain.models.Email.soft_delete) – Mark entity as soft-deleted.
- [**validate_bcc_emails**](#leadr.infra.email.domain.models.Email.validate_bcc_emails) – Validate BCC email addresses.
- [**validate_body**](#leadr.infra.email.domain.models.Email.validate_body) – Validate email body.
- [**validate_cc_emails**](#leadr.infra.email.domain.models.Email.validate_cc_emails) – Validate CC email addresses.
- [**validate_from_email**](#leadr.infra.email.domain.models.Email.validate_from_email) – Validate sender email address.
- [**validate_reply_to**](#leadr.infra.email.domain.models.Email.validate_reply_to) – Validate reply-to email address.
- [**validate_subject**](#leadr.infra.email.domain.models.Email.validate_subject) – Validate email subject.
- [**validate_to_email**](#leadr.infra.email.domain.models.Email.validate_to_email) – Validate recipient email address.

**Attributes:**

- [**bcc**](#leadr.infra.email.domain.models.Email.bcc) (<code>[list](#list)\[[str](#str)\]</code>) –
- [**body**](#leadr.infra.email.domain.models.Email.body) (<code>[str](#str)</code>) –
- [**cc**](#leadr.infra.email.domain.models.Email.cc) (<code>[list](#list)\[[str](#str)\]</code>) –
- [**created_at**](#leadr.infra.email.domain.models.Email.created_at) (<code>[datetime](#datetime.datetime)</code>) –
- [**deleted_at**](#leadr.infra.email.domain.models.Email.deleted_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**error_message**](#leadr.infra.email.domain.models.Email.error_message) (<code>[str](#str) | None</code>) –
- [**failed_at**](#leadr.infra.email.domain.models.Email.failed_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**from_email**](#leadr.infra.email.domain.models.Email.from_email) (<code>[str](#str) | None</code>) –
- [**id**](#leadr.infra.email.domain.models.Email.id) (<code>[EmailID](./common.md#leadr.common.domain.ids.EmailID)</code>) –
- [**is_deleted**](#leadr.infra.email.domain.models.Email.is_deleted) (<code>[bool](#bool)</code>) – Check if entity is soft-deleted.
- [**model_config**](#leadr.infra.email.domain.models.Email.model_config) –
- [**priority**](#leadr.infra.email.domain.models.Email.priority) (<code>[EmailPriority](./infra.md#leadr.infra.email.domain.models.EmailPriority)</code>) –
- [**provider_message_id**](#leadr.infra.email.domain.models.Email.provider_message_id) (<code>[str](#str) | None</code>) –
- [**provider_response**](#leadr.infra.email.domain.models.Email.provider_response) (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\] | None</code>) –
- [**reply_to**](#leadr.infra.email.domain.models.Email.reply_to) (<code>[str](#str) | None</code>) –
- [**sent_at**](#leadr.infra.email.domain.models.Email.sent_at) (<code>[datetime](#datetime.datetime) | None</code>) –
- [**status**](#leadr.infra.email.domain.models.Email.status) (<code>[EmailStatus](./infra.md#leadr.infra.email.domain.models.EmailStatus)</code>) –
- [**subject**](#leadr.infra.email.domain.models.Email.subject) (<code>[str](#str)</code>) –
- [**template_data**](#leadr.infra.email.domain.models.Email.template_data) (<code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\] | None</code>) –
- [**to**](#leadr.infra.email.domain.models.Email.to) (<code>[str](#str)</code>) –
- [**updated_at**](#leadr.infra.email.domain.models.Email.updated_at) (<code>[datetime](#datetime.datetime)</code>) –

######## `leadr.infra.email.domain.models.Email.bcc`

```python
bcc: list[str] = Field(default_factory=list, description='BCC recipients')
```

######## `leadr.infra.email.domain.models.Email.body`

```python
body: str = Field(..., description='Email body content')
```

######## `leadr.infra.email.domain.models.Email.cc`

```python
cc: list[str] = Field(default_factory=list, description='CC recipients')
```

######## `leadr.infra.email.domain.models.Email.create`

```python
create(to, subject, body, from_email=None, reply_to=None, cc=None, bcc=None, priority=EmailPriority.NORMAL, template_data=None)
```

Create a new Email entity.

######## `leadr.infra.email.domain.models.Email.created_at`

```python
created_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp when entity was created (UTC)')
```

######## `leadr.infra.email.domain.models.Email.deleted_at`

```python
deleted_at: datetime | None = Field(default=None, description='Timestamp when entity was soft-deleted (UTC), or null if active')
```

######## `leadr.infra.email.domain.models.Email.error_message`

```python
error_message: str | None = Field(None, description='Error message if failed')
```

######## `leadr.infra.email.domain.models.Email.failed_at`

```python
failed_at: datetime | None = Field(None, description='Time email failed')
```

######## `leadr.infra.email.domain.models.Email.from_email`

```python
from_email: str | None = Field(None, description='Sender email address')
```

######## `leadr.infra.email.domain.models.Email.id`

```python
id: EmailID = Field(frozen=True, default_factory=EmailID, description='Unique email identifier')
```

######## `leadr.infra.email.domain.models.Email.is_deleted`

```python
is_deleted: bool
```

Check if entity is soft-deleted.

**Returns:**

- <code>[bool](#bool)</code> – True if the entity has a deleted_at timestamp, False otherwise.

######## `leadr.infra.email.domain.models.Email.mark_as_delivered`

```python
mark_as_delivered()
```

Mark email as delivered.

######## `leadr.infra.email.domain.models.Email.mark_as_failed`

```python
mark_as_failed(error_message, provider_response=None)
```

Mark email as failed.

######## `leadr.infra.email.domain.models.Email.mark_as_sent`

```python
mark_as_sent(provider_message_id, provider_response)
```

Mark email as sent.

######## `leadr.infra.email.domain.models.Email.model_config`

```python
model_config = ConfigDict(validate_assignment=True)
```

######## `leadr.infra.email.domain.models.Email.priority`

```python
priority: EmailPriority = Field(default=(EmailPriority.NORMAL), description='Email priority')
```

######## `leadr.infra.email.domain.models.Email.provider_message_id`

```python
provider_message_id: str | None = Field(None, description='Provider message ID')
```

######## `leadr.infra.email.domain.models.Email.provider_response`

```python
provider_response: dict[str, Any] | None = Field(None, description='Provider API response')
```

######## `leadr.infra.email.domain.models.Email.reply_to`

```python
reply_to: str | None = Field(None, description='Reply-to email address')
```

######## `leadr.infra.email.domain.models.Email.restore`

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

######## `leadr.infra.email.domain.models.Email.sent_at`

```python
sent_at: datetime | None = Field(None, description='Time email was sent')
```

######## `leadr.infra.email.domain.models.Email.soft_delete`

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

######## `leadr.infra.email.domain.models.Email.status`

```python
status: EmailStatus = Field(default=(EmailStatus.PENDING), description='Email status')
```

######## `leadr.infra.email.domain.models.Email.subject`

```python
subject: str = Field(..., description='Email subject')
```

######## `leadr.infra.email.domain.models.Email.template_data`

```python
template_data: dict[str, Any] | None = Field(None, description='Template data for email rendering')
```

######## `leadr.infra.email.domain.models.Email.to`

```python
to: str = Field(..., description='Recipient email address')
```

######## `leadr.infra.email.domain.models.Email.updated_at`

```python
updated_at: datetime = Field(default_factory=(lambda: datetime.now(UTC)), description='Timestamp of last update (UTC)')
```

######## `leadr.infra.email.domain.models.Email.validate_bcc_emails`

```python
validate_bcc_emails(v)
```

Validate BCC email addresses.

######## `leadr.infra.email.domain.models.Email.validate_body`

```python
validate_body(v)
```

Validate email body.

######## `leadr.infra.email.domain.models.Email.validate_cc_emails`

```python
validate_cc_emails(v)
```

Validate CC email addresses.

######## `leadr.infra.email.domain.models.Email.validate_from_email`

```python
validate_from_email(v)
```

Validate sender email address.

######## `leadr.infra.email.domain.models.Email.validate_reply_to`

```python
validate_reply_to(v)
```

Validate reply-to email address.

######## `leadr.infra.email.domain.models.Email.validate_subject`

```python
validate_subject(v)
```

Validate email subject.

######## `leadr.infra.email.domain.models.Email.validate_to_email`

```python
validate_to_email(v)
```

Validate recipient email address.

####### `leadr.infra.email.domain.models.EmailPriority`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Email priority enumeration.

**Attributes:**

- [**HIGH**](#leadr.infra.email.domain.models.EmailPriority.HIGH) –
- [**LOW**](#leadr.infra.email.domain.models.EmailPriority.LOW) –
- [**NORMAL**](#leadr.infra.email.domain.models.EmailPriority.NORMAL) –
- [**URGENT**](#leadr.infra.email.domain.models.EmailPriority.URGENT) –

######## `leadr.infra.email.domain.models.EmailPriority.HIGH`

```python
HIGH = 'high'
```

######## `leadr.infra.email.domain.models.EmailPriority.LOW`

```python
LOW = 'low'
```

######## `leadr.infra.email.domain.models.EmailPriority.NORMAL`

```python
NORMAL = 'normal'
```

######## `leadr.infra.email.domain.models.EmailPriority.URGENT`

```python
URGENT = 'urgent'
```

####### `leadr.infra.email.domain.models.EmailStatus`

Bases: <code>[str](#str)</code>, <code>[Enum](#enum.Enum)</code>

Email status enumeration.

**Attributes:**

- [**DELIVERED**](#leadr.infra.email.domain.models.EmailStatus.DELIVERED) –
- [**FAILED**](#leadr.infra.email.domain.models.EmailStatus.FAILED) –
- [**PENDING**](#leadr.infra.email.domain.models.EmailStatus.PENDING) –
- [**SENT**](#leadr.infra.email.domain.models.EmailStatus.SENT) –

######## `leadr.infra.email.domain.models.EmailStatus.DELIVERED`

```python
DELIVERED = 'delivered'
```

######## `leadr.infra.email.domain.models.EmailStatus.FAILED`

```python
FAILED = 'failed'
```

######## `leadr.infra.email.domain.models.EmailStatus.PENDING`

```python
PENDING = 'pending'
```

######## `leadr.infra.email.domain.models.EmailStatus.SENT`

```python
SENT = 'sent'
```

##### `leadr.infra.email.service`

Email service with dependency injection and convenience methods.

**Classes:**

- [**EmailService**](./infra.md#leadr.infra.email.service.EmailService) – Email service with dependency injection for testing and flexibility.

**Attributes:**

- [**logger**](./infra.md#leadr.infra.email.service.logger) –

###### `leadr.infra.email.service.EmailService`

```python
EmailService(provider, db=None, validate_on_init=False)
```

Email service with dependency injection for testing and flexibility.

**Functions:**

- [**get_default_from_email**](#leadr.infra.email.service.EmailService.get_default_from_email) – Get default from email address.
- [**send_email**](#leadr.infra.email.service.EmailService.send_email) – Send an email using the configured provider.
- [**send_invite_email**](#leadr.infra.email.service.EmailService.send_invite_email) – Send an invite email when a user is invited to an account.
- [**send_notification_email**](#leadr.infra.email.service.EmailService.send_notification_email) – Send a notification email.
- [**send_verification_code**](#leadr.infra.email.service.EmailService.send_verification_code) – Send a verification code email for LEADR registration.
- [**send_welcome_email**](#leadr.infra.email.service.EmailService.send_welcome_email) – Send a welcome email after successful LEADR registration.
- [**validate_provider_config**](#leadr.infra.email.service.EmailService.validate_provider_config) – Validate the email provider configuration.

**Attributes:**

- [**db**](./infra.md#leadr.infra.email.service.EmailService.db) –
- [**provider**](./infra.md#leadr.infra.email.service.EmailService.provider) –
- [**repository**](./infra.md#leadr.infra.email.service.EmailService.repository) –
- [**templates_dir**](#leadr.infra.email.service.EmailService.templates_dir) –

**Parameters:**

- **provider** (<code>[EmailProvider](./infra.md#leadr.infra.email.domain.interfaces.EmailProvider)</code>) – Email provider implementation (e.g., Mailgun).
- **db** (<code>[AsyncSession](#sqlalchemy.ext.asyncio.AsyncSession) | None</code>) – Optional database session for persisting email records.
- **validate_on_init** (<code>[bool](#bool)</code>) – Whether to validate provider config on initialization.

####### `leadr.infra.email.service.EmailService.db`

```python
db = db
```

####### `leadr.infra.email.service.EmailService.get_default_from_email`

```python
get_default_from_email()
```

Get default from email address.

####### `leadr.infra.email.service.EmailService.provider`

```python
provider = provider
```

####### `leadr.infra.email.service.EmailService.repository`

```python
repository = EmailRepository(db) if db else None
```

####### `leadr.infra.email.service.EmailService.send_email`

```python
send_email(to, subject, body, from_email=None, reply_to=None, cc=None, bcc=None, priority=EmailPriority.NORMAL, template_data=None)
```

Send an email using the configured provider.

####### `leadr.infra.email.service.EmailService.send_invite_email`

```python
send_invite_email(to, account_name, code)
```

Send an invite email when a user is invited to an account.

**Parameters:**

- **to** (<code>[str](#str)</code>) – Email address to send the invite to.
- **account_name** (<code>[str](#str)</code>) – Name of the account the user is being invited to.
- **code** (<code>[str](#str)</code>) – The 6-character verification code.

**Returns:**

- <code>[dict](#dict)\[[str](#str), [Any](#typing.Any)\]</code> – Email provider response dict.

####### `leadr.infra.email.service.EmailService.send_notification_email`

```python
send_notification_email(to, subject, message, priority=EmailPriority.NORMAL, from_email=None)
```

Send a notification email.

####### `leadr.infra.email.service.EmailService.send_verification_code`

```python
send_verification_code(to, code)
```

Send a verification code email for LEADR registration.

####### `leadr.infra.email.service.EmailService.send_welcome_email`

```python
send_welcome_email(to, user_name, account_name, account_slug, from_email=None)
```

Send a welcome email after successful LEADR registration.

####### `leadr.infra.email.service.EmailService.templates_dir`

```python
templates_dir = Path(__file__).parent / 'templates'
```

####### `leadr.infra.email.service.EmailService.validate_provider_config`

```python
validate_provider_config()
```

Validate the email provider configuration.

###### `leadr.infra.email.service.logger`

```python
logger = logging.getLogger(__name__)
```
