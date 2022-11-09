cmake_minimum_required(VERSION 3.10)

aux_source_directory(${CMAKE_CURRENT_SOURCE_DIR}/src src_dir)

# add a static library target dedupClientLib
add_library(dedupClientLib6 STATIC ${src_dir} )
target_include_directories(dedupClientLib6 PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/include)
target_link_libraries(dedupClientLib6 -L/usr/local/ssl/lib    -lssl -lcrypto -lpthread -ldl -lgf_complete)
add_executable(ClientTest6 dev-test/main.cc)
target_link_libraries(ClientTest6 dedupClientLib6)
target_include_directories(ClientTest6 PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/include)