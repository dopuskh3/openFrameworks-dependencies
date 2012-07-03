cmake_minimum_required(VERSION 2.8)
include(ExternalProject)

get_filename_component(PROJECT_ROOT ${CMAKE_CURRENT_LIST_FILE} PATH)

ExternalProject_Add(
    fmodex
    URL http://www.fmod.org/index.php/release/version/fmodapi44010linux64.tar.gz
    PREFIX ${PROJECT_ROOT}
    INSTALL_DIR ${OF_DEPS_PREFIX}
    BUILD_IN_SOURCE 1
    CONFIGURE_COMMAND ""
    PATCH_COMMAND sed -i "s#/usr/local#<INSTALL_DIR>#g" <SOURCE_DIR>/Makefile
    BUILD_COMMAND ""
    INSTALL_COMMAND make install
)

ExternalProject_Add_Step(
  fmodex prepareInstall
  WORKING_DIRECTORY <INSTALL_DIR>
  COMMAND mkdir -p <INSTALL_DIR>/include <INSTALL_DIR>/lib
  DEPENDERS install
)


ExternalProject_Add_Step(
  fmodex patchMakeFile1
  COMMAND sed -i "s#include/fmodex#include#g" <SOURCE_DIR>/Makefile
  DEPENDEES patch
)
