# Debug Bot source files
file(GLOB SOURCES_DEBUGBOT "*.cpp" "*.h")

# Include directories
include_directories(SYSTEM
    ${PROJECT_SOURCE_DIR}/src/debugbot
    ${PROJECT_SOURCE_DIR}/s2client-api/include
    ${PROJECT_BINARY_DIR}/s2client-api/generated
)

# Create the executable.
add_executable(DebugBot ${SOURCES_DEBUGBOT})
target_link_libraries(DebugBot
    sc2api sc2lib sc2utils
)