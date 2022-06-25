project(MLIR-Toy)
cmake_minimum_required(VERSION 3.18)

add_subdirectory(thirdparty EXCLUDE_FROM_ALL)

set(LLVM_SOURCE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/thirdparty/llvm-project/llvm")
set(LLVM_BINARY_DIR "${CMAKE_CURRENT_BINARY_DIR}/thirdparty/llvm-project/llvm")

set(MLIR_SOURCE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/thirdparty/llvm-project/mlir")
set(MLIR_BINARY_DIR "${CMAKE_CURRENT_BINARY_DIR}/thirdparty/llvm-project/llvm/tools/mlir")

set(LLVM_INCLUDE_DIRS
    "${LLVM_SOURCE_DIR}/include"
    "${LLVM_BINARY_DIR}/include"
)

set(MLIR_INCLUDE_DIRS
    "${MLIR_SOURCE_DIR}/include"
    "${MLIR_BINARY_DIR}/include"
)


add_subdirectory(example)
