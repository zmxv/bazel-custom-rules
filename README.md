Bazel custom build rules for TypeScript
==

Custom [Bazel](http://bazel.io/) build rules to compile [TypeScript](http://www.typescriptlang.org).

Syntax
--
```python
ts_library(
  name = "externs",
  srcs = ["externs.d.ts"],
)

ts_library(
  name = "common",
  srcs = ["common.ts"],
  deps = [":externs"],
)

ts_binary(
  name = "main"
  srcs = ["main.ts"],
  deps = [":common"],
  flags = [
      "--removeComments",
      "--noEmitOnError",
  ],
)
```

Build example
--
1. Install [Bazel](http://bazel.io/)
1. Add `load("/build-rules/typescript", "ts_library", "ts_binary")` to `%bazel/tools/build_rules/prelude_bazel`
1. Run `git clone https://github.com/zmxv/bazel-custom-rules && cd bazel-custom-rules`
1. Run `bazel build //examples/typescript:main`
1. Examine the output in `bazel-bin/examples/typescript/main.js`

