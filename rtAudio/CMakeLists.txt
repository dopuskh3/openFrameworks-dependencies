cmake_minimum_required(VERSION 2.8)
include(ExternalProject)

get_filename_component(PROJECT_ROOT ${CMAKE_CURRENT_LIST_FILE} PATH)

ExternalProject_Add(
    rtAudio
    URL http://www.music.mcgill.ca/~gary/rtaudio/release/rtaudio-4.0.11.tar.gz
    PREFIX ${PROJECT_ROOT}
    INSTALL_DIR ${OF_DEPS_PREFIX}
    CONFIGURE_COMMAND ./configure
    BUILD_IN_SOURCE 1
    BUILD_COMMAND make
)

ExternalProject_Add_Step(
  rtAudio preparePrefix
  WORKING_DIRECTORY <INSTALL_DIR>
  COMMAND mkdir -p lib/${LIBDIR} include
  DEPENDEES build
  DEPENDERS install
)

ExternalProject_Add_Step(
  rtAudio install1
  WORKING_DIRECTORY <SOURCE_DIR>
  COMMAND cp librtaudio.a <INSTALL_DIR>/lib/${LIBDIR}/libRtAudio.a
  DEPENDEES install
)

ExternalProject_Add_Step(
  rtAudio install2
  WORKING_DIRECTORY <SOURCE_DIR>
  COMMAND cp RtAudio.h RtError.h <INSTALL_DIR>/include
  DEPENDEES install1
)







