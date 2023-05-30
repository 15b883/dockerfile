FROM python:3.10-slim

ENV TIMEZONE=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TIMEZONE /etc/localtime && echo $TIMEZONE > /etc/timezone

RUN pip3 install -i https://pypi.douban.com/simple/ -U pip
RUN pip3 config set global.index-url https://pypi.douban.com/simple/


ADD . /opt/python-serv


RUN pip3 install -r /opt/python-serv/requirements.txt


EXPOSE 8080

ENTRYPOINT ["python3", "/opt/python-serv/main.py"]