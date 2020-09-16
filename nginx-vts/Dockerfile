FROM debian:10 AS base

RUN apt update \
    && apt install -y git wget build-essential \
    libpcre3 libpcre3-dev zlib1g-dev openssl libssl-dev

RUN cd /root && git clone git://github.com/vozlt/nginx-module-vts.git \
    && wget https://nginx.org/download/nginx-1.19.2.tar.gz -O /root/nginx.tgz \
    && tar zxvf /root/nginx.tgz \
    && cd /root/nginx-1.19.2 \
    && ./configure --prefix=/usr/local/nginx --user=www-data --group=www-data \
    --with-compat --with-file-aio --with-threads --with-http_addition_module \
    --with-http_auth_request_module --with-http_dav_module --with-http_flv_module \
    --with-http_gunzip_module --with-http_gzip_static_module --with-http_mp4_module \
    --with-http_random_index_module --with-http_realip_module --with-http_secure_link_module \
    --with-http_slice_module --with-http_ssl_module --with-http_stub_status_module \
    --with-http_sub_module --with-http_v2_module --with-mail --with-mail_ssl_module \
    --with-stream --with-stream_realip_module --with-stream_ssl_module \
    --with-stream_ssl_preread_module --add-module=/root/nginx-module-vts \
    && make && make install

FROM debian:10

LABEL maintainer="hsin@opsxin.com"
LABEL nginx-version="1.19.2"
LABEL nginx-export="http://IP:8080/nginx_status"

ENV TZ Asia/Shanghai

WORKDIR /usr/local/nginx

RUN apt update \
    && apt install -y --no-install-recommends \
    libpcre3 libpcre3-dev zlib1g-dev openssl libssl-dev \
    && rm -rf /var/lib/apt/lists/*

COPY --from=base /usr/local/nginx /usr/local/nginx

COPY nginx.conf /usr/local/nginx/conf/nginx.conf
COPY status.conf /usr/local/nginx/conf/conf.d/

EXPOSE 80 8080

CMD ["/usr/local/nginx/sbin/nginx"]
