FROM nginx

# Only use stable sources
#RUN rm -rf /etc/apt/sources.list.d/proposed.list

# Install packages
RUN apt-get update
RUN apt-get install -y \
  cron \
  supervisor \
  curl \
  wget \
  php5-fpm \
  php5-mysql \
  php5-mcrypt \
  php5-gd \
  php5-memcached \
  php5-curl \
  php5-gearman \
  exiftool

# Create required directories
RUN ["mkdir", "-p", "/var/log/supervisor"]
RUN ["mkdir", "-p", "/etc/nginx"]
RUN ["mkdir", "-p", "/var/run/php5-fpm"]

# Set the timezone.
RUN echo "Asia/Hong_Kong" > /etc/timezone
RUN dpkg-reconfigure -f noninteractive tzdata

# Add configuration files
ADD supervisord.conf /etc/supervisor/conf.d/supervisord.conf
ADD php.ini /etc/php5/fpm/conf.d/40-custom.ini
ADD xextra.conf /etc/php5/fpm/pool.d/xextra.conf
ADD xtc.vhost /etc/nginx/conf.d/default.conf
ADD crontab.root /var/spool/cron/crontabs/root
COPY nginx.conf /etc/nginx/

# Expose volumes
VOLUME ["/var/www"]

EXPOSE 80 9000

CMD ["/usr/bin/supervisord"]
