# CMake 最低版本号要求

cmake_minimum_required (VERSION 2.8)

# 项目信息

project (glLearn)

file( GLOB APP_SOURCES src/*.cpp)
#message(${APP_SOURCES})
foreach( sourcefile ${APP_SOURCES} )
    # I used a simple string replace, to cut off .cpp.
    string( REPLACE ".cpp" "" temp ${sourcefile} )
	string( REGEX REPLACE ".*/" "" src ${temp} )
	message(${src})
    add_executable( ${src} ${sourcefile} )
    # Make sure YourLib is linked to each app
    target_link_libraries( ${src} opengl32 glfw3 glad )
endforeach( sourcefile ${APP_SOURCES} )