project(Bindings.SofaRuntime)

set(SOURCE_FILES
    ${CMAKE_CURRENT_SOURCE_DIR}/src/SofaPython3/SofaRuntime/Module_SofaRuntime.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/src/SofaPython3/SofaRuntime/Timer/Submodule_Timer.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/src/SofaPython3/SofaRuntime/Input/Submodule_Input.cpp
)

set(HEADER_FILES
    ${CMAKE_CURRENT_SOURCE_DIR}/src/SofaPython3/SofaRuntime/Timer/Submodule_Timer.h
    ${CMAKE_CURRENT_SOURCE_DIR}/src/SofaPython3/SofaRuntime/Timer/Submodule_Timer_doc.h
    ${CMAKE_CURRENT_SOURCE_DIR}/src/SofaPython3/SofaRuntime/Input/Submodule_Input.h
    ${CMAKE_CURRENT_SOURCE_DIR}/src/SofaPython3/SofaRuntime/Input/Submodule_Input_doc.h
)

find_package(SofaSimulation REQUIRED)

SP3_add_python_package(
    SOURCE_DIRECTORY
        ${CMAKE_CURRENT_SOURCE_DIR}/package
    TARGET_DIRECTORY
        ${SP3_PYTHON_PACKAGES_DIRECTORY}/SofaRuntime
)

SP3_add_python_module(
        TARGET       ${PROJECT_NAME}
        PACKAGE_NAME SofaRuntime
        MODULE_NAME  SofaRuntime
        SOURCES      ${SOURCE_FILES}
        HEADERS      ${HEADER_FILES}
        DEPENDS      SofaSimulationGraph SofaPython3::Plugin SofaPython3::Bindings.Sofa.Core
)

if(SP3_BUILD_TEST)
    add_subdirectory(tests)
endif()
