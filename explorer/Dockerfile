FROM node:8-alpine

RUN apk add --update git &&\
    apk --no-cache add --virtual native-deps g++ gcc libgcc libstdc++ linux-headers make python && \
    npm install --quiet node-gyp bower -g

RUN git clone https://github.com/ovsoil/explorer.git

WORKDIR /explorer

RUN npm install &&\
    bower install --allow-root

EXPOSE 8000

CMD ["npm", "start"]
