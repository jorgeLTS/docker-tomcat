FROM jorgelts/ubuntu:20.04

# Label
LABEL maintainer="Jorge Mendoza (github.com/jorgeLTS)"

### Set defaults
ENV JAVA_HOME=/usr/local/java/jdk1.7.0_80 \
        CATALINA_HOME=/usr/local/tomcat/apache-tomcat-7.0.92

WORKDIR /home

COPY install/* ./

RUN mkdir -p /usr/local/java/ && \
        mkdir -p /usr/local/tomcat/ && \
        tar -xzvf jdk1.7.0_80.tar.gz -C /usr/local/java/ && \
        tar -xzvf apache-tomcat-7.0.92.tar.gz -C /usr/local/tomcat/ && \
        update-alternatives --install /usr/bin/java java /usr/local/java/jdk1.7.0_80/bin/java 2 && \
        cp *.ttf /usr/local/java/jdk1.7.0_80/jre/lib/fonts/ && \
        rm -rf /home/*

WORKDIR /usr/local/tomcat/apache-tomcat-7.0.92

RUN echo -ne "export CATALINA_OPTS=" >> bin/setenv.sh &&\
    echo -ne "-XX:PermSize=512m -XX:MaxPermSize=1024m -server" >> bin/setenv.sh

EXPOSE 8080

CMD ["bin/catalina.sh", "run"]