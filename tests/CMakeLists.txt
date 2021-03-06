project (tests CXX)
set (OUTPUT_DIR ${CMAKE_BINARY_DIR})

if (NOT PLIBSYS_TESTS_STATIC)
        find_package (Boost COMPONENTS unit_test_framework REQUIRED)
        include_directories (${Boost_INCLUDE_DIR})
else()
        find_package (Boost COMPONENTS unit_test_framework)

        if (NOT Boost_FOUND AND NOT BOOST_ROOT)
                message (FATAL_ERROR "You must specify BOOST_ROOT variable when building static tests without proper Boost installation")
        elseif (Boost_FOUND)
                add_definitions (-DPLIBSYS_TESTS_STATIC)
                set (Boost_LIBRARIES "")
                
                include_directories (${Boost_INCLUDE_DIR})
        else()
                add_definitions (-DPLIBSYS_TESTS_STATIC)
                set (Boost_LIBRARIES "")

                if (NOT IS_ABSOLUTE "${BOOST_ROOT}")
                        get_filename_component (BOOST_ROOT_ABSOLUTE "${CMAKE_CURRENT_BINARY_DIR}/${BOOST_ROOT}" ABSOLUTE)
                        set (BOOST_ROOT ${BOOST_ROOT_ABSOLUTE})
                endif()

                include_directories (${BOOST_ROOT})
        endif()
endif()

include_directories (${PROJECT_SOURCE_DIR}/../src ${CMAKE_BINARY_DIR})

if (MSVC)
        add_definitions (-D_CRT_SECURE_NO_WARNINGS)
endif()

set (PATOMIC_TEST_SRCS patomic_test.cpp)
add_executable (patomic_test ${PATOMIC_TEST_SRCS})
target_link_libraries (patomic_test ${Boost_LIBRARIES} plibsys)
set_target_properties (patomic_test PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${OUTPUT_DIR})

set (PCONDVARIABLE_TEST_SRCS pcondvariable_test.cpp)
add_executable (pcondvariable_test ${PCONDVARIABLE_TEST_SRCS})
target_link_libraries (pcondvariable_test ${Boost_LIBRARIES} plibsys)
set_target_properties (pcondvariable_test PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${OUTPUT_DIR})

set (PCRYPTOHASH_TEST_SRCS pcryptohash_test.cpp)
add_executable (pcryptohash_test ${PCRYPTOHASH_TEST_SRCS})
target_link_libraries (pcryptohash_test ${Boost_LIBRARIES} plibsys)
set_target_properties (pcryptohash_test PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${OUTPUT_DIR})

set (PERROR_TEST_SRCS perror_test.cpp)
add_executable (perror_test ${PERROR_TEST_SRCS})
target_link_libraries (perror_test ${Boost_LIBRARIES} plibsys)
set_target_properties (perror_test PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${OUTPUT_DIR})

set (PDIR_TEST_SRCS pdir_test.cpp)
add_executable (pdir_test ${PDIR_TEST_SRCS})
target_link_libraries (pdir_test ${Boost_LIBRARIES} plibsys)
set_target_properties (pdir_test PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${OUTPUT_DIR})

set (PFILE_TEST_SRCS pfile_test.cpp)
add_executable (pfile_test ${PFILE_TEST_SRCS})
target_link_libraries (pfile_test ${Boost_LIBRARIES} plibsys)
set_target_properties (pfile_test PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${OUTPUT_DIR})

set (PHASHTABLE_TEST_SRCS phashtable_test.cpp)
add_executable (phashtable_test ${PHASHTABLE_TEST_SRCS})
target_link_libraries (phashtable_test ${Boost_LIBRARIES} plibsys)
set_target_properties (phashtable_test PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${OUTPUT_DIR})

set (PINI_TEST_SRCS pinifile_test.cpp)
add_executable (pinifile_test ${PINI_TEST_SRCS})
target_link_libraries (pinifile_test ${Boost_LIBRARIES} plibsys)
set_target_properties (pinifile_test PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${OUTPUT_DIR})

