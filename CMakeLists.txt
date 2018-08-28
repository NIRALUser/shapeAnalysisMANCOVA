cmake_minimum_required(VERSION 3.5)
project(shapeAnalysisMANCOVAPackage)

find_package(ITK REQUIRED)
if(ITK_FOUND) 
  include(${ITK_USE_FILE})
endif()

find_package(VTK REQUIRED)
if(VTK_FOUND) 
  include(${VTK_USE_FILE})
endif()

find_package(GenerateCLP REQUIRED)
if(GenerateCLP_FOUND) 
  include(${GenerateCLP_USE_FILE})
endif()

find_package(Boost)
if(Boost_FOUND)
  include_directories(${Boost_INCLUDE_DIRS})
  link_directories(${Boost_LIBRARY_DIRS})
endif()

option(COMPILE_StatNonParamTestPDM "Compile StatNonParamTestPDM." OFF)
option(COMPILE_shapeAnalysisMANCOVA "Compile shapeAnalysisMANCOVA." OFF)

if (COMPILE_StatNonParamTestPDM)
   add_subdirectory(StatNonParamTestPDM)
endif()

if (COMPILE_StatNonParamTestPDM)
   add_subdirectory(shapeAnalysisMANCOVA)
endif()

option(COMPILE_shapeAnalysisMANCOVA_Wizard "Compile shapeAnalysisMANCOVA_Wizard." OFF)

if(COMPILE_shapeAnalysisMANCOVA_Wizard)
  find_package(Qt4)
  if(QT4_FOUND)
    include(${QT_USE_FILE})
  else()
    message(FATAL_ERROR "Qt4 was not found")
  endif()
  add_subdirectory(shapeAnalysisMANCOVA_Wizard)
endif()

