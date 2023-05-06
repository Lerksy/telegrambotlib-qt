# Generated from telegrambotlib-qt.pri.

cmake_minimum_required(VERSION 3.16)
project(telegrambotlib-qt VERSION 1.0 LANGUAGES CXX)

set(CMAKE_INCLUDE_CURRENT_DIR ON)

set(CMAKE_AUTOMOC ON)

find_package(QT NAMES Qt5 Qt6 REQUIRED COMPONENTS Core)
find_package(Qt${QT_VERSION_MAJOR} REQUIRED COMPONENTS Gui Network)

add_library(${PROJECT_NAME} STATIC
    modules/httpserver/httpserver.cpp modules/httpserver/httpserver.h
    modules/sslserver/sslserver.cpp modules/sslserver/sslserver.h
    src/jsonhelper.cpp src/jsonhelper.h
    src/telegrambot.cpp src/telegrambot.h
    src/telegramdatainterface.h
    src/telegramdatastructs.h
)

target_include_directories(${PROJECT_NAME} PUBLIC
    modules/httpserver
    modules/sslserver
    src
)

add_subdirectory(vendor/qdelegate)

target_link_libraries(${PROJECT_NAME} PUBLIC
    Qt::Core
    Qt::Network
    QDelegate
)
