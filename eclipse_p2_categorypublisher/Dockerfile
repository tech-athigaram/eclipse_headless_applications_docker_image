#Stage I : Just to collect Eclipse platform 4.15 from Eclipse official releases
FROM ubuntu:20.10
RUN apt-get update
RUN apt-get install -y curl
RUN mkdir data
RUN curl -L -k -o /data/eclipse.tar.gz https://download.eclipse.org/eclipse/downloads/drops4/R-4.15-202003050155/eclipse-platform-4.15-linux-gtk-x86_64.tar.gz

#Stage II : Shipping the eclipse with ubuntu and jre container to making it ready for headless execution
FROM techathigaram/jre_adoptopenjdk8_ubuntu:8u252-b09
COPY --from=0 /data/*.tar.gz eclipse.tar.gz
RUN mkdir app
RUN tar -xzf eclipse.tar.gz -C /app/
WORKDIR /app/eclipse
ENV PATH=/app/eclipse:/opt/java/jre/bin:/usr/local/sbin:/usr/local/bin:/usr/bin:/sbin:/bin
COPY entrypoint.sh /app/
WORKDIR /app
RUN mkdir workspace
VOLUME ["/app/data"]
ENTRYPOINT ["/app/entrypoint.sh"]