set (PLIBRARYLOADER_TEST_SRCS plibraryloader_test.cpp)
add_executable (plibraryloader_test ${PLIBRARYLOADER_TEST_SRCS})
target_link_libraries (plibraryloader_test ${Boost_LIBRARIES} plibsys)
set_target_properties (plibraryloader_test PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${OUTPUT_DIR})

set (PLIST_TEST_SRCS plist_test.cpp)
add_executable (plist_test ${PLIST_TEST_SRCS})
target_link_libraries (plist_test ${Boost_LIBRARIES} plibsys)
set_target_properties (plist_test PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${OUTPUT_DIR})

set (PMACROS_TEST_SRCS pmacros_test.cpp)
add_executable (pmacros_test ${PMACROS_TEST_SRCS})
target_link_libraries (pmacros_test ${Boost_LIBRARIES} plibsys)
set_target_properties (pmacros_test PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${OUTPUT_DIR})

set (PMAIN_TEST_SRCS pmain_test.cpp)
add_executable (pmain_test ${PMAIN_TEST_SRCS})
target_link_libraries (pmain_test ${Boost_LIBRARIES} plibsys)
set_target_properties (pmain_test PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${OUTPUT_DIR})

set (PMEM_TEST_SRCS pmem_test.cpp)
add_executable (pmem_test ${PMEM_TEST_SRCS})
target_link_libraries (pmem_test ${Boost_LIBRARIES} plibsys)
set_target_properties (pmem_test PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${OUTPUT_DIR})

set (PMUTEX_TEST_SRCS pmutex_test.cpp)
add_executable (pmutex_test ${PMUTEX_TEST_SRCS})
target_link_libraries (pmutex_test ${Boost_LIBRARIES} plibsys)
set_target_properties (pmutex_test PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${OUTPUT_DIR})

set (PPROCESS_TEST_SRCS pprocess_test.cpp)
add_executable (pprocess_test ${PPROCESS_TEST_SRCS})
target_link_libraries (pprocess_test ${Boost_LIBRARIES} plibsys)
set_target_properties (pprocess_test PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${OUTPUT_DIR})

set (PRWLOCK_TEST_SRCS prwlock_test.cpp)
add_executable (prwlock_test ${PRWLOCK_TEST_SRCS})
target_link_libraries (prwlock_test ${Boost_LIBRARIES} plibsys)
set_target_properties (prwlock_test PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${OUTPUT_DIR})

set (PSEMAPHORE_TEST_SRCS psemaphore_test.cpp)
add_executable (psemaphore_test ${PSEMAPHORE_TEST_SRCS})
target_link_libraries (psemaphore_test ${Boost_LIBRARIES} plibsys)
set_target_properties (psemaphore_test PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${OUTPUT_DIR})

set (PSHMBUFFER_TEST_SRCS pshmbuffer_test.cpp)
add_executable (pshmbuffer_test ${PSHMBUFFER_TEST_SRCS})
target_link_libraries (pshmbuffer_test ${Boost_LIBRARIES} plibsys)
set_target_properties (pshmbuffer_test PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${OUTPUT_DIR})

set (PSHM_TEST_SRCS pshm_test.cpp)
add_executable (pshm_test ${PSHM_TEST_SRCS})
target_link_libraries (pshm_test ${Boost_LIBRARIES} plibsys)
set_target_properties (pshm_test PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${OUTPUT_DIR})

set (PSOCKET_TEST_SRCS psocket_test.cpp)
add_executable (psocket_test ${PSOCKET_TEST_SRCS})
target_link_libraries (psocket_test ${Boost_LIBRARIES} plibsys)
set_target_properties (psocket_test PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${OUTPUT_DIR})

set (PSOCKETADDRESS_TEST_SRCS psocketaddress_test.cpp)
add_executable (psocketaddress_test ${PSOCKETADDRESS_TEST_SRCS})
target_link_libraries (psocketaddress_test ${Boost_LIBRARIES} plibsys)
set_target_properties (psocketaddress_test PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${OUTPUT_DIR})

