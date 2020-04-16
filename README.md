# cpprest-x86_x64
Native Visual Studio solution/project files to compile on Windows x86/x64/Debug/Release

# Background #
cpprest uses CMake. The solution/project files are not flexible, does
not identify dependencies like websocketpp, openssl, brotli etc. These
project files will allow people to compile for x64/x86/Release/Debug
along with using natively compiled libraries like websocketpp etc.

# Installation #

  * git clone [cpprestsdk, tested w/ v2.10.15](https://github.com/microsoft/cpprestsdk) into a local folder.
  * git clone [cpprest-x86_x64](https://github.com/sridharb1/cpprest-x86_x64) into another folder. 
  * Copy the contents of the build folder of cpprest-x86_x64 into the cpprestsdk tree.
  * cpprestsdk depends upon other libraries. Those libraries and how
    to get them to compile with Visual Studio is detailed in the
    section below.

# Note #

To compile cpprestsdk, you need 

  * [zlib, tested w/ v1.2.11](https://github.com/madler/zlib)
  * Use my [zlib-x86_x64](https://github.com/sridharb1/zlib-x86_x64) to compile zlib on Windows.
  * [OpenSSL, tested w/ v1.1.1g-DEV](https://github.com/openssl/openssl)
  * Use my [openssl-x86_x64](https://github.com/sridharb1/openssl-x86_x64) to compile openssl on Windows.
  * [websocketpp, tested w/ v0.8.1](https://github.com/zaphoyd/websocketpp)
  * Use my [websocketpp-x86_x64](https://github.com/sridharb1/websocketpp-x86_x64) to compile on Windows.
  * [brotli, tested w/ v1.0.7+](https://github.com/google/brotli)
  * Use my [brotli-x86_x64](https://github.com/sridharb1/brotli-x86_x64) to compile on Windows
  * boost c++ libraries. See how to fetch and compile boost below.

## Fetching and compiling boost ##

  * Get the latest boost (I used v1.72). Instructions available at [Boost with git](https://github.com/boostorg/wiki/wiki/Getting-Started%3A-Overview)
  * My projects follow this heirarchy. I keep all the projects in the
    same level, for e.g. zlib is in E:\Projects\zlib, websocketpp is
    in E:\Projects\websocketpp etc. boost sources would be in
    E:\Projects\Boost.
  * The last command below installs boost headers and libraries in
    E:\Boost. These projects refer to this relative path (i.e. the
    installed boost is in one level higher than the Projects folder).
  * This command uses toolset=msvc-14.2 (aka VS 2019). As newer
    versions come, please adjust accordingly. Please refer to [Boost Toolsets](https://boostorg.github.io/build/manual/develop/index.html).
  * This builds static boost libraries for x86/x64/Release/Debug with
    CRT DLL runtimes. This is the combination that I use in all my
    projects.

  ``` shell
  git clone --recursive https://github.com/boostorg/boost.git
  cd boost
  .\bootstrap
  .\b2 -a -j8 toolset=msvc-14.2 architecture=x86 address-model=32,64 --prefix=E:\Boost variant=debug,release link=static runtime-link=shared threading=multi install
  ```
