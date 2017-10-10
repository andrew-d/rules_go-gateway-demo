workspace(name = "com_test")

git_repository(
    name = "io_bazel_rules_go",
    remote = "git://github.com/bazelbuild/rules_go.git",
    commit = "e254d73bf1181101ed82791fa5d204c4c5b1b105",
    #remote = "git://github.com/andrew-d/rules_go.git",          # ** uncomment to fix build
    #commit = "e207bc78c3b57449518a57082c754c39157d4755",        # ** uncomment to fix build
)

git_repository(
    name = "org_pubref_rules_protobuf",
    remote = "git://github.com/pubref/rules_protobuf.git",
    commit = "ff3b7e7963daa7cb3b42f8936bc11eda4b960926",
)

load("@io_bazel_rules_go//go:def.bzl", "go_repository")
go_repository(
    name = "org_golang_google_grpc",
    importpath = "google.golang.org/grpc",
    tag = "v1.6.0",
    #build_file_proto_mode = "disable",                          # ** uncomment to fix build
)
go_repository(
    name = "com_github_grpc_ecosystem_grpc_gateway",
    importpath = "github.com/grpc-ecosystem/grpc-gateway",
    commit = "f2862b476edcef83412c7af8687c9cd8e4097c0f",
    #build_file_proto_mode = "disable",                          # ** uncomment to fix build
)

# Load grpc-gateway first, so the Go tooling doesn't conflict
load("@org_pubref_rules_protobuf//go:rules.bzl", "go_proto_repositories")
go_proto_repositories()

load("@org_pubref_rules_protobuf//grpc_gateway:rules.bzl", "grpc_gateway_proto_repositories")
grpc_gateway_proto_repositories()

# Load this after all the grpc-gateway deps, above
load("@io_bazel_rules_go//go:def.bzl", "go_rules_dependencies", "go_register_toolchains")
go_rules_dependencies()
go_register_toolchains()

load("@io_bazel_rules_go//proto:def.bzl", "proto_register_toolchains")
proto_register_toolchains()
