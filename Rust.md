# Anatomy of a DinoPark Rust service

All DinoPark Rust services use [actix] as their web framework. In general the
endpoints are separated into small apps:

```ini
src
├── endpoint1
│   ├── app.rs
│   ├── mod.rs
│   └── …
├── endpoint2
│   ├── app.rs
│   ├── mod.rs
│   └── …
├── healthz.rs # basic health check endpoint for k8s
├── main.rs
└── settings.rs
```

## Scopes

Permissions are and authentication happens via [DinoPark Gate]. It decodes and verifies
the id_token and translates it into _user\_id_, _scope_, _groups_scope_ and _AAL_. Routes
may be guarded to on a minimal requirement on either of those claims by [DinoPark Guard]
via a simple annotation like: `#[guard(Staff, Creator, Medium)]` which would only allow
access to this route if the logged in user is a staff member, is an allowed access group creator and is logged in via a MFA'd login method.

## CIS Integration

All services use a common [CIS client] to interact with the [CIS] APIs. Signing fields
is also supported given the correct signing keys.

## Code Style and Rules

All Rust code must pass at least:
```
cargo fmt --all -- --check
cargo clippy -- -D warnings
cargo test --all
```


[actix]: https://actix.rs/
[DinoPark Gate]: https://github.com/mozilla-iam/dino-park-gate
[DinoPark Guard]: https://github.com/mozilla-iam/dino-park-guard
[CIS client]: https://github.com/mozilla-iam/cis_client-rust
[CIS]: https://github.com/mozilla-iam/cis