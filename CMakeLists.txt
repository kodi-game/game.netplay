cmake_minimum_required(VERSION 3.1)
project(game.netplay)

list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR})

# ------------------------------------------------------------------------------
# Add-on Dependencies
# ------------------------------------------------------------------------------

find_package(Kodi REQUIRED)
find_package(kodiplatform REQUIRED)
find_package(p8-platform REQUIRED)

include_directories(${KODI_INCLUDE_DIR}/.. # Hack way with "/..", need bigger Kodi cmake rework to match right include ways (becomes done in future)
                    ${kodiplatform_INCLUDE_DIRS}
                    ${p8-platform_INCLUDE_DIRS}
                    ${PROJECT_SOURCE_DIR}/src)

list(APPEND DEPLIBS ${kodiplatform_LIBRARIES} ${p8-platform_LIBRARIES})

set(NETPLAY_SOURCES src/addon.cpp
)

set(NETPLAY_HEADERS src/addon.h
)

# ------------------------------------------------------------------------------
# Add-on Build Command
# ------------------------------------------------------------------------------

build_addon(${PROJECT_NAME} NETPLAY DEPLIBS)
