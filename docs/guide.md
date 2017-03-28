# User guide

Maailma's idea of configuration is a single map that is read on startup. What
Maailma provides is tools for loading and merging configuration from various
sources.

The code examples in this guide assume that `maailma.core` is required as `m`.

```clojure
(require '[maailma.core :as m])
```

## The opinionated interface

The simplest way to use Maailma is to use `maailma.core/read-config!`.

```clojure
(m/read-config! "app")
```

The first argument is the used as a prefix for the names of environment
variables and JVM system properties. The configuration is read in this order:

- An EDN resource called `config-defaults.edn`.
- Environment variables with the given prefix.
- System properties with the given prefix.
- A file `config-local.edn` in the working directory.

Finally, if you want to override something, you can add a second argument that
contains your data:

```clojure
(m/read-config! "app" {:http {:port 8080}})
```

## The less opinionated interface

If you want more control over the configuration sources, you can use
`maailma.core/build-config`. You call it with the configuration sources you want
to use and it merges them.

For example, maybe you only want to read configuration from a file called
`my-config.edn` and environmental variables prefix with `APP`. Here's your
solution:

```clojure
(m/build-config
  (m/file "./my-config.edn")
  (m/env "APP"))
```

## Configuration sources



