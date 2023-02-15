FROM debian
RUN apt update && apt install -y lsb-release apt-transport-https ca-certificates software-properties-common

RUN wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg 

RUN sh -c 'echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list'

RUN apt update && php-8.2-fpm