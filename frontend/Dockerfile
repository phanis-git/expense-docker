FROM nginx
RUN rm -rf /usr/share/nginx/html/*
WORKDIR /usr/share/nginx/html
RUN useradd expense
COPY static asset-manifest.json robots.txt index.html .
COPY expense.conf /etc/nginx/default.d/
EXPOSE 80
USER expense
CMD ["nginx", "-g", "daemon off;"]