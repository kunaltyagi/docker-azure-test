FROM ubuntu:18.04

RUN apt-get update && \
    apt-get install -y \
    build-essential cmake git ninja-build python && \
    rm -fr /var/lib/apt/lists/*
RUN cd root && \
    git clone --depth=1 git://github.com/llvm/llvm-project && \
    cd llvm-project && \
    mkdir build && cd build && \
    cmake -GNinja \
          -DCMAKE_BUILD_TYPE=Release \
          -DLLVM_ENABLE_PROJECTS="clang;libcxx;libcxxabi;lld;compiler-rt" \
          -DLLVM_ENABLE_BACKTRACES=OFF \
          -DLLVM_ENABLE_WARNINGS=OFF \
          -DLLVM_INCLUDE_TESTS=OFF \
          -DLLVM_INCLUDE_UTILS=OFF \
          -DLLVM_INCLUDE_EXAMPLES=OFF \
          -DLLVM_INCLUDE_DOCS=OFF \
          -DLLVM_ENABLE_LTO=Thin \
          -DCLANG_ENABLE_ARCMT=OFF \
          -DCMAKE_CXX_FLAGS="-fvisibility=hidden" \
          ../llvm && \
    ninja && \
    ninja install && \
    rm -fr /root/
