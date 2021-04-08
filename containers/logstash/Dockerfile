FROM docker.elastic.co/logstash/logstash-oss:7.11.2-amd64

COPY logstashpath.sh /etc/profile.d
USER root
RUN chmod 0644 /etc/profile.d/logstashpath.sh
USER logstash

# Add bundler to logstash gem file
# see:
# https://github.com/elastic/logstash/issues/6052
# https://github.com/elastic/logstash/issues/3612
RUN grep -qs bundler /usr/share/logstash/Gemfile || echo 'gem "bundler"' >> /usr/share/logstash/Gemfile
