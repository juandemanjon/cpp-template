set(This src)

add_library(${This}
    code.cpp
)

# https://retifrav.github.io/blog/2021/03/08/cmake-cpp-library/
target_include_directories(${This}
    PRIVATE
        # where the library itself will look for its internal headers
        ${CMAKE_CURRENT_SOURCE_DIR}/src
    PUBLIC
        # where top-level project will look for the library's public headers
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
        # where external projects will look for the library's public headers
        $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>
)

target_link_libraries(${This}
    PUBLIC
)

add_subdirectory("tests")