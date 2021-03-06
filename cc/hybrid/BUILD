licenses(["notice"])  # Apache 2.0

cc_library(
    name = "hybrid_decrypt_set_wrapper",
    srcs = ["hybrid_decrypt_set_wrapper.cc"],
    hdrs = ["hybrid_decrypt_set_wrapper.h"],
    visibility = ["//visibility:private"],
    deps = [
        "//cc:crypto_format",
        "//cc:hybrid_decrypt",
        "//cc:primitive_set",
        "//cc/util:status",
        "//cc/util:statusor",
        "//proto:tink_cc_proto",
        "@com_google_protobuf//:protobuf_lite",
    ],
)

cc_library(
    name = "hybrid_encrypt_set_wrapper",
    srcs = ["hybrid_encrypt_set_wrapper.cc"],
    hdrs = ["hybrid_encrypt_set_wrapper.h"],
    visibility = ["//visibility:private"],
    deps = [
        "//cc:crypto_format",
        "//cc:hybrid_encrypt",
        "//cc:primitive_set",
        "//cc/util:status",
        "//cc/util:statusor",
        "//proto:tink_cc_proto",
        "@com_google_protobuf//:protobuf_lite",
    ],
)

cc_library(
    name = "hybrid_decrypt_factory",
    srcs = ["hybrid_decrypt_factory.cc"],
    hdrs = ["hybrid_decrypt_factory.h"],
    visibility = ["//visibility:public"],
    deps = [
        ":ecies_aead_hkdf_private_key_manager",
        ":hybrid_decrypt_set_wrapper",
        "//cc:hybrid_decrypt",
        "//cc:key_manager",
        "//cc:keyset_handle",
        "//cc:primitive_set",
        "//cc:registry",
        "//cc/util:status",
        "//cc/util:statusor",
    ],
)

cc_library(
    name = "hybrid_encrypt_factory",
    srcs = ["hybrid_encrypt_factory.cc"],
    hdrs = ["hybrid_encrypt_factory.h"],
    visibility = ["//visibility:public"],
    deps = [
        ":ecies_aead_hkdf_public_key_manager",
        ":hybrid_encrypt_set_wrapper",
        "//cc:hybrid_encrypt",
        "//cc:key_manager",
        "//cc:keyset_handle",
        "//cc:primitive_set",
        "//cc:registry",
        "//cc/util:status",
        "//cc/util:statusor",
    ],
)

cc_library(
    name = "ecies_aead_hkdf_hybrid_decrypt",
    srcs = ["ecies_aead_hkdf_hybrid_decrypt.cc"],
    hdrs = ["ecies_aead_hkdf_hybrid_decrypt.h"],
    visibility = ["//visibility:private"],
    deps = [
        "//cc:hybrid_decrypt",
        "//cc/util:status",
        "//cc/util:statusor",
        "//proto:common_cc_proto",
        "//proto:ecies_aead_hkdf_cc_proto",
        "//proto:tink_cc_proto",
    ],
)

cc_library(
    name = "ecies_aead_hkdf_hybrid_encrypt",
    srcs = ["ecies_aead_hkdf_hybrid_encrypt.cc"],
    hdrs = ["ecies_aead_hkdf_hybrid_encrypt.h"],
    visibility = ["//visibility:private"],
    deps = [
        "//cc:hybrid_encrypt",
        "//cc/util:status",
        "//cc/util:statusor",
        "//proto:common_cc_proto",
        "//proto:ecies_aead_hkdf_cc_proto",
        "//proto:tink_cc_proto",
    ],
)

cc_library(
    name = "ecies_aead_hkdf_private_key_manager",
    srcs = ["ecies_aead_hkdf_private_key_manager.cc"],
    hdrs = ["ecies_aead_hkdf_private_key_manager.h"],
    visibility = ["//visibility:private"],
    deps = [
        ":ecies_aead_hkdf_hybrid_decrypt",
        "//cc:hybrid_decrypt",
        "//cc:key_manager",
        "//cc:registry",
        "//cc/util:status",
        "//cc/util:statusor",
        "//proto:common_cc_proto",
        "//proto:ecies_aead_hkdf_cc_proto",
        "//proto:tink_cc_proto",
    ],
)

cc_library(
    name = "ecies_aead_hkdf_public_key_manager",
    srcs = ["ecies_aead_hkdf_public_key_manager.cc"],
    hdrs = ["ecies_aead_hkdf_public_key_manager.h"],
    visibility = ["//visibility:private"],
    deps = [
        ":ecies_aead_hkdf_hybrid_encrypt",
        "//cc:hybrid_encrypt",
        "//cc:key_manager",
        "//cc:registry",
        "//cc/util:status",
        "//cc/util:statusor",
        "//proto:common_cc_proto",
        "//proto:ecies_aead_hkdf_cc_proto",
        "//proto:tink_cc_proto",
    ],
)

