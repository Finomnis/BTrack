add_library (
    BTrack STATIC
    BTrack.cpp
    BTrack.h
    OnsetDetectionFunction.cpp
    OnsetDetectionFunction.h
    CircularBuffer.h
)

source_group (Source src)

target_compile_definitions (BTrack PUBLIC -DUSE_KISS_FFT)
target_include_directories (BTrack PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/src)
target_include_directories (BTrack PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/../libs/kiss_fft130)
target_include_directories (BTrack PRIVATE /opt/homebrew/include)

# Link against libsamplerate
target_link_libraries(BTrack PRIVATE SampleRate::samplerate)

# ALIAS to use if BTrack is included from other project with add_subdirectory()
add_library(BTrack::BTrack ALIAS BTrack)
