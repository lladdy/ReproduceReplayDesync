# Debug Bot source files
file(GLOB SOURCES_REPRODUCEREPLAYDESYNC "*.cpp" "*.h")

# Include directories
include_directories(SYSTEM
    ${PROJECT_SOURCE_DIR}/src/reproducereplaydesync
    ${PROJECT_SOURCE_DIR}/s2client-api/include
    ${PROJECT_BINARY_DIR}/s2client-api/generated
)

# Create the executable.
add_executable(ReproduceReplayDesync ${SOURCES_REPRODUCEREPLAYDESYNC})
target_link_libraries(ReproduceReplayDesync
    sc2api sc2lib sc2utils
)