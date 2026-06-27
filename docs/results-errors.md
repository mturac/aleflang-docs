# Results and Errors

Alef favors explicit result values for operations that can fail.

## Result

```alef
fn divide(a: f64, b: f64) -> Result<f64, string> {
    if b == 0.0 {
        return Err("division by zero")
    }
    return Ok(a / b)
}
```

## `?` Operator

```alef
let x = divide(20.0, 4.0)?
let y = divide(x, 2.0)?
```

`?` unwraps `Ok(value)` and early-returns on `Err(error)`.

## HTTP Client

Native HTTP client calls return `Result<HttpResponse, string>`:

```alef
match std.http.get("https://example.com") {
    Ok(r) => println(r.body),
    Err(e) => println("request failed: {e}"),
}
```

This makes timeout, DNS, and transport failures visible in normal code.

