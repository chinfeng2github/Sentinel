FROM openjdk:8-jre
##需要参数覆盖, spring编译会产生一个boot jar文件 和一个原始文件(xxx-plain.jar)
#ARG JAR_FILE_NAME
#ARG JAR_FILE=build/libs/${JAR_FILE_NAME}

MAINTAINER chinfeng.pan@gmail.com

RUN /bin/cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \&& echo 'Asia/Shanghai' >/etc/timezone

# /tmp 目录作为容器数据卷目录，SpringBoot内嵌Tomcat容器默认使用/tmp作为工作目录，任何向 /tmp 中写入的信息不会记录进容器存储层，从而保证容器存储层的无状态化
# 在宿主机的/var/lib/docker目录下创建一个临时文件并把它链接到容器中的/tmp目录
VOLUME /tmp

# 复制jar到镜像
COPY target/sentinel-dashboard.jar /app.jar

#ENTRYPOINT ["java","-jar","/app.jar"]
ENTRYPOINT ["java", "-Djava.security.egd=file:/dev/./urandom", "-jar", "/app.jar"]

EXPOSE 8080
