FROM centos:7
RUN yum install -y wget unzip curl; yum upgrade -y; yum update -y; yum clean all
ENV JDK_VERSION 8u31
ENV JDK_BUILD_VERSION b13
RUN curl -LO "http://download.oracle.com/otn-pub/java/jdk/$JDK_VERSION-$JDK_BUILD_VERSION/jdk-$JDK_VERSION-linux-x64.rpm" -H 'Cookie: oraclelicense=accept-securebackup-cookie' && rpm -i jdk-$JDK_VERSION-linux-x64.rpm; rm -f jdk-$JDK_VERSION-linux-x64.rpm; yum clean all
ENV JAVA_HOME /usr/java/default

RUN wget https://download.elasticsearch.org/elasticsearch/elasticsearch/elasticsearch-1.4.4.zip && unzip elasticsearch-1.4.4.zip && rm elasticsearch-1.4.4.zip
RUN chmod +x /elasticsearch-1.4.4/bin/elasticsearch
CMD /elasticsearch-1.4.4/bin/elasticsearch
