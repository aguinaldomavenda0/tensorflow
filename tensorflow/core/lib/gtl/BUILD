load("//tensorflow:tensorflow.bzl", "filegroup")
load(
    "//tensorflow/core/platform:rules_cc.bzl",
    "cc_library",
)

package(
    default_visibility = [
        # tensorflow/core:lib effectively exposes all targets under tensorflow/core/lib/**
        "//tensorflow/core:__pkg__",
        # tensorflow/core/lib/random uses on gtl:array_slice
        "//tensorflow/core/lib/random:__pkg__",
        # tensorflow/core/lib/strings:proto_serialization uses on gtl:inlined_vector
        "//tensorflow/core/lib/strings:__pkg__",
        # tensorflow/core/lib/histogram uses array_slice
        "//tensorflow/core/lib/histogram:__pkg__",
        # tensorflow/core/framework uses array_slice, map_util, and flatmap
        "//tensorflow/core/framework:__pkg__",
        # tensorflow/core/util uses array_slice, inlined_vector
        "//tensorflow/core/util:__pkg__",
        # tensorflow/core/tfrt/utils uses array_slice, inlined_vector
        "//tensorflow/core/tfrt/utils:__pkg__",
        # tensorflow/examples/custom_ops_doc/simple_hash_table uses map_util
        "//tensorflow/examples/custom_ops_doc/simple_hash_table:__pkg__",
        "//tensorflow/compiler/xla/stream_executor:__subpackages__",
        # TODO(aminim): remove when array_slice migrates to TSL
        "//tensorflow/tsl:__subpackages__",
    ],
    licenses = ["notice"],
)

# Todo(bmzhao): Remaining targets to add to this BUILD file are: all tests.

cc_library(
    name = "array_slice",
    hdrs = ["array_slice.h"],
    deps = [
        "//tensorflow/core/lib/gtl:inlined_vector",
        "@com_google_absl//absl/types:span",
    ],
)

cc_library(
    name = "cleanup",
    hdrs = ["cleanup.h"],
    deps = ["//tensorflow/core/platform:macros"],
)

cc_library(
    name = "compactptrset",
    hdrs = ["compactptrset.h"],
    deps = [
        "//tensorflow/tsl/lib/gtl:compactptrset",
    ],
)

cc_library(
    name = "edit_distance",
    hdrs = ["edit_distance.h"],
    deps = [
        "//tensorflow/core/lib/gtl:array_slice",
        "//tensorflow/core/lib/gtl:inlined_vector",
    ],
)

cc_library(
    name = "flatmap",
    hdrs = ["flatmap.h"],
    visibility = [
        "//tensorflow/c/eager:__pkg__",
        "//tensorflow/core:__pkg__",
        "//tensorflow/core/framework:__pkg__",
        "//tensorflow/core/lib/histogram:__pkg__",
        "//tensorflow/core/lib/random:__pkg__",
        "//tensorflow/core/lib/strings:__pkg__",
    ],
    deps = [
        "//tensorflow/core/lib/gtl:flatrep",
        "//tensorflow/core/lib/hash",
        "//tensorflow/core/platform:logging",
        "//tensorflow/core/platform:types",
        "//tensorflow/tsl/lib/gtl:flatmap",
    ],
)

cc_library(
    name = "flatrep",
    hdrs = ["flatrep.h"],
    deps = [
        "//tensorflow/tsl/lib/gtl:flatrep",
    ],
)

cc_library(
    name = "flatset",
    hdrs = ["flatset.h"],
    deps = [
        "//tensorflow/tsl/lib/gtl:flatset",
    ],
)

cc_library(
    name = "inlined_vector",
    hdrs = ["inlined_vector.h"],
    deps = [
        "//tensorflow/core/platform:macros",
        "//tensorflow/core/platform:types",
        "//tensorflow/tsl/lib/gtl:inlined_vector",
        "@com_google_absl//absl/container:inlined_vector",
    ],
)

cc_library(
    name = "int_type",
    hdrs = ["int_type.h"],
    deps = [
        "//tensorflow/tsl/lib/gtl:int_type",
    ],
)

cc_library(
    name = "iterator_range",
    hdrs = ["iterator_range.h"],
    deps = [
        "//tensorflow/tsl/lib/gtl:iterator_range",
    ],
)

cc_library(
    name = "manual_constructor",
    hdrs = ["manual_constructor.h"],
    deps = [
        "//tensorflow/core/platform:macros",
        "//tensorflow/core/platform:platform_port",
    ],
)

