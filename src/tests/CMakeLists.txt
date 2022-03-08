set(This src_test)

find_package(fmt CONFIG REQUIRED)
find_package(Catch2 CONFIG REQUIRED)

add_executable(${This}
    # Automation
    src_test.cpp
)

target_link_libraries(${This} PRIVATE src fmt::fmt Catch2::Catch2)

include(CTest)
include(Catch)
catch_discover_tests(${This})

include(CPack)
