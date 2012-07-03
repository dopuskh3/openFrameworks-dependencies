cmake_minimum_required(VERSION 2.8)
include(ExternalProject)


get_filename_component(PROJECT_ROOT ${CMAKE_CURRENT_LIST_FILE} PATH)

ExternalProject_Add(
    tess2
    URL http://libtess2.googlecode.com/files/libtess2-1.0.zip
    PREFIX ${PROJECT_ROOT}
    INSTALL_DIR ${OF_DEPS_PREFIX}
    BUILD_IN_SOURCE 1
    PATCH_COMMAND cp -v ${CMAKE_CURRENT_LIST_DIR}/tess2-CMakeLists.txt <SOURCE_DIR>/CMakeLists.txt
    CMAKE_ARGS -DCMAKE_INSTALL_PREFIX=<INSTALL_DIR>
)








