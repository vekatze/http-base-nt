# http-base

`http-base` provides basic HTTP entities such as requests and responses.

## Installation

```sh
neut get http-base https://github.com/vekatze/http-base-nt/raw/main/archive/0-1-50.tar.zst
```

## Types

### Basics

```neut
// Represents an HTTP request.
data request {
| Request(
    method: request-method,
    path: string,
    fields: header,
    body: string,
  )
}

// Represents an HTTP response.
data response {
| Response(
    status-code: int,
    fields: header,
    body: string,
  )
}

// Represents an HTTP request method.
data request-method {
| GET
| HEAD
| POST
| PUT
| DELETE
| OPTIONS
| TRACE
| PATCH
}

// Represents an HTTP header.
alias header {
  list(field)
}

// Represents an HTTP header key-value pair.
data field {
| Field(
    key: string,
    value: string,
  )
}
```

### Utilities

```neut
// A parser for an HTTP/1.1 request.
constant request-parser<c>: zonk(c, request)

// A parser for an HTTP/1.1 response.
constant response-parser<c>: zonk(c, response)

// Formats a request as an HTTP/1.1 request.
define show-request(r: request) -> string

// Formats a response as an HTTP/1.1 response.
define show-response(resp: response) -> string

// Constructs a response from a status code and a body.
define string-response(status-code: int, body: string) -> response
```
