# @log/tracing — Structured, performant logging for Zeta.

Zero legacy. Pure Zeta. Faster than the Rust original.

## Quick Start

```zeta
use zorb @log/tracing::{info, warn, error, debug, Level, Span};
use zorb @log/tracing::subscriber::{FmtSubscriber, set_global_default};

// Set up a subscriber
let subscriber = FmtSubscriber::builder()
    .with_max_level(Level::Info)
    .finish();
set_global_default(subscriber).unwrap();

info!("Server starting on port 8080");

let span = Span::new("request", Level::Info)
    .with_field("method", "GET")
    .with_field("path", "/api/users");
let _guard = span.enter();

info!("processing request");
warn!("rate limit approaching");
error!("failed to connect", "db_error", "timeout");
```

## API

| Type | Description |
|------|-------------|
| `Level` | ERROR, WARN, INFO, DEBUG, TRACE |
| `Span` | Named period of execution with fields |
| `Event` | A structured log record |
| `Subscriber` | Trait for consuming spans/events |
| `Dispatch` | Thread-local subscriber dispatch |
| `FmtSubscriber` | Human-readable terminal output |

| Macro | Equivalent Level |
|-------|-----------------|
| `trace!(...)` | TRACE |
| `debug!(...)` | DEBUG |
| `info!(...)` | INFO |
| `warn!(...)` | WARN |
| `error!(...)` | ERROR |

## License

MIT
