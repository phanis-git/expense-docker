FROM nodejs:20
EXPOSE 8080
WORKDIR /opt/server
COPY schema .
COPY *.js .
COPY package.json .
RUN useradd expense
ENV DB_HOST="mysql"
USER expense
CMD ["server.js"]
ENTRYPOINT ["node"]