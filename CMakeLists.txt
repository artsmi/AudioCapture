cmake_minimum_required(VERSION 2.8)

project(AudioCapture)

add_executable(AudioCapture main.cpp)

find_package(ALSA REQUIRED)
if (NOT ALSA_FOUND)
   message(SEND_ERROR "Failed to find ALSA")
   return()
else()
   message("ALSA's been found!")
   message("ALSA information: ALSA_VERSION_STRING: " ${ALSA_VERSION_STRING})
   message("ALSA information: ALSA_INCLUDE_DIR: " ${ALSA_INCLUDE_DIR})
   include_directories(${ALSA_INCLUDE_DIR})
   target_link_libraries(AudioCapture ${ALSA_LIBRARY})
endif()
