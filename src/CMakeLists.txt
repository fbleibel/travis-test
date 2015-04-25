file (GLOB_RECURSE PROJECT_SRCS *.cpp *.cxx *.cc *.C *.c *.h *.hpp)
set (PROJECT_BIN ${PROJECT_NAME})

add_library(staticlib STATIC ${PROJECT_SRCS})
target_link_libraries(staticlib ${PROJECT_LIBS})
set_target_properties(staticlib PROPERTIES VERSION "${APPLICATION_VERSION_MAJOR}.${APPLICATION_VERSION_MINOR}" OUTPUT_NAME ${PROJECT_BIN} CLEAN_DIRECT_OUTPUT 1)
install(TARGETS staticlib DESTINATION lib)

add_library(sharedlib SHARED ${PROJECT_SRCS})
target_link_libraries(sharedlib ${PROJECT_LIBS})
set_target_properties(sharedlib PROPERTIES VERSION "${APPLICATION_VERSION_MAJOR}.${APPLICATION_VERSION_MINOR}" OUTPUT_NAME ${PROJECT_BIN} CLEAN_DIRECT_OUTPUT 1)
install(TARGETS sharedlib DESTINATION lib)

set_property(TARGET sharedlib staticlib PROPERTY CXX_STANDARD 11)
