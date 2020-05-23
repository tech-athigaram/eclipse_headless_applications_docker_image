#Stage I : Just to collect OpenJDK8 JRE from AdoptOpenJDK releases
FROM ubuntu:20.10
RUN apt-get update
RUN apt-get install -y curl
RUN mkdir data
RUN curl -L -k -o /data/jre.tar.gz https://github.com/AdoptOpenJDK/openjdk8-binaries/releases/download/jdk8u252-b09/OpenJDK8U-jre_x64_linux_hotspot_8u252b09.tar.gz

#Stage II : Shipping the jre with ubuntu container to making it ready for eclipse installation
FROM ubuntu:20.10
COPY --from=0 /data/jre.tar.gz jre.tar.gz
RUN cd /opt/ && mkdir java
RUN tar -xzf /jre.tar.gz -C /opt/java
RUN mv /opt/java/jdk8u252-b09-jre /opt/java/jre
ENV JAVA_HOME=/opt/java/jre PATH=/opt/java/jre/bin:/usr/local/sbin:/usr/local/bin:/usr/bin:/sbin:/bin
