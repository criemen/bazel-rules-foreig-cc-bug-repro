load("@rules_foreign_cc//foreign_cc:defs.bzl", "cmake_variant", "cmake")

filegroup(
    name = "all_srcs",
    srcs = glob(["**"]),
    visibility = ["//visibility:private"],
)

cmake_variant(
    name = "mimalloc_variant",
    lib_source = ":all_srcs",

    # On POSIX, we want to statically link against `mimalloc.o`, so make sure we emit it.
    # Probably not what a "binary" is supposed to be, but there doesn't seem to be a good way
    # to get a single object file (rather than an archive/library) from a cmake rule.
    out_bin_dir = "",
    out_binaries = ["lib/mimalloc-2.1/mimalloc.o"],
    toolchain = "@rules_foreign_cc//toolchains:preinstalled_make_toolchain",
    visibility = ["//visibility:public"],
)

cmake(
    name = "mimalloc_single",
    lib_source = ":all_srcs",

    # On POSIX, we want to statically link against `mimalloc.o`, so make sure we emit it.
    # Probably not what a "binary" is supposed to be, but there doesn't seem to be a good way
    # to get a single object file (rather than an archive/library) from a cmake rule.
    out_bin_dir = "",
    out_binaries = ["lib/mimalloc-2.1/mimalloc.o"],
    visibility = ["//visibility:public"],
)

filegroup(
    name = "mimalloc.o",
    srcs = [":mimalloc"],
    output_group = "mimalloc.o",
    visibility = ["//visibility:public"],
)
