FROM centos:7

ADD https://download.elasticsearch.org/kibana/kibana/kibana-4.0.0-linux-x64.tar.gz /kibana.tar.gz

RUN yum install -y tar; yum upgrade -y; yum update -y; yum clean all

RUN tar zxf /kibana.tar.gz 
ADD kibana.yml /kibana-4.0.0-linux-x64/config/kibana.yml
EXPOSE 5601

CMD ["/kibana-4.0.0-linux-x64/bin/kibana"]
