set(GTEST_DIR ../third-party/gtest-1.7.0)

file(GLOB_RECURSE INC_FILES ../include/*.h)
file(GLOB TESTS_FILES *.hpp *.cpp)

include_directories(
	../include
    ${GTEST_DIR}
    ${GTEST_DIR}/include)

add_definitions(-DGTEST_HAS_PTHREAD=0)

add_executable(ArduinoJsonTests 
    ${TESTS_FILES}
	${INC_FILES}
    ${GTEST_DIR}/src/gtest-all.cc
    ${GTEST_DIR}/src/gtest_main.cc)

target_link_libraries(ArduinoJsonTests ArduinoJson)

add_test(ArduinoJsonTests ${CMAKE_RUNTIME_OUTPUT_DIRECTORY}/ArduinoJsonTests)
