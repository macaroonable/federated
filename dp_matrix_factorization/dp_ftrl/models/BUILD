load("@rules_python//python:defs.bzl", "py_library", "py_test")

package(default_visibility = ["//dp_matrix_factorization/dp_ftrl:__subpackages__"])

licenses(["notice"])

py_library(
    name = "stackoverflow_models",
    srcs = ["stackoverflow_models.py"],
    srcs_version = "PY3",
)

py_test(
    name = "stackoverflow_models_test",
    srcs = ["stackoverflow_models_test.py"],
    python_version = "PY3",
    srcs_version = "PY3",
    deps = [":stackoverflow_models"],
)
