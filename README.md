# Bazel Windows MSVC toolchain
A standalone Windows CROSSTOOL for Bazel

# How to use it

### Using [http_archive](https://docs.bazel.build/versions/master/be/workspace.html#http_archive) rule
Add the following to your **WORKSPACE** file, replace `<commit-number>` with the one you want to point to:
```python
http_archive(
    name = "standalone_cc_toolchain",
    urls = ["https://github.com/meteorcloudy/windows-crosstool/archive/<commit-number>.zip"],
    strip_prefix = "windows-crosstool-<commit-number>",
)

load("@standalone_cc_toolchain//:cc_configure.bzl", "cc_configure")

cc_configure()
```
Add `build --crosstool_top=@standalone_local_config_cc//:toolchain` to your **bazelrc** file.

### Using [local_repository](https://docs.bazel.build/versions/master/be/workspace.html#local_repository) rule
Download this repository to your machine, add the following to your **WORKSPACE** file:
```python
local_repository(
    name = "standalone_cc_toolchain",
    path = "<path>/<to>/<your>/windows-crosstool",
)

load("@standalone_cc_toolchain//:cc_configure.bzl", "cc_configure")

cc_configure()
```

Add `build --crosstool_top=@standalone_local_config_cc//:toolchain` to your **bazelrc** file.
