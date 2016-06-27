cmake_minimum_required(VERSION 2.8.12)
project(structlog)
find_package(catkin REQUIRED COMPONENTS catkin_pip)

# We need to install dev-requirements for testing
catkin_pip_requirements(dev-requirements.txt --ignore-installed)

# This replace catkin_python_setup()
# For devel, this will install all your unsatisfied pip dependencies.
# Upon install, this should bark (but currently might choke and die) if some dependencies are not already satisfied (installed on system by ROS).
catkin_pip_setup()

# Here we plug back into usual catkin package build flow
catkin_package()

## Unit tests
if (CATKIN_ENABLE_TESTING)
    catkin_add_pytests(tests)
endif()
