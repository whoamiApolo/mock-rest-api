FROM node:latest

RUN npm install -g json-server

RUN echo '{"data":[{"id":1,"title":"HP","year":"2001"}]}' > /tmp/base.json

ENTRYPOINT ["json-server", "--port", "8080", "--host", "0.0.0.0"]

CMD ["/tmp/base.json"]