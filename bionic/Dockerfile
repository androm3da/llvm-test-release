
FROM ubuntu:18.04
VOLUME ['/tmp/']
RUN apt-get -qq update && apt-get -qq install -y --force-yes \
        build-essential subversion chrpath wget file python python-virtualenv \
        cmake ninja-build tar libxml2-dev libedit-dev swig python-dev libncurses5-dev

RUN cd /tmp && \
    wget --quiet https://raw.githubusercontent.com/llvm-mirror/llvm/master/utils/release/test-release.sh && \
    wget --quiet https://releases.llvm.org/8.0.0/clang+llvm-8.0.0-x86_64-linux-gnu-ubuntu-14.04.tar.xz && \
    tar xf clang+llvm-8.0.0-x86_64-linux-gnu-ubuntu-14.04.tar.xz && \
    chmod +x test-release.sh && \
    /usr/bin/env \
      CXX=/tmp/clang+llvm-8.0.0-x86_64-linux-gnu-ubuntu-14.04/bin/clang++ \
      CC=/tmp/clang+llvm-8.0.0-x86_64-linux-gnu-ubuntu-14.04/bin/clang \
        ./test-release.sh -release 9.0.0 -final \
        -triple x86_64-linux-gnu-ubuntu-18.04 \
        -use-ninja \
         || /bin/true
