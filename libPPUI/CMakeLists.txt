add_library(libPPUI STATIC)

target_sources(libPPUI PRIVATE
    AutoComplete.cpp
    CDialogResizeHelper.cpp
    CEditWithButtons.cpp
    clipboard.cpp
    CListAccessible.cpp
    CListControl-Cells.cpp
    CListControl-Subst.cpp
    CListControl.cpp
    CListControlHeaderImpl.cpp
    CListControlTruncationTooltipImpl.cpp
    CListControlWithSelection.cpp
    CMiddleDragImpl.cpp
    commandline_parser.cpp
    Controls.cpp
    CPowerRequest.cpp
    DarkMode.cpp
    gdiplus_helpers.cpp
    GDIUtils.cpp
    IDataObjectUtils.cpp
    ImageEncoder.cpp
    InPlaceCombo.cpp
    InPlaceEdit.cpp
    InPlaceEditTable.cpp
    listview_helper.cpp
    PaintUtils.cpp
    stdafx.cpp
    TypeFind.cpp
    win32_op.cpp
    win32_utility.cpp
)

# use C++ 17
target_compile_features(libPPUI PRIVATE cxx_std_17)

# copied from libPPUI.cvxproj
# "<WarningLevel>Level3</WarningLevel>" = /W3
# "<CharacterSet>Unicode</CharacterSet>" = /DUNICODE and /D_UNICODE
# "<TreatSpecificWarningsAsErrors>4715</TreatSpecificWarningsAsErrors>" = /we4715
target_compile_options(libPPUI PRIVATE $<$<CXX_COMPILER_ID:MSVC>:/W3 /DUNICODE /D_UNICODE /we4715>)

# "<SubSystem>Windows</SubSystem>" = /SUBSYSTEM:Windows
target_link_options(libPPUI PRIVATE $<$<CXX_COMPILER_ID:MSVC>:/SUBSYSTEM:Windows>)

# add include directory as INTERFACE so dependents can import this lib with
# #import <libPPUI/...>
target_include_directories(libPPUI INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}/..)

# add WTL headers
target_link_libraries(libPPUI PUBLIC wtl)

# add pfc
target_link_libraries(libPPUI PUBLIC pfc)