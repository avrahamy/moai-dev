cmake_minimum_required ( VERSION 2.8.5 )
project ( moai )

#
# Multi-platform flags
#
set ( BUILD_OSX         FALSE  CACHE STRING "Build Moai SDK for MacOSX"      FORCE )
set ( BUILD_LINUX       TRUE CACHE STRING "Build Moai SDK for Linux"       FORCE )
set ( BUILD_WIN32       FALSE CACHE STRING "Build Moai SDK for Windows"     FORCE )
set ( BUILD_IOS         FALSE CACHE STRING "Build Moai SDK for iOS"         FORCE )
set ( BUILD_ANDROID     FALSE CACHE STRING "Build Moai SDK for Android"     FORCE )
set ( BUILD_BLACKBERRY  FALSE CACHE STRING "Build Moai SDK for BlackBerry"  FORCE )
set ( BUILD_FLASCC      FALSE CACHE STRING "Build Moai SDK for FlasCC"      FORCE )

#
# Optional modules
#
set ( MOAI_BOX2D          FALSE CACHE STRING "Build Moai SDK with Box2D Support" FORCE )
set ( MOAI_CHIPMUNK       FALSE CACHE STRING "Build Moai SDK with Chipmunk Support" FORCE )
set ( MOAI_EXPAT          FALSE CACHE STRING "Build Moai SDK with Lua extensions Support" FORCE )
set ( MOAI_FREETYPE       FALSE CACHE STRING "Build Moai SDK with FreeType Support" FORCE )
set ( MOAI_JSON           FALSE CACHE STRING "Build Moai SDK with JSON Support" FORCE )
set ( MOAI_JPG            FALSE CACHE STRING "Build Moai SDK with Jpg Support" FORCE )
set ( MOAI_LUAEXT         FALSE CACHE STRING "Build Moai SDK with Lua extensions Support" FORCE )
set ( MOAI_OGG            FALSE CACHE STRING "Build Moai SDK with Png Support" FORCE )
set ( MOAI_OPENGLES1      FALSE CACHE STRING "Build Moai SDK with OpenGL ES 1.0 Support" FORCE )
set ( MOAI_SQLITE3        FALSE CACHE STRING "Build Moai SDK with SQLite3 Support" FORCE )
set ( MOAI_TINYXML        FALSE CACHE STRING "Build Moai SDK with TinyXML Support" FORCE )
set ( MOAI_PNG            FALSE CACHE STRING "Build Moai SDK with Png Support" FORCE )
set ( MOAI_SFMT           FALSE CACHE STRING "Build Moai SDK with SFMT Support" FORCE )

set ( MOAI_CURL           FALSE CACHE STRING "Build Moai SDK with CURL Support" FORCE )
set ( MOAI_OPENSSL        FALSE CACHE STRING "Build Moai SDK with OpenSSL Support" FORCE )

# TODO: Fix build in MacOSX
# set ( MOAI_CRYPTO         FALSE CACHE STRING "Build Moai SDK with Lua extensions Support" FORCE )

#
# Moai SDK Extensions
#
set ( MOAI_UNTZ           FALSE CACHE STRING "Build Moai SDK with Untz Support" FORCE )


#
# Set as debug
#
set ( DEBUG OFF )

#
# Build testing code
#
set ( TESTING OFF )

if ( DEBUG )
  set ( CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -O4")
  set ( CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O4")
endif ( DEBUG )

add_subdirectory ( third-party )

add_subdirectory ( zlcore )
add_subdirectory ( uslscore )
add_subdirectory ( moai-core )
add_subdirectory ( moaiext-server )

if ( BUILD_OSX )
  add_subdirectory ( moai-host-glut )
endif ( BUILD_OSX )

add_subdirectory ( http-host )

add_subdirectory ( untz )
add_subdirectory ( moai-untz )
