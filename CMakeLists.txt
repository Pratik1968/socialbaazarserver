cmake_minimum_required(VERSION 3.2.0)
project(cppREST VERSION 0.1.0)

include(CTest)
enable_testing()

set(CMAKE_CXX_STANDARD 17)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS}")



include_directories(/opt/homebrew/Cellar/asio/1.28.1/include)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/dependencies/Crow/include)


link_directories(/opt/homebrew/lib)
add_executable(cppREST main.cpp)
set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)
target_link_libraries(${PROJECT_NAME} PRIVATE Threads::Threads)
# target_link_libraries(cppREST boost_system)
# target_link_libraries(cppREST pthread)

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)