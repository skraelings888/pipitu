# Pull da imagem base
# ---------------
FROM jenkins/jenkins:lts

# Autor
# ------
MAINTAINER Mark Heckler <mark.heckler@gmail.com, @MkHeck>

# Buildando o container
# -------------------
USER root

# Instalar o wget
RUN apt-get install -y wget

# get maven 3.2.2
RUN wget --no-verbose -O /tmp/apache-maven-3.5.3-bin.tar.gz http://apache.cs.utah.edu/maven/maven-3/3.5.3/binaries/apache-maven-3.5.3-bin.tar.gz

# verificar checksum
RUN echo "51025855d5a7456fc1a67666fbef29de /tmp/apache-maven-3.5.3-bin.tar.gz" | md5sum -c

# Instalar maven
RUN tar xzf /tmp/apache-maven-3.5.3-bin.tar.gz -C /opt/
RUN ln -s /opt/apache-maven-3.5.3 /opt/maven
RUN ln -s /opt/maven/bin/mvn /usr/local/bin
RUN rm -f /tmp/apache-maven-3.5.3-bin.tar.gz
ENV MAVEN_HOME /opt/maven

RUN chown -R jenkins:jenkins /opt/maven

# remover arquivos baixados
RUN apt-get clean

USER jenkins
