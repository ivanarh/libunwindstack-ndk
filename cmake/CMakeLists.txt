set(UNWINDSTACK_ROOT ${CMAKE_CURRENT_SOURCE_DIR}/../)

add_subdirectory(lzma)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
include_directories(${UNWINDSTACK_ROOT} ${UNWINDSTACK_ROOT}/include ${UNWINDSTACK_ROOT}/lzma/C)
file(GLOB UNWINDSTACK_SOURCES
    ${UNWINDSTACK_ROOT}/ArmExidx.cpp
    ${UNWINDSTACK_ROOT}/DwarfCfa.cpp
    ${UNWINDSTACK_ROOT}/DwarfDebugFrame.cpp
    ${UNWINDSTACK_ROOT}/DwarfEhFrame.cpp
    ${UNWINDSTACK_ROOT}/DwarfMemory.cpp
    ${UNWINDSTACK_ROOT}/DwarfOp.cpp
    ${UNWINDSTACK_ROOT}/DwarfSection.cpp
    ${UNWINDSTACK_ROOT}/Elf.cpp
    ${UNWINDSTACK_ROOT}/ElfInterface.cpp
    ${UNWINDSTACK_ROOT}/ElfInterfaceArm.cpp
    ${UNWINDSTACK_ROOT}/Log.cpp
    ${UNWINDSTACK_ROOT}/MapInfo.cpp
    ${UNWINDSTACK_ROOT}/Maps.cpp
    ${UNWINDSTACK_ROOT}/Memory.cpp
    ${UNWINDSTACK_ROOT}/Regs.cpp
    ${UNWINDSTACK_ROOT}/Symbols.cpp
    ${UNWINDSTACK_ROOT}/android-base/stringprintf.cpp
    ${UNWINDSTACK_ROOT}/getline.c
)
add_library(unwindstack STATIC ${UNWINDSTACK_SOURCES})
target_link_libraries(unwindstack lzma)
