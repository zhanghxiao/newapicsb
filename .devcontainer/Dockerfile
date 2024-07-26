# 使用 pengzhile/new-api:latest 镜像
FROM pengzhile/new-api:latest

# 设置工作目录
WORKDIR /app

# 尝试安装 curl 和 sudo
RUN (command -v apk && apk add --no-cache curl sudo) || \
    (command -v apt-get && (apt-get update && apt-get install -y curl sudo && rm -rf /var/lib/apt/lists/*)) || \
    echo "Unable to install packages. Manual installation may be required."

# 创建数据目录
RUN mkdir -p /home/ubuntu/data/new-api && chmod -R 777 /home/ubuntu/data/new-api

# 暴露应用程序端口
EXPOSE 3000

# 设置默认命令（使用原镜像的入口点）
CMD ["./api"]
