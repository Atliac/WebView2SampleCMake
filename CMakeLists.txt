# CMakeList.txt : Top-level CMake project file, do global configuration
# and include sub-projects here.
#
cmake_minimum_required (VERSION 3.15) 
include(FetchContent)

project ("WebView2_CMake_Sample")

#### webview2 dependencies start

# Microsoft.Windows.ImplementationLibrary 
# The Windows Implementation Libraries (wil) were created to improve productivity and solve problems commonly seen by Windows developers. by: Microsoft WindowsImplementationLibraryTeam
FetchContent_Declare(
  wil
  URL  https://www.nuget.org/api/v2/package/Microsoft.Windows.ImplementationLibrary/1.0.211019.2
  URL_HASH SHA1=FB082B22DC30C11CCDB118A0EB9B8A32E99765B1
)
# Microsoft.Web.WebView2
FetchContent_Declare(
  webview2
  URL  https://www.nuget.org/api/v2/package/Microsoft.Web.WebView2/1.0.1072.54
  URL_HASH SHA1=aa8ae9db5015a9184011bb195efc5c8caa58a86b
)
FetchContent_MakeAvailable(wil webview2)

include_directories(SYSTEM "${wil_SOURCE_DIR}/include/")
include_directories(SYSTEM "${webview2_SOURCE_DIR}/build/native/include/")

if(CMAKE_SIZEOF_VOID_P EQUAL 8)
    set(PLATFORM "x64")
elseif(CMAKE_SIZEOF_VOID_P EQUAL 4)
    set(PLATFORM "x86")
endif()
link_libraries("${webview2_SOURCE_DIR}/build/native/${PLATFORM}/WebView2LoaderStatic.lib")

#### webview2 dependencies end
# Include sub-projects.
add_subdirectory ("WebView2SampleCMake")
