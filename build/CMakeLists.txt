# CMake最低版本號要求
# 這一行功能在確定目前使用的 CMake 版本符合需求，當版本不滿足最低需求時會發出錯誤訊息。即使沒加上這一檢查仍然可以繼續完成建置工作，只是 CMake 會發出警告。
cmake_minimum_required(VERSION 3.0)

# 項目名稱
project(main)

#建立愈編譯文件列表
aux_source_directory(${CMAKE_SOURCE_DIR}/../src SRC_LIST)
#list(REMOVE_ITEM SRC_LIST "exclude.cpp") 
#list(APPEND SRC_LIST test.cpp)


include_directories("."
		    "${CMAKE_SOURCE_DIR}/../OpenCV343/include")

set(OpenCV_DIR "${CMAKE_SOURCE_DIR}/../OpenCV343")
#find_package( OpenCV REQUIRED )

message(STATUS "OpenCV library status:")
message(STATUS "version: ${OpenCV_VERSION}")
message(STATUS "libraries: ${OpenCV_LIBS}")
message(STATUS "include path: ${OpenCV_INCLUDE_DIRS}")


file(GLOB DLLA_LIST "${CMAKE_SOURCE_DIR}/../OpenCV343/x64/mingw/lib/*.dll.a")
message(STATUS "include path: ${DLLA_LIST}")

SET(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/../bin)


# 指定生成目標
add_executable(${PROJECT_NAME} ${SRC_LIST})
#target_link_libraries(${PROJECT_NAME} ${OpenCV_LIBS})
target_link_libraries(${PROJECT_NAME} ${DLLA_LIST})