cc_library(
    name = "map_util",
    srcs = [
        "map_util.h",
        "//tensorflow/core/lib/gtl/subtle:map_traits",
    ],
    hdrs = ["map_util.h"],
    deps = [
        "//tensorflow/core/platform:hash",  # TODO(dduneavy) examples/custom_ops_doc transitively depends on this
        "//tensorflow/tsl/lib/gtl:map_util",
    ],
)

cc_library(
    name = "optional",
    hdrs = ["optional.h"],
    deps = ["@com_google_absl//absl/types:optional"],
)

cc_library(
    name = "priority_queue_util",
    hdrs = ["priority_queue_util.h"],
)

cc_library(
    name = "top_n",
    hdrs = ["top_n.h"],
    deps = ["//tensorflow/core/platform:logging"],
)

filegroup(
    name = "legacy_lib_gtl_headers",
    srcs = [
        "array_slice.h",
        "cleanup.h",
        "compactptrset.h",
        "edit_distance.h",
        "flatmap.h",
        "flatset.h",
        "inlined_vector.h",
        "iterator_range.h",
        "optional.h",
        "priority_queue_util.h",
        "//tensorflow/tsl/lib/gtl:legacy_lib_gtl_headers",
    ],
    visibility = ["//tensorflow/core:__pkg__"],
)

filegroup(
    name = "legacy_lib_internal_public_gtl_headers",
    srcs = [
        "edit_distance.h",
        "int_type.h",
        "manual_constructor.h",
        "map_util.h",
        "top_n.h",
        "//tensorflow/tsl/lib/gtl:legacy_lib_internal_public_gtl_headers",
    ],
    visibility = ["//tensorflow/core:__pkg__"],
)

filegroup(
    name = "legacy_lib_test_internal_headers",
    srcs = [
        "manual_constructor.h",
        "//tensorflow/tsl/lib/gtl:legacy_lib_test_internal_headers",
    ],
    visibility = ["//tensorflow/core:__pkg__"],
)

filegroup(
    name = "legacy_android_gif_internal_headers",
    srcs = [
        "cleanup.h",
        "//tensorflow/tsl/lib/gtl:legacy_android_gif_internal_headers",
    ],
    visibility = [
        "//tensorflow/core:__pkg__",
        "//tensorflow/core/lib/gif:__pkg__",
    ],
)

# Export source files needed for mobile builds, which do not use granular targets.
filegroup(
    name = "mobile_srcs_no_runtime",
    srcs = [
        "array_slice.h",
        "flatmap.h",
        "flatrep.h",
        "inlined_vector.h",
        "top_n.h",
        "//tensorflow/tsl/lib/gtl:mobile_srcs_no_runtime",
    ],
    visibility = ["//tensorflow/core:__pkg__"],
)

filegroup(
    name = "mobile_srcs_only_runtime",
    srcs = [
        "cleanup.h",
        "edit_distance.h",
        "flatset.h",
        "int_type.h",
        "iterator_range.h",
        "manual_constructor.h",
        "map_util.h",
        "optional.h",
        "priority_queue_util.h",
        "//tensorflow/core/lib/gtl/subtle:map_traits",
        "//tensorflow/tsl/lib/gtl:mobile_srcs_only_runtime",
    ],
    visibility = ["//tensorflow/core:__pkg__"],
)

filegroup(
    name = "legacy_lib_gtl_all_headers",
    srcs = [
        "array_slice.h",
        "cleanup.h",
        "compactptrset.h",
        "edit_distance.h",
        "flatmap.h",
        "flatrep.h",
        "flatset.h",
        "inlined_vector.h",
        "int_type.h",
        "iterator_range.h",
        "manual_constructor.h",
        "map_util.h",
        "optional.h",
        "priority_queue_util.h",
        "top_n.h",
        "//tensorflow/core/lib/gtl/subtle:map_traits",
        "//tensorflow/tsl/lib/gtl:legacy_lib_gtl_all_headers",
    ],
    visibility = ["//tensorflow/core:__pkg__"],
)

filegroup(
    name = "legacy_lib_gtl_tests",
    srcs = [
        "cleanup_test.cc",
        "edit_distance_test.cc",
        "manual_constructor_test.cc",
        "top_n_test.cc",
    ],
    visibility = ["//tensorflow/core:__pkg__"],
)
