cmake_minimum_required(VERSION 3.8)
project(iqr_ptu2)

# ────────── core CMake / Python helpers ──────────
find_package(ament_cmake REQUIRED)
find_package(ament_cmake_python REQUIRED)     # ← the missing line
find_package(Python3 REQUIRED COMPONENTS Interpreter)

# ────────── Python package install ───────────────
ament_python_install_package(
  iqr_ptu2_ros2
  PACKAGE_DIR src/iqr_ptu2_ros2)

install(PROGRAMS
  src/iqr_ptu2_ros2/node.py
  src/iqr_ptu2_ros2/model.py
  src/iqr_ptu2_ros2/teleop.py
  DESTINATION lib/${PROJECT_NAME})

install(DIRECTORY launch urdf DESTINATION share/${PROJECT_NAME})
install(FILES 56-pan-tilt.rules DESTINATION share/${PROJECT_NAME})

ament_package()
