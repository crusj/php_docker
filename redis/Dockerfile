FROM redis

##### 阿里源
RUN sed -i "s/deb.debian.org/mirrors.aliyun.com/g;s/security.debian.org/mirrors.aliyun.com/g" /etc/apt/sources.list  \
&&  cd /etc/apt/sources.list.d && if [ "$(ls)" ]; then  ls | xargs  sed -i "s/deb.debian.org/mirrors.aliyun.com/g;s/security.debian.org/mirrors.aliyun.com/g"; fi \
&&  apt update

RUN apt install -y vim telnet net-tools
