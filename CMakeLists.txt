cmake_minimum_required(VERSION 3.21)
project( obstack-standalone LANGUAGES C)

add_library(obstack STATIC obstack.c)
target_include_directories(obstack PRIVATE ".")
set_target_properties(obstack PROPERTIES PUBLIC_HEADER "obstack.h")

add_executable(tst-obstack tst-obstack.c)
target_link_libraries(tst-obstack PRIVATE obstack)
target_include_directories(tst-obstack PRIVATE ".")

install(TARGETS obstack
        LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
        PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})

add_test(build_test_code "${CMAKE_COMMAND}" --build ${CMAKE_BINARY_DIR} --target tst-obstack)
add_test(NAME test COMMAND $<TARGET_FILE:tst-obstack>)
set_tests_properties(test PROPERTIES DEPENDS build_test_code)
enable_testing()

