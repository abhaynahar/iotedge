ARG base_tag=3.1.4-bionic-arm32v7
FROM mcr.microsoft.com/dotnet/core/aspnet:${base_tag}

RUN apt-get update && \
    apt-get install -y libsnappy1v5 && \
    ln -s /lib/arm-linux-gnueabihf/libdl.so.2 /usr/lib/arm-linux-gnueabihf/libdl.so && \
    ln -s /lib/arm-linux-gnueabihf/libc.so.6 /usr/lib/arm-linux-gnueabihf/libc.so && \
    rm -rf /var/lib/apt/lists/*

# create a user to allow agent to optionally run as non-root
ARG EDGEAGENTUSER_ID=1000	
RUN useradd -ms /bin/bash -u ${EDGEAGENTUSER_ID} edgeagentuser 

COPY librocksdb.so /usr/lib/