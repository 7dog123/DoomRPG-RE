file(GLOB_RECURSE HEADER_FILES
	"*.hpp"
	"*.h")

file(GLOB_RECURSE SOURCE_FILES
	"*.cpp"
	"*.c")

file(GLOB_RECURSE RESOURCES_FILES
	"*.rc"
	"*.ico")

source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR} PREFIX "Header Files" FILES ${HEADER_FILES})
source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR} PREFIX "Source Files" FILES ${SOURCE_FILES})
source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR} PREFIX "Resources Files" FILES ${RESOURCES_FILES})

add_executable(${PROJECT_NAME} ${HEADER_FILES} ${SOURCE_FILES} ${RESOURCES_FILES})

if(PS2)
target_link_libraries(${PROJECT_NAME} SDL2::SDL2 SDL2::mixer ZLIB::ZLIB -lfluidsynth -lgskit -ldmakit 
	-lcdvd -lm -lpoweroff -ldebug -lpatches -lstdc++ -lmodplug -lps2_drivers -lmouse -lkbd)
else()
target_link_libraries(${PROJECT_NAME} SDL2::SDL2 SDL2::mixer ZLIB::ZLIB FluidSynth::libfluidsynth)
endif()
