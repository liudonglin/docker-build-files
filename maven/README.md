
# 下载maven，此处版本3.9.4

wget https://dlcdn.apache.org/maven/maven-3/3.9.6/binaries/apache-maven-3.9.6-bin.tar.gz

## 创建Dockerfile

cat << EOF > Dockerfile

# 以微软官方镜像`mcr.microsoft.com/openjdk/jdk:17-ubuntu` 构建包含maven-3.9.6的基础镜像
FROM mcr.microsoft.com/openjdk/jdk:17-ubuntu

# ADD和COPY的区别是ADD可以自动解压压缩包
ADD apache-maven-3.9.6-bin.tar.gz /usr/local/maven/
COPY ./settings.xml /root/.m2/

# 设置环境变量
ENV MAVEN_HOME=/usr/local/maven/apache-maven-3.9.6
ENV MAVEN_CONFIG=/root/.m2

ENV CLASSPATH=.:$JAVA_HOME/lib/jrt-fs.jar:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
ENV PATH=$PATH:$JAVA_HOME/bin:$MAVEN_HOME/bin

# 加这句命令，可以在后台驻留运行
# CMD ["/bin/bash"]

EOF

# 构建镜像
# 在Dockerfile所在目录执行以下命令
# docker build --platform linux/amd64 -f ./Dockerfile -t 10.0.0.17:3060/cicd/microsoft-openjdk-maven:17-3.9.6 .

docker build -t 10.0.0.17:3060/cicd/maven-microsoft-openjdk:latest .