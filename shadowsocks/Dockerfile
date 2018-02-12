# Version: 0.0.1
FROM ubuntu:16.04
MAINTAINER zizhazhu "zizhazhu@gmail.com"
RUN apt-get update
RUN apt-get install -y python
RUN apt-get install -y python-pip
RUN pip install shadowsocks
COPY shadowsocks.json /etc/shadowsocks.json
CMD ["ssserver", "-c", "/etc/shadowsocks.json"]
EXPOSE 51556


