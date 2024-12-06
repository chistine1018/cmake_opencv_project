cmake_minimum_required(VERSION 2.8)

# 專案名稱
project(OpenImage)

# 添加 OpenCV 配置
set(OpenCV_DIR "C:/Users/user/Downloads/opencv/build/x64/vc14/lib")
find_package(OpenCV REQUIRED)

if(OpenCV_FOUND)
    message("OpenCV found at ${OpenCV_DIR}")
else()
    message(FATAL_ERROR "OpenCV not found! Please check the path or installation.")
endif()

# 定義包含路徑
include_directories(
    "."
    "C:/Users/user/Downloads/opencv/build/include"
    "C:/Users/user/Downloads/opencv/build/include/opencv"
    "C:/Users/user/Downloads/opencv/build/include/opencv2"
)

# 定義函式來創建可執行檔案
MACRO(MY_DEFINE_EXAMPLE name srcs) 
    add_executable(${name} ${srcs})

    # 鏈接 OpenCV 庫
    target_link_libraries(${name} ${OpenCV_LIBS})

    # 使用 Unicode
    add_definitions(-DUNICODE -D_UNICODE)
ENDMACRO(MY_DEFINE_EXAMPLE)

# 定義範例
MY_DEFINE_EXAMPLE(DisplayImage DisplayImage.cpp)
