cmake_minimum_required(VERSION 3.13)

project(minIni LANGUAGES C)

option(MININI_USE_STDIO ON "enable stdio")
option(MININI_USE_NX ON "enable native nx support")
option(MININI_USE_FLOAT ON "enable floating support")

add_library(minIni
    source/minGlue-nx.c
    source/minGlue.c
    source/minIni.c
)

target_include_directories(minIni PUBLIC include)

set_target_properties(minIni PROPERTIES
    C_STANDARD 99
)

target_compile_definitions(minIni PRIVATE
    MININI_USE_STDIO=$<BOOL:${MININI_USE_STDIO}>
    MININI_USE_NX=$<BOOL:${MININI_USE_NX}>
    MININI_USE_FLOAT=$<BOOL:${MININI_USE_FLOAT}>
)
