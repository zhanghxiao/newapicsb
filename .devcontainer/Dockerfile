FROM pengzhile/new-api:latest

# 安装 curl 和其他必要的工具
RUN apk update && apk add --no-cache curl && \
    rm -rf /var/cache/apk/*

# 安装 cloudflared
RUN curl -L https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64 -o cloudflared && \
    chmod +x cloudflared && \
    mv cloudflared /usr/local/bin/

# 设置工作目录
WORKDIR /app

# 暴露端口
EXPOSE 3000

# 启动命令将在 tasks.json 中定义
CMD ["tail", "-f", "/dev/null"]
