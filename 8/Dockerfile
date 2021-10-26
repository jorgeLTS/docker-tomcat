FROM jorgelts/ubuntu:20.04

# Label
LABEL maintainer="Jorge Mendoza (github.com/jorgeLTS)"

### Set defaults
ENV JAVA_HOME=/usr/local/java/jdk1.8.0_221 \
        CATALINA_HOME=/usr/local/tomcat/apache-tomcat-8.0.21

WORKDIR /home

COPY install/* ./

RUN mkdir -p /usr/local/java/ && \
        mkdir -p /usr/local/tomcat/ && \
        tar -xzvf jdk1.8.0_221.tar.gz -C /usr/local/java/ && \
        tar -xzvf apache-tomcat-8.0.21.tar.gz -C /usr/local/tomcat/ && \
        update-alternatives --install /usr/bin/java java /usr/local/java/jdk1.8.0_221/bin/java 2 && \
        cp *.ttf /usr/local/java/jdk1.8.0_221/jre/lib/fonts/ && \
        rm -rf /home/*

WORKDIR /usr/local/tomcat/apache-tomcat-8.0.21

RUN echo -ne "export CATALINA_OPTS=" >> bin/setenv.sh &&\
    echo -ne "-XX:PermSize=512m -XX:MaxPermSize=1024m -server" >> bin/setenv.sh

EXPOSE 8080

CMD ["bin/catalina.sh", "run"]