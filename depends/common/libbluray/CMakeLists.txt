project(libbluray)

cmake_minimum_required(VERSION 2.8)

include(ExternalProject)
externalproject_add(libbluray
                    SOURCE_DIR ${CMAKE_SOURCE_DIR}
                    UPDATE_COMMAND ""
                    CONFIGURE_COMMAND <SOURCE_DIR>/configure
                      --prefix=${OUTPUT_DIR}
                      --enable-static
                      --disable-shared
                      --without-libxml2
                      --disable-bdjava-jar
                      --disable-doxygen-doc
                      --without-freetype
                      CFLAGS=-fPIC
                    INSTALL_COMMAND ""
                    BUILD_IN_SOURCE 1)

install(CODE "execute_process(COMMAND make install WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR})")
