# UUID package for Go language

[![Build Status](https://travis-ci.org/lwalen/uuid.png?branch=master)](https://travis-ci.org/lwalen/uuid)
[![Coverage Status](https://coveralls.io/repos/github/lwalen/uuid/badge.svg?branch=master)](https://coveralls.io/github/lwalen/uuid)
[![GoDoc](http://godoc.org/github.com/lwalen/uuid?status.png)](http://godoc.org/github.com/lwalen/uuid)

## Differences from [satori/go.uuid](https://github.com/satori/go.uuid)

* Implementation of [driver.Valuer](https://golang.org/pkg/database/sql/driver/#Valuer)
returns `nil` instead for Nil UUID, to produce NULL in database fields. (Will panic if not nullable)
* Unmarshals `NULL` database value into Nil UUID.
* Provides [`Must`](https://godoc.org/github.com/lwalen/uuid#Must) helper instead of `*OrNil` functions.
* Provides methods to output base64 strings.
* Removes other parts of API that I don't need.

***

This package provides pure Go implementation of Universally Unique Identifier (UUID). Supported both creation and parsing of UUIDs.

With 100% test coverage and benchmarks out of box.

Supported versions:
* Version 1, based on timestamp and MAC address (RFC 4122)
* Version 2, based on timestamp, MAC address and POSIX UID/GID (DCE 1.1)
* Version 3, based on MD5 hashing (RFC 4122)
* Version 4, based on random numbers (RFC 4122)
* Version 5, based on SHA-1 hashing (RFC 4122)

## Installation

Use the `go` command:

	$ go get github.com/lwalen/uuid

## Requirements

UUID package requires Go >= 1.2.

## Example

```go
package main

import (
	"fmt"
	"github.com/lwalen/uuid"
)

func main() {
	// Creating UUID Version 4
	u1 := uuid.NewV4()
	fmt.Printf("UUIDv4: %s\n", u1)

	// Parsing UUID from string input
	u2, err := uuid.FromString("6ba7b810-9dad-11d1-80b4-00c04fd430c8")
	if err != nil {
		fmt.Printf("Something gone wrong: %s", err)
	}
	fmt.Printf("Successfully parsed: %s", u2)
}
```

## Documentation

[Documentation](http://godoc.org/github.com/lwalen/uuid) is hosted at GoDoc project.

## Links
* [RFC 4122](http://tools.ietf.org/html/rfc4122)
* [DCE 1.1: Authentication and Security Services](http://pubs.opengroup.org/onlinepubs/9696989899/chap5.htm#tagcjh_08_02_01_01)

## Copyright

Copyright (C) 2013-2016 by Maxim Bublis <b@codemonkey.ru>.

UUID package released under MIT License.
See [LICENSE](https://github.com/lwalen/uuid/blob/master/LICENSE) for details.
