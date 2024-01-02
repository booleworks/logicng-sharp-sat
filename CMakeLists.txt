cmake_minimum_required (VERSION 3.24)
project (SHARPSAT) 

set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -std=c++11 -Wall")

set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} -std=c++11 -O3 -DNDEBUG -Wall")

set(CMAKE_CXX_FLAGS_PROFILING "${CMAKE_CXX_FLAGS_PROFILING} -std=c++11 -O3 -g -DNDEBUG -Wall")

IF(UNIX)
  IF(APPLE)
    IF(CMAKE_APPLE_SILICON_PROCESSOR)
      include_directories(/opt/homebrew/include/Cellar/gmp/6.3.0/include)
    ELSE(CMAKE_APPLE_SILICON_PROCESSOR)
      include_directories(/usr/local/Cellar/gmp/6.3.0/include)
    ENDIF(CMAKE_APPLE_SILICON_PROCESSOR)
  ELSE(APPLE)
    
    
  ENDIF(APPLE)
ELSE(UNIX)

ENDIF(UNIX)


find_library(GMP_LIB gmp)
find_library(GMPXX_LIB gmpxx)


add_subdirectory(src)
