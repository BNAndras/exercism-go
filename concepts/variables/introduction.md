# Introduction

Go is statically typed, so every variable will have a type known at compile time.
Once declared, a variable's type cannot change.

The `var` statement typically declares both a variable and its type:

```go
var count int
```

Go can infer a type from a provided initial value:

```go
var count = 1 // count is int
```

Inside a function, the `:=` short assignment statement accomplishes this in a concise format:

```go
count := 1
```

The `=` assignment operator can set a new value for an existing variable:

```go
count := 1
count = 2
```

The new value must have the same type as the variable:

```go
count := 1
count = false // compile error: a Boolean is not an int
```

A variable in Go always has a value.
If no initial value is set at declaration, Go provides one, a zero value, based on the variable type.

```go
var count int      // 0
var name string   // ""
var ready bool    // false
```
