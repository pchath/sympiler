cmake_minimum_required(VERSION 3.1)
project(CholeskyTestCHOLMOD)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -DMKL -DCOLDCACHE -Wall -std=gnu++11  -m64  ")

set(SOURCE_FILES TestCHOLMOD.cpp )

include_directories(${MKL_INC} ${SUITE_INC} )
link_directories(${MKL_LIB} ${MMM}  ${SUITE_LIB})
add_executable(CholeskyTestCHOLMOD ${SOURCE_FILES})
target_link_libraries(CholeskyTestCHOLMOD
        iomp5
        mkl_sequential
        mkl_intel_lp64
        mkl_core
        #mkl_gnu_thread
        mkl_intel_thread
        pthread
        m
        dl

        amd
        cholmod
        suitesparseconfig

        )


project(CholeskyTestMKL)
#TODO use env instead



set(SOURCE_FILES  TestMKL.cpp)

include_directories(${MKL_INC} ${SUITE_INC})
link_directories(${MKL_LIB} ${MMM} ${SUITE_LIB})
add_executable(CholeskyTestMKL ${SOURCE_FILES})
target_link_libraries(CholeskyTestMKL
        #mkl_intel_ilp64
        #gomp
        iomp5
        mkl_sequential
        mkl_intel_lp64
        mkl_core
        #mkl_gnu_thread
        mkl_intel_thread
        pthread
        m
        dl
        )