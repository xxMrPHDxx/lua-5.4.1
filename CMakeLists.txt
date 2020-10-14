cmake_minimum_required( VERSION 3.10 )
project( lua541 )

file( GLOB_RECURSE HDRS src/*.h )
set( SRCS
	src/lapi.c
	src/lauxlib.c
	src/lbaselib.c
	src/lcode.c
	src/lcorolib.c
	src/lctype.c
	src/ldblib.c
	src/ldebug.c
	src/ldo.c
	src/ldump.c
	src/lfunc.c
	src/lgc.c
	src/linit.c
	src/liolib.c
	src/llex.c
	src/lmathlib.c
	src/lmem.c
	src/loadlib.c
	src/lobject.c
	src/lopcodes.c
	src/loslib.c
	src/lparser.c
	src/lstate.c
	src/lstring.c
	src/lstrlib.c
	src/ltable.c
	src/ltablib.c
	src/ltm.c
	src/lundump.c
	src/lutf8lib.c
	src/lvm.c
	src/lzio.c
)

add_definitions( -DLUA_USE_POSIX )
add_library( lua ${SRCS} )
target_link_libraries( lua m )
add_executable( luae ${HDRS} src/lua.c )
target_link_libraries( luae lua )
add_executable( luac ${HDRS} src/luac.c )
target_link_libraries( luac lua )

file( COPY src/
    DESTINATION include/
    FILES_MATCHING
        PATTERN .hpp
        PATTERN .h
)