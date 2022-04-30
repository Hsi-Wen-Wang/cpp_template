cmake_minimum_required(VERSION 3.10)

set(PROJECT_DEPS lib_name) # use the lib_name what you set
include_directories(${CMAKE_SOURCE_DIR}/lib)



# Set file list
file(GLOB PROJECT_SRCS
    ${CMAKE_CURRENT_SOURCE_DIR}/*.c
    ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp
    )

# Add definition
if(CMAKE_BUILD_TYPE MATCHES Debug)
    add_definitions(-DDEBUG)
    #add_definitions(-D_GLIBCXX_DEBUG)
endif()

# Build test
foreach(TEST_FILE_PATH ${PROJECT_SRCS})
    # Get each file name
    get_filename_component(TEST_FILE_NAME ${TEST_FILE_PATH} NAME_WE)

    # Build executable
    add_executable(${TEST_FILE_NAME} ${TEST_FILE_PATH})
    set_target_properties(${TEST_FILE_NAME} PROPERTIES
        OUTPUT_NAME ${TEST_FILE_NAME}
        )
    target_link_libraries(${TEST_FILE_NAME} ${PROJECT_DEPS})

    # Install
    install(TARGETS ${TEST_FILE_NAME}
        RUNTIME DESTINATION "${CMAKE_INSTALL_PREFIX}/bin"
        )
endforeach()


