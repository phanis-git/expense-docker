# FROM node:20-alpine 
# EXPOSE 8080
# WORKDIR /opt/server
# COPY schema ./schema
# COPY *.js .
# COPY package.json .
# ENV DB_HOST="mysql"
# RUN addgroup -S expense && adduser -S expense -G expense
# RUN npm install
# USER expense
# ENTRYPOINT ["node"]
# CMD ["server.js"]


# FROM node:20-alpine 
# WORKDIR /opt/server
# EXPOSE 8080
# COPY package.json .
# COPY schema ./schema
# COPY *.js .
# RUN npm install
# ENV DB_HOST="mysql"
# RUN addgroup -S expense && adduser -S expense -G expense && \
#     chown -R expense:expense /opt/server
# USER expense
# CMD ["index.js"]
# ENTRYPOINT ["node"]


FROM node:20.18.3-alpine3.21 AS builder
WORKDIR /opt/backend
COPY package.json ./
COPY *.js ./
RUN npm install


FROM node:20.18.3-alpine3.21
RUN addgroup -S expense && adduser -S expense -G expense && \
    mkdir /opt/backend && \
    chown -R expense:expense /opt/backend
ENV DB_HOST="mysql" 
WORKDIR /opt/backend
USER expense
COPY --from=builder /opt/backend /opt/backend
CMD ["node", "index.js"]
