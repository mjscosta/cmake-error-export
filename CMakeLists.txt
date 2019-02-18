cmake_minimum_required(VERSION 3.12)

project(rock VERSION 0.0.0 LANGUAGES C CXX)

include(GNUInstallDirs)

add_subdirectory(src)

install(EXPORT rock-targets
  FILE
    rockTargets.cmake
  NAMESPACE
    rock::
  DESTINATION
    ${CMAKE_INSTALL_LIBDIR}/cmake/rock
)

