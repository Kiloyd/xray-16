add_subdirectory(LuaJIT-proj)
add_subdirectory(luabind)
if (USE_CXIMAGE)
    add_subdirectory(cximage)
endif()
add_subdirectory(GameSpy)
add_subdirectory(OPCODE)
add_subdirectory(ode)
#add_subdirectory(NVTT)

if (MEMORY_ALLOCATOR STREQUAL "mimalloc")
    set(MI_BUILD_TESTS   OFF CACHE STRING "" FORCE)
    set(MI_BUILD_DYNAMIC OFF CACHE STRING "" FORCE)
    set(MI_SKIP_INSTALL  ON CACHE STRING "" FORCE)
    add_subdirectory(mimalloc)
    set_target_properties(mimalloc-static PROPERTIES
        POSITION_INDEPENDENT_CODE ON
    )
endif()
