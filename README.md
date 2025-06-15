# CPP Libraries Builds - Prebuilt C++ Libraries Collection

A structured collection of commonly used C++ libraries, built and ready for integration into modern C++ projects.

## Included Libraries:
- [**openssl v3.5.0**](https://github.com/openssl/openssl) – TLS/SSL and cryptographic functions  
- [**libcurl v8.14.1**](https://github.com/curl/curl) – multi-protocol URL transfer library  
- [**zlib v1.3.1**](https://github.com/madler/zlib) – compression library  
- [**brotli v1.1.0**](https://github.com/google/brotli) – compression algorithm developed by Google  
- [**jsoncpp v1.9.6**](https://github.com/open-source-parsers/jsoncpp) – JSON parser/writer for C++  

## Usage:
These libraries are ready to use in your projects without the need to build them yourself.

### 1. Include the headers
Each library provides a standard include directory.  
For example:
```cpp
#include <OpenSSL/ssl.h>
#include <cURL/curl.h>
#include <zLib/zlib.h>
#include <Brotli/decode.h>
#include <JsonCPP/json.h>
```

### 2. Link the static `.lib` files
Each library provides a prebuilt `.lib` file under its respective `/lib/x64` directory.  
You can link them in your project settings or using CMake.

**Example:**
```
CPPLibrariesBuilds
├── openssl\
│   ├── include\OpenSSL\*.h
│   └── lib\x64\libssl.lib, libcrypto.lib
├── libcurl\
│   ├── include\cURL\*.h
│   └── lib\x64\libcurl.lib
├── zlib\
│   ├── include\zLib\*.h
│   └── lib\x64\zlib.lib
├── brotli\
│   ├── include\Brotli\*.h
│   └── lib\x64\brotlicommon.lib, brotlidec.lib, brotlienc.lib
├── jsoncpp\
│   ├── include\JsonCPP\*.h
│   └── lib\x64\jsoncpp.lib
```

### 3. Linker settings
In Visual Studio:
- Go to **Project Properties > Linker > Input > Additional Dependencies**
- Add the required `.lib` files (e.g., `libssl.lib`, `libcrypto.lib`, `libcurl.lib`, etc.)
- Add the `lib\x64` paths to **Linker > General > Additional Library Directories**
- Add the `include\` paths to **C/C++ > General > Additional Include Directories**

Or, in **CMake**:
```cmake
target_include_directories(MyApp PRIVATE C:/openssl/include" "C:/libcurl/include")
target_link_directories(MyApp PRIVATE "C:/openssl/lib/x64" "C:/libcurl/lib/x64")
target_link_libraries(MyApp PRIVATE libssl libcrypto libcurl)
```

## Notes:
- Only static builds are provided. No shared (DLL) builds are included.
- This project intentionally excludes 32-bit (x86) builds to promote modern, 64-bit software development practices.
- All builds are optimized for x64 architecture, ensuring better performance, memory usage, and future-proofing.

## License:
- All original content in this repository (scripts, documentation, structure) is licensed under the MIT License.

## Author:
[Furkan Kadir Güzeloğlu](https://github.com/furkankadirguzeloglu)

## Acknowledgements:
- Thanks to the maintainers of [openssl](https://github.com/openssl/openssl), [libcurl](https://github.com/curl/curl), [zlib](https://github.com/madler/zlib), [brotli](https://github.com/google/brotli), and [jsoncpp](https://github.com/open-source-parsers/jsoncpp).
- Inspired by the need to streamline dependency management in C++ development environments.
