cmake_minimum_required(VERSION 3.4.1)

# sdl2 options for Android (inspired to the Android.mk file in SDL2 sources)
set(VIDEO_WAYLAND OFF CACHE BOOL "")
set(PTHREADS OFF CACHE BOOL "")
set(PULSEAUDIO OFF CACHE BOOL "")
set(DISKAUDIO OFF CACHE BOOL "")
set(VIDEO_DUMMY OFF CACHE BOOL "")
set(SDL_FILESYSTEM OFF CACHE BOOL "")
set(DEPENDENCY_TRACKING ON CACHE BOOL "")
set(EXTRA_CFLAGS "${EXTRA_CFLAGS} -DGL_GLEXT_PROTOTYPES")
set(EXTRA_LDFLAGS "-L${ANDROID_NDKDIR}/platforms/android-15/arch-arm/usr/lib -ldl -lGLESv1_CM -lGLESv2 -llog -landroid")
set(HAVE_GCC_FVISIBILITY OFF CACHE BOOL "")

add_subdirectory("SDL")
add_subdirectory("my_module")