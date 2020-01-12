# 查找当前目录下的所有源文件

include_directories("D:/Documents/IndieGame/openGL-externel/include")

link_directories("D:/Documents/IndieGame/openGL-externel/lib")


# 并将名称保存到 DIR_LIB_SRCS 变量

aux_source_directory(. DIR_LIB_SRCS)

# 生成链接库

add_executable(hello_window_clear hello_window_clear.cpp)
target_link_libraries(hello_window_clear opengl32 glfw3 glad)

add_executable(hello_triangle_indexed hello_triangle_indexed.cpp)
target_link_libraries(hello_triangle_indexed opengl32 glfw3 glad)