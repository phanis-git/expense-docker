# FROM nginx
# WORKDIR /usr/share/nginx/html
# RUN rm -rf /usr/share/nginx/html/*
# RUN useradd expense
# COPY static asset-manifest.json robots.txt index.html .
# COPY expense.conf /etc/nginx/default.d/
# EXPOSE 80
# USER expense
# CMD ["nginx", "-g", "daemon off;"]



# Running nginx as non root user

FROM nginx:alpine
WORKDIR /usr/share/nginx/html
RUN rm /etc/nginx/nginx.conf /etc/nginx/conf.d/default.conf
RUN rm -rf /usr/share/nginx/html/*

#install nginx

RUN mkdir -p /var/cache/nginx/client_temp && \
        mkdir -p /var/cache/nginx/proxy_temp && \
        mkdir -p /var/cache/nginx/fastcgi_temp && \
        mkdir -p /var/cache/nginx/uwsgi_temp && \
        mkdir -p /var/cache/nginx/scgi_temp && \
        chown -R nginx:nginx /var/cache/nginx && \
        chown -R nginx:nginx /etc/nginx/ && \
        chmod -R 755 /etc/nginx/ && \
        chown -R nginx:nginx /var/log/nginx
RUN mkdir -p /etc/nginx/ssl/ && \
    chown -R nginx:nginx /etc/nginx/ssl/ && \
    chmod -R 755 /etc/nginx/ssl/
    
RUN touch /var/run/nginx.pid && \
    chown -R nginx:nginx /var/run/nginx.pid /run/nginx.pid
COPY nginx.conf /etc/nginx/nginx.conf
COPY static/ /usr/share/nginx/html
COPY index.html /usr/share/nginx/html/index.html
# USER nginx

CMD ["nginx", "-g", "daemon off;"]
