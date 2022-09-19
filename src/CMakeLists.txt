set(LIBS
  PRIVATE
    MLIRAnalysis
    MLIRIR
    MLIRParser
    MLIRPass
    MLIRSideEffectInterfaces
    MLIRTransforms
)

add_llvm_executable(ToyHello
    toyc.cpp
    parser/AST.cpp

    mlir/MLIRGen.cpp
    mlir/Dialect.cpp
    mlir/ToyCombine.cpp

    DEPENDS
    ToyOpsIncGen
)

llvm_update_compile_flags(ToyHello)

add_subdirectory(include)

target_link_libraries(ToyHello PRIVATE ${LIBS})
include_directories(include/)
include_directories(${CMAKE_CURRENT_BINARY_DIR}/include/)

mlir_check_all_link_libraries(ToyHello)
