

在Dockerfile里添加一个可以检查的healthcheck接口，你可以使用Docker提供的`HEALTHCHECK`指令。

此指令告诉Docker如何测试容器是否仍在正常运行。

`HEALTHCHECK`有两个选项：

- `--interval=DURATION` (默认值：30s)：定义Docker在进行健康状况检查之间等待的时间长度。
- `--timeout=DURATION` (默认值：30s)：定义Docker等待健康状况检查完成的最长时间。
- `--start-period=DURATION` (默认值：0s)：定义容器启动后Docker应等待多长时间，然后才开始进行正常的健康检查。
- `--retries=N` (默认值：3)：定义Docker在视为容器不健康之前，连续几次健康状况检查失败。



```dockerfile
FROM nginx:alpine

# 配置nginx，在/health路径返回200
RUN echo 'server { listen 80; location /health { return 200 "Healthy"; } }' > /etc/nginx/conf.d/default.conf

EXPOSE 80

# 使用curl检查/health路径，查看服务器是否在运行
HEALTHCHECK CMD curl --fail http://localhost:80/health || exit 1
```





```
docker build -t healthcheck:v1 .


docker run -itd -p 80:80 --name healthcheck1 healthcheck:v1


curl localhost:80/health
```

