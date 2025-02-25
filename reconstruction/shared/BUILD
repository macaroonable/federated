load("@rules_python//python:defs.bzl", "py_binary", "py_library", "py_test")

licenses(["notice"])

package(default_visibility = ["//reconstruction:__subpackages__"])

py_library(
    name = "federated_trainer_lib",
    srcs = ["federated_trainer.py"],
    srcs_version = "PY3",
    deps = [
        ":federated_evaluation",
        ":federated_trainer_utils",
        "//reconstruction:evaluation_computation",
        "//reconstruction:reconstruction_model",
        "//reconstruction:reconstruction_utils",
        "//reconstruction:training_process",
        "//reconstruction/movielens:federated_movielens",
        "//reconstruction/stackoverflow:federated_stackoverflow",
        "//utils:utils_impl",
        "//utils/optimizers:optimizer_utils",
    ],
)

py_binary(
    name = "federated_trainer",
    srcs = ["federated_trainer.py"],
    python_version = "PY3",
    srcs_version = "PY3",
    deps = [
        ":federated_trainer_lib",
    ],
)

py_library(
    name = "federated_trainer_utils",
    srcs = ["federated_trainer_utils.py"],
    srcs_version = "PY3",
    deps = ["//reconstruction:reconstruction_utils"],
)

py_library(
    name = "federated_evaluation",
    srcs = ["federated_evaluation.py"],
    srcs_version = "PY3",
    deps = [
        "//reconstruction:evaluation_computation",
        "//reconstruction:keras_utils",
        "//reconstruction:reconstruction_utils",
    ],
)

py_test(
    name = "federated_trainer_utils_test",
    srcs = ["federated_trainer_utils_test.py"],
    python_version = "PY3",
    srcs_version = "PY3",
    deps = [":federated_trainer_utils"],
)

py_test(
    name = "federated_evaluation_test",
    srcs = ["federated_evaluation_test.py"],
    python_version = "PY3",
    srcs_version = "PY3",
    deps = [
        ":federated_evaluation",
        "//reconstruction:keras_utils",
        "//reconstruction:reconstruction_model",
    ],
)

py_test(
    name = "federated_tasks_test",
    size = "large",
    timeout = "eternal",
    srcs = ["federated_tasks_test.py"],
    data = ["//reconstruction/movielens/testdata:movielens_small"],
    python_version = "PY3",
    srcs_version = "PY3",
    tags = [
        "manual",
        "nopresubmit",
    ],
    deps = [
        "//reconstruction:evaluation_computation",
        "//reconstruction:reconstruction_model",
        "//reconstruction:reconstruction_utils",
        "//reconstruction:training_process",
        "//reconstruction/movielens:federated_movielens",
        "//reconstruction/shared:federated_evaluation",
        "//reconstruction/stackoverflow:federated_stackoverflow",
    ],
)
