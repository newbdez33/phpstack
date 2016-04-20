FROM ubuntu:trusty

RUN rm -rf /etc/apt/sources.list.d/proposed.list
RUN apt-get update && apt-get install -y gearman-job-server && rm -r /var/lib/apt/lists/*

VOLUME ["/var/www"]
WORKDIR /var/www

CMD "gearmand"
