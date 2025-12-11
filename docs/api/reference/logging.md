### `leadr.logging`

Structured logging configuration using structlog.

This module configures structlog for the LEADR application with support for:

- JSON output for production (machine-parseable)
- Colored console output for development (human-readable)
- File logging with rotation
- Integration with standard library logging (captures third-party logs)

**Functions:**

- [**bind_contextvars**](#leadr.logging.bind_contextvars) – Bind context variables that will be included in all subsequent log entries.
- [**clear_contextvars**](#leadr.logging.clear_contextvars) – Clear all bound context variables.
- [**get_logger**](#leadr.logging.get_logger) – Get a structlog logger instance.
- [**setup_logging**](#leadr.logging.setup_logging) – Configure structlog for the application.

#### `leadr.logging.bind_contextvars`

```python
bind_contextvars(**kwargs)
```

Bind context variables that will be included in all subsequent log entries.

This is useful for adding request-scoped context like request_id that should
appear in all logs within that context.

**Parameters:**

- \*\***kwargs** (<code>[Any](#typing.Any)</code>) – Key-value pairs to bind to the context

<details class="example" open markdown="1">
<summary>Example</summary>

> > > from leadr.logging import bind_contextvars
> > > bind_contextvars(request_id="req-123", user_id="user-456")
> > >
> > > # All subsequent logs will include request_id and user_id

</details>

#### `leadr.logging.clear_contextvars`

```python
clear_contextvars()
```

Clear all bound context variables.

Call this at the start of a new request to ensure no context leaks
between requests.

#### `leadr.logging.get_logger`

```python
get_logger(name)
```

Get a structlog logger instance.

**Parameters:**

- **name** (<code>[str](#str)</code>) – Logger name, typically __name__ of the calling module

**Returns:**

- <code>[BoundLogger](#structlog.stdlib.BoundLogger)</code> – A bound structlog logger that can be used for structured logging

<details class="example" open markdown="1">
<summary>Example</summary>

> > > from leadr.logging import get_logger
> > > logger = get_logger(__name__)
> > > logger.info("User created", user_id="abc-123")

</details>

#### `leadr.logging.setup_logging`

```python
setup_logging(*, log_level='INFO', json_format=True, log_to_file=False, log_dir=Path('/var/log/leadr'), app_name='LEADR', env='PROD')
```

Configure structlog for the application.

This function sets up structured logging using structlog with integration
to the standard library logging module. This allows both structlog loggers
and standard library loggers (used by third-party packages like uvicorn)
to be processed through the same pipeline.

**Parameters:**

- **log_level** (<code>[str](#str)</code>) – Logging level (DEBUG, INFO, WARNING, ERROR)
- **json_format** (<code>[bool](#bool)</code>) – Use JSON format (True) or colored console (False)
- **log_to_file** (<code>[bool](#bool)</code>) – Enable file logging in addition to stdout
- **log_dir** (<code>[Path](#pathlib.Path)</code>) – Directory for log files when log_to_file is enabled
- **app_name** (<code>[str](#str)</code>) – Application name added to each log entry
- **env** (<code>[str](#str)</code>) – Environment name added to each log entry
