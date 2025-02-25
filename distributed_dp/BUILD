load("@rules_python//python:defs.bzl", "py_binary", "py_library", "py_test")

package(default_visibility = ["//private_linear_compression:__subpackages__"])

licenses(["notice"])

py_library(
    name = "accounting_utils",
    srcs = ["accounting_utils.py"],
    srcs_version = "PY3",
    visibility = [
        "//private_linear_compression:__subpackages__",
    ],
)

py_library(
    name = "compression_query",
    srcs = ["compression_query.py"],
    deps = [":compression_utils"],
)

py_test(
    name = "compression_query_test",
    srcs = ["compression_query_test.py"],
    python_version = "PY3",
    deps = [
        ":compression_query",
        ":distributed_discrete_gaussian_query",
    ],
)

py_library(
    name = "compression_utils",
    srcs = ["compression_utils.py"],
    visibility = [
        "//private_linear_compression:__subpackages__",
    ],
)

py_test(
    name = "compression_utils_test",
    srcs = ["compression_utils_test.py"],
    python_version = "PY3",
    deps = [":compression_utils"],
)

py_library(
    name = "ddpquery_utils",
    srcs = ["ddpquery_utils.py"],
    srcs_version = "PY3",
    deps = [
        ":accounting_utils",
        ":compression_query",
        ":distributed_discrete_gaussian_query",
        ":distributed_skellam_query",
    ],
)

py_library(
    name = "discrete_gaussian_utils",
    srcs = ["discrete_gaussian_utils.py"],
)

py_test(
    name = "discrete_gaussian_utils_test",
    srcs = ["discrete_gaussian_utils_test.py"],
    python_version = "PY3",
    deps = [":discrete_gaussian_utils"],
)

py_library(
    name = "distributed_discrete_gaussian_query",
    srcs = ["distributed_discrete_gaussian_query.py"],
    deps = [":discrete_gaussian_utils"],
)

py_test(
    name = "distributed_discrete_gaussian_query_test",
    srcs = ["distributed_discrete_gaussian_query_test.py"],
    python_version = "PY3",
    deps = [
        ":discrete_gaussian_utils",
        ":distributed_discrete_gaussian_query",
    ],
)

py_library(
    name = "distributed_skellam_query",
    srcs = ["distributed_skellam_query.py"],
)

py_test(
    name = "distributed_skellam_query_test",
    srcs = ["distributed_skellam_query_test.py"],
    python_version = "PY3",
    deps = [":distributed_skellam_query"],
)

py_library(
    name = "dme_utils",
    srcs = ["dme_utils.py"],
    srcs_version = "PY3",
    deps = [":modular_clipping_factory"],
)

py_binary(
    name = "dme_run",
    srcs = ["dme_run.py"],
    python_version = "PY3",
    srcs_version = "PY3",
    deps = [
        ":accounting_utils",
        ":ddpquery_utils",
        ":dme_utils",
    ],
)

py_library(
    name = "fl_utils",
    srcs = ["fl_utils.py"],
    srcs_version = "PY3",
    deps = [
        ":accounting_utils",
        ":ddpquery_utils",
        ":modular_clipping_factory",
    ],
)

py_binary(
    name = "fl_run",
    srcs = ["fl_run.py"],
    python_version = "PY3",
    srcs_version = "PY3",
    deps = [
        ":fl_utils",
        "//utils:task_utils",
        "//utils:training_utils",
        "//utils:utils_impl",
        "//utils/optimizers:optimizer_utils",
    ],
)

py_library(
    name = "modular_clipping_factory",
    srcs = ["modular_clipping_factory.py"],
    srcs_version = "PY3",
)

py_test(
    name = "modular_clipping_factory_test",
    srcs = ["modular_clipping_factory_test.py"],
    python_version = "PY3",
    srcs_version = "PY3",
    deps = [":modular_clipping_factory"],
)

filegroup(
    name = "standalone_scripts",
    srcs = [
        "dme_merge_repeats.py",
        "plot_client_dropout.py",
    ],
    tags = ["ignore_srcs"],
)
