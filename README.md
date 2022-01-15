# WebView2SampleCMake
This repository contains a Win32 Getting Started app that builds with Cmake.
# Prerequisites
1. [CMake](https://cmake.org/)
2. [WebView2 Runtime](https://developer.microsoft.com/microsoft-edge/webview2)
3. Network connection
# Build
```
cmake
cmake --build .
```
or set FETCHCONTENT_QUIET=OFF to print deps download info. that is:
```
cmake -DFETCHCONTENT_QUIET=OFF
cmake --build .
```
