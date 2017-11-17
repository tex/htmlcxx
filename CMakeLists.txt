cmake_minimum_required(VERSION 3.9)
project(htmlcxx VERSION 0.86.1 DESCRIPTION "htmlcxx")
include(GNUInstallDirs)
add_library(htmlcxx html/ParserSax.cc html/ParserDom.cc html/Extensions.cc html/CharsetConverter.cc html/Uri.cc html/Node.cc html/utils.cc)
set_target_properties(htmlcxx PROPERTIES
    VERSION ${PROJECT_VERSION}
    SOVERSION 1
    PUBLIC_HEADER "${CMAKE_SOURCE_DIR}/html/tree.h;${CMAKE_SOURCE_DIR}/html/ParserSax.tcc;${CMAKE_SOURCE_DIR}/html/Node.h;${CMAKE_SOURCE_DIR}/html/ParserDom.h;${CMAKE_SOURCE_DIR}/html/ParserSax.h")
configure_file(htmlcxx.pc.in htmlcxx.pc @ONLY)
target_include_directories(htmlcxx PRIVATE html)
install(TARGETS htmlcxx
    ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/htmlcxx/html)
install(FILES ${CMAKE_BINARY_DIR}/htmlcxx.pc
    DESTINATION ${CMAKE_INSTALL_DATAROOTDIR}/pkgconfig)
