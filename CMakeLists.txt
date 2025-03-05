cmake_minimum_required(VERSION 3.10)
project(nvblox_sim)

# Set the required CMake version
cmake_minimum_required(VERSION 3.10)

# Default to C99
if(NOT CMAKE_C_STANDARD)
	set(CMAKE_C_STANDARD 99)
endif()

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
	set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(builtin_interfaces REQUIRED)

# Include directories for your package
include_directories(include)


if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  ament_lint_auto_find_test_dependencies()
endif()

###########
# Python ##
###########

# Install Python modules
ament_python_install_package(${PROJECT_NAME})

# Install P.gitignoreython executables
# install(PROGRAMS
#   DESTINATION lib/${PROJECT_NAME}
# )

# Install python launch files.
install(FILES
  src/launch/nvblox.launch.py
  DESTINATION share/${PROJECT_NAME}/
)


ament_package()