# tests

cc_test(
    name = "hybrid_decrypt_set_wrapper_test",
    size = "small",
    srcs = ["hybrid_decrypt_set_wrapper_test.cc"],
    copts = ["-Iexternal/gtest/include"],
    deps = [
        ":hybrid_decrypt_set_wrapper",
        "//cc:hybrid_decrypt",
        "//cc:primitive_set",
        "//cc/util:status",
        "//cc/util:test_util",
        "//proto:tink_cc_proto",
        "@gtest//:gtest",
    ],
)

cc_test(
    name = "hybrid_encrypt_set_wrapper_test",
    size = "small",
    srcs = ["hybrid_encrypt_set_wrapper_test.cc"],
    copts = ["-Iexternal/gtest/include"],
    deps = [
        ":hybrid_encrypt_set_wrapper",
        "//cc:hybrid_encrypt",
        "//cc:primitive_set",
        "//cc/util:status",
        "//cc/util:test_util",
        "//proto:tink_cc_proto",
        "@gtest//:gtest",
    ],
)

cc_test(
    name = "hybrid_decrypt_factory_test",
    size = "small",
    srcs = ["hybrid_decrypt_factory_test.cc"],
    copts = ["-Iexternal/gtest/include"],
    deps = [
        ":hybrid_decrypt_factory",
        "//cc:hybrid_decrypt",
        "//cc:keyset_handle",
        "//cc/util:status",
        "//cc/util:test_util",
        "//proto:ecies_aead_hkdf_cc_proto",
        "//proto:tink_cc_proto",
        "@gtest//:gtest",
    ],
)

cc_test(
    name = "hybrid_encrypt_factory_test",
    size = "small",
    srcs = ["hybrid_encrypt_factory_test.cc"],
    copts = ["-Iexternal/gtest/include"],
    deps = [
        ":hybrid_encrypt_factory",
        "//cc:hybrid_encrypt",
        "//cc:keyset_handle",
        "//cc/util:status",
        "//cc/util:test_util",
        "//proto:ecies_aead_hkdf_cc_proto",
        "//proto:tink_cc_proto",
        "@gtest//:gtest",
    ],
)

cc_test(
    name = "ecies_aead_hkdf_hybrid_decrypt_test",
    size = "small",
    srcs = ["ecies_aead_hkdf_hybrid_decrypt_test.cc"],
    copts = ["-Iexternal/gtest/include"],
    deps = [
        ":ecies_aead_hkdf_hybrid_decrypt",
        "//cc:hybrid_decrypt",
        "//cc/util:status",
        "//cc/util:statusor",
        "//proto:common_cc_proto",
        "//proto:ecies_aead_hkdf_cc_proto",
        "@gtest//:gtest",
    ],
)

cc_test(
    name = "ecies_aead_hkdf_hybrid_encrypt_test",
    size = "small",
    srcs = ["ecies_aead_hkdf_hybrid_encrypt_test.cc"],
    copts = ["-Iexternal/gtest/include"],
    deps = [
        ":ecies_aead_hkdf_hybrid_encrypt",
        "//cc:hybrid_encrypt",
        "//cc/util:status",
        "//cc/util:statusor",
        "//proto:common_cc_proto",
        "//proto:ecies_aead_hkdf_cc_proto",
        "@gtest//:gtest",
    ],
)

cc_test(
    name = "ecies_aead_hkdf_private_key_manager_test",
    size = "small",
    srcs = ["ecies_aead_hkdf_private_key_manager_test.cc"],
    copts = ["-Iexternal/gtest/include"],
    deps = [
        ":ecies_aead_hkdf_private_key_manager",
        "//cc:hybrid_decrypt",
        "//cc/util:status",
        "//cc/util:statusor",
        "//proto:aes_eax_cc_proto",
        "//proto:common_cc_proto",
        "//proto:ecies_aead_hkdf_cc_proto",
        "//proto:tink_cc_proto",
        "@gtest//:gtest",
    ],
)

cc_test(
    name = "ecies_aead_hkdf_public_key_manager_test",
    size = "small",
    srcs = ["ecies_aead_hkdf_public_key_manager_test.cc"],
    copts = ["-Iexternal/gtest/include"],
    deps = [
        ":ecies_aead_hkdf_public_key_manager",
        "//cc:hybrid_encrypt",
        "//cc/util:status",
        "//cc/util:statusor",
        "//proto:aes_eax_cc_proto",
        "//proto:common_cc_proto",
        "//proto:ecies_aead_hkdf_cc_proto",
        "//proto:tink_cc_proto",
        "@gtest//:gtest",
    ],
)