set (PSPINLOCK_TEST_SRCS pspinlock_test.cpp)
add_executable (pspinlock_test ${PSPINLOCK_TEST_SRCS})
target_link_libraries (pspinlock_test ${Boost_LIBRARIES} plibsys)
set_target_properties (pspinlock_test PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${OUTPUT_DIR})

set (PSTRING_TEST_SRCS pstring_test.cpp)
add_executable (pstring_test ${PSTRING_TEST_SRCS})
target_link_libraries (pstring_test ${Boost_LIBRARIES} plibsys)
set_target_properties (pstring_test PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${OUTPUT_DIR})

set (PTIMEPROFILER_TEST_SRCS ptimeprofiler_test.cpp)
add_executable (ptimeprofiler_test ${PTIMEPROFILER_TEST_SRCS})
target_link_libraries (ptimeprofiler_test ${Boost_LIBRARIES} plibsys)
set_target_properties (ptimeprofiler_test PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${OUTPUT_DIR})

set (PTREE_TEST_SRCS ptree_test.cpp)
add_executable (ptree_test ${PTREE_TEST_SRCS})
target_link_libraries (ptree_test ${Boost_LIBRARIES} plibsys)
set_target_properties (ptree_test PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${OUTPUT_DIR})

set (PTYPES_TEST_SRCS ptypes_test.cpp)
add_executable (ptypes_test ${PTYPES_TEST_SRCS})
target_link_libraries (ptypes_test ${Boost_LIBRARIES} plibsys)
set_target_properties (ptypes_test PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${OUTPUT_DIR})

set (PUTHREAD_TEST_SRCS puthread_test.cpp)
add_executable (puthread_test ${PUTHREAD_TEST_SRCS})
target_link_libraries (puthread_test ${Boost_LIBRARIES} plibsys)
set_target_properties (puthread_test PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${OUTPUT_DIR})

add_test (NAME patomic_test COMMAND patomic_test)
add_test (NAME pcondvariable_test COMMAND pcondvariable_test)
add_test (NAME pcryptohash_test COMMAND pcryptohash_test)
add_test (NAME pdir_test COMMAND pdir_test)
add_test (NAME perror_test COMMAND perror_test)
add_test (NAME pfile_test COMMAND pfile_test)
add_test (NAME phashtable_test COMMAND phashtable_test)
add_test (NAME pinifile_test COMMAND pinifile_test)
add_test (NAME plibraryloader_test COMMAND plibraryloader_test -- "$<TARGET_FILE:plibsys>")
add_test (NAME plist_test COMMAND plist_test)
add_test (NAME pmacros_test COMMAND pmacros_test)
add_test (NAME pmain_test COMMAND pmain_test)
add_test (NAME pmem_test COMMAND pmem_test)
add_test (NAME pmutex_test COMMAND pmutex_test)
add_test (NAME pprocess_test COMMAND pprocess_test)
add_test (NAME prwlock_test COMMAND prwlock_test)
add_test (NAME psemaphore_test COMMAND psemaphore_test)
add_test (NAME pshmbuffer_test COMMAND pshmbuffer_test)
add_test (NAME pshm_test COMMAND pshm_test)
add_test (NAME psocket_test COMMAND psocket_test)
add_test (NAME psocketaddress_test COMMAND psocketaddress_test)
add_test (NAME pspinlock_test COMMAND pspinlock_test)
add_test (NAME pstring_test COMMAND pstring_test)
add_test (NAME ptimeprofiler_test COMMAND ptimeprofiler_test)
add_test (NAME ptree_test COMMAND ptree_test)
add_test (NAME ptypes_test COMMAND ptypes_test)
add_test (NAME puthread_test COMMAND puthread_test)

# Print summary 
SET (PLIBSYS_TESTS_SUMMARY
"
        == Tests configuration ==

        Build static tests:     ${PLIBSYS_TESTS_STATIC}
        Build static library:   ${PLIBSYS_BUILD_STATIC}

        Boost directory:        ${BOOST_ROOT}
")

message ("${PLIBSYS_TESTS_SUMMARY}")
