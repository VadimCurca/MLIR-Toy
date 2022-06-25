set(LIBS
  PRIVATE
    # MLIRAnalysis
    # MLIRIR
    MLIRParser
    # MLIRPass
    # MLIRSideEffectInterfaces
    # MLIRTransforms
)

add_llvm_executable(ToyHello
    toyc.cpp
    ${PROJECT_SOURCE_DIR}/parser/AST.cpp
)

llvm_update_compile_flags(ToyHello)

target_link_libraries(ToyHello PRIVATE ${LIBS})

mlir_check_all_link_libraries(ToyHello)
