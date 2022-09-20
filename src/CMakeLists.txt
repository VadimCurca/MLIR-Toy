include_directories(include)
add_subdirectory(include)

get_property(dialect_libs GLOBAL PROPERTY MLIR_DIALECT_LIBS)

set(LIBS
  PRIVATE
    ${dialect_libs}
    MLIRAnalysis
    MLIRCastInterfaces
    MLIRCallInterfaces
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
    mlir/ShapeInferencePass.cpp
    mlir/LowerToAffineLoops.cpp

    DEPENDS
    ToyOpsIncGen
    ToyCombineIncGen
    ToyShapeInferenceInterfaceIncGen
)

llvm_update_compile_flags(ToyHello)

target_link_libraries(ToyHello PRIVATE ${LIBS})
include_directories(${CMAKE_CURRENT_BINARY_DIR})
include_directories(${CMAKE_CURRENT_BINARY_DIR}/include/)

mlir_check_all_link_libraries(ToyHello)
