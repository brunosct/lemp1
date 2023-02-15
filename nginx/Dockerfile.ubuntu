FROM ubuntu:latest

# RUN apt update && apt install -y curl gnupg2 ca-certificates lsb-release debian-archive-keyring

RUN apt update && apt install -y curl gnupg2 ca-certificates lsb-release ubuntu-keyring
RUN curl https://nginx.org/keys/nginx_signing.key | gpg --dearmor   \
    | tee /usr/share/keyrings/nginx-archive-keyring.gpg >/dev/null

# RUN echo "deb [signed-by=/usr/share/keyrings/nginx-archive-keyring.gpg] \
#     http://nginx.org/packages/debian `lsb_release -cs` nginx" \
#     | tee /etc/apt/sources.list.d/nginx.list
RUN echo "deb [signed-by=/usr/share/keyrings/nginx-archive-keyring.gpg] \
    http://nginx.org/packages/ubuntu `lsb_release -cs` nginx" \
    | tee /etc/apt/sources.list.d/nginx.list
RUN apt update && apt install nginx


RUN echo "Europe/Madrid" >/etc/timezone
RUN DEBIAN_FRONTEND="noninteractive" apt install -y php-fpm

EXPOSE 80

RUN mkdir -p /run/php/
RUN touch /run/php/php8.1-fpm.sock

# RUN sed -i "s/^listen\.owner.*$/listen.owner = nginx/" /etc/php/7.4/fpm/pool.d/www.conf
# RUN sed -i  "s/^listen\.group.*$/listen.group = nginx/" /etc/php/7.4/fpm/pool.d/www.conf


CMD ["/sbin/entrypoint.sh"]