package(default_visibility = ["//visibility:public"])

load("//tools:build_rules/go.bzl", "go_binary")
load("@io_bazel_rules_docker//container:container.bzl", "container_image")

go_binary(
    name = "envserver",
    srcs = [
        "main.go",
    ],
)

container_image(
    name = "docker",
    base = "@ubuntu//image",
    files = [
        ":envserver",
    ],
)
