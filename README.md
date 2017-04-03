# go-base64

A raw base64 URL encoding library for JSON.

[Code of Conduct](./.github/CONDUCT.md) |
[Contribution Guidelines](./.github/CONTRIBUTING.md)

[![GitHub release](https://img.shields.io/github/tag/manifoldco/go-base64.svg?label=latest)](https://github.com/manifoldco/go-base64/releases)
[![GoDoc](https://img.shields.io/badge/godoc-reference-blue.svg)](https://godoc.org/github.com/manifoldco/go-base64)
[![Travis](https://img.shields.io/travis/manifoldco/go-base64/master.svg)](https://travis-ci.org/manifoldco/go-base64)
[![Go Report Card](https://goreportcard.com/badge/github.com/manifoldco/go-base64)](https://goreportcard.com/report/github.com/manifoldco/go-base64)
[![License](https://img.shields.io/badge/license-BSD-blue.svg)](./LICENSE.md)

## Usage

`base64` Provides a convenient way to read and write raw (no padding) base64 URL
values.

```go
package main

import (
	"encoding/json"
	"fmt"

	"github.com/manifoldco/go-base64"
)

type Example struct {
	Name        string        `json:"name"`
	Data        *base64.Value `json:"data"`
	RegularData []byte        `json:"regular"`
}

func main() {
	sample := []byte{0xF, 0xEE, 0xD, 0xC, 0x0D}
	e := &Example{
		Name:        "test data",
		Data:        base64.New(sample),
		RegularData: sample,
	}

	o, _ := json.MarshalIndent(e, "", "  ")
	fmt.Println(string(o))
}
```

Outputs:

```
{
  "name": "test data",
  "data": "D-4NDA0",
  "regular": "D+4NDA0="
}
```
