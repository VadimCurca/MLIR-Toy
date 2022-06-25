add_mlir_dialect_library(MLIRToy
	AST.cpp

        ADDITIONAL_HEADER_DIRS
        ${PROJECT_SOURCE_DIR}/example/include/Toy

	LINK_LIBS PUBLIC
	MLIRIR
	)
