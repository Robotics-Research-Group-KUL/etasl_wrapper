cmake_minimum_required(VERSION 3.8)
project(etasl_wrapper)
find_package(ament_cmake REQUIRED)

MESSAGE(STATUS "hello from erwin")
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

# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)

#add_library(etasl_wrapper_library SHARED src/etasl_wrapper_library.cpp)
#target_compile_features(etasl_wrapper_library PUBLIC c_std_99 cxx_std_17)  # Require C99 and C++17

#target_include_directories(etasl_wrapper_library PUBLIC
#  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
#  $<INSTALL_INTERFACE:include>
#)

# Causes the visibility macros to use dllexport rather than dllimport,
# which is appropriate when building the dll but not consuming it.
#target_compile_definitions(etasl_wrapper_library PRIVATE "ETASL_WRAPPER_BUILDING_LIBRARY")

# install(
#   DIRECTORY include/
#   DESTINATION include
# )

# install(
#   TARGETS etasl_wrapper_library
#   EXPORT export_etasl_wrapper
#   ARCHIVE DESTINATION lib
#   LIBRARY DESTINATION lib
#   RUNTIME DESTINATION bin)


#add_executable(etasl_wrapper_binary src/etasl_wrapper_binary.cpp)
#target_link_libraries(etasl_wrapper_binary etasl_wrapper_library)


#
# compiling etasl:
set(PYTHON_EXECUTABLE /usr/bin/python3) 
SET(ENABLE_ETASL_PY OFF CACHE BOOL "Use python capabilities of eTaSL" FORCE)
set(ENABLE_API_DOC OFF CACHE BOOL "enable generation of API documentation" FORCE) 
add_subdirectory( ${CMAKE_SOURCE_DIR}/ThirdParty/etasl-cmake/standalone-cmake )


# install(
#   TARGETS etasl_wrapper_binary
#   EXPORT export_etasl_wrapper
#   DESTINATION lib/${PROJECT_NAME})

# export targets

# TODO:
#set(export_targets ${export_targets};etasl_wrapper_library)
#set(export_targets ${export_targets};etasl_wrapper_binary)



#export(EXPORT export_etasl_wrapper
#  FILE "${PROJECT_BINARY_DIR}/export_etasl_wrapper.cmake")

# # Create the etasl_wrapperConfig.cmake
# set(CONF_INCLUDE_DIRS "${CMAKE_INSTALL_PREFIX}/include")
# configure_file(etasl_wrapperConfig.cmake.in
#   "${PROJECT_BINARY_DIR}/${CMAKE_FILES_DIRECTORY}/etasl_wrapperConfig.cmake" @ONLY)

# # Create the etasl_wrapperConfigVersion.cmake
# configure_file(etasl_wrapperConfigVersion.cmake.in
#   "${PROJECT_BINARY_DIR}/etasl_wrapperConfigVersion.cmake" @ONLY)

# install(FILES
#   "${PROJECT_BINARY_DIR}/${CMAKE_FILES_DIRECTORY}/etasl_wrapperConfig.cmake"
#   "${PROJECT_BINARY_DIR}/etasl_wrapperConfigVersion.cmake"
#   DESTINATION "share/${PROJECT_NAME}/cmake" COMPONENT dev)
# install(EXPORT export_etasl_wrapper
#   DESTINATION "share/${PROJECT_NAME}/cmake"
#   FILE export_etasl_wrapper.cmake
#   COMPONENT dev)



#ament_environment_hooks("${CMAKE_CURRENT_SOURCE_DIR}/env-hooks/etasl_wrapper.sh.in")
#ament_environment_hooks("${CMAKE_CURRENT_SOURCE_DIR}/env-hooks/etasl_wrapper.dsv.in")
ament_package()
