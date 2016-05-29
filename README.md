# Libkermit
[![GoDoc](https://godoc.org/github.com/libkermit/compose-check?status.png)](https://godoc.org/github.com/libkermit/compose-check)
[![Build Status](https://travis-ci.org/libkermit/compose-check.svg?branch=master)](https://travis-ci.org/libkermit/compose-check)
[![Go Report Card](https://goreportcard.com/badge/github.com/libkermit/compose-check)](https://goreportcard.com/report/github.com/libkermit/compose-check)
[![License](https://img.shields.io/github/license/libkermit/compose-check.svg)]()

When `libkermit/compose` meet with `go-check`.

**Note: This is experimental and not even implemented yet. You are on your own right now**


## Package `compose`

This package map the `compose` package but takes a `*check.C` struct
on all methods. The idea is to write even less. Let's write the same
example as above.


```go
package yours

import (
    "testing"

	"github.com/go-check/check"
    "github.com/libkermit/compose-check"
)

// Hook up gocheck into the "go test" runner
func Test(t *testing.T) { check.TestingT(t) }

type CheckSuite struct{}

var _ = check.Suite(&CheckSuite{})

func (s *CheckSuite) TestItMyFriend(c *check.C) {
    project := compose.CreateProject(c, "simple", "./assets/simple.yml")
    project.Start(c)

    // Do your stuff

    project.Stop(c)
}
```



## Other packages to come

- `suite` : functions and structs to setup tests suites.


