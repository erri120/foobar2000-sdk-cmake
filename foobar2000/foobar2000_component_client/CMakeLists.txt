add_library(foobar2000_component_client STATIC component_client.cpp)

# use C++ 17
target_compile_features(foobar2000_component_client PRIVATE cxx_std_17)

# copied from foobar2000_component_client.cvxproj
# "<WarningLevel>Level3</WarningLevel>" = /W3
# "<CharacterSet>Unicode</CharacterSet>" = /DUNICODE and /D_UNICODE
# "<TreatSpecificWarningsAsErrors>4715</TreatSpecificWarningsAsErrors>" = /we4715
target_compile_options(foobar2000_component_client PRIVATE $<$<CXX_COMPILER_ID:MSVC>:/W3 /DUNICODE /D_UNICODE /we4715>)

# add SDK
target_link_libraries(foobar2000_component_client PUBLIC foobar2000_SDK)