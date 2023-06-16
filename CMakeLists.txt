project (matplotlib-cpp)
cmake_minimum_required(VERSION 3.15)
set(CMAKE_CXX_STANDARD 20)

find_package(Python3 COMPONENTS Development NumPy)

add_library(${PROJECT_NAME} INTERFACE)
target_include_directories(${PROJECT_NAME} INTERFACE include ${Python3_INCLUDE_DIRS} ${Python3_NumPy_INCLUDE_DIRS})
target_link_libraries(${PROJECT_NAME} INTERFACE Python3::Python Python3::NumPy)

if(MSVC)
    target_compile_definitions(${PROJECT_NAME} INTERFACE _USE_MATH_DEFINES=1)
endif()
