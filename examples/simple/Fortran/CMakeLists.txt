execute_process(COMMAND ${PROJECT_SOURCE_DIR}/util/effis-cpp.py repo ${CMAKE_CURRENT_SOURCE_DIR} --tree-output=${CMAKE_CURRENT_BINARY_DIR})
add_definitions(${fotran_free_flag})

add_executable(writer ${CMAKE_CURRENT_BINARY_DIR}/writer-kittie.F90)
target_link_libraries(writer kittie_f adios2::adios2_f)

add_executable(reader ${CMAKE_CURRENT_BINARY_DIR}/reader-kittie.F90)
target_link_libraries(reader kittie_f adios2::adios2_f)

install(TARGETS writer DESTINATION ${CMAKE_INSTALL_PREFIX}/examples/simple/Fortran)
install(TARGETS reader DESTINATION ${CMAKE_INSTALL_PREFIX}/examples/simple/Fortran)
install(FILES ${CMAKE_CURRENT_SOURCE_DIR}/example.yaml DESTINATION ${CMAKE_INSTALL_PREFIX}/examples/simple/Fortran)
install(FILES ${CMAKE_CURRENT_SOURCE_DIR}/setup.sh DESTINATION ${CMAKE_INSTALL_PREFIX}/examples/simple/Fortran)
install(FILES ${CMAKE_CURRENT_SOURCE_DIR}/writer.F90 DESTINATION ${CMAKE_INSTALL_PREFIX}/examples/simple/Fortran)
install(FILES ${CMAKE_CURRENT_SOURCE_DIR}/reader.F90 DESTINATION ${CMAKE_INSTALL_PREFIX}/examples/simple/Fortran)
install(FILES ${CMAKE_CURRENT_BINARY_DIR}/writer-kittie.F90 DESTINATION ${CMAKE_INSTALL_PREFIX}/examples/simple/Fortran)
install(FILES ${CMAKE_CURRENT_BINARY_DIR}/reader-kittie.F90 DESTINATION ${CMAKE_INSTALL_PREFIX}/examples/simple/Fortran)
