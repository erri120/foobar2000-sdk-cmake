add_library(foobar2000_SDK STATIC)

target_sources(foobar2000_SDK PRIVATE
    abort_callback.cpp
    advconfig.cpp
    album_art.cpp
    app_close_blocker.cpp
    audio_chunk_channel_config.cpp
    audio_chunk.cpp
    cfg_var_legacy.cpp
    cfg_var.cpp
    chapterizer.cpp
    commandline.cpp
    commonObjects.cpp
    completion_notify.cpp
    componentversion.cpp
    config_io_callback.cpp
    config_object.cpp
    configStore.cpp
    console.cpp
    dsp_manager.cpp
    dsp.cpp
    file_cached_impl.cpp
    file_info_const_impl.cpp
    file_info_impl.cpp
    file_info_merge.cpp
    file_info.cpp
    file_operation_callback.cpp
    filesystem_helper.cpp
    filesystem.cpp
    foosort.cpp
    foosortstring.cpp
    fsItem.cpp
    guids.cpp
    hasher_md5.cpp
    image.cpp
    input_file_type.cpp
    input.cpp
    link_resolver.cpp
    main_thread_callback.cpp
    mainmenu.cpp
    mem_block_container.cpp
    menu_helpers.cpp
    menu_item.cpp
    menu_manager.cpp
    metadb_handle_list.cpp
    metadb_handle.cpp
    metadb.cpp
    output.cpp
    packet_decoder.cpp
    playable_location.cpp
    playback_control.cpp
    playlist_loader.cpp
    playlist.cpp
    popup_message.cpp
    preferences_page.cpp
    replaygain_info.cpp
    replaygain.cpp
    service.cpp
    stdafx.cpp
    tag_processor_id3v2.cpp
    tag_processor.cpp
    threaded_process.cpp
    titleformat.cpp
    track_property.cpp
    ui_element.cpp
    ui.cpp
    utility.cpp
)

# add pch
target_precompile_headers(foobar2000_SDK PRIVATE foobar2000-sdk-pch.h)

# use C++ 17
target_compile_features(foobar2000_SDK PRIVATE cxx_std_17)

# copied from foobar2000_SDK.cvxproj
# "<WarningLevel>Level3</WarningLevel>" = /W3
# "<CharacterSet>Unicode</CharacterSet>" = /DUNICODE and /D_UNICODE
# "<TreatSpecificWarningsAsErrors>4715</TreatSpecificWarningsAsErrors>" = /we4715
target_compile_options(foobar2000_SDK PRIVATE $<$<CXX_COMPILER_ID:MSVC>:/W3 /DUNICODE /D_UNICODE /we4715>)

# add include directory as INTERFACE so dependents can import this lib with
# #import <SDK/...>
target_include_directories(foobar2000_SDK INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}/..)

# add pfc
target_link_libraries(foobar2000_SDK PUBLIC pfc)