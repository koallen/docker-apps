FROM mhart/alpine-node:6.10.0

RUN apk add --no-cache make gcc g++ python git

WORKDIR /wiki-js
RUN npm install wiki.js@latest

EXPOSE 3001
CMD ["node", "wiki", "start"]
