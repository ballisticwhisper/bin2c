
set(EXECUTABLE_OUTPUT_PATH "${CMAKE_SOURCE_DIR}/build")

SET( BIN2C_ROOT_DIR "${CMAKE_SOURCE_DIR}/tools/bin2c" )

FILE( GLOB BIN2C_FILES "${BIN2C_ROOT_DIR}/*.c" )

source_group( "" FILES ${BIN2C_FILES} )

IF(WIN32)
SET(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} /subsystem:windows") 
ENDIF(WIN32)

add_executable (bin2c ${BIN2C_FILES} )

target_link_libraries ( bin2c winmm.lib shlwapi.lib comctl32.lib rpcrt4.lib version.lib wsock32.lib wininet.lib )

IF( WIN32 )
	ADD_DEFINITIONS( -DWIN32 -D_CRT_SECURE_NO_DEPRECATE=1 -D_CRT_NON_CONFORMING_SWPRINTFS=1 -D_SCL_SECURE_NO_WARNINGS=1 -D__WXMSW__ -D_UNICODE -D_WINDOWS -DNOPCH )
ENDIF(  )