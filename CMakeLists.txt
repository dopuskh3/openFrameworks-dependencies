cmake_minimum_required(VERSION 2.8)

set(LIBDIR "")
set(OF_DEPS_PREFIX ${CMAKE_CURRENT_LIST_DIR}/of-deps)

add_subdirectory(poco)
add_subdirectory(rtAudio)
add_subdirectory(fmodex)
add_subdirectory(tess2)
add_subdirectory(portaudio)
add_subdirectory(freetype)
add_subdirectory(kiss)
