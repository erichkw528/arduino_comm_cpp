cmake_minimum_required(VERSION 3.8)
project(arduino_comm_cpp)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake_auto REQUIRED)

ament_auto_find_build_dependencies(REQUIRED
  ${${PROJECT_NAME}_BUILD_DEPENDS}
  ${${PROJECT_NAME}_BUILDTOOL_DEPENDS}
)


include_directories(
  include
)

set(${PROJECT_NAME}_SRC
  src/arduino_comm_cpp_node.cpp

)



ament_auto_add_executable(${PROJECT_NAME}_node
  ${${PROJECT_NAME}_SRC}
)

# # Plugins
# ament_auto_add_library(${PROJECT_NAME} SHARED
#   ${${PROJECT_NAME}_PLUGIN_SRC}
#   ${${PROJECT_NAME}_SRC}
# )


ament_auto_package(INSTALL_TO_SHARE
  launch
  params
  include
)

