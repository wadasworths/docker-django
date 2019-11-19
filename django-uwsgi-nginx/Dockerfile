FROM ubuntu:16.04
FROM daocloud.io/python:3

MAINTAINER longfellow <longfellow_wang@163.com>

RUN apt-get update && \
    apt-get upgrade -y && \ 
    apt-get install -y \
	git \
	python3-dev \
	python3-setuptools \
	python3-pip \
	nginx \
	supervisor \
	libmysqlclient-dev && \
        pip3 install --upgrade -i https://pypi.doubanio.com/simple/ pip setuptools && \
  	rm -rf /var/lib/apt/lists/*

RUN pip3 install -i https://pypi.doubanio.com/simple/ uwsgi

# 环境变量
ENV PYTHONIOENCODING=utf-8

ENV MYSQL_DATABASE_NAME test
ENV EMAIL_HOST_USER longfellow_wang@163.com
ENV EMAIL_HOST_PASSWORD wxh#1234

RUN echo "daemon off;" >> /etc/nginx/nginx.conf
COPY nginx-app.conf /etc/nginx/sites-available/default
COPY supervisor-app.conf /etc/supervisor/conf.d/

COPY requirements.txt /home/docker/code/webproject/
RUN pip3 install -i https://pypi.doubanio.com/simple/ -r /home/docker/code/webproject/requirements.txt

# uwsgi.ini 及 uwsgi_params

COPY . /home/docker/code/


EXPOSE 80
CMD ["supervisord", "-n"] 
