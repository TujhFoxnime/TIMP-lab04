# TIMP-lab03

Часть I

1) sudo apt install cmake
2) mkdir formatter_lib
3) cd formatter_lib
4) mkdir file
5) cd file
6) wget https://raw.githubusercontent.com/tp-labs/lab03/master/formatter_lib/formatter.h
7) wget https://raw.githubusercontent.com/tp-labs/lab03/master/formatter_lib/formatter.cpp
8) cd
9) cd formatter_lib
10) mkdir folder
11) cmake --version             версия cmake
12) which g++       путь до джи++
    /usr/bin/g++
12) nano CMakeLists.txt :                             редактор
cmake_minimum_required(VERSION 3.22.1 FATAL_ERROR)     это общие стандарты (cmake)
set(CMAKE_CXX_STANDARD 11)                             и это                
set(CMAKE_CXX_STANDARD_REQUIRED ON)                    и это
project(formatter)                                     а этот присваивает имя проекту
add_library(formatter_lib STATIC ${CMAKE_CURRENT_SOURCE_DIR}/b/formatter.cpp)             а тут указывается путь до библиотеки

cd prep
cmake ..                       компиляция файлов в prep
cmake --build .                  сборка
                        [100%] Built target formatter_lib





Часть II


1) mkdir formatter_ex_lib
2) cd formatter_ex_lib
3) mkdir b
4) cd b
5) wget https://github.com/tp-labs/lab03/blob/master/formatter_ex_lib/formatter_ex.h
6) wget https://github.com/tp-labs/lab03/blob/master/formatter_ex_lib/formatter_ex.cpp
7) cd formatter_ex_lib
8) mkdir prep
9) nano CMakeLists.txt

cmake_minimum_required(VERSION 3.22.1 FATAL_ERROR)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
project(formatter_ex)
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../formatter_lib formatter)
add_library(formatter_ex_lib STATIC ${CMAKE_CURRENT_SOURCE_DIR}/b/formatter_ex.>     ПУТЬ ДО ДО ФАЙЛА
target_include_directories(formatter_ex_lib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/>      добавляем включаемые каталоги в цель
target_link_libraries(formatter_ex_lib formatter_lib)                   связка библиотек (1 и 2)


10) cd prep
11) cmake ..
12) cmake -- build .    

                   [100%] Built target formatter_ex_lib





Часть III. hello_world


1) mkdir hw
2) cd hw
3) ~/hw$ mkdir build
4) ~/hw$ cd build
5) ~/hw/build$ wget https://raw.githubusercontent.com/tp-labs/lab03/master/hello_world_application/hello_world.cpp
6) ~$ cd hw
7) ~/hw$ nano CMakeLists.txt

cmake_minimum_required(VERSION 3.22.1 FATAL_ERROR)
project(hello_world)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../formatter_ex_lib formatter_ex)
add_executable(hello_world ${CMAKE_CURRENT_SOURCE_DIR}/build/hello_world.cpp)
include_directories("~/formatter_lib/b")
include_directories("~/formatter_ex_lib/b")
target_link_libraries(hello_world formatter_ex_lib)

8) ~/hw$ cd build
9) ~/hw/build$ cmake ..
10) ~/hw/build$ cmake --build .
                                [100%] Built target hello_world


Часть III  _solver


1) mkdir solver_lib
2) cd solver_lib
3) mkdir build
4) cd build
5) wget https://github.com/tp-labs/lab03/blob/master/solver_lib/solver.cpp

wget https://raw.githubusercontent.com/tp-labs/lab03/blob/master/solver_lib/solver.h

wget https://raw.githubusercontent.com/tp-labs/lab03/blob/master/solver_application/equation.cpp](https://github.com/tp-labs/lab03/blob/master/solver_application/equation.cpp)

6) cd solver_lib
7) nano CMakeLists.txt

cmake_minimum_required(VERSION 3.22.1 FATAL_ERROR)
project(solver)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../formatter_ex_lib formatter_ex_l>
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../solver_lib solver_lib_dir)
add_executable(solver "~/solver_lib/build/equation.cpp")
target_include_directories(solver PUBLIC
{CMAKE_CURRENT_SOURCE_DIR}/../solver_lib/build)
target_link_libraries(solver formatter_ex_lib solver_lib)



8) cd build
9) cmake ..
10) cmake --build .
[ 12%] Building CXX object slvr/CMakeFiles/solver_lib.dir/src/solver.cpp.o
[ 25%] Linking CXX static library libsolver_lib.a
[ 25%] Built target solver_lib
[ 37%] Building CXX object frmtr_ex/formatter/CMakeFiles/formatter_lib.dir/src/formatter.cpp.o
[ 50%] Linking CXX static library libformatter_lib.a
[ 50%] Built target formatter_lib
[ 62%] Building CXX object frmtr_ex/CMakeFiles/formatter_ex_lib.dir/src/formatter_ex.cpp.o
[ 75%] Linking CXX static library libformatter_ex_lib.a
[ 75%] Built target formatter_ex_lib
[ 87%] Building CXX object CMakeFiles/solver.dir/src/equation.cpp.o
[100%] Linking CXX executable solver
[100%] Built target solver
