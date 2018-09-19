# strict-json

This is a fork of Go's standard `encoding/json` with the following changes to `Unmarshal`:

- Does not allow unmarshaling `null`s into primitives (strings, ints...)
- Adds `required` struct tag to force a field to be present when unmarshaling.
- Errors on two object fields with the same key (original one keeps the value of the last appearance
- Strictly case sensitive.

`strict-json` is API compatible with the original `encoding/json`, you can drop it in place and it should just work.

`strict-json` is ideal for unmarshaling request bodies of a JSON REST API. If
your API is  too liberal when unmarshaling JSON, clients might end up depending
on that  behavior, forcing you to support it forever. The best solution is to be
as strict as possible.

For further strictness, it's highly recommended to set `DisallowUnknownFields` (also present on the original `encoding/json`).
