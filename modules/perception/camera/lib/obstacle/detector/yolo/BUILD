load("//tools:cpplint.bzl", "cpplint")
load("//tools:cuda_library.bzl", "cuda_library")

package(default_visibility = ["//visibility:public"])


cuda_library(
    name = "region_output_cuda",
    srcs = [
        "region_output.cu",
    ],
    hdrs = [
        "region_output.h",
    ],
    deps = [
        ":object_maintainer",
        "//modules/perception/base:base",
        "//modules/perception/camera/common:common",
        "//modules/perception/camera/lib/obstacle/detector/yolo/proto:yolo_proto",
        "@cuda",
    ],
)


cc_library(
    name = "region_output",
    srcs = [
        "region_output.cc",
        ":region_output_cuda",
    ],
    hdrs = [ 
        "region_output.h",
    ],
    deps = [
        "//cyber",
        "//modules/perception/base:base",
        "//modules/perception/camera/common:common",
        "//modules/perception/camera/lib/obstacle/detector/yolo/proto:yolo_proto",
    ],
)


cc_library(
    name = "yolo_obstacle_detector",
    srcs = [
        "yolo_obstacle_detector.cc",

    ],
    hdrs = [ 
        "yolo_obstacle_detector.h",
    ],
    deps = [
        ":region_output",
        "//modules/common/util:file_util",
        "//modules/perception/base:base",
        "//modules/perception/camera/common:common",
        "//modules/perception/camera/lib/feature_extractor/tfe:external_feature_extractor",
        "//modules/perception/camera/lib/feature_extractor/tfe:project_feature",
        "//modules/perception/camera/lib/feature_extractor/tfe:tracking_feat_extractor",
        "//modules/perception/camera/lib/interface:interface",
        "//modules/perception/camera/lib/obstacle/detector/yolo/proto:yolo_proto",
        "//modules/perception/inference:inference_factory_lib",
        "//modules/perception/inference:inference_lib",
        "//modules/perception/inference/utils:inference_resize_lib",
        "//modules/perception/inference/utils:inference_util_lib",
        "//modules/perception/lib/utils:utils",
    ],
)


cc_library(
    name = "object_maintainer",
    hdrs = [ 
        "object_maintainer.h",
    ],
    deps = [
        "//modules/perception/base:base",
    ],
)

cpplint()
