

add_library(core-objects OBJECT main.cpp)

target_include_directories(core-objects
  PUBLIC 
    $<INSTALL_INTERFACE:include>
    $<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}/include> # project public includes
  PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR} # private includes go here
)

set_property(TARGET core-objects
  PROPERTY POSITION_INDEPENDENT_CODE ON
)


add_library(core-static STATIC)

target_link_libraries(core-static PUBLIC core-objects)

add_library(core SHARED)

target_link_libraries(core PUBLIC core-objects)

install(TARGETS core
    EXPORT rock-targets
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}/rock COMPONENT libs
)
