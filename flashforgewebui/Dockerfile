ARG BUILD_ARCH
FROM debian:bookworm-slim

ARG BUILD_ARCH
ENV DATA_DIR=/data

RUN apt-get update && apt-get install -y --no-install-recommends curl ca-certificates \
    && case "${BUILD_ARCH}" in \
         aarch64) BIN="flashforge-webui-linux-arm64" ;; \
         armv7)   BIN="flashforge-webui-linux-armv7" ;; \
         amd64)   BIN="flashforge-webui-linux-x64" ;; \
         *) echo "Unsupported arch: ${BUILD_ARCH}" && exit 1 ;; \
       esac \
    && curl -fL -o /usr/local/bin/flashforge-webui \
         "https://github.com/Parallel-7/FlashForgeWebUI/releases/download/v1.1.0/${BIN}" \
    && chmod +x /usr/local/bin/flashforge-webui \
    && apt-get purge -y curl && apt-get autoremove -y && rm -rf /var/lib/apt/lists/*

EXPOSE 3000
CMD ["/usr/local/bin/flashforge-webui", "--last-used"]
