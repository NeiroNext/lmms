IF(LMMS_SUPPORT_VST)
   # Enable C++11
   ADD_DEFINITIONS(-std=c++0x)

   INCLUDE(BuildPlugin)
   INCLUDE_DIRECTORIES("${CMAKE_CURRENT_SOURCE_DIR}/../vst_base")
   LINK_DIRECTORIES("${CMAKE_CURRENT_BINARY_DIR}/../vst_base")
   LINK_LIBRARIES(vstbase)
   IF(LMMS_BUILD_WIN32)
	BUILD_PLUGIN(vestige vestige.cpp vestige.h MOCFILES vestige.h EMBEDDED_RESOURCES "${CMAKE_CURRENT_SOURCE_DIR}/*.png")
   ELSE()
	BUILD_PLUGIN(vestige vestige.cpp vestige.h MOCFILES vestige.h EMBEDDED_RESOURCES "${CMAKE_CURRENT_SOURCE_DIR}/*.png" LINK SHARED)
   ENDIF()
ENDIF(LMMS_SUPPORT_VST)

