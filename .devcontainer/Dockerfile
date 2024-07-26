FROM pengzhile/new-api:latest

# 安装必要的工具
RUN apt-get update && apt-get install -y \
    curl \
    sudo \
    && rm -rf /var/lib/apt/lists/*

# 设置工作目录
WORKDIR /app

# 创建数据目录
RUN mkdir -p /home/ubuntu/data/new-api && chmod -R 777 /home/ubuntu/data/new-api

# 下载并安装 cloudflared
RUN curl -L --output cloudflared.deb https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb \
    && dpkg -i cloudflared.deb \
    && rm cloudflared.deb

# 暴露应用程序端口
EXPOSE 3000

# 设置默认命令
CMD ["./api"]
