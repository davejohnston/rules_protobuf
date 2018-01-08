
load("@org_pubref_rules_protobuf//go:rules.bzl", "go_proto_library")
load("@org_pubref_rules_protobuf//grpc_gateway:rules.bzl", "grpc_gateway_proto_library", "grpc_gateway_swagger_compile")

go_proto_library(
    name = "messages",
    imports = [
        "external/com_github_google_protobuf/src/",
    ],
    inputs = [
        "@com_github_google_protobuf//:well_known_protos",
    ],
    protos = [
        "message.proto",
    ],
    deps = [
        "@com_github_golang_protobuf//ptypes/any:go_default_library",
    ],
    verbose = 2,
)

grpc_gateway_proto_library(
    name = "greeter_grpc_gateway_go_proto",
    protos = [
        "greeter.proto",
    ],
    proto_deps = [
        ":messages",
    ],
    importpath = "github.com/pubref/rules_protobuf/greeter",
    visibility = [
        "//visibility:public",
    ],
    verbose = 2,
)

grpc_gateway_swagger_compile(
    name = "greeter_swagger",
    protos = [
        "greeter.proto",
        "message.proto",
    ],
)
