FROM nginx:alpine

# 配置nginx，在/health路径返回200
RUN echo 'server { listen 80; location /health { return 200 "Healthy"; } }' > /etc/nginx/conf.d/default.conf

EXPOSE 80

# 使用curl检查/health路径，查看服务器是否在运行
HEALTHCHECK CMD curl --fail http://localhost:80/health || exit 1
