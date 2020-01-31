# CMake 最低版本号要求

cmake_minimum_required (VERSION 2.8)

# 项目信息

project (glLearn)

# 查找当前目录下的所有源文件

include_directories("D:/Documents/IndieGame/openGL-externel/include")
include_directories("D:/Documents/IndieGame/glLearn")

link_directories("D:/Documents/IndieGame/openGL-externel/lib")
set(MY_PATH "PATH=%PATH%" "D:/Documents/IndieGame/glLearn")

file( GLOB APP_SOURCES src/*.cpp)
#message(${APP_SOURCES})
foreach( sourcefile ${APP_SOURCES} )
    # I used a simple string replace, to cut off .cpp.
    string( REPLACE ".cpp" "" temp ${sourcefile} )
	string( REGEX REPLACE ".*/" "" src ${temp} )
	message(${src})
    add_executable( ${src} ${sourcefile} )
    # Make sure YourLib is linked to each app
    target_link_libraries( ${src} opengl32 glfw3 glad learnopengl)
	#set_target_properties(${src} PROPERTIES VS_DEBUGGER_ENVIRONMENT "${MY_PATH}")
	set_target_properties(${src} PROPERTIES VS_DEBUGGER_WORKING_DIRECTORY "D:/Documents/IndieGame/glLearn/work") 
endforeach( sourcefile ${APP_SOURCES} )