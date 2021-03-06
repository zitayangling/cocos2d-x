
if(WINDOWS)
  set(PLATFORM_LINK websockets)
elseif(LINUX)
  set(PLATFORM_LINK websockets ssl crypto)
elseif(ANDROID)
  set(PLATFORM_LINK websockets)
else()
  set(PLATFORM_LINK websockets)
endif()

if(ANDROID)
  set(COCOS_NETWORK_SRC
    network/HttpClient-android.cpp
    network/SocketIO.cpp
    network/WebSocket.cpp
    network/CCDownloader.cpp
    network/CCDownloader-android.cpp
    network/Uri.cpp
  )
elseif(MACOSX OR IOS)
  set(COCOS_NETWORK_SRC
    network/CCDownloader-apple.mm
    network/HttpClient.cpp
    network/SocketIO.cpp
    network/WebSocket.cpp
    network/CCDownloader.cpp
    network/CCDownloader-curl.cpp
    network/Uri.cpp
  )
else()
  set(COCOS_NETWORK_SRC
    network/HttpClient.cpp
    network/SocketIO.cpp
    network/WebSocket.cpp
    network/CCDownloader.cpp
    network/CCDownloader-curl.cpp
    network/Uri.cpp
  )
endif()

if(WINDOWS)
  set(COCOS_NETWORK_LINK 
    libcurl_imp 
    ${PLATFORM_LINK}
  )
elseif(ANDROID)
  set(COCOS_NETWORK_LINK
    ${PLATFORM_LINK} 
  )
else()
  set(COCOS_NETWORK_LINK 
    curl
    ${PLATFORM_LINK} 
  )
endif()
