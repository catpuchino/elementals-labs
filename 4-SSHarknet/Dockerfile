FROM ubuntu:22.04

RUN \
	apt-get update && apt-get install -y \
	curl cron openssh-server unzip tcpdump exa bat vsftpd zsh libcap2-bin xxd

# Instalación OhMyPosh
RUN curl -s https://ohmyposh.dev/install.sh | bash -s
COPY .zshrc /root/.zshrc

# Archivos de configuración
COPY vsftpd.conf /root/vsftpd.conf
COPY createkey.sh /root/createkey.sh
COPY initserver.py /root/initserver.py
COPY backup.sh /root/backup.sh

EXPOSE 21 22 40000-40010

# Configuración de script principal
COPY entrypoint.sh /usr/local/bin/entrypoint.sh
RUN chmod 770 /usr/local/bin/entrypoint.sh
ENTRYPOINT ["/usr/local/bin/entrypoint.sh"]
