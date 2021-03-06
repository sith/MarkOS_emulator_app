cmake_minimum_required(VERSION 3.9)
project(MarkOS_emulator_app)

find_package(Boost 1.66 REQUIRED COMPONENTS)
include_directories(${Boost_INCLUDE_DIRS})


add_executable(${PROJECT_NAME}
        src/Emulator.cpp
        src/client/CommandManager.cpp
        src/client/CommandManager.h
        src/EmulatorEnvironment.cpp src/EmulatorEnvironment.h)

target_include_directories(${PROJECT_NAME} PUBLIC src)
target_link_libraries(${PROJECT_NAME} LINK_PUBLIC MarkOS_commons)
target_link_libraries(${PROJECT_NAME} LINK_PUBLIC MarkI)
target_link_libraries(${PROJECT_NAME} LINK_PUBLIC MarkOS_emulator_lib)
target_link_libraries(${PROJECT_NAME} LINK_PUBLIC ${Boost_LIBRARIES})


add_executable(${PROJECT_NAME}_client
        src/client/EmulatorClient.cpp
        src/client/CommandManager.cpp
        src/client/CommandManager.h
        )

target_include_directories(${PROJECT_NAME}_client PUBLIC src)
target_link_libraries(${PROJECT_NAME}_client LINK_PUBLIC MarkOS_commons)
target_link_libraries(${PROJECT_NAME}_client LINK_PUBLIC MarkI)
target_link_libraries(${PROJECT_NAME}_client LINK_PUBLIC MarkOS_emulator_lib)
target_link_libraries(${PROJECT_NAME}_client LINK_PUBLIC ${Boost_LIBRARIES})
