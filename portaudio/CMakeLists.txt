cmake_minimum_required(VERSION 2.8)
include(ExternalProject)

get_filename_component(PROJECT_ROOT ${CMAKE_CURRENT_LIST_FILE} PATH)

ExternalProject_Add(
    portaudio
    URL http://www.portaudio.com/archives/pa_stable_v19_20111121.tgz
    PREFIX ${PROJECT_ROOT}
    INSTALL_DIR ${OF_DEPS_PREFIX}
    BUILD_IN_SOURCE 1
    CONFIGURE_COMMAND ./configure --prefix=<INSTALL_DIR>
    BUILD_COMMAND make
    INSTALL_COMMAND make install
)

