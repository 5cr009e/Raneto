# LLVM writeup
LLVM froentend tutorials for ocaml, haskell are heavily outdated. The community focus on c++ interfaces which is a better start point.

## [Kaleidoscope](https://llvm.org/docs/tutorial/MyFirstLanguageFrontend/index.html)
A great tutorial for learning frontend.

## Setup CMake Env
"llvm-config" is a bad way to automate compilation. Set up cmake project with the following tempalte

```
cmake_minimum_required(VERSION 3.4.3)
project(Toy)

find_package(LLVM REQUIRED CONFIG)

message(STATUS "Found LLVM ${LLVM_PACKAGE_VERSION}")
message(STATUS "Using LLVMConfig.cmake in: ${LLVM_DIR}")

# Set your project compile flags.
# E.g. if using the C++ header files
# you will need to enable C++11 support
# for your compiler.

include_directories(${LLVM_INCLUDE_DIRS})
add_definitions(${LLVM_DEFINITIONS})

# Now build our tools
add_executable(toy toy.cpp)

# Find the libraries that correspond to the LLVM components
# that we wish to use
llvm_map_components_to_libnames(llvm_libs support core irreader)

# Link against LLVM libraries
target_link_libraries(toy ${llvm_libs})⏎
```