cmake_minimum_required(VERSION 3.9)
project(shapefile++ VERSION 0.0.1 DESCRIPTION "shapefile++ is c++ wrapper for shapefile library")
include(GNUInstallDirs)
add_library(shapefile++ SHARED sources/shapefile.cpp)
set_target_properties(shapefile++ PROPERTIES
    VERSION ${PROJECT_VERSION}
    SOVERSION 1
    PUBLIC_HEADER sources/shapefile.hpp)
configure_file(shapefile++.pc.in shapefile++.pc @ONLY)
target_include_directories(shapefile++ PRIVATE .)
install(TARGETS shapefile++
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})
install(FILES ${CMAKE_BINARY_DIR}/shapefile++.pc
    DESTINATION ${CMAKE_INSTALL_DATAROOTDIR}/pkgconfig)
