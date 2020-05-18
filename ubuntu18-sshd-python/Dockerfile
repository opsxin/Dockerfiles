FROM ubuntu:18.04
LABEL Maintainer="hsin" Version="1.0" Password="123456" \
    Description="Ubuntu 18, install ssh and python" 

RUN apt-get update && apt-get install -y \
    openssh-server python3 \
    && rm -rf /var/lib/apt/lists/*

# 添加 python3 软连接
RUN ln -s /usr/bin/python3 /usr/bin/python

RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN mkdir /var/run/sshd 

RUN echo 'root:123456' | chpasswd

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]

