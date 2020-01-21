cmake_minimum_required(VERSION 3.10)

project("How to call C libraries from C++" LANGUAGES C CXX)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

file(GLOB_RECURSE SRCS Po7/*.cpp PlusPlust/*.h PlusPlust/*.cpp)

add_library(socketwrapper STATIC ${SRCS})
target_include_directories(
	socketwrapper
	PUBLIC ${CMAKE_CURRENT_LIST_DIR}/PlusPlus/Forwarding
	PUBLIC ${CMAKE_CURRENT_LIST_DIR}/PlusPlus/Invoking
	PUBLIC "${CMAKE_CURRENT_LIST_DIR}/PlusPlus/Invoking/Group modifiers"
	PUBLIC ${CMAKE_CURRENT_LIST_DIR}/PlusPlus/Invoking/Groups
	PUBLIC ${CMAKE_CURRENT_LIST_DIR}/PlusPlus/Seizing
	PUBLIC ${CMAKE_CURRENT_LIST_DIR}/PlusPlus/Standardish
	PUBLIC ${CMAKE_CURRENT_LIST_DIR}/PlusPlus/Wrapping
	PUBLIC ${CMAKE_CURRENT_LIST_DIR}/Po7
)

add_executable(po7socket-test main.cpp)
target_link_libraries(po7socket-test socketwrapper)



