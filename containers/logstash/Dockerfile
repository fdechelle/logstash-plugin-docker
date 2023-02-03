FROM logstash:8.6.1

ENV PLUGIN_FULL_NAME=logstash-codec-awesome
ENV PLUGIN_HOME=/home/logstash/plugins/$PLUGIN_FULL_NAME
ENV LOGSTASH_GEMFILE=/opt/logstash/Gemfile

# Add plugin to logstash gem file
RUN grep -qs ${PLUGIN_FULL_NAME} ${LOGSTASH_GEMFILE} || echo 'gem "'${PLUGIN_FULL_NAME}'", :path => "'${PLUGIN_HOME}'"' >> ${LOGSTASH_GEMFILE}

# Must pass --enable-local-plugin-development option to run logstash 

# Leftover from the old way of building plugins
#COPY logstashpath.sh /etc/profile.d
#USER root
#RUN chmod 0644 /etc/profile.d/logstashpath.sh
#USER logstash
# Add bundler to logstash gem file
# see:
# https://github.com/elastic/logstash/issues/6052
# https://github.com/elastic/logstash/issues/3612
#RUN grep -qs bundler /usr/share/logstash/Gemfile || echo 'gem "bundler"' >> /usr/share/logstash/Gemfile
#RUN PATH=/usr/share/logstash/jdk/bin:/usr/share/logstash/vendor/jruby/bin:/usr/share/logstash/vendor/bundle/jruby/2.5.0/gems/rake-12.3.3/bin:$PATH gem install bundler
# Build plugin
#RUN source /etc/profile.d/logstashpath.sh ; cd /home/logstash-plugin ; gem build $PLUGIN_GEMSPEC

