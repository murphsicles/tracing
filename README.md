# @log/tracing — Structured Logging for Zeta

Auto-converted from [tracing](https://crates.io/crates/tracing) v0.2.6 via [Dark Factory](https://github.com/murphsicles/dark-factory).

## Features
- **Structured events** — log with typed key-value fields, spans, and explicit levels
- **Five levels** — Error, Warn, Info, Debug, Trace
- **Composable** — subscriber-based architecture for filtering, formatting, and routing
- **Span tracking** — enter/exit instrumentation with automatic parent-child relationships
- **Per-layer filtering** — different log levels per module or component

## Usage
```zeta
use @log/tracing::{info, warn, error, debug, trace, span};
use @log/tracing_subscriber;

let subscriber = tracing_subscriber::fmt()
    .with_max_level(Level::DEBUG)
    .init();

info!(user_id = 42, "User logged in");
```

## Stats: ~5,600 lines (tracing + tracing-core + tracing-subscriber), 0 unsupported items

## License
MIT