# Copyright (c) Meta Platforms, Inc. and affiliates.
#
# This source code is licensed under the MIT license found in the
# LICENSE file in the root directory of this source tree.

cmake_minimum_required(VERSION 3.13)
set(CMAKE_VERBOSE_MAKEFILE on)

include(${REACT_COMMON_DIR}/cmake-utils/react-native-flags.cmake)

file(GLOB react_cxx_platform_react_logging_SRC CONFIGURE_DEPENDS *.cpp)
add_library(react_cxx_platform_react_logging OBJECT ${react_cxx_platform_react_logging_SRC})

target_include_directories(react_cxx_platform_react_logging PUBLIC ${REACT_CXX_PLATFORM_DIR})

target_link_libraries(react_cxx_platform_react_logging
      glog
      react_codegen_rncore
      jserrorhandler
      react_bridging
      logger
)
target_compile_reactnative_options(react_cxx_platform_react_logging PRIVATE)
target_compile_options(react_cxx_platform_react_logging PRIVATE -Wpedantic)
