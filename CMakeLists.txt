set(headers
    src/SocketIOclient.h
    src/WebSockets.h
    src/WebSockets4WebServer.h
    src/WebSocketsClient.h
    src/WebSocketsServer.h
    src/WebSocketsVersion.h
    src/libb64/cdecode_inc.h
    src/libb64/cencode_inc.h
    src/libsha1/libsha1.h
)

set(sources
    src/SocketIOclient.cpp
    src/WebSockets.cpp
    src/WebSocketsClient.cpp
    src/WebSocketsServer.cpp
    src/libb64/cdecode.c
    src/libb64/cencode.c
    src/libsha1/libsha1.c
)

set(dependencies
)

idf_component_register(
    INCLUDE_DIRS
        src
    SRCS
        ${headers}
        ${sources}
    REQUIRES
        ${dependencies}
)

target_compile_options(${COMPONENT_TARGET}
    PUBLIC
        -DESP32
        -DWEBSOCKETS_NETWORK_TYPE=NETWORK_ESP32
    PRIVATE
        -fstack-reuse=all
        -fstack-protector-all
        -Wno-unused-function
        -Wno-deprecated-declarations
        -Wno-missing-field-initializers
        -Wno-parentheses
)
