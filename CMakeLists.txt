project(vfs.bluray)

cmake_minimum_required(VERSION 2.6)

list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR})

enable_language(CXX)

find_package(Bluray REQUIRED)
find_package(Kodi REQUIRED)
find_package(p8-platform REQUIRED)
find_package(kodiplatform REQUIRED)

include_directories(${KODI_INCLUDE_DIR}/.. # Hack way with "/..", need bigger Kodi cmake rework to match right include ways
                    ${kodiplatform_INCLUDE_DIRS}
                    ${p8-platform_INCLUDE_DIRS}
                    ${BLURAY_INCLUDE_DIRS})

set(NFS_HEADERS src/BlurayDirectory.h
                src/BlurayFile.h)

set(NFS_SOURCES src/BlurayDirectory.cpp
                src/BlurayFile.cpp)

set(DEPLIBS ${BLURAY_LIBRARIES} ${p8-platform_LIBRARIES} ${kodiplatform_LIBRARIES})

build_addon(vfs.bluray Bluray DEPLIBS)
