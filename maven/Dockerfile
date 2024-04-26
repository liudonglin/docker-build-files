# 以微软官方镜像`mcr.microsoft.com/openjdk/jdk:17-ubuntu` 构建包含maven-3.9.6的基础镜像
FROM mcr.microsoft.com/openjdk/jdk:17-ubuntu

# ADD和COPY的区别是ADD可以自动解压压缩包
ADD apache-maven-3.9.6-bin.tar.gz /usr/local/maven/
COPY ./settings.xml /root/.m2/

# 设置环境变量
ENV MAVEN_HOME=/usr/local/maven/apache-maven-3.9.6
ENV MAVEN_CONFIG=/root/.m2
ENV JAVA_HOME=/usr/lib/jvm/msopenjdk-17

ENV PATH=$PATH:$JAVA_HOME/bin:$MAVEN_HOME/bin