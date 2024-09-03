set(BOOST_INSTALL_DIR ${CMAKE_CURRENT_SOURCE_DIR}/boost_install CACHE PATH "Boost installation directory")
if(EXISTS ${CMAKE_CURRENT_SOURCE_DIR}/boost_install)
    message(STATUS "boost has been installed")
else()
    # ./bootstrap.sh --prefix=boost_install/
    execute_process(COMMAND ./bootstrap.sh --prefix=boost_install/
                    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR})

    # .b2 install
    execute_process(COMMAND ./b2 install
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR})
endif()
