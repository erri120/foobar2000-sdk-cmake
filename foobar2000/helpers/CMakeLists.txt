add_library(foobar2000_helpers STATIC)

target_sources(foobar2000_helpers PRIVATE
    album_art_helpers.cpp
    AutoComplete.cpp
    cfg_guidlist.cpp
    cfg_var_import.cpp
    create_directory_helper.cpp
    CTableEditHelper-Legacy.cpp
    cue_creator.cpp
    cue_parser_embedding.cpp
    cue_parser.cpp
    cuesheet_index_list.cpp
    DarkMode.cpp
    dialog_resize_helper.cpp
    dropdown_helper.cpp
    dynamic_bitrate_helper.cpp
    file_list_helper.cpp
    file_move_helper.cpp
    file_win32_wrapper.cpp
    filetimetools.cpp
    image_load_save.cpp
    inplace_edit.cpp
    input_helper_cue.cpp
    input_helpers.cpp
    mp3_utils.cpp
    packet_decoder_aac_common.cpp
    packet_decoder_mp3_common.cpp
    readers.cpp
    seekabilizer.cpp
    StdAfx.cpp
    stream_buffer_helper.cpp
    text_file_loader_v2.cpp
    text_file_loader.cpp
    ThreadUtils.cpp
    track_property_callback_impl.cpp
    ui_element_helpers.cpp
    VisUtils.cpp
    VolumeMap.cpp
    win-systemtime.cpp
    win32_dialog.cpp
    win32_misc.cpp
    window_placement_helper.cpp
    WindowPositionUtils.cpp
    writer_wav.cpp
)

# add pch
target_precompile_headers(foobar2000_helpers PRIVATE StdAfx.h)

# use C++ 17
target_compile_features(foobar2000_helpers PRIVATE cxx_std_17)

# add include directory as INTERFACE so dependents can import this lib with
# #import <helpers/...>
target_include_directories(foobar2000_helpers INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}/..)

# copied from foobar2000_sdk_helpers.cvxproj
# "<WarningLevel>Level3</WarningLevel>" = /W3
# "<CharacterSet>Unicode</CharacterSet>" = /DUNICODE and /D_UNICODE
# "<TreatSpecificWarningsAsErrors>4715</TreatSpecificWarningsAsErrors>" = /we4715
target_compile_options(foobar2000_helpers PRIVATE $<$<CXX_COMPILER_ID:MSVC>:/W3 /DUNICODE /D_UNICODE /we4715>)

# add WTL headers
target_link_libraries(foobar2000_helpers PUBLIC wtl)

# add pcf
target_link_libraries(foobar2000_helpers PUBLIC pfc)

# add SDK
target_link_libraries(foobar2000_helpers PUBLIC foobar2000_SDK)