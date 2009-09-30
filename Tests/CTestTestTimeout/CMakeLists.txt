cmake_minimum_required (VERSION 2.6)
PROJECT(CTestTestTimeout)

SET(DART_ROOT "" CACHE STRING "" FORCE)
ENABLE_TESTING()
INCLUDE (${CMAKE_ROOT}/Modules/Dart.cmake)

GET_FILENAME_COMPONENT(CTEST_COMMAND "${CMAKE_COMMAND}" PATH)
SET(CTEST_COMMAND "${CTEST_COMMAND}/ctest")

ADD_EXECUTABLE (Timeout timeout.c)

ENABLE_TESTING ()

ADD_TEST (TestTimeout Timeout)
SET_TESTS_PROPERTIES(TestTimeout PROPERTIES TIMEOUT 1)

INCLUDE (CTest)