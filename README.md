# CMake_Note

## 說明
紀錄一些CMake常用指令，包括如何加入library

## 事前作業
需先安裝mingw
教學有空補

## CMakeList
```C++
# 符合版本的警告
cmake_minimum_required(VERSION 3.0)

# 專案名稱
project(main)

#把當前目錄(cpp)都加進LIST
aux_source_directory(${CMAKE_SOURCE_DIR}/../src SRC_LIST)
#加進LIST
list(APPEND SRC_LIST addition.cpp)
#排除LIST
list(REMOVE_ITEM SRC_LIST exclude.cpp) 

#include目錄
include_directories("."
                    "${CMAKE_SOURCE_DIR}/../OpenCV343/include")
                    

#把相同附檔名納入清單 (載入lib) (如有需要)
file(GLOB DLLA_LIST "${CMAKE_SOURCE_DIR}/../OpenCV343/x64/mingw/lib/*.dll.a")
#print出狀態
message(STATUS "DLLA_LIST : ${DLLA_LIST}")

# 建立exe檔案
add_executable(${PROJECT_NAME} ${SRC_LIST})

# 連結lib庫(如有需要)
target_link_libraries(${PROJECT_NAME} ${DLLA_LIST})
```

## CMark Macro
```C++
${PROJECT_NAME} 專案名稱
${CMAKE_SOURCE_DIR} CMakeList所在檔案路徑
```

## Build Setup
```C++
cd Build
cmake -G"Unix Makefiles" -DCMAKE_BUILD_TYPE=Debug .
make .
```
