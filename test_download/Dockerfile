from {{ distro }}:{{ tag }}
COPY install_salt.sh /tmp/install_salt.sh
COPY check_cmd_returns.py /tmp/check_cmd_returns.py

{% if 'debian' in osflavor %}

RUN apt-get update
RUN apt-get -y install wget sudo
RUN if ! dpkg -l ca-certificates > /dev/null; then apt-get install ca-certificates -y; else exit 0; fi

{% elif 'centos' in os %}
  RUN if ! type wget > /dev/null; then yum install wget -y; fi
  RUN yum install sudo -y

{% endif %}
RUN bash /tmp/install_salt.sh
