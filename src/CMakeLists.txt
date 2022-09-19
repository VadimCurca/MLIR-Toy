add_subdirectory(include)
include_directories(include)

set(LIBS
  PRIVATE
    MLIRAnalysis
    MLIRIR
    MLIRParser
    MLIRPass
    MLIRSideEffectInterfaces
    MLIRTransforms
)

set(LLVM_TARGET_DEFINITIONS mlir/ToyCombine.td)
mlir_tablegen(ToyCombine.inc -gen-rewriters)
add_public_tablegen_target(ToyCombineIncGen)

add_llvm_executable(ToyHello
    toyc.cpp
    parser/AST.cpp

    mlir/MLIRGen.cpp
    mlir/Dialect.cpp
    mlir/ToyCombine.cpp

    DEPENDS
    ToyOpsIncGen
    ToyCombineIncGen
)

llvm_update_compile_flags(ToyHello)

target_link_libraries(ToyHello PRIVATE ${LIBS})
include_directories(${CMAKE_CURRENT_BINARY_DIR})
include_directories(${CMAKE_CURRENT_BINARY_DIR}/include/)

mlir_check_all_link_libraries(ToyHello)
