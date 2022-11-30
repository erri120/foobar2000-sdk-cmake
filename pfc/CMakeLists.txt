add_library(pfc STATIC)

target_sources(pfc PRIVATE
    audio_math.cpp
    audio_sample.cpp
    base64.cpp
    bigmem.cpp
    bit_array.cpp
    bsearch.cpp
    charDownConvert.cpp
    cpuid.cpp
    crashWithMessage.cpp
    filehandle.cpp
    guid.cpp
    nix-objects.cpp
    other.cpp
    pathUtils.cpp
    pfc-fb2k-hooks.cpp
    printf.cpp
    selftest.cpp
    SmartStrStr.cpp
    sort.cpp
    splitString2.cpp
    stdafx.cpp
    string_base.cpp
    string_conv.cpp
    string-compare.cpp
    string-conv-lite.cpp
    string-lite.cpp
    synchro_nix.cpp
    threads.cpp
    timers.cpp
    unicode-normalize.cpp
    utf8.cpp
    wildcard.cpp
    win-objects.cpp
)

# add pch
target_precompile_headers(pfc PRIVATE pfc-lite.h)

# use C++ 17
target_compile_features(pfc PRIVATE cxx_std_17)

# copied from pfc.cvxproj
# "<WarningLevel>Level3</WarningLevel>" = /W3
# "<CharacterSet>Unicode</CharacterSet>" = /DUNICODE and /D_UNICODE
# "<TreatSpecificWarningsAsErrors>4715</TreatSpecificWarningsAsErrors>" = /we4715
target_compile_options(pfc PRIVATE $<$<CXX_COMPILER_ID:MSVC>:/W3 /DUNICODE /D_UNICODE /we4715>)

# add previously defined options
target_link_libraries(pfc PUBLIC project_options)
