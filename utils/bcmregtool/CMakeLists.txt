project(bcmregtool)


add_subdirectory(apeloader)

add_definitions(-Wall -Werror)
set(SOURCES
    main.cpp
)

simulator_add_executable(${PROJECT_NAME} ${SOURCES})
target_link_libraries(${PROJECT_NAME} PRIVATE NVRam VPD MII APE apeloader-binary NCSI Network)
target_link_libraries(${PROJECT_NAME} PRIVATE simulator OptParse elfio)

format_target_sources(${PROJECT_NAME})

INSTALL(TARGETS ${PROJECT_NAME} DESTINATION bin)

ADD_ENDIANNESS_DEFINES(${PROJECT_NAME})
