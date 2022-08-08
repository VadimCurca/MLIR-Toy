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
    ${CMAKE_CURRENT_SOURCE_DIR}/parser/AST.cpp
)

llvm_update_compile_flags(ToyHello)

target_link_libraries(ToyHello PRIVATE ${LIBS})
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)

mlir_check_all_link_libraries(ToyHello)
