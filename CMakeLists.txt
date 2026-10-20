cmake_minimum_required(VERSION 3.20)
project(NinjaGaidenIIRecomp C CXX)

# NESRecomp cycle backend integration. See runner/cyc/PROJECTS.md.
set(NESRECOMP_ROOT "${CMAKE_CURRENT_LIST_DIR}/../nesrecomp")
set(NESRECOMP_BACKEND "cycle" CACHE STRING "CPU backend: cycle or legacy")
set_property(CACHE NESRECOMP_BACKEND PROPERTY STRINGS cycle legacy)

if(NESRECOMP_BACKEND STREQUAL "cycle")
    include("${NESRECOMP_ROOT}/runner/cyc/project.cmake")
    nesrecomp_add_cycle_game(NinjaGaidenIIRecomp
        ROM "${CMAKE_CURRENT_SOURCE_DIR}/../game/Ninja Gaiden II - The Dark Sword of Chaos (USA).nes"
        GAME_CONFIG "${CMAKE_CURRENT_SOURCE_DIR}/game.toml"
        REGION NTSC
    )
    return()
endif()

if(NOT NESRECOMP_BACKEND STREQUAL "legacy")
    message(FATAL_ERROR "Unknown NESRECOMP_BACKEND: ${NESRECOMP_BACKEND}")
endif()