Motivation
====

Android and it's development tools are constantly evolving and lot of things have changed since the beginning. Gradle (the build toolkit used by Android Studio projects) has become the de-facto standard build toolkit for Android projects and [since Android Studio 2.2 you can manage native code from whitin the IDE](https://developer.android.com/studio/projects/add-native-code.html). So, it seemed reasonable to me to try to set up a Gradle project for building (and debugging) SDL2 apps for Android.

The only similar project I've been able to find is [this](https://github.com/stephen47/android-sdl2-gradle-template), but it makes use of the Android experimental plugin for Gradle, and it's not primarily intended for Android Studio compatibility.

Installation
====

To have a working SDL Gradle Android project, you need to:

0) download either the Android Sdk packaged with Android Studio or the _basic Android command line tools_, and install these `ndk-bundle` package
1) clone this repo
2) either set the `ANDROID_HOME` and `ANDROID_NDK_HOME` environment variables to point where your Android SDK and NDK are installed to, or create a `local.properties` file in the root folder of the project and specifies SDK and NDK paths, like this:

		sdk.dir=/path/to/android/sdk
		ndk.dir=/path/to/android/sdk/ndk-bundle

3) download SDL2 to `app/src/main/cpp/SDL`, or create a symlink pointing to an `SDL` intallation present in your machine
4) apply the patch `app/src/main/cpp/patches/SDL2_CMakeLists.patch` to `app/src/main/cpp/SDL/CMakeLists.txt`:

		patch app/src/main/cpp/SDL/CMakeLists.txt app/src/main/cpp/patches/SDL2_CMakeLists.patch

	**Note** that this will modify your `SDL/CMakeLists.txt` file
5) from the root directory of the project, run `./gradlew assemble[Debug|Release]`, or `./gradlew install[Debug|Release]`, to build or install the _apk_ (Gradle will download and install all the stuff you miss to build the project, possibly the `cmake` package, the build-tools or the target platform, so **it may take some time**)


Credits
====

- The `main.cpp` file is from [stephen47](https://github.com/stephen47)'s [android-sdl2-gradle-template](https://github.com/stephen47/android-sdl2-gradle-template)
- The [SDL](https://www.libsdl.org/) project of course; the `SDLActivity.java` file, in particular, comes (slightly adapted) from their Android template project


Limitations
====

Currently, this project template support just a single ABI at a time; the problem I has not been able to solve is how to select the correct `libsdl` folder depending on the ABI name, so it's hardcoded for a single ABI.

Known issues
====
Android Sdk's Cmake may have OpenSSL version issues with some linux distributions;
in particular, it wasn't able to use `libssl.so.1.0.0` and `libcrypto.so.1.0.0` shipped with the system.

To solve the problem, I had to download and build an older revision of _OpenSSL 1.0.0_, and replace the symbolic links in `/usr/lib/` of course.