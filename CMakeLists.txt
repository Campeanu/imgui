cmake_minimum_required(VERSION 3.8)

set(This ImGUI)

set(HEADERS
    imconfig.h
    imgui_internal.h
    imgui.h
    imstb_rectpack.h
    imstb_textedit.h
    imstb_truetype.h
)

set(SOURCES
    imgui_demo.cpp
    imgui_draw.cpp
    imgui_widgets.cpp
    imgui.cpp
)

include_directories(${SFML}/include)
link_directories(${SFML}/lib)

add_library(${This} STATIC ${SOURCES} ${HEADERS})

target_link_libraries(${This} PUBLIC
    sfml-graphics-d
    sfml-audio-d
    sfml-network-d
    sfml-window-d
    sfml-system-d
    opengl32
)

target_include_directories(${This} PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

set_target_properties(${This} PROPERTIES
    FOLDER Libraries
)
