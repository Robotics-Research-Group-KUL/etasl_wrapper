cmake_minimum_required(VERSION 3.8)
project(etasl_wrapper)
find_package(ament_cmake REQUIRED)

set(etasl_wrapper_MAJOR_VERSION 1)
set(etasl_wrapper_MINOR_VERSION 4)
set(etasl_wrapper_PATCH_VERSION 0)
set(etasl_wrapper_VERSION
  ${etasl_wrapper_MAJOR_VERSION}.${etasl_wrapper_MINOR_VERSION}.${etasl_wrapper_PATCH_VERSION})

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
    #add_compile_options(-Wall -Wextra -Wpedantic)
    add_compile_options(-Wall -Wextra -Wno-deprecated -Wno-unused-but-set-variable -Wno-unused-parameter -Wno-unused-variable -Wno-reorder)
endif()
add_definitions(-DBOOST_DISABLE_PRAGMA_MESSAGE)

ament_environment_hooks("${CMAKE_CURRENT_SOURCE_DIR}/env-hooks/etasl_wrapper.sh.in") 

#
# compiling etasl:
set(PYTHON_EXECUTABLE /usr/bin/python3) 
SET(ENABLE_ETASL_PY OFF CACHE BOOL "Use python capabilities of eTaSL" FORCE)
set(ENABLE_API_DOC OFF CACHE BOOL "enable generation of API documentation" FORCE) 

add_subdirectory( ${CMAKE_SOURCE_DIR}/ThirdParty/etasl-cmake/standalone-cmake )


ament_package()
