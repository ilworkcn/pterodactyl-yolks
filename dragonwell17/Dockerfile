#设置初始镜像
FROM registry.cn-hangzhou.aliyuncs.com/dragonwell/dragonwell:17.0.3.0.3.7-GA_alpine_x86_64

LABEL       author="iLwork.CN > Ice_Ling" maintainer="iceling@ilwork.cn"

LABEL       org.opencontainers.image.source="AliBaba Dragonwell 17"
LABEL       org.opencontainers.image.licenses=MIT


#安装一些基础软件
RUN apk add --no-cache --update curl ca-certificates openssl git tar bash sqlite fontconfig \
    && adduser --disabled-password --home /home/container container
    
    
#COPY运行脚本并设置权限
COPY        ./entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh \ 
    && chown container /entrypoint.sh
  
USER        container
ENV         USER=container HOME=/home/container 

WORKDIR     /home/container

CMD         [ "/bin/bash", "/entrypoint.sh" ]
