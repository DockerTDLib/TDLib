ARG dname="arm64v8"
FROM ${dname}/golang:buster
RUN apt update
RUN apt upgrade -y
RUN apt install make git zlib1g-dev libssl-dev gperf php-cli cmake clang libc++-dev libc++abi-dev -y
RUN git clone https://github.com/tdlib/td.git && \
    cd td && \
    mkdir build && \
    cd build && \
    CXXFLAGS="-stdlib=libc++" CC=/usr/bin/clang CXX=/usr/bin/clang++ cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX:PATH=/usr/local .. && \
    cmake --build . --target install -j $(nproc)