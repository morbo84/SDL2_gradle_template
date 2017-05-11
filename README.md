NOTE: in order to build SDL2 for Android, you have to:

1 - download SDL2 to `app/src/main/cpp/SDL`, or create a symlink to another `SDL` folder in your machine
2 - apply the patch `app/src/main/cpp/patches/SDL2_CMakeLists.patch` to `app/src/main/cpp/SDL/CMakeLists.txt`:

	patch app/src/main/cpp/SDL/CMakeLists.txt app/src/main/cpp/patches/SDL2_CMakeLists.patch

Note that this will modify your `SDL/CMakeLists.txt` file


Credits
====

- The `main.cpp` file is from [stephen47](https://github.com/stephen47)'s [android-sdl2-gradle-template](https://github.com/stephen47/android-sdl2-gradle-template)
- The [SDL](https://www.libsdl.org/) project of course; the `SDLActivity.java` file, in particular, comes (slightly adapted) from their Android template project


Known issues and limitations
====

Currently, this project template support just a single ABI at a time; the problem I has not been able to solve is how to select the correct `libsdl` folder depending on the ABI name, so it's hardcoded for a single ABI.