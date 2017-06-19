cmake_minimum_required(VERSION 2.8)
PROJECT(sbpl)

find_package(catkin REQUIRED COMPONENTS
)

catkin_package(
  INCLUDE_DIRS src/include
  LIBRARIES sbpl
  #CATKIN_DEPENDS
  #DEPENDS
)

include_directories(src/include)

add_library(sbpl SHARED
  src/discrete_space_information/environment_nav2D.cpp
  src/discrete_space_information/environment_navxythetalat.cpp
  src/discrete_space_information/environment_navxythetamlevlat.cpp
  src/discrete_space_information/environment_nav2Duu.cpp
  src/discrete_space_information/environment_XXX.cpp
  src/discrete_space_information/environment_robarm.cpp
  src/heuristics/embedded_heuristic.cpp
  src/planners/adplanner.cpp
  src/planners/ANAplanner.cpp
  src/planners/araplanner.cpp
  src/planners/lazyARA.cpp
  src/planners/mhaplanner.cpp
  src/planners/ppcpplanner.cpp
  src/planners/rstarplanner.cpp
  src/planners/viplanner.cpp
  src/utils/heap.cpp
  src/utils/mdp.cpp
  src/utils/utils.cpp
  src/utils/2Dgridsearch.cpp
  src/utils/config.cpp	
  )

install(
  TARGETS sbpl
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

install(DIRECTORY src/include/sbpl
  DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
  FILES_MATCHING PATTERN "*.h"
)


add_executable(test_sbpl src/test/main.cpp)
target_link_libraries(test_sbpl sbpl)

add_executable(test_adjacency_list src/test/test_adjacency_list.cpp)
target_link_libraries(test_adjacency_list sbpl)
