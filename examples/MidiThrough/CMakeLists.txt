cmake_minimum_required (VERSION 2.8)
project(MidiThrogh)


build_vst2(TARGET MidiThroughVST UI_BACKEND NONE SOURCES "MidiThroughExamplePlugin.cpp" INCLUDE_DIRECTORIES "./")
build_lv2(TARGET MidiThrough UI_BACKEND NONE SOURCES "MidiThroughExamplePlugin.cpp" INCLUDE_DIRECTORIES "./")



if(DPF_INSTALL)
    install(TARGETS MidiThroughVST DESTINATION lib/vst)
    install(TARGETS MidiThrough DESTINATION lib/lv2/MidiThrough.lv2)
    #When generating files for lv2 plugin, the generated files are saved as ${LV2PLUGINNAME}_TTL_FILES
    install(FILES ${MidiThrough_TTL_FILES} DESTINATION lib/lv2/MidiThrough.lv2)
endif(DPF_INSTALL)
