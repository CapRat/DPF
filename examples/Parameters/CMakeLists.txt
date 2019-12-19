cmake_minimum_required (VERSION 2.8)
project(Parameters)


BUILD_LV2(TARGET Parameters UI_BACKEND OPENGL
    SOURCES ExamplePluginParameters.cpp
    UI_SOURCES ExampleUIParameters.cpp
    INCLUDE_DIRECTORIES "./")

BUILD_VST2(TARGET ParametersVst UI_BACKEND OPENGL
    SOURCES ExamplePluginParameters.cpp ExampleUIParameters.cpp
    INCLUDE_DIRECTORIES "./")

if(DSSI_SUPPORT)
BUILD_DSSI(TARGET Parameters-DSSI UI_BACKEND OPENGL
    SOURCES ExamplePluginParameters.cpp
    UI_SOURCES ExampleUIParameters.cpp
    INCLUDE_DIRECTORIES "./")
endif(DSSI_SUPPORT)

if(DPF_INSTALL)
    INSTALL(TARGETS ParametersVst DESTINATION lib/vst)
    INSTALL(TARGETS Parameters Parameters_ui DESTINATION lib/lv2/Parameters.lv2)
    #When generating files for lv2 plugin, the generated files are saved as ${LV2PLUGINNAME}_TTL_FILES
    INSTALL(FILES ${Parameters_TTL_FILES} DESTINATION lib/lv2/Parameters.lv2)
    if(DSSI_SUPPORT)
        INSTALL(TARGETS Parameters-DSSI Parameters-DSSI_ui DESTINATION lib/dssi)
    endif(DSSI_SUPPORT)
endif(DPF_INSTALL)