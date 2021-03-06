# Part of Beast

GroupSources(extras/beast beast)
GroupSources(include/beast beast)
GroupSources(test/websocket "/")

add_executable (websocket-tests
    ${BEAST_INCLUDES}
    ../../extras/beast/unit_test/main.cpp
    websocket_async_echo_peer.hpp
    websocket_sync_echo_peer.hpp
    error.cpp
    option.cpp
    rfc6455.cpp
    stream.cpp
    teardown.cpp
    detail/frame.cpp
    detail/mask.cpp
    detail/stream_base.cpp
    detail/utf8_checker.cpp
)

if (NOT WIN32)
    target_link_libraries(websocket-tests ${Boost_LIBRARIES} Threads::Threads)
endif()

add_executable (websocket-echo
    ${BEAST_INCLUDES}
    websocket_async_echo_peer.hpp
    websocket_sync_echo_peer.hpp
    websocket_echo.cpp
)

if (NOT WIN32)
    target_link_libraries(websocket-echo ${Boost_LIBRARIES} Threads::Threads)
endif()
