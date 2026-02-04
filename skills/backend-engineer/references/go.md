# Go Implementation Guide

## Conventions

### Formatting
Run `goimports` after every code change to format and organize imports.

### Testing
- Test file: `*_test.go` in same package
- Table-driven tests preferred
- Use `testify` for assertions if needed

## Common Patterns

### Dependency Injection
```go
type UserService struct {
    repo UserRepository
}

func NewUserService(repo UserRepository) *UserService {
    return &UserService{repo: repo}
}
```

### Interface Definition
```go
// Define interfaces where they are used, not where implemented
type UserRepository interface {
    GetByID(ctx context.Context, id string) (*User, error)
}
```

### Context Usage
- First parameter for functions that do I/O
- Pass through, don't store in structs
