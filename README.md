# Timex

> [!CAUTION]
> This module is deprecated and is provided for backward compatibility only. Do not use for new work.

`timex.Timex` enhances the standard `time.Time` to make it more compatible with JavaScript and SQL. It adjusts JSON marshaling of the zero time to `null` and infers the layout when parsing a string. It also implements the `Scanner` and `Valuer` interfaces for SQL integration.

With the introduction of `omitzero` in Go 1.24, there is no longer need for custom JSON marshaling code for `time.Time`.

If you project relies on the `timex` package in [`fabric`](https://github.com/microbus-io/fabric) v1.10 or earlier:
- `go get github.com/microbus-io/timex`
- Replace all imports of `github.com/microbus-io/fabric/timex` with `github.com/microbus-io/timex`
- Replace all used of `svc.NowX(ctx)` with `timex.New(svc.Now(ctx))`

Going forward:
- Use `omitzero` instead of `omitempty` when marshaling `time.Time`
- Use `sql.NullTime` to interface with the database
