message(STATUS "Building benchmarks")

set(target dkm_bench)

set(sources
	bench.cpp
)

find_package(OpenCV REQUIRED)
add_executable(${target} ${sources})
target_link_libraries(${target} ${OpenCV_LIBS})
if(OpenMP_CXX_FOUND)
	target_link_libraries(${target} OpenMP::OpenMP_CXX)
endif()

file(COPY "iris.data.csv" DESTINATION "${EXECUTABLE_OUTPUT_PATH}")
file(COPY "s1.data.csv" DESTINATION "${EXECUTABLE_OUTPUT_PATH}")
file(COPY "birch3.data.csv" DESTINATION "${EXECUTABLE_OUTPUT_PATH}")
file(COPY "dim128.data.csv" DESTINATION "${EXECUTABLE_OUTPUT_PATH}")