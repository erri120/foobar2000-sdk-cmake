cmake_minimum_required(VERSION 3.21)

project(
    myproject
    LANGUAGES CXX C
)

add_subdirectory(pfc)

# Windows Template Library (WTL) is required by libPPUI
add_subdirectory(wtl)
add_subdirectory(libPPUI)

add_subdirectory(foobar2000)