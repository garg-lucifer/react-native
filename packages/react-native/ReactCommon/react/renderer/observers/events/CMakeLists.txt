# Copyright (c) Meta Platforms, Inc. and affiliates.
#
# This source code is licensed under the MIT license found in the
# LICENSE file in the root directory of this source tree.

cmake_minimum_required(VERSION 3.13)
set(CMAKE_VERBOSE_MAKEFILE on)

include(${REACT_COMMON_DIR}/cmake-utils/react-native-flags.cmake)

file(GLOB react_renderer_observers_events_SRC CONFIGURE_DEPENDS *.cpp)
add_library(react_renderer_observers_events OBJECT ${react_renderer_observers_events_SRC})

target_include_directories(react_renderer_observers_events PUBLIC ${REACT_COMMON_DIR})
target_link_libraries(react_renderer_observers_events
        react_debug
        react_performance_timeline
        react_timing
        react_renderer_core
        react_renderer_runtimescheduler
        react_featureflags
        react_renderer_uimanager
        react_utils
        rrc_view)
target_compile_reactnative_options(react_renderer_observers_events PRIVATE)
target_compile_options(react_renderer_observers_events PRIVATE -Wpedantic)
