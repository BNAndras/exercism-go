# About

In Go, `range` iterates over slices, arrays, maps, strings, and channels.
Each iteration yields two values: the index (or key) and a copy of the element at that position.

## Iterating over a Slice

`range` over a slice yields the index and value of each element in order:

```go
vals := []int{10, 20, 30}
for i, v := range vals {
    fmt.Println(i, v)
}
// 0 10
// 1 20
// 2 30
```

## Iterating over a Map

`range` over a map yields each key and value, but the iteration order is not guaranteed.
Go deliberately randomizes map iteration order, so the same program may produce different output on each run.

```go
hash := map[int]int{9: 10, 99: 20, 999: 30}
for k, v := range hash {
    fmt.Println(k, v)
}
// 99 20
// 999 30
// 9 10
```

## Omitting Index or Value

Go will not compile if a variable is declared but never used.
If only the value is needed, assign the index or key to `_` to ignore it.

```go
vals := []int{10, 20, 30}
for i, v := range vals {
    fmt.Println(v)
}
// Go build failed: declared and not used: i
```

```go
vals := []int{10, 20, 30}
for _, v := range vals {
    fmt.Println(v)
}
// 10
// 20
// 30
```

If only the index is needed, assign the value to `_` or omit it completely:

```go
vals := []int{10, 20, 30}
for i := range vals {
    fmt.Println(i)
}
// 0
// 1
// 2
```

If neither the index nor the value is needed, both can be omitted:

```go
vals := []int{10, 20, 30}
count := 0
for range vals {
    count++
}
// count == 3
```

## Range over an Integer

Since Go 1.22, `range` can iterate over an integer directly, yielding values from `0` up to but not including that integer:

```go
for n := range 3 {
    fmt.Println(n)
}
// 0
// 1
// 2
```
