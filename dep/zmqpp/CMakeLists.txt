# Copyright (C) 2008-2018 TrinityCore <https://www.trinitycore.org/>
#
# This file is free software; as a special exception the author gives
# unlimited permission to copy and/or distribute it, with or without
# modifications, as long as this notice is preserved.
#
# This program is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY, to the extent permitted by law; without even the
# implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

file(GLOB_RECURSE sources_zmqpp zmqpp/*.cpp zmqpp/*.hpp zmqpp/*.h)

include_directories(${ZMQ_INCLUDE_DIR})

add_library(zmqpp STATIC
  ${sources_zmqpp}
)

target_link_libraries(zmqpp
  PUBLIC
    zmq)

target_include_directories(zmqpp
  PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR})

set_target_properties(zmqpp
  PROPERTIES
    FOLDER
      "dep")

target_compile_definitions(zmqpp
  PRIVATE
    -DBUILD_VERSION_MAJOR=3
    -DBUILD_VERSION_MINOR=2
    -DBUILD_VERSION_REVISION=0
    -DBUILD_VERSION="3.2.0")
