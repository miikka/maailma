# Maailma [![Build Status](https://travis-ci.org/metosin/maailma.svg?branch=master)](https://travis-ci.org/metosin/maailma)

[![Clojars Project](http://clojars.org/metosin/maailma/latest-version.svg)](http://clojars.org/metosin/maailma)

[API Docs](http://metosin.github.io/maailma/maailma.core.html).

## Project statement

Unlike more general of our libraries (like
[compojure-api](https://github.com/metosin/compojure-api) and
[ring-swagger](https://github.com/metosin/ring-swagger)) this project is
primarily intended for use in Metosin's projects. Feel free to use, but
don't expect full support.

- We might remove features if we think they are not useful anymore
- We will reject PRs and issues about features we wouldn't use ourselves

## Features

- Reads configuration from multiple sources and recursively merge it
    - EDN files in classpath – shipped with JAR, useful for default options
    - EDN files in filesystem – created by hand or by deploy tooling
    - Environment variables
    - Java properties
    - Override parameter – useful for overriding options for [test systems](https://github.com/metosin/palikka/blob/master/test/palikka/core_test.clj#L9)
- Encrypted values using EDN tag
    - `{:secret-value #ENC "OAgq01UxKpRp9S+MrIyf1w=="}`
    - Provides a password on read time to decrypt the values
    - Should be useful for providing passwords for development environment
    - Probably still not a good idea to share secrets publicly (at least check
    the encryption options first)

## License

Copyright © 2015 [Metosin Oy](http://www.metosin.fi)

Distributed under the Eclipse Public License, the same as Clojure.
