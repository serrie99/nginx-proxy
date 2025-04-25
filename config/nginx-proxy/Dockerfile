FROM jwilder/nginx-proxy

RUN { \
  echo 'client_max_body_size 0;'; \
  } > /etc/nginx/conf.d/unrestricted_client_body_size.conf

RUN { \
  echo 'proxy_connect_timeout 900;'; \
  echo 'proxy_send_timeout 900;'; \
  echo 'proxy_read_timeout 900;'; \
  echo 'send_timeout 900;'; \
  } > /etc/nginx/conf.d/timeout.conf