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

- [**CommonSettings**](./config.md#leadr.config.CommonSettings) – Base configuration settings shared across all environments.
- [**Settings**](./config.md#leadr.config.Settings) – Production/development environment settings.
- [**TestSettings**](./config.md#leadr.config.TestSettings) – Test environment settings.

**Attributes:**

- [**PROJ_ROOT**](#leadr.config.PROJ_ROOT) –
- [**settings**](./config.md#leadr.config.settings) –

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
- [**APP**](./config.md#leadr.config.CommonSettings.APP) (<code>[str](#str)</code>) –
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
- [**DEBUG**](./config.md#leadr.config.CommonSettings.DEBUG) (<code>[bool](#bool)</code>) –
- [**ENABLE_ADMIN_API**](#leadr.config.CommonSettings.ENABLE_ADMIN_API) (<code>[bool](#bool)</code>) –
- [**ENABLE_CLIENT_API**](#leadr.config.CommonSettings.ENABLE_CLIENT_API) (<code>[bool](#bool)</code>) –
- [**ENV**](./config.md#leadr.config.CommonSettings.ENV) (<code>[str](#str)</code>) –
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

Bases: <code>[CommonSettings](./config.md#leadr.config.CommonSettings)</code>

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

Bases: <code>[CommonSettings](./config.md#leadr.config.CommonSettings)</code>

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
