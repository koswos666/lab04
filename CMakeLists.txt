cmake_minimum_required(VERSION 3.10)
project(lab04)

# Настройка стандарта C++
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Библиотеки
add_library(formatter_lib STATIC formatter_lib/formatter.cpp)
target_include_directories(formatter_lib PUBLIC formatter_lib)

add_library(formatter_ex_lib STATIC formatter_ex_lib/formatter_ex.cpp)
target_include_directories(formatter_ex_lib PUBLIC formatter_ex_lib formatter_lib)

add_library(solver_lib STATIC solver_lib/solver.cpp)
target_include_directories(solver_lib PUBLIC solver_lib)

# Исполняемые файлы
add_executable(hello_world_app hello_world_application/hello_world.cpp)
target_link_libraries(hello_world_app formatter_lib formatter_ex_lib)

add_executable(solver_app solver_application/equation.cpp)
target_link_libraries(solver_app solver_lib formatter_lib formatter_ex_lib)
