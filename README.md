NOTE: in order to build SDL2 for Android, you have to:

1 - download SDL2 to `app/src/main/cpp/SDL`, or create a symlink to another `SDL` folder in your machine
2 - apply the patch `app/src/main/cpp/patches/SDL2_CMakeLists.patch` to `app/src/main/cpp/SDL/CMakeLists.txt`:

	patch app/src/main/cpp/SDL/CMakeLists.txt app/src/main/cpp/patches/SDL2_CMakeLists.patch

Note that this will modify your `SDL/CMakeLists.txt` file