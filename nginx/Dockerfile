FROM nginx

COPY ./app.conf /etc/nginx/conf.d/app.conf

ARG NGINX_SERVER_NAME
ARG NGINX_DOCUMENT_ROOT
ARG PHPFPM_IP

RUN sed -i.bak "s|NGINX_SERVER_NAME|${NGINX_SERVER_NAME}|g" /etc/nginx/conf.d/app.conf
RUN sed -i.bak "s|NGINX_DOCUMENT_ROOT|${NGINX_DOCUMENT_ROOT}|g" /etc/nginx/conf.d/app.conf
RUN sed -i.bak "s|PHPFPM_IP|${PHPFPM_IP}|g" /etc/nginx/conf.d/app.conf