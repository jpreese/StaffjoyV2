package(default_visibility = ["//visibility:public"])

load("//tools:build_rules/go.bzl", "go_binary")
load("@io_bazel_rules_docker//container:container.bzl", "container_image")

go_binary(
    name = "smsserver",
    srcs = [
        "config.go",
        "helpers.go",
        "main.go",
        "sender.go",
        "server.go",
        "whitelist.go",
    ],
    deps = [
        "//auth",
        "//environments",
        "//healthcheck",
        "//sms",
        "@go_gorilla_mux//:mux",
        "@go_grpc//:codes",
        "@go_grpc//:grpc",
        "@go_grpc//:metadata",
        "@go_libphonenumber//:libphonenumber",
        "@go_logrus//:logrus",
        "@go_protobuf//:ptypes",
        "@go_protobuf//:ptypes/empty",
        "@go_x_net//:context",
    ],
)

container_image(
    name = "docker",
    base = "@ubuntu//image",
    cmd = "./smsserver",
    files = [
        ":smsserver",
    ],
    visibility = ["//visibility:public"],
)
