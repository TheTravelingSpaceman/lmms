INCLUDE(BuildPlugin)

# Enable C++11 for CXXFLAGS only
REMOVE_DEFINITIONS(-std=c++0x)
SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++0x")

# Avoid unused warnings for mididata.h
SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wno-unused-variable")

INCLUDE_DIRECTORIES(adplug/src)

BUILD_PLUGIN(opulenz
	OpulenZ.cpp
	OpulenZ.h
	adplug/src/opl.h
	adplug/src/fmopl.c
	adplug/src/fmopl.h
	adplug/src/temuopl.cpp
	adplug/src/temuopl.h
	MOCFILES OpulenZ.h
	EMBEDDED_RESOURCES "${CMAKE_CURRENT_SOURCE_DIR}/*.png"
)
