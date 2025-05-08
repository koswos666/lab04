cmake_minimum_required(VERSION 3.4)
project(lab04)

# Настройка стандарта C++
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Библиотека formatter
add_library(formatter STATIC formatter_lib/formatter.cpp)
target_include_directories(formatter PUBLIC formatter_lib)

# Библиотека solver
add_library(solver STATIC solver_lib/solver.cpp)
target_include_directories(solver PUBLIC solver_lib)

# Основное приложение
add_executable(hello_world hello_world_application/hello_world.cpp)
target_link_libraries(hello_world formatter)

# Дополнительное приложение (если нужно)
add_executable(solver_app solver_application/equation.cpp)
target_link_libraries(solver_app solver formatter)
