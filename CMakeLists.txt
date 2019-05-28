
cmake_minimum_required(VERSION 3.0)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/formatter_ex_lib/)

add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/solver_lib/)

add_executable(hello ${CMAKE_CURRENT_SOURCE_DIR}/hello_world_application/hello_world.cpp)

add_executable(solver ${CMAKE_CURRENT_SOURCE_DIR}/solver_application/equation.cpp)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/hello_world_application/
                    ${CMAKE_CURRENT_SOURCE_DIR}/solver_application/
                    ${CMAKE_CURRENT_SOURCE_DIR}/formatter_ex_lib/
                    ${CMAKE_CURRENT_SOURCE_DIR}/solver_lib/
                    ${CMAKE_CURRENT_SOURCE_DIR}/formatter_lib/
)

target_link_libraries(hello PUBLIC formatter_ex formatter)
target_link_libraries(solver PUBLIC formatter_ex formatter solver_lib)
