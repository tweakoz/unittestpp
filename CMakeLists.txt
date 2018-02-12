project (proj_unittestpp CXX)

set( srcdir ${CMAKE_CURRENT_SOURCE_DIR}/src )
file(GLOB src1 ${srcdir}/*.cpp)
file(GLOB src2 ${srcdir}/Posix/*.cpp)
file(GLOB hdrs ${srcdir}/*.h)
file(GLOB posixhdrs ${srcdir}/Posix/*.h)
set( sources ${src1} ${src2} ${hdrs} )
add_library (ork_unittestpp SHARED ${sources} )
set_target_properties(ork_unittestpp PROPERTIES LINKER_LANGUAGE CXX)

set( destinc ${CMAKE_INSTALL_PREFIX}/include/ )
set( destlib ${CMAKE_INSTALL_PREFIX}/lib/ )

install( FILES ${hdrs} DESTINATION ${destinc}/UnitTest++ )
install( FILES ${posixhdrs} DESTINATION ${destinc}/UnitTest++/Posix )
install( TARGETS ork_unittestpp DESTINATION ${destlib} )
