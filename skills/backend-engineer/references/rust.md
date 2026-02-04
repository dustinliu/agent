# Rust Implementation Guide

## Project Structure

```
project-root/
├── src/
│   ├── main.rs           # Entry point
│   ├── lib.rs            # Library root
│   ├── handlers/
│   │   └── mod.rs
│   ├── services/
│   │   └── mod.rs
│   ├── repositories/
│   │   └── mod.rs
│   └── models/
│       └── mod.rs
├── tests/                # Integration tests
├── Cargo.toml
└── Cargo.lock
```

## Conventions

### Naming
- Modules: snake_case (e.g., `user_handler`)
- Types/Traits: PascalCase (e.g., `UserService`)
- Functions/Variables: snake_case (e.g., `get_user`)
- Constants: SCREAMING_SNAKE_CASE

### Error Handling
- Use `Result<T, E>` for recoverable errors
- Define custom error types with `thiserror`
- Use `anyhow` for application-level errors
- Use `?` operator for propagation

### Testing
- Unit tests in same file: `#[cfg(test)] mod tests`
- Integration tests in `tests/` directory
- Use `#[tokio::test]` for async tests

## Common Patterns

### Dependency Injection
```rust
pub struct UserService<R: UserRepository> {
    repo: R,
}

impl<R: UserRepository> UserService<R> {
    pub fn new(repo: R) -> Self {
        Self { repo }
    }
}
```

### Trait Definition
```rust
#[async_trait]
pub trait UserRepository {
    async fn get_by_id(&self, id: &str) -> Result<User, Error>;
}
```

### Error Types
```rust
use thiserror::Error;

#[derive(Error, Debug)]
pub enum AppError {
    #[error("user not found: {0}")]
    NotFound(String),
    #[error("database error: {0}")]
    Database(#[from] sqlx::Error),
}
```
