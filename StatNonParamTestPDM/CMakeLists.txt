cmake_minimum_required(VERSION 3.5)
project( StatNonParamTestPDM )

find_package(ITK REQUIRED)
if(ITK_FOUND) 
  include(${ITK_USE_FILE})
endif(ITK_FOUND) 

find_package(VTK REQUIRED)
if(VTK_FOUND) 
  include(${VTK_USE_FILE})
endif(VTK_FOUND) 


SET(StatNonParamTestPDM_SRCS
  createPerm.cxx 
  main.cxx
  computeStatPDM.cxx 
  computeStatPDM_vector.cxx 
  itkMeshTovtkPolyData.cxx 
  vtkPolyDataToitkMesh.cxx
)

add_executable(StatNonParamTestPDM ${StatNonParamTestPDM_SRCS})

target_link_libraries( StatNonParamTestPDM
  ${ITK_LIBRARIES}
  ${VTK_LIBRARIES}
)
