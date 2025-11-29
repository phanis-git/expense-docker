FROM node:20-alpine 
EXPOSE 8080
WORKDIR /opt/server
COPY schema ./schema
COPY *.js .
COPY package.json .
ENV DB_HOST="mysql"
RUN addgroup -S expense && adduser -S expense -G expense
RUN npm install
USER expense
ENTRYPOINT ["node"]
CMD ["server.js"]