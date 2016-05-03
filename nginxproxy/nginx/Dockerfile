FROM nginx:latest

COPY ["artifactory.conf", "/etc/nginx/conf.d/" ]
COPY ["runNginx.sh", "updateConf.sh", "/usr/bin/"]

# Install curl and jq to do some http requests
# and generate self-signed certificate
RUN \
  apt-get update && \
  apt-get install -y curl jq && \
  rm -rf /var/lib/apt/lists/* && \
  mkdir -p /etc/pki/tls/private && \
  mkdir -p /etc/pki/tls/certs && \
  openssl req -nodes -x509 -newkey rsa:4096 -keyout /etc/pki/tls/private/example.key -out /etc/pki/tls/certs/example.pem -days 356 \
    -subj "/C=US/ST=California/L=SantaClara/O=IT/CN=localhost"

CMD ["runNginx.sh"]
