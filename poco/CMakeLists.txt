cmake_minimum_required(VERSION 2.8)
include(ExternalProject)

get_filename_component(PROJECT_ROOT ${CMAKE_CURRENT_LIST_FILE} PATH)

ExternalProject_Add(
    poco
    URL http://sourceforge.net/projects/poco/files/sources/poco-1.4.3/poco-1.4.3p1.tar.gz/download#
    INSTALL_DIR ${OF_DEPS_PREFIX}
    PREFIX ${PROJECT_ROOT}/testcomp
    CONFIGURE_COMMAND ./configure --shared --prefix=<INSTALL_DIR>
    BUILD_IN_SOURCE 1
    BUILD_COMMAND make -j
)

