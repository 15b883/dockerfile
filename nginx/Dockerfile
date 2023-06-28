FROM nginx:1.25

ENV TIMEZONE=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TIMEZONE /etc/localtime && echo $TIMEZONE > /etc/timezone

COPY web/* /opt/web/
COPY cfg/web.conf /etc/nginx/sites-enabled/
COPY cfg/nginx.conf /etc/nginx/

EXPOSE 8080

ENTRYPOINT ["nginx", "-g","daemon off;"]