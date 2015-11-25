FROM kibana:latest

RUN apt-get update && apt-get install -y netcat

COPY entrypoint.sh /tmp/entrypoint.sh
RUN chmod +x /tmp/entrypoint.sh

RUN kibana plugin --install elasticsearch/marvel/latest
RUN kibana plugin --install elastic/sense

RUN curl -L -O http://download.elastic.co/beats/dashboards/beats-dashboards-1.0.0.tar.gz
RUN tar xzvf beats-dashboards-1.0.0.tar.gz
WORKDIR beats-dashboards-1.0.0/
RUN ./load.sh

CMD ["/tmp/entrypoint.sh"]
