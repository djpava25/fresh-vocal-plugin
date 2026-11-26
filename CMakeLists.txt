cmake_minimum_required(VERSION 3.22)
project(FreshVocal3 VERSION 1.0.0)

add_subdirectory(JUCE)

juce_add_plugin(FreshVocal3
    COMPANY_NAME "djpava25"
    IS_SYNTH FALSE
    NEEDS_MIDI_INPUT FALSE
    NEEDS_MIDI_OUTPUT FALSE
    IS_MIDI_EFFECT FALSE
    EDITOR_WANTS_KEYBOARD_FOCUS FALSE
    COPY_PLUGIN_AFTER_BUILD FALSE
    PLUGIN_MANUFACTURER_CODE Djpv
    PLUGIN_CODE Frv3
    FORMATS VST3
    PRODUCT_NAME "Fresh Vocal 3"
)

target_sources(FreshVocal3 PRIVATE
    Source/PluginProcessor.cpp
    Source/PluginProcessor.h
)

target_compile_definitions(FreshVocal3 PUBLIC
    JUCE_WEB_BROWSER=0
    JUCE_USE_CURL=0
    JUCE_VST3_CAN_REPLACE_VST2=0
)

target_link_libraries(FreshVocal3 PRIVATE
    juce::juce_audio_utils
    juce::juce_dsp
PUBLIC
    juce::juce_recommended_config_flags
    juce::juce_recommended_lto_flags
    juce::juce_recommended_warning_flags
)
