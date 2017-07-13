# Bazel Windows MSVC toolchain
A standalone Windows CROSSTOOL for Bazel

# How to use it

### Using [new_http_archive](https://docs.bazel.build/versions/master/be/workspace.html#new_http_archive) rule
Add the following to your **WORKSPACE** file, replace `<commit-number>` with the one you want to point to:
```python
new_http_archive(
    name = "standalone_cc_toolchain",
    urls = ["https://github.com/meteorcloudy/windows-crosstool/archive/<commit-number>.zip"],
    strip_prefix = "windows-crosstool-<commit-number>",
    build_file_content = "",
)

load("@standalone_cc_toolchain//:cc_configure.bzl", "cc_configure")

cc_configure()
```
Add `build --crosstool_top=@standalone_local_config_cc//:toolchain` to your **bazelrc** file.

### Using [new_local_repository](https://docs.bazel.build/versions/master/be/workspace.html#new_local_repository) rule
Download this repository to your machine, add the following to your **WORKSPACE** file:
```python
new_local_repository(
    name = "standalone_cc_toolchain",
    path = "<path>/<to>/<your>/windows-crosstool",
    build_file_content = "",
)

load("@standalone_cc_toolchain//:cc_configure.bzl", "cc_configure")

cc_configure()
```

Add `build --crosstool_top=@standalone_local_config_cc//:toolchain` to your **bazelrc** file.
