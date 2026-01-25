# Rust Coding Guidelines

This document outlines the latest coding standards and best practices for Rust. Please refer to this document when developing Rust projects.

## 1. Official Tooling
- **rustfmt**: Must use `rustfmt` for code formatting.
  - Follow the default style: 4-space indentation, 100-character line width.
  - Rust 2024 edition brings updates to sorting rules (e.g., version sorting for `x8`, `x16`, etc.).
- **clippy**: Must use `clippy` for linting.
  - Address `clippy` warnings during development.
  - It is recommended to include `cargo clippy -- -D warnings` in the CI/CD pipeline to ensure code quality.

## 2. Naming Conventions
- **Types (Structs, Enums)**: Use `UpperCamelCase` (PascalCase).
- **Enum Variants**: Use `UpperCamelCase`.
- **Functions, Methods, Variables, Modules**: Use `snake_case`.
- **Constants, Statics**: Use `SCREAMING_SNAKE_CASE`.
- **Naming Principle**: Clarity over brevity; avoid excessive abbreviations.

## 3. Idiomatic Rust
- **Borrow Checker**: Leverage Ownership and Borrowing mechanisms; prioritize using References over excessive Cloning.
- **Error Handling**:
  - Use `Option` for values that may be null.
  - Use `Result` for operations that may fail.
  - Avoid using `unwrap()`; in production code, use `expect()` or appropriate error propagation (`?`).
- **Module Organization**: Place Structs and their `impl` blocks in the same file, utilizing modules for functional encapsulation.
- **Readability**: Avoid mixing too many high-level and low-level operations within a single function.

## 4. Security Best Practices
- **Type System**: Utilize the Type System to catch errors at compile time, such as using the New Type Pattern to avoid type confusion.
- **Unsafe Code**:
  - Use `unsafe` only when absolutely necessary (e.g., FFI, extreme optimization).
  - Must provide detailed comments explaining why `unsafe` is required and how safety is guaranteed.
  - Must undergo rigorous review.
- **Input Validation**: Perform strict validation on all external inputs.
- **Overflow Checks**: It is recommended to enable Integer Overflow checks for release builds or use checked arithmetic (`checked_add`, etc.).
- **Concurrency**: Use safe concurrency primitives like `Arc<Mutex<T>>` to avoid Data Races.

## 5. Unit Test Best Practices
- **Incremental Testing**:
  - Write and execute unit tests as early as possible to confirm the current implementation is correct.
  - Do not wait until all code is completed to start writing unit tests.
  - The earlier unit testing begins, the better.
- **Test Structure**:
  - Unit Tests are typically located in the same file as the code under test, placed within a `#[cfg(test)] mod tests { ... }` block.
  - Integration Tests are placed in the `tests/` directory at the project root. Do not implement integration tests; these are to be implemented by QA.
- **Test Runner**:
  - Strongly recommend using [cargo-nextest](https://nexte.st/) as the Test Runner for faster execution and clearer output.
- **Naming**:
  - Test names should be descriptive, clearly stating the scenario and expected behavior (e.g., `succeeds_with_empty_input` instead of `test1`).
- **Mocking Strategy**:
  - Avoid excessive Mocking; test pure logical operations directly.
  - Use Mocking when isolating external dependencies (e.g., databases, network) is necessary.
  - Recommend using the `mockall` crate (`#[automock]`) or defining Traits for Dependency Injection.
- **Assertions**:
  - Utilize `assert_eq!`, `assert_ne!`, and `assert!(expression)`.
  - For Result/Option, you can use `unwrap()` or `expect()` to fail fast in tests, or have the test return `Result<(), E>` to use the `?` operator.
- **Edge Cases**: Always test boundary conditions (e.g., empty input, maximum values, incorrect formats).
- **Test Coverage**:
  - Strongly recommend using `cargo-llvm-cov` to verify the overall coverage of all Unit Tests.
  - **Requirement**: Overall Coverage must be **85% or higher**.
  - Suggest adding coverage reports as a quality metric in the project.

## 6. Rust 2024 Edition Considerations
- Note new syntax features (such as improved `if-let`).
- For large project upgrades, it is recommended to use `cargo fix --edition` in stages.
