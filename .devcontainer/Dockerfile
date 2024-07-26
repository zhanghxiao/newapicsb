FROM pengzhile/new-api:latest

# 尝试使用不同的包管理器安装 curl 和 sudo
RUN if command -v apk > /dev/null; then \
        apk add --no-cache curl sudo; \
    elif command -v apt-get > /dev/null; then \
        apt-get update && apt-get install -y curl sudo && rm -rf /var/lib/apt/lists/*; \
    elif command -v yum > /dev/null; then \
        yum install -y curl sudo && yum clean all; \
    else \
        echo "Unable to install packages. Please install curl and sudo manually."; \
    fi

# 设置工作目录
WORKDIR /app

# 创建数据目录
RUN mkdir -p /home/ubuntu/data/new-api && chmod -R 777 /home/ubuntu/data/new-api

# 下载 cloudflared（不安装，因为我们不确定包管理器）
RUN curl -L --output /usr/local/bin/cloudflared https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64 && \
    chmod +x /usr/local/bin/cloudflared

# 暴露应用程序端口
EXPOSE 3000

# 设置默认命令
CMD ["./api"]
