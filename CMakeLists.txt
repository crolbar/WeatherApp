cmake_minimum_required(VERSION 3.16)

project(WeatherApp)

set(CMAKE_AUTOMOC ON)

set(CMAKE_BUILD_WITH_INSTALL_RPATH TRUE)

find_package(Qt6 6.5 COMPONENTS Widgets Quick Gui QuickControls2 REQUIRED)

qt_standard_project_setup(REQUIRES 6.5)

qt_add_executable(WeatherApp
    WIN32 src/main.cpp # win32 to hide cmd in windows
)

qt_add_qml_module(WeatherApp
    URI wa
    VERSION 1.0
    QML_FILES
        qml/main.qml
)

install(TARGETS WeatherApp
    BUNDLE  DESTINATION .
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR})

target_link_libraries(WeatherApp
    PRIVATE Qt6::Widgets Qt6::Quick Qt6::Gui Qt6::QuickControls2
)
