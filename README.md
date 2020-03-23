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

# Note #

To compile cpprestsdk, you need 

  * [zlib, tested w/ v1.2.11](https://github.com/madler/zlib)
  * [OpenSSL, tested w/ v1.1.1e-DEV](https://github.com/openssl/openssl)
  * You can use my [openssl-x86_x64](https://github.com/sridharb1/openssl-x86_x64) to compile openssl on Windows.
  * [websocketpp, tested w/ v0.8.1](https://github.com/zaphoyd/websocketpp)
  * Use my [websocketpp-x86_x64](https://github.com/sridharb1/websocketpp-x86_x64) to compile on Windows.
  * [brotli, tested w/ v1.0.7+](https://github.com/google/brotli)
  * Use my [brotli-x86_x64](https://github.com/sridharb1/brotli-x86_x64) to compile on Windows
