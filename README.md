## `deno_bindgen`

This tool aims to simplify glue code generation for Deno FFI libraries written
in Rust.

### Quickstart

```shell
# install CLI
deno install -Afq -n deno_bindgen https://raw.githubusercontent.com/littledivy/deno_bindgen/main/cli.ts
```

```toml
# Cargo.toml
[dependencies]
deno_bindgen = { git = "https://github.com/littledivy/deno_bindgen" }
```

```rust
// add.rs
use deno_bindgen::deno_bindgen;

#[deno_bindgen]
pub struct Input {
  a: i32,
  b: i32,
}

#[deno_bindgen]
fn add(input: Input) -> i32 {
  input.a + input.b
}
```

```shell
$ deno_bindgen
```

```typescript
// add.ts
import { add } from "./bindings/bindings.ts";

add({ a: 1, b: 2 }); // 3
```