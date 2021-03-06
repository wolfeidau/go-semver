# go-semver

[![Build Status](https://travis-ci.org/slantview/go-semver.png)](https://travis-ci.org/slantview/go-semver)
[![Coverage Status](https://coveralls.io/repos/slantview/go-semver/badge.png?branch=master)](https://coveralls.io/r/slantview/go-semver?branch=master)
[![GoDoc](https://godoc.org/github.com/slantview/go-semver?status.png)](http://godoc.org/github.com/slantview/go-semver)

A library for using [semantic versioning](http://semver.org/) in Go.

## Example Usage

```go

s, err := semver.NewVersion("1.0.0")
if err != nil {
    fmt.Printf("Unable to parse version: %s", err)
}

fmt.Printf("%s", s.String())
// "1.0.0"

s.BumpPatch()
fmt.Printf("%s", s.String())
// "1.0.1"

s.BumpMinor()
fmt.Printf("%s", s.String())
// "1.1.0"

s.BumpMajor()
fmt.Printf("%s", s.String())
// "2.0.0"

s.SetPrerelease("alpha")
fmt.Printf("%s", s.String())
// "2.0.0-alpha.1"

s.BumpPrerelease()
fmt.Printf("%s", s.String())
// "2.0.0-alpha.2"

s.SetMetadata("build")
fmt.Printf("%s", s.String())
// "2.0.0+build.1"

s.BumpBuild()
fmt.Printf("%s", s.String())
// "2.0.0+build.2"

v1, _ := semver.NewVersion("1.0.0")
v2, _ := semver.NewVersion("1.0.1")

v1.LessThan(v2) // true
v1.GreaterThan(v2) // false
v1.Equals(v2) // false

```

Author: Steve Rude <steve@slantview.com>