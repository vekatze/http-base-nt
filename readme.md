# http-base

`http-base` provides basic HTTP entities such as requests and responses.

## Installation

```sh
neut get http-base https://github.com/vekatze/http-base-nt/raw/main/archive/0-1-18.tar.zst
```

## Types

### Basics

```neut
// Represents an HTTP request.
data request {
| Request(
    method: request-method,
    path: text,
    fields: header,
    body: text,
  )
}

// Represents an HTTP response.
data response {
| Response(
    status-code: int,
    fields: header,
    body: text,
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
constant header: type {
  list(field)
}

// Represents an HTTP header key-value pair.
data field {
| Field(
    key: text,
    value: text,
  )
}
```

### Utilities

```neut
// A parser for an HTTP/1.1 request.
// You can run this parser using `zonk.parser.run`.
define request-parser(): parser(request)

// A parser for an HTTP/1.1 response.
// You can run this parser using `zonk.parser.run`
define response-parser(): parser(response)

// Formats a request as an HTTP/1.1 request.
define show-request(r: request): text

// Formats a response as an HTTP/1.1 response.
define show-response(r: response): text

// Constructs a response from a status code and a body.
define text-response(status-code: int, body: text)
```
