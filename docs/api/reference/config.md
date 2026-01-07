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

- [**ACCESS_TOKEN_EXPIRY_HOURS**](#leadr.config.CommonSettings.ACCESS_TOKEN_EXPIRY_HOURS) (<code>[int](#int)</code>) –
- [**ANTICHEAT_DUPLICATE_WINDOW_SECONDS**](#leadr.config.CommonSettings.ANTICHEAT_DUPLICATE_WINDOW_SECONDS) (<code>[int](#int)</code>) –
- [**ANTICHEAT_ENABLED**](#leadr.config.CommonSettings.ANTICHEAT_ENABLED) (<code>[bool](#bool)</code>) –
- [**ANTICHEAT_LOGGING_ONLY**](#leadr.config.CommonSettings.ANTICHEAT_LOGGING_ONLY) (<code>[bool](#bool)</code>) –
- [**ANTICHEAT_MIN_SAMPLES_FOR_STATS**](#leadr.config.CommonSettings.ANTICHEAT_MIN_SAMPLES_FOR_STATS) (<code>[int](#int)</code>) –
- [**ANTICHEAT_OUTLIER_THRESHOLD_TIER_A**](#leadr.config.CommonSettings.ANTICHEAT_OUTLIER_THRESHOLD_TIER_A) (<code>[float](#float)</code>) –
- [**ANTICHEAT_OUTLIER_THRESHOLD_TIER_B**](#leadr.config.CommonSettings.ANTICHEAT_OUTLIER_THRESHOLD_TIER_B) (<code>[float](#float)</code>) –
- [**ANTICHEAT_OUTLIER_THRESHOLD_TIER_C**](#leadr.config.CommonSettings.ANTICHEAT_OUTLIER_THRESHOLD_TIER_C) (<code>[float](#float)</code>) –
- [**ANTICHEAT_RATE_LIMIT_TIER_A**](#leadr.config.CommonSettings.ANTICHEAT_RATE_LIMIT_TIER_A) (<code>[int](#int)</code>) –
- [**ANTICHEAT_RATE_LIMIT_TIER_B**](#leadr.config.CommonSettings.ANTICHEAT_RATE_LIMIT_TIER_B) (<code>[int](#int)</code>) –
- [**ANTICHEAT_RATE_LIMIT_TIER_C**](#leadr.config.CommonSettings.ANTICHEAT_RATE_LIMIT_TIER_C) (<code>[int](#int)</code>) –
- [**ANTICHEAT_VELOCITY_THRESHOLD_SECONDS**](#leadr.config.CommonSettings.ANTICHEAT_VELOCITY_THRESHOLD_SECONDS) (<code>[float](#float)</code>) –
- [**API_KEY_SECRET**](#leadr.config.CommonSettings.API_KEY_SECRET) (<code>[str](#str)</code>) –
- [**API_PREFIX**](#leadr.config.CommonSettings.API_PREFIX) (<code>[str](#str)</code>) –
- [**APP**](./config.md#leadr.config.CommonSettings.APP) (<code>[str](#str)</code>) –
- [**BACKGROUND_TASK_EXPIRE_INTERVAL**](#leadr.config.CommonSettings.BACKGROUND_TASK_EXPIRE_INTERVAL) (<code>[int](#int)</code>) –
- [**BACKGROUND_TASK_NONCE_CLEANUP_INTERVAL**](#leadr.config.CommonSettings.BACKGROUND_TASK_NONCE_CLEANUP_INTERVAL) (<code>[int](#int)</code>) –
- [**BACKGROUND_TASK_TEMPLATE_INTERVAL**](#leadr.config.CommonSettings.BACKGROUND_TASK_TEMPLATE_INTERVAL) (<code>[int](#int)</code>) –
- [**BASE_URL**](#leadr.config.CommonSettings.BASE_URL) (<code>[HttpUrl](#pydantic.HttpUrl)</code>) –
- [**BOARDS_UI_DOMAIN**](#leadr.config.CommonSettings.BOARDS_UI_DOMAIN) (<code>[str](#str) | None</code>) –
- [**DASHBOARD_URL**](#leadr.config.CommonSettings.DASHBOARD_URL) (<code>[HttpUrl](#pydantic.HttpUrl)</code>) –
- [**DB_ECHO**](#leadr.config.CommonSettings.DB_ECHO) (<code>[bool](#bool)</code>) –
- [**DB_HOST**](#leadr.config.CommonSettings.DB_HOST) (<code>[str](#str)</code>) –
- [**DB_HOST_DIRECT**](#leadr.config.CommonSettings.DB_HOST_DIRECT) (<code>[str](#str) | None</code>) –
- [**DB_NAME**](#leadr.config.CommonSettings.DB_NAME) (<code>[str](#str)</code>) –
- [**DB_PASSWORD**](#leadr.config.CommonSettings.DB_PASSWORD) (<code>[str](#str)</code>) –
- [**DB_POOL_MAX_OVERFLOW**](#leadr.config.CommonSettings.DB_POOL_MAX_OVERFLOW) (<code>[int](#int)</code>) –
- [**DB_POOL_RECYCLE**](#leadr.config.CommonSettings.DB_POOL_RECYCLE) (<code>[int](#int)</code>) –
- [**DB_POOL_SIZE**](#leadr.config.CommonSettings.DB_POOL_SIZE) (<code>[int](#int)</code>) –
- [**DB_PORT**](#leadr.config.CommonSettings.DB_PORT) (<code>[int](#int)</code>) –
- [**DB_USER**](#leadr.config.CommonSettings.DB_USER) (<code>[str](#str)</code>) –
- [**DEBUG**](./config.md#leadr.config.CommonSettings.DEBUG) (<code>[bool](#bool)</code>) –
- [**DEV_OVERRIDE_IP**](#leadr.config.CommonSettings.DEV_OVERRIDE_IP) (<code>[str](#str) | None</code>) –
- [**ENABLE_ADMIN_API**](#leadr.config.CommonSettings.ENABLE_ADMIN_API) (<code>[bool](#bool)</code>) –
- [**ENABLE_CLIENT_API**](#leadr.config.CommonSettings.ENABLE_CLIENT_API) (<code>[bool](#bool)</code>) –
- [**ENV**](./config.md#leadr.config.CommonSettings.ENV) (<code>[str](#str)</code>) –
- [**GEOIP_DATABASE_PATH**](#leadr.config.CommonSettings.GEOIP_DATABASE_PATH) (<code>[Path](#pathlib.Path)</code>) –
- [**GEOIP_REFRESH_DAYS**](#leadr.config.CommonSettings.GEOIP_REFRESH_DAYS) (<code>[int](#int)</code>) –
- [**JWT_LIFETIME_SECONDS**](#leadr.config.CommonSettings.JWT_LIFETIME_SECONDS) (<code>[int](#int)</code>) –
- [**JWT_SECRET**](#leadr.config.CommonSettings.JWT_SECRET) (<code>[str](#str)</code>) –
- [**KEYS_PATH**](#leadr.config.CommonSettings.KEYS_PATH) (<code>[Path](#pathlib.Path)</code>) –
- [**LOG_DIR**](#leadr.config.CommonSettings.LOG_DIR) (<code>[Path](#pathlib.Path)</code>) –
- [**LOG_JSON**](#leadr.config.CommonSettings.LOG_JSON) (<code>[bool](#bool)</code>) –
- [**LOG_TO_FILE**](#leadr.config.CommonSettings.LOG_TO_FILE) (<code>[bool](#bool)</code>) –
- [**MAILGUN_API_KEY**](#leadr.config.CommonSettings.MAILGUN_API_KEY) (<code>[str](#str)</code>) –
- [**MAILGUN_DOMAIN**](#leadr.config.CommonSettings.MAILGUN_DOMAIN) (<code>[str](#str)</code>) –
- [**MAXMIND_ACCOUNT_ID**](#leadr.config.CommonSettings.MAXMIND_ACCOUNT_ID) (<code>[str](#str)</code>) –
- [**MAXMIND_CITY_DB_URL**](#leadr.config.CommonSettings.MAXMIND_CITY_DB_URL) (<code>[str](#str)</code>) –
- [**MAXMIND_COUNTRY_DB_URL**](#leadr.config.CommonSettings.MAXMIND_COUNTRY_DB_URL) (<code>[str](#str)</code>) –
- [**MAXMIND_LICENSE_KEY**](#leadr.config.CommonSettings.MAXMIND_LICENSE_KEY) (<code>[str](#str)</code>) –
- [**REFRESH_TOKEN_EXPIRY_DAYS**](#leadr.config.CommonSettings.REFRESH_TOKEN_EXPIRY_DAYS) (<code>[int](#int)</code>) –
- [**REGISTRATION_RATE_LIMIT_PER_HOUR**](#leadr.config.CommonSettings.REGISTRATION_RATE_LIMIT_PER_HOUR) (<code>[int](#int)</code>) –
- [**SCORE_METADATA_MAX_SIZE_BYTES**](#leadr.config.CommonSettings.SCORE_METADATA_MAX_SIZE_BYTES) (<code>[int](#int)</code>) –
- [**SOURCE_OAUTH_BASE_URL**](#leadr.config.CommonSettings.SOURCE_OAUTH_BASE_URL) (<code>[HttpUrl](#pydantic.HttpUrl)</code>) –
- [**SUPERADMIN_ACCOUNT_NAME**](#leadr.config.CommonSettings.SUPERADMIN_ACCOUNT_NAME) (<code>[str](#str)</code>) –
- [**SUPERADMIN_ACCOUNT_SLUG**](#leadr.config.CommonSettings.SUPERADMIN_ACCOUNT_SLUG) (<code>[str](#str)</code>) –
- [**SUPERADMIN_API_KEY**](#leadr.config.CommonSettings.SUPERADMIN_API_KEY) (<code>[str](#str)</code>) –
- [**SUPERADMIN_API_KEY_NAME**](#leadr.config.CommonSettings.SUPERADMIN_API_KEY_NAME) (<code>[str](#str)</code>) –
- [**SUPERADMIN_DISPLAY_NAME**](#leadr.config.CommonSettings.SUPERADMIN_DISPLAY_NAME) (<code>[str](#str)</code>) –
- [**SUPERADMIN_EMAIL**](#leadr.config.CommonSettings.SUPERADMIN_EMAIL) (<code>[str](#str)</code>) –
- [**TESTING_EMAIL**](#leadr.config.CommonSettings.TESTING_EMAIL) (<code>[str](#str)</code>) –
- [**VERIFICATION_CODE_EXPIRY_SECONDS**](#leadr.config.CommonSettings.VERIFICATION_CODE_EXPIRY_SECONDS) (<code>[int](#int)</code>) –
- [**VERIFICATION_TOKEN_EXPIRY_SECONDS**](#leadr.config.CommonSettings.VERIFICATION_TOKEN_EXPIRY_SECONDS) (<code>[int](#int)</code>) –
- [**model_config**](#leadr.config.CommonSettings.model_config) –

##### `leadr.config.CommonSettings.ACCESS_TOKEN_EXPIRY_HOURS`

```python
ACCESS_TOKEN_EXPIRY_HOURS: int = Field(default=24, description='Device access token expiration time in hours (default: 24 hours)')
```

##### `leadr.config.CommonSettings.ANTICHEAT_DUPLICATE_WINDOW_SECONDS`

```python
ANTICHEAT_DUPLICATE_WINDOW_SECONDS: int = Field(default=300, description='Time window in seconds for detecting duplicate score submissions (default: 5 minutes)')
```

##### `leadr.config.CommonSettings.ANTICHEAT_ENABLED`

```python
ANTICHEAT_ENABLED: bool = Field(default=False, description='Enable anti-cheat checks on score submissions')
```

##### `leadr.config.CommonSettings.ANTICHEAT_LOGGING_ONLY`

```python
ANTICHEAT_LOGGING_ONLY: bool = Field(default=True, description="Log anti-cheat detections but don't reject/flag submissions (dry-run mode)")
```

##### `leadr.config.CommonSettings.ANTICHEAT_MIN_SAMPLES_FOR_STATS`

```python
ANTICHEAT_MIN_SAMPLES_FOR_STATS: int = Field(default=10, description='Minimum number of scores required before statistical outlier detection is enabled')
```

##### `leadr.config.CommonSettings.ANTICHEAT_OUTLIER_THRESHOLD_TIER_A`

```python
ANTICHEAT_OUTLIER_THRESHOLD_TIER_A: float = Field(default=4.0, description='Outlier threshold for Tier A devices: standard deviations from mean')
```

##### `leadr.config.CommonSettings.ANTICHEAT_OUTLIER_THRESHOLD_TIER_B`

```python
ANTICHEAT_OUTLIER_THRESHOLD_TIER_B: float = Field(default=3.0, description='Outlier threshold for Tier B devices: standard deviations from mean')
```

##### `leadr.config.CommonSettings.ANTICHEAT_OUTLIER_THRESHOLD_TIER_C`

```python
ANTICHEAT_OUTLIER_THRESHOLD_TIER_C: float = Field(default=2.5, description='Outlier threshold for Tier C devices: standard deviations from mean')
```

##### `leadr.config.CommonSettings.ANTICHEAT_RATE_LIMIT_TIER_A`

```python
ANTICHEAT_RATE_LIMIT_TIER_A: int = Field(default=100, description='Rate limit for Tier A (trusted) devices: submissions per hour')
```

##### `leadr.config.CommonSettings.ANTICHEAT_RATE_LIMIT_TIER_B`

```python
ANTICHEAT_RATE_LIMIT_TIER_B: int = Field(default=50, description='Rate limit for Tier B (verified) devices: submissions per hour')
```

##### `leadr.config.CommonSettings.ANTICHEAT_RATE_LIMIT_TIER_C`

```python
ANTICHEAT_RATE_LIMIT_TIER_C: int = Field(default=20, description='Rate limit for Tier C (unverified) devices: submissions per hour')
```

##### `leadr.config.CommonSettings.ANTICHEAT_VELOCITY_THRESHOLD_SECONDS`

```python
ANTICHEAT_VELOCITY_THRESHOLD_SECONDS: float = Field(default=2.0, description='Minimum time between submissions to avoid velocity detection (in seconds)')
```

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

##### `leadr.config.CommonSettings.BACKGROUND_TASK_EXPIRE_INTERVAL`

```python
BACKGROUND_TASK_EXPIRE_INTERVAL: int = Field(default=60, description='Interval in seconds for expiring boards (default: 60s)')
```

##### `leadr.config.CommonSettings.BACKGROUND_TASK_NONCE_CLEANUP_INTERVAL`

```python
BACKGROUND_TASK_NONCE_CLEANUP_INTERVAL: int = Field(default=3600, description='Interval in seconds for cleaning up expired nonces (default: 3600s / 1 hour)')
```

##### `leadr.config.CommonSettings.BACKGROUND_TASK_TEMPLATE_INTERVAL`

```python
BACKGROUND_TASK_TEMPLATE_INTERVAL: int = Field(default=60, description='Interval in seconds for processing due board templates (default: 60s)')
```

##### `leadr.config.CommonSettings.BASE_URL`

```python
BASE_URL: HttpUrl = Field(default=(HttpUrl('http://localhost:8000')), description="Base URL for the API server (e.g., 'https://api.leadr.gg')")
```

##### `leadr.config.CommonSettings.BOARDS_UI_DOMAIN`

```python
BOARDS_UI_DOMAIN: str | None = Field(default=None, description="Base URL for public board UI (e.g., 'https://boards.leadr.gg'). When set, enables url/url_short fields in Game and Board API responses.")
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

##### `leadr.config.CommonSettings.DB_HOST_DIRECT`

```python
DB_HOST_DIRECT: str | None = Field(default=None, description='Direct PostgreSQL host for migrations (bypasses connection pooler). If not set, falls back to DB_HOST. For Neon, use the non-pooler endpoint.')
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

##### `leadr.config.CommonSettings.DEV_OVERRIDE_IP`

```python
DEV_OVERRIDE_IP: str | None = Field(default=None, description='Override IP address for development/testing (bypasses localhost detection)')
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

##### `leadr.config.CommonSettings.GEOIP_DATABASE_PATH`

```python
GEOIP_DATABASE_PATH: Path = Field(default=(PROJ_ROOT / '.geoip'), description='Directory path for storing GeoIP databases')
```

##### `leadr.config.CommonSettings.GEOIP_REFRESH_DAYS`

```python
GEOIP_REFRESH_DAYS: int = Field(default=7, description='Number of days between GeoIP database refresh downloads (default: 7 days)')
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

##### `leadr.config.CommonSettings.LOG_DIR`

```python
LOG_DIR: Path = Field(default=(Path('/var/log/leadr')), description='Directory for log files when LOG_TO_FILE is enabled')
```

##### `leadr.config.CommonSettings.LOG_JSON`

```python
LOG_JSON: bool = Field(default=True, description='Use JSON format for logs (disable for colored console in dev)')
```

##### `leadr.config.CommonSettings.LOG_TO_FILE`

```python
LOG_TO_FILE: bool = Field(default=False, description='Enable file logging in addition to stdout')
```

##### `leadr.config.CommonSettings.MAILGUN_API_KEY`

```python
MAILGUN_API_KEY: str = Field(default='mailgun_api_key', description='Mailgun API key for email sending')
```

##### `leadr.config.CommonSettings.MAILGUN_DOMAIN`

```python
MAILGUN_DOMAIN: str = Field(default='example.mailgun.org', description='Mailgun domain for email sending')
```

##### `leadr.config.CommonSettings.MAXMIND_ACCOUNT_ID`

```python
MAXMIND_ACCOUNT_ID: str = Field(default='', description='MaxMind account ID for database downloads (used for basic auth)')
```

##### `leadr.config.CommonSettings.MAXMIND_CITY_DB_URL`

```python
MAXMIND_CITY_DB_URL: str = Field(default='https://download.maxmind.com/geoip/databases/GeoLite2-City/download?suffix=tar.gz', description='MaxMind GeoLite2 City database download URL')
```

##### `leadr.config.CommonSettings.MAXMIND_COUNTRY_DB_URL`

```python
MAXMIND_COUNTRY_DB_URL: str = Field(default='https://download.maxmind.com/geoip/databases/GeoLite2-Country/download?suffix=tar.gz', description='MaxMind GeoLite2 Country database download URL')
```

##### `leadr.config.CommonSettings.MAXMIND_LICENSE_KEY`

```python
MAXMIND_LICENSE_KEY: str = Field(default='', description='MaxMind license key for database downloads (used for basic auth)')
```

##### `leadr.config.CommonSettings.REFRESH_TOKEN_EXPIRY_DAYS`

```python
REFRESH_TOKEN_EXPIRY_DAYS: int = Field(default=30, description='Device refresh token expiration time in days (default: 30 days)')
```

##### `leadr.config.CommonSettings.REGISTRATION_RATE_LIMIT_PER_HOUR`

```python
REGISTRATION_RATE_LIMIT_PER_HOUR: int = Field(default=3, description='Maximum verification code requests per email per hour (default: 3)')
```

##### `leadr.config.CommonSettings.SCORE_METADATA_MAX_SIZE_BYTES`

```python
SCORE_METADATA_MAX_SIZE_BYTES: int = Field(default=1024, description='Maximum size in bytes for score metadata JSON (default: 1KB)')
```

##### `leadr.config.CommonSettings.SOURCE_OAUTH_BASE_URL`

```python
SOURCE_OAUTH_BASE_URL: HttpUrl = Field(default=(HttpUrl('http://localhost:8000')), description='Base URL for OAuth provider')
```

##### `leadr.config.CommonSettings.SUPERADMIN_ACCOUNT_NAME`

```python
SUPERADMIN_ACCOUNT_NAME: str = Field(default='LEADR', description='Name of the system account for superadmin users')
```

##### `leadr.config.CommonSettings.SUPERADMIN_ACCOUNT_SLUG`

```python
SUPERADMIN_ACCOUNT_SLUG: str = Field(default='leadr', description='URL-friendly slug for the superadmin system account')
```

##### `leadr.config.CommonSettings.SUPERADMIN_API_KEY`

```python
SUPERADMIN_API_KEY: str = Field(default=..., description='API key for the superadmin user. REQUIRED for bootstrap.')
```

##### `leadr.config.CommonSettings.SUPERADMIN_API_KEY_NAME`

```python
SUPERADMIN_API_KEY_NAME: str = Field(default='Superadmin Key', description='Display name for the superadmin API key')
```

##### `leadr.config.CommonSettings.SUPERADMIN_DISPLAY_NAME`

```python
SUPERADMIN_DISPLAY_NAME: str = Field(default='LEADR Admin', description='Display name for the superadmin user')
```

##### `leadr.config.CommonSettings.SUPERADMIN_EMAIL`

```python
SUPERADMIN_EMAIL: str = Field(default='admin@leadr.gg', description='Email address for the superadmin user')
```

##### `leadr.config.CommonSettings.TESTING_EMAIL`

```python
TESTING_EMAIL: str = Field(default='hello@example.com', description='Email address used for testing purposes')
```

##### `leadr.config.CommonSettings.VERIFICATION_CODE_EXPIRY_SECONDS`

```python
VERIFICATION_CODE_EXPIRY_SECONDS: int = Field(default=600, description='Expiry time for email verification codes in seconds (default: 10 minutes)')
```

##### `leadr.config.CommonSettings.VERIFICATION_TOKEN_EXPIRY_SECONDS`

```python
VERIFICATION_TOKEN_EXPIRY_SECONDS: int = Field(default=600, description='Expiry time for verification JWT tokens in seconds (default: 10 minutes)')
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
PROJ_ROOT = Path.cwd()
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

- [**ACCESS_TOKEN_EXPIRY_HOURS**](#leadr.config.Settings.ACCESS_TOKEN_EXPIRY_HOURS) (<code>[int](#int)</code>) –
- [**ANTICHEAT_DUPLICATE_WINDOW_SECONDS**](#leadr.config.Settings.ANTICHEAT_DUPLICATE_WINDOW_SECONDS) (<code>[int](#int)</code>) –
- [**ANTICHEAT_ENABLED**](#leadr.config.Settings.ANTICHEAT_ENABLED) (<code>[bool](#bool)</code>) –
- [**ANTICHEAT_LOGGING_ONLY**](#leadr.config.Settings.ANTICHEAT_LOGGING_ONLY) (<code>[bool](#bool)</code>) –
- [**ANTICHEAT_MIN_SAMPLES_FOR_STATS**](#leadr.config.Settings.ANTICHEAT_MIN_SAMPLES_FOR_STATS) (<code>[int](#int)</code>) –
- [**ANTICHEAT_OUTLIER_THRESHOLD_TIER_A**](#leadr.config.Settings.ANTICHEAT_OUTLIER_THRESHOLD_TIER_A) (<code>[float](#float)</code>) –
- [**ANTICHEAT_OUTLIER_THRESHOLD_TIER_B**](#leadr.config.Settings.ANTICHEAT_OUTLIER_THRESHOLD_TIER_B) (<code>[float](#float)</code>) –
- [**ANTICHEAT_OUTLIER_THRESHOLD_TIER_C**](#leadr.config.Settings.ANTICHEAT_OUTLIER_THRESHOLD_TIER_C) (<code>[float](#float)</code>) –
- [**ANTICHEAT_RATE_LIMIT_TIER_A**](#leadr.config.Settings.ANTICHEAT_RATE_LIMIT_TIER_A) (<code>[int](#int)</code>) –
- [**ANTICHEAT_RATE_LIMIT_TIER_B**](#leadr.config.Settings.ANTICHEAT_RATE_LIMIT_TIER_B) (<code>[int](#int)</code>) –
- [**ANTICHEAT_RATE_LIMIT_TIER_C**](#leadr.config.Settings.ANTICHEAT_RATE_LIMIT_TIER_C) (<code>[int](#int)</code>) –
- [**ANTICHEAT_VELOCITY_THRESHOLD_SECONDS**](#leadr.config.Settings.ANTICHEAT_VELOCITY_THRESHOLD_SECONDS) (<code>[float](#float)</code>) –
- [**API_KEY_SECRET**](#leadr.config.Settings.API_KEY_SECRET) (<code>[str](#str)</code>) –
- [**API_PREFIX**](#leadr.config.Settings.API_PREFIX) (<code>[str](#str)</code>) –
- [**APP**](#leadr.config.Settings.APP) (<code>[str](#str)</code>) –
- [**BACKGROUND_TASK_EXPIRE_INTERVAL**](#leadr.config.Settings.BACKGROUND_TASK_EXPIRE_INTERVAL) (<code>[int](#int)</code>) –
- [**BACKGROUND_TASK_NONCE_CLEANUP_INTERVAL**](#leadr.config.Settings.BACKGROUND_TASK_NONCE_CLEANUP_INTERVAL) (<code>[int](#int)</code>) –
- [**BACKGROUND_TASK_TEMPLATE_INTERVAL**](#leadr.config.Settings.BACKGROUND_TASK_TEMPLATE_INTERVAL) (<code>[int](#int)</code>) –
- [**BASE_URL**](#leadr.config.Settings.BASE_URL) (<code>[HttpUrl](#pydantic.HttpUrl)</code>) –
- [**BOARDS_UI_DOMAIN**](#leadr.config.Settings.BOARDS_UI_DOMAIN) (<code>[str](#str) | None</code>) –
- [**DASHBOARD_URL**](#leadr.config.Settings.DASHBOARD_URL) (<code>[HttpUrl](#pydantic.HttpUrl)</code>) –
- [**DB_ECHO**](#leadr.config.Settings.DB_ECHO) (<code>[bool](#bool)</code>) –
- [**DB_HOST**](#leadr.config.Settings.DB_HOST) (<code>[str](#str)</code>) –
- [**DB_HOST_DIRECT**](#leadr.config.Settings.DB_HOST_DIRECT) (<code>[str](#str) | None</code>) –
- [**DB_NAME**](#leadr.config.Settings.DB_NAME) (<code>[str](#str)</code>) –
- [**DB_PASSWORD**](#leadr.config.Settings.DB_PASSWORD) (<code>[str](#str)</code>) –
- [**DB_POOL_MAX_OVERFLOW**](#leadr.config.Settings.DB_POOL_MAX_OVERFLOW) (<code>[int](#int)</code>) –
- [**DB_POOL_RECYCLE**](#leadr.config.Settings.DB_POOL_RECYCLE) (<code>[int](#int)</code>) –
- [**DB_POOL_SIZE**](#leadr.config.Settings.DB_POOL_SIZE) (<code>[int](#int)</code>) –
- [**DB_PORT**](#leadr.config.Settings.DB_PORT) (<code>[int](#int)</code>) –
- [**DB_USER**](#leadr.config.Settings.DB_USER) (<code>[str](#str)</code>) –
- [**DEBUG**](#leadr.config.Settings.DEBUG) (<code>[bool](#bool)</code>) –
- [**DEV_OVERRIDE_IP**](#leadr.config.Settings.DEV_OVERRIDE_IP) (<code>[str](#str) | None</code>) –
- [**ENABLE_ADMIN_API**](#leadr.config.Settings.ENABLE_ADMIN_API) (<code>[bool](#bool)</code>) –
- [**ENABLE_CLIENT_API**](#leadr.config.Settings.ENABLE_CLIENT_API) (<code>[bool](#bool)</code>) –
- [**ENV**](#leadr.config.Settings.ENV) (<code>[str](#str)</code>) –
- [**GEOIP_DATABASE_PATH**](#leadr.config.Settings.GEOIP_DATABASE_PATH) (<code>[Path](#pathlib.Path)</code>) –
- [**GEOIP_REFRESH_DAYS**](#leadr.config.Settings.GEOIP_REFRESH_DAYS) (<code>[int](#int)</code>) –
- [**JWT_LIFETIME_SECONDS**](#leadr.config.Settings.JWT_LIFETIME_SECONDS) (<code>[int](#int)</code>) –
- [**JWT_SECRET**](#leadr.config.Settings.JWT_SECRET) (<code>[str](#str)</code>) –
- [**KEYS_PATH**](#leadr.config.Settings.KEYS_PATH) (<code>[Path](#pathlib.Path)</code>) –
- [**LOG_DIR**](#leadr.config.Settings.LOG_DIR) (<code>[Path](#pathlib.Path)</code>) –
- [**LOG_JSON**](#leadr.config.Settings.LOG_JSON) (<code>[bool](#bool)</code>) –
- [**LOG_TO_FILE**](#leadr.config.Settings.LOG_TO_FILE) (<code>[bool](#bool)</code>) –
- [**MAILGUN_API_KEY**](#leadr.config.Settings.MAILGUN_API_KEY) (<code>[str](#str)</code>) –
- [**MAILGUN_DOMAIN**](#leadr.config.Settings.MAILGUN_DOMAIN) (<code>[str](#str)</code>) –
- [**MAXMIND_ACCOUNT_ID**](#leadr.config.Settings.MAXMIND_ACCOUNT_ID) (<code>[str](#str)</code>) –
- [**MAXMIND_CITY_DB_URL**](#leadr.config.Settings.MAXMIND_CITY_DB_URL) (<code>[str](#str)</code>) –
- [**MAXMIND_COUNTRY_DB_URL**](#leadr.config.Settings.MAXMIND_COUNTRY_DB_URL) (<code>[str](#str)</code>) –
- [**MAXMIND_LICENSE_KEY**](#leadr.config.Settings.MAXMIND_LICENSE_KEY) (<code>[str](#str)</code>) –
- [**REFRESH_TOKEN_EXPIRY_DAYS**](#leadr.config.Settings.REFRESH_TOKEN_EXPIRY_DAYS) (<code>[int](#int)</code>) –
- [**REGISTRATION_RATE_LIMIT_PER_HOUR**](#leadr.config.Settings.REGISTRATION_RATE_LIMIT_PER_HOUR) (<code>[int](#int)</code>) –
- [**SCORE_METADATA_MAX_SIZE_BYTES**](#leadr.config.Settings.SCORE_METADATA_MAX_SIZE_BYTES) (<code>[int](#int)</code>) –
- [**SOURCE_OAUTH_BASE_URL**](#leadr.config.Settings.SOURCE_OAUTH_BASE_URL) (<code>[HttpUrl](#pydantic.HttpUrl)</code>) –
- [**SUPERADMIN_ACCOUNT_NAME**](#leadr.config.Settings.SUPERADMIN_ACCOUNT_NAME) (<code>[str](#str)</code>) –
- [**SUPERADMIN_ACCOUNT_SLUG**](#leadr.config.Settings.SUPERADMIN_ACCOUNT_SLUG) (<code>[str](#str)</code>) –
- [**SUPERADMIN_API_KEY**](#leadr.config.Settings.SUPERADMIN_API_KEY) (<code>[str](#str)</code>) –
- [**SUPERADMIN_API_KEY_NAME**](#leadr.config.Settings.SUPERADMIN_API_KEY_NAME) (<code>[str](#str)</code>) –
- [**SUPERADMIN_DISPLAY_NAME**](#leadr.config.Settings.SUPERADMIN_DISPLAY_NAME) (<code>[str](#str)</code>) –
- [**SUPERADMIN_EMAIL**](#leadr.config.Settings.SUPERADMIN_EMAIL) (<code>[str](#str)</code>) –
- [**TESTING_EMAIL**](#leadr.config.Settings.TESTING_EMAIL) (<code>[str](#str)</code>) –
- [**VERIFICATION_CODE_EXPIRY_SECONDS**](#leadr.config.Settings.VERIFICATION_CODE_EXPIRY_SECONDS) (<code>[int](#int)</code>) –
- [**VERIFICATION_TOKEN_EXPIRY_SECONDS**](#leadr.config.Settings.VERIFICATION_TOKEN_EXPIRY_SECONDS) (<code>[int](#int)</code>) –
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

- [**ACCESS_TOKEN_EXPIRY_HOURS**](#leadr.config.TestSettings.ACCESS_TOKEN_EXPIRY_HOURS) (<code>[int](#int)</code>) –
- [**ANTICHEAT_DUPLICATE_WINDOW_SECONDS**](#leadr.config.TestSettings.ANTICHEAT_DUPLICATE_WINDOW_SECONDS) (<code>[int](#int)</code>) –
- [**ANTICHEAT_ENABLED**](#leadr.config.TestSettings.ANTICHEAT_ENABLED) (<code>[bool](#bool)</code>) –
- [**ANTICHEAT_LOGGING_ONLY**](#leadr.config.TestSettings.ANTICHEAT_LOGGING_ONLY) (<code>[bool](#bool)</code>) –
- [**ANTICHEAT_MIN_SAMPLES_FOR_STATS**](#leadr.config.TestSettings.ANTICHEAT_MIN_SAMPLES_FOR_STATS) (<code>[int](#int)</code>) –
- [**ANTICHEAT_OUTLIER_THRESHOLD_TIER_A**](#leadr.config.TestSettings.ANTICHEAT_OUTLIER_THRESHOLD_TIER_A) (<code>[float](#float)</code>) –
- [**ANTICHEAT_OUTLIER_THRESHOLD_TIER_B**](#leadr.config.TestSettings.ANTICHEAT_OUTLIER_THRESHOLD_TIER_B) (<code>[float](#float)</code>) –
- [**ANTICHEAT_OUTLIER_THRESHOLD_TIER_C**](#leadr.config.TestSettings.ANTICHEAT_OUTLIER_THRESHOLD_TIER_C) (<code>[float](#float)</code>) –
- [**ANTICHEAT_RATE_LIMIT_TIER_A**](#leadr.config.TestSettings.ANTICHEAT_RATE_LIMIT_TIER_A) (<code>[int](#int)</code>) –
- [**ANTICHEAT_RATE_LIMIT_TIER_B**](#leadr.config.TestSettings.ANTICHEAT_RATE_LIMIT_TIER_B) (<code>[int](#int)</code>) –
- [**ANTICHEAT_RATE_LIMIT_TIER_C**](#leadr.config.TestSettings.ANTICHEAT_RATE_LIMIT_TIER_C) (<code>[int](#int)</code>) –
- [**ANTICHEAT_VELOCITY_THRESHOLD_SECONDS**](#leadr.config.TestSettings.ANTICHEAT_VELOCITY_THRESHOLD_SECONDS) (<code>[float](#float)</code>) –
- [**API_KEY_SECRET**](#leadr.config.TestSettings.API_KEY_SECRET) (<code>[str](#str)</code>) –
- [**API_PREFIX**](#leadr.config.TestSettings.API_PREFIX) (<code>[str](#str)</code>) –
- [**APP**](./config.md#leadr.config.TestSettings.APP) (<code>[str](#str)</code>) –
- [**BACKGROUND_TASK_EXPIRE_INTERVAL**](#leadr.config.TestSettings.BACKGROUND_TASK_EXPIRE_INTERVAL) (<code>[int](#int)</code>) –
- [**BACKGROUND_TASK_NONCE_CLEANUP_INTERVAL**](#leadr.config.TestSettings.BACKGROUND_TASK_NONCE_CLEANUP_INTERVAL) (<code>[int](#int)</code>) –
- [**BACKGROUND_TASK_TEMPLATE_INTERVAL**](#leadr.config.TestSettings.BACKGROUND_TASK_TEMPLATE_INTERVAL) (<code>[int](#int)</code>) –
- [**BASE_URL**](#leadr.config.TestSettings.BASE_URL) (<code>[HttpUrl](#pydantic.HttpUrl)</code>) –
- [**BOARDS_UI_DOMAIN**](#leadr.config.TestSettings.BOARDS_UI_DOMAIN) (<code>[str](#str) | None</code>) –
- [**DASHBOARD_URL**](#leadr.config.TestSettings.DASHBOARD_URL) (<code>[HttpUrl](#pydantic.HttpUrl)</code>) –
- [**DB_ECHO**](#leadr.config.TestSettings.DB_ECHO) (<code>[bool](#bool)</code>) –
- [**DB_HOST**](#leadr.config.TestSettings.DB_HOST) (<code>[str](#str)</code>) –
- [**DB_HOST_DIRECT**](#leadr.config.TestSettings.DB_HOST_DIRECT) (<code>[str](#str) | None</code>) –
- [**DB_NAME**](#leadr.config.TestSettings.DB_NAME) (<code>[str](#str)</code>) –
- [**DB_PASSWORD**](#leadr.config.TestSettings.DB_PASSWORD) (<code>[str](#str)</code>) –
- [**DB_POOL_MAX_OVERFLOW**](#leadr.config.TestSettings.DB_POOL_MAX_OVERFLOW) (<code>[int](#int)</code>) –
- [**DB_POOL_RECYCLE**](#leadr.config.TestSettings.DB_POOL_RECYCLE) (<code>[int](#int)</code>) –
- [**DB_POOL_SIZE**](#leadr.config.TestSettings.DB_POOL_SIZE) (<code>[int](#int)</code>) –
- [**DB_PORT**](#leadr.config.TestSettings.DB_PORT) (<code>[int](#int)</code>) –
- [**DB_USER**](#leadr.config.TestSettings.DB_USER) (<code>[str](#str)</code>) –
- [**DEBUG**](./config.md#leadr.config.TestSettings.DEBUG) (<code>[bool](#bool)</code>) –
- [**DEV_OVERRIDE_IP**](#leadr.config.TestSettings.DEV_OVERRIDE_IP) (<code>[str](#str) | None</code>) –
- [**ENABLE_ADMIN_API**](#leadr.config.TestSettings.ENABLE_ADMIN_API) (<code>[bool](#bool)</code>) –
- [**ENABLE_CLIENT_API**](#leadr.config.TestSettings.ENABLE_CLIENT_API) (<code>[bool](#bool)</code>) –
- [**ENV**](./config.md#leadr.config.TestSettings.ENV) (<code>[str](#str)</code>) –
- [**GEOIP_DATABASE_PATH**](#leadr.config.TestSettings.GEOIP_DATABASE_PATH) (<code>[Path](#pathlib.Path)</code>) –
- [**GEOIP_REFRESH_DAYS**](#leadr.config.TestSettings.GEOIP_REFRESH_DAYS) (<code>[int](#int)</code>) –
- [**JWT_LIFETIME_SECONDS**](#leadr.config.TestSettings.JWT_LIFETIME_SECONDS) (<code>[int](#int)</code>) –
- [**JWT_SECRET**](#leadr.config.TestSettings.JWT_SECRET) (<code>[str](#str)</code>) –
- [**KEYS_PATH**](#leadr.config.TestSettings.KEYS_PATH) (<code>[Path](#pathlib.Path)</code>) –
- [**LOG_DIR**](#leadr.config.TestSettings.LOG_DIR) (<code>[Path](#pathlib.Path)</code>) –
- [**LOG_JSON**](#leadr.config.TestSettings.LOG_JSON) (<code>[bool](#bool)</code>) –
- [**LOG_TO_FILE**](#leadr.config.TestSettings.LOG_TO_FILE) (<code>[bool](#bool)</code>) –
- [**MAILGUN_API_KEY**](#leadr.config.TestSettings.MAILGUN_API_KEY) (<code>[str](#str)</code>) –
- [**MAILGUN_DOMAIN**](#leadr.config.TestSettings.MAILGUN_DOMAIN) (<code>[str](#str)</code>) –
- [**MAXMIND_ACCOUNT_ID**](#leadr.config.TestSettings.MAXMIND_ACCOUNT_ID) (<code>[str](#str)</code>) –
- [**MAXMIND_CITY_DB_URL**](#leadr.config.TestSettings.MAXMIND_CITY_DB_URL) (<code>[str](#str)</code>) –
- [**MAXMIND_COUNTRY_DB_URL**](#leadr.config.TestSettings.MAXMIND_COUNTRY_DB_URL) (<code>[str](#str)</code>) –
- [**MAXMIND_LICENSE_KEY**](#leadr.config.TestSettings.MAXMIND_LICENSE_KEY) (<code>[str](#str)</code>) –
- [**REFRESH_TOKEN_EXPIRY_DAYS**](#leadr.config.TestSettings.REFRESH_TOKEN_EXPIRY_DAYS) (<code>[int](#int)</code>) –
- [**REGISTRATION_RATE_LIMIT_PER_HOUR**](#leadr.config.TestSettings.REGISTRATION_RATE_LIMIT_PER_HOUR) (<code>[int](#int)</code>) –
- [**SCORE_METADATA_MAX_SIZE_BYTES**](#leadr.config.TestSettings.SCORE_METADATA_MAX_SIZE_BYTES) (<code>[int](#int)</code>) –
- [**SOURCE_OAUTH_BASE_URL**](#leadr.config.TestSettings.SOURCE_OAUTH_BASE_URL) (<code>[HttpUrl](#pydantic.HttpUrl)</code>) –
- [**SUPERADMIN_ACCOUNT_NAME**](#leadr.config.TestSettings.SUPERADMIN_ACCOUNT_NAME) (<code>[str](#str)</code>) –
- [**SUPERADMIN_ACCOUNT_SLUG**](#leadr.config.TestSettings.SUPERADMIN_ACCOUNT_SLUG) (<code>[str](#str)</code>) –
- [**SUPERADMIN_API_KEY**](#leadr.config.TestSettings.SUPERADMIN_API_KEY) (<code>[str](#str)</code>) –
- [**SUPERADMIN_API_KEY_NAME**](#leadr.config.TestSettings.SUPERADMIN_API_KEY_NAME) (<code>[str](#str)</code>) –
- [**SUPERADMIN_DISPLAY_NAME**](#leadr.config.TestSettings.SUPERADMIN_DISPLAY_NAME) (<code>[str](#str)</code>) –
- [**SUPERADMIN_EMAIL**](#leadr.config.TestSettings.SUPERADMIN_EMAIL) (<code>[str](#str)</code>) –
- [**TESTING_EMAIL**](#leadr.config.TestSettings.TESTING_EMAIL) (<code>[str](#str)</code>) –
- [**VERIFICATION_CODE_EXPIRY_SECONDS**](#leadr.config.TestSettings.VERIFICATION_CODE_EXPIRY_SECONDS) (<code>[int](#int)</code>) –
- [**VERIFICATION_TOKEN_EXPIRY_SECONDS**](#leadr.config.TestSettings.VERIFICATION_TOKEN_EXPIRY_SECONDS) (<code>[int](#int)</code>) –
- [**model_config**](#leadr.config.TestSettings.model_config) –

##### `leadr.config.TestSettings.ACCESS_TOKEN_EXPIRY_HOURS`

```python
ACCESS_TOKEN_EXPIRY_HOURS: int = Field(default=24, description='Device access token expiration time in hours (default: 24 hours)')
```

##### `leadr.config.TestSettings.ANTICHEAT_DUPLICATE_WINDOW_SECONDS`

```python
ANTICHEAT_DUPLICATE_WINDOW_SECONDS: int = Field(default=300, description='Time window in seconds for detecting duplicate score submissions (default: 5 minutes)')
```

##### `leadr.config.TestSettings.ANTICHEAT_ENABLED`

```python
ANTICHEAT_ENABLED: bool = Field(default=False, description='Enable anti-cheat checks on score submissions')
```

##### `leadr.config.TestSettings.ANTICHEAT_LOGGING_ONLY`

```python
ANTICHEAT_LOGGING_ONLY: bool = Field(default=True, description="Log anti-cheat detections but don't reject/flag submissions (dry-run mode)")
```

##### `leadr.config.TestSettings.ANTICHEAT_MIN_SAMPLES_FOR_STATS`

```python
ANTICHEAT_MIN_SAMPLES_FOR_STATS: int = Field(default=10, description='Minimum number of scores required before statistical outlier detection is enabled')
```

##### `leadr.config.TestSettings.ANTICHEAT_OUTLIER_THRESHOLD_TIER_A`

```python
ANTICHEAT_OUTLIER_THRESHOLD_TIER_A: float = Field(default=4.0, description='Outlier threshold for Tier A devices: standard deviations from mean')
```

##### `leadr.config.TestSettings.ANTICHEAT_OUTLIER_THRESHOLD_TIER_B`

```python
ANTICHEAT_OUTLIER_THRESHOLD_TIER_B: float = Field(default=3.0, description='Outlier threshold for Tier B devices: standard deviations from mean')
```

##### `leadr.config.TestSettings.ANTICHEAT_OUTLIER_THRESHOLD_TIER_C`

```python
ANTICHEAT_OUTLIER_THRESHOLD_TIER_C: float = Field(default=2.5, description='Outlier threshold for Tier C devices: standard deviations from mean')
```

##### `leadr.config.TestSettings.ANTICHEAT_RATE_LIMIT_TIER_A`

```python
ANTICHEAT_RATE_LIMIT_TIER_A: int = Field(default=100, description='Rate limit for Tier A (trusted) devices: submissions per hour')
```

##### `leadr.config.TestSettings.ANTICHEAT_RATE_LIMIT_TIER_B`

```python
ANTICHEAT_RATE_LIMIT_TIER_B: int = Field(default=50, description='Rate limit for Tier B (verified) devices: submissions per hour')
```

##### `leadr.config.TestSettings.ANTICHEAT_RATE_LIMIT_TIER_C`

```python
ANTICHEAT_RATE_LIMIT_TIER_C: int = Field(default=20, description='Rate limit for Tier C (unverified) devices: submissions per hour')
```

##### `leadr.config.TestSettings.ANTICHEAT_VELOCITY_THRESHOLD_SECONDS`

```python
ANTICHEAT_VELOCITY_THRESHOLD_SECONDS: float = Field(default=2.0, description='Minimum time between submissions to avoid velocity detection (in seconds)')
```

##### `leadr.config.TestSettings.API_KEY_SECRET`

```python
API_KEY_SECRET: str = Field(default='your-super-secret-api-key-pepper-change-in-production', description='Secret pepper for API key hashing. MUST be changed in production.')
```

##### `leadr.config.TestSettings.API_PREFIX`

```python
API_PREFIX: str = Field(default='/v1', description="API route prefix for versioning (e.g., '/v1')")
```

##### `leadr.config.TestSettings.APP`

```python
APP: str = Field(default='LEADR', description='Application name identifier')
```

##### `leadr.config.TestSettings.BACKGROUND_TASK_EXPIRE_INTERVAL`

```python
BACKGROUND_TASK_EXPIRE_INTERVAL: int = Field(default=60, description='Interval in seconds for expiring boards (default: 60s)')
```

##### `leadr.config.TestSettings.BACKGROUND_TASK_NONCE_CLEANUP_INTERVAL`

```python
BACKGROUND_TASK_NONCE_CLEANUP_INTERVAL: int = Field(default=3600, description='Interval in seconds for cleaning up expired nonces (default: 3600s / 1 hour)')
```

##### `leadr.config.TestSettings.BACKGROUND_TASK_TEMPLATE_INTERVAL`

```python
BACKGROUND_TASK_TEMPLATE_INTERVAL: int = Field(default=60, description='Interval in seconds for processing due board templates (default: 60s)')
```

##### `leadr.config.TestSettings.BASE_URL`

```python
BASE_URL: HttpUrl = Field(default=(HttpUrl('http://localhost:8000')), description="Base URL for the API server (e.g., 'https://api.leadr.gg')")
```

##### `leadr.config.TestSettings.BOARDS_UI_DOMAIN`

```python
BOARDS_UI_DOMAIN: str | None = Field(default=None, description="Base URL for public board UI (e.g., 'https://boards.leadr.gg'). When set, enables url/url_short fields in Game and Board API responses.")
```

##### `leadr.config.TestSettings.DASHBOARD_URL`

```python
DASHBOARD_URL: HttpUrl = Field(default=(HttpUrl('http://localhost:8000')), description="URL for the web dashboard (e.g., 'https://dashboard.leadr.gg')")
```

##### `leadr.config.TestSettings.DB_ECHO`

```python
DB_ECHO: bool = Field(default=False, description='Log all SQL queries to stdout (useful for debugging)')
```

##### `leadr.config.TestSettings.DB_HOST`

```python
DB_HOST: str = Field(default='localhost', description='PostgreSQL database host')
```

##### `leadr.config.TestSettings.DB_HOST_DIRECT`

```python
DB_HOST_DIRECT: str | None = Field(default=None, description='Direct PostgreSQL host for migrations (bypasses connection pooler). If not set, falls back to DB_HOST. For Neon, use the non-pooler endpoint.')
```

##### `leadr.config.TestSettings.DB_NAME`

```python
DB_NAME: str = Field(default='leadr', description='PostgreSQL database name')
```

##### `leadr.config.TestSettings.DB_PASSWORD`

```python
DB_PASSWORD: str = Field(default='leadr', description='PostgreSQL database password')
```

##### `leadr.config.TestSettings.DB_POOL_MAX_OVERFLOW`

```python
DB_POOL_MAX_OVERFLOW: int = Field(default=10, description='Maximum overflow connections beyond pool size')
```

##### `leadr.config.TestSettings.DB_POOL_RECYCLE`

```python
DB_POOL_RECYCLE: int = Field(default=3600, description='Recycle database connections after this many seconds (default: 1 hour)')
```

##### `leadr.config.TestSettings.DB_POOL_SIZE`

```python
DB_POOL_SIZE: int = Field(default=20, description='Number of database connections to maintain in the pool')
```

##### `leadr.config.TestSettings.DB_PORT`

```python
DB_PORT: int = Field(default=5432, description='PostgreSQL database port')
```

##### `leadr.config.TestSettings.DB_USER`

```python
DB_USER: str = Field(default='leadr', description='PostgreSQL database user')
```

##### `leadr.config.TestSettings.DEBUG`

```python
DEBUG: bool = Field(default=False, description='Enable debug mode with verbose logging and error details')
```

##### `leadr.config.TestSettings.DEV_OVERRIDE_IP`

```python
DEV_OVERRIDE_IP: str | None = Field(default=None, description='Override IP address for development/testing (bypasses localhost detection)')
```

##### `leadr.config.TestSettings.ENABLE_ADMIN_API`

```python
ENABLE_ADMIN_API: bool = Field(default=False, description='Enable admin API endpoints')
```

##### `leadr.config.TestSettings.ENABLE_CLIENT_API`

```python
ENABLE_CLIENT_API: bool = Field(default=False, description='Enable client API endpoints')
```

##### `leadr.config.TestSettings.ENV`

```python
ENV: str = Field(default=..., description="Environment name (e.g., 'DEV', 'PROD', 'TEST'). Required.")
```

##### `leadr.config.TestSettings.GEOIP_DATABASE_PATH`

```python
GEOIP_DATABASE_PATH: Path = Field(default=(PROJ_ROOT / '.geoip'), description='Directory path for storing GeoIP databases')
```

##### `leadr.config.TestSettings.GEOIP_REFRESH_DAYS`

```python
GEOIP_REFRESH_DAYS: int = Field(default=7, description='Number of days between GeoIP database refresh downloads (default: 7 days)')
```

##### `leadr.config.TestSettings.JWT_LIFETIME_SECONDS`

```python
JWT_LIFETIME_SECONDS: int = Field(default=3600, description='JWT token lifetime in seconds (default: 1 hour)')
```

##### `leadr.config.TestSettings.JWT_SECRET`

```python
JWT_SECRET: str = Field(default='your-super-secret-jwt-key-change-in-production', description='Secret key for JWT token signing. MUST be changed in production.')
```

##### `leadr.config.TestSettings.KEYS_PATH`

```python
KEYS_PATH: Path = Field(default=(PROJ_ROOT / '.keys'), description='Directory path for storing cryptographic keys')
```

##### `leadr.config.TestSettings.LOG_DIR`

```python
LOG_DIR: Path = Field(default=(Path('/var/log/leadr')), description='Directory for log files when LOG_TO_FILE is enabled')
```

##### `leadr.config.TestSettings.LOG_JSON`

```python
LOG_JSON: bool = Field(default=True, description='Use JSON format for logs (disable for colored console in dev)')
```

##### `leadr.config.TestSettings.LOG_TO_FILE`

```python
LOG_TO_FILE: bool = Field(default=False, description='Enable file logging in addition to stdout')
```

##### `leadr.config.TestSettings.MAILGUN_API_KEY`

```python
MAILGUN_API_KEY: str = Field(default='mailgun_api_key', description='Mailgun API key for email sending')
```

##### `leadr.config.TestSettings.MAILGUN_DOMAIN`

```python
MAILGUN_DOMAIN: str = Field(default='example.mailgun.org', description='Mailgun domain for email sending')
```

##### `leadr.config.TestSettings.MAXMIND_ACCOUNT_ID`

```python
MAXMIND_ACCOUNT_ID: str = Field(default='', description='MaxMind account ID for database downloads (used for basic auth)')
```

##### `leadr.config.TestSettings.MAXMIND_CITY_DB_URL`

```python
MAXMIND_CITY_DB_URL: str = Field(default='https://download.maxmind.com/geoip/databases/GeoLite2-City/download?suffix=tar.gz', description='MaxMind GeoLite2 City database download URL')
```

##### `leadr.config.TestSettings.MAXMIND_COUNTRY_DB_URL`

```python
MAXMIND_COUNTRY_DB_URL: str = Field(default='https://download.maxmind.com/geoip/databases/GeoLite2-Country/download?suffix=tar.gz', description='MaxMind GeoLite2 Country database download URL')
```

##### `leadr.config.TestSettings.MAXMIND_LICENSE_KEY`

```python
MAXMIND_LICENSE_KEY: str = Field(default='', description='MaxMind license key for database downloads (used for basic auth)')
```

##### `leadr.config.TestSettings.REFRESH_TOKEN_EXPIRY_DAYS`

```python
REFRESH_TOKEN_EXPIRY_DAYS: int = Field(default=30, description='Device refresh token expiration time in days (default: 30 days)')
```

##### `leadr.config.TestSettings.REGISTRATION_RATE_LIMIT_PER_HOUR`

```python
REGISTRATION_RATE_LIMIT_PER_HOUR: int = Field(default=3, description='Maximum verification code requests per email per hour (default: 3)')
```

##### `leadr.config.TestSettings.SCORE_METADATA_MAX_SIZE_BYTES`

```python
SCORE_METADATA_MAX_SIZE_BYTES: int = Field(default=1024, description='Maximum size in bytes for score metadata JSON (default: 1KB)')
```

##### `leadr.config.TestSettings.SOURCE_OAUTH_BASE_URL`

```python
SOURCE_OAUTH_BASE_URL: HttpUrl = Field(default=(HttpUrl('http://localhost:8000')), description='Base URL for OAuth provider')
```

##### `leadr.config.TestSettings.SUPERADMIN_ACCOUNT_NAME`

```python
SUPERADMIN_ACCOUNT_NAME: str = Field(default='LEADR', description='Name of the system account for superadmin users')
```

##### `leadr.config.TestSettings.SUPERADMIN_ACCOUNT_SLUG`

```python
SUPERADMIN_ACCOUNT_SLUG: str = Field(default='leadr', description='URL-friendly slug for the superadmin system account')
```

##### `leadr.config.TestSettings.SUPERADMIN_API_KEY`

```python
SUPERADMIN_API_KEY: str = Field(default='ldr_test_superadmin_key_for_testing_12345678', description='Test superadmin API key (must start with ldr_)')
```

##### `leadr.config.TestSettings.SUPERADMIN_API_KEY_NAME`

```python
SUPERADMIN_API_KEY_NAME: str = Field(default='Superadmin Key', description='Display name for the superadmin API key')
```

##### `leadr.config.TestSettings.SUPERADMIN_DISPLAY_NAME`

```python
SUPERADMIN_DISPLAY_NAME: str = Field(default='LEADR Admin', description='Display name for the superadmin user')
```

##### `leadr.config.TestSettings.SUPERADMIN_EMAIL`

```python
SUPERADMIN_EMAIL: str = Field(default='admin@leadr.gg', description='Email address for the superadmin user')
```

##### `leadr.config.TestSettings.TESTING_EMAIL`

```python
TESTING_EMAIL: str = Field(default='hello@example.com', description='Email address used for testing purposes')
```

##### `leadr.config.TestSettings.VERIFICATION_CODE_EXPIRY_SECONDS`

```python
VERIFICATION_CODE_EXPIRY_SECONDS: int = Field(default=600, description='Expiry time for email verification codes in seconds (default: 10 minutes)')
```

##### `leadr.config.TestSettings.VERIFICATION_TOKEN_EXPIRY_SECONDS`

```python
VERIFICATION_TOKEN_EXPIRY_SECONDS: int = Field(default=600, description='Expiry time for verification JWT tokens in seconds (default: 10 minutes)')
```

##### `leadr.config.TestSettings.model_config`

```python
model_config = SettingsConfigDict(case_sensitive=True, extra='ignore')
```

##### `leadr.config.TestSettings.validate_api_enabled`

```python
validate_api_enabled()
```

Ensure at least one API (Admin or Client) is enabled.

#### `leadr.config.settings`

```python
settings = TestSettings(_env_file=(Path(PROJ_ROOT, '.env.test'))) if os.environ.get('ENV') == 'TEST' else Settings(_env_file=(Path(PROJ_ROOT, '.env')))
```
