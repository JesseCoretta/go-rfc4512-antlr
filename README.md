# go-rfc4512-antlr

[![ANTLR4](https://img.shields.io/badge/antlr-blue?label=%E2%92%B6&labelColor=gray&color=magenta&cacheSeconds=86400)](https://www.antlr.org/) [![RFC4512](https://img.shields.io/badge/RFC-4512-blue)](https://datatracker.ietf.org/doc/html/rfc4512) [![Go Reference](https://pkg.go.dev/badge/github.com/JesseCoretta/go-rfc4512-antlr.svg)](https://pkg.go.dev/github.com/JesseCoretta/go-rfc4512-antlr) [![Software License](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat)](https://github.com/JesseCoretta/go-rfc4512-antlr/blob/main/LICENSE)

Package rfc4512antlr implements Sections 2.5 and 4 of RFC 4512 by way of an unmodified ANTLR4-generated codebase.

## ANTLR

See the `_grammar/RFC4512.g4` file within this repository for ANTLR grammar. Using this file, the codebase was auto-generated using the following `antlr4` command:

```
$ antlr4 -Dlanguage=Go -package rfc4512antlr RFC4512.g4
```

For details on ANTLR, click the above ANTLR badge.

If alterations are desired, modify the above grammar file and regenerate code as needed. Remember it is NOT recommended for auto-generated code to be modified in any way. Code enhancements, convenience wrappers and other extensions devised by the adopter(s) should ONLY be made in separate files sharing the same package namespace.

## Features

  - Compliant RFC 4512 syntax implementation
  - Extremely forgiving of newlines, hanging indents and line-terminating Bash-style comments of schema definitions

## Cyclomatics Notice

Please note that due to the complexity and flexibility of the grammar design (and some questionable antlr4-go design decisions) the ANTLR-generated codebase for the RFC4512 grammar has some pretty high cyclomatic factors.

The upside of this is that a schema instance is usually only spawned once per runtime, and not in rapid succession through multiple threads. A schema is a source of truth, and conceptually it should be a "singular" entity in a process, model or state machine.

Thus the performance of this package -- while still adequately fast -- was really the lowest priority in terms of design goals.
